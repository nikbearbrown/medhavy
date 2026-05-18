# Chapter 5 — The Four Layers

**Suggested titles**
1. The Four Layers
2. Why You Can't Buy the Pieces Separately
3. The Bolt-On Failure: A Procurement Story

**TL;DR.** The reasonable answer to "why a platform?" is "buy the parts and connect them." This chapter shows why that answer fails — not for tooling reasons, but because the seven signals an intelligent textbook must read are *byproducts of specific interaction designs*, and you cannot extract from an instrument the signal it was never measuring. The four layers — Book Library, Curriculum Design, Adaptive Engine, Measurement — only work as a closed loop. The seams are where signal is lost.

---

## Learning objectives

By the end of this chapter you should be able to:

1. **(Understand)** Describe the function of each of the four layers and explain what each layer cannot do without the others.
2. **(Analyze)** Explain why bolt-on tools cannot produce the integrated signal an intelligent textbook requires — and name the specific signal lost at each seam.
3. **(Apply)** Map a specific learning problem to the four layers, identifying what each layer needs to do and what data it exchanges.
4. **(Evaluate)** Assess an existing platform's architecture against the four-layer model and identify which layer is the binding constraint.

**Prerequisites.** Chapters 1–3. You need the IDK-IDK failure (Ch 1), the complexity threshold test (Ch 2), and the evidence base (Ch 3). This chapter opens Act Two — the architecture.

---

## Where this fits the conductor frame

This chapter primarily serves the organization — the third of the three questions, in order. The procurement officer's question — *why not just buy the parts?* — is the institutional question this chapter answers. The learner and the instructor are present, because the seven signals the architecture is built to read are signals about what the learner is doing and what the instructor's design produced. But the audience the chapter is most directly arguing with is the one writing the check.

What this chapter specifies for the conductor is the instrument set — the four layers — she reaches for when the simpler arrangements of Chapter 3 will not generate the evidence the experiment requires. The conductor is not the architecture; the architecture is one set of instruments. The chapter is naming the conditions under which those particular instruments earn their cost: when the seven signals must be read as a loop, and the seams of a bolt-on stack would lose the signal the conductor needs to decide.

The chapter runs the experiment by making the loop itself the falsifiable claim. If a bolt-on stack could produce the seven signals at the granularity the conductor needs, the four-layer architecture would be the wrong instrument. The chapter commits, in the open, to the position that it cannot — and invites the reader to audit each signal's irreducibility. Transparency about the architecture's load-bearing assumption is the precondition for trusting the architecture at all.

---

## 1. The reasonable objection

A reader I respect — call him a Charles Fadel type, because the type really is named after Charles Fadel — has just finished Chapter 3. He has the evidence base. He has watched me argue that EdTech has been failing in both directions, and he is convinced enough to want to do something about it. So he asks the procurement question:

*"I could buy an LMS. I could license a chatbot. I could license a spaced repetition tool. I could buy a case study library. I could hire a developer for two months to connect them. Why do I need a platform?"*

This is the right question. It is not naive. **The bolt-on stack is what most institutions actually build**, and the institutions that build it are not making an obviously wrong choice. They have budget. They have IT staff. They have working procurement relationships with established vendors. The cost of buying four tools and stitching them together is, on paper, a fraction of the cost of building a new platform from scratch. The risk profile is lower. The change-management story is easier. The board approves it.

I want to take the question seriously before I answer it. The answer is not "the platform is better because it is integrated." That is the kind of sentence a brochure writes. The answer is structural: there is a class of signal an intelligent textbook *must* read in order to do its job, and that class of signal is not extractable from the data streams the bolt-on tools produce. **You cannot extract from an instrument the signal it was never measuring.** This is the chapter's central claim, and the rest of it is the argument for why that sentence is true.

The argument runs in two stages. First, the seven signals — what they are, what interaction design has to exist to produce them, what bolt-on tools cannot recover. Then the four layers, which are the architectural response to the signal requirements. The point at the end is the loop, not the layers. The layers individually are not novel. The loop is.

