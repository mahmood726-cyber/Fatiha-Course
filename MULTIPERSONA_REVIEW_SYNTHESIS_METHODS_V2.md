# Multi-Persona Review: Synthesis Methods Rigor (V2)

Date: 2026-02-19  
Scope: `synthesis-course.html` plus all localized synthesis variants

## Findings (ordered by severity)

### 1) High: Advanced-method rankings and Bayesian evidence language risked over-interpretation
- Risk: learners could treat rankings or Bayes-factor conventions as decisive without uncertainty/sensitivity context.
- Improvements:
  - SUCRA and P-score now explicitly framed as ranking summaries, not standalone evidence.
  - Bayes-factor and credible-interval language now explicitly conditional on model/prior assumptions.
- File references:
  - `synthesis-course.html:3095`
  - `synthesis-course.html:3139`
  - `synthesis-course.html:8441`
  - `synthesis-course.html:8525`

### 2) High: NMA teaching slides needed stronger assumption diagnostics
- Risk: users may apply indirect comparisons without checking effect-modifier balance or direct-vs-indirect disagreement.
- Improvements:
  - NMA slides now emphasize uncertainty, trade-offs, and assumptions in comparative interpretation.
  - Transitivity and consistency descriptors now require diagnostic testing and investigation.
- File references:
  - `synthesis-course.html:8030`
  - `synthesis-course.html:8066`
  - `synthesis-course.html:8077`
  - `synthesis-course.html:8084`

### 3) Medium: Publication-bias tool outputs were too definitive
- Risk: asymmetry tests could be interpreted as direct proof of publication bias and trim-and-fill as correction.
- Improvements:
  - Tool interpretation now reports “possible small-study effects” rather than bias proof.
  - Trim-and-fill output now explicitly labeled sensitivity analysis.
- File references:
  - `synthesis-course.html:14277`
  - `synthesis-course.html:14667`

### 4) Medium: Prior-selection guidance had one overly absolute default framing
- Risk: users may treat one prior strategy as universally optimal.
- Improvement:
  - Wording now states weakly informative priors as a common practical default, not a universal best.
- File reference:
  - `synthesis-course.html:8587`

## Cross-Language Propagation
- Applied the same rigor updates to all synthesis localized variants:
  - `synthesis-course-<lang>.html` for `ar,de,es,fr,hi,it,ja,ko,pt,ru,zh`
  - `synthesis-course-original-<lang>.html` for `ar,de,es,fr,hi,it,ja,ko,pt,ru,zh`
- Automated run results:
  - `files_changed=22`
  - `total_replacements=233` (source phrase propagation)
  - translation completion pass: `Total replacements: 108`
  - targeted dry-run convergence: `Total replacements: 0`

## Validation
- `python3 lint_translation_integrity.py` -> `OK: 297 localized files checked, no integrity issues found.`
- Old overconfident phrasings scan across all synthesis localized files -> `old_phrase_hits 0`.
