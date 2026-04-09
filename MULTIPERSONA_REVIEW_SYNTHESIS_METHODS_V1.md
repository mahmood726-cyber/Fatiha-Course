# Multi-Persona Review: Synthesis Methods Rigor (V1)

Date: 2026-02-19  
Primary file reviewed: `synthesis-course.html`

## Personas
- Clinical epidemiologist
- Biostatistician
- Systematic review methodologist
- Guideline/HTA analyst
- Frontline clinician educator

## Findings (ordered by severity)

### 1) High: Small-study effect detection was framed too definitively
- Issue: Egger and funnel asymmetry language could be read as direct proof of publication bias, without the usual minimum-study caveat.
- Risk: Learners may overcall publication bias and misinterpret asymmetry.
- Fixed in:
  - `synthesis-course.html:3050`
  - `synthesis-course.html:6012`

### 2) High: Trim-and-fill wording implied correction rather than sensitivity analysis
- Issue: Trim-and-fill description was too deterministic.
- Risk: Learners may treat imputed studies as recovered truth.
- Fixed in:
  - `synthesis-course.html:3054`

### 3) Medium: I² thresholds were presented as hard categories
- Issue: Cutoffs lacked warning that they are context-dependent heuristics.
- Risk: Mechanical interpretation of heterogeneity.
- Fixed in:
  - `synthesis-course.html:3022`

### 4) Medium: Model-choice lesson needed stronger bias caveat
- Issue: Random effects messaging needed explicit reminder that model choice does not repair biased evidence.
- Risk: False confidence from model switching.
- Fixed in:
  - `synthesis-course.html:6002`
  - `synthesis-course.html:6023`

## Improvements Applied
- Added context-aware interpretation for I².
- Clarified Egger as asymmetry detection (not bias proof), with study-count sufficiency guidance.
- Reframed trim-and-fill as exploratory sensitivity analysis under assumptions.
- Strengthened magnesium lesson language on prespecified sensitivity analyses and robustness justification.

## Residual Recommendations
- Propagate these exact methodological wording updates to localized synthesis files if strict cross-language parity is required.