---

## 2. The seven signals — and what bolt-on cannot recover

Here is the operational form of the argument. For each signal, what it measures, what interaction design produces it, and what an LMS-plus-chatbot-plus-quiz-tool stack cannot do.

**Signal 1 — Temporal engagement pattern.** Where the student's time actually goes across the difficulty surface of a concept. A student who is genuinely engaged spends longer on the moves that are hard for them, shorter on the moves that are already automatic. A student who is borrowing certainty spends time in proportion to how much output they need to produce, not in proportion to where the work was hard. The data the system needs is timestamped attention at sub-paragraph granularity — which paragraph the cursor was on, for how long, whether attention came back after the next paragraph.

What bolt-on cannot do. Canvas logs page views at the page level. A page view of twelve minutes tells you nothing about whether the student spent eleven minutes on the hard paragraph or eleven minutes idle with the page open. The granularity is wrong. The Canvas API was not designed to produce this resolution; Canvas's purpose is course administration, not engagement instrumentation.

**Signal 2 — Error trajectory coherence.** The shape of a student's wrong answers across a sequence of attempts. A real misconception produces coherent errors — question 1 wrong in a way that implicates the same missing component as question 2's error, and question 3 right when the component is repaired. Random wrong answers across question types indicate no underlying model developing. The student is guessing, not building.

What bolt-on cannot do. A separate quiz tool stores grades or pass/fail. The trajectory across a sequence — the actual responses, the misconception tag on each error, the relationship between item 1 and item 3 — either is not stored or is stored in a format that requires a separate analytical layer to extract. Even with the data, the analytical move ("is this error sequence consistent with a known misconception?") requires a misconception model the quiz tool does not have. That model lives in the curriculum design layer (Section 4 below). Without it, error trajectory coherence is uncomputable.

**Signal 3 — Cross-context transfer.** Whether the student applies the concept in a context the instruction did not directly cue. The Bjorkian operational definition of learning: a concept the student "has" is one they can use outside the cue conditions in which they encountered it.

What bolt-on cannot do. Most assessments are within-context — they test the concept in the same kind of problem the instruction used. Cross-context transfer requires *deliberately divergent* problems, sequenced so the student does not recognize that the second problem is "the same concept." A Canvas quiz built by a professor who already knows the concept will tend to present recognizable variants. A platform that gates on transfer has to *generate or curate* the divergent context as a design move, not inherit it from existing question banks.

**Signal 4 — Uncertainty calibration.** The gap between what the student knows and what the student thinks they know. A well-calibrated student is confident on what they are right about, uncertain on what they are wrong about. A miscalibrated student is confident regardless of accuracy. The data requirement is specific: confidence rating elicited *before* the answer is revealed, paired with the accuracy, aggregated into a calibration curve.

What bolt-on cannot do. Pre-response confidence elicitation is a specific interaction design. Canvas quizzes default to "submit answer, see correctness." Even if Canvas is configured to elicit confidence, the calibration data lives in Canvas and is not cross-referenced with the other six signals. Calibration in isolation is informative; calibration as one input to a composite score requires the same system to hold all seven signals.

**Signal 5 — Social knowledge texture.** The signature of authentic encounter with material in the texture of the student's questions and positions. Specific confusions ("why does the reaction go this direction and not the other?" rather than "I don't understand this section"). Genuine surprise when a result resolves differently from expectation. Position changes that track developing understanding rather than authority signals.

What bolt-on cannot do. This is the signal a bolted-on chatbot most obviously misses, because the chatbot's logs live outside the system that tracks the rest of the student's session. A general-purpose chatbot answers the question and forgets it. The *texture* across the student's interactions over a week — the pattern of how their questions changed as they engaged with the material — exists only if the same system that holds the questions also holds the positions and the assessment trajectory.

