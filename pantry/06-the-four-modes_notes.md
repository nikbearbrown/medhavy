# Research Notes — Chapter 6: The Four Modes

*Pantry note for Chapter 6, which specifies the four modes — Ask AI, Case Study, Quiz Me, Glimmer — as the arms of the adaptive engine and the phase gates that prevent each mode's characteristic failure.*

*Compiled 2026-05-17. Sequential to the Ch 4 (Four Layers) and Ch 5 (Measurement Layer) notes. This chapter is application-level: it shows the modes operating against the architecture Chs 4–5 specified. The phase-gate logic uses the GLP signals (Y1–Y7) from Ch 5 as gating criteria.*

---

## A. The hammer problem at mode level

The Ch 6 opening is the hammer problem restated at the mode level. The single-mode platforms each produce their characteristic failure when their one mode is the only available move:

- **Ask AI for everything → the Bastani GPT-Base outcome.** Unguarded conversational AI during practice produces apparent fluency that does not transfer to skill in the AI's absence. Bastani et al. 2025 ([PNAS](https://www.pnas.org/doi/10.1073/pnas.2422633122)) measured this directly: 48% performance lift during practice with unguarded GPT-4, *17% performance drop on the subsequent exam* relative to no-AI controls. The mode produces the artifact (the answered practice problem) without producing the cognitive process (the prediction error that drives encoding). Detailed in `pantry/ask-ai-research.md` §1.2.

- **Quiz Me for everything → performance without storage strength.** Spaced retrieval is powerful for what it teaches (the items in the deck), and useless for what it doesn't teach (the conceptual integration the items presuppose). A platform that does only retrieval practice produces students who can recall facts in the form they were practiced and cannot apply them. Detailed in `pantry/quiz-me-research.md` §1.3 (Pan & Rickard 2018 transfer meta-analysis: *d* = 0.40 on transfer, larger with response congruence, *smaller* without).

- **Glimmer for everything → the novice anxiety failure.** Ill-structured problems require the learner to specify the problem before solving it (Jonassen 1997, 2000). A novice without prior framework cannot perform the specification move productively — they hit the anxiety failure mode that the design-education literature documents extensively (cf. STEM-students-transitioning-to-open-paradigms work in `pantry/Generative Assignments, AI, and Education.txt`). Glimmer is powerful at the application stage and counterproductive at the acquisition stage.

- **Case Study for everything → pattern matching without causal understanding.** Cases anchor concepts in narrative, which is genuinely retrievable (Thistlethwaite 2012 BEME synthesis — `pantry/case-study-research.md` §1.1). But case-only deployments produce students who recognize cases ("this is a case like that case") without the conceptual machinery to handle a novel situation. The Dochy et al. 2003 effect-size split — −0.22 SD on knowledge, +0.46 SD on skills for PBL — names this trade.

The hammer-problem framing is the chapter's structural argument. Each mode has an evidence base that supports its use for *certain learning objectives at certain stages*. Each mode has a characteristic failure when used for everything. The platform's job is to know which mode to deploy when, and the *phase gates* (the mode-selection logic) are how the platform implements that knowledge.

---

## B. Ask AI — context-anchoring as guardrail

### What Ask AI is

Ask AI is the conversational mode where the student asks a question and the platform responds. The mode is structurally close to a general-purpose chatbot, but with two design constraints that distinguish it: **context-anchoring** (the model receives the current section, the prerequisite graph, and the student state as injected context) and **hint-not-answer guardrails** (the model is instructed and constrained to ask questions and provide hints rather than to supply the answer).

The evidence base sits in two literatures that the chapter must not collapse (per `pantry/ask-ai-research.md` §0):

