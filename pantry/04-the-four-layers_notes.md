# Research Notes — Chapter 4: The Four Layers

*Pantry note for the Medhavy book project. Source-anchored research for the architecture chapter — the bolt-on objection, the four layers (Book Library, Curriculum Design / Tic TOC, Adaptive Engine, Measurement Layer), and the integration argument that the seams between layers are where signal is lost.*

*Compiled 2026-05-17. Sequential to the Act One research notes; downstream chapters (Ch 5, 6, 7, 8) will lean on the seven-signals enumeration developed here.*

---

## A. Chapter pivot — what this chapter must do

Chapter 4 sits at the Act One → Act Two seam in the TIKTOC. Act One ended with the reader holding the evidence base; Act Two opens with the architecture. The chapter must do three things and not more:

1. **Take the Charles Fadel objection seriously.** The reasonable reader has just read three chapters of "the field is failing in both directions." His immediate response is procurement, not philosophy: *I could buy an LMS plus a chatbot plus a spaced repetition tool plus a case study library and connect them. Why a platform?* The chapter has to land on this question before any framework is introduced.

2. **Enumerate the seven signals that require live instrumentation.** This is the engine of the bolt-on argument. It is also the prerequisite material for Chapter 5, which goes deep on the measurement layer. The Ch 4 enumeration is the *signal list*; Ch 5 is the GLP framework that operationalizes those signals as the Y1–Y7 components. Same content, different level of resolution.

3. **Specify the four layers with one paragraph each, and then argue that the integration is the architecture.** The layers individually are not novel — Knewton had Layer 3 in some form, DreamBox has a version of Layer 3 in the math domain, Khanmigo has a version of Layer 3's Ask AI. What is novel is the loop: each layer's output is the next layer's input, and the closed loop converts a stack of tools into a learning system.

The chapter is not load-bearing. Skipping it loses the procurement-objection answer, not a downstream capability. But it sets the architecture vocabulary for everything in Act Two.

---

## B. The bolt-on failure — what the seven signals require

The bolt-on objection has structural force because most of what an intelligent textbook *delivers* — explanations, retrieval practice, case studies — does exist as off-the-shelf tools. The argument against bolt-on is that the *measurement* the platform requires is not extractable from the data streams off-the-shelf tools produce.

The seven signals enumeration below is the operational form of this argument. It is drawn from the existing pantry document `pantry/02-why-does-solving-it-require-a-platform.md`, which states the seven signals in plain English. The Ch 5 GLP framework (Y1–Y7) is the formal version of the same list; the Ch 4 version stays in plain English so the reader can hold the argument without the framework.

For each signal: what it is, what interaction design is required to produce it, and what existing tools' data streams cannot recover.

### Signal 1 — Temporal engagement pattern

*What it measures.* The distribution of session time across the difficulty surface of a concept. Genuine engagement tracks concept complexity — the student spends longer on the moves that are genuinely hard for them, shorter on the moves that are already automatic. Borrowed certainty tracks output length, not concept complexity.

*Interaction design required.* Timestamped logs at sub-section granularity. The system must know not only *that* the student was on page 47, but which paragraph their attention was on, for how long, and whether their attention returned to it after the next paragraph.

*What bolt-on cannot do.* Canvas logs page views and time-on-page at the page level. A page view of 12 minutes tells you nothing about whether the student spent 11 minutes on the difficult paragraph or 11 minutes idle with the page open. The granularity is wrong. The Canvas API was not designed to produce this resolution because Canvas's purpose is course administration, not engagement-pattern instrumentation.

### Signal 2 — Error trajectory coherence

*What it measures.* The shape of a student's wrong answers across a sequence of attempts. A real misconception produces *coherent* errors: question 1 wrong in a particular way, question 2 wrong in a related way, question 3 right after the misconception is repaired. Random wrong answers across question types indicate no underlying model developing — the student is guessing, not building.

