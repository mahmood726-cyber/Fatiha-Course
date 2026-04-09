# Multi-Persona Review: Fatiha Course Collection & Gateway

**Date:** 2026-02-04
**Scope:** Full review of the gateway `index.html` and all 23 primary HTML training courses
**Total codebase:** ~85,700 lines across 23 course files + 447-line gateway

---

## Reviewer Panel

| Persona | Focus Area |
|---------|-----------|
| **Dr. Amina (Instructional Designer)** | Pedagogy, learning paths, course structure, engagement |
| **Khalid (Frontend Engineer)** | HTML/CSS/JS quality, bugs, performance, cross-browser |
| **Fatima (Accessibility Specialist)** | WCAG compliance, screen reader support, keyboard nav |
| **Prof. Hassan (Subject Matter Expert)** | Evidence synthesis content accuracy, categorization |
| **Noor (UX Designer)** | User experience, navigation, visual design, mobile |
| **Omar (DevOps / Distribution)** | Packaging, deployment, offline use, maintainability |

---

## 1. Dr. Amina — Instructional Design Review

### 1.1 Overall Assessment: STRONG with structural gaps

The collection represents an ambitious and largely successful curriculum covering evidence synthesis end-to-end. The 23 courses span from foundational (topic selection, methods) through advanced (IPD, MASEM, network meta-analysis) to applied (HTA Oman, TruthCert Africa) and meta-career (Becoming a Methodologist). This breadth is rare in a single self-contained package.

### 1.2 Strengths

- **Narrative-driven pedagogy.** Courses use storytelling frameworks (parables, rhetorical questions, "oath statements," contrast boxes for right/wrong approaches). The `fatiha-course.html` flagship (12,191 lines, 16 modules, 218 slides) is the most developed example of this approach.
- **Gamification is pervasive.** 17 of 23 courses have significant gamification elements (points, XP bars, achievement badges, level systems, streaks). The highest density is in `qualitative-evidence-synthesis-course.html` (361 gamification references), `fatiha-course.html` (342), and `meta-sprint-course.html` (333).
- **Branching scenarios.** Heavy use of decision-based learning paths, especially in `rapid-reviews-course.html` (418 branching references) and `meta-analysis-methods-course.html` (292). These force active engagement rather than passive reading.
- **Quiz density is high.** Every course has quiz/question/answer references, ranging from 57 (TruthCert French) to 479 (Fatiha flagship). This supports retrieval practice principles.

### 1.3 Concerns

- **No prerequisite mapping.** There is zero indication of which courses should be taken before others. A learner encountering "Advanced Meta-Analysis: Beyond the Basics" without completing "Meta-Analysis Methods: From Question to Conclusion" first will struggle. The gateway provides no learning path guidance.

- **Massive variance in depth.** Course sizes range from 1,155 lines (CAST) to 12,191 lines (Fatiha). The CAST course has 16 slides and 0 modules — it functions more as a short presentation than a course. This inconsistency is not surfaced anywhere in the gateway. Users have no way to gauge scope before opening a file.

- **No spaced repetition across courses.** Individual courses may implement spaced repetition internally (the Fatiha flagship has backup versions documenting this), but there is no cross-course review mechanism. A learner who completes GRADE and then moves to Risk of Bias has no scheduled review of GRADE concepts.

- **Missing learning objectives.** The gateway cards show only titles. There are no explicit learning outcomes per course ("After this course, you will be able to..."). This is a fundamental instructional design omission for a training collection.

- **DTA version proliferation.** Four versions (v1 through v4) of the DTA course are accessible. The gateway tries to address this by collapsing v1-v3 under a `<details>` element, but the versioning is confusing: the v3 file's `<title>` says "V4 - Perfect 10" and the v4 file's `<title>` says "V3". These swapped labels will confuse any learner.

### 1.4 Recommendations

