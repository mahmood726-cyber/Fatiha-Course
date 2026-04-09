# Meta-Analysis Methods Course: Complete Build Plan

## Course Identity

**Title:** "From Question to Conclusion: A Meta-Analysis Methods Course"
**Tagline:** "Learn to conduct meta-analyses through the stories of those who got it wrong"
**Format:** Single-file HTML (matching Course 1 architecture)

---

## Pedagogical Framework

### Quranic Story Techniques (Secularized)

| Technique | Application |
|-----------|-------------|
| **The Hook** | Each module opens with a dramatic failure |
| **The Consequence** | Show what happened when methods failed |
| **The Question** | Socratic questions before teaching method |
| **The Repetition** | Key principles restated across modules |
| **The Gradual Reveal** | Complexity builds module by module |
| **The Warning** | End each module with "what to watch for" |

### Seven Principles (Methods Version)

| # | Principle | Meaning |
|---|-----------|---------|
| 1 | "The question shapes the answer" | PICO determines everything |
| 2 | "Pre-specification is protection" | Protocols prevent bias |
| 3 | "What you don't search for, you won't find" | Comprehensive searching |
| 4 | "Every number needs a source" | Data integrity |
| 5 | "Bias hides in plain sight" | Risk of bias assessment |
| 6 | "The average can lie" | Heterogeneity matters |
| 7 | "Certainty must be justified" | GRADE framework |

---

## Module Structure

### Module 0: The Opening
**Story:** The Thalidomide disaster → birth of systematic evidence synthesis
**Content:**
- Why meta-analysis exists
- The promise and peril of evidence synthesis
- Overview of the 7 Principles
**No tool** - conceptual foundation

### Module 1: The Question (PICO)
**Story:** CAST - They asked "Does the drug suppress arrhythmias?" instead of "Does it save lives?"
**Method:**
- Population definition
- Intervention specification
- Comparator selection
- Outcome hierarchy (surrogate vs patient-important)
**Tool:** PICO Builder
**Scenario:** Drug company wants you to use "biomarker response" as primary outcome

### Module 2: The Protocol
**Story:** HRT observational studies - Post-hoc subgroups and outcome switching
**Method:**
- PROSPERO registration
- Pre-specifying analyses
- Avoiding HARKing
- Protocol amendments
**Tool:** Protocol Template Generator
**Scenario:** Halfway through, you find an "interesting" subgroup not in your protocol

### Module 3: The Search
**Story:** Rosiglitazone - GSK hid cardiac trials for years
**Method:**
- Database selection (MEDLINE, EMBASE, CENTRAL)
- Grey literature (ClinicalTrials.gov, FDA, WHO ICTRP)
- Search syntax construction
- Sensitivity vs precision
**Tool:** Search Strategy Builder
**Scenario:** You find 45 published trials but 62 registered - what now?

### Module 4: The Screen
**Story:** Vitamin E meta-analyses - Different inclusion criteria, opposite conclusions
**Method:**
- Eligibility criteria operationalization
- Dual screening
- Disagreement resolution
- PRISMA flow documentation
**Tool:** PRISMA Flow Diagram Generator
**Scenario:** A borderline study could go either way - it would change your conclusion

### Module 5: The Extract
**Story:** DECREASE trials - Poldermans' fabricated data influenced guidelines for years
**Method:**
- Standardized extraction forms
- Dual extraction
- Contacting authors
- Data verification
**Tool:** Data Extraction Form Builder
**Scenario:** One author's data looks "too perfect" - I² = 0% only with their trials

### Module 6: The Assess (Risk of Bias)
**Story:** ORBITA - Without sham control, PCI's "benefit" was placebo effect
**Method:**
- RoB 2 domains
- Signaling questions
- Overall judgment
- Implications for synthesis
**Tool:** RoB 2 Assessment Interface
**Scenario:** A large trial has unclear allocation concealment - how do you rate it?

### Module 7: The Effect
**Story:** SSRI meta-analyses - Standardized vs raw mean differences told different stories
**Method:**
- Risk ratios, odds ratios, hazard ratios
- Mean differences (raw and standardized)
- Choosing the right metric
- Converting between metrics
**Tool:** Effect Size Calculator
**Scenario:** Some trials report medians, others means - can you combine them?