*Interaction design required.* Error logging at the response level, with the response itself stored (not just right/wrong). The trajectory is the data; a single grade is the artifact of the trajectory.

*What bolt-on cannot do.* A separate quiz tool stores grades or pass/fail. The trajectory across a sequence of attempts is either not stored or stored in a format that requires a separate analytical layer to extract. Even with the data, the analytical move — "is this error sequence consistent with a known misconception trajectory?" — requires a misconception model the quiz tool does not have.

### Signal 3 — Cross-context transfer

*What it measures.* Whether a student can apply a concept in a context the instruction did not explicitly cover. This is Bjork's definition of learning operationalized — a concept the student "has" is one they can use outside the cue conditions in which they encountered it.

*Interaction design required.* The system has to present the concept in one context, then present a different context that requires the same concept, and observe whether the student retrieves the concept without a direct cue. The second presentation has to be *outside* the original context's recognition cues.

*What bolt-on cannot do.* Most assessments are within-context — they test the concept in the same kind of problem the instruction used. Cross-context transfer requires deliberately divergent problems, sequenced so the student does not know the second problem is "the same concept." A Canvas quiz designed by a professor who already knows the concept will tend to present recognizable variants. A platform that gates on transfer has to generate the divergent context as a design move, not inherit it from existing question banks.

### Signal 4 — Uncertainty calibration

*What it measures.* The gap between what the student knows and what the student thinks they know. A well-calibrated student is confident on what they are right about, uncertain on what they are wrong about. A miscalibrated student — typically one who borrowed certainty rather than earned it — is confident regardless of accuracy.

*Interaction design required.* Confidence rating elicited *before* the answer is revealed. The rating + the accuracy + the calibration over many items is the signal.

*What bolt-on cannot do.* Confidence-before-correctness is a specific interaction design. Canvas quizzes default to "submit answer, see correctness." Even if Canvas can be configured to elicit confidence, the calibration data lives in Canvas and is not cross-referenced with the other six signals. Calibration in isolation is informative; calibration as one input to a composite GLP score requires the same system to hold all seven signals.

### Signal 5 — Social knowledge texture

*What it measures.* The signature of authentic encounter with material. A learner who has actually engaged with the content shows it in the texture of their questions — specific confusions ("why does the reaction go this direction and not the other?" rather than "I don't understand this section"), genuine surprise when a result resolves differently from expectation, position changes that track developing understanding rather than authority signals.

*Interaction design required.* Free-form question logging, position-change tracking across a session, surprise/expectation logging at decision points. The texture is in the natural-language interaction, not in the assessment.

*What bolt-on cannot do.* This is the signal a bolted-on chatbot most obviously misses, because the chatbot logs lives outside the system that tracks the rest of the student's session. A general-purpose chatbot answers the question and forgets it. The texture across the student's interactions over a week — the pattern of *how their questions changed* as they engaged with the material — exists only if the same system that holds the questions also holds the positions and the assessment trajectory.

### Signal 6 — Retrieval strength decay signature

*What it measures.* The rate at which performance on a tested concept decays in the days after the test. A student with storage strength shows slow decay — they can be retested at two weeks with modest loss. A student with retrieval strength only — the student who "peaked at the test" — shows fast decay because there was no consolidation underneath the performance.

*Interaction design required.* Scheduled retest at intervals calibrated to the learner's demonstrated decay rate, not to the professor's syllabus. The decay signature is the difference between the immediate score and the retest score, modulated by spacing.

*What bolt-on cannot do.* This is the most direct argument against the Khanmigo deployment as currently designed. A platform that advances on the post-test result has been fooled by a performance peak. The decay signature requires the platform to come back, on a schedule it chose, with the concept the student tested on weeks earlier — and to be the same platform, with the same record of what the student knew then, so the delta can be computed. A spaced repetition tool can do *its* version of this for the items in *its* deck, but cannot do it for the concepts the case study tool or the chatbot were meant to teach.

