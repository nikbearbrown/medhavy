# Medhavy Feature Strategy
## What the Platform Should Build — Derived from Research + Coherence Test

**Prepared for:** Nik Bear Brown  
**Sources:** Intelligent Textbook Systems landscape research (May 2026) + *How to Build an Intelligent Textbook* manuscript

---

## The Argument in One Sentence

The coherence test reveals a null finding across every deployed platform: **no intelligent textbook system uses its own pedagogical methodology to teach its own use.** Medhavy passes the test by design — but only if it builds the features that make passing the test visible, auditable, and deployable to the domains already in the textbook catalog.

---

## The Strategic Frame

The book's central claim is that the wrapper is the variable, not the model. The research confirms this — Bastani 2025, Kestin 2025, the IDK-IDK documentation — and the landscape review confirms that no commercial competitor has operationalized it as a design principle rather than a marketing claim.

The feature strategy below is organized around three axes:

1. **Closing the coherence gap** — features that make Medhavy pass its own test
2. **Extending the catalog advantage** — features that turn the 100+ textbook library into a structural moat
3. **Owning the measurement layer** — features that compete on the dimension no competitor has built

---

## Section 1: Close the Coherence Gap
### *The platform should be able to teach its own use, using its own methodology.*

This is the falsifying observation at the center of the peer-reviewed argument. If Medhavy ships this, it becomes the only platform in the field that passes its own test. That is a claims-based competitive advantage no vendor can match without rebuilding their architecture.

---

### Feature 1.1 — The Instructor Onboarding Track (built in Medhavy)

**What it is:** A structured onboarding course *for instructors*, delivered through Medhavy's own four-mode architecture — Ask AI, Quiz Me, Case Study, Glimmer — using the platform's own spaced retrieval, phase gates, and GLP measurement.

**Why it matters:** Every platform in the landscape (ALEKS, Khanmigo, MATHia, ASSISTments, OLI/Torus) externalizes onboarding to vendor walkthroughs, help documentation, or one-day PD events. None instructs its own use adaptively. The Yoon 14-contact-hour threshold, the RAND Europe synthesis, the Michigan Virtual pilot findings — all of them say teacher capacity is the binding constraint. The platforms hand this problem to districts.

**What it teaches:**
- What is a knowledge graph and how to read one (Quiz Me + Ask AI)
- What mastery-based progression means and why it differs from time-based progression (Case Study with failure-mode examples)
- How to interpret the GLP dashboard — what each signal means, what a false positive looks like (Glimmer: design a response protocol for a student whose Y1 is high and Y6 is near zero)
- The IDK-IDK pattern — experienced from the student side via a simulator session (see Feature 1.2)
- What the Bastani wrapper finding means for how the instructor configures Ask AI for their specific course

**Coherence test result:** Medhavy passes. It teaches its own use using its own methodology. Every other platform fails.

**Implementation note:** The onboarding track is a first-class Medhavy deployment, not a help center. It has a concept map, phase gates, GLP measurement, and a delayed retrieval probe. The instructor's GLP on the onboarding track predicts deployment quality. This is both a pedagogical claim and a leading indicator for customer success.

---

### Feature 1.2 — The Student-View Simulator

**What it is:** A sandbox mode where an instructor experiences the platform exactly as a student does — including all failure modes. The simulator has a preset "IDK-IDK" scenario: the instructor plays a student who types non-answers until the system reveals the answer, watches the session log record "engaged," and feels the fluency trap from the inside.

**Why no one has built it:** It requires acknowledging the failure modes publicly. Khanmigo could build this; it would require admitting the IDK-IDK pattern is an architectural failure rather than user behavior. They can't do it without undermining their product narrative. Medhavy can, because the book has already named the failure as the starting point.

**What the simulator contains:**
- Standard engagement scenario (student learning normally)
- IDK-IDK scenario (student gaming the Socratic mode)
- Fluency trap scenario (student reads AI explanation, feels confident, fails 7-day probe)
- Anxiety collapse scenario (student encounters Glimmer without sufficient prior knowledge, abandons)
- Phase gate intervention (student blocked from Glimmer until prerequisites are met, re-routes to Quiz Me)

