# Multi-Persona Review V10: Tooling Hardening Pass

Date: 2026-02-17
Scope: Follow-up review and reliability improvements for translation automation and release checks.

## Findings (ordered by severity)

### 1) High: No automatic rollback in translation writers (operational data-loss risk)
- Impact: Any bad run can overwrite large localized files with no native undo path.
- Resolution: Added `--backup-dir` and pre-write backup creation in all translation write tools.
- File references:
  - `complete_existing_course_translations.py:140`
  - `complete_existing_course_translations.py:161`
  - `sync_translate_from_source.py:168`
  - `sync_translate_from_source.py:250`
  - `translate_index_cards.py:73`
  - `translate_index_cards.py:95`
  - `batch_translate_visible_nodes.py:158`
  - `batch_translate_visible_nodes.py:218`

### 2) High: Include-scripts mode needed stronger corruption guardrails
- Impact: Script-literal translation can accidentally mutate JS object structure and create runtime failures.
- Resolution: Added string-masked script integrity checks before write (localized key detection + non-boolean truth detection).
- File references:
  - `complete_existing_course_translations.py:37`
  - `complete_existing_course_translations.py:41`
  - `complete_existing_course_translations.py:389`
  - `complete_existing_course_translations.py:410`
  - `complete_existing_course_translations.py:412`
  - `complete_existing_course_translations.py:458`

### 3) Medium: No reusable translation-integrity quality gate
- Impact: Corruption detection depended on ad hoc audits after changes.
- Resolution: Added dedicated linter for localized HTML script integrity checks.
- File references:
  - `lint_translation_integrity.py:1`
  - `lint_translation_integrity.py:24`
  - `lint_translation_integrity.py:28`
  - `lint_translation_integrity.py:57`
  - `lint_translation_integrity.py:65`

## Improvement Pass Summary
- Implemented backup-first writes across all translation scripts.
- Hardened script translation safety with masked-source integrity checks.
- Added repeatable integrity linting command for localized pages.

## Validation
- `python -c "...py_compile..."` -> `py_compile ok 7`.
- `python lint_translation_integrity.py` -> `OK: 20 localized files checked, no integrity issues found.`
- `python complete_existing_course_translations.py --dry-run --include-scripts` -> `Total replacements: 0`.
- `python test_methods_course.py` -> `70 passed, 0 failed, 0 warnings`.
- Backup behavior validated with temporary file run (`[BAK] ...` emitted and backup file confirmed).

## Residual Risk
- Some course pages still use many `innerHTML` assignments. Current content appears static/controlled, but if user-supplied text is ever introduced into those paths, sanitization boundaries will need another dedicated hardening pass.
