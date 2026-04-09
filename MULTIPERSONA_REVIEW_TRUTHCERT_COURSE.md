# Multi-Persona Review: TruthCert Africa Course

**Document:** truthcert-course.html
**Review Date:** 2026-02-02
**Reviewers:** 7 simulated personas representing key stakeholders

---

## PERSONA 1: Dr. Amina Okonkwo
**Role:** Health Economist, Nigerian Federal Ministry of Health
**Experience:** 12 years in health policy, trained at LSHTM
**Perspective:** End-user who would actually use TruthCert

### Strengths
- **Local currency emphasis is excellent.** Finally, a tool that speaks in Naira! I'm tired of converting USD figures and explaining exchange rate assumptions to ministers.
- **The Go/No-Go rules are practical.** k >= 4 for African studies is reasonable. We often have sparse local evidence and need clear guidance on when to proceed.
- **Sierra Leone maternal mortality comparison (112x UK) is powerful.** This will resonate with policymakers who need to understand the stakes.
- **The "memory leak = BLOCK" rule is crucial.** I've seen too many policy documents cite "approximately 30%" with no source.

### Concerns
- **Missing: How do I actually USE TruthCert?** The course explains the philosophy beautifully, but where's the practical tutorial? How do I run an analysis? What software do I need?
- **The 60-second performance claim needs verification.** On my 2019 Dell laptop with intermittent power? I'm skeptical.
- **No mention of data availability challenges.** Where do I get the unit costs? The baseline incidence? The course assumes these exist.

### Suggestions
1. Add a Module 7: "Your First TruthCert Analysis" - a hands-on walkthrough
2. Include a slide on data sources: DHS, WHO CHOICE, iDSI cost databases
3. Show a real example output - what does a certified claim actually look like?

### Rating: 7.5/10
*"Philosophically compelling, but I need more practical guidance."*

---

## PERSONA 2: Professor James Whitfield
**Role:** Health Technology Assessment Academic, University of York
**Experience:** 25 years in HTA methods, NICE committee member
**Perspective:** Methodological rigor and academic credibility

### Strengths
- **The CAST story is well-chosen and factually accurate.** The 50,000 figure is from Moore (1995) and is a reasonable estimate. Good to see proper sourcing.
- **Rejection of GDP-multiple thresholds is methodologically sound.** The Woods et al. citation is appropriate. This shows awareness of current debates.
- **Affordability + Net Health Benefit framing is state-of-the-art.** This aligns with the Claxton/Sculpher "opportunity cost" approach.
- **Reproducibility emphasis is excellent.** The Begley & Ellis citation is correct and the 89% non-replication figure is accurate.

### Concerns
- **The four certification grades need more rigorous definition.** What exactly distinguishes STABLE from MODERATE? Is there a checklist? A scoring algorithm?
- **"Scenario analysis only" for EXPOSED is vague.** Which scenarios? One-way? Probabilistic? Structural?
- **The course conflates evidence quality with context transferability.** A STABLE European study may still be UNCERTAIN for Nigeria due to transportability issues, not evidence quality.
- **No discussion of heterogeneity quantification.** How does TruthCert handle I-squared, prediction intervals, or between-study variance?

### Suggestions
1. Add a technical appendix defining each certification grade with explicit criteria
2. Distinguish between "evidence certainty" and "contextual applicability"
3. Include discussion of GRADE framework and how TruthCert relates to it
4. Address the transportability problem more formally (target trial emulation?)

### Rating: 6.5/10
*"Good communication, but methodological details need tightening."*

---

## PERSONA 3: Fatou Diallo
**Role:** Community Health Worker, The Gambia
**Experience:** 8 years in rural health delivery, high school education
**Perspective:** Ground-level health worker, non-technical audience

### Strengths
- **The storytelling is powerful and accessible.** "Have you not heard the tale of the physicians..." - this speaks to me. I understand stories.
- **The refrain structure helps me remember.** "And the numbers were naked" - I will remember this phrase.
- **The maternal mortality numbers are real to me.** I have seen mothers die. 458 per 100,000 in my country - I have witnessed this.
- **The big red "50,000" number is shocking and memorable.** This is how you teach.

### Concerns
- **Too much English jargon.** "Evidence locator," "cryptographic hash," "transformation trail" - what do these mean? I don't understand.
- **The quiz assumes I remember numbers.** I remember stories, not "786888" or "k >= 4."
- **No Wolof, Mandinka, or French version.** Most health workers in Gambia don't read English well.
- **The computer/browser requirement excludes me.** I have a phone, not a laptop.

### Suggestions
1. Create a simplified version with less jargon - maybe a visual/infographic version
2. Translate to French (for West Africa) and Swahili (for East Africa)
3. Make a mobile-friendly version that works on smartphones
4. Replace technical quiz questions with story-based recall ("What happened to the patients in America?")

### Rating: 6/10
*"The stories touched my heart, but the technical parts lost me."*