**Output:** After each scenario, a debrief dashboard showing what the engagement metrics reported vs. what the GLP signals showed. The gap is the lesson.

**Why this is load-bearing for the peer-reviewed argument:** The coherence test requires not just that the platform can teach its use, but that the teaching is experiential — not readable. The simulator is the mechanism. A teacher who has felt the fluency trap has a mental model no workshop can replicate.

---

### Feature 1.3 — The Configuration Sandbox

**What it is:** A teacher-facing environment where Ask AI guardrail settings can be adjusted in real time, with live preview of how outputs change. Not an IT function — a pedagogical learning activity.

**The three dimensions instructors can adjust:**
- Context injection depth (section only → chapter → prerequisites graph → full book)
- Hint-vs-answer guardrail (strict Socratic → hint ladder → partial answer → full answer)
- Misconception trap density (off → surface misconceptions flagged → deep misconceptions targeted)

**What the instructor observes:** The same student question answered under each configuration, side by side. The "lost in the middle" degradation when full-book context is injected. The Bastani GPT-Base outcome emerging when the hint guardrail is relaxed. The GPT-Tutor outcome when it is tight.

**Why this is a feature, not a settings page:** The instructor who has *experimented* with what happens when hints are removed has built the mental model needed to make deployment decisions. The instructor who attended the demo has not. Configuration-as-learning-activity is the design move.

---

### Feature 1.4 — The Dashboard Explainer Layer

**What it is:** Every metric on every instructor dashboard has an embedded, inline explanation of what it actually measures — triggered on hover or first encounter — delivered in Medhavy's own Ask AI mode.

**The four questions answered per metric:**
1. What is this measuring? (Plain language, no jargon)
2. What action does a high/low reading recommend?
3. What does a false positive on this metric look like?
4. How does this metric relate to genuine learning vs. engagement?

**Why this matters specifically:** Dashboard blindness is one of the most consistently documented barriers to instructor adoption in the implementation literature. The ASSISTments research, the MATHia LiveLab data, the Khanmigo teacher-tools evaluation — all show teachers who don't understand a metric ignore it. The explainer layer is the difference between a dashboard that gets used and one that gets closed.

**Coherence test implication:** The platform is using Ask AI to explain Ask AI's outputs. It is using its own methodology to teach its own use at the dashboard layer. Pass.

---

## Section 2: Extend the Catalog Advantage
### *Turn 100+ textbooks into a structural moat, not a list of SKUs.*

The textbook catalog (100+ titles across biology, chemistry, physics, math, psychology, history, philosophy, economics, finance, CS, and more) is the platform's most underutilized asset. Every competitor is building a single AI layer over a single content type. Medhavy has a cross-domain library. The features below make that cross-domain coverage a compounding advantage rather than a content storage problem.

---

### Feature 2.1 — The Tic TOC Public Library

**What it is:** A sharable, browsable library of completed Tic TOC concept maps — one per textbook in the catalog — with prerequisite graphs, Bloom-level assignments, mode-appropriateness flags, and phase-gate specifications visible and downloadable.

**Why it creates a moat:** A faculty member choosing between Medhavy and Knewton Alta can see exactly what Medhavy's curriculum layer specifies for their course. The concept map is evidence of design discipline. A competitor who has not run backward design on their content catalog cannot show this. The map is the differentiator.

**Secondary function:** Instructors can fork a public Tic TOC map and modify it for their course. The contribution model builds the library. The library reduces onboarding friction. The network effect is the moat.

**What to prioritize first:** The 20 highest-enrollment subject areas in the catalog (introductory biology, introductory chemistry, college algebra, intro statistics, intro psychology, US history, world history, principles of economics, intro philosophy, intro programming). These are the courses where the largest number of instructors will evaluate the platform and where the Knewton Alta / ALEKS competition is most direct.