1. Add a **suggested learning pathway** to the gateway (e.g., "Start here" → "Then these" → "Choose your specialty")
2. Add **estimated duration and difficulty level** to each gateway card
3. Add **learning objectives** (2-3 bullets) per course, visible on the gateway
4. Remove or clearly archive superseded DTA versions — only the latest should be prominent
5. Fix the v3/v4 title swap in the DTA files
6. Consider adding a **cross-course review quiz** that tests concepts from previously completed courses

---

## 2. Khalid — Frontend Engineering Review

### 2.1 Gateway `index.html` — Bugs Found

#### BUG 1 (HIGH): Search and category filter do not compose

The search handler (lines 400-415) and category filter handler (lines 420-443) operate independently. When a user:
1. Clicks the "Methods" filter tab (only Methods cards shown)
2. Types "meta" in search

...the search handler unconditionally shows ANY card matching "meta", overriding the active category filter. Cards from "Meta / Planning" reappear despite "Methods" being the active filter.

**Root cause:** The search handler's logic `card.classList.toggle('hidden', q && !text.includes(q))` does not check the active category. The two filters need to be composed into a single render function.

#### BUG 2 (HIGH): `<details>` section excluded from filtering

The collapsed DTA archive section's inner grid `<div>` (line 369) has no `data-cat` attribute. The category filter code treats `undefined !== "methods"` as `true` and always hides this grid when any filter is active — even "Methods," which is the correct category for DTA courses.

Additionally, when search hides all three DTA archive cards, the `<details>` element and its `<summary>` remain visible, showing an expandable label that reveals empty space.

#### BUG 3 (MEDIUM): Hardcoded stats are wrong

- "25 Courses" — actual count is 23 (main) or 26 (including archived DTA versions)
- "6 Categories" — actual filterable categories = 5 (the "French" tag is visual only, not a filter)

#### BUG 4 (LOW): No "no results" feedback

Searching for a term that matches nothing produces a completely blank page between the filter tabs and footer. No message indicates zero results.

### 2.2 Course Files — Technical Patterns

**Consistent design system:** All courses share the same CSS variable naming (`--navy`, `--deep-navy`, `--gold`, `--cream`, `--green`, `--red`), the same font stack (Cormorant Garamond + Source Sans Pro via Google Fonts), and the same sidebar/main-content flex layout. This is good for maintainability.

**External dependencies are minimal:**
- All courses: Google Fonts (1 CDN call)
- 4 courses: Plotly.js CDN for interactive charts (`advanced-meta-analysis`, `meta-analysis-methods`, `publication-bias-detective`, `ipd-meta-analysis`)
- No other frameworks (no React, no jQuery, no build tools)

**Self-contained single-file architecture:** Each course is one HTML file with inline CSS and inline JS. This is excellent for offline distribution (USB sticks, email, ZIP files) but creates massive code duplication. The shared CSS/JS patterns are copy-pasted across all 23 files. A bug fix in one course's quiz engine does not propagate to others.

**No back-to-gateway navigation:** None of the 23 course files contain a link back to `index.html`. Once a user opens a course, they must use the browser back button.

### 2.3 Cross-Browser

- **`-webkit-background-clip: text`** used in the gateway without the standard `background-clip: text`. Works in practice but is technically non-standard.
- **`-webkit-text-fill-color: transparent`** has no standard equivalent and no fallback `color` declaration. If a browser doesn't support this, the gradient heading would show body text color against the gradient background — likely unreadable.
- Courses using Plotly.js are pinned to version `2.27.0` — good for reproducibility.

### 2.4 Performance

No concerns. All files are static HTML, load no images, and execute minimal JS. The largest file (12,191 lines, ~400KB) still loads instantly. The gateway has 28 DOM cards with trivial filtering logic — no debounce needed.

---

## 3. Fatima — Accessibility Review

### 3.1 Gateway `index.html` — WCAG Audit

