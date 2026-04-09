# Multi-Persona Review V2: Fatiha Course Collection & Gateway

**Date:** 2026-02-04
**Scope:** Full review of updated gateway, rewritten umbrella reviews course, and all 27 active HTML files
**Review conducted after:** Fix round 2 (mobile hamburger menus, accessibility, Plotly fallback, CAST rename, umbrella rewrite, ZIP rebuild)

---

## Executive Summary

| Category | Score | Change from V1 |
|----------|-------|-----------------|
| Gateway: HTML/CSS Technical Quality | 8/10 | +1 |
| Gateway: JavaScript Quality | 7/10 | +1 |
| Gateway: Accessibility (WCAG 2.1 AA) | 6/10 | +2 |
| Gateway: Responsive Design | 8/10 | +1 |
| Gateway: Content Accuracy | 9/10 | +1 |
| Gateway: Cross-Browser | 7/10 | -- |
| Gateway: Missing Features / Polish | 6/10 | +1 |
| Umbrella Reviews: Content Accuracy | 9/10 | NEW |
| Umbrella Reviews: Technical Integrity | 8/10 | NEW |
| Umbrella Reviews: Course Differentiation | 10/10 | NEW |
| Umbrella Reviews: Design & UX | 9/10 | NEW |
| Umbrella Reviews: Accessibility | 9/10 | NEW |
| Collection: Mobile Navigation | 8/10 | +4 |
| Collection: Back-to-Gateway Links | 10/10 | +10 |
| Collection: Plotly Fallback | 10/10 | +10 |
| Collection: Accessibility Baseline | 5/10 | +2 |
| Collection: File Naming | 7/10 | +3 |
| Collection: Design System Consistency | 7/10 | -- |
| Collection: Cross-Course Issues | 8/10 | +3 |
| Collection: VERSION.txt | 7/10 | NEW |
| **Overall Weighted Score** | **7.8/10** | **+1.1** |

**Previous overall score:** 6.7/10
**Current overall score:** 7.8/10
**Improvement:** +1.1 points (+16%)

---

## Persona 1: Front-End Engineer (Gateway Review)

### Strengths (what improved since V1)
- Navy/gold design system now matches course files perfectly
- Search + filter composition bug FIXED (single `renderCards()` function with `activeCategory` state)
- ARIA tablist pattern with arrow key navigation (Home/End per WAI-ARIA)
- `minmax(min(320px, 100%), 1fr)` grid prevents all mobile overflow
- Print styles included
- "/" keyboard shortcut for search focus

### Remaining Issues

| ID | Severity | Finding |
|----|----------|---------|
| GW-1 | Critical | ARIA tablist pattern is semantically incorrect -- no `role="tabpanel"` elements. Should use `role="toolbar"` or `role="radiogroup"` instead. Missing roving tabindex. |
| GW-2 | Critical | No skip-to-main-content link. WCAG 2.4.1 (Level A) failure. |
| GW-3 | Major | `.meta` text contrast ~2.8:1 (needs 4.5:1). Fix: change `rgba(255,255,255,0.4)` to `rgba(255,255,255,0.62)`. |
| GW-4 | Major | `.search-hint` contrast ~2.2:1. Fix: change `rgba(255,255,255,0.3)` to `rgba(255,255,255,0.55)`. |
| GW-5 | Major | Dead code on line 719 (`mainCards` variable declared but never used). |
| GW-6 | Major | Archive cards included in `visibleCount`, inflating "X courses found" announcement. |
| GW-7 | Major | No search clear ("X") button. No Escape key handler. |
| GW-8 | Minor | No debouncing on screen reader announcements (rapid typing causes noise). |
| GW-9 | Minor | Search clears silently on category change without user feedback. |
| GW-10 | Minor | No accent-insensitive search for French course names. |
| GW-11 | Minor | Learning path section sits outside ARIA landmarks (between nav and main). |
| GW-12 | Minor | No URL state persistence (filters/search lost on refresh). |
| GW-13 | Minor | Touch targets on filter tabs (~30px) and path steps (~28px) below 44px WCAG recommendation. |
| GW-14 | Nit | No `<link rel="preconnect">` for Google Fonts. |
| GW-15 | Nit | Emoji search icon (CSS `\1F50D`) renders inconsistently cross-platform. |
| GW-16 | Nit | No favicon, no Open Graph meta tags, no `<meta name="theme-color">`. |
| GW-17 | Nit | Missing `lang="fr"` on French course card content. |