### Module 8: The Synthesize
**Story:** ISIS-4 magnesium - Small trials showed benefit, mega-trial showed nothing
**Method:**
- Fixed vs random effects
- Weighting schemes
- When to pool (and when not to)
- Inverse variance method
**Tool:** Forest Plot Builder
**Scenario:** Your I² is 85% - do you report a pooled estimate?

### Module 9: The Heterogeneity
**Story:** ACCORD - The average showed benefit, but some subgroups were harmed
**Method:**
- I², τ², H²
- Prediction intervals
- Subgroup analysis
- Meta-regression
**Tool:** Heterogeneity Explorer
**Scenario:** Pooled RR = 0.80 (0.70-0.91), but prediction interval crosses 1.0

### Module 10: The Bias
**Story:** Antidepressants - 94% of published trials positive vs 51% submitted to FDA
**Method:**
- Funnel plots
- Egger's test
- Trim and fill (and its limitations)
- Contour-enhanced funnels
**Tool:** Funnel Plot Builder & Analyzer
**Scenario:** Your funnel is asymmetric - is it publication bias or heterogeneity?

### Module 11: The Certainty
**Story:** SPRINT - High-quality RCT, but does it apply to your diabetic patients?
**Method:**
- GRADE domains (5 down, 3 up)
- Making judgments
- Summary of Findings tables
- Communicating uncertainty
**Tool:** GRADE Assessment Builder
**Scenario:** You have RCTs but high risk of bias and serious indirectness

### Module 12: The Report
**Story:** Reproducibility crisis - Reviews that can't be replicated
**Method:**
- PRISMA 2020 checklist
- Transparent reporting
- Data sharing
- Living reviews
**Tool:** PRISMA Checklist Generator
**Scenario:** Word limit forces cuts - what's essential to keep?

### Module 13: The Capstone
**Full guided walkthrough:** Conduct a mini meta-analysis from scratch
- Provided dataset (3-5 studies)
- Use all tools from previous modules
- Generate complete outputs
- Peer review exercise

### Module 14: Final Assessment
**Comprehensive exam** covering all modules
**Portfolio review** of artifacts created

---

## Stories Allocation

### From Evidence_Reversal_40 (Reserve Stories)

| Story | Module | Teaching Point |
|-------|--------|----------------|
| FIDELITY | 6 (RoB) | Sham surgery importance |
| Vertebroplasty | 6 (RoB) | Placebo effect |
| CSAW | 6 (RoB) | Blinding subjective outcomes |
| ASTRAL | 8 (Synthesize) | Selection bias in trials |
| SYMPLICITY | 6 (RoB) | Unblinded BP measurement |
| 6S | 9 (Heterogeneity) | Class effects |
| CHEST | 9 (Heterogeneity) | Neutral ≠ safe |
| OSCILLATE | 8 (Synthesize) | Early stopping |
| HPS2-THRIVE | 7 (Effect) | Benefit-harm tradeoff |
| ASCT | 4 (Screen) | Inclusion criteria bias |
| Shanghai BSE | 1 (Question) | Detection vs mortality outcomes |
| PREPIC2 | 7 (Effect) | Intermediate endpoints |
| SAVE | 9 (Heterogeneity) | Adherence vs ITT |

### New Stories Needed

| Module | Story Needed | Source |
|--------|--------------|--------|
| 0 | Thalidomide/Cochrane origin | Historical |
| 3 | Paroxetine Study 329 | Published |
| 4 | Vitamin E contradictory MAs | Published |
| 7 | SSRI effect size controversy | Published |
| 10 | Antidepressant publication bias | Turner 2008 |
| 12 | Irreproducible systematic reviews | Glasziou 2014 |

---

## Interactive Tools Specifications

### Tool 1: PICO Builder
```
Input: Free text descriptions
Output: Structured PICO table
Features:
- Suggests outcome hierarchy (mortality > morbidity > surrogate)
- Flags potential surrogate traps
- Generates searchable terms
```

### Tool 2: Protocol Template Generator
```
Input: PICO + methods choices
Output: PROSPERO-ready protocol draft
Features:
- Pre-specification checklist
- Analysis plan template
- Amendment log
```

### Tool 3: Search Strategy Builder
```
Input: PICO terms
Output: Database-specific search strings
Features:
- MEDLINE/EMBASE/CENTRAL syntax
- Boolean operators
- MeSH/Emtree suggestions
- Sensitivity calculator
```

