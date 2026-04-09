# Multi-Persona Review V11: Operational Safety and Guard Strictness

Date: 2026-02-17
Scope: Follow-up improvement pass after V10, focused on safe recovery and deterministic run behavior.

## Findings (ordered by severity)

### 1) High: Backup targets could be overwritten across repeated runs
- Previous behavior: backups were written to a stable path and could be replaced by later runs.
- Risk: rollback fidelity degraded over time (only latest backup retained by path).
- Improvement applied: all translation tools now create a per-run timestamped backup folder under `--backup-dir`.
- File references:
  - `complete_existing_course_translations.py:140`
  - `complete_existing_course_translations.py:430`
  - `sync_translate_from_source.py:250`
  - `sync_translate_from_source.py:257`
  - `translate_index_cards.py:73`
  - `translate_index_cards.py:247`
  - `batch_translate_visible_nodes.py:218`
  - `batch_translate_visible_nodes.py:225`

### 2) High: Guard-blocked writes were not explicitly surfaced as non-success outcome
- Previous behavior: a guard block could skip a file without forcing non-zero process status.
- Risk: automation may interpret partial application as full success.
- Improvement applied: `complete_existing_course_translations.py` now tracks guard blocks and exits non-zero when any guard block occurs.
- File references:
  - `complete_existing_course_translations.py:431`
  - `complete_existing_course_translations.py:452`
  - `complete_existing_course_translations.py:482`

### 3) Medium: Translation integrity checks needed validation against false positives
- Improvement applied: retained masked-script scanning logic and revalidated with lint and dry-runs.
- File references:
  - `complete_existing_course_translations.py:389`
  - `lint_translation_integrity.py:65`

## Improvement Pass Summary
- Added per-run timestamped backup roots across all translation write tools.
- Added strict guard exit semantics for script-integrity blocked writes in completion tool.
- Revalidated translation-integrity lint after these changes.

## Validation
- `python -c "...py_compile..."` -> `py_compile ok 7`.
- `python complete_existing_course_translations.py --dry-run --include-scripts` -> `Total replacements: 0`.
- `python sync_translate_from_source.py --lang fr --pairs "index.html>index-fr.html" --dry-run` -> `0 replacements`.
- `python translate_index_cards.py --dry-run` -> `0 replacements`.
- `python lint_translation_integrity.py` -> `OK: 20 localized files checked, no integrity issues found.`
- Runtime regression check: `python test_methods_course.py` -> `70 passed, 0 failed, 0 warnings`.

## Residual Risk
- One external python process (`python -`) was detected outside this workspace flow and intentionally left untouched.