---

## Persona 2: Evidence-Based Medicine Methodologist (Umbrella Reviews Course)

### Content Accuracy Assessment

All 7 modules are methodologically accurate and cover the essential umbrella review curriculum:

| Module | Title | Topic | Accuracy |
|--------|-------|-------|----------|
| 1 | The Canopy | Definition, when to choose umbrella review | ACCURATE |
| 2 | The Harvest | Search strategy for SRs, eligibility, PROSPERO | ACCURATE |
| 3 | The Lens | AMSTAR 2: 16 items, 7 critical domains, confidence ratings | ACCURATE |
| 4 | The Overlap | CCA method (Pieper 2014), thresholds 0-5/6-10/11-15/>15% | ACCURATE |
| 5 | The Synthesis | Narrative vs quantitative, GRADE independence, discordance | ACCURATE |
| 6 | The Map | Evidence mapping, harvest plots, gap identification | ACCURATE |
| 7 | The Report | PRIOR statement, 5 common pitfalls, ring-structure closure | ACCURATE |

### Specific Validations
- AMSTAR 2 critical domains correctly listed (all 7 per Shea et al. 2017)
- Confidence rating scale accurate (High/Moderate/Low/Critically Low)
- CCA thresholds match Pieper et al. 2014 exactly
- GRADE approach correctly advises independent application (not averaging)
- PRIOR reporting statement correctly referenced
- All 21 decision scenarios have exactly one correct answer; feedback is accurate
- Ring structure successfully returns Module 7 to Module 1's guideline panel scenario
- Refrains are thematically consistent; Modules 1 and 7 share the same closing refrain

### Differentiation from Living Reviews: COMPLETE (10/10)
Zero content overlap. Different module names, stories, decision scenarios, and methodological focus. CSS and gamification engine are byte-identical (as intended). localStorage keys are distinct (`umbrellaReviewGame` vs `livingReviewGame`).

### Minor Methodological Notes
- Module 1 stats ("8000+ SRs published yearly", "30-50% overlap") labeled as approximate but lack specific citations
- CCA formula described in prose rather than mathematical notation (acceptable for HTML format)
- No Module 1 completion badge (by design, but could add one)

---

## Persona 3: Accessibility Specialist (Collection-Wide)

### What Improved Since V1
- Skip-links added to 3 courses (truthcert, truthcert-fr, ai-meta-analysis)
- `role="navigation"` and `aria-label` added to those same 3 courses
- Keyboard-focusable module items with `tabindex`, `role="button"`, `onkeydown` handlers
- Umbrella reviews course has full ARIA coverage (inherited from template)

### Current State

| Feature | Files with it | Files without it | Coverage |
|---------|--------------|-----------------|----------|
| Skip-links | 19 of 27 | 8 (all 4 DTA, advanced-meta, writing-course, CAST, gateway) | 70% |
| `role="navigation"` | ~15 of 27 | ~12 | 56% |
| `aria-label` (any) | 27 of 27 | 0 | 100% |
| `aria-label` (good density) | ~15 of 27 | ~12 (minimal: 1-3 labels) | 56% |
| Mobile hamburger | 25 of 25 sidebar courses | 0 | 100% |
| Reduced motion support | ~12 of 27 | ~15 | 44% |
| Focus-visible styles | ~12 of 27 | ~15 | 44% |

### Priority Fixes

| ID | Severity | Files | Fix |
|----|----------|-------|-----|
| A11Y-1 | Medium | 8 files lacking skip-links | Add skip-link pattern from umbrella course template |
| A11Y-2 | Medium | ~12 files lacking `role="navigation"` | Add to sidebar `<nav>` elements |
| A11Y-3 | Low | Collection-wide | Standardize minimum aria-label baseline |