### Signal 7 — Scaffolding response curve

*What it measures.* The performance gain from a partial structural hint. A student with genuine partial understanding has a zone of proximal development: a small activation (a half-explained step, a redirected cue) produces nearly the gain that a full explanation would. A student who borrowed the structure has no ZPD — the hint produces no improvement because there is no underlying structure to activate.

*Interaction design required.* The system must observe performance at time T, deliver a partial hint, observe performance at time T+1, and log the delta. This is a specific interaction sequence that does not exist by default in any general-purpose tool.

*What bolt-on cannot do.* Chatbots that give the answer collapse this distinction. A chatbot that gives a hint instead of an answer exists in some configurations (Bastani's GPT-Tutor, Khanmigo's documented prompt structure) — but the delta-before-and-after-the-hint is the signal, and that delta is only computable if the system logs the performance state on both sides of the hint. Most chatbots log only the response; the cognitive state of the student before and after the hint is not stored in any form a downstream analytic layer could use.

### The bolt-on summary

The argument is structural, not contingent on any specific tool's limitations. The seven signals are *byproducts of specific interaction designs.* Canvas was not designed to produce these byproducts because Canvas's purpose is course administration. A standalone chatbot was not designed to produce them because the chatbot's purpose is question-answering. A spaced repetition tool produces signal 6 *only for the items in its deck*, not for the concepts the case study tool covered. You cannot extract from an instrument the signals it was never measuring.

The architectural consequence: the measurement infrastructure and the learning infrastructure must be the same system. Not parallel, not bolted-on. The same system, because the measurements only exist as byproducts of the interaction designs that produce the learning. Pull them apart and you have a learning system that produces no evidence and a measurement system that has no learning to measure.

---

## C. The four layers — one paragraph each

### Layer 1 — Book Library (domain-specific content)

The content layer is the textbook in its multiple incarnations. Each base book in the library is structured around the concept node map that Layer 2 produces, and each base book has multiple framings: Prompt Engineering for Art and Design students, Organic Chemistry for pre-med students, Algorithms for non-CS majors. Same concept graph, different voice, different worked examples, different motivational frame.

The argument the Book Library makes against the bolt-on alternative is the domain-specificity finding (see `pantry/domain-specific-instruction-research.md`). Level 1 (generic) and Level 2 (generic + domain capstone) instruction underperform Level 3 (domain-specific throughout with generic backbone) on near-transfer and motivation — at production cost factors of 1.5× to 2× over generic. A bolt-on tool inherits whatever textbook the institution licensed; the library produces the content the curriculum design layer ordered.

