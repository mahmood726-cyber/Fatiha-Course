# Multi-Persona Review V15: Fail-Fast Input Safety and Preflight Validation

Date: 2026-02-17  
Scope: Follow-up pass after V14, focused on removing traceback-style failures and silent no-op success paths in tooling CLIs.

## Findings (ordered by severity)

### 1) High: Invalid `--pairs` format in sync translator raised an uncaught traceback
- Previous behavior: malformed pair syntax (for example `index.html:index-fr.html`) raised `ValueError` and produced stacktrace noise.
- Risk: poor operator UX and brittle automation parsing.
- Improvement applied:
  - Replaced exception-throw path with explicit parse error reporting.
  - Added strict fail-fast return when pair format errors are present.
- File references:
  - `sync_translate_from_source.py:330`
  - `sync_translate_from_source.py:335`
  - `sync_translate_from_source.py:342`

### 2) High: Lint `--files` selection could silently pass on nonexistent requested files
- Previous behavior: `lint_translation_integrity.py --files not-a-real-file-fr.html` returned success with “No localized HTML files found to lint.”
- Risk: CI/operator false confidence that requested target files were checked.
- Improvement applied:
  - Added explicit requested-file existence validation against localized targets.
  - Added non-zero return on selection mismatch.
- File references:
  - `lint_translation_integrity.py:118`
  - `lint_translation_integrity.py:125`
  - `lint_translation_integrity.py:126`

### 3) Medium: Root/source preflight checks were inconsistent across scripts
- Previous behavior: invalid `--root` or missing required source files could fail late or noisily depending on script.
- Improvement applied:
  - Added explicit root directory checks in translation/lint CLIs.
  - Added required source file preflight in index-card translator.
- File references:
  - `complete_existing_course_translations.py:444`
  - `sync_translate_from_source.py:299`
  - `batch_translate_visible_nodes.py:265`
  - `translate_index_cards.py:266`
  - `translate_index_cards.py:270`
  - `lint_translation_integrity.py:115`

## Improvement Pass Summary
- Replaced traceback-prone pair parsing with actionable CLI error handling.
- Eliminated lint selection false-success behavior.
- Standardized fail-fast preflight validation for invalid roots and missing required source files.

## Validation
- Syntax:
  - `python -m py_compile complete_existing_course_translations.py translate_index_cards.py sync_translate_from_source.py batch_translate_visible_nodes.py lint_translation_integrity.py test_methods_course.py` -> success.
- Baseline integrity:
  - `python lint_translation_integrity.py` -> `OK: 20 localized files checked, no integrity issues found.`
  - `python complete_existing_course_translations.py --dry-run --include-scripts` -> clean run, `Total replacements: 0`.
- Negative-path checks:
  - `python sync_translate_from_source.py --lang fr --pairs "index.html:index-fr.html" --dry-run` -> explicit invalid pair error, exit non-zero.
  - `python lint_translation_integrity.py --files not-a-real-file-fr.html` -> explicit selection error, exit non-zero.
  - Root preflight checks now fail fast (non-zero) in completion/sync/batch/index scripts when `--root` is invalid.
- Runtime regression:
  - `python test_methods_course.py` -> `70 passed, 0 failed, 0 warnings`.

## Residual Risk
- Translation availability and quality remain dependent on external Google Translate endpoint behavior and network conditions.