---

## PERSONA 4: Dr. Chen Wei
**Role:** Global Health Program Officer, Bill & Melinda Gates Foundation
**Experience:** 15 years in global health funding, MPH/MBA
**Perspective:** Funder deciding whether to support TruthCert adoption

### Strengths
- **Clear problem statement with quantified impact.** 50,000 deaths/year from CAST, 112x maternal mortality disparity - these are fundable problems.
- **The equity angle is compelling.** "Different verdicts based on where you were born" - this aligns with our equity mandate.
- **Low-resource design is smart.** "Ordinary laptop, browser only" - this is scalable.
- **13 countries, 7 disease groups = 91 packs** - this is a defined, measurable scope.

### Concerns
- **No theory of change.** How does "clothed numbers" lead to "mothers lived"? What's the causal pathway?
- **No mention of sustainability.** Who maintains the country packs? Who updates the evidence? What happens when TruthCert funding ends?
- **No implementation evidence.** Has this been piloted? What was the uptake? Did it change any decisions?
- **The Ahmadiyya hospital mention is oddly specific.** Is this designed for a particular religious community? That could limit scale.

### Suggestions
1. Add a logic model: Inputs → Activities → Outputs → Outcomes → Impact
2. Include a sustainability plan: training local teams, open-source codebase, institutional embedding
3. Pilot in 2-3 countries and document case studies before claiming impact
4. Clarify the relationship with Ahmadiyya healthcare network - is this a partnership or an example?

### Rating: 7/10
*"Promising concept, but needs implementation evidence and sustainability plan."*

---

## PERSONA 5: Sister Margaret Osei
**Role:** Hospital Administrator, Ahmadiyya Hospital Apapa, Nigeria
**Experience:** 20 years in hospital management
**Perspective:** Healthcare delivery institution mentioned in the course

### Strengths
- **I'm pleased to see our hospital mentioned.** The Apapa hospital does have a busy maternity ward, and we do face these protocol decisions daily.
- **The scenario described is realistic.** A doctor deciding whether to adopt NICE guidelines is exactly what happens.
- **Local currency reporting would help our budgeting.** We plan in Naira, not USD.

### Concerns
- **The course puts words in our doctors' mouths.** The scenario implies our staff would use TruthCert, but we've never heard of it. Has anyone consulted us?
- **No discussion of training requirements.** How long to train a doctor to use this? We're short-staffed.
- **The "4 African studies" requirement may not exist for many of our clinical questions.** Will we be told "BLOCK" for most queries?
- **Integration with our existing systems?** We use paper records and basic EMR. How does TruthCert fit?

### Suggestions
1. Reach out to actual hospitals before using them as examples - get consent and input
2. Add realistic training time estimates: "2-hour online course" or "1-week intensive"
3. Discuss workarounds when k < 4: expert elicitation, Bayesian priors, regional pooling
4. Address integration: Can TruthCert work offline? Export to PDF? Print for meetings?

### Rating: 6.5/10
*"I appreciate being included, but please consult us before speaking for us."*

---

## PERSONA 6: Kwame Asante
**Role:** Graduate Student, Health Economics, University of Ghana
**Experience:** 2 years into PhD, studying cost-effectiveness in malaria
**Perspective:** Next-generation researcher learning the field

### Strengths
- **This is the best introduction to "why HTA matters" I've seen.** The CAST story is more compelling than any textbook chapter.
- **The reproducibility emphasis aligns with open science values.** Fixed seeds, transparent methods - this is how research should be.
- **The critique of GDP thresholds validates my own doubts.** I always felt uncomfortable with 1-3x GDP, but my supervisor used it.
- **The course makes me want to learn more.** I'll read the Woods et al. paper now.

### Concerns
- **No references list.** The course mentions studies but doesn't provide full citations I can follow up on.
- **How does this relate to my thesis?** I'm using TreeAge and R. Does TruthCert replace these? Complement them?
- **The technical implementation is opaque.** What's the actual algorithm for assigning STABLE vs MODERATE? I want to see the code.
- **No discussion of limitations.** Every method has weaknesses. What can TruthCert NOT do?

### Suggestions
1. Add a references slide with full citations (CAST, Begley & Ellis, Woods et al., WHO data)
2. Clarify TruthCert's relationship to existing tools: "TruthCert is a certification layer that works with your existing models"
3. Open-source the grading algorithm so students can study and critique it
4. Add a "Limitations" section: what TruthCert doesn't address (e.g., political feasibility, implementation costs)

### Rating: 8/10
*"Intellectually exciting - please give me more technical depth."*

---

## PERSONA 7: Honorable Minister Abubakar Sule
**Role:** Minister of Health, hypothetical African country
**Experience:** Politician, former physician, needs to justify budget to parliament
**Perspective:** Ultimate decision-maker who must act on HTA advice