| Issue | WCAG Criterion | Severity |
|-------|---------------|----------|
| `.file` text contrast ~3.8:1 on card bg (`#94a3b8` on `#1e293b`) | 1.4.3 Contrast (Minimum) | **FAIL — AA** |
| Search input has no `<label>` or `aria-label` | 1.3.1 Info & Relationships | **FAIL — A** |
| Filter tabs lack `role="tablist"` / `role="tab"` / `aria-selected` | 4.1.2 Name, Role, Value | **FAIL — A** |
| No `aria-live` region for search results count | 4.1.3 Status Messages | **FAIL — AA** |
| No visible `:focus` styles on cards or filter buttons | 2.4.7 Focus Visible | **FAIL — AA** |
| No `<nav>` landmark around filter tabs | 1.3.1 Info & Relationships | **FAIL — A** |
| No skip link | 2.4.1 Bypass Blocks | Advisory |

**Positive:** Correct heading hierarchy (`<h1>` → `<h2>`), proper use of `<header>`, `<main>`, `<footer>` landmarks, and semantic `<a>` elements for course cards.

### 3.2 Course Files — Accessibility Landscape

Accessibility varies dramatically across the collection:

| Tier | Courses | A11y Keyword Count | Features Present |
|------|---------|-------------------|-----------------|
| **Good** | `rapid-reviews-course.html` (147), `becoming-methodologist.html` (102), `fatiha-course.html` (72) | 70+ | ARIA attributes, skip links, focus management, some keyboard nav |
| **Moderate** | `hta-oman-course.html` (68), `ipd-meta-analysis.html` (58), `meta-analysis-methods.html` (54) | 30-70 | Some ARIA, partial keyboard support |
| **Poor** | `truthcert-course.html` (0), `truthcert-course-fr.html` (0), `ai-meta-analysis.html` (0), `dta-v2.html` (1) | 0-5 | No accessibility features |

**Key findings:**
- The **flagship course** (`fatiha-course.html`) and later courses (`becoming-methodologist`, `rapid-reviews`) show significantly better accessibility, suggesting awareness grew over time
- **Earlier/smaller courses** (`truthcert`, `ai-meta-analysis`, `dta-v1/v2`) have zero accessibility markup
- **No course has a fully accessible quiz system** — answer selection typically relies on click handlers on `<div>` elements rather than native `<input type="radio">` or `<button>` elements with proper ARIA
- The sidebar navigation across all courses uses `<div>` click handlers instead of `<button>` or `<a>` elements — not keyboard-accessible without `tabindex` and `keydown` handlers
- **Mobile:** Most courses hide the sidebar entirely below 768px (`display: none`). This means the module navigation — the primary way to navigate the course — completely disappears on mobile. No hamburger menu or alternative navigation is provided. Users on mobile are trapped on whatever slide they can reach via forward/back buttons.

### 3.3 Recommendations

1. **Gateway:** Add `aria-label="Search courses"` to the search input, wrap filter tabs in `<nav role="tablist">`, add `aria-live="polite"` results counter, add visible focus outlines
2. **All courses:** Convert sidebar module items to `<button>` elements, add `tabindex` and keyboard event handlers
3. **All courses:** Add a mobile navigation alternative (hamburger menu or bottom sheet)
4. **Quiz systems:** Use native form elements (`<fieldset>`, `<legend>`, `<input type="radio">`) or proper ARIA roles (`role="radiogroup"`, `role="radio"`)
5. **Standardize:** Back-port accessibility improvements from newer courses to older ones

---

## 4. Prof. Hassan — Subject Matter Expert Review

### 4.1 Curriculum Completeness

The collection covers an impressive breadth of evidence synthesis methodology:

**Core methodology (well covered):**
- Systematic review fundamentals (topic selection → search → methods → writing)
- Effect size calculation, heterogeneity assessment
- Risk of bias tools (RoB 2, ROBINS-I implied by context)
- GRADE certainty of evidence
- Publication bias detection and adjustment

**Specialized methods (well covered):**
- Diagnostic test accuracy (DTA) meta-analysis — 4 versions showing iterative refinement
- Individual participant data (IPD) meta-analysis
- Network meta-analysis (within advanced course)
- Qualitative evidence synthesis
- Prognostic reviews
- Umbrella reviews / overviews of reviews

