# Research Notes — Appendix A: The Medhavy Lexicon

*Pantry note for Appendix A — the reference vocabulary glossary that the book uses to make the design conversation between Charles Fadel (the commissioning reader) and the developer (the implementing reader) possible. Compiled 2026-05-17. Companion to the Chapter 12 design-conversation notes (`pantry/12-the-design-conversation_notes.md`), which establishes that the lexicon is itself the operational test of whether the book delivered on its promise: both readers can say the same sentence about the same design decision in the same vocabulary by the end of the book.*

*This is not a chapter. It is a reference appendix. The 7-section gatherer format is adapted: §A enumerates the lexicon entries themselves (each entry is the "concept"), §B–G follow standard form. The appendix author's job is to translate the precise definitions and chapter mappings below into 1–2 entries per term, sorted alphabetically, with cross-references rendered as inline links.*

---

## A. The lexicon entries — definitions and chapter mappings

The thirteen terms below are the platform-specific vocabulary the book introduces. They are listed here in the order TIKTOC Appendix A specifies (which is roughly the order they first appear in the book), not alphabetically. The final appendix should alphabetize for reference use. Each entry below carries: (1) the precise definition the appendix should land in 2–4 sentences; (2) the first-appearance chapter and section; (3) cross-references to other entries with which it interacts; (4) the canonical pantry source for the term.

### A.1 The IDK-IDK problem

*Definition.* The IDK-IDK problem is the documented failure mode in which a student types "I don't know, I don't know" into a Socratic chatbot prompt, the system records the exchange as engagement, and durable learning does not occur. The chatbot's Socratic guardrail leaks under student pressure — Common Sense Media has documented that "persistent prompting would lead to Khanmigo offering a more complete answer" — and the session is logged as a successful tutoring interaction while the GLP composite score for the same session is near zero. The IDK-IDK problem is the canonical instance of measuring engagement and calling it learning. It is what the entire four-layer architecture exists to forestall.

*First appearance.* Chapter 1, §opening case (the Khanmigo IDK-IDK incident — Kristen DiCerbo, Khan Academy CAO, publicly acknowledged the pattern: *"I will tell you, we see more 'IDK IDK,' more passive kinds of interaction than we would like"*).

*Cross-references.* The measurement layer (§A.4); Genuine Learning Probability (§A.13); the fluency trap (§A.10); engagement vs. learning.

*Canonical source.* `pantry/01-what-is-an-intelligent-textbook_notes.md` §A.3 (the all-AI failure mode) and §B.1 (the Khanmigo IDK-IDK incident as worked example). Primary citations: Common Sense Media review of Khanmigo; Dan Meyer Substack, "RIP Khanmigo and EdTech Industry Dreams of AI Tutors"; Khan Academy 2024 efficacy blog. The DiCerbo quote's exact venue and date carries a `[verify]` flag in the Chapter 1 notes.

### A.2 The four layers — Book Library / Tic TOC / Adaptive Engine / Measurement Layer

*Definition.* The four layers are the architectural decomposition of an intelligent textbook into the four kinds of work the platform must do simultaneously. The Book Library (Layer 1) supplies the domain-specific content, multi-framed for the audiences the curriculum serves. Tic TOC (Layer 2 — the curriculum design layer) produces the concept node map, the prerequisite graph, and the mode-appropriateness flags that the engine adapts within. The Adaptive Engine (Layer 3) is the within-learner contextual bandit that selects, for this learner on this concept at this moment, which of the four modes to offer. The Measurement Layer (Layer 4) is the GLP framework — the seven friction signals — that supplies the reward signal closing the loop back to Layer 3. The architectural claim is that the integration is the architecture: none of the four layers does anything useful in isolation, and the closed loop converts a stack of tools into a learning system.

*First appearance.* Chapter 1, §A.4 (the four-layer architecture as the answer to the Khanmigo / Horvath measurement-error question). Specified in full in Chapter 4 ("The Four Layers"), where each layer gets one paragraph and the integration argument is developed.

*Cross-references.* The within-learner bandit (§A.6); Genuine Learning Probability (§A.13); the seven signals (§A.4); phase gates (§A.5); the four modes (§A.3); the conductor (§A.9).

*Canonical source.* `pantry/04-the-four-layers_notes.md` §C (the four layers — one paragraph each). The earlier internal source is `pantry/04-what-makes-this-different.md`; the chapter-level introduction is in `pantry/01-what-is-an-intelligent-textbook_notes.md` §A.4.

*Naming note.* "Tic TOC" is the Medhavy-internal name for the curriculum design layer (the table of contents that ticks — concepts that have been demonstrated as known turn green; concepts that are due turn yellow; concepts whose retest is overdue turn red). The pun is deliberate. The book's outline tool (the TIKTOC) is named after the same instrument; the appendix should distinguish "Tic TOC the curriculum-design layer" from "the TIKTOC outline tool" if both are referenced in the same paragraph.

### A.3 The four modes — Ask AI / Case Study / Quiz Me / Glimmer

*Definition.* The four modes are the action arms the adaptive engine selects among for any given (learner, concept, moment) triple. **Ask AI** is the conversational mode, context-anchored to the current section and the prerequisites graph, with hint-not-answer guardrails (per the Bastani et al. 2025 GPT-Tutor specification). **Case Study** is the application-stage mode in which the student works through a faculty-curated, pre-written case with an AI facilitator that asks Socratic questions but does not supply the verdict. **Quiz Me** is the spaced retrieval practice mode, scheduled by FSRS (Free Spaced Repetition Scheduler), with phase-gate logic that does not surface items for material the student has not demonstrated reading engagement with. **Glimmer** is the creative-cumulative mode — an ill-structured problem at the session level (Jonassen 1997, 2000), with backwards-faded scaffolding (Atkinson, Renkl & Merrill 2003) that fades from the back of the solution toward the front as the learner's competence grows. Each mode has a characteristic failure when used as the only available move; the platform's job is to know which mode to deploy when.

*First appearance.* Chapter 6 ("The Four Modes"), §A (the hammer problem at mode level). Each mode gets its own section (B–E) with evidence base and phase gate; the integration into the engine's arm space is the bridge to Chapter 7.

*Cross-references.* Phase gates (§A.5); the within-learner bandit (§A.6); the seven signals (§A.4); the due-today counter (§A.12, the load-bearing UI element for Quiz Me); the fluency trap (§A.10, the failure mode unguarded Ask AI produces).

*Canonical source.* `pantry/06-the-four-modes_notes.md` §§B–E. Mode-specific evidence bases live in `pantry/ask-ai-research.md`, `pantry/case-study-research.md`, `pantry/quiz-me-research.md`, `pantry/glimmer-research.md`, and `pantry/glimmer-displacement-research.md`. The Medhavy-internal source for the mode selection rationale is `pantry/PEDAGOGY ARCHITECTURE.txt`.

