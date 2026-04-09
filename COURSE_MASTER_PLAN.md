# THE SYNTHESIS META-ANALYSIS COURSE
## Master Implementation Plan

**Vision:** Create the world's best meta-analysis course in a single HTML file, using narrative storytelling patterns—signs, illustrative stories, repetition, questions that provoke reflection—anchored in real evidence reversals that changed medicine.

---

## PART I: PHILOSOPHICAL FOUNDATIONS

### The Synthesis Teaching Method

The course follows a **seven-fold path** (like the seven verses), where each module:

1. **Opens with stillness** — A moment of centering before new knowledge
2. **Presents a sign** — A real-world observation that seemed true
3. **Reveals the hidden assumption** — What was believed without testing
4. **Shows the reversal** — How rigorous methods exposed the truth
5. **Teaches the method** — The technique that would have prevented the error
6. **Provides practice** — Interactive exercises with real data
7. **Seals with retrieval** — Three questions that cement understanding

### Narrative Principles

- **No invented characters or quotes** — Only real trials, real investigators, real numbers
- **The refrain returns** — Key phrases repeated across modules for memory
- **Questions before answers** — Socratic discovery, not lecture
- **Signs before methods** — Story creates need for technique
- **Minimalism** — ≤15 words per concept slide, one chart per reversal
- **Provenance always visible** — Every number traceable to source

---

## PART II: COURSE ARCHITECTURE

### Module Structure (12 Core Modules + Capstone)

```
┌─────────────────────────────────────────────────────────────────┐
│  MODULE 0: THE OPENING                                          │
│  "Not every bright sign is guidance"                            │
│  - Why meta-analysis exists                                     │
│  - When NOT to pool                                             │
│  - The hierarchy of evidence                                    │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│  MODULE 1: THE QUESTION (PICO)                                  │
│  Evidence Reversal: CAST Trial (antiarrhythmics)                │
│  - Surrogate vs hard endpoints                                  │
│  - Framing the answerable question                              │
│  - Population, Intervention, Comparator, Outcome                │
│  Interactive: PICO Builder Tool                                 │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│  MODULE 2: THE PROTOCOL                                         │
│  Evidence Reversal: Hormone Replacement Therapy                 │
│  - Pre-specification prevents fishing                           │
│  - PROSPERO registration                                        │
│  - Amendment discipline                                         │
│  Interactive: Protocol Builder (MetaSprint integration)         │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│  MODULE 3: THE SEARCH                                           │
│  Evidence Reversal: Rosiglitazone/RECORD (missing trials)       │
│  - Comprehensive is survival                                    │
│  - PRESS checklist                                              │
│  - Grey literature matters                                      │
│  Interactive: CT.gov Search Builder (from ctgov-strategies)     │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│  MODULE 4: THE SCREENING                                        │
│  Evidence Reversal: Vioxx (selective reporting)                 │
│  - Dual screening prevents bias                                 │
│  - PRISMA flow                                                  │
│  - Calibration and adjudication                                 │
│  Interactive: Screening Simulator (from Screenr)                │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│  MODULE 5: THE EXTRACTION                                       │
│  Evidence Reversal: Beta-blockers in surgery (DECREASE trials)  │
│  - Provenance for every number                                  │
│  - Dual extraction with disagreement                            │
│  - Effect size calculation                                      │
│  Interactive: Extraction Form + Effect Size Calculator          │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│  MODULE 6: THE BIAS ASSESSMENT                                  │
│  Evidence Reversal: Aprotinin (BART trial)                      │
│  - Risk of Bias 2.0                                             │
│  - ROBINS-I for observational                                   │
│  - Traffic light visualization                                  │
│  Interactive: RoB Assessment Tool                               │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│  MODULE 7: THE SYNTHESIS                                        │
│  Evidence Reversal: Magnesium in MI (ISIS-4 vs small trials)    │
│  - Fixed vs Random effects                                      │
│  - The 8 tau² estimators                                        │
│  - Forest plot interpretation                                   │
│  Interactive: Meta-Analysis Calculator + Forest Plot Generator  │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│  MODULE 8: THE HETEROGENEITY                                    │
│  Evidence Reversal: Intensive glucose control (ACCORD)          │
│  - I², τ², prediction intervals                                 │
│  - When not to pool                                             │
│  - Subgroup analysis credibility (ICEMAN)                       │
│  Interactive: Heterogeneity Explorer                            │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│  MODULE 9: THE HIDDEN STUDIES                                   │
│  Evidence Reversal: Reboxetine (EMA re-analysis)                │
│  - Publication bias                                             │
│  - Egger, Peters, Trim-and-fill                                 │
│  - Funnel plot interpretation                                   │
│  Interactive: Publication Bias Detector                         │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│  MODULE 10: THE CERTAINTY                                       │
│  Evidence Reversal: Early surfactant (Cochrane update)          │
│  - GRADE framework                                              │
│  - Summary of Findings tables                                   │
│  - From evidence to recommendation                              │
│  Interactive: GRADE Assessment Builder                          │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│  MODULE 11: THE LIVING REVIEW                                   │
│  Evidence Reversal: COVID-19 treatments (rapid evolution)       │
│  - Living systematic reviews                                    │
│  - Trial Sequential Analysis                                    │
│  - When to update                                               │
│  Interactive: Living Review Dashboard                           │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│  MODULE 12: THE ADVANCED METHODS                                │
│  Network Meta-Analysis, Dose-Response, IPD, DTA                 │
│  - When standard pairwise isn't enough                          │
│  - Treatment ranking (SUCRA)                                    │
│  - Dose-response curves                                         │
│  Interactive: NMA Network Builder + Dose-Response Modeler       │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│  CAPSTONE: THE COMPLETE REVIEW                                  │
│  Full 40-day sprint simulation using MetaSprint                 │
│  - Protocol to publication                                      │
│  - Audit trail and reproducibility                              │
│  - TruthCert certification                                      │
└─────────────────────────────────────────────────────────────────┘
```

