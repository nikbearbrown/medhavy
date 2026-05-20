# The Coherence Gap: No Intelligent Textbook Platform Teaches Its Own Use
## Paper Outline with Tasks and Timeline

**Target venue:** Computers & Education (primary) or British Journal of Educational Technology  
**Format:** Critical review with empirical survey component + design implications  
**Estimated length:** 7,000–9,000 words  
**Timeline:** 7 working days to submittable draft  

---

## The Argument in One Paragraph

Every major intelligent textbook platform claims to teach content adaptively — using spaced retrieval, phase-gated progression, Socratic dialogue, or mastery-based sequencing. None applies this methodology to teaching its own use. Instructor onboarding across all major platforms consists of vendor documentation, walkthrough videos, and one-day training events — none of which meet the platforms' own stated standards for effective learning. This is not a coincidence: it is a design indictment. The platform that cannot teach its own use has revealed the actual scope of its adaptivity. We document this null finding across twelve major platforms, propose the coherence test as a novel evaluation criterion, and specify the minimum viable design that would allow a platform to pass it.

---

## Paper Structure

### Abstract (150 words)
- States the coherence test
- Reports the null finding (N platforms evaluated, N passing = 0)
- Names the structural explanation (attribution error: design failures classified as implementation failures)
- States the constructive implication

---

### Section 1 — Introduction (600–800 words)

**Core moves:**
1. Open with the implementation failure rate as the field's acknowledged problem (Glimpse K12: two-thirds of EdTech licenses unused; cite the RAND Europe synthesis; cite the Yoon 14-contact-hour threshold finding)
2. Name the standard explanation: "implementation failure" attributed to teacher resistance, insufficient PD, inadequate district support
3. Introduce the alternative explanation: the attribution is backwards. Implementation failure is a design category that has been misclassified as a user-behavior category
4. State the coherence test: if a platform claims to teach anything adaptively, it should be able to teach its own use by the same standard
5. State the null finding and its implication
6. Preview the paper structure