---

## Persona 4: Gamification Designer (Umbrella Reviews Course)

### XP Economy Analysis

| Module | Completion XP | Decision XP | Decisions | Total Possible |
|--------|--------------|-------------|-----------|----------------|
| 1 (Canopy) | 140 | 25 each | 3 | 215 |
| 2 (Harvest) | 150 | 25 each | 3 | 225 |
| 3 (Lens) | 160 | 25 each | 3 | 235 |
| 4 (Overlap) | 160 | 25 each | 3 | 235 |
| 5 (Synthesis) | 170 | 25 each | 3 | 245 |
| 6 (Map) | 170 | 25 each | 3 | 245 |
| 7 (Report) | 190 | 35 each | 3 | 295 |
| **Total** | **1140** | | **21** | **~1695** |

**Level 8 threshold:** 1700 XP
**Max achievable:** ~1695 XP (if all decisions correct)
**Assessment:** Very tight -- a learner who gets even one decision wrong cannot reach level 8. Consider raising Module 7's completion XP from 190 to 200, or reducing the level 8 threshold to 1650.

### Badge Mapping: VERIFIED CORRECT

All 12 badges have unique IDs and correct awarding triggers. Module-completion badges (2-7) map correctly. Generic badges (first_scenario, perfect_5, decision_maker, finisher, streak_3, streak_7) all fire at correct thresholds.

### Level Titles: THEMATICALLY STRONG

Review Reader -> Search Scout -> Quality Assessor -> Overlap Analyst -> Evidence Synthesizer -> Gap Mapper -> Reporting Expert -> Umbrella Master

Progression follows the course arc. Each title maps to the module that unlocks that level.

### Issue
- Sidebar HTML hardcodes "SK" / "Seed Keeper" (living reviews defaults). Overwritten by JS on load, but may flash briefly. Should be "RR" / "Review Reader".

---

## Persona 5: DevOps / Build Engineer (Collection Health)

### File Inventory

| Type | Count | Status |
|------|-------|--------|
| Active course HTML | 26 | Clean |
| Gateway HTML | 1 | Clean |
| VERSION.txt | 1 | Minor inaccuracy |
| Backup HTML | 8 | Should archive/remove |
| Backup Python | 2 | Should archive/remove |
| Documentation .md | 20 | Dev artifacts |
| ZIP bundle | 1 (0.92 MB, 28 files) | Clean (no backups) |

### Design System Consistency

All 27 active HTML files share the same design system EXCEPT:
- `publication-bias-detective.html`: uses `--navy: #1a1a2e` (vs standard `#1E2761`) and `--cream: #f5f5f0` (vs `#FAF8F5`)

All files use the same Google Fonts (Cormorant Garamond + Source Sans Pro). Only `ipd-meta-analysis-course.html` has offline `@font-face` fallback.

### Cross-Course Verification

| Check | Result |
|-------|--------|
| All 26 gateway links resolve to real files | PASS |
| No broken internal references | PASS |
| Umbrella != Living reviews content | PASS |
| DTA v3 title = "V3", DTA v4 title = "V4" | PASS |
| All courses link back to gateway | PASS |
| All Plotly courses have offline fallback | PASS |
| All sidebar courses have mobile nav | PASS |

### VERSION.txt Issues
- States "25 courses" but actual count is 26 (or 23 current + 3 archived)
- Does not acknowledge remaining known issues

---

## Persona 6: Technical Writer (Umbrella Course Pedagogy)

### Module Flow Assessment: EXCELLENT

The 7-module arc follows a natural research workflow:
1. **Why** (The Canopy) -- motivation and definition
2. **Find** (The Harvest) -- search and selection
3. **Assess** (The Lens) -- quality appraisal
4. **Check** (The Overlap) -- overlap detection
5. **Combine** (The Synthesis) -- evidence synthesis
6. **Map** (The Map) -- visualization and gaps
7. **Report** (The Report) -- standards and closure