---

## PART III: EVIDENCE REVERSALS LIBRARY

### Module 1: CAST Trial (1989)
- **What was believed:** Suppressing PVCs after MI saves lives
- **What was hidden:** Surrogate endpoint assumed causal
- **What changed:** 50,000 excess deaths/year stopped
- **Method taught:** PICO framework, hard vs surrogate endpoints

### Module 2: Hormone Replacement Therapy (2002)
- **What was believed:** HRT prevents heart disease in postmenopausal women
- **What was hidden:** Observational studies confounded by healthy user bias
- **What changed:** WHI RCT showed increased CV risk
- **Method taught:** Protocol pre-specification, RCT necessity

### Module 3: Rosiglitazone (2007)
- **What was believed:** TZDs are safe for diabetics
- **What was hidden:** Unpublished trials showing CV harm
- **What changed:** Nissen meta-analysis forced FDA action
- **Method taught:** Comprehensive search, grey literature

### Module 4: Vioxx (2004)
- **What was believed:** COX-2 inhibitors are GI-safer alternatives
- **What was hidden:** CV events selectively not reported in VIGOR
- **What changed:** 88,000+ heart attacks, drug withdrawn
- **Method taught:** Screening for selective reporting, PRISMA

### Module 5: DECREASE Trials (2011)
- **What was believed:** Beta-blockers reduce perioperative mortality
- **What was hidden:** Fabricated data in Don Poldermans trials
- **What changed:** Guidelines retracted, mortality may have increased
- **Method taught:** Data extraction with verification, provenance

### Module 6: Aprotinin/BART (2008)
- **What was believed:** Aprotinin safely reduces surgical bleeding
- **What was hidden:** Observational studies had residual confounding
- **What changed:** BART RCT stopped for increased mortality
- **Method taught:** Risk of Bias assessment, RCT vs observational

### Module 7: Magnesium in MI (1995)
- **What was believed:** Small trials showed 50% mortality reduction
- **What was hidden:** Small-study effects, publication bias
- **What changed:** ISIS-4 (58,000 patients) showed no benefit
- **Method taught:** Fixed vs random effects, large trial dominance

### Module 8: ACCORD Trial (2008)
- **What was believed:** Tighter glucose control always better
- **What was hidden:** Heterogeneity in patient response
- **What changed:** Intensive control increased mortality in some
- **Method taught:** Heterogeneity, subgroup credibility

### Module 9: Reboxetine (2010)
- **What was believed:** Effective antidepressant based on published trials
- **What was hidden:** 74% of patient data never published
- **What changed:** Re-analysis showed no benefit vs placebo
- **Method taught:** Publication bias detection, funnel plots

### Module 10: Early Surfactant (2012)
- **What was believed:** Prophylactic surfactant best for preterm infants
- **What was hidden:** Trials done before CPAP became standard
- **What changed:** Updated MA showed selective approach better
- **Method taught:** GRADE, evidence certainty, updating

### Module 11: COVID-19 Hydroxychloroquine (2020)
- **What was believed:** Early observational studies suggested benefit
- **What was hidden:** Confounding, immortal time bias
- **What changed:** RCTs showed no benefit, potential harm
- **Method taught:** Living reviews, rapid updating