**Tasks:**
- [ ] Pull the Glimpse K12 unused-license statistic — verify the primary source (not secondary citation)
- [ ] Pull the Yoon 14-contact-hour threshold — get the exact citation and the finding's scope (what kind of PD, what outcome measure)
- [ ] Pull the RAND Europe synthesis on teacher capacity as binding constraint — exact title, year, finding
- [ ] One-sentence statement of the coherence test (lock this before writing anything else — it is the paper's operative definition)

---

### Section 2 — Background (900–1,100 words)

**2.1 — The implementation evidence (400 words)**

What the research says about why EdTech deployments fail:
- Teacher capacity as binding constraint (RAND Europe synthesis)
- Yoon et al. 14-contact-hour threshold: the dose-response relationship between PD and student outcomes
- Two-year ASSISTments implementation evidence: teacher engagement with analytics is the mediating variable between platform deployment and student learning
- Michigan Virtual Khanmigo pilot: teacher time savings documented; IDK-IDK pattern documented; adoption inconsistent
- The 14-college adaptive learning experiment: no significant average effect on completion; weak instructor continuation intent

Argumentative point: the implementation research is unanimous that teacher capacity is the binding constraint, and that the current response (external PD providers, vendor walkthroughs) is insufficient. What the research does not do is ask whose responsibility the gap is.

**Tasks:**
- [ ] Locate the 14-college adaptive learning experiment — which consortium ran it, what year, what the exact finding was on instructor continuation intent
- [ ] Pull the Michigan Virtual Khanmigo pilot report — verify it is publicly available; if behind a paywall, document what is publicly citable
- [ ] Pull the two-year ASSISTments implementation study — confirm it is peer-reviewed (not just IES documentation)

**2.2 — The attribution problem (300 words)**

"Implementation failure" as a category does real political work: it protects the platform from design accountability by locating the failure in the district, the teacher, or the PD provider. Cite the Bastani 2025 PNAS finding here not for its AI-tutoring claim but for its structural parallel: the same model with a different wrapper produced opposite outcomes. The wrapper was a design decision. When it failed, the failure was not attributed to the teacher who deployed it — it was visible as a design variable. The argument: onboarding is a wrapper. When it fails, the failure should be attributed the same way.

**2.3 — The coherence test (400 words)**

Define the test formally:
> A platform passes the coherence test if and only if it uses the same pedagogical methodology it claims to apply to student learning to teach instructors how to use the platform effectively — including measuring instructor learning with the same type of signal it uses to measure student learning.

Operationalize it:
- **Criterion A (Methodology match):** Does the platform deliver instructor onboarding through its own adaptive architecture (concept map, phase gates, mode selection, spaced retrieval) rather than through static documentation or synchronous event-based training?
- **Criterion B (Measurement match):** Does the platform assess instructor learning with the same type of signal it uses for student learning (e.g., delayed retrieval probe, GLP-equivalent measure) rather than through satisfaction surveys, completion certificates, or self-report?
- **Criterion C (Feedback loop):** Does the platform use instructor learning data to adapt subsequent onboarding content, as it would for student content?

A platform passes if all three criteria are met. Partial pass if one or two criteria are met. Fail if none are met.

**Tasks:**
- [ ] Lock the three criteria — do not adjust after the search begins
- [ ] Decide: is a partial pass a finding worth reporting separately, or will the paper treat anything less than full pass as a fail? (Recommend: report partial passes separately; they strengthen the argument by showing the gradient)

---

### Section 3 — Methods (500–700 words)

**3.1 — Platform selection**

Inclusion criteria:
- Actively deployed at scale (operational, not research prototype)
- Claims to use adaptive methodology (learning objective model, concept graph, spaced retrieval, AI tutoring, or equivalent)
- Has publicly accessible onboarding materials OR responds to documentation request

Exclusion criteria:
- Pure assessment platforms without instructional content (not the claim being tested)
- Research-only ITS systems not in commercial deployment (CTAT, AutoTutor)
- Platforms discontinued before 2024 (Smart Sparrow, Knewton standalone)

**Sampling rationale:** Three tiers by access model, capturing the full deployment landscape:

| Tier | Platforms | Rationale |
|------|-----------|-----------|
| Free | ASSISTments, OLI/Torus, Khanmigo (teacher tier), OpenStax Assignable | Highest accessibility; weakest resource base for onboarding development |
| Student-pay | ALEKS, Knewton Alta | Dominant in higher ed; direct instructor-facing deployment |
| Institutional | MATHia/Carnegie Learning, Realizeit, CogBooks, Acrobatiq/VitalSource | Highest per-student cost; highest obligation to pass coherence test |

Target N: 10–14 platforms. Aim for 12.

**3.2 — Data collection procedure**

For each platform, three-step procedure:
1. **Public documentation audit:** Platform website, help center, onboarding guides, video tutorials, published implementation guides. Coded against the three criteria.
2. **Customer success inquiry:** Standard inquiry sent to each platform's sales/support contact asking: "Does your platform provide instructor onboarding through the same adaptive methodology used for student learning?" Document the response verbatim.
3. **Published implementation studies:** Peer-reviewed or IES-documented studies that describe onboarding procedures in sufficient detail to evaluate against criteria.

**3.3 — Coding procedure**

Two-coder design if a second coder is available; single-coder with documented decision rules if not. For each criterion (A, B, C) per platform: Pass / Partial / Fail, with quoted evidence for each rating.

Inter-rater reliability target if two coders: κ > 0.70.

**Tasks:**
- [ ] Build the 12-platform list — confirm each platform is currently active and deployable (some may have changed since the landscape research)
- [ ] Draft the standard inquiry email — one paragraph, sent identically to all platforms
- [ ] Build the coding sheet — one row per platform, three criterion columns, evidence quote column, overall rating column
- [ ] Decide: single-coder or two-coder? If two-coder, identify who the second coder is before data collection begins

---

### Section 4 — Results (800–1,000 words)

**4.1 — Summary finding**

Table: Platform × Criterion A × Criterion B × Criterion C × Overall rating

Expected structure of the finding:
- Criterion A (methodology match): All or nearly all platforms fail. Onboarding is documentation + synchronous events universally.
- Criterion B (measurement match): All platforms fail. No platform measures instructor learning with the equivalent of a delayed retrieval probe or GLP signal.
- Criterion C (feedback loop): All platforms fail. No platform adapts onboarding content based on instructor learning data.

If any platform achieves a partial pass, report it with specificity — which criterion, what evidence, what the gap is.

**4.2 — Patterns across tiers**

Do higher-cost institutional platforms (MATHia, Realizeit) invest more in onboarding than free platforms (ASSISTments)? The prediction: higher investment in external PD resources, not in platform-delivered adaptive onboarding. If this holds, it strengthens the attribution argument — even the best-resourced platforms externalize rather than internalize.

**4.3 — The self-description gap**

Qualitative observation: compare each platform's description of effective learning (from their own marketing, documentation, and peer-reviewed validation studies) against their onboarding design. The gap between "what we claim to know about learning" and "how we teach our own platform" is the coherence gap made visible per platform.

This is the section that will resonate with EdSurge readers. It is also the section that requires the most careful documentation — every claim attributed to a platform must be verifiable.

**Tasks:**
- [ ] For each platform: pull their stated pedagogical principles from public documentation (website, published studies, help center). Quote verbatim, note source.
- [ ] For each platform: document onboarding procedure exactly as described in public documentation. Quote verbatim.
- [ ] Code each platform against the three criteria. Document the evidence for each rating.
- [ ] Identify any partial passes and document with specificity.

---

### Section 5 — Discussion (1,200–1,500 words)

**5.1 — The structural explanation (400 words)**

Why does this gap exist across every platform? Three structural factors:

*Factor 1: Math-centricity of the evidence base.* The strongest evidence for adaptive learning is in mathematics — Carnegie Learning MATHia (RAND study), ALEKS (Knowledge Space Theory), ASSISTments (IES). Mathematics has properties that make it tractable for adaptive systems: clear right/wrong answers, well-defined prerequisite structures, unambiguous mastery criteria. Platform onboarding is a domain-agnostic metacognitive task — it does not resolve to a correct answer at a specific point in time, and it requires reflection rather than procedural performance. If the adaptivity only works for well-structured STEM content, the platform cannot turn its own methodology on itself.

*Factor 2: The attribution architecture protects the platform.* "Implementation failure" as a category has been institutionalized in EdTech research, procurement, and customer success workflows. Platforms are not asked to demonstrate that their onboarding meets the standard they claim for student learning. The procurement checklist does not include the coherence test. No evaluation framework currently used by districts, institutions, or researchers operationalizes this criterion.

*Factor 3: The cost structure externalizes the incentive.* External PD providers absorb the cost of building onboarding. This makes it rational for platforms to externalize — the platform does not pay the cost of inadequate onboarding, the district does. The cost-to-benefit structure does not reward platforms for closing the gap.

**5.2 — Implications for the implementation failure attribution (300 words)**

When a platform with a well-documented adaptive methodology for student learning produces poor implementation outcomes that are attributed to teacher resistance or insufficient PD — and the platform's own onboarding does not meet the standard the platform claims is necessary for effective learning — the attribution is premature. This does not mean teacher resistance is never real or that external PD is never valuable. It means the design hypothesis (the platform's onboarding methodology is adequate) has not been tested, and attributing failure to the user without testing the design is not scientifically defensible.

