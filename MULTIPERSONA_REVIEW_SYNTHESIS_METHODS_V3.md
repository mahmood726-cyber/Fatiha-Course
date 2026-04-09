# Multi-Persona Review: Synthesis Methods Rigor (V3)

Date: 2026-02-19  
Scope: Follow-up editorial pass on `synthesis-course.html` + localized synthesis propagation

## Findings (ordered by severity)

### 1) High: SUCRA interpretation still implied deterministic ranking
- Risk: learners may misread ranking summaries as guaranteed treatment superiority.
- Improvement:
  - Updated SUCRA teaching text to probability framing instead of absolute "always best/worst."
- File reference:
  - `synthesis-course.html:8778`

### 2) High: Contour-enhanced funnel interpretation still overcalled publication bias
- Risk: learners may infer causal proof from asymmetry pattern alone.
- Improvement:
  - Reworded interpretation to "more plausible (not proven)" to preserve uncertainty.
- File reference:
  - `synthesis-course.html:9513`

### 3) Medium: Quiz feedback framed funnel asymmetry too narrowly as publication bias
- Risk: over-attribution to publication bias rather than broader small-study effects.
- Improvement:
  - Updated feedback to "small-study effects; publication bias is one explanation."
- File references:
  - `synthesis-course.html:6151`
  - `synthesis-course.html:6154`
  - `synthesis-course.html:6157`
  - `synthesis-course.html:6160`

### 4) Medium: Extended spaced-repetition question still used narrow publication-bias wording
- Risk: reinforces oversimplified interpretation in retrieval practice loop.
- Improvement:
  - Option/feedback now uses "possible small-study effects" and explicit multi-cause framing.
- File reference:
  - `synthesis-course.html:15071`

## Cross-Language Propagation
- Applied this V3 wording update set across:
  - `synthesis-course-<lang>.html` (`ar,de,es,fr,hi,it,ja,ko,pt,ru,zh`)
  - `synthesis-course-original-<lang>.html` (`ar,de,es,fr,hi,it,ja,ko,pt,ru,zh`)
- Translation update run for affected localized files:
  - `Total replacements: 10`
- Targeted synthesis dry-run convergence after write:
  - `Total replacements: 0`

## Validation
- Global translation dry-run:
  - `Total replacements: 0`
- Integrity lint:
  - `OK: 297 localized files checked, no integrity issues found.`