### Module 12: Network Meta-Analysis Examples
- **Antipsychotics (Leucht 2013):** 15 drugs compared via NMA
- **Blood pressure targets:** Dose-response relationships
- **Diagnostic tests:** Bivariate models for sensitivity/specificity

---

## PART IV: INTERACTIVE COMPONENTS TO EXTRACT

### From Screenr (rayyanreplacement/screenr.html)
```javascript
// Extract these components:
1. Record screening interface (decision buttons, keyboard shortcuts)
2. Risk of Bias 2.0 assessment form
3. GRADE profiling system
4. Meta-analysis calculator (calculateMetaAnalysis function)
5. Forest plot SVG renderer
6. Funnel plot with Egger's test
7. Publication bias methods (trim-and-fill, PET-PEESE)
8. Inter-rater reliability (Cohen's Kappa)
```

### From Truthcert1 (app.js - 20,033 lines)
```javascript
// Extract these validated functions:
1. Effect size calculators (OR, RR, RD, SMD, MD)
2. All 8 tau² estimators (DL, REML, ML, PM, HS, SJ, HE, EB)
3. Heterogeneity metrics (I², τ², Q, H², prediction intervals)
4. HKSJ adjustment
5. Publication bias tests (Egger, Peters, Harbord)
6. Trim-and-fill algorithm
7. Leave-one-out sensitivity analysis
8. Influence diagnostics (DFBETAS, Cook's D)
9. Forest plot generation
10. Funnel plot generation
```

### From MetaSprint (meta-sprint-v3_0-2.html)
```javascript
// Integrate the full 40-day sprint framework:
1. DoD Gates (A through E)
2. Checklist system with story hints
3. Red-team QA framework
4. Protocol deviation logging
5. Audit trail generation
6. Timeline tracking
7. PRISMA template
8. GRADE assessment interface
```

### From ctgov-search-strategies
```python
// Convert to JavaScript:
1. PRESS validator (6 elements)
2. PICO search generator
3. Boolean optimizer
4. Database translator (PubMed ↔ Embase ↔ CT.gov)
5. Strategy performance metrics
6. Grey literature checklist
```

### From HTA-oman (engine modules)
```javascript
// Extract advanced methods:
1. Network meta-analysis (nma.js)
2. Bayesian MCMC (bayesianMCMC.js)
3. Publication bias selection models (Andrews-Kasy, Copas)
4. EVSI/EVPI calculations
5. Survival analysis methods
```

### From dose-response-meta-analysis.html
```javascript
// Extract dose-response methods:
1. GLS (Greenland-Longnecker) estimator
2. Spline fitting (linear, quadratic, cubic)
3. Dose-response curve visualization
4. Sensitivity analysis
```

### From lec_phase0_project (statistics.py → JavaScript)
```javascript
// Convert these methods:
1. ICEMAN credibility assessment
2. Subgroup analysis with interaction testing
3. Prediction interval calculation
4. Enhanced funnel plots with contours
```

---

## PART V: TECHNICAL ARCHITECTURE

### Single HTML File Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>The Synthesis Meta-Analysis Course</title>
    <style>
        /* ~15KB compressed CSS */
        /* Design system with Cormorant Garamond + Source Sans Pro */
        /* Navy, gold, cream color scheme */
        /* Responsive, accessible */
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav id="course-nav">
        <!-- Module selector -->
        <!-- Progress tracker -->
    </nav>

    <!-- Main Content Area -->
    <main id="course-content">
        <!-- Dynamically loaded module content -->
    </main>

    <!-- Interactive Tools Panel -->
    <aside id="tools-panel">
        <!-- Embedded calculators and simulators -->
    </aside>

    <!-- Scripts -->
    <script>
        // ~200KB compressed JavaScript
        // All statistical functions from Truthcert1
        // All interactive components from Screenr
        // MetaSprint workflow engine
        // Module content and navigation
    </script>