Implication for evaluation frameworks: the coherence test should be a standard criterion in EdTech procurement evaluations, alongside LTI compliance, accessibility (WCAG), and evidence quality.

**5.3 — What a passing platform would require (400 words)**

Not a product pitch — a design specification derived from the platforms' own stated pedagogical principles:

1. A concept map for the onboarding curriculum, with prerequisite dependencies and Bloom-level assignments, built using the same backward-design methodology the platform applies to student content
2. Delivery of onboarding content through the platform's own adaptive modes — not documentation, not a Zoom walkthrough
3. A student-view simulator that allows instructors to experience the platform's failure modes (engagement-without-learning, IDK-IDK pattern, fluency trap) from the student side
4. A configuration sandbox where instructors can adjust guardrail settings and observe output changes — building the mental model needed for deployment decisions
5. Measurement of instructor learning with the platform's own signals — a delayed retrieval probe on platform concepts at 7 days, equivalent to what the platform administers for student content
6. An instructor-facing analytics layer that explains what each metric means and what it recommends — delivered through the platform's own Ask AI equivalent, not through a separate help center

Note: "This design specification is consistent with the architecture described in [book citation]. The author discloses a financial interest in a platform designed to meet these criteria. The specification above is derived from the platforms' own stated design principles and does not depend on the author's platform or its performance."

