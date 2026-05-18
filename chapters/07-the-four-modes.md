# Chapter 7 — The Four Modes

**Suggested titles**
1. The Four Modes
2. The Arms the Engine Pulls
3. When the Mode Is the Hammer

**TL;DR.** Each of the four modes — Ask AI, Case Study, Quiz Me, Glimmer — has an evidence base for what it does well, and a characteristic failure when it is used for *everything*. The platform's job is not to deploy modes; it is to know which mode to deploy when. The *phase gates* — the conditions under which each mode is offered — are how the platform implements that knowledge. Phase gates are not pedagogical decisions. They are *measurement decisions*: the GLP signal from Chapter 5 is the gating criterion.

---

## Learning objectives

By the end of this chapter you should be able to:

1. **(Understand)** Explain the evidence base for each of the four modes and identify the specific learning mechanism each mode activates.
2. **(Analyze)** Explain why each mode is phase-gated and what specific failure mode each gate prevents.
3. **(Apply)** Select the appropriate mode or mode sequence for a given learning objective, using evidence and phase-gate logic as criteria.
4. **(Evaluate)** Diagnose a mode-deployment failure and specify the design correction.

**Prerequisites.** Chapter 4 (the four layers) and Chapter 5 (the GLP framework). You need the seven signals as Y1–Y7, because the phase gates are specified in their terms.

---

## Where this fits the conductor frame

This chapter primarily serves the learner — the first of the three questions, in order — because the four modes are the instruments that touch the learner directly. Ask AI, Quiz Me, Case Study, Glimmer: each one is a different way of producing the cognitive work the learner needs to do. The instructor designs which mode is appropriate where; the organization is downstream of both. But what the chapter is fundamentally specifying is what the learner experiences when the conductor picks an instrument.

What this chapter specifies for the conductor is the instrument inventory itself, and the phase-gate logic that decides when each one plays. Each mode has an evidence base for what it does well and a characteristic failure when it is used for everything. Phase gates are how the conductor's judgment becomes machine-readable: a Glimmer is not offered until prerequisite signals say the learner has the framework to use it; Ask AI is constrained by context-anchoring so the model does not become the artifact-generator the Bastani study warned about.

The chapter runs the experiment by making each phase gate a falsifiable commitment. The conductor is not asserting that retrieval practice produces transfer at *d* = 0.40 in this deployment; she is committing to measure transfer against retrieval-practice dosage and update the gate if the data does not bear it out. The mode-level hammer problem is what the conductor is openly testing against — not by defending one mode but by running the comparison continuously.

---

## 1. The hammer problem, at mode level

Maslow's hammer says that if the only tool you have is a hammer, everything looks like a nail. The hammer problem at the platform level was Chapter 1's argument — a system with one mode treats every learning problem as the problem its one mode is good at. I want to restate the argument at *mode* level, because that's where the chapter actually does its work. Each of the four modes has a characteristic failure when it is the only mode available, and the evidence for the failure is specific.