**Signal 6 — Retrieval strength decay signature.** The rate at which performance on a tested concept decays in the days after the test. A student with storage strength shows slow decay; a student with retrieval strength only — the student who peaked at the test — shows fast decay because there was no consolidation underneath the performance.

What bolt-on cannot do. This is the most direct argument against any platform that advances on the immediate post-test result. The decay signature requires the platform to come back, on a schedule *it chose*, with the concept the student tested on weeks earlier — and to be the same platform, with the same record of what the student knew then, so the delta can be computed. A spaced repetition tool can do its version of this for the items in its deck, but cannot do it for the concepts the case study tool or the chatbot were meant to teach.

**Signal 7 — Scaffolding response curve.** The performance gain from a partial structural hint. A student with genuine partial understanding has a zone of proximal development — a small activation produces nearly the gain a full explanation would. A student who borrowed the structure has no ZPD; the hint produces no improvement because there is nothing to activate.

What bolt-on cannot do. The signal is the *delta* — performance before the hint, performance after — and that delta is only computable if the system logs the cognitive state on both sides of the hint. Chatbots that give the answer collapse the distinction entirely. Chatbots that give hints (Bastani's GPT-Tutor variant, some Khanmigo configurations) log the response but not the cognitive state the student was in when they received it. The state is the measurement.

### Why this is a structural argument, not a vendor complaint

The point is not that Canvas is bad or that Anki is bad. Canvas is excellent at course administration. Anki is excellent at spaced retrieval for items in a deck. **The argument is that the seven signals are byproducts of specific interaction designs**, and the interaction designs that produce those byproducts are not the interaction designs Canvas or Anki or your favorite chatbot was built around. Canvas was built to deliver assignments. Anki was built to schedule cards. A standalone chatbot was built to answer questions. None of them was built to produce the seven signals, because none of them was built to be the substrate of a learning system that needed to read those signals.

You cannot extract from an instrument the signal it was never measuring. The measurement infrastructure and the learning infrastructure must be the same system, because the measurements only exist as byproducts of the interaction designs that produce the learning. Pull them apart and you have a learning system that produces no evidence and a measurement system that has no learning to measure.

That is the bolt-on failure. The four layers are the response.

---

## 3. Layer 1 — Book Library

The Book Library is the textbook in its multiple incarnations. Each base book in the library is structured around the concept node map that Layer 2 (next section) produces, and each base book has multiple framings: Prompt Engineering for Art and Design students, Organic Chemistry for pre-med, Algorithms for non-CS majors. Same concept graph, different voice, different worked examples, different motivational frame.

The argument the Book Library makes against the bolt-on alternative is the *domain specificity* finding. Sadler and colleagues (Sadler, Sonnert, Coyle, Cook-Smith & Miller 2013, [*American Educational Research Journal* 50(5): 1020–1049](https://journals.sagepub.com/doi/10.3102/0002831213477680)) showed that teachers who could identify the common student misconceptions in their specific domain produced substantially larger gains than teachers who could not, controlling for content knowledge. **The content the bandit chooses among must be content that is calibrated to the specific misconceptions students bring to the specific domain.** Generic content cannot do this. Cost-collapse AI-generated content can begin to do it, but only if the faculty review gate verifies that the misconception calibration is right (Chapter 9 develops this).

This is what bolt-on inherits instead. The institution licenses a textbook. The textbook is a single framing, written for a generic student, calibrated to misconceptions the publisher's editorial board imagined rather than the misconceptions a particular cohort actually brings. The chatbot answers from the textbook plus the public internet. The spaced repetition deck contains items the publisher (or a teaching assistant) wrote for the textbook. The case study library contains cases the publisher curated. None of these is wrong; they are simply uncoordinated, and the coordination is what would have to exist for the next layer to choose among framings rather than choose among accidents.

The forward pointer to Chapter 10: Level-3 (domain-specific) content costs roughly 1.5× to 2× what Level-1 (generic) content costs to produce, but produces reliably larger gains on near-transfer and on motivation. The economics chapter argues that AI flips this calculus — and that the binding cost shifts from content authorship to faculty review.

---

## 4. Layer 2 — Curriculum Design (Tic TOC as instrument)

The curriculum design layer is upstream of every other layer. It produces the concept node map — the prerequisite graph, the outcomes specified at Bloom's-level granularity, the phase gate logic, the mode appropriateness flags — that the adaptive engine reads.

Tic TOC is the instrument: a structured intake conversation with the domain expert that converts their expertise into a specification a downstream layer can act on. The output is three artifacts (Kindle book, Medhavy course, Canvas course) from one design session, but the load-bearing output is the concept map. **The map is what the engine adapts within.** Without it, the adaptive engine is choosing among modes on an unstructured concept space.

The argument against the bolt-on alternative is structural: prior platforms inherited course structure from the professor's existing syllabus. Inheriting a syllabus inherits its pedagogical gaps — the prerequisite assumption that was never made explicit, the Bloom's-level ambiguity ("students will understand X" versus "students will calculate Y given Z"), the assessment that did not align with the stated outcome. The bandit then adapts within a structurally broken concept space and produces adaptation that is technically correct and pedagogically incoherent.

I'll forward-point to Chapter 8, where this becomes the "suggest 15 chapters" failure mode. The short version: if you ask an LLM to design a course, you get fifteen chapters whose ordering looks reasonable until you check whether each chapter's prerequisites are actually established by the chapters above it. They usually aren't. Backward design (Wiggins & McTighe — see McTighe & Silver, *Teaching for Deeper Learning* [verify edition], in `pantry/_lib_teaching-for-deeper-learning_...md`) is the discipline that prevents this; Tic TOC is the operational form of backward design.

---

## 5. Layer 3 — Adaptive Engine

The adaptive engine is what most people mean by "the AI." It is the layer that selects, for *this learner on this concept at this point in time*, which of the four modes (Ask AI, Case Study, Quiz Me, Glimmer — Chapter 6 unpacks each) to offer next. The selection is a *within-learner contextual bandit*: each learner is their own experiment, and the engine's reward signal updates per learner per concept per session.

I'll give you the slot-machine version once and then promise it as Chapter 7's job. A contextual bandit is what you get when you have several arms to pull (the modes), each arm gives you a reward of variable quality, and the reward you get depends on *context* — the learner's history, the concept's prerequisites, the time since their last session, their prior calibration scores. The engine learns, per learner, which arm to pull when. The math sits in Chapter 7, the formalization sits in Appendix D, and the canonical reference for those who want it is [Sutton & Barto, *Reinforcement Learning: An Introduction*, 2nd ed., Ch 2](http://incompleteideas.net/book/the-book-2nd.html).

The argument against the bolt-on alternative has two parts. First, most adaptive platforms use *cross-learner* generalization — they learn from one cohort which approaches work, then apply those approaches to the next cohort. Cross-learner generalization requires the assumption that learners are similar enough that what worked for cohort A will work for cohort B. **The within-learner design refuses that assumption.** It is the design choice consistent with the intelligence-is-not-one-thing argument from Chapter 1. The cost is convergence time — within-learner bandits need more sessions per learner before the policy is informative. The benefit is that they don't average over learners whose actual learning paths are different in kind, not just in degree.

Second — and this is the seam between Layer 3 and Layer 4 — the bandit needs a *reward signal* to learn from. If the reward is engagement, the bandit will optimize for engagement, which is the IDK-IDK failure restated as a control-theory problem. The reward has to be evidence of genuine learning. That evidence is what Layer 4 produces. Without Layer 4, Layer 3 is a hammer.

---

## 6. Layer 4 — Measurement Layer (GLP framework)

The measurement layer is the seven signals from Section 2, *formalized* as the GLP framework with seven components (Y1–Y7) and an ensemble architecture that combines them. Chapter 5 develops it in full; here I introduce it as the layer that closes the loop.

The full specification is Chapter 5's job. For Chapter 4 the point is the architectural role. The measurement layer is the input to Layer 3's reward signal. It tells the engine whether the mode it selected produced learning, not just whether the student stayed on the page. The components themselves — temporal engagement pattern, error trajectory coherence, cross-context transfer, uncertainty calibration, social knowledge texture, retrieval strength decay signature, scaffolding response curve — are the formal versions of the seven signals enumerated above. Same content, different resolution. Chapter 5 specifies how each one is computed, why seven and not one, and how the composite is built.

For Chapter 4: the measurement layer is what makes the engine optimize for learning rather than for engagement. **Without Layer 4, Layer 3 is optimizing on proxies, and the IDK-IDK failure is restated at architectural granularity.** With Layer 4 but without Layers 1–3, Layer 4 has nothing to measure, because the system has no learning infrastructure to instrument. The four layers cohere only as a loop.

---

## 7. The integration — the loop is the architecture

Here is the central move of the chapter, and the place I have to be careful, because it sounds like a brochure sentence and isn't.

**The four boxes drawn separately are a stack. The four boxes drawn with the feedback arrow from Layer 4 back to Layer 3 are a system.**

What the loop produces that the layers individually cannot:

1. **The bandit knows what it is adapting within.** A bandit that selects among modes without a concept map is choosing on a topology it does not understand. With the map, the bandit knows which prerequisites a concept depends on, and can route to remediation before adapting on the surface concept.

2. **The content layer knows what the engine asked for.** Multiple framings of a concept are useful only if the engine can specify *which framing* is appropriate for *which learner*. Without the alignment between framings and the concept map, the library is a set of textbooks rather than the operational raw material the engine can choose among.

3. **The measurement layer measures the right thing.** A general "is the student learning?" question is unanswerable. A specific "is the student learning *this concept* under *this mode* with *this content framing*?" question is answerable, because the question has handles. The handles come from Layers 1–3.

4. **The reward signal updates a policy that has structure.** A bandit that updates a flat policy over modes is operating on the wrong granularity. The policy that gets updated is (mode × concept × time × context). The structure comes from the concept map and the content library.

I'll name the comparison directly because it is the place the argument earns its keep. Knewton, launched 2008, valued at hundreds of millions of dollars, acquired by Wiley in 2019 for a fraction of that valuation: item response theory selecting questions from a publisher's content bank. That is one part of Layer 3, with no Layer 1 in the sense I'm describing (the content was inherited from the publisher), no Layer 2 (the curriculum was inherited from the course), and no Layer 4 (the reward signal was test performance, not learning evidence). DreamBox: adaptive mathematics practice that produces real but modest effects (roughly 0.10–0.15 SD on standardized measures `[verify exact effect-size range against current DreamBox evaluation literature]`). A version of Layer 3 in a narrow domain. No multi-framing library. No GLP-style measurement. Khanmigo: a version of Ask AI — part of Layer 3 — without the concept node map, without the multi-framing content library, without the GLP measurement. The IDK-IDK incident from Chapter 1 is the structural consequence.

**Every prior platform optimized within one layer.** What I am claiming is novel about the four-layer architecture is not any individual layer. Knewton had a version of Layer 3. DreamBox has a version of Layer 3. Khanmigo has a version of one mode within Layer 3. The thing that is missing across all three is the closed loop — the architecture in which each layer's output is the next layer's input, and the measurement updates the selection policy.

The closed loop is not a feature of the architecture. It is the architecture.

---

## 8. Worked example — one student session

*(Illustrative case — composite, not a single deployed student. Labeled as such per workshop conventions.)*

A medical student — call her S — working through an oncology concept in Medhavy's cancer textbook deployment. The concept: the mechanism of action of immune checkpoint inhibitors.

**Session start.** S opens the chapter. Layer 1 delivers the medical-school framing of the concept, with worked examples drawn from clinical scenarios rather than from undergraduate immunology problem sets. Layer 2 has already specified the prerequisite map: S must have demonstrated understanding of T-cell receptor signaling and tumor antigen presentation before this concept becomes appropriate. The system checks S's profile. Both prerequisites are flagged as "demonstrated, decay < 14 days." The concept is unlocked.

**Mode selection.** Layer 3 receives the context. S has high prior GLP scores on mechanism-style questions, low confidence on quantitative pharmacology, and her last session was Quiz Me on the prerequisite concepts. The bandit selects Ask AI as the entry mode — the historical reward signal favors Ask AI for this learner on mechanism-style content. (Chapter 7 unpacks why.)

**Interaction.** S asks: *"Why does PD-1 blockade work in some tumors and not others?"* Ask AI is context-anchored — the model knows S is in the immune checkpoint section, knows what the prerequisite section on T-cell exhaustion said, knows S has not yet seen the tumor mutational burden material. Hint-not-answer guardrail. The response is a question, not the answer: *"What did you observe about T-cell exhaustion in the prerequisite section that might be relevant here?"* S replies. The system logs the reply, and several things happen in parallel.

**Measurement update.** Layer 4 processes the interaction. *Y1 (temporal engagement)* — S spent four minutes on the question, consistent with the difficulty norm for this concept. *Y2 (error trajectory)* — her response contains a recognizable misconception (she confused exhaustion with anergy, a known confusion that the curriculum design layer flagged), so the system tags this as a remediation opportunity. *Y4 (uncertainty calibration)* — S rated her confidence at 60% before answering; her answer was partially correct, so calibration is good. *Y5 (social knowledge texture)* — the question is specific to the mechanism, not a generic "I don't understand." The composite GLP score is updated.

**Policy update.** Layer 3 receives the measurement update. The reward signal for (Ask AI × immune checkpoint inhibitors × this learner) is positive but not maximal — the partial misconception means the representation is forming, not formed. The bandit notes that the next session on this concept should probably include a Quiz Me phase to convert the partial understanding into storage strength, and queues the retrieval interval per the FSRS-style scheduler (Chapter 6 explains FSRS).

**What an LMS-plus-standalone-chatbot deployment would have produced.** A Canvas page view of four minutes. A chatbot conversation log stored separately, with no link to the concept map, no misconception tag, no uncertainty calibration. No update to anything. The next time S returns to the platform, the system has no record of what she understood or what she confused. The signals existed in the session. The instrument did not measure them.

This is the first time in the book that all four layers are operating simultaneously on a single interaction. The contrast with the bolt-on alternative is what carries the argument: not "the platform is better" but "the platform measures the things the architecture commits the engine to optimize on, and the alternative does not."

---

## 9. Common misconceptions

**"The four layers are just an LMS, a chatbot, a quiz tool, and an analytics dashboard."**
*Why it fails.* It sounds right and is wrong on the seams. An LMS is roughly Layer 1 minus the multi-framing and minus the concept map. A chatbot is roughly one mode within Layer 3 minus the context-anchoring and minus the prerequisites graph. A quiz tool is roughly one mode within Layer 3 minus the FSRS-scheduled retest and minus the misconception model. An analytics dashboard is roughly Layer 4 minus the seven signals and minus the ensemble. The components rhyme. The seams between them — the data the next layer needs from this layer — are absent. The seams are the architecture; the components are not.

**"With enough integration work, you can recover the same signals from off-the-shelf tools."**
*Why it fails.* You can recover *some* signals partially. Y1 (temporal engagement) can be approximated from Canvas page-view logs at the page level, with a meaningful loss of resolution. Y6 (retrieval decay) can be partially recovered if a spaced repetition tool happens to cover the same items the case study tool tested. The rest of the signals require interaction designs the off-the-shelf tools do not implement — pre-response confidence elicitation, hint-not-answer guardrails with state logging, deliberately divergent cross-context items. Integration work moves data around. It does not produce the data the interaction designs were never built to produce.

**"The four-layer architecture is a specific Medhavy thing. It would not generalize."**
*Why it fails.* The four layers are not Medhavy-specific. They are the architectural response to the seven-signal requirement. Any platform that wants to optimize on learning evidence rather than engagement proxies will end up needing something that does Layer 1's job (provide multi-framing content aligned to a concept map), something that does Layer 2's job (produce the concept map), something that does Layer 3's job (select among interaction modes per learner per concept), and something that does Layer 4's job (measure learning evidence). What is Medhavy-specific is the particular choice of modes, the particular GLP framework, the particular bandit design. The four-layer skeleton is the field's, not Medhavy's.

---

## 10. Exercises

**4.1 — (Apply.)** Choose a learning problem you understand well — undergraduate organic chemistry, residency-level differential diagnosis, freshman calculus, your own domain. Specify what each layer must *produce* and what each layer must *receive* from the layer upstream of it. Draw the four boxes and the arrows between them, including the feedback arrow from Layer 4 to Layer 3. *(Produces something — required by chapter anatomy.)*

**4.2 — (Analyze.)** A platform uses an institutional LMS for content delivery, a third-party general-purpose chatbot for student questions, and a separate spaced repetition tool for retrieval practice. For each of the seven signals, identify whether it is *partially recoverable*, *unrecoverable*, or *recoverable but unlinked* in this architecture. Where it is recoverable but unlinked, explain why "with enough integration work" does not solve the problem.

**4.3 — (Evaluate.)** Reread the Khanmigo IDK-IDK incident from Chapter 1. Using the four-layer model, identify which layer was the binding constraint — that is, the layer whose absence or weakness produced the failure that the other three layers' presence could not compensate for. Then specify, in one paragraph, what would have to be added to the deployment to prevent the IDK-IDK outcome.

---

## What would change my mind

If a bolt-on deployment — an institutional LMS plus a general-purpose chatbot plus a spaced repetition tool plus a case study library, connected by a custom integration layer — produced GLP-equivalent measurements (all seven signals, ensemble-combined) on a per-concept per-learner basis with fidelity comparable to a purpose-built integrated platform, the structural argument in this chapter would be wrong. The seams would be bridgeable. I have not seen this and I do not expect it on technical grounds, but it is the empirical finding that would force a rewrite.

## Still puzzling

1. Where exactly is the boundary between "layers as architecture" and "layers as label"? Knewton arguably had partial versions of three layers. Why is the fourth missing layer (Y4-Y7-style measurement) structurally consequential while Knewton's missing Layer 2 was apparently survivable in the markets they served?
2. If a bolt-on integration layer were built around an *open* concept-graph standard — every off-the-shelf tool publishing to and reading from a shared knowledge graph — how much of the four-layer integration could be approximated? Is the binding constraint architectural or interface-standard-related?
3. The four-layer model is described in the context of a single course on a single platform. What happens when a student takes three courses on three different Medhavy deployments? Is the measurement layer per-deployment, per-student, or some federation we have not specified?
4. The within-learner bandit (Layer 3) needs many sessions per learner to converge. For a short course (8 weeks, two sessions per week), does the engine ever accumulate enough signal to outperform a well-designed cross-learner default? This is the cold-start problem and it is one of Chapter 11's open questions.

## Bridge to Chapter 5

Measurement determines what every other layer can learn. The bandit can only optimize on a reward signal that has been formally specified; the content library is only choosable-among if the engine can read what learning evidence the framings produced; the curriculum design layer is only validatable if the system can detect whether the prerequisite structure actually produced the gains the design predicted. **Chapter 5 specifies the measurement layer first**, because understanding it is prerequisite to understanding why mode design and engine design take the shape they do. It is the load-bearing chapter of Act Two.

---

**Tags:** four-layer architecture · bolt-on failure · seven signals · within-learner bandit · GLP measurement · Knewton · Khanmigo · DreamBox · concept node map · Tic TOC