---

### Feature 2.2 — Cross-Textbook Prerequisite Linking

**What it is:** A system that surfaces prerequisite relationships *across* textbooks in the catalog — the cross-discipline edges the Chapter 9 warfarin example named explicitly (vitamin K cycle from biochemistry as a prerequisite for pharmacology; classical mechanics as a prerequisite for thermodynamics).

**Why it exists nowhere else:** Commercial competitors couple their adaptive engine to a single publisher's content graph. Cross-textbook prerequisites require content coverage across domains. Medhavy has it. No one else does.

**The student-facing feature:** When a student hits a concept they are failing, the platform can surface: "This concept depends on [concept from a different textbook in your library]. You have not demonstrated mastery of that prerequisite. Would you like to start there?" The remediation goes to the right place rather than doubling down on the wrong concept.

**The instructor-facing feature:** A cross-textbook prerequisite audit at the start of each course — "students entering this course typically lack mastery of these three prerequisite concepts from prior courses." The audit runs on GLP data from prior cohorts, not on the instructor's assumption.

---

### Feature 2.3 — Domain-Specific Wrapper Presets

**What it is:** Pre-configured Ask AI wrapper specifications — context injection depth, hint ladder design, misconception trap targets — tailored to specific subject domains in the catalog.

**The Bastani implication:** The GPT-Tutor wrapper that preserved learning in a Turkish high school math course is not the same wrapper that should run for a medical school pharmacology course, a US history survey, or an introduction to philosophy. The misconceptions are domain-specific. The hint ladder should be calibrated to the field's characteristic confusion points. The context-injection depth should match the prerequisite density of the domain.

**What this looks like for specific catalog domains:**
- **Medical/biology content:** High misconception-trap density, strict hint guardrail, vitamin K / CYP450 / receptor-theory error patterns pre-loaded
- **Mathematics content:** Step-level feedback mode, worked-example anchoring, common computational error patterns
- **History/philosophy/social science content:** Argument-structure scaffolding, source-evaluation prompts, claim-vs-evidence distinction as the primary misconception target
- **Programming content:** Error message interpretation mode, debugging scaffold, common conceptual-vs-syntactic error distinction

**Why this is not just prompt engineering:** The wrappers are products of the Sadler insight — domain-specific pedagogical content knowledge in the prompt architecture. They are built from the catalog's domain coverage and from the misconception data the GLP measurement layer accumulates.

---

### Feature 2.4 — The Homes of Hope Plus One Track (Proof of Concept for Minimum Viable Deployments)

**What it is:** A fully specified, publicly documented Medhavy deployment for the Homes of Hope vocational English program — the Priya case from Chapter 3, built as a real product.

**Why it matters strategically:** The field argues about whether AI tutoring is for elite institutions or accessible to underserved populations. Medhavy's architecture argument (the complexity threshold test from Chapter 3) says the right tool is often simpler than the full architecture — Anki + a Humanitarians AI volunteer, not a $24,000 platform license. The Homes of Hope deployment demonstrates the principle: Medhavy as conductor, Anki and the volunteer as instruments, GLP measurement tracking the few signals that matter (Y6 retrieval decay, Y2 error trajectory on job-specific vocabulary).

**The coherence test application:** If Medhavy can teach the Homes of Hope students vocabulary acquisition, it can teach instructors platform use. Same architecture, different domain, smaller scale. The minimum viable deployment is also the demo of the conductor frame working at minimum cost.

**Strategic signaling:** The deployment demonstrates that Medhavy's architecture scales *down* as well as up. Every EdTech platform is designed for maximum feature usage. Medhavy is designed to use exactly the features the learning problem requires — no more, no less. That is a differentiator in the OER market and the nonprofit market, neither of which can afford ALEKS pricing.

---

## Section 3: Own the Measurement Layer
### *Build the thing no competitor has: a trustworthy learning signal.*

