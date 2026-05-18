# TIKTOC.md
# How to Build an Intelligent Textbook
**Author:** Nik Bear Brown · ni.brown@neu.edu · Bear Brown & Company
**Publisher:** Bear Brown, LLC
**Format:** Kindle / KDP ($1 / Kindle Unlimited) + epub (direct distribution)
**Status:** TIKTOC complete — ready for Research Gatherer → Chapter Writer pipeline
**Version:** 1.0

---

## Book concept summary

This book teaches **how to design an intelligent textbook** — specifying
its architecture, its pedagogical commitments, and its technology decisions
— to **domain experts with content and conviction, and the developers they
work with**, by providing the design specification framework that neither
the EdTech optimists nor the skeptics have produced, filling the gap left
by books that cherry-pick the positive (Khan) or cherry-pick the negative
(Horvath) without ever asking what you would have to build if you took all
the evidence seriously. It succeeds if the reader — whether a Charles Fadel
type or the developer who got handed an API spec — holds a complete,
defensible design map by the final chapter, and if both readers are now
capable of having the same conversation about the same decisions.

**One-sentence logline:**
The field has spent twenty years arguing about whether EdTech works;
this book asks what you would have to build if you took all the evidence
seriously — and hands you the design specification.

## Central thesis

"This book argues that the intelligent textbook field has been asking the
wrong question — whether AI helps or harms — which means that no one has
produced the design specification for what you would have to build if you
took all the evidence seriously, and this matters because without that
specification, domain experts keep commissioning platforms that measure
engagement and call it learning, developers keep building hammers, and the
IDK-IDK problem keeps getting logged as success."

**The book this is NOT:**
*Brave New Words* (Khan). Not the optimistic case for AI in education.
Not a book that picks a side. Human + AI, not human versus AI. An
intelligent textbook that is just a hammer is going to have difficulty
when the wood needs sawing.

## Primary readers — two people, one book

**The Charles Fadel type:** Domain expert. Has content, conviction, and
a coherent argument about what education is missing. Zero pathway from
"I have this content" to "here is a working intelligent textbook that
actually measures learning." Needs to understand what he is commissioning.

**The developer who got handed API.md:** Can build what is specified.
Doesn't know why the Glimmer exists, why the phase gates matter, why
engagement metrics are the wrong optimization target. Makes bad tradeoff
decisions under pressure because they don't understand what they're
trading away.

**Why one book serves both:** The book is the shared language. Charles
can say "Socratic isn't right here because of retrieval interference" and
the developer can say "we already have something close — here's what it
does" and they're talking about the same design decision in the same terms.

## Book type and deployment

**Field-defining monograph with a practical landing.** Read front to back.
The argument builds. Every chapter ends with a real-world or illustrative
case (simulated cases labeled as such). The final chapter delivers the map.

**Three circulation paths:**
1. Kindle / $1 / Kindle Unlimited — Learning Engineering community (~3,600
   members), Charles Fadel type, developer who got handed API.md
2. Direct epub — colleague-to-colleague handoff before a build starts
3. Course assignment — graduate EdTech, instructional design, learning
   engineering programs

**Feedback loop is structural:** The community says "Chapter 6 is wrong
about X" or "we built something like your Glimmer and here's what actually
happened." The book sharpens through deployment. This enacts the thesis:
the platform is an experimental apparatus. So is the book.

## Three comparable texts

**Hattie, *Visible Learning*:** Everyone in this community knows it.
Wildly different views on it. The 0.40 hinge point appears in this book,
contested. Used correctly here as a cost-effectiveness guideline, not
an absolute binary.

**Khan, *Brave New Words*:** The community knows it and most hate it.
The IDK-IDK problem in book form: optimistic about engagement, thin on
measurement, confident about outcomes the data doesn't support. This book
takes the promise seriously and asks what it would actually require to
deliver it.

**Horvath, *The Digital Delusion*:** The antibody. Correctly diagnoses
the hammer problem. Doesn't build the toolbox. Cherry-picks the negative
the way Khan cherry-picks the positive. Both are arguing about whether
EdTech works. This book asks what you would have to build if you took all
the evidence seriously.

## Three-act learning arc

**Arc statement:** This book takes the reader from *recognizing the failure
they've already witnessed or been handed* to *conducting the design
conversation that produces a specification worth building from* by first
establishing precisely why the field keeps failing in both directions and
what the right question actually is (Act One: Chapters 1–4), then building
the complete architecture layer by layer with evidence at every decision
point (Act Two: Chapters 5–11), then naming the bets honestly and
delivering the tool that converts thinking into specification
(Act Three: Chapters 12–13).

**Act One → Act Two transition condition:** The reader can answer: "Given
what the evidence actually shows — all of it — what would the architecture
have to do to prevent the IDK-IDK failure?"

**Act Two → Act Three transition condition:** The reader can specify all
four layers for a given learning problem.

## Load-bearing chapters (cannot be skipped)

Chapters 1, 4, 6, 8. The introduction should include a one-paragraph
reading guide naming these four (the conductor-frame chapter plus three downstream load-bearing chapters).

## Illustrative platform: Medhavy

Medhavy is used as the primary illustrative case throughout. It appears
as both:
- **Medhavy the platform** — what gets built (the cancer textbook, the
  physics textbook, the Hub architecture)
- **Medhavy the instrument** — the design conversation tool (Chapter 13)
  that converts thinking into a buildable specification

The Medhavi Hub architecture (API.md, ARCHITECTURE.md) is available in
pantry for technical layer descriptions. Use at appropriate depth —
enough for Charles to understand what he is commissioning, enough for
the developer to recognize the architecture.

## Pantry contents available for research

- `ask-ai-research.md` — ITS and generative-AI chatbot effectiveness,
  Bastani PNAS 2025, guardrail design
- `case-study-research.md` — CBL literature, Thistlethwaite 2012,
  pre-written vs. on-demand cases
- `quiz-me-research.md` — retrieval practice, spaced repetition, FSRS,
  SM-2, Cepeda 2006/2008
- `quiz-me-habit-research.md` — Anki habit system, due-today counter,
  Zeigarnik closure, Fogg/Eyal/Wood
- `glimmer-research.md` — generative learning, ill-structured problems,
  Jonassen 1997, Fiorella & Mayer 2016
- `glimmer-displacement-research.md` — AI displacement, studio-critique,
  scaffolding fading, Renkl, van Merriënboer
- `concept-sequencing-research.md` — frequency sequencing, BKT, DKT,
  prerequisite chaining, importance weighting
- `domain-specific-instruction-research.md` — PCK, situated learning,
  Level-3 specificity, Sadler 2013
- `educational-media-economics-research.md` — Sesame Street, Mayer CTML,
  cost-collapse asymmetry, minimum viable audience
- GLP preprint (Frictional / Irreducibly Human series) — seven friction
  components, decoupling problem, ensemble architecture
- API.md — Medhavi Hub API reference
- ARCHITECTURE.md — Medhavi Hub system architecture
- Lexicon.txt — Medhavy vocabulary/lexicon features
- MVAL.txt — Medhavy learning value features
- `PEDAGOGY ARCHITECTURE.txt` — Medhavy pedagogical architecture
- `Contextual Bandits.txt` — contextual bandit implementation notes
- Computational Skepticism Substack — author's published review of
  Horvath (The Digital Delusion)
- Homes of Hope Plus One book.md — Course 2 complete, Priya case

## Chapter anatomy (all chapters)