**5.4 — Limitations (200 words)**

- Single-coder design if a second coder was not available; inter-rater reliability not established
- Public documentation may underrepresent actual onboarding practice — some platforms may deliver adaptive onboarding in undocumented customer success workflows
- The coherence test is a novel criterion; it has not been validated against implementation outcomes (i.e., we do not yet have evidence that platforms passing the coherence test produce better adoption rates)
- The analysis is synchronic; platforms may be developing onboarding features not yet in public documentation

**Tasks:**
- [ ] Math-centricity claim — verify with a citation to the ITS evidence concentration in mathematics
- [ ] Attribution architecture claim — find a citation that operationalizes "implementation failure" as a category in EdTech research (EDUCAUSE? a curriculum implementation framework?)
- [ ] Cost-externalization claim — find the statistic or evidence that implementation/PD costs land on the district rather than the vendor
- [ ] Conflict of interest disclosure — draft the exact language (one paragraph, placed in the Acknowledgments and in the relevant Discussion subsection)

---

### Section 6 — Conclusion (300–400 words)

- Restate the null finding plainly
- Name the coherence test as the proposed addition to EdTech evaluation frameworks
- Name the attribution correction: implementation failure is a category that has been protecting platforms from design accountability
- Close with the positive framing: the cost collapse documented in the intelligent textbook literature has made it economically feasible to build onboarding that meets this standard; there is no longer a resource argument for externalizing the problem

---

## Task List by Day

### Day 1 — Lock the protocol (no research yet)
- [ ] Write the one-sentence coherence test definition
- [ ] Lock the three criteria (A, B, C) — do not adjust after Day 2
- [ ] Finalize the 12-platform list — confirm each is active
- [ ] Build the coding sheet
- [ ] Draft the standard inquiry email
- [ ] Decision: single-coder or two-coder?
- [ ] Pull and verify: Glimpse K12 statistic, Yoon threshold, RAND Europe synthesis, 14-college experiment
- **Day 1 output:** Locked protocol document (2 pages). Nothing is written for the paper yet.

### Day 2 — Data collection, Tier 1 (Free platforms)
- [ ] ASSISTments: documentation audit + inquiry email sent
- [ ] OLI/Torus: documentation audit + inquiry email sent
- [ ] Khanmigo teacher tier: documentation audit + inquiry email sent
- [ ] OpenStax Assignable: documentation audit + inquiry email sent
- [ ] Code each against A, B, C with evidence quotes
- **Day 2 output:** Coded rows for 4 platforms. Inquiry emails sent.