- **Class A: Intelligent Tutoring Systems (ITS).** VanLehn 2011 ([*Educational Psychologist* 46(4)](https://www.tandfonline.com/doi/abs/10.1080/00461520.2011.611369)): *d* ≈ 0.76 for step-based ITS vs. no tutoring, essentially indistinguishable from human tutoring. Kulik & Fletcher 2016 ([*Review of Educational Research* 86(1)](https://journals.sagepub.com/doi/abs/10.3102/0034654315581420)): median effect *g* = 0.66 across 50 controlled evaluations. AutoTutor (Graesser et al. 2005) — the closest ITS analog to a chatbot — produces *d* ≈ 0.7–0.8 on deep comprehension. These results establish what is *possible* from a tightly-scripted dialog tutor.

- **Class B: Generative-AI chatbots.** Bastani et al. 2025 PNAS (already cited). Wang, Ribeiro et al. 2024 ([Tutor CoPilot, arXiv:2410.03017](https://arxiv.org/abs/2410.03017)): +4 pp on learning-objective mastery overall, +9 pp for students working with lower-quality tutors. Kestin, Miller et al. 2025 ([Harvard physics RCT, *Scientific Reports*](https://www.nature.com/articles/s41598-025-97652-6)): *d* ≈ 0.7–1.3 for a custom AI tutor designed against research-based pedagogical principles. The pattern is *bimodal* in this literature — strongly negative effects when AI is unguarded, large positive effects when designed against pedagogical principles.

The Ask AI mode in Medhavy bets on the second pattern: that context-anchoring plus hint-not-answer guardrails produce the GPT-Tutor outcome rather than the GPT-Base outcome.

### Context-anchoring as the guardrail

The context injection design is the load-bearing mechanism (see `pantry/ask-ai-research.md` §3). The candidate contexts, in order of cost and value:

1. Section title only — cheap, insufficient.
2. Current paragraph or selected passage — minimum for "ground the answer in *this* explanation, not a generic one."
3. Chapter so far — lets the chatbot use the chapter's specific definitions.
4. Prerequisites graph — lets the chatbot diagnose "your confusion is upstream of where you are."
5. Student state — what they've read, where they've struggled.
6. Full book — maximal coherence, maximal "lost in the middle" exposure.

The empirical constraint: *more context is not uniformly better.* The "lost in the middle" finding (Liu et al. 2023, [arXiv:2307.03172](https://arxiv.org/abs/2307.03172)) shows performance follows a U-shaped curve along the position of the relevant information — high at the beginning and end, significantly degraded (sometimes 30 pp lower) in the middle. The Chroma 2025 context-rot report extends this to all 18 frontier models tested as of 2025. Dumping the full chapter into context degrades the answer.

The Medhavy design discipline (per the existing `pantry/ask-ai-research.md` §3.3 specification):
- Inject current paragraph unconditionally.
- Inject specific prerequisites on demand, retrieved by RAG against the prerequisites graph.
- Avoid full-chapter dumps unless the question genuinely requires cross-section synthesis.
- Place high-value context at beginning and end; user query at the very end.
- Treat student state as separable context (structured summary, not transcript).

### The open question

The chapter must name the open question explicitly (per TIKTOC Ch 11): *does context-anchoring alone convert GPT-Base failure to GPT-Tutor success, or does the hint-not-answer guardrail discipline have to be separate from the context injection?* The Bastani study bundled context (teacher-designed hints) with discipline (model instructed to give hints, not answers). The literature does not yet separate the two variables. Medhavy's design effectively bundles them as well — but the chapter should flag that a planned A/B inside Medhavy could be a publishable result.

### Hint design — the Aleven/Koedinger tradition

The ITS literature on hint sequences transfers directly to chatbot design (`pantry/ask-ai-research.md` §2.2). Aleven, McLaren, Roll & Koedinger (2016, [*IJAIED* 26(1)](https://link.springer.com/article/10.1007/s40593-015-0089-1)) documented that students misuse on-demand hints — they click through hint sequences to reach the bottom-out hint (which gives away the answer) without reading the earlier hints. The Koedinger & Aleven (2007) *assistance dilemma* names the structural problem: there is an optimum amount of assistance, below which the student fails and above which the student offloads rather than learns. The optimum is curvilinear and depends on prior knowledge.

The operational translation for Ask AI: a single fixed prompt cannot be optimal across all students. The hint level should be a function of (student prior knowledge × current concept × prior performance on this concept). This is one of the inputs the engine (Ch 7) is learning over.

---

## C. Case Study — solo asynchronous AI-facilitated CBL

### What Case Study is in Medhavy

The Case Study mode presents a faculty-curated, pre-written case at the application stage of a concept's progression. The student works through the case alone (no group, no live facilitator), with the AI as a facilitator that asks Socratic questions, prompts re-examination of evidence, and surfaces missed considerations. The case has a defined learning objective, a decision point, and a consequence — the case design constraints Thistlethwaite 2012 names (`pantry/case-study-research.md` §1.1).

### Evidence base — Thistlethwaite 2012 BEME synthesis

Thistlethwaite et al. 2012 ("The Effectiveness of Case-Based Learning in Health Professional Education," BEME Guide No. 23, [*Medical Teacher* 34(6): e421–e444](https://www.tandfonline.com/doi/abs/10.3109/0142159X.2012.680939) `[verify exact pagination — confirmed in pantry case-study-research.md]`) is the canonical CBL synthesis. Design: BEME systematic review, 104 studies retained, 41 fully analyzed. Findings:

- CBL is associated with positive student satisfaction and self-reported gains in clinical reasoning across medical, dental, nursing, pharmacy, and allied health programs.
- Objective evidence for knowledge gains is *equivocal* — no clear advantage over lecture-based instruction on factual knowledge assessment.
- Effect on clinical reasoning skills shows a favorable trend, but the evidence base is heterogeneous and most studies are pre-post designs rather than RCTs.

The honest read for the Medhavy chapter: CBL is well-supported as an *application-stage* pedagogical move and is not supported as a *content-acquisition* move. This justifies the phase-gate that places Case Study after Quiz Me has demonstrated retrieval strength on the underlying concepts.

### The solo-asynchronous-AI-facilitated variant — what evidence licenses

The Thistlethwaite evidence base is on group, live, human-facilitated CBL. Medhavy's variant — solo, asynchronous, AI-facilitated — is not directly tested in this literature. The TIKTOC Ch 11 names this as one of the eight open questions: *does pre-written faculty-reviewed CBL produce reasoning gains comparable to group human-facilitated CBL when solo/asynchronous?*

The chapter should be honest about this:

- The *case structure* (decision point, consequence, defended reasoning as the assessable product) is what Thistlethwaite's evidence supports.
- The *solo asynchronous AI-facilitated* delivery is a different intervention with limited direct evidence.
- The bet: the AI facilitator can implement the *defensibility-of-reasoning* criterion (Jonassen 1997 — `pantry/glimmer-research.md` §1.5) by asking the structured questions a good human facilitator would ask.

### Pre-written vs. on-demand cases

The chapter should also engage the pre-written vs. on-demand decision. The Tarnvik (2007, *Medical Teacher* 29(1): e32–e36 — `pantry/case-study-research.md` §1.4) argument is that PBL's resource cost (one tutor per 6–8 students for week-long cases) drove medical schools to revert to CBL as the politically viable compromise. AI changes this calculus: on-demand AI-generated cases are cheap. The faculty review gate is the residual constraint — an unreviewed AI-generated case can introduce a misconception, a clinical error, or a misframing that the student will learn alongside the intended concept.

Medhavy's licensed-by-evidence path: pre-written, faculty-reviewed cases at the application stage. AI on-demand case generation is a research direction, not a deployment-ready feature, until the faculty-review gate can be reliably automated (which it cannot today).

---

## D. Quiz Me — FSRS, due-today counter, Zeigarnik closure

### What Quiz Me is

Quiz Me is the spaced retrieval practice mode. The student is presented with retrieval items on the current and prior concepts, scheduled by FSRS (Free Spaced Repetition Scheduler). The mode is gated by reading completion (Y1 evidence — see Ch 5) so that retrieval is not being asked for material that has not been encountered.

### Evidence base — three literatures the chapter must not confuse

Per `pantry/quiz-me-research.md` §0, three constructs are routinely conflated and produce wrong effect-size claims when fused:

1. **Retrieval practice** (the testing effect) — a *learning mechanism*. Roediger & Karpicke 2006 (canonical demonstration), Adesope, Trevisan & Sundararajan 2017 ([meta-analysis, *Review of Educational Research* 87(3)](https://journals.sagepub.com/doi/abs/10.3102/0034654316689306): *g* = 0.51 vs. re-study, *g* = 0.93 vs. filler, *g* ≈ 0.67 in classroom settings).

2. **Spaced repetition** (the spacing effect) — a *scheduling principle*. Cepeda, Pashler, Vul, Wixted & Rohrer 2006 ([meta-analysis, *Psychological Bulletin* 132(3)](https://pubmed.ncbi.nlm.nih.gov/16719566/), 839 assessments) — distributed practice consistently outperforms massed practice; the optimal inter-study interval is a function of the retention interval, not a fixed value.

3. **FSRS, SM-2, Anki, SuperMemo** — *scheduling algorithms*. Implementations of the spacing principle. FSRS is the default scheduler in Anki since November 2023 (v23.10) and is open-source (`pantry/quiz-me-research.md` §2).

When the chapter says "Quiz Me uses FSRS, an evidence-based algorithm for scheduling review at intervals that maximize durable retention," it is claiming three things at once: that retrieval practice works (mechanism), that spacing matters (principle), and that FSRS is the right implementation of the principle (algorithm). The first two are well-supported. The third is supported by FSRS's internal benchmarks against SM-2 (≈20–30% fewer reviews for the same target retention; FSRS-5 hits target retention with ±5.3% error vs. SM-2's ±16.2% — per `pantry/quiz-me-research.md` §2.3) but **is not yet established by RCT comparing learning outcomes under FSRS vs. SM-2**. The claim "FSRS produces better scheduling" is established; the claim "FSRS produces better learning" is not.

### FSRS as canonical citation

FSRS (Free Spaced Repetition Scheduler) was developed since 2022 by Jarrett Ye (research engineer at MaiMemo Inc.) and the open-spaced-repetition community on GitHub. The model represents each card with three latent variables: D (Difficulty), S (Stability — the number of days at which retrievability is predicted to fall to a target retention level, e.g., 90%), and R (Retrievability — the current predicted recall probability). After each review, the user gives a 1–4 rating; the model updates D and S as a function of the rating, current R, and prior values.

Canonical references:
- Open Spaced Repetition project: https://open-spaced-repetition.github.io/
- fsrs4anki repository: https://github.com/open-spaced-repetition/fsrs4anki
- ABC of FSRS wiki: https://github.com/open-spaced-repetition/fsrs4anki/wiki/abc-of-fsrs
- fsrs PyPI: https://pypi.org/project/fsrs/
- Expertium benchmark: https://expertium.github.io/Benchmark.html

The chapter should cite the wiki and PyPI documentation as primary sources for the algorithm specification (`[verify: at the time of drafting, confirm there is a published academic paper from Ye and collaborators; if so, that should be the citation; otherwise the project documentation is canonical]`). The underlying theory — Bjork & Bjork 1992 retrieval-strength/storage-strength — is the academic backbone.

### The due-today counter as Zeigarnik closure — the habit-formation argument

Per `pantry/quiz-me-habit-research.md` (cross-referenced from the existing pantry), the Quiz Me mode's adoption depends not on the algorithm sophistication but on the habit-formation UI — specifically the *due-today counter* that drives users to return to the app and clear their queue.

The Zeigarnik effect (Zeigarnik 1927, summarized in Lewin's field theory): unfinished tasks produce a tension state that motivates completion. A visible counter of "you have 47 cards due today" creates and surfaces the Zeigarnik tension. Anki users report that the due-count is the load-bearing UI element — it is what they check, it is what they clear, it is what defines the habit loop.

The honest read for the chapter (per the existing pantry note): the algorithm is a small contributor to whether students adopt the tool at all. The due-count is *load-bearing UI*. The chapter must land this — the engineering instinct will be to optimize the algorithm; the design instinct should be to optimize the counter.

This is also one of the eight open questions in TIKTOC Ch 11: *is the Quiz Me habit loop driven by the due-count or the algorithm?* The chapter flags the question and points forward.

### Phase gate for Quiz Me

The Quiz Me phase gate uses Y1 (temporal engagement pattern) as the gating criterion: the system does not surface Quiz Me items for material the student has not demonstrated reading engagement with. The gate prevents the "quiz on material I haven't read" failure mode that produces frustration without learning.

The deeper gate is the *evidence-not-completion* principle (`pantry/02-why-does-solving-it-require-a-platform.md`): Quiz Me items advance from "due" to "mastered" not when the student gets them right once, but when the retest at the FSRS-scheduled interval shows the storage strength has consolidated. This is the Y6 (retrieval strength decay) signal in operation — the gate is the measurement.

---

## E. Glimmer — ill-structured problem at session level, backwards-faded scaffolding

### What Glimmer is

Glimmer is the creative cumulative assignment mode. At the session level, the student receives an ill-structured problem: design a clinical protocol, draft a research proposal, write a critique of a published paper. The problem has multiple valid solutions, no agreed evaluation criteria, and requires the student to specify the problem before solving it.

The cumulative aspect: across many Glimmer sessions over a term, the pieces assemble into a substantial project the student did not know they were building. The emergence is the design move.

### Evidence base — four constructs the chapter must not confuse

Per `pantry/glimmer-research.md` §0, "creative assignments" in EdTech vendor writing collapses four distinct constructs:

1. **Generative Learning Activities (GLA)** — Wittrock 1974, Fiorella & Mayer 2016 ([*Educational Psychology Review* 28(4)](https://link.springer.com/article/10.1007/s10648-015-9348-9)). Eight activities (summarize, map, draw, imagine, self-explain, teach, enact, self-test). Effect sizes vary by activity; self-explanation is the largest (*d* ≈ 0.55 on both retention and transfer).

2. **Elaborative Interrogation (EI)** — Pressley et al. 1987, 1992. The "why is this true?" technique. Dunlosky et al. 2013 ([*Psychological Science in the Public Interest* 14(1)](https://journals.sagepub.com/doi/10.1177/1529100612453266)) rated EI as "moderate utility." Effect sizes typically *d* = 0.40 to 0.75 on delayed retention of factual material.

3. **Ill-Structured Problems (ISP)** — Jonassen 1997, 2000. The literature on multiple-solution, contested-criteria problem-solving. Belland et al. 2017 ([scaffolding meta-analysis, *Review of Educational Research* 87(2)](https://journals.sagepub.com/doi/10.3102/0034654316670999): *g* = 0.46 for computer-based scaffolding for STEM cognitive outcomes).

4. **Project-Based Learning (PBL)** — Hmelo-Silver 2004 synthesis ([*Educational Psychology Review* 16(3)](https://link.springer.com/article/10.1023/B:EDPR.0000034022.16470.f3)); Chen & Yang 2019 meta-analysis ([*Educational Research Review* 26: 71–81](https://www.sciencedirect.com/science/article/abs/pii/S1747938X18301027): *g* = 0.71 vs. traditional instruction, moderators include duration and technology support).

Glimmer at the *session* level is most cleanly an ISP. The rubric (WHY / usefulness / mechanism / defensibility / specificity) maps onto Jonassen's defensibility-of-reasoning criterion. Glimmer at the *term* level is closer to PBL — but with a critical divergence: in PBL the driving question is *announced* at the start; in Glimmer it is *hidden* until weeks 10–11. This divergence means the Chen & Yang 2019 effect size for PBL does not directly transfer to Glimmer. The chapter must flag this honestly.

### The novice anxiety failure mode (weeks 1–3)

The chapter must address the most documented Glimmer failure: novices presented with ill-structured problems before they have the prerequisite structure crash into anxiety and disengage. The design-education literature on STEM students transitioning to open-ended paradigms (per `pantry/Generative Assignments, AI, and Education.txt` and the underlying NSF PAR / engineering-education work) documents this extensively — the student who cannot specify the problem productively reaches anxiety, then either fakes a specification or disengages.

The failure mode shows up empirically as: 60% of students abandoning the mode in week 2. The exercise the TIKTOC specifies (Exercise 6.2 in Ch 6) uses exactly this data point.

The mechanism: ill-structured problems require the learner to *specify* the problem before solving it (Jonassen 2000, eleven problem types). Specification requires prior framework. A novice without framework cannot perform the specification move productively. The anxiety is the metacognitive signal of "I cannot make progress and I do not know how to make progress" — a different state from "this is hard and I'm working through it."

### Backwards-faded scaffolding — Atkinson, Renkl & Merrill 2003

The design response is *backwards-faded scaffolding*. Atkinson, Renkl & Merrill 2003 ("Transitioning from studying examples to solving problems: Effects of self-explanation prompts and fading worked-out steps," [*Journal of Educational Psychology* 95(4): 774–783](https://doi.org/10.1037/0022-0663.95.4.774)) is the canonical citation. The idea: a problem is initially presented with *all steps worked out*, the student studies the worked solution; then later versions of similar problems are presented with the *last step missing*, requiring the student to complete it; then the *last two steps* missing, and so on, with the scaffolding fading *from the back* of the solution toward the front. By the time the student is solving from scratch, they have built the framework by working backwards from the end state.

The pedagogical mechanism: each fading step asks the student to perform exactly one new cognitive operation in a context where every other operation is already supported. The cognitive load is bounded (Sweller's cognitive load theory). The anxiety failure is prevented because the student is never asked to perform an operation they have no scaffold for.

Renkl on worked examples generally (`pantry/domain-specific-instruction-research.md` §3.5): Renkl 2014 ([*Cognitive Science* 38(1)](https://doi.org/10.1111/cogs.12086)) — worked examples produce reliably stronger learning than equivalent time on problem-solving alone, particularly for novices, effect sizes typically 0.5–1.0 SD on near-transfer.

For Glimmer specifically: the weeks 1–3 design must include backwards-faded worked examples of *the Glimmer rubric being satisfied*. The student is not asked to produce a well-defended design from scratch in week 1; they are asked to evaluate a fully-worked example, then to complete the last move on a partially-worked example, then to take more of the work on each successive Glimmer. The fading is the scaffolding.

This is one of the eight open questions in TIKTOC Ch 11: *does backwards-faded scaffolding prevent the anxiety collapse in novice Glimmer users?*

### Pea 2004 on scaffolding withdrawal

Pea, R. D. 2004. "The Social and Technological Dimensions of Scaffolding and Related Theoretical Concepts for Learning, Education, and Human Activity," [*Journal of the Learning Sciences* 13(3): 423–451](https://www.tandfonline.com/doi/abs/10.1207/s15327809jls1303_6).

Pea's contribution: pulled the term *scaffolding* back to its original Wood, Bruner & Ross (1976) meaning — *temporary* support, calibrated to the learner's current need, withdrawn as competence grows. **Permanent scaffolding is not scaffolding; it is dependency.** The EdTech failure mode Pea names is systems that treated scaffolding as a permanent feature ("we have scaffolds!") rather than a transient one.

For Glimmer: the AI reviewer's questions must be *contingent* on what the learner produced (not a generic checklist), must *reduce in support* as the learner's framing matures (not constant pressure on every dimension every week), and must *transfer* — the learner who has done 10 Glimmers should be able to ask themselves the reviewer's questions without the reviewer present.

Per `pantry/glimmer-displacement-research.md` §3.3 — Puntambekar & Hübscher 2005 ([*Educational Psychologist* 40(1)](https://www.tandfonline.com/doi/abs/10.1207/s15326985ep4001_1)): systems with full contingency-and-fading scaffolding produced reliably larger learning gains than systems with initial-support-only. The effect was particularly strong on *transfer*. Permanent scaffolding produced students who could perform with the scaffold and not without it.

### Phase gate for Glimmer

The Glimmer phase gate uses Y7 (scaffolding response curve) as the gating criterion: the system does not surface a Glimmer for a concept until the student's prior performance shows hint-responsive understanding. This prevents the novice-anxiety failure structurally — a student whose Y7 is low for the concept has no underlying framework, so the Glimmer would ask for specification work the student cannot perform productively.

The deeper gate is the curriculum-design specification: each Glimmer's rubric must include scaffolding elements that fade per the Atkinson-Renkl design, and the AI reviewer's intervention level must be contingent on the learner's prior Glimmer performance.

---

## F. Phase gates as measurement decisions

The chapter's structural argument is that phase gates are not merely pedagogical decisions; they are *measurement decisions*. Each gate uses a specific GLP signal (from Ch 5) as the gating criterion:

- **Quiz Me gated until section read** — uses Y1 (temporal engagement pattern). The student must have demonstrated reading engagement before retrieval practice is appropriate.
- **Glimmer gated until concept built** — uses Y7 (scaffolding response curve). The student must show hint-responsive understanding before ill-structured problem-solving is appropriate.
- **Case Study gated until representation sufficient** — uses Y3 (cross-context transfer) plus Y6 (retrieval decay). The student must be able to apply the concept outside instructional context, and the concept must be in storage rather than transient performance.
- **Ask AI not gated, but bounded by context-anchoring** — Ask AI is the *entry* mode and is always available, but the responses are constrained by the prerequisites graph. If the student is asking about a concept whose prerequisites they have not built, the Ask AI response routes them to remediation rather than answering the surface question.

The phase-gate framework is a closed-loop architecture: the GLP signal from the measurement layer informs the mode-selection decision; the mode selection generates the learning interaction; the learning interaction produces new GLP signal; the next phase-gate decision uses the updated signal.

This is what makes the four modes a *system* rather than a *menu*. A menu lets the learner pick — and the learner will pick the mode that feels easiest (the fluency trap from Ch 5). The phase-gate system selects on the learner's behalf, using evidence the learner does not have direct access to. The platform knows what the student does not. This is the same uncomfortable claim Ch 5 had to land, restated at the mode-selection level.

---

## G. Worked example sketch — pharmacokinetics mode sequence

The TIKTOC asks for a worked example showing a medical student working through a pharmacokinetics concept across multiple modes. A schematic for the chapter draft:

1. **Ask AI to clarify a prerequisite.** Student arrives at the pharmacokinetics chapter; the prerequisite graph flags that linear vs. nonlinear kinetics depends on Michaelis-Menten enzyme kinetics, which the learner's profile shows as "weak Y6 — high initial performance, sharp decay." Ask AI is context-anchored to the Michaelis-Menten section of the biochemistry textbook, hint-only mode. Student asks: "Why does saturation matter for drug dosing?" The Ask AI response asks: "What did the Michaelis-Menten kinetics tell you about reaction rate at high substrate concentrations?" The student attempts the answer; the system logs the response and the confidence rating; Y4 (uncertainty calibration) is updated.

2. **Quiz Me on the core mechanism.** After the Ask AI session, the system schedules Quiz Me items on linear vs. nonlinear pharmacokinetics. The items are scheduled by FSRS; the due-today counter shows 12 items. The student clears the queue. The Y1 signal confirms reading engagement; the Y6 retest at 7 days will confirm storage strength.

3. **Case Study on a drug interaction scenario.** Once the Y6 retest shows the student has converted performance to storage strength on linear vs. nonlinear kinetics, the system surfaces a pre-written, faculty-reviewed case study on warfarin-amiodarone interaction. The case has a decision point (which dose adjustment, with what monitoring schedule) and a consequence (the bleeding risk if the dose is not adjusted). The AI facilitator asks Socratic questions: "What did your previous analysis of CYP3A4 inhibition predict about the half-life change?" The student's reasoning is the product; the verdict is less important than the defensibility of the reasoning.

4. **Glimmer: design a dosing protocol for a complex patient.** In week 8 of the course, after the student has demonstrated mastery on individual concepts and case-application, the Glimmer surfaces: design a dosing protocol for a patient with renal impairment, on warfarin, requiring amiodarone for atrial fibrillation. The Glimmer's rubric: name the drug-drug interactions and their direction; specify the monitoring schedule and the decision rule for dose adjustment; defend the choice of starting dose given the renal function. The AI reviewer asks contingent questions — if the student named CYP3A4 inhibition but not P-gp, the reviewer asks "what else might be at play?" rather than "you missed P-gp." The scaffolding is the design.

At each mode transition, the measurement layer captures the GLP signals. The engine (Ch 7) uses the signals to update the per-learner reward function for this concept and these modes. The next session begins with an updated policy.

---

## H. Cross-references to existing pantry

- `pantry/ask-ai-research.md` — primary source for Ask AI section. Bastani PNAS 2025, VanLehn 2011, Kestin et al. 2025, the context-injection design, the lost-in-the-middle and context-rot findings, the Aleven/Koedinger hint-design literature, the fluency-trap evidence. Cite directly throughout.

- `pantry/case-study-research.md` — primary source for Case Study section. Thistlethwaite 2012 BEME synthesis, Dochy 2003 PBL meta-analysis, Hartling 2010, Tarnvik 2007, the closed-vs-open case design debate, the pre-written-vs-on-demand decision.

- `pantry/quiz-me-research.md` — primary source for Quiz Me section. Roediger & Karpicke 2006, Adesope et al. 2017, Pan & Rickard 2018 transfer meta-analysis, Cepeda 2006 / 2008 spacing meta-analyses, Bjork & Bjork 1992 storage/retrieval theory, FSRS specification and benchmarks. Critical: the three-literature distinction (mechanism, principle, algorithm).

- `pantry/quiz-me-habit-research.md` — primary source for the due-today counter / Zeigarnik / habit-formation argument. The "load-bearing UI" framing.

- `pantry/glimmer-research.md` — primary source for Glimmer section. Fiorella & Mayer 2016, Jonassen 1997 / 2000 on ISPs, Belland 2014 / Belland et al. 2017 scaffolding meta-analysis, Hmelo-Silver 2004 PBL synthesis, Chen & Yang 2019 PBL meta-analysis, Dunlosky et al. 2013 ranking of study techniques, Pressley elaborative interrogation, the four-construct disambiguation.

- `pantry/glimmer-displacement-research.md` — primary source for scaffolding-fading argument. Pea 2004, Puntambekar & Hübscher 2005, van de Pol et al. 2010 on operationalizing scaffolding, the pseudocode-problem framing.

- `pantry/domain-specific-instruction-research.md` — for Renkl 2014 on worked examples, Atkinson et al. 2000 on instructional principles from worked-examples research. Supports the backwards-faded scaffolding section.

- `pantry/concept-sequencing-research.md` — for the prerequisite-graph reasoning, BKT/DKT, and the importance-weighting argument. Used in the phase-gate section.

- `pantry/PEDAGOGY ARCHITECTURE.txt` — Medhavy-internal source for the rationale on these specific modes (vs. others). The chapter draws on this for the "why these four and not others" framing — the criteria were (a) implementable within a text-based AI conversation, (b) meaningfully different content requirements, (c) produce distinguishable learner behavior the bandit can observe.

- `pantry/_lib_case_study_prompts.md` — for example prompts that have been used in CBL deployments. Useful as illustration of the AI-facilitator question structure for the Case Study section.

- `pantry/Generative Assignments, AI, and Education.txt` — for the engineering-education literature on novice anxiety in ill-structured problem solving, and the emergent-portfolio writing pedagogy that informs Glimmer's term-level structure. The Works Cited list in this file is the source for several of the design-education citations.

- `pantry/04-what-makes-this-different.md` — internal draft source for the four-modes description as it stands in current Medhavy 1.5. Use as the operational ground truth for what the platform currently does; flag where the textbook version diverges (e.g., the textbook collapses the older 5-mode design to 4 by merging "direct instruction" and "Ask AI").

---

## I. Top three consequential gaps / flags

1. **The solo-asynchronous-AI-facilitated CBL evidence gap.** Thistlethwaite 2012's evidence base is on group, live, human-facilitated CBL. Medhavy's variant differs on three dimensions (solo, asynchronous, AI-facilitated) and the chapter should not claim the Thistlethwaite effect sizes transfer. The honest framing: the *case structure* is what the evidence supports; the *delivery mode* is a research bet. This is one of the eight open questions in Ch 11 and should be flagged in the Ch 6 draft as well. **Flag for Nik:** confirm the chapter should treat this as a clearly-labeled open question, not as a settled application of Thistlethwaite.

2. **The backwards-faded scaffolding citation chain needs verification.** Atkinson, Renkl & Merrill 2003 in *Journal of Educational Psychology* is the canonical citation for the technique; Renkl 2014 in *Cognitive Science* is the general worked-examples synthesis. The exact pagination and DOI should be confirmed before the chapter is drafted. The pantry's `domain-specific-instruction-research.md` cites Renkl 2014 with DOI 10.1111/cogs.12086 — this should be the primary cite for the general principle. Atkinson et al. 2003 needs `[verify]` flag in the chapter until confirmed. The pantry also cites Atkinson, Derry, Renkl & Wortham 2000 ([*Review of Educational Research* 70(2)](https://doi.org/10.3102/00346543070002181)) as the more general principles-from-worked-examples paper — that may be the better citation alongside Atkinson et al. 2003 for the backwards-faded technique specifically.

3. **The FSRS academic-paper citation status.** FSRS is well-documented in the open-spaced-repetition project documentation and is the default scheduler in Anki since November 2023. The chapter should cite the project documentation as authoritative; however, the academic-paper status is uncertain — Ye and collaborators may have published a formal description in a venue like the Educational Data Mining proceedings or as a preprint. `[verify: search for "Ye FSRS" in academic databases and arXiv before the chapter is drafted; if a published paper exists, that should be the primary citation alongside the project documentation.]` This matters because the chapter is making a load-bearing claim ("Quiz Me uses FSRS, an evidence-based algorithm") and the evidence base for FSRS specifically (vs. spaced repetition generally) rests primarily on the internal benchmark data, not on RCT learning-outcome comparisons.

---

*End of Ch 6 research notes. The four modes are application-level material against the architecture established by Chs 4–5; the phase-gate framework is where this chapter does its most original work, by showing that mode selection is fundamentally a measurement decision (GLP signal → gate → mode → new GLP signal). The hammer-problem opening and the worked example are the structural pivots.*