Every chapter must contain:
1. Learning objectives (Bloom's level explicit, 3–5 outcomes)
2. Opening case (failure-first or concrete case before any framework)
3. Core content sections (4–6), each: concept → example → application
4. Worked example (real or explicitly labeled illustrative/simulated)
5. Common misconceptions (state as plausible claim, then why it fails)
6. Assessable exercises (minimum 3; at least one at Apply or above;
   at least one requiring the reader to produce something)
7. What would change my mind (one paragraph — specific empirical
   finding that would require revising the chapter's central claim)
8. Still puzzling (2–4 open questions the chapter raises but does
   not resolve)
9. Chapter closing / bridge to next chapter (one question this
   chapter raises that the next chapter answers)

**Enforcement:** A draft chapter missing items 4, 7, 8, or 9 is
incomplete. Do not advance to editorial review without resolving it.

---

## Chapter list

---

### ACT ONE — THE RIGHT QUESTION (Chapters 1–4)
*What this act does: names what Medhavy is (the conductor frame),
names the failure precisely, establishes that the field is asking
the wrong question, calibrates the reader against over-building,
delivers the complete evidence base.*

---

### CHAPTER 1 — What is Medhavy?

**Filename:** `01-what-is-medhavy.md`
**One-line:** The reader learns to name Medhavy as the conductor (not
the intelligent textbook); to order the three audiences — learner,
instructor, organization — in the sequence the frame requires; and
to apply the experiment-as-product test to a given EdTech deployment.
**Act:** One
**Bloom's primary level:** Understand → Evaluate
**Load-bearing:** YES — establishes the frame that runs every later chapter

**Learning outcomes:**
1. (Understand) State the conductor frame in one sentence and explain
   why Medhavy is not the intelligent textbook but the system that
   conducts what might be one.
2. (Apply) Order the three audiences — learner, instructor,
   organization — in the sequence the frame requires and explain why
   the order matters more than the content of any single answer.
3. (Analyze) Identify when a platform has solved the wrong problem
   because it has the three audiences in the wrong order.
4. (Evaluate) Apply the experiment-as-product test: is the deployment
   running a continuously controlled experiment, or is it defending
   a model?
5. (Understand) Explain why transparency is the precondition for the
   trust that learning requires.

**Opening case:** The conductor metaphor. The conductor does not play
the instruments. She decides which one plays, when, and for how long
— based on evidence, not assumption. And she adjusts as the evidence
changes. The chapter opens with the metaphor and immediately defends
the distinction the metaphor makes load-bearing for the rest of the
book: Medhavy is the conductor; the intelligent textbook is whatever
the conductor conducts. Sometimes that is the four-layer platform.
Sometimes it is Anki, a Kindle book, and a Humanitarians AI volunteer
on a Zoom call.

**Core content:**
1. Not a feature. Not a product category. A frame.
2. The three questions, in order — learner first, instructor second,
   organization third; why the order is the argument
3. Experiment is the product — the impact of AI on learning is
   obvious; the right implementation is not; Medhavy doesn't pick
   a model and defend it
4. Without transparency, there is no trust; without trust, there is
   no learning — data, decision, and uncertainty transparencies
5. Worked example — what the conductor does in twenty minutes of a
   Wednesday afternoon (Priya, Anki, the volunteer Zoom, the
   medical-vocabulary domain shift)

**Worked example:** Priya's Wednesday afternoon — Anki review,
six Again cards in the medical-vocabulary domain, the conductor's
recommendation for Friday combining role-play and Anki, the consent-
based notification to Priya that closes the loop. The reader watches
the conductor work at the scale of a single learner's twenty minutes.

**Assessable exercises:**
1. (Analyze) Apply the three-questions test to a learning product
   you have used. Where did the product land?
2. (Apply) Sketch a Medhavy conductor specification for a learning
   problem you understand well.
3. (Evaluate) Diagnose the frame of a vendor's pitch deck that opens
   with institutional dashboards before student experience.
4. (Create) Write a one-paragraph transparency disclosure for a
   hypothetical learner.

**Bridge to Chapter 2:** Chapter 2 is titled *What Is an Intelligent
Textbook?* — the question about the second-order object, the thing
the conductor conducts. The chapter catalogs the two failure modes
the field has been committing in opposite directions. The conductor
frame is the diagnostic.

**Key pantry sources:** Bear's *What is Medhavy?* philosophy text
(verbatim throughout chapter); `02-when-anki-is-enough_notes.md`
(Priya case grounding); `medhavy-1.5-feature-roadmap.md` (instrument
framing).

---

### CHAPTER 2 — What Is an Intelligent Textbook?

**Filename:** `02-what-is-an-intelligent-textbook.md`
**One-line:** The reader learns to name both failure modes precisely and
understand why the field keeps committing both simultaneously.
**Act:** One
**Bloom's primary level:** Analyze
**Load-bearing:** YES

**Learning outcomes:**
1. (Understand) Explain why content was never the product education was
   selling — using the MIT OpenCourseWare experiment and the Khanmigo
   IDK-IDK data as the evidence.
2. (Analyze) Distinguish between the "no AI" failure mode and the "all AI"
   failure mode, and name the specific mechanism by which each produces
   worse outcomes than its proponents acknowledge.
3. (Understand) Describe the four-layer architecture of an intelligent
   textbook and explain why the integration of layers is the architecture,
   not the layers themselves.
4. (Evaluate) Identify which failure mode a given EdTech deployment
   represents, using the engagement-vs-learning distinction as the
   diagnostic.

**Opening case:** The IDK-IDK incident. A student types "I don't know,
I don't know" into a Khanmigo Socratic prompt and moves on. The system
logs them as engaged. They are not learning. The most ambitious AI
tutoring deployment in history — backed by the most credentialed EdTech
optimist in the field — produced this. Not because the AI was bad.
Because the architecture was wrong.

**Core content:**
1. Content was never the product — MIT OpenCourseWare, enrollment did
   not collapse, what got more valuable was the experience
2. The no-AI failure mode — professor absorbs automatable work,
   irreducibly human work gets crowded out by accident
3. The all-AI failure mode — chatbot becomes the relationship,
   IDK-IDK logged as engaged, measurement system reports success
4. The third position — not a compromise, a different question:
   what would you have to build if you took all the evidence seriously?
5. The four-layer architecture introduced as a sketch — Book Library,
   Tic TOC, Adaptive Engine, Measurement Layer
6. The platform is opinionated. The model has no opinions of its own.

**Worked example:** A real EdTech deployment where engagement metrics
reported success while learning outcome data showed failure. Walk through
what the engagement dashboard showed, what a learning evidence dashboard
would have shown, and the gap between them. (Illustrative case — label
as such if not sourced.)

**Assessable exercises:**
1. (Apply) Given a description of an EdTech deployment, classify it
   as "no AI," "all AI," or "neither" failure mode and identify the
   specific architectural decision that produced the outcome.
2. (Analyze) The Khanmigo IDK-IDK incident — what would the engagement
   dashboard have shown? What would a learning evidence dashboard have
   shown? What is the gap?
3. (Evaluate) MIT OpenCourseWare increased enrollment rather than
   collapsing it. What does this prove about content as the product —
   and what does it not prove?

**Bridge to Chapter 3:** Before the architecture is introduced, the
reader needs the honest check: for some learning problems, the right
answer is a simpler tool. Chapter 3 delivers that check.

**Key pantry sources:** ask-ai-research.md (IDK-IDK / Khanmigo data),
educational-media-economics-research.md (MIT OpenCourseWare framing),
Computational Skepticism Substack

---

### CHAPTER 3 — When Anki Is Enough

**Filename:** `03-when-anki-is-enough.md`
**One-line:** The reader learns to apply the complexity threshold test
before reaching for the full architecture.
**Act:** One
**Bloom's primary level:** Evaluate
**Load-bearing:** No (skippable for a reader who already knows they
need the full architecture — they lose calibration and the Homes of
Hope case but not a capability build)

**Learning outcomes:**
1. (Evaluate) Apply a complexity threshold test to a learning problem
   and determine whether the full intelligent textbook architecture is
   warranted or whether simpler tools are the correct answer.
2. (Analyze) Identify the three conditions under which intelligent
   textbook complexity earns its cost: multi-layered capability build,
   live instrumentation requirement, and adaptive sequencing across
   concepts that cannot be pre-ordered.
3. (Apply) Map a specific learner profile and learning goal to the
   minimum viable tool set.
4. (Evaluate) Distinguish between "this tool is insufficient" and
   "this tool is the wrong tool."

**Opening case:** Priya. 19 years old. Six years in a Homes of Hope
residence in Hyderabad. Telugu and basic English. A smartphone. The three
most accessible jobs in Hyderabad's employment market — BPO customer
service, hospital support, NGO administration — all require English. The
door is closed. Anki opens it. With a Kindle book. With a Humanitarians
AI volunteer from the BPO sector on a Zoom call. Zero dollars.

**Core content:**
1. What Priya needs — 500-word job-functional vocabulary, spaced
   repetition, a human who came from the sector she is entering
2. The complexity threshold test — three questions: adaptive sequencing
   required? Live instrumentation required? Multi-layered capability build?
3. The three conditions that earn the full architecture — medical school
   clinical reasoning, engineering design judgment, ill-structured domains
4. The tool is not the problem. The context is the problem. — Homes of
   Hope girl on TikTok vs. Homes of Hope girl using Anki to get a job.
   Same phone. Different context.
5. Human + AI, not human versus AI — Priya's volunteer is the
   irreducibly human part; Anki is the AI part; neither works without
   the other

**Worked example:** Side-by-side comparison. Priya's learning problem
(vocabulary acquisition, job placement goal, phone-based delivery, zero
budget) versus a medical school clinical reasoning problem (diagnosis under
ambiguity, transfer required, performance indistinguishable from
understanding without live instrumentation). Same complexity threshold
test — completely different answers. Show the test applied to both.

**Assessable exercises:**
1. (Apply) Given three learning problems — corporate onboarding,
   surgical residency, professional certification exam — apply the
   complexity threshold test and specify the minimum viable tool set.
2. (Evaluate) A well-meaning EdTech vendor proposes replacing Priya's
   Anki deck with a full adaptive platform. What is the honest
   cost-benefit analysis?
3. (Analyze) What would have to change about Priya's learning problem
   to make the full architecture the right answer?

**Bridge to Chapter 4:** The complexity threshold test claims certain
tools work for certain problems. How do we know? Chapter 4 delivers the
evidence base.

**Key pantry sources:** Homes of Hope Plus One book.md (Priya case),
quiz-me-research.md (Anki / spaced repetition evidence),
quiz-me-habit-research.md (why Anki works as a habit system),
educational-media-economics-research.md (cost arguments)

---

### CHAPTER 4 — The Evidence Base

**Filename:** `04-the-evidence-base.md`
**One-line:** The reader acquires the evidence base that every
architecture chapter will cite — and the diagnostic for identifying
cherry-picked evidence when they encounter it.
**Act:** One
**Bloom's primary level:** Analyze
**Load-bearing:** YES

**Learning outcomes:**
1. (Analyze) Distinguish between the evidence Khan uses, the evidence
   Horvath uses, and the evidence both omit.
2. (Evaluate) Apply Hattie's 0.40 effect size threshold correctly:
   as a cost-effectiveness guideline, not an absolute binary.
3. (Understand) Explain the Bastani PNAS 2025 finding and identify the
   design variable that determined the difference between outcomes.
4. (Analyze) Identify which findings from the ITS, spaced repetition,
   CBL, and generative assignment literatures apply to a specific
   intelligent textbook design decision.
5. (Evaluate) Assess a claimed EdTech evidence base for cherry-picking.

**Opening case:** The Butter Knife Fallacy. Judging the scalpel's
potential by observing its average misuse. The PISA data showing 6+
hours of daily computer use correlates with a 66-point score drop is
real and important. It is also a description of indiscriminate
high-dosage deployment, not a description of what a well-designed
constrained tool produces.

**Core content:**
1. What Horvath proves beyond reasonable doubt — PISA/TIMSS/PIRLS
   correlations, meta-analytic synthesis (ES = +0.29), smartphone harm
2. Where Horvath overreaches — 0.40 as absolute binary, "nearly every
   context" claim provably false when ITS (ES = +0.52) exists
3. What Khan gets right — the promise is real; engagement-as-proxy-for-
   learning is the problem, not the AI
4. The Bastani PNAS 2025 finding — same GPT-4, two prompt wrappers,
   opposite outcomes; the guardrail design is the variable
5. The ITS literature — ES +0.40 to +0.70 for well-designed ITS;
   what makes them work
6. The spaced repetition canon — Roediger & Karpicke 2006, Cepeda
   2006/2008, retrieval practice mechanism
7. The CBL literature — Thistlethwaite 2012 BEME synthesis, what the
   evidence licenses for solo asynchronous AI-facilitated CBL
8. The generative assignment literature — Fiorella & Mayer 2016,
   Jonassen 1997, what Glimmer-style assignments can claim

**Worked example:** The author's own published analysis of Horvath's
*The Digital Delusion* (available in Computational Skepticism Substack).
Walk through the evidence audit: what the book got right, what it
overreached, and what a complete reading of the literature shows. This
is the chapter's meta-lesson: how to read EdTech evidence claims.

**Assessable exercises:**
1. (Evaluate) A vendor claims their platform produces ES = +0.45 based
   on a meta-analysis of 12 studies. Identify three questions you must
   ask before accepting this claim.
2. (Analyze) Horvath's claim that EdTech fails "in nearly every context"
   — what does the evidence actually support, and what does it not?
3. (Apply) The Bastani finding — what does it imply for the Ask AI
   mode's guardrail design? What specific design decision does it justify?

**Bridge to Chapter 5:** The reader now holds the evidence base. The
architecture chapters can cite rather than argue. Chapter 5 delivers
the blueprint: why the layers must be integrated, and what is lost when
they are not.

**Key pantry sources:** ALL nine pantry research notes are primary
sources for this chapter. Computational Skepticism Substack review of
Horvath is the worked example. Bastani PNAS 2025 is the single most
important finding — verify citation.

---

### ACT TWO — THE ARCHITECTURE (Chapters 5–11)
*What this act does: delivers the complete four-layer architecture —
measurement, modes, engine, curriculum design, content, economics —
in the sequence that makes each layer comprehensible given what
precedes it. Evidence at every decision point.*

---

### CHAPTER 5 — The Four Layers

**Filename:** `05-the-four-layers.md`
**One-line:** The reader learns why bolt-on tools cannot produce what
an intelligent textbook requires — and what each layer must do for
the integration to function.
**Act:** Two
**Bloom's primary level:** Apply
**Load-bearing:** No

**Learning outcomes:**
1. (Understand) Describe the function of each of the four layers and
   explain what each layer cannot do without the others.
2. (Analyze) Explain why bolt-on tools cannot produce the integrated
   signal an intelligent textbook requires — and name the specific
   signal lost at each seam.
3. (Apply) Map a specific learning problem to the four layers,
   identifying what each layer needs to do and what data it exchanges.
4. (Evaluate) Assess an existing platform's architecture against the
   four-layer model and identify which layer is the binding constraint.

**Opening case:** The reasonable objection. A Charles Fadel type has
just read Chapters 1–4. He says: "I could buy an LMS, a chatbot, a
spaced repetition tool, and a case study library and connect them. Why
do I need a platform?" The bolt-on failure answers before he finishes
asking.

**Core content:**
1. The bolt-on failure — what gets lost when tools are assembled rather
   than integrated: the seven signals that require live instrumentation
2. Layer 1: Book Library — domain-specific content, Level-3 specificity,
   what it must provide to the curriculum layer and adaptive engine
3. Layer 2: Curriculum Design Layer — Tic TOC as the instrument, concept
   map, prerequisite dependencies, phase gate specifications
4. Layer 3: Adaptive Engine — the within-learner bandit, mode selection,
   reward signal, what it needs from measurement
5. Layer 4: Measurement Layer — GLP framework, seven friction components,
   what it must capture for the engine to optimize for learning
6. The integration — the layers are a loop, not a stack; a break anywhere
   degrades the whole

**Worked example:** One student session in Medhavy's cancer textbook
deployment. A medical student working through an oncology concept. Show
what data flows between layers at each step. What the measurement layer
captures. What the engine receives. What mode it selects and why. First
time the reader sees all four layers operating simultaneously.

**Assessable exercises:**
1. (Apply) Given a learning problem, specify the data each layer must
   produce and receive. Draw the dependency map.
2. (Analyze) A platform uses an LMS for content, a third-party chatbot
   for Ask AI, and a separate quiz tool for retrieval practice. Identify
   the specific signal lost at each seam.
3. (Evaluate) The Khanmigo deployment — which layer was the binding
   constraint? What would have to change to prevent the IDK-IDK outcome?

**Bridge to Chapter 6:** Measurement determines what every other layer
can learn. Chapter 6 specifies the measurement layer first — because
understanding it is prerequisite to understanding why mode design and
engine design take the shape they do.

**Key pantry sources:** ARCHITECTURE.md (system architecture),
API.md (technical layer descriptions), all nine pantry notes (for
the seven signals argument), GLP preprint

---

### CHAPTER 6 — The Measurement Layer

**Filename:** `06-the-measurement-layer.md`
**One-line:** The reader learns to specify a measurement layer that
captures learning evidence rather than engagement proxies.
**Act:** Two
**Bloom's primary level:** Create
**Load-bearing:** YES — generates prerequisites for Chapters 7, 8, 12

**⚠ LOAD-BEARING FLAG: If this chapter is written poorly, three
downstream chapters break. Priority chapter for hostile reader review
before any other chapter goes to editorial.**

**Learning outcomes:**
1. (Analyze) Explain the decoupling problem: why the artifact can no
   longer be trusted as sole evidence of the process that produced it.
2. (Apply) Identify which of the seven GLP friction components are
   measurable in a given platform architecture.
3. (Evaluate) Assess a measurement system against the engagement-vs-
   learning distinction.
4. (Create) Specify a minimum viable measurement layer for a given
   intelligent textbook.

**Opening case:** The artifact used to be proof of the process. It no
longer is. A well-structured essay can now be produced in seconds by a
system that has performed none of the cognitive work the essay was
designed to evidence. The forensic window is closing. In writing it is
largely closed already. This chapter opens on the decoupling problem
before introducing the GLP framework as the response to it.

**Core content:**
1. The decoupling problem — the causal chain that broke; Genuine
   Learning → Cognitive Process → Artifact; AI inserts a bypass
2. Why friction traces exist — genuine learning is a biological event;
   dopamine-mediated prediction error; BDNF; dendritic spine formation;
   behavioral consequences are traceable
3. The seven GLP components — Y1 Temporal Engagement Pattern, Y2 Error
   Trajectory Coherence, Y3 Cross-Context Transfer, Y4 Uncertainty
   Calibration, Y5 Social Knowledge Texture, Y6 Retrieval Strength
   Decay Signature, Y7 Scaffolding Response Curve
4. The ensemble architecture — why seven components, not one; gaming
   cost argument
5. The fluency trap — brain confuses perceptual fluency with
   understanding; smooth AI explanation produces genuine fluency;
   the feeling of understanding is real; the understanding is not
6. Minimum viable measurement layer — which three GLP components are
   highest priority; what can be approximated from LMS clickstream data

**Worked example:** Two students submit identical essays on a clinical
pharmacology concept. One used AI to generate it. One wrote it after
genuine engagement. The artifact is indistinguishable. Walk through
what each of the seven GLP components would show for each student.
Where the signals diverge. What the composite GLP score looks like.

**Assessable exercises:**
1. (Apply) Given a platform architecture, identify which GLP components
   are already measurable from existing data streams with no additional
   instrumentation.
2. (Evaluate) A platform dashboard shows: time on platform, pages
   viewed, quiz completion rate, chat interactions. Classify each as
   engagement proxy, performance proxy, or learning evidence.
3. (Create) Specify the minimum viable measurement layer for a single-
   subject intelligent textbook. Name what gets instrumented, what
   signals are captured, what threshold triggers an adaptive engine
   response.

**Bridge to Chapter 7:** The measurement layer specifies what the
adaptive engine can learn. Chapter 7 delivers the four modes as the
engine's arms — and why phase gates are a measurement decision as much
as a pedagogical one.

**Key pantry sources:** GLP preprint (primary source — seven components
fully specified), all nine pantry notes (for the neurobiology section
and the fluency trap), ARCHITECTURE.md

---

### CHAPTER 7 — The Four Modes

**Filename:** `07-the-four-modes.md`
**One-line:** The reader learns to select the right mode for a given
learning objective and specify the phase gate logic that prevents each
mode's characteristic failure.
**Act:** Two
**Bloom's primary level:** Apply
**Load-bearing:** No

**Learning outcomes:**
1. (Understand) Explain the evidence base for each of the four modes
   and identify the specific learning mechanism each mode activates.
2. (Analyze) Explain why each mode is phase-gated and what specific
   failure mode each gate prevents.
3. (Apply) Select the appropriate mode or mode sequence for a given
   learning objective using evidence and phase gate logic as criteria.
4. (Evaluate) Diagnose a mode deployment failure and specify the
   design correction.

**Opening case:** The hammer problem restated at mode level. A platform
with only one mode is a hammer. Ask AI for every interaction produces
the Bastani GPT-Base outcome. Quiz Me for every interaction produces
performance without storage strength. Glimmer for every interaction
produces the anxiety failure mode in novice learners. Case Study for
every interaction produces pattern matching without causal understanding.

**Core content:**
1. Ask AI — the guardrail is the design decision; context-anchoring
   (RAG to current section + prerequisites) as primary guardrail;
   the open question: does context-anchoring alone convert GPT-Base
   to GPT-Tutor success?
2. Case Study — solo asynchronous AI-facilitated CBL on faculty-
   curated cases at the application stage; Thistlethwaite 2012 as
   the applicable evidence base; pre-written + faculty-reviewed as
   the evidence-licensed path
3. Quiz Me — retrieval practice as mechanism; FSRS as scheduling
   algorithm; due-today counter as Zeigarnik closure variable; the
   algorithm is a small contributor to whether students adopt the
   tool at all — the due-count is load-bearing UI
4. Glimmer — ill-structured problem at session level; backwards-faded
   scaffolding weeks 1–3; the anxiety failure mode in novice learners;
   scaffolding fading, not scaffolding removal
5. Phase gates as measurement decisions — Quiz Me gated until section
   read (Y1), Glimmer gated until concept built (Y7), Case Study
   gated until representation sufficient (Y3)

**Worked example:** A medical student working through a pharmacokinetics
concept. Mode sequence: Ask AI to clarify a prerequisite (context-
anchored, hint-only). Quiz Me on the core mechanism (spaced, due-count
visible). Case Study on a drug interaction scenario (pre-written,
faculty-reviewed, gated until Quiz Me mastery threshold). Glimmer:
design a dosing protocol for a complex patient (open, scaffolding-faded
by week). Show what the measurement layer captures at each mode
transition.

**Assessable exercises:**
1. (Apply) Given a learning objective and learner profile, specify the
   mode sequence with phase gate logic and the failure mode each
   gate prevents.
2. (Evaluate) A Glimmer deployment shows 60% of students abandoning
   the mode in week 2. Diagnose the failure mode and specify the
   scaffolding correction.
3. (Analyze) A Quiz Me deployment shows high session scores but poor
   retention at 30-day re-assessment. Which GLP component is the
   diagnostic? What does it suggest about the scheduling algorithm's
   configuration?

**Bridge to Chapter 8:** The modes are the engine's arms. Chapter 8
delivers how the engine learns which arm to pull for which learner on
which concept — and why that learning requires the measurement layer
Chapter 6 specified.

**Key pantry sources:** ask-ai-research.md, case-study-research.md,
quiz-me-research.md, quiz-me-habit-research.md, glimmer-research.md,
glimmer-displacement-research.md, PEDAGOGY ARCHITECTURE.txt

---

### CHAPTER 8 — The Adaptive Engine

**Filename:** `08-the-adaptive-engine.md`
**One-line:** The reader learns what the adaptive engine is actually
optimizing, why within-learner beats cross-learner generalization, and
how to specify a reward function that does not silently drift toward
engagement.
**Act:** Two
**Bloom's primary level:** Evaluate
**Load-bearing:** YES

**Learning outcomes:**
1. (Understand) Explain the difference between cross-learner
   generalization and within-learner bandit optimization — and why
   the difference matters for learning outcomes.
2. (Analyze) Identify what the adaptive engine is learning across
   (mode × concept × time) cells and what data the measurement layer
   must provide.
3. (Apply) Specify the reward signal for a given intelligent textbook
   — naming what GLP components contribute and how the engine updates.
4. (Evaluate) Assess an adaptive engine design for the engagement trap
   — whether it is optimizing for the right reward signal or drifting.

**Opening case:** The casino. Five slot machines. 1,000 tokens. You
cannot tell from looking which machine pays best. This is the
exploration-exploitation dilemma — formalized by Herbert Robbins in
1952. Now replace the slot machines with Ask AI, Case Study, Quiz Me,
and Glimmer. Replace the tokens with a student's study sessions.
Replace the payout with genuine learning probability.

**Core content:**
1. The slot machine version — epsilon-greedy, UCB1, exploration-
   exploitation tradeoff; the contextual bandit: what if payout
   depended on wind speed? In Medhavy, wind speed is (learner history
   × concept prerequisites × time since last session × prior mode
   performance)
2. The within-learner distinction — most adaptive platforms use cross-
   learner generalization; within-learner bandit learns per-learner
   reward functions; requires more sessions to converge but does not
   require the assumption that learners are similar
3. What the engine is learning — reward function over (mode × concept
   × time) cells; updates every session
4. The engagement trap — the casino owner watching through the security
   camera; engagement-optimizing platform keeps genuine earnings low
   while logging the learner as a winner; an engine that receives
   engagement signals instead of GLP signals will drift
5. The reward function specification — GLP components, initial weights
   from evidence base, update from deployment data; honest uncertainty:
   right weights are one of the book's eight open bets
6. What the engine cannot learn — cross-learner generalization outside
   its scope by design; curriculum sequencing outside its scope

**Worked example:** A within-learner bandit session log for a medical
student across six weeks of oncology study. Show engine's initial mode
distribution (near-uniform — pure exploration). Week 2 update (this
student responds to Quiz Me better than Ask AI on factual concepts).
Week 4 (Glimmer underperforming — engine reduces weight). Week 6
(Case Study receiving higher allocation for application-level concepts).
Walk through the reward function update at each step.

**Assessable exercises:**
1. (Apply) Given a reward function specification and a four-week
   deployment log, calculate the engine's updated mode allocation
   for a specific learner-concept pair.
2. (Evaluate) An adaptive engine's session logs show increasing time-
   on-platform and decreasing GLP scores over six weeks. Diagnose the
   failure. What reward signal is the engine actually optimizing?
3. (Analyze) A platform claims to "personalize learning to each
   student." What question do you ask to determine whether it uses
   cross-learner generalization or within-learner optimization?

**Bridge to Chapter 9:** The engine's learning depends on a well-
specified curriculum. Chapter 9 delivers the curriculum design layer —
why backward design is the instrument that produces the structured
input the engine requires.

**Key pantry sources:** Contextual Bandits.txt (primary technical
source), MVAL.txt, concept-sequencing-research.md, GLP preprint,
ARCHITECTURE.md. Reference the Robert C. Gray multi-armed bandit
explanation style: slot machines first, technical vocabulary second.

---

### CHAPTER 9 — The Curriculum Design Layer

**Filename:** `09-the-curriculum-design-layer.md`
**One-line:** The reader learns to produce a chapter specification
detailed enough that a developer can configure the adaptive engine
without a meeting.
**Act:** Two
**Bloom's primary level:** Create
**Load-bearing:** No

**Learning outcomes:**
1. (Understand) Explain why curriculum design is a prerequisite for
   an adaptive engine — and what happens to the bandit's learning
   when the concept map is underspecified.
2. (Apply) Use backward design to specify the learning outcomes,
   sequencing logic, and prerequisite map for a chapter or module.
3. (Analyze) Identify the three curriculum design failure modes:
   topic coverage masquerading as capability build, sequences that
   serve author expertise rather than learner progression, prerequisite
   gaps that appear as learner failure.
4. (Create) Produce a chapter specification — outcomes, phase gates,
   mode assignments, prerequisite dependencies — detailed enough for
   a developer to act on.

**Opening case:** The "suggest 15 chapters" failure. An author opens
a design tool and types "suggest 15 chapters for a medical school
pharmacology textbook." The tool produces 15 plausible-sounding chapter
titles. The author accepts them. The adaptive engine now has a concept
map with no prerequisite dependencies, no outcome statements, no phase
gate logic, no mode assignments. It is flying blind.

**Core content:**
1. Why the engine needs the curriculum layer — garbage curriculum in,
   garbage adaptation out; "Drug Metabolism" as a topic vs. as a
   capability; what the engine cannot learn from an underspecified map
2. Backward design as the instrument — two-paragraph introduction for
   developers who haven't encountered this; outcomes first, assessment
   second, content structure third
3. The concept map — what it must contain: concept nodes, prerequisite
   dependencies, Bloom's level assignments, mode appropriateness flags
4. The chapter specification — the shared deliverable Charles produces
   and the developer configures from; the shared language the book
   promised
5. The three curriculum design failure modes — topic coverage disguised
   as capability, author-sequence vs. learner-sequence, prerequisite
   gaps appearing as learner failure
6. Tic TOC as the curriculum design instrument — the meta-move: this
   book was produced through a Tic TOC session; the reader has been
   experiencing the methodology since Chapter 1

**Worked example:** A pharmacology chapter specified incorrectly (topic-
coverage model) versus specified correctly (backward design model).
What the engine receives from each. What it can learn. What the student
experiences as a result. The correctly specified chapter produces a
concept map the engine can use. The topic-coverage chapter produces a
list the engine cannot adapt to.

**Assessable exercises:**
1. (Create) Given a chapter topic and learner profile, produce a
   chapter specification that passes backward design audit: outcomes
   at Apply level or above, phase gate logic for each mode, prerequisite
   dependency map with no broken chains.
2. (Analyze) A student is failing Chapter 8 of a deployed intelligent
   textbook. Platform logs show high engagement and low GLP scores.
   Diagnose: curriculum design failure, measurement failure, or content
   failure?
3. (Apply) Convert a topic-coverage chapter outline into a backward-
   design chapter specification. Name every change made and why.

**Bridge to Chapter 10:** The curriculum design layer produces the
specification. The content layer produces what the specification
describes. Chapter 10 answers: given what the curriculum layer requires
from the content layer, what content production decisions are justified
by the evidence?

**Key pantry sources:** PEDAGOGY ARCHITECTURE.txt, Lexicon.txt,
domain-specific-instruction-research.md, concept-sequencing-research.md

---

### CHAPTER 10 — The Content Layer

**Filename:** `10-the-content-layer.md`
**One-line:** The reader learns which content production decisions
the evidence supports and which ones cost-collapse changes — without
changing the burden of proof for high-stakes content.
**Act:** Two
**Bloom's primary level:** Evaluate
**Load-bearing:** No

**Learning outcomes:**
1. (Analyze) Explain the domain-specificity finding and identify the
   design constraint it imposes on content production.
2. (Evaluate) Apply the cost-collapse asymmetry: identifying which
   content decisions have low burden of proof and which retain high
   burden of proof regardless of production cost.
3. (Apply) Specify the content requirements for a given intelligent
   textbook — domain specificity level, AI-generation policy, faculty
   review gates, minimum viable content layer.
4. (Evaluate) Assess an AI-generated content sample against the
   vetting requirements the evidence base specifies.

**Opening case:** Content last. Deliberately. Every author wants to
start here. This chapter opens by naming why it is last: content is
what every author thinks is the product. The preceding eight chapters
have argued it is one layer among four — and the least interesting
design decision if the other three layers are wrong.

**Core content:**
1. The domain-specificity finding — Level 1 (generic) vs. Level 2
   (generic + domain capstone) vs. Level 3 (domain-specific throughout,
   generic backbone); Level 3 captures bulk of transfer and motivation
   benefits at ~1.5-2× production cost
2. The cost-collapse asymmetry — AI content at $5/unit changes burden
   of proof asymmetrically; low-risk content burden lowered; high-risk
   content burden unchanged
3. The AI-generation policy — which content elements can be AI-
   generated with light review; which require domain expert authorship;
   the faculty review gate is not optional
4. The Sesame Street standard — $5/child/year producing measurable
   learning gains; what AI-generated content produces is genuinely
   unknown for initial concept acquisition — named as an open bet
5. The minimum viable content layer — what the curriculum design layer
   requires; a chapter specification without content is an engine
   without fuel

**Worked example:** Two versions of the same pharmacology concept
explanation. Version A: AI-generated, generic, unreviewed. Version B:
domain-specific, faculty-reviewed, cross-domain comparison included.
What each version produces in the measurement layer. What GLP
components respond differently. What the engine learns from each
after ten student sessions.

**Assessable exercises:**
1. (Apply) Given a content production budget and a domain, specify
   the content layer: which elements get AI-generated with light
   review, which require domain expert authorship, and why.
2. (Evaluate) An AI-generated explanation contains one factual error
   and two conceptually misleading simplifications. What does the GLP
   measurement layer capture — and when? What is the faculty review
   gate's job?
3. (Analyze) A platform claims their AI-generated content is "as
   effective as professionally produced content" based on engagement
   metrics. What evidence would actually support this claim?

**Bridge to Chapter 11:** The architecture is complete. Chapter 11
delivers the economic argument for why this moment — this specific
convergence of cost collapse, AI capability, and evidence base —
is the right moment to build it.

**Key pantry sources:** educational-media-economics-research.md
(Sesame Street, Mayer CTML, cost-collapse), domain-specific-
instruction-research.md (PCK, Level-3 specificity, Sadler 2013)

---

### CHAPTER 11 — The Economics of Intelligent Textbooks

**Filename:** `11-the-economics.md`
**One-line:** The reader learns to make the economic case for an
intelligent textbook — and to identify when the economics do not
support the build.
**Act:** Two
**Bloom's primary level:** Evaluate
**Load-bearing:** No (skippable for a reader whose build decision
is already made — they lose the cost-collapse argument but not
the architecture)

**Learning outcomes:**
1. (Understand) Explain why cost collapse changes the economics
   of intelligent textbook production asymmetrically.
2. (Analyze) Calculate the minimum viable audience for an intelligent
   textbook at a given production cost and price point.
3. (Evaluate) Assess a proposed intelligent textbook investment against
   the cost-collapse asymmetry.
4. (Apply) Specify the minimum viable investment for a given
   intelligent textbook.

**Opening case:** Sesame Street. $5 per child per year. The most
cost-effective educational intervention ever documented at scale.
For forty years this was the floor. Then the floor collapsed.
AI-generated content at $5 per unit. What does this change — and
what does it not change?

**Core content:**
1. The cost collapse — what AI-generated content costs now vs.
   professionally produced content before; the asymmetry
2. The binding cost shift — when production cost collapses, the
   binding constraint shifts to knowledge of the individual learner;
   Sadler 2013: teachers who identified student misconceptions produced
   substantially larger gains; cheap content makes pedagogical content
   knowledge more valuable, not less
3. The minimum viable audience calculation — what audience size justifies
   the architecture investment at different price points; the Kindle/$1
   model; the Learning Engineering community as minimum viable audience
4. The homeschool and micro-audience market — cost collapse makes
   intelligent textbooks viable for previously too-small audiences;
   Homes of Hope as the minimum viable audience example where Anki
   wins on economics, not just pedagogy
5. What the economics do not change — burden of proof for high-stakes
   content; faculty review gate; domain expert curriculum design;
   GLP measurement instrumentation

**Worked example:** Three intelligent textbook projects at different
investment levels. Project A: $15K (Dirac Quantum Tutor). Project B:
$150K (medical school pilot). Project C: $1.5M (full-scale platform).
What each can and cannot build at that investment level. Which layers
are feasible, which are minimum viable, which must be deferred.

**Assessable exercises:**
1. (Apply) Given a production budget and target audience, specify
   what the intelligent textbook can and cannot build at that
   investment.
2. (Evaluate) A vendor proposes an intelligent textbook for a niche
   professional certification with 500 potential users at $50/year.
   Does the economics support the full four-layer architecture? What
   is the minimum viable version?
3. (Analyze) Cost collapse changed the economics of content production.
   What did it not change? Name three costs that are unchanged and
   explain why.

**Bridge to Chapter 12:** The architecture is complete. The economics
are specified. Act Three begins: honesty about what is not yet known,
and the tool that converts everything the book has built into a
specification worth handing to a developer.

**Key pantry sources:** educational-media-economics-research.md
(Sesame Street, minimum viable audience, AI content quality evidence,
Sunstein burden-of-proof inversion), Homes of Hope Plus One book.md
(economics of the minimum viable case)

---

### ACT THREE — THE MAP (Chapters 12–13)
*What this act does: names the bets honestly, delivers the instrument
that converts thinking into specification, demonstrates that the book's
method is itself an instance of the methodology it describes.*

---

### CHAPTER 12 — What the Platform Does Not Know Yet

**Filename:** `12-what-the-platform-does-not-know-yet.md`
**One-line:** The reader learns to distinguish what the evidence
supports from what is a design bet — and to specify the instrumentation
that makes the bets testable.
**Act:** Three
**Bloom's primary level:** Evaluate
**Load-bearing:** No (skippable for a reader who trusts the
architecture and is not interested in the epistemic inventory —
they lose the honest uncertainty framing but not a capability)

**NOTE FOR CHAPTER AUTHOR:** This chapter requires the author's
voice more than any other chapter. It cannot be written as a
literature review. The author must speak in first person about
bets they are personally making. A contributor cannot write
this chapter — it will read as false.

**Learning outcomes:**
1. (Evaluate) Assess an intelligent textbook deployment's epistemic
   honesty: distinguishing adjacent evidence, direct evidence, and
   design bets.
2. (Apply) Specify the instrumentation required to make a given
   design bet testable from deployment data.
3. (Analyze) Explain the student consent architecture as a design
   decision with learning consequences.
4. (Understand) Describe switching behavior as signal and explain
   what the adaptive engine should do with it.

**Opening case:** The Montaigne register. What Medhavy currently
knows. What it does not. Why the not-knowing is itself an instrumented
research bet, not a gap to be embarrassed about. The chapter opens
with the eight open questions the platform is designed to answer.

**Core content:**
1. The eight open questions:
   - Does context-anchoring alone convert GPT-Base failure to
     GPT-Tutor success?
   - Does pre-written faculty-reviewed CBL produce reasoning gains
     comparable to group human-facilitated CBL when solo/asynchronous?
   - Does FSRS-style scheduling generalize to conceptual material?
   - Is the Quiz Me habit loop driven by the due-count or the algorithm?
   - Does backwards-faded scaffolding prevent the anxiety collapse
     in novice Glimmer users?
   - Does priority-weighted scheduling outperform recall-only
     scheduling?
   - Does Level-3 domain specificity outperform Level-1 generic
     instruction enough to justify the production cost?
   - Does AI-generated educational content produce durable learning
     outcomes comparable to professionally produced content?
2. What the adjacent evidence supports — ITS, spaced repetition,
   CBL — provides adjacent support; does not directly test the
   integrated platform claim
3. What the direct evidence does not yet show — no published RCT
   has tested the integrated four-layer architecture
4. The student consent architecture — what data the platform
   collects, what it commits not to collect, why this is a design
   decision with learning consequences
5. Switching behavior as signal — when a learner switches from
   Quiz Me to Glimmer mid-session, the switch is information

**Worked example:** The Medhavy cancer textbook deployment at six
weeks. What the data show. What they do not show. Which of the eight
open questions has preliminary evidence. Which is still genuinely open.
A deployment report that a researcher could use as a preprint — not
polished findings, but honest preliminary evidence with appropriate
uncertainty.

**Assessable exercises:**
1. (Apply) For a given intelligent textbook deployment, specify the
   minimum instrumentation required to generate preliminary evidence
   on three of the eight open questions within one semester.
2. (Evaluate) A platform publishes a white paper claiming their
   intelligent textbook "improves learning outcomes by 40%." Apply
   the epistemic audit: adjacent evidence, direct evidence, or
   assertion?
3. (Analyze) Design the student consent architecture for a medical
   school intelligent textbook. What data must be collected for GLP
   to function? What should not be collected? What must be disclosed?

**Bridge to Chapter 13:** The honest inventory is complete. Chapter 13
delivers the design conversation itself — the instrument that converts
everything this book has built into a specification worth handing to
a developer. And the meta-move: the reader has been living this
conversation since Chapter 1.

**Key pantry sources:** All nine pantry notes (for the eight open
questions), GLP preprint, ARCHITECTURE.md. The eight open questions
are drawn directly from the manuscript summary's "open questions the
deployment is designed to answer" section.

---

### CHAPTER 13 — The Design Conversation

**Filename:** `13-the-design-conversation.md`
**One-line:** The reader conducts the design conversation that
produces a specification worth building from — and understands why
the tool can only work if the thinking came first.
**Act:** Three
**Bloom's primary level:** Create
**Load-bearing:** No

**NOTE FOR CHAPTER AUTHOR:** The worked example in this chapter
depends on Medhavy the instrument existing as a usable tool.
If the tool is not built when the chapter is drafted, the worked
example must be labeled explicitly as a design specification of
what the session will produce — not a product demo. The book's
epistemic honesty commitment requires this label. It is fine —
a book describing a tool it is building is more interesting than
a book describing a tool that already exists.

**Learning outcomes:**
1. (Understand) Explain why a "suggest 15 chapters" prompt produces
   unusable output — and what the tool requires from the human before
   it can produce a specification worth building from.
2. (Apply) Conduct the design conversation — the question-by-question
   process this book has modeled — that produces the inputs Medhavy
   needs.
3. (Create) Use Medhavy to produce a design map — complete
   specification of layers, modes, phase gates, measurement signals,
   and curriculum architecture — that can be handed to a developer
   without a translation meeting.
4. (Evaluate) Assess a Medhavy-generated specification for
   completeness: which layers are underspecified, which phase gates
   are missing, which measurement commitments are absent.

**Opening case:** The meta-move named. This book is a Tic TOC session.
The reader has been experiencing the design conversation methodology
since Chapter 1 — question by question, intake before architecture,
evidence before specification, honest inventory before the map. The
chapter opens by naming this explicitly.

**Core content:**
1. Why the tool requires the thinking — a Medhavy session without the
   thinking this book provides produces "suggest 15 chapters" output;
   the tool amplifies the thinking, it does not replace it
2. The platform vs. instrument distinction — Medhavy the platform is
   what gets built; Medhavy the instrument is what produces the
   specification for what gets built
3. How to conduct the design conversation — the intake questions,
   learner profile, complexity threshold test, evidence audit, four-
   layer specification, economics check, honest inventory
4. What the map contains — complete specification; everything a
   developer needs to build without a translation meeting; everything
   Charles needs to evaluate whether what gets built is what he designed
5. The shared language — Charles can say "Socratic isn't right here
   because of retrieval interference"; the developer can say "we
   already have something close"; both talking about the same decision
6. The Gru connection — "senior dev is 80% thinking, 20% coding";
   the map Medhavy produces is the 80%; the Gru-assisted build is
   the 20%

**Worked example:** A complete Medhavy session for a new intelligent
textbook project — run at accessible depth. Show the intake questions,
learner profile, complexity threshold decision, four-layer specification
emerging, and the map that results. The reader watches a design
conversation produce a buildable specification.

**Assessable exercises:**
1. (Create) Run a Medhavy session for a real learning problem. Produce
   the specification. Hand it to someone who was not in the session.
   Can they build from it without asking a question? This is the only
   test that matters.
2. (Evaluate) Given a Medhavy-generated specification, identify which
   layer is underspecified, which phase gates are missing, which
   measurement commitments are absent. What questions would the
   developer ask?
3. (Apply) Charles Fadel has content on 21st century skills and
   curriculum redesign. Run the first three intake questions of a
   Medhavy session for his intelligent textbook. What do you learn
   that changes the specification?

**Chapter closing (book's last paragraph):** The reader holds the map.
The developer has a specification they can build from. Charles has the
language to evaluate whether what gets built is what he designed.
The platform is opinionated. The model has no opinions of its own.
The conversation is what makes the platform worth building — and the
conversation is what this book has been, from the first IDK-IDK
incident to this page.

**Key pantry sources:** ARCHITECTURE.md, API.md, PEDAGOGY
ARCHITECTURE.txt, Lexicon.txt (for Medhavy vocabulary). The Gru
connection is deliberately brief — one section, not a full technical
treatment. The implementation book is the right home for the full
Gru specification.

---

## Appendices

*Appendices are written from pantry material by Cowork. Each appendix
is a standalone reference document — not required reading, but
available for readers who want technical depth on specific Medhavy
features or implementation approaches.*

---

### APPENDIX A — The Medhavy Lexicon: Vocabulary the Platform Teaches

**Filename:** `A-medhavy-lexicon.md`
**Source:** Lexicon.txt, NanoLex / Wikipedia Pipeline notes
**One-line:** The platform-specific vocabulary the book introduces,
defined precisely and mapped to their first appearance in each chapter.

**Contents:**
- The IDK-IDK problem
- The four layers (Book Library / Tic TOC / Adaptive Engine /
  Measurement Layer)
- The four modes (Ask AI / Case Study / Quiz Me / Glimmer)
- The seven signals
- Phase gates
- The within-learner bandit
- The GLP reward signal
- Ambient infrastructure
- The conductor
- The fluency trap
- Cost-collapse asymmetry
- The due-today counter
- Genuine Learning Probability (GLP)

**NanoLex connection:** The NanoLex / Wikipedia pipeline (Pipeline A
live on dev; Pipeline B a publishable paper — "Automated Lexical Entry
Generation for Nanomedicine") is the production implementation of the
lexicon layer described in this appendix. Document the pipeline
architecture and its relationship to the Book Library content layer.

---

### APPENDIX B — The Causal Knowledge Graph: Mapping What Works

**Filename:** `B-causal-knowledge-graph.md`
**Source:** Hattie's Visible Learning DAG framework notes, Causal
Knowledge Graph project files (Satwik Reddy Sripathi)
**One-line:** How Hattie's Visible Learning variables map into a DAG
framework (Intervention/Diagnostic/Context taxonomy) and what the
Adherence Classifier architecture adds.

**Contents:**
- Hattie's Visible Learning as a knowledge base — the 250+ effect
  sizes and what they represent
- The Intervention/Diagnostic/Context taxonomy — how Hattie's variables
  map to the three categories
- The DAG framework — directed relationships between intervention,
  context, and outcome variables
- The Adherence Classifier architecture — what it detects and why
  it matters for the adaptive engine
- Connection to Chapter 8 (The Adaptive Engine) — how the causal
  knowledge graph informs the engine's prior on reward function weights
- Open questions: the causal discovery vs. expert elicitation debate
  applied to educational interventions

---

### APPENDIX C — The GLP Framework: Technical Specification

**Filename:** `C-glp-technical-specification.md`
**Source:** GLP preprint (Frictional / Irreducibly Human series)
**One-line:** The full technical specification of the Genuine Learning
Probability framework — the seven components, the ensemble architecture,
the tier calibration, and the validation methodology.

**Contents:**
- The seven GLP components with full mathematical specification
- The three-layer ensemble architecture (component models → tier-
  conditioned combination → meta-model)
- Tier calibration table (seven cognitive tiers, primary friction
  signal per tier)
- Validation methodology (labeled corpus construction, calibration
  assessment, information gain test)
- The arms race problem and why process-based measurement is different
  from artifact-based detection
- Implementation guidance: which components are measurable from LMS
  clickstream data, which require additional instrumentation

---

### APPENDIX D — Contextual Bandits: Implementation Notes

**Filename:** `D-contextual-bandits.md`
**Source:** Contextual Bandits.txt, MVAL.txt, ARCHITECTURE.md
**One-line:** Technical implementation notes for the within-learner
contextual bandit — the algorithm, the context features, the reward
signal, and the update mechanics.

**Contents:**
- The contextual bandit formulation — arms, context features, reward
- Context features for Medhavy: learner history, concept prerequisites,
  time since last session, prior mode performance, GLP component scores
- Reward signal specification — GLP components and weights
- Exploration strategy — epsilon-greedy vs. UCB1 vs. Thompson sampling
  for the Medhavy use case
- Update mechanics — how the per-learner reward function is updated
  after each session
- Cold start problem — what the engine does for a new learner with
  no session history
- MVAL (Medhavy Value) — the platform's internal value metric and
  its relationship to GLP
- Open questions: right weights, generalization across learner
  populations, convergence rate

---

### APPENDIX E — The Medhavi Hub: Architecture Reference

**Filename:** `E-medhavi-hub-architecture.md`
**Source:** API.md, ARCHITECTURE.md
**One-line:** The Medhavi Hub system architecture — authentication,
access control, textbook registry, analytics, and memory API —
for developers building on the platform.

**Contents:**
- System context diagram (from ARCHITECTURE.md)
- Tech stack (Next.js, Clerk, Supabase, AWS S3, PostHog)
- Auth architecture (JWT token flow, CORS strategy, logout invalidation)
- Textbook access decision tree
- Database schema (core tables, analytics tables, concept map tables)
- Key design decisions (Clerk for identity / Supabase for data,
  JWT vs. proxied sessions, dynamic CORS, service role key)
- API reference summary (access, textbooks, classes, analytics,
  memory — from API.md)
- Concept map editor workflow (pipeline → session → node review →
  export to S3)

---

### APPENDIX F — Medhavy 1.5 Feature Roadmap

**Filename:** `F-medhavy-1.5-feature-roadmap.md`
**Source:** `medhavy-1.5-feature-roadmap.md` (in pantry)
**One-line:** The product-and-engineering alignment document for the
1.5 release — what already exists, what 1.5 adds, and the research
rationale behind each feature.

**Contents:**
- How to read the document (cognitive-operations framing — different
  kinds of learning require different kinds of help)
- The platform as it exists today — Ask AI as the context-aware tutor,
  MoE routing in the Cancer Biology textbook, physics widget tools
  in the Physics Vol. 1 textbook
- What 1.5 adds — Quiz Me, Case Study, Glimmer — with the research
  rationale for each design choice and the failure modes each is
  designed to avoid
- How the four modes fit together — the cognitive logic that makes
  the combination more than the sum of its parts
- The Medhavy 2.0 architecture preview (contextual bandit mode
  selection) — pointer forward to Appendix I

**Relation to chapters:** This appendix is the engineering-and-product
restatement of what Chapters 5–7 specify pedagogically. A reader who
prefers the build-side framing can read this appendix first and then
return to Chapter 5 for the architectural argument. A developer who
inherits API.md should read this appendix before reading the code.

---

### APPENDIX G — Medhavy 1.5 Video and Animation

**Filename:** `G-medhavy-1.5-video-animation.md`
**Source:** `medhavy-1.5-video-animation.md` (in pantry)
**One-line:** The cost-effectiveness argument and design discipline
for AI-produced educational video and animation in Medhavy textbooks
— addendum to the 1.5 Feature Roadmap.

**Contents:**
- The cost-effectiveness argument — Nina Harris's $75K–$150K per
  two-minute video estimate at professional production standards
  collapses to ~$5/video via AI pipelines (15,000–30,000× reduction)
- The minimum-viable-audience inversion — at $5/video a 30-student
  section justifies production if any measurable gain exists
- The evidence base for domain-specific video effectiveness — Mayer's
  Cognitive Theory of Multimedia Learning (multimedia / modality /
  coherence principles, ~1.13 SD modality effect), Mares & Pan's
  cross-country meta-analysis (ES = 0.29 overall, 0.41 for low-SES)
- Why physics and dynamic biological processes are the right initial
  domains — spatial, temporal, dynamic structure that text + diagrams
  cannot capture
- The coherence-principle risk — cheap production tempts violation of
  the design discipline that makes video effective; poorly produced
  video produces negative learning relative to text-with-diagrams

**Relation to chapters:** This appendix is the production-economics
companion to Chapter 10 (Content Layer) and Chapter 11 (Economics).
Where Chapter 10 specifies the content layer's burden-of-proof
discipline, Appendix G specifies the cost-collapse asymmetry as it
applies specifically to educational video, and names the coherence-
principle trap that the cost collapse creates.

---

### APPENDIX H — Canvas LTI Integration Research

**Filename:** `H-canvas-lti-research.md`
**Source:** `medhavy-2.0-canvas-lti-research.md` (in pantry)
**One-line:** The technical and institutional groundwork for Medhavy's
Canvas LTI integration — what LTI 1.3 + LTI Advantage provides,
where the authentication and grade-passback fit relative to the
existing Clerk + Supabase + JWT architecture, and where the actual
deployment bottleneck lives (institutional approval, not technical
integration).

**Contents:**
- Executive summary — LTI 1.3 with LTI Advantage as the standard;
  Canvas LTI Advantage Complete certification; three LTI Advantage
  services (AGS, NRPS, Deep Linking) cover everything Medhavy 2.0
  needs
- The institutional approval bottleneck — technical integration takes
  days; institutional approval takes weeks to months (security review,
  legal review, accessibility review, data processing agreements);
  the University of Washington November 2024–March 2025 LTI freeze
  as the cautionary example
- The authentication flow — OIDC over OAuth 2.0 with RSA-signed JWTs;
  how this layers onto the existing Medhavy Hub JWT flow; the new
  LTI identity mapping table
- Canvas Dynamic Registration (added 2025) — eliminates manual JSON
  config copy-paste; should be Medhavy's primary installation path
- What this means for the existing auth architecture — LTI is an
  additional pathway, not a replacement; direct-access students
  continue using the Clerk-based flow

**Relation to chapters:** This appendix is the institutional-integration
companion to Appendix E (Medhavi Hub Architecture). Where Appendix E
specifies the standalone deployment, Appendix H specifies the LMS-
embedded deployment. A developer building for institutional adoption
should read both. The institutional-approval framing is also relevant
to Chapter 11's economics — the deployment-cost variable is not the
code but the legal and security review at each institution.

---

### APPENDIX I — Contextual Bandits for Learning Mode Selection (2.0)

**Filename:** `I-contextual-bandits-2.0.md`
**Source:** `medhavy-2.0-contextual-bandit-research.md` (in pantry)
**One-line:** The Medhavy 2.0 design-grounding research for the
contextual bandit that will select between Ask AI / Quiz Me /
Case Study / Glimmer at each session re-entry point — the algorithm
choice (Thompson sampling with the 2025 WAPTS variant), the reward
design (Impatient Bandit framework combining delayed retrieval with
short-term progressive signals), the feature vector (extending the
Korbit/LinUCB 2022 template with FSRS Retrievability, concept
importance tier, and Glimmer rubric history), and the cold-start
strategy (hierarchical prior populated from cross-student
cross-concept-node data).

**Contents:**
- What a contextual bandit is and why it is the right architecture
  for mode selection (vs. supervised learning, vs. full RL)
- Algorithm choice — Thompson sampling baseline; WAPTS (Song et al.
  2025) for small-cohort robustness; why LinUCB under-performs TS
  in noisy-feedback educational settings
- Reward definition — the seven-day delayed retrieval signal is
  theoretically correct but creates a learning delay; Impatient
  Bandit (Spotify / NeurIPS 2023; arXiv 2025) combines delayed
  ground truth with short-term progressive signals through a
  Bayesian filter — the single most important design decision for 2.0
- Feature vectors — the Korbit/LinUCB (Belfer et al. 2022) template
  as the closest published reference; Medhavy's additions (FSRS
  Retrievability, concept importance tier, Glimmer rubric history)
- The cold-start problem — every published deployment reports cold
  start as the dominant practical challenge; hierarchical prior as
  the recommended path
- What the literature has not yet solved — no published system has
  used a contextual bandit to select between *qualitatively different*
  mode types (retrieval practice vs. case study vs. generative
  assignment) for the same concept; all prior work selects between
  exercises of the same type; Medhavy 2.0 is a genuinely novel
  deployment, not an application of a solved problem

**Relation to chapters:** This appendix is the 2.0 technical follow-up
to Chapter 8 (Adaptive Engine) and Appendix D (Contextual Bandits
Implementation Notes). Where Chapter 8 establishes within-learner
optimization as the right architecture and Appendix D specifies the
1.x implementation, Appendix I specifies the 2.0 next-step research
program. The "genuinely novel deployment" framing also reinforces
Chapter 12 (What the Platform Does Not Know Yet) — App I makes the
unsolved-problem honest claim concrete and citation-anchored.

---

## Open questions for the book

| # | Question | Stakes | Decision deadline |
|---|---------|--------|------------------|
| 1 | Medhavy instrument vs. platform — how much of Chapter 13 can be written if the tool is not yet built? | Chapter 13 completeness | Before manuscript |
| 2 | The eight open bets — which have deployment data at publication time? | Chapter 12 accuracy | Before publication |
| 3 | The Gru chapter — is the implementation book named explicitly as a follow-up, or left implied? | Series strategy | Before proposal |
| 4 | Simulated data cases — which chapters use them and how are they labeled? | Epistemic honesty policy | Before drafting |
| 5 | The Homes of Hope case — is Priya a real person (requires permission) or a labeled composite? | Ethics / IRB | Before Chapter 3 draft |

---

## Pantry index (for Research Gatherer)

Research Gatherer: scan the following pantry files and copy relevant
content to notes files for each chapter. Do not fabricate sources.
Flag any claim not found in pantry or verifiable by web search.

**Primary pantry files:**
- ask-ai-research.md → Chapters 2, 4, 7
- case-study-research.md → Chapters 4, 7
- quiz-me-research.md → Chapters 3, 4, 7
- quiz-me-habit-research.md → Chapters 3, 7
- glimmer-research.md → Chapters 4, 7
- glimmer-displacement-research.md → Chapters 4, 7
- concept-sequencing-research.md → Chapters 8, 9
- domain-specific-instruction-research.md → Chapters 4, 10
- educational-media-economics-research.md → Chapters 3, 4, 11
- GLP preprint → Chapters 5, 6, 12, Appendix C
- API.md → Chapters 5, 8, Appendix E
- ARCHITECTURE.md → Chapters 5, 8, Appendix E
- Lexicon.txt → Chapter 13, Appendix A
- MVAL.txt → Chapter 8, Appendix D (note: MVAL is *Minimum Viable Analytical Log*, not "Medhavy Value")
- PEDAGOGY ARCHITECTURE.txt → Chapters 7, 9
- Contextual Bandits.txt → Chapter 8, Appendix D (note: file currently absent from pantry; reconstruct from 07-the-adaptive-engine_notes.md)
- Homes of Hope Plus One book.md → Chapters 3, 11
- Computational Skepticism Substack → Chapter 4
- medhavy-1.5-feature-roadmap.md → Appendix F (also Chapters 5, 7 — current platform features)
- medhavy-1.5-video-animation.md → Appendix G (also Chapter 10 — video production economics)
- medhavy-2.0-canvas-lti-research.md → Appendix H (also Chapter 11 — institutional deployment economics)
- medhavy-2.0-contextual-bandit-research.md → Appendix I (also Chapter 8, Chapter 12 — next-step bandit research)

---

*TIKTOC.md v1.2 — ready for Research Gatherer → Chapter Writer pipeline*
*v1.2 (2026-05-17): Adds Chapter 1 (What is Medhavy?) — conductor-frame chapter. Renumbers existing Ch 1-12 to Ch 2-13. Threads conductor philosophy through all chapters via "Where this fits the conductor frame" sidebars. Load-bearing chapters now Ch 1, 4, 6, 8.
*v1.1 (2026-05-17): Adds Appendices F (1.5 Feature Roadmap), G (1.5 Video and Animation), H (Canvas LTI Research), I (2.0 Contextual Bandit Research). Pantry index updated.*
*v1.0: All phases complete — Vision (/i1–/i4), Learning Architecture (/l1–/l4), Chapter Architecture (/c1 full pass), Scope & Market (partial — /m1–/m4 recommended before publisher proposal)*
*Next step: run Research Gatherer against this TIKTOC.md and pantry/*
