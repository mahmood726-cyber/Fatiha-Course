# Multi-Persona Review: Synthesis Methods Rigor (V4)

Date: 2026-02-19  
Scope: Follow-up conceptual validity pass on `synthesis-course.html` + localized synthesis propagation

## Findings (ordered by severity)

### 1) High: NMA assumption definitions were partially conflated
- Issue: transitivity was phrased as direct-vs-indirect agreement (which is consistency), risking conceptual confusion.
- Risk: learners may run inconsistency tests without first checking exchangeability/effect modifiers.
- Improvements:
  - Transitivity now defined as effect-modifier comparability across comparisons.
  - Consistency now defined as agreement between direct and indirect estimates within uncertainty.
- File references:
  - `synthesis-course.html:8758`
  - `synthesis-course.html:8763`

### 2) High: Bayesian quiz language lacked explicit model/prior conditioning
- Issue: credible-interval explanation implied unconditional probability statements.
- Risk: overconfidence in Bayesian outputs without sensitivity discipline.
- Improvements:
  - Quiz feedback now explicitly conditions interpretation on the specified model and prior.
  - Correct option wording now states posterior probability conditional on assumptions.
  - Heterogeneity-prior quiz reframed from "recommended" to "commonly used weakly informative prior family."
- File references:
  - `synthesis-course.html:8476`
  - `synthesis-course.html:8623`
  - `synthesis-course.html:8640`

### 3) Medium: Ranking metric explanation still implied certainty language
- Issue: P-score text used "certainty" phrasing without uncertainty framing.
- Risk: rank-centric interpretation detached from effect sizes and precision.
- Improvement:
  - P-score text now explicitly requires interpretation with effect sizes and uncertainty.
- File reference:
  - `synthesis-course.html:8781`

### 4) Medium: Publication-bias interpretation still too deterministic in final quiz/reversal story
- Issue: some content still framed publication bias as definitive explanation.
- Risk: causal over-attribution from asymmetry patterns.
- Improvements:
  - Final exam feedback now states pattern is consistent with small-study effects and publication bias as one plausible explanation.
  - Magnesium reversal insight now uses "likely contributed" instead of "explained."
- File references:
  - `synthesis-course.html:11312`
  - `synthesis-course.html:12340`

## Cross-Language Propagation
- Applied this V4 wording set across:
  - `synthesis-course-<lang>.html` (`ar,de,es,fr,hi,it,ja,ko,pt,ru,zh`)
  - `synthesis-course-original-<lang>.html` (`ar,de,es,fr,hi,it,ja,ko,pt,ru,zh`)
- Translation update run for affected localized files:
  - `Total replacements: 10`
- Targeted synthesis dry-run convergence:
  - `Total replacements: 0`

## Validation
- Global translation dry-run:
  - `Total replacements: 0`
- Integrity lint:
  - `OK: 297 localized files checked, no integrity issues found.`