**Applied/contextual (unique value):**
- Health technology assessment with Oman context — rare regional perspective
- TruthCert Africa (English + French) — evidence certification for African health systems
- CAST (When Certainty Kills) — case study on the dangers of overconfident evidence
- AI in meta-analysis — timely and forward-looking
- Rapid reviews in crisis — pandemic-era relevance

**Notable gaps:**
- **No dedicated network meta-analysis course** (covered only within "Advanced Meta-Analysis")
- **No course on Bayesian meta-analysis** — increasingly important in the field
- **No course on meta-analysis of proportions or rates** — common in prevalence studies
- **No course on prospective meta-analysis / registration** (partially covered in "Living Reviews")
- **No dedicated search strategy course** — search methodology is the foundation of systematic reviews

### 4.2 Category Assignments in Gateway

The gateway's 5-category taxonomy (Core, Methods, Specialty, Applied, Meta) is generally sound. One debatable assignment:

- **Qualitative Evidence Synthesis** is categorized under "Methods" but could arguably be "Specialty" since it is a distinct paradigm from quantitative meta-analysis, not merely a method variation
- **CAST (When Certainty Kills)** is in "Applied" but is more of a cautionary case study — possibly better under "Meta" alongside "Becoming a Methodologist"

These are judgment calls, not errors.

### 4.3 Title Consistency

Most titles follow a compelling `"Evocative Title: Descriptive Subtitle"` pattern. Two anomalies:

1. **`umbrella-reviews-course.html`** has `<title>Living Reviews: Future of the Field</title>` — this is the wrong title. It's a copy of the living reviews title. The gateway correctly displays it as "Umbrella Reviews: Reviews of Reviews" but the actual HTML `<title>` tag is wrong.
2. **DTA v3/v4 title swap** as noted above.

---

## 5. Noor — UX Design Review

### 5.1 Gateway UX

**Strengths:**
- Clean, modern dark theme with strong visual hierarchy
- Category color-coding (6 distinct tag colors) provides instant visual grouping
- Search bar is prominently placed and functional
- Filter tabs are intuitive pill-style buttons
- Card hover effects give clear affordance (border glow + subtle lift)
- Collapsed `<details>` for archive versions is a good progressive disclosure pattern

**Weaknesses:**

1. **Cards are information-sparse.** Each card shows: a category tag, a title, and a filename. The filename is developer information that adds no value for learners. It should be replaced with a 1-line course description or module count.

2. **No visual indication of course scope.** A 1,155-line presentation (CAST) and a 12,191-line comprehensive course (Fatiha) appear identically. Users need some signal — module count, estimated duration, or a size indicator.

3. **No "start here" signposting.** A first-time visitor sees 23 courses with no indication of where to begin. The Core category helps, but even within Core there's no suggested order.

4. **The footer is empty of utility.** It repeats the collection name. This space could hold a quick-start guide, author info, or version/date information.

5. **No breadcrumb or back navigation in courses.** Users who open a course have no way to return to the gateway except the browser back button. Every course should have a small "Back to Course Library" link in the header/sidebar.

6. **Mobile experience is poor across courses.** The sidebar (primary navigation) disappears at 768px with no replacement. On the gateway, the grid overflows on screens narrower than ~368px because `minmax(320px, 1fr)` exceeds the available width minus padding.

### 5.2 Visual Consistency Across Courses

The courses share a consistent design language:
- **Color palette:** Deep navy + gold + cream (academic, premium feel)
- **Typography:** Cormorant Garamond for headings (serif, classical), Source Sans Pro for body (clean, modern)
- **Layout:** Fixed sidebar (280-320px) + scrollable main content
- **Interactions:** Module list in sidebar, slide-based content, forward/back navigation

