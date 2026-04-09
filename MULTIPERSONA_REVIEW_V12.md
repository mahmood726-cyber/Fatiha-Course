# Multi-Persona Review V12: Runtime Hardening and Integrity Signal Quality

Date: 2026-02-17  
Scope: Follow-up pass after V11, focused on runtime robustness and guard/lint signal precision.

## Findings (ordered by severity)

### 1) High: Import-time stdout wrapping created avoidable runtime side effects
- Previous behavior: several scripts reassigned `sys.stdout` at import time.
- Risk: import-time mutation can break test runners, subprocess wrappers, or environments where `stdout.buffer` is unavailable.
- Improvement applied: replaced top-level reassignment with best-effort `configure_stdout_utf8()` invoked inside `main()` / `run_tests()`.
- File references:
  - `complete_existing_course_translations.py:109`
  - `complete_existing_course_translations.py:430`
  - `sync_translate_from_source.py:26`
  - `sync_translate_from_source.py:252`
  - `translate_index_cards.py:29`
  - `translate_index_cards.py:252`
  - `batch_translate_visible_nodes.py:24`
  - `batch_translate_visible_nodes.py:224`
  - `test_methods_course.py:15`
  - `test_methods_course.py:47`

### 2) High: Per-file exceptions in completion flow were not reflected in exit status
- Previous behavior: `complete_existing_course_translations.py` logged exceptions but only returned non-zero for guard blocks.
- Risk: automation can treat a partially failed run as successful.
- Improvement applied: added `file_errors` tracking and non-zero exit when either guard blocks or file errors occur.
- File references:
  - `complete_existing_course_translations.py:446`
  - `complete_existing_course_translations.py:503`
  - `complete_existing_course_translations.py:515`

### 3) Medium: Guard/lint suspicious-key regex needed encoding-stable literals without false positives
- Observation during pass: broadening pattern to include unaccented variants caused false positives on legitimate `consequence:` keys.
- Improvement applied: switched to Unicode escape forms for accented localized keys only (`cons\u00e9quence`, `r\u00e9sultat`, `v\u00e9rit\u00e9`), preserving detection while avoiding English-key collisions.
- File references:
  - `complete_existing_course_translations.py:34`
  - `lint_translation_integrity.py:24`

## Improvement Pass Summary
- Removed import-time stdout mutation from translation and Selenium runtime scripts.
- Added strict per-file failure accounting to translation completion exit behavior.
- Kept guard/lint parity while tightening suspicious-key matching to avoid false alarms.

## Validation
- `python -m py_compile complete_existing_course_translations.py lint_translation_integrity.py sync_translate_from_source.py translate_index_cards.py batch_translate_visible_nodes.py test_methods_course.py` -> success.
- `python lint_translation_integrity.py` -> `OK: 20 localized files checked, no integrity issues found.`
- `python complete_existing_course_translations.py --dry-run --include-scripts` -> `Total replacements: 0` and clean per-file run.
- `python test_methods_course.py` -> `70 passed, 0 failed, 0 warnings`.

## Residual Risk
- `test_methods_course.py` is still an end-to-end browser test and remains dependent on local Chrome/driver availability.