Sadler 2013 is the load-bearing study in this area — teachers who could identify common student misconceptions in their specific domain produced substantially larger gains than teachers who could not, controlling for content knowledge ([Sadler, Sonnert, Coyle, Cook-Smith & Miller 2013, *AERA Open* / *American Educational Research Journal*](https://journals.sagepub.com/doi/10.3102/0002831213477680) `[verify exact journal — domain-specific-instruction-research.md cites this work; double-check the journal and pagination before final draft]`). The implication for the library: the content the bandit chooses among must be content that is calibrated to the specific misconceptions students bring to the specific domain. Generic content cannot do this; cost-collapse-AI-generated content can begin to do it but requires faculty review to verify the misconception calibration is correct (Chapter 9 develops this).

### Layer 2 — Curriculum Design Layer (Tic TOC as instrument)

The curriculum design layer is upstream of every other layer. It is what produces the concept node map — the prerequisite graph, the outcomes specified at Bloom's-level granularity, the phase gate logic, the mode appropriateness flags — that the adaptive engine reads.

Tic TOC is the instrument: a structured intake conversation with the domain expert that converts their expertise into a specification a downstream layer can act on. The output is three artifacts (Kindle book, Medhavy course, Canvas course) from one design session, but the load-bearing output is the concept map. The map is what the engine adapts within. Without it, the adaptive engine is choosing among modes on an unstructured concept space, which is the "suggest 15 chapters" failure that Chapter 8 develops.

The argument against the bolt-on alternative is structural: prior platforms inherited course structure from the professor's existing syllabus. Inheriting a syllabus inherits its pedagogical gaps — the prerequisite assumption that was never made explicit, the Bloom's-level ambiguity ("students will understand X" vs. "students will calculate Y given Z"), the assessment that did not align with the stated outcome. The bandit then adapts within a structurally broken concept space and produces adaptation that is technically correct and pedagogically incoherent.

### Layer 3 — Adaptive Engine (within-learner contextual bandit)

The adaptive engine is what most people mean by "the AI." It is the layer that selects, for this learner on this concept at this point in time, which of the four modes (Ask AI, Case Study, Quiz Me, Glimmer — Chapter 6 unpacks each) to offer next. The selection is a within-learner contextual bandit: each learner is their own experiment, and the engine's reward signal updates per learner per concept per session.

The contextual bandit formalism is the slot-machines-with-side-information framing that Chapter 7 develops. The "context" in Medhavy is (learner history × concept prerequisites × time since last session × prior mode performance × GLP component scores). The "arms" are the four modes. The "reward" is the composite GLP score from Layer 4. Update mechanics: the engine updates after each session.

The argument against the bolt-on alternative: most adaptive platforms use *cross-learner* generalization — they learn from one cohort which approaches work, then apply those approaches to the next cohort. This requires the assumption that learners are similar, which is the assumption the multi-mode design exists to refuse. Within-learner adaptation requires more sessions to converge but does not require the similarity assumption, and is the design choice consistent with the "intelligence is not one thing" argument (Chapter 1).

### Layer 4 — Measurement Layer (GLP framework)

The measurement layer is the seven-signals enumeration above, formalized as the GLP framework with its seven components (Y1–Y7) and ensemble architecture. It is the input to Layer 3's reward signal. Chapter 5 develops it in full; Chapter 4 introduces it as the layer that closes the loop.

The closed loop is the architectural claim. Layer 2 produces the concept map. Layer 1 produces the content at each node. Layer 3 selects the mode at each node. Layer 4 measures whether the mode produced genuine learning. That measurement updates Layer 3's selection policy for this learner on this concept. The next session begins with an updated policy.

Without Layer 4, Layer 3 is optimizing on engagement proxies — the IDK-IDK failure structurally restated. With Layer 4 but without Layers 1–3, Layer 4 has nothing to measure because the system has no learning infrastructure to instrument. The four layers cohere only as a loop, not as a collection.

---

## D. The integration — why the loop is the architecture

The integration argument is the chapter's central move. The pantry document `pantry/04-what-makes-this-different.md` (an earlier internal draft of this material) makes this argument cleanly: every prior platform optimized within one layer. Knewton had item selection within a content bank — one part of Layer 3, with no Layer 1, no Layer 2, no Layer 4. DreamBox has adaptive mathematics practice — a version of Layer 3 in a narrow domain. Khanmigo has Ask AI — part of Layer 3 — without the concept node map, without the multi-framing content library, without the GLP measurement.

What the loop produces that the layers individually cannot:

1. **The bandit knows what it is adapting within.** A bandit that selects among modes without a concept map is choosing on a topology it does not understand. With the map, the bandit knows which prerequisites a concept depends on, and can route to remediation before adapting on the surface concept.

2. **The content layer knows what the engine asked for.** Multiple framings of a concept are useful only if the engine can specify *which framing* is appropriate for *which learner*. Without the alignment between framings and the concept map, the library is a set of textbooks rather than the operational raw material the engine can choose among.

3. **The measurement layer measures the right thing.** A general "is the student learning?" question is unanswerable. A specific "is the student learning *this concept* under *this mode* with *this content framing*?" question is answerable because the question has handles. The handles come from Layers 1–3.

4. **The reward signal updates a policy that has structure.** A bandit that updates a flat policy over modes is operating on the wrong granularity. The policy that gets updated is (mode × concept × time × context). The structure comes from the concept map and the content library.

The closed loop is not a feature of the architecture. It is the architecture. The four boxes drawn separately are a stack; the four boxes drawn with the feedback arrow from Layer 4 back to Layer 3 are a system.

---

## E. Worked example sketch — one student session

For the chapter's worked example (Section 4 of the TIKTOC chapter anatomy). A medical student named *(label: illustrative case)* working through an oncology concept — say, the mechanism of action of immune checkpoint inhibitors — in the Medhavy cancer textbook deployment.

**Session start.** The student opens the chapter. Layer 1 (Book Library) delivers the medical-school framing of the concept, with worked examples drawn from clinical scenarios. Layer 2 (Curriculum Design) has already specified the prerequisite map: the student must have demonstrated understanding of T-cell receptor signaling and tumor antigen presentation before this concept becomes appropriate. The system checks the learner's profile — both prerequisites are flagged as "demonstrated, decay < 14 days." The concept is unlocked.

**Mode selection.** Layer 3 (Adaptive Engine) receives the context (learner has high prior GLP scores on mechanism-style questions, low confidence on quantitative pharmacology, last session was Quiz Me on the prerequisite concepts). The bandit selects Ask AI as the entry mode — the student is building a representation of a new mechanism and the historical reward signal favors Ask AI for this learner on mechanism-style content.

**Interaction.** The student asks: *"Why does PD-1 blockade work in some tumors and not others?"* The Ask AI mode (context-anchored, hint-only — Chapter 6 develops this) responds with a question rather than the answer: *"What did you observe about T-cell exhaustion in the prerequisite section that might be relevant here?"* The student's reply is logged. The system records uncertainty calibration (the student stated 60% confidence before answering; their answer was partially correct), error trajectory (the student's misconception aligns with a known misconception in the concept map), and social knowledge texture (the question is specific to the mechanism, not a generic "I don't understand").

**Measurement update.** Layer 4 (Measurement) processes the interaction. Y1 (temporal engagement) — the student spent 4 minutes on the question, consistent with the difficulty norm. Y2 (error trajectory) — the misconception is the *known* misconception, and the system tags this as a remediation opportunity. Y4 (uncertainty calibration) — the student was appropriately uncertain. The composite GLP score is updated.

**Policy update.** Layer 3 receives the measurement update. The reward signal for (Ask AI × immune checkpoint inhibitors × this learner) is positive but not maximal. The bandit notes that the next session for this concept should probably include a Quiz Me phase to convert the partial understanding to storage strength, and queues the spaced retrieval interval per the FSRS-style scheduler.

**What an LMS + standalone chatbot deployment would have produced.** A Canvas page view of 4 minutes. A chatbot conversation log stored separately, with no link to the concept map. No uncertainty calibration. No error trajectory coherence (the chatbot has no model of which misconceptions are known). No update to anything — the next time this learner returns to the platform, the system has no record of what they understood or what they confused.

This is the chapter's "first time the reader sees all four layers operating simultaneously" moment. The contrast is what carries the argument.

---

## F. Cross-references to existing pantry

The Chapter 4 argument leans on, and does not re-research, material that is already in the pantry. Cite by filename:

- `pantry/02-why-does-solving-it-require-a-platform.md` — the source of the seven signals enumeration in plain English. The current Ch 4 notes are a tightening of this material for the textbook-chapter context. The same seven signals are formalized as Y1–Y7 in the Ch 5 GLP framework.

- `pantry/04-what-makes-this-different.md` — the source of the four-layer integration argument as previously stated. The earlier draft frames Layer 2 as "curriculum design" with Tic TOC and Layer 4 as "GLP measurement"; this chapter inherits both. Use directly for the integration paragraph and the comparison-to-prior-platforms section (Knewton, DreamBox, Khanmigo).

- `pantry/ask-ai-research.md` — for Bastani PNAS 2025, ITS effect sizes (VanLehn 2011 *d* ≈ 0.76 for step-based ITS), the "lost in the middle" context-rot finding (Liu et al. 2023; Chroma 2025), and the fluency-trap evidence (Lee et al. 2025 CHI). These power the Layer 3 / Ask AI paragraph and the argument for context-anchored guardrails. Do not re-cite — quote from the existing note.

- `pantry/case-study-research.md` — for Thistlethwaite 2012 BEME synthesis. The Layer 1 / Layer 3 boundary in Case Study mode rests on the "pre-written, faculty-reviewed" specification this note documents.

- `pantry/quiz-me-research.md` — for the Roediger & Karpicke 2006 retrieval-practice canon, Cepeda 2006/2008 spacing meta-analyses, and FSRS as scheduling-algorithm citation. These power the Quiz Me sub-paragraph in the Layer 3 description.

- `pantry/glimmer-research.md` — for Fiorella & Mayer 2016 generative-learning synthesis, Jonassen 1997 ill-structured-problems framework, and the "construct confusion" warning that Glimmer is not one of GLA/EI/ISP/PBL but a hybrid. Layer 3 / Glimmer paragraph cites this.

- `pantry/glimmer-displacement-research.md` — for Pea 2004 on scaffolding withdrawal, the "permanent scaffolding is not scaffolding" framing, and the pseudocode-problem failure mode. This material reappears more centrally in Ch 6 (Four Modes); in Ch 4 it supports the Layer 3 design rationale at one sentence's depth.

- `pantry/concept-sequencing-research.md` — for prerequisite-chaining literature, knowledge-component models, BKT/DKT, and the importance-weighted sequencing argument. Layer 2 / Curriculum Design paragraph cites this for the concept-map structure.

- `pantry/domain-specific-instruction-research.md` — for the Level-1 / Level-2 / Level-3 specificity decision (the 1.5–2× production cost figure in the Layer 1 paragraph comes from here), Sadler 2013 on PCK, and the Renkl & Atkinson worked-examples line. Layer 1 paragraph cites this.

- `pantry/educational-media-economics-research.md` — for the cost-collapse asymmetry (which is developed fully in Ch 10) and the Sesame Street $5/child/year benchmark. Ch 4 references this only in the Layer 1 paragraph as a forward pointer to Ch 9–10.

- `pantry/PEDAGOGY ARCHITECTURE.txt` — for the Medhavy-internal framing of why these five (now four, in the 1.5 deployment) approaches and not others, and the cold-start fallback to direct instruction. Ch 6 leans on this more heavily; Ch 4 references it for the Layer 3 description.

- `pantry/Causal Graphs_ A Testable Architecture for Pedagogical Research Using AI-Mediated Instruction.txt` — this is the *causal graphs / DAG* paper, not the GLP preprint. (See section H below — the GLP preprint as a standalone document does not exist in this pantry; what we have is the seven-signal description in `02-why-does-solving-it-require-a-platform.md`, plus the GLP-framework name and ensemble architecture sketch in `04-what-makes-this-different.md`.) The DAG paper supports the Layer 4 / measurement-as-experimental-substrate argument: Medhavy as policy executor, individual-level random assignment, SUTVA satisfied by design.

- `pantry/medhavy-1.5-feature-roadmap-complete.md` — for the current deployment state of each layer. Ch 4 references this to anchor "what Medhavy 1.5 does today" vs. "what Medhavy 2.0 will do when the bandit is live."

---

## G. Suggested chapter spine

Following the TIKTOC chapter anatomy:

1. **Opening case** — Charles Fadel raises the procurement objection. Reproduce the objection in his voice ("I could buy an LMS, a chatbot, a spaced repetition tool, and a case study library and connect them. Why a platform?").
2. **The seven signals** — enumerate; for each, state what it measures and what bolt-on cannot recover. This is the operational form of the bolt-on argument.
3. **Layer 1: Book Library** — what it produces, what it requires (domain specificity at Level 3), what bolt-on inherits instead.
4. **Layer 2: Curriculum Design (Tic TOC)** — what it produces (the concept map), why it must be upstream of adaptation, what happens when it's missing (the "suggest 15 chapters" failure — forward pointer to Ch 8).
5. **Layer 3: Adaptive Engine** — within-learner bandit, four modes, the slot-machine framing as preview of Ch 7.
6. **Layer 4: Measurement Layer** — the GLP framework introduced as the formal version of the seven signals, with full development deferred to Ch 5.
7. **The integration** — the loop. What it produces that the layers don't. The Knewton/DreamBox/Khanmigo comparison — each missed three of four layers, and the missing layers were structurally consequential.
8. **Worked example** — the one-session walkthrough.
9. **Assessable exercises** (TIKTOC specifies three).
10. **What would change my mind** + **Still puzzling** + **Bridge to Chapter 5**.

The bridge to Ch 5: "Measurement determines what every other layer can learn. Chapter 5 specifies the measurement layer first, because understanding it is prerequisite to understanding why mode design and engine design take the shape they do."

---

## H. Top three consequential gaps / flags

1. **The GLP preprint is not in the pantry as a standalone document.** What is in the pantry is (a) the seven-signal description in plain English in `02-why-does-solving-it-require-a-platform.md`, (b) the seven-component listing and ensemble-architecture framing in `04-what-makes-this-different.md`, and (c) the *Causal Graphs* paper in `Causal Graphs_ A Testable Architecture for Pedagogical Research Using AI-Mediated Instruction.txt`, which is an adjacent paper (Hattie's variables → DAG → Medhavy as experimental substrate) but is *not* the GLP preprint with formal Y1–Y7 specification. **Flag for Nik:** the chapter cites the "GLP preprint" but the canonical document for the seven components, ensemble architecture, tier-calibration table, and validation methodology described in TIKTOC Appendix C does not appear to exist as a finished artifact. The Ch 4 enumeration uses the plain-English version from `02-why-does-solving-it-require-a-platform.md` as authoritative; the Ch 5 formal Y1–Y7 specification will have to be reconstructed from the same source plus the ensemble-architecture sketch in `04-what-makes-this-different.md`.

2. **Sadler 2013 citation needs verification.** The "teachers who could identify common student misconceptions produced substantially larger gains" finding is cited in the existing `domain-specific-instruction-research.md` pantry note and reappears in the Medhavy book argument multiple times. The journal and pagination need to be verified before the Ch 4 draft cites it — `[verify: Sadler, Sonnert, Coyle, Cook-Smith & Miller 2013, exact journal — domain-specific-instruction-research.md should be the load-bearing source]`.

3. **The Layer 4 → Layer 3 update mechanic needs more specification.** The chapter claims a closed loop: Layer 4 measures, the measurement updates Layer 3's selection policy. The specific update rule — Thompson sampling vs. UCB1 vs. epsilon-greedy, prior on the reward function, convergence rate per learner — is Chapter 7 material. Chapter 4 must claim the loop without specifying the mechanics, and the chapter draft has to land this without leaving the reader's developer-half feeling hand-waved. The honest move is to specify what is in Chapter 7 and what is in `pantry/Contextual Bandits.txt` / `pantry/MVAL.txt` and not try to do Chapter 7's work here.

---

*End of Ch 4 research notes. Use the seven-signals enumeration and the four-layer paragraphs as the structural backbone; lean on the existing pantry notes (cited by filename in section F) rather than re-researching the underlying literature.*