The landscape research is unambiguous — no deployed platform currently measures genuine learning rather than engagement proxies. The GLP framework (seven components, delayed retrieval probe) is the architectural claim the peer-reviewed paper builds toward. These features make the claim operational.

---

### Feature 3.1 — The Seven-Day Delayed Retrieval Probe (Standard)

**What it is:** A systematized, automatic, lightweight assessment delivered seven days after every significant concept encounter — Quiz Me, Case Study, or Glimmer completion. One to three items, calibrated to the concept's Bloom level, delivered via the platform's standard Quiz Me interface so it feels like ordinary practice, not a test.

**Why it is the most important single feature Medhavy could ship:** The 7-day delayed retrieval probe is the only measurement that directly tests storage strength rather than retrieval strength. Every platform in the competitive landscape uses immediate post-test or session completion as its primary learning signal. Those signals measure the fluency trap, not learning. The probe directly measures what the engagement metrics cannot.

**What it changes:** Every instructor dashboard, every student progress view, every engine reward signal becomes a genuine learning signal rather than an engagement proxy. This is the feature that makes the Bastani argument operational: the platform can now *see* the difference between the GPT-Base student and the GPT-Tutor student.

**Implementation note:** The probe must be perceptually lightweight — students should not experience it as a test, only as a Quiz Me session that arrived a week after a concept they remember engaging with. Framing matters. "A concept from last week" is better than "your retention assessment."

---

### Feature 3.2 — The GLP Dashboard (Student-Facing)

**What it is:** A student-facing view that shows genuine learning strength per concept — not a score, not a completion bar, but a calibrated probability estimate with visible decay curves.

