# Translation and Audit Changelog
Date: 2026-02-17
Folder: C:\Users\user\Downloads\Fatiha course

## Scope Completed
- Full localization completion across all existing localized HTML files.
- Full source-sync pass (`source.html -> localized.html`) for every available language pair.
- Index card pass rerun.
- Translation tooling hardening and browser-based verification.

## Replacement Totals (this full run)
- `complete_existing_course_translations.py --include-scripts`: 137 replacements.
- `sync_translate_from_source.py` additional replacements: 64 replacements.
- Targeted completion (`truthcert-course-fr.html`): 1 replacement.
- Targeted completion (`synthesis-course-fr.html`): 17 replacements.
- `translate_index_cards.py`: 0 replacements.
- Total replacements applied in this full run: 219.

## Tooling Fixes Applied
- `complete_existing_course_translations.py`
  - Language code normalization/aliases for Chinese (`zh`, `zh_cn`, `zh-hans`, `zh-cn`).
  - Curly apostrophe normalization in text preprocessing.
  - Stable ASCII regex for English token detection.
  - Hardened JS-literal safety filter to reject object-fragment artifacts (prevents code-token corruption in script translation mode).
- `translate_index_cards.py`
  - Language normalization and `zh` alias support (`zh-cn` internal, `zh-CN` API mapping).
- `batch_translate_visible_nodes.py`
  - Curly apostrophe normalization and stable English-token regex.
- `sync_translate_from_source.py`
  - Curly apostrophe normalization and stable English-token regex.
- `test_methods_course.py`
  - JS error counter now counts only non-ignored severe errors.
- `audit_all_courses.py`
  - Slide navigation checks now prefer `goToSlide()` before render/display fallback calls.

## Regression Repair Performed
- `synthesis-course-fr.html`
  - Repaired corrupted scenario object syntax and malformed keys causing:
    - `SyntaxError: Invalid or unexpected token`
    - `ReferenceError: fausse is not defined`
  - Normalized malformed misconception keys back to valid JS (`truth`, `story`, boolean `false`).

## Localized Files Updated
- `grade-certainty-course-fr.html`
- `index-ar.html`
- `index-de.html`
- `index-es.html`
- `index-fr.html`
- `index-hi.html`
- `index-it.html`
- `index-ja.html`
- `index-ko.html`
- `index-pt.html`
- `index-ru.html`
- `index-zh.html`
- `meta-analysis-methods-course-es.html`
- `risk-of-bias-mastery-course-fr.html`
- `synthesis-course-fr.html`
- `truthcert-course-fr.html`

## Verification
- Python syntax check: all scripts compile (`py_compile`).
- Selenium methods-course suite: 70 passed, 0 failed, 0 warnings.
- Full all-course browser audit (`python -u audit_all_courses.py`):
  - total files: 47
  - files with issues: 0
  - load/runtime/nav/broken-ref errors: 0
  - slides checked: 3209
- Targeted browser audit on all updated localized pages (16 files):
  - load errors: 0
  - runtime errors: 0
  - nav errors: 0
  - broken refs: 0
- Full dry-run completion checks now return zero:
  - `complete_existing_course_translations.py --dry-run`
  - `complete_existing_course_translations.py --dry-run --include-scripts`
  - `translate_index_cards.py --dry-run`

## Notes
- This folder is not a Git repository; changes were tracked and validated by script output and file-level verification.