### Tool 4: PRISMA Flow Generator
```
Input: Numbers at each stage
Output: Visual PRISMA 2020 flow diagram
Features:
- Exportable SVG
- Reason tracking for exclusions
```

### Tool 5: Data Extraction Form
```
Input: Study characteristics
Output: Standardized extraction table
Features:
- Dual entry comparison
- Discrepancy flagging
- Export to CSV
```

### Tool 6: RoB 2 Assessment
```
Input: Signaling questions
Output: Traffic light visualization
Features:
- Domain-by-domain assessment
- Overall judgment algorithm
- Justification prompts
```

### Tool 7: Effect Size Calculator
```
Input: Raw data (2x2, means/SDs, etc.)
Output: Effect sizes with CIs
Features:
- RR, OR, HR conversion
- MD, SMD calculation
- Variance estimation
```

### Tool 8: Forest Plot Builder
```
Input: Studies with effects + CIs
Output: Interactive forest plot
Features:
- Fixed/random effects toggle
- Drag to reorder
- Subgroup capability
- Export as image
```

### Tool 9: Heterogeneity Explorer
```
Input: Forest plot data
Output: I², τ², prediction interval
Features:
- Visual explanation of each metric
- "What if" scenario testing
- Prediction interval visualization
```

### Tool 10: Funnel Plot Builder
```
Input: Effect sizes + SEs
Output: Funnel plot with tests
Features:
- Egger's test
- Contour enhancement
- Trim-and-fill visualization
```

### Tool 11: GRADE Builder
```
Input: Evidence profile
Output: Summary of Findings table
Features:
- Domain-by-domain rating
- Footnote generator
- Certainty statement generator
```

### Tool 12: PRISMA Checklist
```
Input: Manuscript sections
Output: Completed checklist
Features:
- Item-by-item guidance
- Location tracking
- Completeness score
```

---

## Gamification System

### Points
| Action | Points |
|--------|--------|
| Complete module content | 100 |
| Tool exercise completed | 50 |
| Scenario correct | 30 |
| Quiz perfect score | 50 |
| Capstone milestone | 200 |

### Badges
| Badge | Requirement |
|-------|-------------|
| Question Crafter | Complete PICO for 5 topics |
| Search Master | Build 3 comprehensive searches |
| Bias Detective | Complete 10 RoB assessments |
| Forest Ranger | Build 5 forest plots |
| GRADE Graduate | Rate certainty for 5 outcomes |
| Methods Master | Complete all modules |
| Capstone Champion | Finish capstone project |

### Levels
1. Novice (0-500)
2. Apprentice (500-1500)
3. Practitioner (1500-3000)
4. Methodologist (3000-5000)
5. Master (5000+)

---

## Technical Architecture

### File Structure
- Single HTML file (~600-800KB)
- Embedded CSS (dark theme matching Course 1)
- Embedded JavaScript (all tools)
- No external dependencies except fonts

### Data Persistence
- localStorage for progress
- Export/import for portfolio
- Tool outputs saved

### Responsive Design
- Desktop-first (tools need space)
- Tablet-compatible
- Mobile: content only, tools desktop-recommended

---

## Build Sequence

### Phase 1: Core Structure
1. HTML shell with navigation
2. CSS styling (match Course 1 aesthetic)
3. Module content framework
4. Basic JavaScript architecture

### Phase 2: Content
5. Write all module narratives
6. Create scenarios for each module
7. Write quiz questions
8. Develop misconception challenges

### Phase 3: Tools
9. PICO Builder
10. Search Builder
11. Forest Plot Builder (most complex)
12. Other calculators
13. GRADE Builder

### Phase 4: Gamification
14. Points system
15. Badge system
16. Progress dashboard
17. Persistence

### Phase 5: Polish
18. Testing
19. Edge cases
20. Performance optimization

---

## Success Metrics

| Metric | Target |
|--------|--------|
| Module completion | 80%+ |
| Tool usage | 70%+ use each tool |
| Capstone completion | 50%+ |
| Return rate (7-day) | 60%+ |
| Artifact quality | Peer-rated 4/5 |

---

## Timeline Estimate

- Phase 1: Core structure (this session)
- Phase 2: Content (this session)
- Phase 3: Tools (partial this session)
- Phase 4-5: Follow-up session

---

*Plan created: February 2026*
*Target: Complete functional course in single HTML file*