### Day 3 — Data collection, Tier 2 and Tier 3
- [ ] ALEKS: documentation audit
- [ ] Knewton Alta: documentation audit
- [ ] MATHia/Carnegie Learning: documentation audit
- [ ] Realizeit: documentation audit
- [ ] Acrobatiq/VitalSource: documentation audit
- [ ] CogBooks: documentation audit
- [ ] Code each against A, B, C with evidence quotes
- [ ] Check inquiry email responses from Day 2 platforms; log responses
- **Day 3 output:** Coded rows for 10 platforms. Running tally of results.

### Day 4 — Complete data collection + analysis
- [ ] 2 remaining platforms (Google LearnLM and one more TBD)
- [ ] All inquiry email responses logged
- [ ] Self-description gap: pull stated pedagogical principles for each platform, compare to onboarding documentation
- [ ] Identify any partial passes; document with specificity
- [ ] Build the results table
- **Day 4 output:** Complete coded dataset. Results table draft.

### Day 5 — Draft Sections 1, 2, 3
- [ ] Introduction (600–800 words)
- [ ] Background 2.1 and 2.2 (700 words)
- [ ] Background 2.3 — coherence test definition (400 words)
- [ ] Methods (500–700 words)
- **Day 5 output:** ~2,400 words drafted

### Day 6 — Draft Sections 4 and 5
- [ ] Results (800–1,000 words) — populate from coded dataset
- [ ] Discussion 5.1–5.4 (1,200–1,500 words)
- [ ] Conflict of interest disclosure language finalized
- **Day 6 output:** ~2,500 words drafted. Full paper draft complete.

### Day 7 — Abstract, conclusion, references, review
- [ ] Conclusion (300–400 words)
- [ ] Abstract (150 words)
- [ ] References — verify every citation used in the draft
- [ ] Read against the coherence test criteria — does the paper meet its own standard for evidence? (No claims that exceed the documented data; no vendor-claim evidence used without appropriate qualification)
- [ ] Confirm Northeastern APC eligibility with Amy Lewontin before submitting
- **Day 7 output:** Submittable draft.

---

## What the Paper Is Not

To prevent scope creep during the week:

- **Not a full review of intelligent textbook systems.** The landscape research document covers that. This paper cites it selectively for the implementation evidence and the platform descriptions, but does not re-survey the field.
- **Not a paper about whether intelligent textbooks work.** The Bastani finding, the VanLehn meta-analysis, the RAND MATHia study — these are cited as context for the coherence test, not as the paper's evidence base.
- **Not a paper about Medhavy.** One conflict-of-interest disclosure, one citation to the book for the design specification, no product claims.
- **Not a position paper.** The null finding is an empirical claim derived from documented platform behavior. The interpretation (attribution error) is argument, clearly marked as such. Keep these on separate tracks.

---

## The One Decision That Changes Everything

Before Day 2 begins, decide what you will do if you find a partial pass — a platform that meets Criterion A (methodology match) but not B (measurement match), for example.

**Option 1:** Report partial passes as partial passes, separate from full fails. This strengthens the paper because it shows the gradient — some platforms are closer than others — and makes the null finding more precise: no platform meets all three criteria.

**Option 2:** Treat anything less than full pass as a fail for the headline finding, and report partial passes in a footnote or supplementary table.

Recommendation: Option 1. The gradient is the more interesting scientific finding, and it is more honest. A reviewer will ask whether you found any partial passes; better to have answered that question in the paper than in response to the review.

---

## Conflict of Interest Language (Draft)

> The author is the designer of a learning platform intended to meet the design criteria described in Section 5.3. The platform has not been independently evaluated against those criteria. The criteria in Section 5.3 are derived from the platforms' own stated pedagogical principles and from the design framework in [Brown 2026, citation]. The author's financial interest in that platform does not affect the empirical findings reported in Sections 3 and 4, which are based solely on publicly available documentation from the evaluated platforms.

Place this in: (1) the Acknowledgments section, (2) a footnote at the first mention of Section 5.3 in the Discussion.