**What it shows:**
- Retrieval strength today (predicted probability of correct recall right now)
- Storage strength estimate (how stable this knowledge is likely to be at 30 days)
- Decay rate (how fast this concept's strength is decreasing without review)
- Next review recommendation (FSRS-scheduled, with reasoning shown: "This concept has a 14-day stability window; your next review is in 3 days to keep it above 90% retrievability")

**Why students need this:** The fluency trap is a metacognitive failure — students don't know they don't know. The GLP dashboard is the measurement layer's output in student-readable form. It is also the transparency commitment from the book's three transparency types (Decision transparency: "I recommend this because...").

**What this is not:** A gamification layer. No streaks, no XP, no badges. The decay curve is information, not motivation. If the habit-loop design is correct (the due-today counter as the primary adoption mechanism), gamification is not needed and would compromise the signal's credibility.

---

### Feature 3.3 — The Pre-Registration Interface

**What it is:** A tool that allows instructors to pre-register predictions about their course before deployment — "I expect students to show high engagement but low 7-day retention on the pharmacokinetics module" — and tracks those predictions against actual GLP outcomes.

**Why this is a feature, not a research workflow:** Pre-registration prevents the Exploring-After-Results-are-Known (HARKING) failure mode at the instructor level. An instructor who has pre-registered their prediction and sees it confirmed or disconfirmed is doing what the book calls "experiment-as-product." An instructor who sees only results without a prior has no epistemic anchor for interpreting them.

**The coherence test application:** Medhavy teaches instructors to do science on their own courses. Pre-registration is the mechanism. The platform that can teach this is the platform that takes "experiment-as-product" seriously as a design commitment rather than a preface talking point.

---

### Feature 3.4 — The Engagement vs. Learning Audit Report

**What it is:** A per-course, per-cohort report that shows, side by side, what engagement metrics indicate and what GLP signals indicate — surfacing the gap where they diverge.

**Format:**
```
Concept: First-pass metabolism (Pharmacology, Chapter 4)

Engagement signal:         HIGH
  - Average session time: 11.2 min (above norm)
  - Completion rate: 94%
  - Return rate: 87%

GLP signal:                LOW
  - 7-day retrieval probe: 34% accuracy (below threshold)
  - Y6 decay rate: fast (half-life ~4 days)
  - Y3 cross-context transfer: 28% (below threshold)

Diagnosis: Fluency trap likely. Students are engaging with the 
material but not consolidating it. Recommend: 
  1. Add misconception-targeted content (Tier 2 review flagged)
  2. Increase spacing interval on Quiz Me for this concept
  3. Gate Case Study until 7-day probe > 70%
```

**Strategic value:** This report is the peer-reviewed paper's argument made operational. It demonstrates the gap between engagement-as-proxy and genuine learning measurement in the instructor's own course data. It is also the primary sales artifact for the procurement conversation — show the district the gap in their current platform's data, then show Medhavy's data for the same course.

---

## Section 4: The Catalog-Specific Build Priority

Given the 100+ textbooks in the catalog, the feature build should be sequenced against the domains where:
1. Evidence of the coherence gap is strongest (highest-enrollment courses)
2. GLP signal collection is most tractable (well-defined Bloom levels, clean answer keys)
3. The competitive displacement opportunity is clearest (ALEKS, Knewton Alta, Khanmigo overlap)

**Priority Tier 1 — Build first:**
- **Introductory biology** (biology-plus-one, biology-plus-one-genetics-and-evolution, biology-plus-one-the-cell): High enrollment, clean misconception structure, ALEKS/DreamBox displacement
- **College algebra / pre-algebra** (college-algebra-bundle-with-llms, prealgebra-bundle-with-llms): Direct Knewton Alta / ALEKS competition, strong retrieval-practice signal tractability
- **Introductory statistics** (introductory-statistics-bundle-with-llms, bayesian-probability-with-llms): High enrollment, well-defined misconceptions (p-value misinterpretation, confidence interval confusion), no strong competitor with GLP-equivalent measurement
- **Introductory psychology** (psychology-with-llms): High enrollment, Khanmigo overlap, strong cross-context transfer signal for applying concepts to novel cases
- **Computational skepticism / AI literacy** (computational-skepticism-for-ai, conducting-ai): These are Medhavy's own domain — a deployment here is the coherence test run publicly

**Priority Tier 2 — Build second:**
- Chemistry, physics, economics, history, philosophy bundles
- Medical/biology content (cancer-biology, microbiology-with-llms) — highest stakes, requires Tier 3 content review, but strongest GLP differentiation story
- Programming courses (introduction-python-programming-claude) — GLP measurement for code is tractable via step-level error trajectory

**Priority Tier 3 — Catalog depth:**
- Specialty content (electron-microscopy, quantum-mechanics) — small audiences, but strongest domain-specificity PCK story
- Vocational/applied content (homes-of-hope-plus-one, business ethics) — minimum viable deployment proof of concept

---

## Section 5: The Platform-as-Argument

The peer-reviewed paper argues that no platform has passed the coherence test. The EdSurge piece asks why the most expensive EdTech deployments produce "implementation failure." The ISTE+ASCD piece asks what instructional leaders should demand from their next procurement. The EL Magazine piece asks what teachers should expect from the tools they are given.

All four articles point back to the same product claim: **Medhavy is the platform that passes its own test.**

The features above are not a roadmap. They are evidence. Each feature is a falsifiable claim about what the platform can do that no competitor can. Each claim can be verified against the coherence test, the Bastani finding, the Sadler result, the seven GLP signals.

The competitive position is not "Medhavy has more features than ALEKS." It is: **every other platform externalizes its hardest design problem. Medhavy is designed around that problem.**

That is the argument. The features are what make it true.

---

## Summary: The Minimum Viable Coherence-Test Pass

If Medhavy ships nothing else from this document, it should ship these three things:

1. **The Instructor Onboarding Track** — built in Medhavy, using Medhavy's four modes, with GLP measurement. This is the coherence test passed in product form.

2. **The Seven-Day Delayed Retrieval Probe** — standardized, automatic, lightweight. This is the measurement layer made operational and the engagement-proxy gap made visible.

3. **The Engagement vs. Learning Audit Report** — side-by-side per course. This is the peer-reviewed argument made into a sales artifact.

Everything else in this document extends, deepens, or scales those three. The three are the argument. The rest is the moat.
