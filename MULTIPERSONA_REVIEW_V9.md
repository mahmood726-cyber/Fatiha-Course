# Multi-Persona Review V9: Reliability and Translation Safety Pass

Date: 2026-02-17
Scope: Translation tooling and release-safety hardening after full localization pass.

## Personas Used
- QA Engineer: runtime integrity, recoverability, regression prevention.
- Localization Engineer: translation correctness and script-key integrity.
- Release Engineer: repeatable CLI workflows and failure isolation.
- Security Reviewer: script mutation safety and unsafe write-path exposure.

## Findings (ordered by severity)

### 1) High: Translation writers had no rollback path on overwrite
- Risk: a bad translation run could permanently overwrite large HTML files.
- Affected tools: `complete_existing_course_translations.py`, `sync_translate_from_source.py`, `translate_index_cards.py`, `batch_translate_visible_nodes.py`.
- Fix applied: backup support added via `--backup-dir` plus automatic backup creation before write.
- Refs:
  - `complete_existing_course_translations.py:140`, `complete_existing_course_translations.py:161`
  - `sync_translate_from_source.py:168`, `sync_translate_from_source.py:250`
  - `translate_index_cards.py:73`, `translate_index_cards.py:95`
  - `batch_translate_visible_nodes.py:158`, `batch_translate_visible_nodes.py:218`

### 2) High: Script-literal translation could mutate JS object structure
- Risk: include-scripts mode can accidentally transform keys/values and introduce runtime errors.
- Fix applied: pre-write script integrity guard with string-literal masking and suspicious-key/truth checks.
- Refs:
  - `complete_existing_course_translations.py:37`
  - `complete_existing_course_translations.py:41`
  - `complete_existing_course_translations.py:389`
  - `complete_existing_course_translations.py:458`

### 3) Medium: No standalone lint gate for localized integrity
- Risk: corruption could be discovered late (during browser audit) instead of early in CI-like checks.
- Fix applied: new lint script `lint_translation_integrity.py`.
- Refs:
  - `lint_translation_integrity.py:24`
  - `lint_translation_integrity.py:28`
  - `lint_translation_integrity.py:57`
  - `lint_translation_integrity.py:65`

## Improvement Pass Applied
- Added backup support to all translation writers with consistent CLI behavior.
- Added script-integrity guard in the main completion tool to block dangerous writes.
- Added dedicated lint tool for localized integrity checking.
- Kept existing workflows backward compatible (`--backup-dir` defaults safely).

## Validation Evidence
- `py_compile` succeeded for all Python files: `py_compile ok 7`.
- `python complete_existing_course_translations.py --dry-run --include-scripts` => `Total replacements: 0`.
- `python lint_translation_integrity.py` => `OK: 20 localized files checked, no integrity issues found.`
- Backup path tested with a temporary file via `batch_translate_visible_nodes.py`; backup file created as expected.

## Residual Risk (not changed in this pass)
- Many course files still use `innerHTML` with template-generated content. Current data flow appears local/static, but if future user-controlled content is introduced, this area needs stricter sanitization boundaries.