Each module follows a consistent internal pattern: title -> objectives -> story -> concept/stats -> checklist -> 3 decisions -> refrain. This predictability helps learners focus on content rather than navigation.

### Ring Structure: PRESENT AND EFFECTIVE

Module 1 opens with five conflicting reviews confusing a guideline panel. Module 7 closes by revisiting the same panel, now equipped with umbrella review results. The shared refrain ("When reviews multiply, the umbrella gathers them") anchors both ends.

### Decision Scenario Quality: HIGH

All 21 scenarios present realistic methodological dilemmas. Feedback for incorrect answers educates rather than just corrects. The final Module 7 decision integrates quality, concordance, and overlap assessment into a single integrative judgment -- an excellent capstone.

---

## All Issues Summary (by priority)

### Critical (2)
1. Gateway: Incorrect ARIA tablist pattern (no tabpanels, no roving tabindex)
2. Gateway: Missing skip-to-main-content link

### Major (7)
3. Gateway: `.meta` text contrast ~2.8:1
4. Gateway: `.search-hint` contrast ~2.2:1
5. Gateway: Dead `mainCards` code
6. Gateway: Archive cards inflate visible count
7. Gateway: No search clear button / Escape handler
8. Collection: 8 courses missing skip-links
9. Collection: ~12 courses missing `role="navigation"`

### Medium (2)
10. `publication-bias-detective.html` divergent color palette
11. Umbrella course: missing `gold-bg` CSS class (shared template bug in both umbrella + living)

### Minor (10)
12. Gateway: No debounce on SR announcements
13. Gateway: Search clears on category change
14. Gateway: No accent-insensitive search
15. Gateway: Learning path outside landmarks
16. Gateway: No URL state persistence
17. Gateway: Undersized touch targets
18. Umbrella: Sidebar hardcodes "SK"/"Seed Keeper" defaults
19. Umbrella: XP cap ~1695 vs level 8 threshold 1700 (very tight)
20. Collection: `fatiha-course.html` uses different toggle function name
21. VERSION.txt course count off by 1

### Nit (6)
22. Gateway: No font preconnect hints
23. Gateway: Emoji search icon inconsistent
24. Gateway: No favicon / OG tags / theme-color
25. Gateway: Missing `lang="fr"` on French card
26. Collection: 26/27 files lack offline font fallback
27. Collection: 8 backup files + 2 backup scripts in directory

---

## Score Comparison: V1 vs V2

| Category | V1 Score | V2 Score | Delta |
|----------|----------|----------|-------|
| Overall | 6.7 | 7.8 | +1.1 |
| Gateway average | 5.7 | 7.3 | +1.6 |
| Umbrella Reviews | N/A (duplicate) | 9.0 | NEW |
| Collection average | 5.5 | 7.4 | +1.9 |

### What was fixed in V2
1. Umbrella reviews course: fully rewritten with 7 original modules (was byte-for-byte duplicate)
2. Mobile navigation: added to 11 courses that lacked it (now 100% coverage)
3. Back-to-gateway links: added to all 25 course files (was 0%)
4. Plotly offline fallback: added to all 4 Plotly courses (was 0%)
5. Accessibility: skip-links + ARIA added to 3 courses (truthcert, truthcert-fr, ai-meta)
6. CAST file renamed to kebab-case
7. DTA v3/v4 titles fixed (were swapped)
8. Gateway completely redesigned (search, filters, categories, descriptions, learning path)
9. VERSION.txt added
10. Clean ZIP rebuilt (0.92 MB, 28 files, no backups)

### What remains for V3
1. Fix gateway ARIA pattern (tablist -> toolbar/radiogroup)
2. Add skip-links to 8 remaining files
3. Add `role="navigation"` to ~12 remaining files
4. Fix contrast ratios on gateway (`.meta`, `.search-hint`)
5. Add `gold-bg` CSS class to umbrella + living courses
6. Fix sidebar default text in umbrella course
7. Align publication-bias-detective colors to standard palette
8. Clean up backup files from directory