**However, the gateway uses a completely different design language:**
- Different color palette (Tailwind-inspired slate/sky blue vs. navy/gold)
- Different font stack (Segoe UI / system-ui vs. Cormorant Garamond / Source Sans Pro)
- No sidebar, grid-based layout

This creates a jarring visual transition when moving from gateway → course. The gateway should adopt the navy/gold/Cormorant Garamond design system used by all courses.

### 5.3 Recommendations

1. **Restyle the gateway** to match the navy/gold/serif design language of the courses
2. Replace filenames on cards with **short descriptions** and **module counts**
3. Add a **"Recommended Starting Path"** section at the top (3-4 courses in order)
4. Add a **"Back to Library"** link in every course's sidebar header
5. Add a **mobile hamburger menu** to courses or a sticky bottom nav
6. Fix the grid minimum to `minmax(min(320px, 100%), 1fr)` for narrow viewports

---

## 6. Omar — DevOps & Distribution Review

### 6.1 Packaging Assessment

**Current state:** 23 course HTML files + 1 gateway HTML file + supporting files (screenshots, markdown docs, Python test files, backup HTML files) in a flat directory. Packaged into a 1.6 MB ZIP.

**Strengths:**
- **Self-contained single-file courses.** Each HTML file includes all CSS and JS inline. No build step required. Can be opened from a USB stick, email attachment, or any file system. This is ideal for low-bandwidth environments (Africa, Oman contexts targeted by several courses).
- **Minimal external dependencies.** Only Google Fonts (graceful degradation to system fonts if offline) and Plotly.js (4 courses only, for interactive charts).
- **Small total size.** 1.6 MB zipped for 23 courses is remarkably compact.

**Concerns:**

1. **ZIP includes backup files.** The current ZIP contains ALL `.html` files in the directory, including 8 backup/versioned files (`fatiha-course_backup_*.html`, `dta-course-when-the-test-lies-v2/v3.html`). These add ~25,000 lines of redundant content. The ZIP should either:
   - Exclude backups entirely, OR
   - Include them in a clearly separated `archive/` subdirectory