### Strengths
- **The opening is attention-grabbing.** If my health secretary showed me this, I'd watch the whole thing.
- **The "50,000 deaths from drugs that made sense" is a powerful warning.** I don't want to be the minister who caused such a catastrophe.
- **The local currency point resonates.** I present budgets in our currency. USD figures confuse my colleagues.
- **The four-grade system is simple enough.** STABLE = proceed, UNCERTAIN = don't - I can explain this to cabinet.

### Concerns
- **What do I actually DO with a TruthCert report?** If it says MODERATE, do I fund the program or not?
- **Political reality is missing.** Sometimes I must fund popular but ineffective programs. Does TruthCert help me navigate this?
- **No mention of stakeholder management.** Pharmaceutical companies, patient advocacy groups, and professional associations all pressure me. How does TruthCert help?
- **The course doesn't mention cost of TruthCert itself.** Is this free? Donor-funded? What happens to our HTA capacity when funding ends?

### Suggestions
1. Add a "For Decision-Makers" executive summary - 5 slides maximum
2. Include guidance on communicating uncertain evidence: "How to say 'we don't know' without losing credibility"
3. Discuss political economy: when evidence conflicts with politics, how to use TruthCert as a shield
4. Clarify sustainability: is this a permanent capability or a project?

### Rating: 7/10
*"Compelling case, but I need practical political guidance."*

---

## SYNTHESIS: COMMON THEMES

### Universal Praise
1. **Storytelling is effective** - all personas found the CAST story and refrains memorable
2. **Local currency emphasis** - resonated with everyone from ministers to health workers
3. **Equity framing** - the critique of GDP thresholds and "where you were born" was universally appreciated
4. **Reproducibility** - academics and students especially valued this emphasis

### Universal Concerns
1. **Practical implementation missing** - How do I actually USE this?
2. **Training requirements unclear** - How long? What prerequisites?
3. **Technical definitions vague** - What exactly is STABLE vs MODERATE?
4. **Sustainability unaddressed** - Who maintains this long-term?
5. **No pilot evidence** - Has this been tested? What were results?

### Priority Recommendations (by frequency)

| Recommendation | Personas Who Raised It |
|----------------|----------------------|
| Add practical tutorial/walkthrough | 1, 5, 7 |
| Define certification grades precisely | 2, 6 |
| Include full reference list | 2, 6 |
| Address sustainability | 4, 7 |
| Create non-English versions | 3 |
| Develop mobile-friendly version | 3 |
| Add decision-maker guidance | 7 |
| Consult actual institutions | 5 |
| Show real example outputs | 1, 6 |
| Discuss limitations | 6 |

---

## RECOMMENDED COURSE REVISIONS

### High Priority (Address Before Deployment)
1. **Add Module 7: "Running Your First Analysis"** - hands-on practical walkthrough
2. **Create Technical Appendix** - precise definitions of STABLE/MODERATE/EXPOSED/UNCERTAIN
3. **Add References Slide** - full citations for all studies mentioned
4. **Develop Executive Summary** - 5-slide version for ministers and busy executives

### Medium Priority (Address Within 3 Months)
5. **French Translation** - essential for West Africa
6. **Mobile-Responsive Version** - for smartphone access
7. **Sustainability Section** - who maintains, how funded, exit strategy
8. **Real Output Examples** - show what a certified claim looks like

### Lower Priority (Address Within 6 Months)
9. **Swahili Translation** - for East Africa
10. **Video Version** - for low-literacy audiences
11. **Political Economy Guidance** - how to use TruthCert when evidence conflicts with politics
12. **Integration Guide** - how TruthCert works with TreeAge, R, Excel

---

## OVERALL ASSESSMENT

**Aggregate Score: 6.9/10**

| Persona | Score | Weight | Weighted Score |
|---------|-------|--------|----------------|
| Health Economist (Nigeria) | 7.5 | 1.5x | 11.25 |
| HTA Academic (York) | 6.5 | 1.0x | 6.5 |
| Community Health Worker (Gambia) | 6.0 | 1.0x | 6.0 |
| Funder (Gates) | 7.0 | 1.5x | 10.5 |
| Hospital Administrator (Nigeria) | 6.5 | 1.0x | 6.5 |
| PhD Student (Ghana) | 8.0 | 0.5x | 4.0 |
| Minister (hypothetical) | 7.0 | 1.5x | 10.5 |
| **Total** | | **8.0** | **55.25** |
| **Weighted Average** | | | **6.9** |

**Verdict:** The course is **philosophically compelling and emotionally engaging**, with excellent use of true stories and memorable refrains. However, it is **incomplete as a training tool** due to missing practical guidance, vague technical definitions, and no implementation evidence.

**Recommendation:** Address High Priority items before deployment. The course is ready for **awareness-raising and advocacy** but not yet ready for **operational training**.

---

*Review completed by multi-persona simulation. Real stakeholder input should supplement this analysis.*
