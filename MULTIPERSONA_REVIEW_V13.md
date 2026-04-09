# Multi-Persona Review V13: Input Validation and Backup Run Isolation

Date: 2026-02-17  
Scope: Follow-up improvement pass after V12, focused on CLI safety and deterministic backup isolation.

## Findings (ordered by severity)

### 1) High: Backup run folders could still collide when scripts start in the same second
- Previous behavior: per-run backups used second-level timestamps only.
- Risk: concurrent/rapid invocations could share the same run directory and blur rollback boundaries.
- Improvement applied: introduced `make_backup_run_dir(...)` in all translation writers with timestamp + sanitized run label + PID + nanosecond nonce.
- File references:
  - `complete_existing_course_translations.py:185`
  - `sync_translate_from_source.py:192`
  - `translate_index_cards.py:119`
  - `batch_translate_visible_nodes.py:182`

### 2) High: `complete_existing_course_translations.py --files` accepted invalid file names silently
- Previous behavior: unknown `--files` entries were ignored without an error.
- Risk: automation can report success while intended targets were skipped due to typo/input drift.
- Improvement applied: explicit selection validation with `[ERR]` output and non-zero exit when requested files are not valid localized targets.
- File references:
  - `complete_existing_course_translations.py:464`
  - `complete_existing_course_translations.py:534`
  - `complete_existing_course_translations.py:539`

### 3) Medium: Batch and pair translation CLIs lacked early existence checks
- Previous behavior: missing inputs surfaced only later via open/processing failures.
- Risk: slower failure detection and less actionable operator feedback.
- Improvement applied:
  - `sync_translate_from_source.py`: validates source/target pair files before processing.
  - `batch_translate_visible_nodes.py`: validates all `--files` upfront and exits non-zero on selection errors.
- File references:
  - `sync_translate_from_source.py:311`
  - `sync_translate_from_source.py:314`
  - `sync_translate_from_source.py:316`
  - `batch_translate_visible_nodes.py:264`
  - `batch_translate_visible_nodes.py:265`

## Improvement Pass Summary
- Added unique backup run-folder creation across all translation writer scripts.
- Added strict input selection validation in completion/batch/pair workflows.
- Preserved existing translation-integrity guard/lint behavior and runtime compatibility.

## Validation
- `python -m py_compile complete_existing_course_translations.py sync_translate_from_source.py translate_index_cards.py batch_translate_visible_nodes.py lint_translation_integrity.py test_methods_course.py` -> success.
- `python lint_translation_integrity.py` -> `OK: 20 localized files checked, no integrity issues found.`
- `python complete_existing_course_translations.py --dry-run --include-scripts` -> clean run, `Total replacements: 0`.
- Negative-path checks:
  - `python complete_existing_course_translations.py --dry-run --files not-a-real-file-fr.html` -> exits non-zero with selection error.
  - `python batch_translate_visible_nodes.py --lang fr --files not-a-real-file.html --dry-run` -> exits non-zero with file selection error.
  - `python sync_translate_from_source.py --lang fr --pairs "index.html>not-a-real-target.html" --dry-run` -> exits non-zero with pair validation error.
- Runtime regression check:
  - `python test_methods_course.py` -> `70 passed, 0 failed, 0 warnings`.

## Residual Risk
- The translation scripts still depend on external Google Translate endpoint availability and rate behavior; this pass did not change network fallback strategy.