*Historical note.* The older five-approach formulation included Direct Instruction as a separate arm. Medhavy 2.0 consolidates Direct Instruction into Ask AI; the appendix should record this consolidation explicitly so readers of older Medhavy documentation can map the change.

### A.4 The seven signals — the GLP friction components Y1–Y7

*Definition.* The seven signals are the operational measurements that distinguish genuine learning from engagement. They are the formal Y1–Y7 components of the GLP framework: **Y1 Temporal Engagement Pattern** (time distribution across the difficulty surface of a concept, not output length); **Y2 Error Trajectory Coherence** (the conceptual coherence of a learner's wrong answers across attempts, with respect to a misconception model); **Y3 Cross-Context Transfer** (whether the learner applies a concept in a context the instruction did not directly cue); **Y4 Uncertainty Calibration** (the correlation between expressed confidence and actual accuracy across many items); **Y5 Social Knowledge Texture** (the signature of authentic encounter with material in the texture of the learner's questions, positions, and surprise reactions); **Y6 Retrieval Strength Decay Signature** (the rate of performance decay between an initial demonstration and a scheduled retest); **Y7 Scaffolding Response Curve** (the performance gain produced by a partial structural hint, as a function of where the learner is in their developing understanding). The seven components are designed to be partially independent — gaming them simultaneously approaches the cognitive cost of the learning they were designed to measure.

*First appearance.* Chapter 1, §A.4 (the four-layer architecture sketch names them as Y1–Y7 at the layer-4 description). Enumerated in plain English in Chapter 4 (§B, the bolt-on failure — what the seven signals require). Specified as the formal Y1–Y7 framework in Chapter 5 (§C — the seven GLP components, full enumeration).

*Cross-references.* Genuine Learning Probability (§A.13, the composite); phase gates (§A.5, which use specific signals as gating criteria); the GLP reward signal (§A.7); the IDK-IDK problem (§A.1, the worked example of low GLP across all seven); the fluency trap (§A.10, what high engagement and low GLP looks like).

*Canonical source.* `pantry/05-the-measurement-layer_notes.md` §C (formal Y1–Y7 specification). Plain-English source: `pantry/02-why-does-solving-it-require-a-platform.md` (the seven-signal description in plain English). Ensemble architecture sketch: `pantry/04-what-makes-this-different.md`.

*Verification flag.* The GLP preprint as a finished standalone document does not appear in the pantry. The Y1–Y7 specification above is the best reconstruction from existing pantry material; it needs Nik's review before becoming canonical. This is flagged at the chapter level (Ch 4 and Ch 5 notes) and should be flagged here as well.

### A.5 Phase gates

*Definition.* Phase gates are the mode-selection conditions that determine when a given mode becomes available for a given learner on a given concept. Each gate uses a specific GLP signal as its gating criterion: Quiz Me is gated by Y1 (the student must have demonstrated reading engagement before retrieval practice is appropriate); Glimmer is gated by Y7 (the student must show hint-responsive understanding before ill-structured problem-solving is appropriate); Case Study is gated by Y3 plus Y6 (the student must be able to apply the concept outside instructional context, and the concept must be in storage rather than transient performance); Ask AI is not gated, but is bounded by context-anchoring to the prerequisites graph. The argument the appendix should record: **phase gates are not merely pedagogical decisions; they are measurement decisions.** Mode selection on the learner's behalf, using evidence the learner does not have direct access to, is what makes the four modes a system rather than a menu.

*First appearance.* Chapter 6 (§F — phase gates as measurement decisions). Foreshadowed in Chapter 4's Layer 2 (curriculum design) and Chapter 5's component specifications.

*Cross-references.* The seven signals (§A.4); the four modes (§A.3); the within-learner bandit (§A.6); the fluency trap (§A.10, what the absence of phase gates lets through).

*Canonical source.* `pantry/06-the-four-modes_notes.md` §F. The phase-gate-as-measurement-decision framing is the chapter's most original move.

### A.6 The within-learner bandit

*Definition.* The within-learner bandit is the algorithmic specification of the Adaptive Engine: a contextual multi-armed bandit whose arms are the four modes, whose context is a feature vector (learner history × concept prerequisites × time since last session × prior mode performance × GLP component scores), whose reward is the composite GLP estimate, and whose policy update is **per learner**, not pooled across learners. The within-learner discipline does not require the assumption that learners are similar (which the cross-domain learning analytics literature has not been able to validate at scale, per Yudelson, Koedinger & Gordon 2013 on individualized BKT). It costs more sessions to converge than cross-learner pooling — each learner's bandit starts from a cold-start prior — but the convergence is to a policy that is statistically distinct for this learner, not to a population mean diluted by the wrong subgroup. The Medhavy 2.0 implementation choice is Thompson Sampling (rather than ε-greedy or UCB1) because it extends naturally to contextual bandits, handles non-stationarity, and the Bayesian framing maps cleanly onto the "prior weights from evidence base, posterior from deployment data" architecture.

*First appearance.* Chapter 1 (named in the §A.4 four-layer sketch as the Adaptive Engine). Specified in Chapter 4 (§C.3 — Layer 3, Adaptive Engine, one paragraph). Developed in full in Chapter 7 ("The Adaptive Engine"), §C (the casino and its formalization) through §D (within-learner vs. cross-learner — the consequential design decision).