**Ask AI for everything → the Bastani GPT-Base outcome.** Bastani, Bastani, Sungu, Ge, Kabakcı & Mariman (2025, *PNAS* 122(26), [e2422633122](https://www.pnas.org/doi/10.1073/pnas.2422633122)) measured this directly: students using unguarded GPT-4 during practice scored 48 percentage points higher than no-AI controls *during practice* — and 17 percentage points lower than no-AI controls on the subsequent exam where AI was unavailable. The mode produces the artifact (the answered practice problem) without producing the cognitive process (the prediction error that drives encoding). One mode, applied universally, becomes the fluency trap Chapter 5 named.

**Quiz Me for everything → performance without storage strength.** Spaced retrieval is powerful for what it teaches (the items in the deck) and useless for what it does not (the conceptual integration the items presuppose). Pan & Rickard (2018, *Psychological Bulletin* 144(7)) meta-analyzed the transfer effects of retrieval practice and found *d* ≈ 0.40 on transfer overall, larger when the retrieval and transfer formats were congruent, *smaller* when they were not. A Quiz Me–only deployment produces students who can recall facts in the form they were practiced and cannot apply them in the form they encounter clinically.

**Glimmer for everything → the novice anxiety failure.** Ill-structured problems (Jonassen 1997, 2000) require the learner to *specify the problem* before solving it. A novice without prior framework cannot perform the specification move productively. The design-education literature documents the result: 60% of students abandoning open-ended creative assignments in week 2 is not unusual when the scaffolding has not been built in. The anxiety is the metacognitive signal of "I cannot make progress and I do not know how to make progress" — a different state from "this is hard and I'm working through it."

**Case Study for everything → pattern matching without causal understanding.** Cases anchor concepts in narrative, which is genuinely retrievable. Thistlethwaite et al. (2012, BEME Guide No. 23, *Medical Teacher* 34(6): e421–e444) is the canonical CBL synthesis: 104 studies retained, 41 fully analyzed, positive effects on satisfaction and self-reported reasoning, *equivocal* on factual knowledge gains. Case-only deployments produce students who recognize cases ("this is a case like that case") without the conceptual machinery to handle a novel situation.

The hammer-problem framing is the chapter's structural argument. Each mode has an evidence base that supports its use *for certain learning objectives at certain stages*. Each mode has a characteristic failure when used for everything. **The platform's job is to know which mode to deploy when. The phase gates are how the platform implements that knowledge.**

---

## 2. Ask AI — context-anchoring as the guardrail

### What Ask AI is

Ask AI is the conversational mode where the student asks a question and the platform responds. Structurally it is close to a general-purpose chatbot, with two design constraints that distinguish it: **context-anchoring** (the model receives the current section, the prerequisite graph, and the student's state as injected context) and a **hint-not-answer guardrail** (the model is instructed and constrained to ask questions and provide hints rather than to supply the answer).

The evidence base sits in two literatures the chapter must not collapse.

**Class A — Intelligent Tutoring Systems.** VanLehn (2011, [*Educational Psychologist* 46(4)](https://www.tandfonline.com/doi/abs/10.1080/00461520.2011.611369)) reported step-based ITS at *d* ≈ 0.76 versus no tutoring, essentially indistinguishable from human tutoring. Kulik & Fletcher (2016, [*Review of Educational Research* 86(1)](https://journals.sagepub.com/doi/abs/10.3102/0034654315581420)) found a median effect of *g* = 0.66 across 50 controlled evaluations. AutoTutor (Graesser et al. 2005) — the closest ITS analog to a chatbot — produces *d* ≈ 0.7–0.8 on deep comprehension. These results establish what is *possible* from a tightly-scripted dialog tutor.

**Class B — Generative-AI chatbots.** Bastani et al. 2025 (already cited) is the GPT-Base / GPT-Tutor split — same GPT-4, two prompt wrappers, opposite outcomes. Wang, Ribeiro et al. (2024, [Tutor CoPilot, arXiv:2410.03017](https://arxiv.org/abs/2410.03017)) showed +4 percentage points on learning-objective mastery overall, +9 percentage points for students working with lower-quality tutors. Kestin, Miller et al. (2025, Harvard physics RCT, [*Scientific Reports*](https://www.nature.com/articles/s41598-025-97652-6)) found *d* ≈ 0.7–1.3 for a custom AI tutor designed against research-based pedagogical principles. **The pattern is bimodal**: strongly negative effects when AI is unguarded, large positive effects when designed against pedagogical principles.

Ask AI in Medhavy bets on the second pattern. Context-anchoring plus hint-not-answer guardrails produce the GPT-Tutor outcome rather than the GPT-Base outcome.

### Context-anchoring as the primary guardrail

The context-injection design is the load-bearing mechanism. The candidate contexts, in roughly increasing order of cost and value:

1. Section title only — cheap, insufficient.
2. Current paragraph or selected passage — minimum for "ground the answer in *this* explanation, not a generic one."
3. Chapter so far — lets the chatbot use the chapter's specific definitions.
4. Prerequisites graph — lets the chatbot diagnose "your confusion is upstream of where you are."
5. Student state — what they've read, where they've struggled.
6. Full book — maximal coherence, maximal "lost in the middle" exposure.

The empirical constraint: **more context is not uniformly better.** The "lost in the middle" finding (Liu et al. 2023, [arXiv:2307.03172](https://arxiv.org/abs/2307.03172)) shows performance follows a U-shaped curve along the position of the relevant information — high at the beginning and end, significantly degraded (sometimes 30 percentage points lower) in the middle. The Chroma 2025 context-rot report extends this to all 18 frontier models tested as of 2025. Dumping the full chapter into context degrades the answer.

The Medhavy design discipline:

- Inject current paragraph unconditionally.
- Inject specific prerequisites on demand, retrieved by RAG against the prerequisites graph.
- Avoid full-chapter dumps unless the question genuinely requires cross-section synthesis.
- Place high-value context at the beginning and end; user query at the very end.
- Treat student state as separable context (structured summary, not transcript).

I want to flag this honestly: the literature does not yet *separate* the two variables — context anchoring versus hint-not-answer discipline. Bastani's positive GPT-Tutor result bundled teacher-designed hints (context) with model instructions to give hints rather than answers (discipline). Medhavy's design bundles them as well. **An A/B inside Medhavy that varied one while holding the other constant could be a publishable result.** This is one of Chapter 11's open questions.

### Hint design — the assistance dilemma

The ITS literature on hint sequences transfers directly. Aleven, McLaren, Roll & Koedinger (2016, [*IJAIED* 26(1)](https://link.springer.com/article/10.1007/s40593-015-0089-1)) documented that students misuse on-demand hints — they click through hint sequences to reach the bottom-out hint (which gives away the answer) without reading the earlier ones. Koedinger & Aleven (2007) named the structural problem: the *assistance dilemma*. There is an optimum amount of help, below which the student fails and above which the student offloads rather than learns. The optimum is curvilinear and depends on prior knowledge.

The operational translation: a single fixed prompt cannot be optimal across all students. Hint level should be a function of (student prior knowledge × current concept × prior performance on this concept). This is one of the inputs the engine (Chapter 7) learns over.

---

## 3. Case Study — solo asynchronous AI-facilitated CBL

### What Case Study is in Medhavy

The Case Study mode presents a faculty-curated, pre-written case at the *application stage* of a concept's progression. The student works through the case alone (no group, no live facilitator). The AI serves as a facilitator that asks Socratic questions, prompts re-examination of evidence, and surfaces missed considerations. The case has a defined learning objective, a decision point, and a consequence.

### Evidence base — Thistlethwaite 2012, carefully

Thistlethwaite et al. 2012 is the canonical CBL synthesis. The honest read:

- CBL is associated with positive student satisfaction and self-reported gains in clinical reasoning across medical, dental, nursing, pharmacy, and allied health programs.
- Objective evidence for knowledge gains is *equivocal* — no clear advantage over lecture-based instruction on factual knowledge assessment.
- Effect on clinical reasoning skills shows a favorable trend, but the evidence base is heterogeneous and most studies are pre-post designs rather than RCTs.

The implication: CBL is well-supported as an *application-stage* pedagogical move and is not supported as a *content-acquisition* move. This justifies the phase gate that places Case Study after Quiz Me has demonstrated retrieval strength on the underlying concepts.

### The solo-asynchronous-AI-facilitated variant — what evidence licenses

Thistlethwaite's evidence base is on *group, live, human-facilitated* CBL. Medhavy's variant is solo, asynchronous, AI-facilitated. **These are three differences from the tested intervention.** I want to be honest about this. The case *structure* (decision point, consequence, defended reasoning as the assessable product) is what Thistlethwaite's evidence supports. The *delivery mode* is a research bet. The bet: the AI facilitator can implement the defensibility-of-reasoning criterion (Jonassen 1997) by asking the structured questions a good human facilitator would ask. The bet may pay off. It is not the literature's claim. This is one of Chapter 11's open questions and should be read here as a clearly-labeled bet, not a settled application of Thistlethwaite.

### Pre-written versus on-demand cases

The pre-written-versus-on-demand decision matters. Tarnvik (2007, *Medical Teacher* 29(1): e32–e36) `[verify exact pagination]` argued that PBL's resource cost — one tutor per six to eight students for week-long cases — drove medical schools to revert to CBL as the politically viable compromise. AI changes this calculus. On-demand AI-generated cases are cheap. The faculty review gate is the residual constraint: an unreviewed AI-generated case can introduce a misconception, a clinical error, or a misframing that the student learns alongside the intended concept.

Medhavy's evidence-licensed path: **pre-written, faculty-reviewed cases at the application stage.** AI on-demand case generation is a research direction, not a deployment-ready feature, until the faculty-review gate can be reliably automated — which it cannot today.

---

## 4. Quiz Me — FSRS, due-today counter, Zeigarnik closure

### What Quiz Me is

Quiz Me is the spaced retrieval practice mode. The student is presented with retrieval items on the current and prior concepts, scheduled by FSRS (Free Spaced Repetition Scheduler). The mode is gated by reading completion (Y1 evidence — Chapter 5) so retrieval is not being asked for material the student has not encountered.

### Three literatures the chapter must not confuse

This is where Quiz Me's evidence base gets routinely garbled in vendor writing, so I want to keep the three threads separate.

**Retrieval practice (the testing effect) — a learning mechanism.** Roediger & Karpicke 2006 is the canonical demonstration. Adesope, Trevisan & Sundararajan (2017, [meta-analysis, *Review of Educational Research* 87(3)](https://journals.sagepub.com/doi/abs/10.3102/0034654316689306)) found *g* = 0.51 versus re-study, *g* = 0.93 versus filler, and *g* ≈ 0.67 in classroom settings. The mechanism is well-supported.

**Spaced repetition (the spacing effect) — a scheduling principle.** Cepeda, Pashler, Vul, Wixted & Rohrer (2006, [meta-analysis, *Psychological Bulletin* 132(3)](https://pubmed.ncbi.nlm.nih.gov/16719566/), 839 assessments) — distributed practice consistently outperforms massed practice. The optimal inter-study interval is a function of the retention interval, not a fixed value. The principle is well-supported.

**FSRS, SM-2, Anki, SuperMemo — scheduling algorithms.** Implementations of the spacing principle. FSRS has been the default scheduler in Anki since November 2023 (v23.10). It is open-source.

When someone says "Quiz Me uses FSRS, an evidence-based algorithm for scheduling review at intervals that maximize durable retention," they are claiming three things at once: that retrieval practice works (mechanism), that spacing matters (principle), and that FSRS is the right implementation of the principle (algorithm). The first two are well-supported. The third is supported by FSRS's *internal benchmarks* against SM-2 — roughly 20–30% fewer reviews for the same target retention; FSRS-5 hits target retention with ±5.3% error versus SM-2's ±16.2%. **But the third claim has not been established by RCT comparing learning outcomes under FSRS versus SM-2.** "FSRS produces better scheduling" is established; "FSRS produces better learning" is a reasonable bet from the better-scheduling claim, not a directly demonstrated finding. The chapter cites the project documentation as canonical (`[verify: search for "Ye FSRS" in academic databases — if a published paper or preprint exists, that should be the primary citation alongside the project docs]`) and flags this as Chapter 11 open question.

### FSRS — the algorithm in plain English

FSRS (Free Spaced Repetition Scheduler) was developed since 2022 by Jarrett Ye (MaiMemo Inc.) and the open-spaced-repetition community. The model represents each card with three latent variables: D (Difficulty), S (Stability — the number of days at which retrievability is predicted to fall to a target retention level, e.g., 90%), and R (Retrievability — the current predicted recall probability). After each review the user gives a 1–4 rating; the model updates D and S as a function of the rating, current R, and prior values.

Primary references:

- [Open Spaced Repetition project](https://open-spaced-repetition.github.io/)
- [fsrs4anki repository](https://github.com/open-spaced-repetition/fsrs4anki)
- [ABC of FSRS wiki](https://github.com/open-spaced-repetition/fsrs4anki/wiki/abc-of-fsrs)
- [fsrs PyPI](https://pypi.org/project/fsrs/)
- [Expertium benchmark](https://expertium.github.io/Benchmark.html)

The underlying theory — Bjork & Bjork 1992 retrieval-strength / storage-strength duality — is the academic backbone. FSRS is the implementation; spacing is the principle; retrieval practice is the mechanism. Three threads.

### The due-today counter as Zeigarnik closure — the load-bearing UI

Here is the part that surprised me and that I think the engineering instinct gets wrong. Quiz Me's adoption depends *not* on the algorithm's sophistication but on the *habit-formation UI* — specifically the due-today counter that drives users to return to the app and clear their queue.

The Zeigarnik effect (Zeigarnik 1927, summarized in Lewin's field theory): unfinished tasks produce a tension state that motivates completion. A visible counter of "you have 47 cards due today" creates and surfaces the Zeigarnik tension. Anki users report — and the existing Medhavy habit research replicates — that the due-count is the load-bearing UI element. It is what they check. It is what they clear. It is what defines the habit loop.

The honest implication: **the algorithm is a small contributor to whether students adopt the tool at all. The due-count is load-bearing UI.** This is uncomfortable for the engineering-minded reader, because it implies that the most consequential design decision in Quiz Me is the placement and visibility of one number on the screen, not the latent-variable architecture underneath it. But the evidence (and the operational experience of Anki) point the same direction. If the counter is invisible or misplaced, the habit does not form. If the counter is clear and the queue is clearable, the habit forms and the algorithm runs in the background doing its work.

This is one of Chapter 11's open questions: is the Quiz Me habit loop driven by the due-count or the algorithm? Operationally, the platform should bet on both — and design the counter as if the counter is the product.

### Phase gate for Quiz Me

The Quiz Me phase gate uses **Y1 (temporal engagement pattern)** as the gating criterion. The system does not surface Quiz Me items for material the student has not demonstrated reading engagement with. The gate prevents the "quiz on material I haven't read" failure mode that produces frustration without learning.

The deeper gate is the *evidence-not-completion* principle. Quiz Me items advance from "due" to "mastered" not when the student gets them right once, but when the *retest* at the FSRS-scheduled interval shows the storage strength has consolidated. This is Y6 (retrieval strength decay) in operation. The gate is the measurement.

---

## 5. Glimmer — ill-structured problem, backwards-faded scaffolding

### What Glimmer is

Glimmer is the creative cumulative assignment mode. At the *session* level the student receives an ill-structured problem: design a clinical protocol, draft a research proposal, write a critique of a published paper. The problem has multiple valid solutions, no agreed evaluation criteria, and requires the student to *specify* the problem before solving it. At the *term* level, the pieces assemble into a substantial project the student did not know they were building. The emergence is the design move.

### Four constructs the chapter must not confuse

"Creative assignments" in EdTech vendor writing collapses four distinct constructs. The chapter has to keep them separate.

**Generative Learning Activities (GLA).** Wittrock 1974; Fiorella & Mayer (2016, [*Educational Psychology Review* 28(4)](https://link.springer.com/article/10.1007/s10648-015-9348-9)). Eight activities — summarize, map, draw, imagine, self-explain, teach, enact, self-test. Self-explanation is the largest effect (*d* ≈ 0.55 on both retention and transfer).

**Elaborative Interrogation (EI).** Pressley et al. 1987, 1992. The "why is this true?" technique. Dunlosky et al. (2013, [*Psychological Science in the Public Interest* 14(1)](https://journals.sagepub.com/doi/10.1177/1529100612453266)) rated EI as moderate utility. Effect sizes typically *d* = 0.40 to 0.75 on delayed retention of factual material.

**Ill-Structured Problems (ISP).** Jonassen 1997, 2000. Multiple-solution, contested-criteria problem-solving. Belland et al. (2017, [scaffolding meta-analysis, *Review of Educational Research* 87(2)](https://journals.sagepub.com/doi/10.3102/0034654316670999)) — *g* = 0.46 for computer-based scaffolding on STEM cognitive outcomes.

**Project-Based Learning (PBL).** Hmelo-Silver 2004 synthesis; Chen & Yang (2019, [*Educational Research Review* 26: 71–81](https://www.sciencedirect.com/science/article/abs/pii/S1747938X18301027)) — *g* = 0.71 versus traditional instruction, with duration and technology support as moderators.

Glimmer at the *session* level is most cleanly an ISP. Its rubric (WHY / usefulness / mechanism / defensibility / specificity) maps onto Jonassen's defensibility-of-reasoning criterion. Glimmer at the *term* level is closer to PBL — but with a critical divergence. **In PBL the driving question is announced at the start; in Glimmer it is hidden until weeks 10–11.** This divergence means the Chen & Yang 2019 effect size for PBL does not directly transfer to Glimmer. I want to flag this honestly: the term-level emergence is a design bet borrowed from emergent-portfolio writing pedagogy, not from a meta-analyzed PBL effect.

### The novice anxiety failure mode

The most documented Glimmer failure: novices presented with ill-structured problems before they have prerequisite structure crash into anxiety and disengage. The design-education literature on STEM students transitioning to open-ended paradigms documents this extensively. The empirical signature: 60% of students abandoning the mode in week 2 is not unusual when the scaffolding has not been built in.

The mechanism: ill-structured problems require the learner to *specify* the problem before solving it. Specification requires prior framework. A novice without framework cannot perform the specification move productively. The anxiety is the metacognitive signal of "I cannot make progress and I do not know how to make progress" — a different state from "this is hard and I'm working through it."

### Backwards-faded scaffolding — the design response

Atkinson, Renkl & Merrill (2003, "Transitioning from studying examples to solving problems: Effects of self-explanation prompts and fading worked-out steps," [*Journal of Educational Psychology* 95(4): 774–783](https://doi.org/10.1037/0022-0663.95.4.774)) `[verify exact pagination and DOI]` is the canonical citation for backwards-faded scaffolding. The idea: a problem is initially presented with *all steps worked out*. The student studies the worked solution. Later versions of similar problems are presented with the *last step missing*, requiring the student to complete it. Then the *last two steps* missing. And so on, with the scaffolding fading *from the back* of the solution toward the front. By the time the student is solving from scratch, they have built the framework by working backwards from the end state.

The pedagogical mechanism: each fading step asks the student to perform exactly one new cognitive operation in a context where every other operation is already supported. Cognitive load is bounded (Sweller). The anxiety failure is prevented because the student is never asked to perform an operation they have no scaffold for.

Renkl on worked examples more generally (Renkl 2014, [*Cognitive Science* 38(1)](https://doi.org/10.1111/cogs.12086)): worked examples produce reliably stronger learning than equivalent time on problem-solving alone, particularly for novices. Effect sizes typically 0.5–1.0 SD on near-transfer.

For Glimmer specifically: the weeks 1–3 design must include backwards-faded worked examples of *the Glimmer rubric being satisfied*. The student is not asked to produce a well-defended design from scratch in week 1. They are asked to evaluate a fully-worked example, then to complete the last move on a partially-worked example, then to take more of the work on each successive Glimmer. **The fading is the scaffolding.**

This is one of Chapter 11's open questions: does backwards-faded scaffolding prevent the anxiety collapse in novice Glimmer users? It is a design bet anchored in worked-examples evidence, but the specific application to a term-long ill-structured project sequence has not been directly tested.

### Pea 2004 on scaffolding withdrawal

Pea (2004, "The Social and Technological Dimensions of Scaffolding," [*Journal of the Learning Sciences* 13(3): 423–451](https://www.tandfonline.com/doi/abs/10.1207/s15327809jls1303_6)) pulled the term *scaffolding* back to its original Wood, Bruner & Ross (1976) meaning: *temporary* support, calibrated to the learner's current need, withdrawn as competence grows. **Permanent scaffolding is not scaffolding. It is dependency.** The EdTech failure mode Pea named is systems that treated scaffolding as a permanent feature ("we have scaffolds!") rather than as a transient one.

For Glimmer: the AI reviewer's questions must be *contingent* on what the learner produced (not a generic checklist), must *reduce in support* as the learner's framing matures (not constant pressure on every dimension every week), and must *transfer* — the learner who has done ten Glimmers should be able to ask themselves the reviewer's questions without the reviewer present. Puntambekar & Hübscher 2005 — systems with full contingency-and-fading scaffolding produced reliably larger learning gains than systems with initial-support-only. The effect was particularly strong on transfer.

### Phase gate for Glimmer

The Glimmer phase gate uses **Y7 (scaffolding response curve)** as the gating criterion. The system does not surface a Glimmer for a concept until the student's prior performance shows hint-responsive understanding. This prevents the novice-anxiety failure *structurally* — a student whose Y7 is low for the concept has no underlying framework, and the Glimmer would ask for specification work the student cannot perform productively.

The deeper gate is the curriculum-design specification: each Glimmer's rubric includes scaffolding elements that fade per the Atkinson-Renkl design, and the AI reviewer's intervention level is contingent on the learner's prior Glimmer performance.

---

## 6. Phase gates as measurement decisions

The chapter's structural argument is that phase gates are not pedagogical decisions in the usual sense. They are *measurement decisions*. Each gate uses a specific GLP signal from Chapter 5 as the gating criterion:

- **Quiz Me gated until section read** — uses **Y1 (temporal engagement pattern)**. The student must have demonstrated reading engagement before retrieval practice is appropriate.
- **Glimmer gated until concept built** — uses **Y7 (scaffolding response curve)**. The student must show hint-responsive understanding before ill-structured problem-solving is appropriate.
- **Case Study gated until representation sufficient** — uses **Y3 (cross-context transfer)** plus **Y6 (retrieval strength decay)**. The student must be able to apply the concept outside instructional context, and the concept must be in storage rather than transient performance.
- **Ask AI not gated, but bounded by context-anchoring.** Ask AI is the *entry* mode and is always available — but the response is *constrained* by the prerequisites graph. If the student is asking about a concept whose prerequisites they have not built, the Ask AI response routes them to remediation rather than answering the surface question.

The phase-gate framework is a closed-loop architecture: the GLP signal from the measurement layer informs the mode-selection decision; the mode selection generates the learning interaction; the learning interaction produces a new GLP signal; the next phase-gate decision uses the updated signal.

This is what makes the four modes a *system* rather than a *menu*. **A menu lets the learner pick — and the learner will pick the mode that feels easiest, which is the fluency trap restated at mode level.** The phase-gate system selects on the learner's behalf, using evidence the learner does not have direct access to. The platform knows what the student does not. This is the same uncomfortable claim Chapter 5 had to land, restated at the mode-selection level.

---

## 7. Worked example — pharmacokinetics across the modes

*(Illustrative — composite, not deployed data. Labeled as such.)*

A medical student, working through a pharmacokinetics concept across multiple sessions. The concept: linear versus nonlinear (Michaelis-Menten) pharmacokinetics.

**Session 1 — Ask AI to clarify a prerequisite.** The prerequisite graph flags that linear-versus-nonlinear depends on Michaelis-Menten enzyme kinetics, which the student's profile shows as "weak Y6 — high initial performance, sharp decay." Ask AI is context-anchored to the Michaelis-Menten section of the biochemistry textbook, hint-only mode. The student asks: *"Why does saturation matter for drug dosing?"* The Ask AI response asks back: *"What did the Michaelis-Menten kinetics tell you about reaction rate at high substrate concentrations?"* The student attempts the answer. The system logs the response and the confidence rating; Y4 (uncertainty calibration) is updated; Y5 (texture) is updated (the question was specific, the surprise reaction was present when the student noticed that the dosing implication was non-obvious).

**Measurement transition.** Y1 logs reading engagement on the prerequisite section. Y2 logs a known misconception about clearance kinetics (the student conflated zero-order with first-order behavior at saturation). The misconception is in the curriculum design layer's library, so it is recognized rather than novel.

**Session 2 — Quiz Me on the core mechanism.** The Y1 gate confirms reading engagement on the pharmacokinetics section. Quiz Me items on linear-versus-nonlinear are scheduled by FSRS. The due-today counter shows 12 items. The student clears the queue. The Y6 retest at 7 days will confirm storage strength.

**Measurement transition.** Y6 retest at 7 days shows 85% retention on the core items. The Y3 transfer cue — a problem framed in terms of phenytoin dosing rather than the textbook's lidocaine example — produces 70% performance, within the population norm for the concept. The student has demonstrated *cross-context transfer* on the underlying mechanism.

**Session 3 — Case Study on a drug interaction scenario.** The Y3 + Y6 gates for Case Study are satisfied. The system surfaces a pre-written, faculty-reviewed case study on warfarin-amiodarone interaction. The case has a decision point (which dose adjustment, with what monitoring schedule) and a consequence (the bleeding risk if the dose is not adjusted). The AI facilitator asks Socratic questions: *"What did your previous analysis of CYP3A4 inhibition predict about the half-life change?"* The student's reasoning is the assessable product; the verdict is less important than the defensibility of the reasoning.

**Measurement transition.** The case interaction adds Y5 texture (multiple specific questions about CYP isoforms, position changes as the student updates their interaction prediction). The composite GLP score on this concept is now high. The student has demonstrated the representation under application.

**Session 4 — Glimmer: design a dosing protocol.** Week 8 of the course. The student's Y7 (scaffolding response curve) for the underlying concepts is in the hint-responsive range. The Glimmer surfaces: *design a dosing protocol for a patient with renal impairment, on warfarin, requiring amiodarone for atrial fibrillation.* The rubric: name the drug-drug interactions and their direction; specify the monitoring schedule and the decision rule for dose adjustment; defend the choice of starting dose given the renal function. The AI reviewer asks *contingent* questions — if the student named CYP3A4 inhibition but not P-gp, the reviewer asks *"what else might be at play?"* rather than *"you missed P-gp."* The scaffolding is the design.

At each mode transition, the measurement layer captures the GLP signals. The engine (Chapter 7) uses the signals to update the per-learner reward function for this concept and these modes. The next session begins with an updated policy.

---

## 8. Common misconceptions

**"The four modes are just four different things the student can do. The student should pick what they want."**
*Why it fails.* The student picking what they want is exactly the failure mode the phase gates prevent. The fluency trap from Chapter 5 is restated here: a learner left to pick the mode that feels best will pick the mode that produces the most immediate fluency, which is the mode least likely to produce durable learning at this stage. Phase-gating is what makes the four modes a *system* rather than a menu. The platform knows things about the learner's state — the Y6 decay rate, the Y7 hint-response — that the learner does not have access to. Using that knowledge to gate the mode is the design move; offering a menu is the absence of the move.

**"Phase gates are paternalistic. The platform is deciding for the student."**
*Why it fails — but only partially.* The objection has a real edge. A platform that gates aggressively can become coercive, and the line between gating and coercion is not trivially drawn. The honest framing: gates are *decisions about what to surface*, not decisions about what to forbid. A student who wants to ask AI about a concept whose prerequisites they have not built can still ask. The Ask AI response will route them to remediation. A student who wants to attempt a Glimmer before they have demonstrated hint-responsive understanding of the underlying concept will see a notice rather than the Glimmer. The platform's bet is that the routing produces better learning than the unconditional access; the routing is contestable and should be revisable as deployment evidence accumulates. Y1 and Y7 thresholds should be tunable per learner population. Gating is a design choice that has to earn its place every deployment. It is not a moral claim.

**"FSRS is well-validated. If Quiz Me uses FSRS, the learning gains are well-validated."**
*Why it fails.* This conflates three layers. Retrieval practice as a *mechanism* is well-validated (Adesope 2017 meta-analysis, *g* ≈ 0.67 in classroom settings). Spacing as a *principle* is well-validated (Cepeda 2006 meta-analysis, 839 assessments). FSRS as an *algorithm* is well-validated on its own benchmark target — it schedules better than SM-2 against a target retention rate, by about 20–30% fewer reviews. The claim "FSRS produces better *learning* than SM-2" is a reasonable bet from the better-scheduling claim, not a directly demonstrated finding. The three should not be collapsed. Vendor writing collapses them constantly. The chapter does not.

---

## 9. Exercises

**6.1 — (Apply.)** Choose a learning objective in a domain you know well. Specify a mode sequence — which mode comes first, what evidence triggers the transition to the next mode, and what failure mode each transition prevents. Your answer should name a specific GLP signal at each phase gate and explain why that signal is the right gating criterion for that transition. *(Produces something — required by chapter anatomy.)*

**6.2 — (Evaluate.)** A Glimmer deployment in an introductory biochemistry course shows 60% of students abandoning the mode in week 2. Diagnose the failure mode using the framework in this chapter. Specify the scaffolding correction in three parts: (a) the Y7-based phase gate that should have been in place; (b) the backwards-faded design that the weeks 1–3 sequence should have implemented; (c) one diagnostic the deployment team should look at to confirm the diagnosis is right before applying the correction.

**6.3 — (Analyze.)** A Quiz Me deployment in a pharmacology course shows high session scores (90%+ on initial Quiz Me items) but poor retention at 30-day re-assessment (40%). Which GLP component is the diagnostic? What does the pattern suggest about the FSRS scheduler's configuration — and what does it suggest about whether *FSRS itself* is the problem, versus *the gating evidence the scheduler is operating on*?

---

## What would change my mind

If a head-to-head deployment trial showed that a *menu-based* four-mode system (student chooses mode each session) produced GLP-equivalent durable-learning outcomes to a *phase-gated* four-mode system, the phase-gates-as-measurement-decisions argument would not survive. The gating discipline would be added cost without added signal. I do not expect this — the fluency-trap evidence and the menu-selection bias argument predict the gated version outperforms — but the comparison has not been run, and a clean null result is the empirical finding that would force a rewrite of Section 6.

Equally: if the backwards-faded Glimmer scaffolding sequence in weeks 1–3 did *not* prevent the novice anxiety collapse — if abandonment rates remained near 60% after the worked-example fading was in place — the design response in Section 5 would be wrong. I would have to either restructure the Glimmer to be a much later-stage mode entirely or rethink what the scaffolding has to look like for ill-structured term-long projects.

## Still puzzling

1. The literature has not separated *context-anchoring* from *hint-not-answer discipline* in the Ask AI variable. Medhavy bundles them. Does context-anchoring alone convert GPT-Base to GPT-Tutor success, or is the discipline necessary independently? An A/B inside the platform could be a publishable result.
2. Is the Quiz Me habit loop driven by the *due-count counter* or by the *algorithm's scheduling*? Operational experience says the counter; algorithm researchers tend to assume the algorithm. Both are likely contributing, but the relative weights matter for design priorities on the next platform iteration.
3. The solo-asynchronous-AI-facilitated Case Study variant inherits its design discipline from Thistlethwaite-style group-human-facilitated CBL. Does the AI facilitator actually implement the defensibility-of-reasoning criterion the human facilitator implicitly enforces? Or is something specific to the human conversation that the AI version cannot replicate?
4. The Glimmer term-level emergence (the driving question hidden until weeks 10–11) diverges from PBL's announced-driving-question structure. Does the surprise pay off in motivation and integration, or does it produce confusion that depresses persistence? The PBL effect sizes do not transfer here.

## Bridge to Chapter 7

The modes are the engine's arms. **Chapter 7 delivers how the engine learns which arm to pull** for which learner on which concept — and why that learning requires the measurement layer Chapter 5 specified. The bandit formalism (Robbins 1952 plus Thompson 1933, contextual bandits, within-learner adaptation, the reward function specification that does not silently drift toward engagement) is the next chapter's load-bearing material. The modes are what the engine selects among; the engine is what selects.

---

**Tags:** Ask AI · Case Study · Quiz Me · Glimmer · FSRS · context-anchoring · phase gates · Bastani PNAS 2025 · Thistlethwaite CBL · backwards-faded scaffolding · Zeigarnik · due-today counter