</body>
</html>
```

### Estimated Size
- HTML structure: ~20KB
- CSS (compressed): ~15KB
- JavaScript (compressed): ~200KB
- Embedded data/content: ~100KB
- **Total: ~335KB** (loads instantly, works offline)

---

## PART VI: LEARNING FEATURES

### 1. Retrieval Practice System
Every module ends with the same three questions:
1. **What was believed?** (prior assumption)
2. **What was hidden?** (methodological flaw)
3. **What changed?** (evidence reversal)

Plus one **misconception check** (true/false with explanation).

### 2. Spaced Repetition
- Day 2 recap quiz after each module
- Day 10 interleaved review mixing prior episodes
- Cumulative final assessment

### 3. Progressive Disclosure
- Beginner mode: Simplified interface, guided workflows
- Intermediate mode: Full tools, some automation
- Expert mode: Raw data, all options exposed

### 4. Provenance Tracking
Every calculation shows:
- Input data source (trial name, PMID, table reference)
- Formula applied
- Intermediate steps
- Final result with confidence interval

### 5. Code Export
Students can export their analyses as:
- R code (metafor package)
- Python code (statsmodels)
- Reproducible capsule for verification

---

## PART VII: IMPLEMENTATION PHASES

### Phase 1: Foundation (Week 1)
- [ ] Create base HTML structure with navigation
- [ ] Implement CSS design system
- [ ] Extract and validate core statistical functions from Truthcert1
- [ ] Build Module 0 (The Opening) and Module 1 (CAST story)

### Phase 2: Core Methods (Weeks 2-3)
- [ ] Modules 2-6: Protocol through Bias Assessment
- [ ] Integrate PICO builder from ctgov-search-strategies
- [ ] Integrate screening simulator from Screenr
- [ ] Integrate RoB assessment tool

### Phase 3: Synthesis (Weeks 3-4)
- [ ] Modules 7-9: Synthesis through Publication Bias
- [ ] Full meta-analysis calculator
- [ ] Forest plot generator
- [ ] Funnel plot with bias detection

### Phase 4: Advanced (Weeks 4-5)
- [ ] Modules 10-12: GRADE through Advanced Methods
- [ ] Network meta-analysis tool
- [ ] Dose-response modeler
- [ ] Living review dashboard

### Phase 5: Integration (Week 5-6)
- [ ] Capstone: Full MetaSprint integration
- [ ] TruthCert certification system
- [ ] Assessment and grading system
- [ ] Final testing and optimization

---

## PART VIII: QUALITY STANDARDS

### Validation Requirements
1. All statistical functions validated against R metafor (tolerance <0.001)
2. All evidence reversals verified against primary sources
3. All interactive tools tested with known datasets
4. Accessibility: WCAG 2.1 AA compliance
5. Performance: <3s load time on 3G connection

### Pedagogical Standards
1. Every module reviewed by methods expert
2. Every story verified against published literature
3. Every exercise tested with naive learners
4. Clear learning objectives with measurable outcomes
5. Assessment aligned with objectives

---

## PART IX: SOURCE FILES REFERENCE

### Primary Sources to Extract From:

| Component | Source File | Lines to Extract |
|-----------|-------------|------------------|
| CAST Story | Synthesis course/CAST_WhenCertaintyKills.html | Full file (template) |
| Statistical Core | Truthcert1/app.js | Lines 1-5000 |
| Screening UI | rayyanreplacement/screenr.html | Lines 2400-3500 |
| RoB Assessment | rayyanreplacement/screenr.html | Lines 8000-9000 |
| Meta-analysis Calc | rayyanreplacement/screenr.html | Lines 5312-5550 |
| Forest Plots | Truthcert1/app.js | Lines 6000-7000 |
| MetaSprint Core | metasprint/meta-sprint-v3_0-2.html | Lines 500-2500 |
| Search Builder | ctgov-search-strategies/*.py | Convert to JS |
| NMA Engine | HTA-oman/src/engine/nma.js | Full file |
| Dose-Response | dose-response-meta-analysis.html | Lines 1-3000 |
| GRADE System | rayyanreplacement/screenr.html | Lines 3100-3200 |
| HKSJ/Advanced | lec_phase0_project/src/lec/metaengine/statistics.py | Convert to JS |

---

## PART X: THE SEVEN REFRAINS

These phrases recur throughout the course, building memory:

1. **"Not every bright sign is guidance."** — Opening
2. **"Methods protect patients from our confidence."** — CAST
3. **"What was hidden in plain sight?"** — Before each reversal
4. **"The number without provenance is not a number."** — Extraction
5. **"Heterogeneity is a message, not noise."** — Synthesis
6. **"Absence of evidence is not evidence of absence."** — Publication bias
7. **"Certainty must be earned, not assumed."** — GRADE

---

## NEXT STEPS

1. **Confirm this plan** — Review and approve overall structure
2. **Begin Phase 1** — Create base HTML with CAST module as template
3. **Extract statistical functions** — Port Truthcert1 core to standalone JS
4. **Build module by module** — Following the phase timeline
5. **Validate continuously** — Test each component against R benchmarks

---

*"We have made the path clear. Now walk it."*