*Cross-references.* The four modes (§A.3 — the bandit's arms); the GLP reward signal (§A.7 — what the bandit optimizes); the seven signals (§A.4 — what feeds the reward); the conductor (§A.9 — the metaphor the chapter uses to name the bandit-as-experimentalist).

*Canonical source.* `pantry/07-the-adaptive-engine_notes.md` §C–§E. Theoretical backbone in `pantry/_lib_reinforcement_learning_an_introduction.md` (Sutton & Barto Ch 2). Bayesian framing in `pantry/_lib_everything-is-predictable_-how-bayesian-statistics-explain-our-world.md`. Medhavy-internal implementation in `pantry/medhavy-1.5-feature-roadmap-complete.md` Appendix and `pantry/MVAL.txt`.

*Foundational citations.* Robbins, H. 1952. "Some Aspects of the Sequential Design of Experiments," *Bulletin of the AMS* 58(5): 527–535 (the formalization). Thompson, W. R. 1933. "On the Likelihood that One Unknown Probability Exceeds Another in View of the Evidence of Two Samples," *Biometrika* 25: 285–294 (the historical primary source for Thompson sampling). Auer, Cesa-Bianchi & Fischer 2002. "Finite-time Analysis of the Multiarmed Bandit Problem," *Machine Learning* 47: 235–256 (UCB1).

### A.7 The GLP reward signal

*Definition.* The GLP reward signal is the composite quantity the within-learner bandit maximizes: a weighted combination of the seven Y-components, augmented by a delayed retrieval probe (proposed at seven days) that supplies the most direct measurable proxy for durable learning the platform has. The initial weights come from the evidence base — spaced retrieval has strong evidence, CBL has moderate evidence under specific conditions, Glimmer-style ill-structured problems have transfer evidence with anxiety failure modes for novices, Ask AI has Bastani 2025 as the cautionary data point. The weights update from deployment data, within the within-learner discipline. The signal is *composite* (not single-channel) and *delayed* (not within-session) — both choices are architectural commitments against the engagement trap. The right weights are one of the book's eight open bets (TIKTOC Ch 11, bet #6).

*First appearance.* Chapter 5 (named as the engine input the measurement layer produces, §C and §I). Specified in full in Chapter 7 (§E — the reward function — and the engagement trap), where the casino-owner-watching-through-the-security-camera image lives.

*Cross-references.* The within-learner bandit (§A.6 — what the signal feeds); the seven signals (§A.4 — what the signal is composited from); Genuine Learning Probability (§A.13 — the underlying construct); the fluency trap (§A.10 — what an engagement-shaped reward signal silently produces).

*Canonical source.* `pantry/07-the-adaptive-engine_notes.md` §E. The neurobiological grounding (why the seven signals exist as byproducts of learning) is in `pantry/05-the-measurement-layer_notes.md` §B (Schultz 1997 on dopamine prediction error; Cowansage 2010 on BDNF; Yang, Pan & Gan 2009 on dendritic spines).

*Casino-owner image.* The chapter's central engagement-trap image, sourced to TIKTOC Ch 7. The casino is the platform; the gambler is the learner; the slot machines are the modes; the casino owner is the platform's measurement system. The security camera sees what the casino owner wants it to see — time on machine, repeat play, return visits — and not whether the gambler is going home with money. In learning terms: whether durable knowledge actually accumulated. The platform-as-casino metaphor is uncomfortable on purpose.

### A.8 Ambient infrastructure

*Definition.* Ambient infrastructure is the design commitment that the platform travels with the learner across contexts — phone, Canvas, co-op placement, field trip, museum kiosk — rather than confining learning evidence to controlled platform interactions. The hypothesis: transfer observed in a real work context (debugging code on a co-op, applying a concept in a clinical rotation, recognizing a phenomenon at a museum exhibit) is qualitatively richer than transfer observed on a practice problem inside the platform. Ambient infrastructure is what makes Y3 (cross-context transfer) measurable beyond the platform's deliberately divergent items. As of 2026 it is **aspirational** — the instrumentation for collecting authentic-context evidence is being designed; the data is not yet flowing. The appendix should record this honestly.

*First appearance.* Chapter 5 (the measurement layer's claim that the seven signals can in principle be measured beyond the platform). Developed in Chapter 11 (the platform-does-not-know-yet inventory — what the ambient context evidence reveals is named there as an open question, and the consent gating for ambient instrumentation is specified).

*Cross-references.* The seven signals (§A.4, specifically Y3); the within-learner bandit (§A.6, which can in principle use ambient evidence as context features); the conductor (§A.9, which can see both platform and ambient evidence).

*Canonical source.* `pantry/05_what_doesnt_it_know_yet.md` §5 (what the ambient context evidence reveals). Also referenced in `pantry/11-what-the-platform-does-not-know-yet_notes.md` and `pantry/04-what-makes-this-different.md` §[ambient infrastructure transfer evidence is aspirational]. Consent design for ambient instrumentation is in `pantry/11-what-the-platform-does-not-know-yet_notes.md` §[Behavioral data outside the learning system — the platform does not act as a generic surveillance tool just because it could].

*Honesty caveat.* Ambient infrastructure is the most aspirational of the lexicon entries. The appendix should not let the reader confuse ambient *intent* with ambient *deployment*. The Medhavy 1.5 deployment is platform-bound; the Medhavy 2.0 roadmap names ambient instrumentation as a development priority.

### A.9 The conductor

*Definition.* The conductor is the metaphor for what the within-learner bandit is doing — not a recommendation engine choosing among preferences, but an experimenter running a continuously updating experiment on this learner to find what produces genuine learning for them on this concept right now. A recommendation engine optimizes engagement: it learns revealed preferences and serves them back, refined. A conductor optimizes the *destination* (the cognitive structure the concept requires, the transfer capability the curriculum specified) and uses preferences as evidence about *which path* gets this learner there. The spinach principle: if spinach doesn't work for this learner, the conductor doesn't conclude vegetables are wrong and serve chocolate instead — the conductor finds what achieves the same nutritional outcome in a form that works. The score tells the conductor what needs to be played; preferences tell the conductor which instrument to reach for. The conductor is accountable for the outcome (the learner can now do something they couldn't do before — explain, calculate, apply, transfer, create); a recommendation engine is not.

*First appearance.* Chapter 3 (the conducting-AI frame, specifically the recommendation-engine-failure section in `pantry/06-medhavy-conducting-ai.md`). The conductor framing reappears across the book wherever the within-learner bandit is the subject. Chapter 12 (the design conversation) makes the conductor a load-bearing metaphor: the human conducting Medhavy as the orchestra is the design conversation between Charles Fadel and the developer.

*Cross-references.* The within-learner bandit (§A.6 — the conductor *is* the bandit); the GLP reward signal (§A.7 — what the conductor optimizes); the fluency trap (§A.10 — what happens to a conductor whose reward signal is engagement-shaped); the four modes (§A.3 — the conductor's available actions).

*Canonical source.* `pantry/06-medhavy-conducting-ai.md` (the chapter brief titled *"What Is the Conductor Doing?"*). The book-level framing — *the platform is opinionated; the model has no opinions of its own* — is the conductor's load-bearing claim restated. The metaphor is also referenced in `pantry/12-the-design-conversation_notes.md` §6 as one of the thirteen lexicon terms.

*Naming note.* "Medhavy" itself means *intelligent* / *learned* in Sanskrit; the conductor framing is the operationalized version of what "intelligent" means in this platform context. The appendix entry should land this if space allows.

### A.10 The fluency trap

*Definition.* The fluency trap is the failure mode in which the learner genuinely *believes* they have learned, and is wrong. Human metacognition uses perceptual fluency as a proxy for understanding — a concept that can be read without halts feels understood. This heuristic is normally reliable (centuries of fluent-after-effort being a real signal); it fails specifically when fluency is produced *without effort*. Re-reading produces fluency-without-effort (Bjork & Bjork 1992 / 2011 on desirable difficulties). AI-mediated explanation produces fluency-without-effort at a higher rate than any prior instructional medium — language models are optimized for fluency; their outputs are smooth, well-organized, syntactically clean. The student reads the AI explanation; the explanation feels lucid; the metacognitive system reports understanding; the understanding is not there. Bastani et al. 2025 PNAS measured this directly: 48% performance lift during practice with unguarded GPT-4, 17% performance drop on the subsequent exam where AI was unavailable. The fluency trap is the IDK-IDK problem's inverse — the student no longer experiences not-knowing, so the platform's failure to gate on not-knowing closes silently.

*First appearance.* Chapter 5 (§E — the fluency trap, the smooth AI explanation, and the feeling of understanding). The Lee, Sarkar et al. 2025 CHI knowledge-worker survey (319 participants, 936 first-hand GenAI examples) is the cleanest non-classroom corroboration: higher confidence in GenAI was associated with less critical thinking; higher self-confidence was associated with more critical thinking.

*Cross-references.* Genuine Learning Probability (§A.13 — what catches the fluency trap when the learner cannot); the seven signals (§A.4 — specifically Y4 uncertainty calibration and Y6 retrieval decay, the two signals most diagnostic of the trap); the IDK-IDK problem (§A.1, the inverse failure mode); the four modes (§A.3 — Ask AI's hint-not-answer guardrail is the chapter-level defense).

*Canonical source.* `pantry/05-the-measurement-layer_notes.md` §E. Primary citations: Bastani et al. 2025 PNAS 122(26), e2422633122; Lee, Sarkar et al. 2025 CHI; Bjork & Bjork 1992, 2011 on desirable difficulties. Detailed in `pantry/ask-ai-research.md`.

*Uncomfortable claim.* The fluency trap entry implies that the platform is in some operational sense *more reliable about the student's learning than the student is themselves*. The appendix should land this without arrogance — human metacognition uses fluency as a proxy in conditions for which it was calibrated; AI-mediated learning produces fluency-without-effort, breaking the calibration; the platform observes a different signal (the seven friction byproducts) that the student does not have access to.

### A.11 Cost-collapse asymmetry

*Definition.* Cost-collapse asymmetry is the observation that AI generation has reduced production cost for some content (text, basic explanatory video, image generation, single-domain question banks) by one to three orders of magnitude, while leaving production cost for other content (high-production-value studio video; expert-vetted clinical scenarios; misconception-targeted instruction) approximately unchanged. The asymmetry matters because it shifts the burden of proof asymmetrically — Sunstein's *Laws of Fear* framing applied operationally: for content whose failure mode is small and reversible (a slightly awkward worked example), AI generation with light review is now defensible; for content whose failure mode is large or persistent (a clinical case that teaches a misconception, a probability problem whose answer is wrong), AI generation does *not* lower the burden of proof. The asymmetry has a corollary the appendix should land: *AI generation makes the cheap content cheaper; it does not make the expensive content cheap.* The total content production cost for a Level 3 (domain-specific-throughout) Medhavy deployment falls — possibly substantially — but the human-expert-authorship cost for high-stakes content remains the binding constraint.

*First appearance.* Chapter 1 (forward pointer in the §A.1 MIT OpenCourseWare framing — content was never the binding constraint, and AI generation accelerates this realization). Specified in full in Chapter 9 ("The Content Layer," §E — the cost-collapse asymmetry), and developed economically in Chapter 10.

*Cross-references.* The four layers (§A.2 — specifically Book Library); the four modes (§A.3 — Case Study mode's "pre-written, faculty-reviewed" specification is the asymmetry applied to one mode); the conductor (§A.9 — the conductor cannot conduct content that teaches a misconception).

*Canonical source.* `pantry/09-the-content-layer_notes.md` §E (the cost-collapse asymmetry). The Sesame Street comparator ($5/child/year producing measurable cognitive gains; Mares & Pan 2013, *d* = 0.29 on 15-country meta-analysis) is in `pantry/educational-media-economics-research.md`. Sunstein's burden-of-proof inversion framing is in `pantry/09-the-content-layer_notes.md` §E.3.

*Sesame Street standard.* The cost-collapse argument should not be confused with cost parity at quality. Sesame Street operates at roughly $5/child/year producing *d* = 0.29 on cognitive outcomes. AI content has achieved cost parity (and often beats it) but has not been shown to clear the Sesame Street design-quality bar for initial concept acquisition. The honest position the appendix records: deploy AI-generated content where the failure mode is small and reversible; retain expert authorship where the failure mode is large or persistent.

### A.12 The due-today counter

*Definition.* The due-today counter is the Quiz Me UI element that displays the number of retrieval items the FSRS scheduler has queued for the learner today — and, the appendix should record, **the load-bearing UI element for Quiz Me adoption**. The Zeigarnik effect (Zeigarnik 1927) names the mechanism: unfinished tasks produce a tension state that motivates completion. The counter creates and surfaces the Zeigarnik tension; the learner returns to clear it; the habit loop closes. Anki users report that the due-count is what they check, what they clear, and what defines the habit. The honest read the appendix should preserve: the algorithm (FSRS vs. SM-2 vs. Leitner) is a small contributor to whether students adopt the tool at all; the due-count is load-bearing. The engineering instinct is to optimize the algorithm; the design instinct should be to optimize the counter. Whether the Quiz Me habit loop is driven by the due-count or the algorithm is one of the book's eight open questions (TIKTOC Ch 11, bet #4).

*First appearance.* Chapter 6 (§D — Quiz Me; the due-today counter as Zeigarnik closure subsection). Returned to as one of the eight open bets in Chapter 11.

*Cross-references.* The four modes (§A.3 — specifically Quiz Me); the seven signals (§A.4 — specifically Y6 retrieval decay, the underlying mechanism the FSRS scheduling implements); the within-learner bandit (§A.6 — the bandit and the counter are different layers of the same habit-and-evidence loop).

*Canonical source.* `pantry/quiz-me-habit-research.md` (Zeigarnik effect, the Anki natural experiment, BJ Fogg's behavior model — motivation/ability/trigger, the Hooked framework — trigger/action/variable-reward/investment, and the *load-bearing UI* framing). FSRS specification and benchmarks: `pantry/quiz-me-research.md` §2. Underlying theory: Bjork & Bjork 1992 retrieval-strength/storage-strength duality.

*Counter-intuitive teaching point.* The due-today counter entry should preserve the discipline that the algorithm and the counter are doing different jobs. The algorithm produces good scheduling; the counter produces daily use. A platform that ships the world's best scheduling algorithm with a bad counter will have very few users producing very good learning trajectories. A platform that ships a Leitner-box algorithm with a great counter will have many users producing decent learning trajectories. The second platform produces more aggregate learning. The appendix should not let the reader optimize the wrong layer.

### A.13 Genuine Learning Probability (GLP)

*Definition.* Genuine Learning Probability (GLP) is the composite scalar the measurement layer produces — the platform's probabilistic estimate, conditional on the seven friction signals and (where available) the delayed retrieval probe, that genuine learning has occurred for this learner on this concept in this session. GLP is *not* engagement (time on platform, clicks, turns, completions); GLP is the byproduct of cognitive work that cannot be faked without doing equivalent cognitive work. The composite is an *ensemble* in the technical sense: multiple noisy classifiers (one per Y-component) whose errors are partially independent, combined via a tier-conditioned weighting to produce a calibrated scalar with quantified uncertainty. The ensemble architecture is what makes the system gaming-expensive — to produce a high GLP score by gaming, the gamer must manufacture all seven signals simultaneously, each of which is itself a byproduct of the cognitive work the system is designed to measure. The compositional gaming cost approaches the cognitive cost of genuine learning. The system is not gaming-*proof*; it is gaming-*expensive*. This is a meaningfully different design target than "make AI use undetectable."

*First appearance.* Chapter 1, §A.4 (named in the four-layer architecture sketch — *Y1 Temporal Engagement, Y2 Error Trajectory, …*). Specified in full in Chapter 5 (the full enumeration of the seven Y-components, the ensemble architecture, the neurobiological grounding, the fluency trap and arms-race arguments). Consumed by the within-learner bandit's reward function in Chapter 7.

*Cross-references.* The seven signals (§A.4 — the components GLP is built from); the GLP reward signal (§A.7 — how GLP enters the engine); the IDK-IDK problem (§A.1 — the worked example of low GLP); the fluency trap (§A.10 — what high engagement and low GLP looks like); the within-learner bandit (§A.6 — what GLP optimizes).

*Canonical source.* `pantry/05-the-measurement-layer_notes.md` §C, §D, §G. Neurobiological grounding: Schultz 1997 (dopamine prediction error, *Science* 275: 1593–1599); Cowansage 2010 (BDNF, *Current Molecular Pharmacology* 3: 12–29) and the broader Lu, Christian & Lu 2008 *Nature Reviews Neuroscience* review; Yang, Pan & Gan 2009 (dendritic spines, *Nature* 462: 920–924). All three citations carry `[verify]` flags in the Ch 5 notes; the appendix should propagate the flags.

*Foundational claim.* The Ch 5 chapter's payoff line is also the appendix entry's load-bearing sentence: *the artifact is no longer proof of the process. The process is the proof of the process. Measure the process and the artifact stops being load-bearing.* The appendix should record this as the GLP entry's epigraph or closing sentence.

---

## B. Domain examples and cases — illustrative anchors per term

For an appendix this is mostly redundant with the chapter-level worked examples, but the appendix should record where each term's canonical worked example lives so a reader looking up the term in the appendix can find the example without re-reading the chapter.

- **IDK-IDK problem** — Khanmigo quadratic-equation example (Ch 1 §B.1). A high-school student types "idk idk" through three to five turns; the system either offers a more complete hint or the student abandons.
- **Four layers** — One medical student session through immune checkpoint inhibitors (Ch 4 §E). All four layers operating simultaneously; the contrast with an LMS-plus-standalone-chatbot deployment is the carrying argument.
- **Four modes** — Pharmacokinetics mode sequence (Ch 6 §G). Ask AI → Quiz Me → Case Study → Glimmer across one concept's development; each transition gated by the appropriate Y-signal.
- **Seven signals** — Two students, one essay (Ch 5 §H). One student wrote the essay after genuine engagement; one used AI. The artifact is indistinguishable; the seven signals diverge sharply (Y6 retest at 14 days: 85% retention vs. 15%).
- **Phase gates** — Embedded in the pharmacokinetics example (Ch 6 §G) — Quiz Me gates on Y1 reading evidence; Case Study gates on Y3+Y6.
- **Within-learner bandit** — Six-week oncology trajectory worked example (Ch 7 §H). Cold-start to convergence; Glimmer reduction in week 4 after anxiety failure; Case Study allocation growth as concepts advance from Understand to Apply level.
- **GLP reward signal** — The same six-week oncology trajectory (Ch 7) with explicit reward function update at each session, showing Y6 update to the Quiz Me posterior.
- **Ambient infrastructure** — The platform-traveling description in Ch 5 (`pantry/05_what_doesnt_it_know_yet.md` §5) — phone, Canvas, co-op, field trip, museum kiosk. The example is aspirational; the appendix should flag this.
- **The conductor** — The spinach example (`pantry/06-medhavy-conducting-ai.md`): a learner who hates worked examples but loves case studies still needs procedural fluency; the conductor finds a case study that requires working through the procedure.
- **Fluency trap** — Bastani et al. 2025 PNAS: 48% practice lift, 17% exam drop. The 65-point swing is the cleanest in-education measurement.
- **Cost-collapse asymmetry** — The Sesame Street comparator in Ch 9 ($5/child/year, *d* = 0.29). The Veo/Sora vs. faculty-curated case scenario contrast in the same chapter.
- **Due-today counter** — The Anki-vs-SuperMemo natural experiment (`pantry/quiz-me-habit-research.md` §[Anki gets all three. SuperMemo (the academic ancestor) had the algorithm and the motivation but failed on ability]). Same algorithm class, vastly different interface, vastly different adoption.
- **Genuine Learning Probability** — The two-students-one-essay table (Ch 5 §H) is the canonical worked example for the GLP composite.

---

## C. Connections and dependencies — the lexicon as a graph

The thirteen entries are not independent. The appendix should let the reader see the connections, ideally with a cross-reference index at the end. The structural connections:

- The **measurement layer / seven signals / GLP** triangle is the conceptual core. Layer 4 *is* the seven signals' aggregate *is* GLP. Three names for one architectural commitment.
- The **within-learner bandit / four modes / GLP reward signal** triangle is the engine layer. The bandit selects among the modes; the modes generate interactions; the interactions produce GLP; the GLP updates the bandit's policy. The closed loop.
- The **phase gates** entry is the bridge between the measurement triangle and the engine triangle. Each gate uses a Y-signal as criterion; each mode's availability depends on a gate.
- The **IDK-IDK problem** and the **fluency trap** are paired failure modes: the IDK-IDK failure is the student who reports not-knowing into a system that does not gate on the report; the fluency trap is the student who no longer experiences not-knowing because the AI explanation produced the *feeling* of understanding without the cognitive work. They bracket the range of failures the GLP measurement layer exists to catch.
- The **conductor** is the metaphor that unifies the engine triangle for the reader who has been thinking of adaptive platforms as recommendation engines. The metaphor is load-bearing in Ch 3, redeployed in Ch 7, and named explicitly in Ch 12.
- The **cost-collapse asymmetry** entry sits outside the architectural core — it is about *content production*, which is Layer 1's input. But it is the entry that connects the four layers to the economic argument of Ch 10 and the design-conversation Ch 12. Without it, the appendix reads as an architecture spec; with it, the appendix reads as the platform's design philosophy.
- The **due-today counter** entry sits inside the Quiz Me mode but does conceptual work that should not be lost: the load-bearing UI claim is a counter-intuitive teaching point the book argues for. The appendix entry should not be a UI footnote.
- The **ambient infrastructure** entry is the most aspirational. It connects the four layers to the deployment surface beyond the platform — Canvas, mobile, co-op, museum. The appendix should record the honesty caveat: ambient *intent*, not yet ambient *deployment*.

The connections suggest a possible appendix structure: alphabetical entries (for reference) with a one-page "lexicon at a glance" diagram (for synthesis). The diagram could be the four-layer architecture with the lexicon terms placed at the layers they instrument; the IDK-IDK problem and the fluency trap as the bracketing failure modes; the conductor and the cost-collapse asymmetry as the cross-cutting design commitments.

---

## D. Current state of the field — what the lexicon competes with

The Medhavy lexicon is not the only platform-specific vocabulary in adaptive-learning discourse. The appendix should briefly record the field's existing vocabulary so the reader is not confused when other platforms' terms appear:

- **Knewton** introduced "knowledge graph" and "adaptive engine" as production terms. Both terms are now generic. Medhavy's "concept node map" (Tic TOC output) and "within-learner bandit" are the descendants. The appendix should record that "adaptive engine" in Knewton-derived usage typically means *cross-learner* adaptation; Medhavy's usage is explicitly within-learner.
- **DreamBox** introduced "intelligent adaptive learning" as a marketing term for K–8 mathematics adaptation. The term has lost specificity. Medhavy avoids it.
- **Khan Academy / Khanmigo** introduced "AI tutor" as a popular term. The book's claim is that AI tutor is a content-generation choice, not an architecture; the within-learner bandit is the meta-question the AI-tutor framing does not address.
- **ASSISTments** and the Knowledge Tracing literature use "BKT" (Bayesian Knowledge Tracing) and "DKT" (Deep Knowledge Tracing). Medhavy uses these terms internally (especially in Y2 error trajectory coherence and in the curriculum design layer's prerequisite-mastery state estimation), but does not promote them to the lexicon — they are technical primitives the book references rather than terms the Charles Fadel reader needs to be fluent in.
- **Carnegie Learning** uses "cognitive tutor" — the term traces to John Anderson's ACT-R-based ITS work at CMU. The Medhavy book treats cognitive-tutor evidence (VanLehn 2011's step-based ITS effect sizes; Kulik & Fletcher 2016) as the relevant prior for what well-designed Ask AI can produce, but does not adopt the term itself.
- **Open Spaced Repetition / FSRS** — the FSRS algorithm is named explicitly in the Quiz Me chapter; the appendix should record FSRS as a referenced specification rather than as a lexicon term. The Quiz Me mode uses FSRS as its scheduler; the due-today counter is the UI built on top.
- **Sesame Workshop / Children's Television Workshop** — the Sesame Street comparator is in the lexicon by reference (cost-collapse asymmetry entry); the design vocabulary of *formative research → measurement-first design → segmented production* is borrowed and acknowledged in Ch 9.

The Medhavy lexicon is small (thirteen entries) on purpose. It is the minimum vocabulary required for the Charles Fadel reader and the developer to have the same conversation about the same design decision. Larger vocabularies are available; the appendix is not in the business of producing them.

---

## E. Teaching considerations — what the appendix is for

The appendix is not a chapter. It does not have a hook, a deep-dive, or a synthesis. It is a reference instrument. Three teaching considerations:

1. **The appendix is a checking tool, not a reading tool.** A reader who has read the book in order will encounter every lexicon term at its first-appearance chapter, in context, with the full evidence base. The appendix is for the reader who comes back to the term later — to settle a disagreement, to remind themselves what the precise definition was, to confirm a cross-reference. The entries should be tight (2–4 sentences for the definition; longer for cross-references and source notes) and the chapter-and-section pointer should always be visible.

2. **The appendix is also a discoverability tool.** A reader who skims the book may encounter "the within-learner bandit" or "the fluency trap" without context. The appendix is where they can land long enough to recover the context before deciding whether to read the chapter. Each entry should answer the question *"is this term load-bearing enough that I need to read the chapter, or is the appendix definition enough for my purposes?"*

3. **The appendix is the test of whether the lexicon coheres.** If two entries contradict each other, the book has a problem. If an entry's definition cannot be stated in 2–4 sentences without referencing terms the appendix has not defined, the lexicon is too vocabulary-heavy. If the cross-references form a cycle the reader cannot escape, the lexicon is not a reference tool. The appendix should be reviewed for coherence, not just for accuracy.

The appendix author should resist the temptation to add entries. Thirteen is the right number — the TIKTOC's choice — and adding more dilutes the test. If a term feels essential and is not in the list, the appropriate move is to take it to Nik for the next revision, not to add it silently.

---

## F. Library files — what existing pantry covers

The lexicon's evidence base is distributed across the existing pantry. The appendix should cite by filename and not re-research:

- `pantry/Lexicon.txt` — the NanoLex / Wikipedia Pipeline specification (v0.2, March 2026, Lead: Thejus Thomson; Reviewers: Prof. Brown, Dhruv, Riya). Primary source for the Pipeline A (live on dev) and Pipeline B (publishable paper) framing referenced in §G below.
- `pantry/01-what-is-an-intelligent-textbook_notes.md` — Ch 1 research notes. Source for the IDK-IDK problem entry (§A.1) and the four-layer sketch first appearance (§A.2).
- `pantry/02-why-does-solving-it-require-a-platform.md` — earlier internal draft. Source for the seven-signals plain-English description.
- `pantry/04-the-four-layers_notes.md` — Ch 4 research notes. Source for the four-layer specification (§A.2) and the seven-signal enumeration in plain English (§A.4).
- `pantry/04-what-makes-this-different.md` — earlier internal draft. Source for the ensemble architecture sketch (§A.13 GLP).
- `pantry/05-the-measurement-layer_notes.md` — Ch 5 research notes. Source for the formal Y1–Y7 specification (§A.4), the ensemble architecture (§A.13 GLP), the neurobiological grounding (Schultz, Cowansage, Yang), and the fluency trap entry (§A.10).
- `pantry/05_what_doesnt_it_know_yet.md` — Ch 5 chapter brief (earlier draft). Source for the ambient infrastructure entry (§A.8).
- `pantry/06-the-four-modes_notes.md` — Ch 6 research notes. Source for the four modes entry (§A.3) and the phase gates entry (§A.5).
- `pantry/06-medhavy-conducting-ai.md` — Ch 3 chapter brief (the conducting-AI frame). Source for the conductor entry (§A.9), specifically the recommendation-engine-failure section, the spinach principle, and the "preferences tell the conductor which instrument to reach for; the score tells the conductor what needs to be played" framing.
- `pantry/07-the-adaptive-engine_notes.md` — Ch 7 research notes. Source for the within-learner bandit entry (§A.6) and the GLP reward signal entry (§A.7), specifically the casino-owner-watching-through-the-security-camera image.
- `pantry/09-the-content-layer_notes.md` — Ch 9 research notes. Source for the cost-collapse asymmetry entry (§A.11), the Level 1/2/3 domain-specificity framing, and the Sunstein burden-of-proof inversion.
- `pantry/quiz-me-habit-research.md` — habit-formation research note. Source for the due-today counter entry (§A.12), specifically the Zeigarnik effect, the Anki-vs-SuperMemo natural experiment, and the BJ Fogg / Hooked frameworks.
- `pantry/quiz-me-research.md` — Quiz Me evidence base. Source for FSRS specification and benchmarks referenced in §A.12.
- `pantry/ask-ai-research.md` — Ask AI evidence base. Source for Bastani et al. 2025 PNAS (§A.10 fluency trap and §A.7 GLP reward signal); Lee, Sarkar et al. 2025 CHI; VanLehn 2011; Kestin et al. 2025.
- `pantry/case-study-research.md` — Case Study evidence base. Source for Thistlethwaite 2012 BEME synthesis referenced in §A.3.
- `pantry/glimmer-research.md` and `pantry/glimmer-displacement-research.md` — Glimmer evidence base. Source for Jonassen 1997 / 2000, Atkinson-Renkl-Merrill 2003 backwards-faded scaffolding, Pea 2004 on scaffolding withdrawal.
- `pantry/concept-sequencing-research.md` — Source for BKT/DKT, Yudelson 2013 individualized BKT, prerequisite sequencing referenced in §A.6 (within-learner bandit) and §A.4 (Y2 error trajectory coherence).
- `pantry/domain-specific-instruction-research.md` — Source for Sadler 2013 PCK, Shulman 1986, Hill-Rowan-Ball 2005 referenced in §A.11 (cost-collapse asymmetry, specifically the misconception-targeted content carve-out).
- `pantry/educational-media-economics-research.md` — Source for the Sesame Street comparator ($5/child/year, *d* = 0.29), Mayer's CTML, the cost-collapse framing.
- `pantry/PEDAGOGY ARCHITECTURE.txt` — Medhavy-internal source for the four-modes rationale and the cold-start strategy referenced in §A.6.
- `pantry/MVAL.txt` and `pantry/medhavy-1.5-feature-roadmap-complete.md` — Medhavy-internal sources for the implementation status of each lexicon term (what is live in v1.5 vs. what is on the v2.0 roadmap).
- `pantry/12-the-design-conversation_notes.md` §6 — the source list of the thirteen terms the lexicon owns, with first-appearance pointers. This appendix note follows that list exactly.
- `pantry/_lib_reinforcement_learning_an_introduction.md` — Sutton & Barto. Source for the bandit formalization referenced in §A.6 and §A.7.
- `pantry/_lib_everything-is-predictable_-how-bayesian-statistics-explain-our-world.md` — Source for the Bayesian framing referenced in §A.6 (Thompson Sampling).

---

## G. Gaps and flags

### G.1 The NanoLex / Wikipedia Pipeline — Pipeline A and Pipeline B

The TIKTOC lists the NanoLex / Wikipedia Pipeline connection as a lexicon entry — specifically the distinction between **Pipeline A** (keyword pop-ups, live on dev, blocked only on the MDX component contract from Dhruv) and **Pipeline B** (lexical entry generation via fine-tuning, publishable as the paper *"Automated Lexical Entry Generation for Nanomedicine"*). The pantry source for this entry is `pantry/Lexicon.txt` (v0.2, dated March 2026, Lead: Thejus Thomson; Reviewers: Prof. Brown, Dhruv, Riya). The document specifies:

- **Pipeline A.** Wikipedia → Medhavi MDX. Stages: subwiki.py (parse Wikipedia XML by Biotechnology/Nanotechnology categories, output JSONL); keyword detector (scan Medhavi textbook content for matches); mdx_exporter.py (render matched keywords as MDX pop-up components — *blocked on Dhruv's MDX component contract decision*). Stage 1 complete; stage 3 blocked on Decision 1. The pop-up displays at minimum: term name, short definition (first sentence of Wikipedia article or NanoLex main definition), source URL, optionally an image.

- **Pipeline B.** NanoLex → fine-tuned model. Stages: training corpus (~1,000 NanoLex entries with Classification, Synonymy, Hypernymy, Hyponymy, Meronymy, Part Holonyms, Verb Relations, Antonymy, Relational Adjectives, Expanded Definition); system prompt (draft framing the fine-tuned model as a domain lexicographer — pending Prof. Brown approval); SFT run (Llama 3 8B preferred; Mistral 7B fallback; on Northeastern Discovery cluster); entry extension (run the fine-tuned model on the Wikipedia corpus for terms without an existing NanoLex entry). Stage 1 ready; stages 2–4 pending Decision 2. Validation: 10% holdout (100 entries) scored against the NanoLex schema — all eight sections present, no hallucinated synonyms, correct ontological relationships, expanded definition tied to actual biomedical application context.

**Why the entry matters in the Medhavy lexicon.** The NanoLex pipeline is the operational evidence that *the lexicon layer itself can be an AI-generated artifact*. Pipeline B fine-tunes a model on the human-curated ~1,000 NanoLex entries; the fine-tuned model extends the vocabulary into Wikipedia nanomedicine terms not yet in NanoLex. This is the same architectural move the Medhavy platform makes at the content layer (Ch 9): cost-collapse for production where the failure mode is small and reversible; expert authorship retained where the failure mode is large or persistent. The NanoLex pipeline is the reflexive instance — the platform's own lexicon being generated by the architecture the platform argues for.

**Verification flags for the NanoLex entry:**

- The paper *"Automated Lexical Entry Generation for Nanomedicine"* is described in `Lexicon.txt` as the publishable Pipeline B output. **A web search (2026-05-17) on the exact title returned no published or preprint version**; the paper appears not to be public yet. Adjacent published work — *NanoSafari* (a generative AI copilot for biomedical nanoengineering, ACS Nano 2025); *NANOGPT* (a query-driven RAG system for nanotechnology research, arXiv:2502.20541); the *Landscape of Nanomedical Clinical Trials* (Gultepe, Valluru, Brown, Sridhar 2026, *Nano Today*) — exists but is not the same artifact. **The appendix should flag that the *Automated Lexical Entry Generation for Nanomedicine* citation is a forthcoming artifact, not a published one, and should not be linked as if it were public.** The Medhavy book may need to delay the citation or describe the work in the present tense ("a paper currently in preparation describes...") rather than past tense.

- The **Northeastern Nanomedicine Innovation Center** (`nanomedicine.sites.northeastern.edu`) is the institutional home for NanoLex. The appendix can cite the center as the institutional context without claiming the pipeline is public-facing.

- The **NanoLex schema** (Classification, Synonymy, Hypernymy, Hyponymy, Meronymy, Part Holonyms, Verb Relations, Antonymy, Relational Adjectives, Expanded Definition with application context) is documented in `Lexicon.txt` §5. The appendix can describe the schema at this level of detail; deeper technical specification belongs in the implementation book, not in this textbook's appendix.

- The **MDX component contract** is named as a pending decision (Dhruv to confirm by selecting Option A — term reference only / Option B — inline props / Option C — child content block). The appendix should not commit to one option; the implementation is moving and the book is not the place to resolve a still-open engineering decision.

**Recommendation for the appendix author.** Treat the NanoLex entry as a *two-part* entry: (1) Pipeline A — keyword pop-ups, live on dev, mechanism documented in `Lexicon.txt`; (2) Pipeline B — lexical entry generation via fine-tuning, paper in preparation, **flagged `[verify: paper title and publication venue when public]`**. The entry should make the reflexive point — the platform's own lexicon is an instance of the cost-collapse asymmetry the book argues for — without overclaiming the paper's status.

### G.2 The GLP preprint as a finished document

The Y1–Y7 specification used throughout the appendix is reconstructed from `pantry/02-why-does-solving-it-require-a-platform.md` (plain-English version) and `pantry/04-what-makes-this-different.md` (seven-component listing with ensemble-architecture framing). **The GLP preprint as a standalone, formal, citation-ready document does not appear in the pantry.** Both the Ch 4 and Ch 5 research notes flag this. The appendix's GLP entry (§A.13) and seven-signals entry (§A.4) both depend on this specification being canonical. If Nik intends to publish the GLP preprint separately, the appendix can cite it; if not, the appendix is the first formal statement of the framework in citable form, and that should be acknowledged.

**Flag for Nik.** Confirm whether (a) the GLP preprint exists elsewhere in your files and should be added to the pantry, (b) the preprint is in preparation and should be cited as forthcoming, or (c) the textbook chapter (Ch 5) is the canonical statement of the Y1–Y7 framework, in which case the appendix's GLP entry should explicitly say "first specified in Chapter 5 of this book" rather than citing an external preprint.

### G.3 Neurobiology citations

The three citations in the GLP entry (§A.13) — Schultz 1997, Cowansage 2010, Yang Pan & Gan 2009 — all carry `[verify]` flags in the Ch 5 research notes:

- **Schultz 1997.** *Science* 275(5306): 1593–1599. Multiple Schultz papers in this period; confirm the 1997 review-style paper, not the earlier primary findings. Translation from macaque dopamine to human classroom learning is consistent with broader literature but is a translation, not a direct extrapolation.
- **Cowansage 2010.** *Current Molecular Pharmacology* 3(1): 12–29. The TIKTOC specifies this citation; Lu, Christian & Lu 2008 in *Nature Reviews Neuroscience* (BDNF and synaptic plasticity, learning, and memory) may be the more canonical synaptic-consolidation review and should be cross-cited.
- **Yang, Pan & Gan 2009.** *Nature* 462(7275): 920–924. Mouse motor learning; the extrapolation to human declarative learning is supported by the broader literature (Bailey, Kandel & Harris 2015; Holtmaat & Svoboda 2009) but the specific extrapolation should be flagged in the appendix entry, not asserted.

**Recommendation.** The appendix should cite the three papers (with `[verify]` flags propagated from the Ch 5 notes), one cross-reference per paper to a more general review, and one sentence acknowledging the animal-to-human translation. The neurobiology grounds the *plausibility* of behaviorally traceable learning; it does not assert a one-to-one mapping.

### G.4 The DiCerbo "IDK IDK" quote attribution

The IDK-IDK entry (§A.1) leans on the Kristen DiCerbo (Khan Academy CAO) quote *"I will tell you, we see more 'IDK IDK,' more passive kinds of interaction than we would like."* The Ch 1 research notes flag this:

- The quote is widely reported and consistent across multiple secondary sources (Dan Meyer Substack, itutorsoft, CompleteAI Training, Common Sense Media).
- The primary venue appears to be an interview or panel discussion — likely an EdSurge or Education Next interview circa 2024–2025.
- **Verify the exact primary venue and date before the appendix attributes the quote**, especially because the appendix is a permanent reference document.

**Recommendation.** Attribute by title as well as name ("Khan Academy's Chief Academic Officer Kristen DiCerbo, in a [verify venue] interview, circa [verify date]"). The quote itself is the operational citation; the institutional acknowledgment is what makes it load-bearing.

### G.5 The Robert C. Gray bandit-explanation-style reference

The Ch 7 research notes flag a TIKTOC reference to *"Robert C. Gray multi-armed bandit explanation style — slot machines first, technical vocabulary second."* The Ch 7 notes searched and could not find a canonical Robert C. Gray bandit explanation in the literature or the pantry. The appendix's within-learner bandit entry (§A.6) does not require this attribution — the slot-machines-first move can be sourced to Sutton & Barto Ch 2 directly without naming Gray. If Nik can confirm the Gray reference is canonical, the appendix can cite it; if not, the appendix should follow the Ch 7 recommendation and adopt the style without citing the unverifiable author.

### G.6 "Medhavy" naming consistency

Throughout the pantry, the platform is spelled both **Medhavy** and **Medhavi** (e.g., `Lexicon.txt` uses "Medhavi" in its title and "Medhavi textbook page" / "Medhavi MDX layer" in body text; the book uses "Medhavy" throughout). The appendix should pick one spelling and use it consistently. **Recommendation:** "Medhavy" matches the book slug (`books/medhavy/`) and is the form Nik uses in the textbook drafts; the appendix should follow this convention and treat "Medhavi" in `Lexicon.txt` as an artifact of the internal-document drafting history. The appendix can note the variation parenthetically in the entry for the platform name if helpful, but should not introduce a separate lexicon entry for the spelling variant.

### G.7 The thirteen-entry count

The TIKTOC names thirteen terms; this note treats them as thirteen entries. The §A counting yields entries A.1 through A.13 — thirteen entries. **Note that "the four layers" and "the four modes" are each *one* entry (not four), per the TIKTOC's framing.** The appendix should follow this convention. If the appendix author finds a fourteenth term essential (the NanoLex / Wikipedia Pipeline entry is a candidate for promotion from the §G flag to a fourteenth A entry, if Nik wants the pipeline named in the lexicon rather than only flagged), the appropriate move is to take the proposal to Nik before adding it.

### G.8 Cross-reference cycle check

The lexicon's cross-references should not form impossible cycles (entry A defined by entry B defined by entry A). The appendix author should run a cycle check before publication. Suspicious cases to watch:

- *Genuine Learning Probability* and *the seven signals* are tightly coupled; the appendix should let GLP cite the seven signals as components without circularly defining either. The seven signals entry defines each Y-component; the GLP entry names the composite. The asymmetry is correct.
- *The within-learner bandit* and *the GLP reward signal* are coupled; the bandit consumes the reward, the reward is produced by the measurement layer. The two entries can reference each other without cycling because the third party (the measurement layer / the seven signals) breaks the apparent loop.
- *The conductor* references the within-learner bandit (the conductor *is* the bandit, framed as an experimenter). The conductor entry should not duplicate the within-learner bandit specification; it should be the metaphor entry, cross-referenced to the formal entry.

---

*End of appendix research notes. Approx. 5,200 words. For Appendix A author use. The thirteen entries above are the operational specification of the Medhavy vocabulary; the appendix's job is to render them as a coherent, alphabetized, cross-referenced reference instrument. Two flags for Nik are top-priority: (1) the NanoLex Pipeline B paper status (§G.1); (2) the GLP preprint document status (§G.2).*
