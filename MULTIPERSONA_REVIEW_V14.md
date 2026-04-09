# Multi-Persona Review V14: Selection Validation and Language-Code Safety

Date: 2026-02-17  
Scope: Follow-up pass after V13, focused on preventing silent no-op runs caused by invalid language and filter inputs.

## Findings (ordered by severity)

### 1) High: Invalid `--langs` in completion flow could previously lead to successful no-op behavior
- Risk: operators could mistype a language and still receive a green exit status with no files processed.
- Improvement applied:
  - Added dynamic `available_langs` derivation from localized files.
  - Added explicit errors for unknown requested languages.
  - Added explicit error when filters are provided but no files match.
- File references:
  - `complete_existing_course_translations.py:453`
  - `complete_existing_course_translations.py:469`
  - `complete_existing_course_translations.py:544`

### 2) High: Index-card translator did not fail on unsupported selected language filters
- Risk: `--langs` typos could silently do nothing.
- Improvement applied:
  - Added unsupported-language detection for index-specific language map.
  - Added selected-file-missing errors when a chosen language page is absent.
  - Added explicit non-zero return when selected filters produce no processable files.
- File references:
  - `translate_index_cards.py:293`
  - `translate_index_cards.py:303`
  - `translate_index_cards.py:329`
  - `translate_index_cards.py:337`

### 3) Medium: Pair/batch translators accepted malformed language codes and empty effective selections
- Risk: malformed language codes (`english`) could proceed unpredictably; empty parsed inputs could no-op.
- Improvement applied:
  - Added alias-aware language normalization and strict language-code regex validation.
  - Added explicit error for empty parsed `--pairs` in sync workflow.
  - Added language normalization and validation in batch workflow (including zh alias mapping to `zh-CN`).
- File references:
  - `sync_translate_from_source.py:43`
  - `sync_translate_from_source.py:299`
  - `sync_translate_from_source.py:329`
  - `batch_translate_visible_nodes.py:92`
  - `batch_translate_visible_nodes.py:265`

## Improvement Pass Summary
- Hardened all translation CLIs against silent success on invalid selection/language input.
- Standardized language normalization behavior where missing (including `zh` -> `zh-CN` path).
- Preserved prior backup/guard integrity hardening from V11-V13.

## Validation
- Syntax:
  - `python -m py_compile complete_existing_course_translations.py translate_index_cards.py sync_translate_from_source.py batch_translate_visible_nodes.py lint_translation_integrity.py test_methods_course.py` -> success.
- Integrity:
  - `python lint_translation_integrity.py` -> `OK: 20 localized files checked, no integrity issues found.`
- Baseline dry-run:
  - `python complete_existing_course_translations.py --dry-run --include-scripts` -> clean run, `Total replacements: 0`.
- Negative-path checks (all now fail correctly):
  - `python complete_existing_course_translations.py --dry-run --langs xx` -> selection errors, exit non-zero.
  - `python translate_index_cards.py --dry-run --langs xx` -> selection errors, exit non-zero.
  - `python sync_translate_from_source.py --lang english --pairs "index.html>index-fr.html" --dry-run` -> invalid language error, exit non-zero.
  - `python batch_translate_visible_nodes.py --lang english --files index-fr.html --dry-run` -> invalid language error, exit non-zero.
- Alias sanity checks:
  - `python sync_translate_from_source.py --lang zh --pairs "index.html>index-fr.html" --dry-run` -> processed successfully.
  - `python batch_translate_visible_nodes.py --lang zh --files index-fr.html --dry-run` -> processed successfully.
- Runtime regression:
  - `python test_methods_course.py` -> `70 passed, 0 failed, 0 warnings`.

## Residual Risk
- Translation quality and availability still depend on external Google Translate API behavior (rate/latency/content), unchanged in this pass.