2. **ZIP does not include screenshot directories.** The `screenshots/` and `screenshots_new_features/` directories are excluded. If any course references these images, they will be broken when extracted from the ZIP. (Based on the HTML inspection, courses appear self-contained and don't reference local images, so this is likely fine.)

3. **No offline fallback for Google Fonts.** All 23 courses load `fonts.googleapis.com`. Offline, they fall back to Georgia/sans-serif, which changes the visual appearance significantly. For true offline distribution, the fonts should be bundled (WOFF2 files are ~60KB total for the two families used).

4. **No offline fallback for Plotly.js.** Four courses load `cdn.plot.ly/plotly-2.27.0.min.js` (~3.5 MB). Offline, all interactive charts in these courses silently fail. Options:
   - Bundle a minified Plotly.js in the ZIP (~3.5 MB added)
   - Use a lightweight charting alternative
   - Add a visible "offline mode" message when Plotly fails to load

5. **Markdown and Python files in the directory are not user-facing.** Files like `COURSE_MASTER_PLAN.md`, `IMPROVEMENT_PLAN.md`, `test_gui.py`, and `MULTIPERSONA_REVIEW_*.md` are development artifacts. They should be excluded from the distribution ZIP or moved to a `dev/` subdirectory.

6. **No versioning or changelog.** There is no `VERSION` file, no `CHANGELOG.md`, and no date stamp in the gateway. When users receive an updated ZIP, they have no way to know what changed.

### 6.2 Maintainability

**Code duplication is the primary maintainability risk.** The shared design system (sidebar, navigation, quiz engine, gamification, slide transitions) is duplicated across 23 files. Estimated shared CSS: ~200 lines per file = ~4,600 lines of duplicated CSS. Estimated shared JS (navigation, quiz, progress tracking): ~150-300 lines per file = ~3,500-7,000 lines of duplicated JS.

A refactor to extract shared CSS/JS into common files would reduce total codebase by ~30-40% and make bug fixes propagate automatically. However, this would break the self-contained single-file property, which is a core distribution advantage for the target audiences (low-bandwidth, offline-first contexts).

**Recommendation:** Accept the duplication as a conscious trade-off for distribution simplicity. Document this decision. When a shared bug is found, use a script to patch all files.

### 6.3 ZIP Build Recommendations

Create a clean build script that:
1. Copies only non-backup HTML files + `index.html` to a staging directory
2. Optionally bundles Google Fonts WOFF2 files for offline use
3. Excludes `.md`, `.py`, `screenshots*/`, and `*backup*` files
4. Adds a `VERSION.txt` with date and course count
5. Produces the ZIP from the staging directory

---

## Consolidated Findings

### Critical (must fix)

| # | Finding | Owner |
|---|---------|-------|
| 1 | Gateway: Search + category filter do not compose (search overrides active filter) | Khalid |
| 2 | Gateway: `<details>` section excluded from category filtering (missing `data-cat`) | Khalid |
| 3 | Gateway: Hardcoded stats wrong ("25 Courses" and "6 Categories") | Khalid |
| 4 | `umbrella-reviews-course.html` has wrong `<title>` tag (says "Living Reviews" instead of "Umbrella Reviews") | Prof. Hassan |
| 5 | DTA v3/v4 files have swapped version labels in `<title>` tags | Prof. Hassan |

### High (should fix)

| # | Finding | Owner |
|---|---------|-------|
| 6 | Gateway: `.file` text fails WCAG AA contrast (~3.8:1) | Fatima |
| 7 | Gateway: Search input has no `<label>` or `aria-label` | Fatima |
| 8 | Gateway: Filter tabs lack ARIA tab pattern (`role="tablist"`, `aria-selected`) | Fatima |
| 9 | Gateway: No `aria-live` region for search result feedback | Fatima |
| 10 | Gateway: No visible focus styles on cards and filter buttons | Fatima |
| 11 | Gateway visual design mismatches course design language (different palette + fonts) | Noor |
| 12 | No back-to-gateway link in any course file | Noor / Khalid |
| 13 | All courses: sidebar navigation disappears on mobile with no replacement | Fatima / Noor |
| 14 | ZIP includes backup files and dev artifacts | Omar |
| 15 | No learning path guidance in gateway | Dr. Amina |

### Medium (should address)

| # | Finding | Owner |
|---|---------|-------|
| 16 | Gateway: No "no results" message when search matches nothing | Khalid |
| 17 | Gateway: Grid overflows on viewports narrower than ~368px | Khalid / Noor |
| 18 | Gateway: French TruthCert tag says "French" but `data-cat="applied"` (inconsistent) | Khalid |
| 19 | Gateway cards show filenames instead of descriptions | Noor |
| 20 | No course duration/scope indicators on gateway cards | Dr. Amina / Noor |
| 21 | 4 courses depend on Plotly.js CDN with no offline fallback | Omar |
| 22 | All courses depend on Google Fonts CDN with no offline fallback | Omar |
| 23 | Accessibility varies wildly (0 to 147 A11y markers across courses) | Fatima |
| 24 | Quiz systems use div click handlers instead of native form elements | Fatima |

### Low (nice to have)

| # | Finding | Owner |
|---|---------|-------|
| 25 | Gateway: Missing `background-clip: text` (standard, unprefixed) | Khalid |
| 26 | Gateway: No `<meta name="description">` or favicon | Khalid |
| 27 | Gateway: No `@media print` styles | Khalid |
| 28 | No versioning/changelog for the collection | Omar |
| 29 | `CAST_WhenCertaintyKills.html` breaks kebab-case naming convention | Omar |
| 30 | No cross-course spaced repetition mechanism | Dr. Amina |
| 31 | No Bayesian meta-analysis or network meta-analysis dedicated course | Prof. Hassan |
| 32 | No dedicated search strategy course | Prof. Hassan |

---

## Scores

| Persona | Score | Summary |
|---------|-------|---------|
| Dr. Amina (Instructional Design) | **7.5/10** | Rich pedagogy with gamification, branching, and quizzes. Missing learning paths, objectives, and cross-course review. |
| Khalid (Frontend Engineering) | **6.5/10** | Clean self-contained architecture. Gateway has 3 functional bugs. Good performance. Code duplication is a conscious trade-off. |
| Fatima (Accessibility) | **4.5/10** | Gateway has 6 WCAG failures. Course accessibility ranges from zero to good. Mobile navigation is broken across all courses. |
| Prof. Hassan (Subject Matter) | **8.5/10** | Exceptional breadth covering 23 evidence synthesis topics. Minor gaps (Bayesian, NMA). Two title tag errors. |
| Noor (UX Design) | **6/10** | Courses have premium visual feel. Gateway mismatches design language. Cards lack descriptions. No learning path signposting. Mobile UX is poor. |
| Omar (DevOps) | **7/10** | Excellent offline-first, single-file architecture. ZIP needs cleanup. No versioning. CDN dependencies need offline fallbacks. |

**Overall Collection Score: 6.7/10**

The collection is pedagogically ambitious and content-rich, with a production-ready visual design in the courses themselves. The main areas for improvement are: (1) fixing the gateway bugs, (2) accessibility standardization across all courses, (3) mobile navigation, and (4) adding learning path guidance to the gateway.

---

## Appendix A: Course-by-Course Deep Analysis

### Course Tiers by Feature Richness

| Tier | Courses | Key Features |
|------|---------|-------------|
| **Tier 1 — Full Feature Set** | `fatiha-course.html` (flagship) | SM-2 spaced repetition + gamification + branching scenarios + Plotly + RoB tool + GRADE calculator + mini forest plots |
| **Tier 2 — Gamification + Plotly** | `advanced-meta-analysis-course.html`, `publication-bias-detective.html` | Interactive Plotly.js charts (Bayesian posterior, SROC curves, funnel plots, p-curves) + quizzes + gamification |
| **Tier 3 — Gamification + Decision Trees** | `umbrella-reviews-course.html`, `grade-certainty-course.html`, `meta-sprint-course.html`, `qualitative-evidence-synthesis-course.html`, `risk-of-bias-mastery-course.html` | XP/badges/levels + decision scenarios + quizzes + localStorage progress |
| **Tier 4 — Quizzes + Progress** | `dta-course-when-the-test-lies-v4.html`, `truthcert-course.html`, `ai-meta-analysis-course.html`, `hta-oman-course.html`, `becoming-methodologist.html` | Quiz/answer system + progress tracking (no gamification engine) |

### Individual Course Profiles

| Course | Lines | Modules | Slides | Interactive Highlights | Unique Features |
|--------|-------|---------|--------|----------------------|----------------|
| **Evidence Reversal (flagship)** | 12,191 | 15 | ~128 | RoB 2.0 tool, GRADE calculator, forest plots, SM-2 spaced rep, branching scenarios | Only course with full SM-2 spaced repetition engine; Quranic storytelling rhythm |
| **Advanced Meta-Analysis** | 3,210 | 9 | JS-dynamic | 4 Plotly.js charts (Bayesian, SROC, network, dose-response) | Interactive Plotly visualizations; glossary/flashcard system (29 terms) |
| **DTA: When The Test Lies v4** | 2,532 | 20 | ~99 | Sensitivity/specificity sliders, 2x2 table exercises | Most granular module structure (20 modules); thematic "blood-red" medical coloring |
| **TruthCert Africa** | 2,072 | 15 | ~50 | Decision scenarios | Africa-focused (Sudan, Nigeria, Tanzania, Ghana, Kenya); provenance/trust-chain teaching |
| **AI in Meta-Analysis** | 2,268 | 15 | 93 | Module-based interactive content | ASReview tutorial, validated prompt library, consumer's guide for AI-generated reviews |
| **Umbrella/Living Reviews** | 2,153 | 7 | JS-dynamic | Decision trees, gamification (8 levels, 12 badges) | Living review sustainability/retirement decision-making; COVID-era case studies |
| **GRADE Certainty** | 3,072 | 10 | JS-dynamic | Decision scenarios with XP, prediction activities | Upgrading factors module (rare in GRADE courses); real mortality data for certainty errors |
| **META-SPRINT** | 4,002 | 9 | JS-dynamic | Decision scenarios, prediction-before-reveal | 40-day sprint methodology; CondGO emergency framework; Colchicine case study |
| **HTA Oman** | 2,709 | 11 | ~97 | ICER/QALY exercises | Only health economics course; GCC/Oman contextualized (42 regional references) |
| **Publication Bias Detective** | 6,307 | 7 | JS-dynamic | 4 Plotly.js charts (funnel, contour, trim-fill, p-curve) | Detective/forensic investigation theme; module time estimates (15-35 min each) |
| **Qualitative Evidence Synthesis** | 3,235 | 10 | JS-dynamic | Decision scenarios, gamification (8 levels, 18 badges) | Only qualitative methods course; GRADE-CERQual 4-domain coverage; meta-ethnography |
| **Becoming a Methodologist** | 3,140 | 9 | ~102 | Heavy quiz emphasis (107 references) | Only career-focused course; highest ARIA accessibility (91 references) |
| **Risk of Bias Mastery** | 2,029 | 7 | JS-dynamic | Decision scenarios, gamification | Most compact course; domain-specific gamification titles (Allocation Guard, etc.) |

### Two Rendering Architectures Found

The courses use two distinct approaches:

1. **Hardcoded HTML slides** (`fatiha-course`, `dta-v4`, `truthcert`, `hta-oman`, `becoming-methodologist`) — Slides are written directly in the HTML. Larger file sizes but all content visible in source.
2. **JavaScript-driven dynamic rendering** (`advanced-meta-analysis`, `umbrella-reviews`, `grade-certainty`, `meta-sprint`, `publication-bias-detective`, `qualitative-evidence-synthesis`, `risk-of-bias-mastery`) — Slide content is defined in JS data arrays and rendered dynamically. More compact files but content is harder to inspect/search.

This architectural split is a maintenance concern: bug fixes or feature additions must account for both patterns.

### Accessibility Ranking (detailed)

| Rank | Course | ARIA/A11y References | Key A11y Features |
|------|--------|---------------------|-------------------|
| 1 | Becoming a Methodologist | 91 | Skip-link, ARIA labels, role attributes, keyboard nav |
| 2 | HTA Oman | 63 | ARIA labels, role attributes, keyboard nav |
| 3 | Evidence Reversal (flagship) | 62 | Skip-link, sr-only class, focus-visible, WCAG contrast notes |
| 4 | Umbrella/Living Reviews | 37 | Skip-link, ARIA labels, keyboard nav |
| 5 | Risk of Bias Mastery | 37 | Skip-link, ARIA labels, keyboard nav |
| 6 | Qualitative Evidence Synthesis | 30 | ARIA labels, skip-link, keyboard nav |
| 7 | Publication Bias Detective | 28 | ARIA labels, skip-link, keyboard nav |
| 8 | META-SPRINT | 28 | Skip-link, ARIA labels, keyboard nav |
| 9 | GRADE Certainty | 25 | Skip-link, gamification stats panel |
| 10 | Advanced Meta-Analysis | 1 | Keyboard nav only |
| 11 | DTA v4 | 1 | Keyboard nav only |
| 12 | TruthCert Africa | 0 | None |
| 13 | AI in Meta-Analysis | 0 | None |

**Pattern:** Courses built later in the development cycle show markedly better accessibility, suggesting growing awareness. The earliest courses (TruthCert, AI in Meta-Analysis, DTA) have zero accessibility features. The most recent (Becoming a Methodologist, HTA Oman) have the most.

---

*Review conducted using automated structural analysis + deep content inspection of all 13 primary course files across all 6 categories.*
