# Chapter 13 — The Design Conversation


## TL;DR

- Here is what happens when someone opens a design tool and types the wrong first sentence.
- The chapter moves through What this book has been doing, Two things called Medhavy, What the tool requires from the human, The six moves, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

*The tool amplifies the thinking. It does not replace it.*

---

Here is what happens when someone opens a design tool and types the wrong first sentence.

They type: *"Suggest 15 chapters for a medical school pharmacology textbook."*

The tool produces 15 plausible-sounding chapter titles. The author accepts them. The adaptive engine now has a concept map with no prerequisite dependencies — chapter 7 may require chapter 12 for any given concept. No learning-outcome statements — the chapters are topics, not capabilities. No phase-gate logic — the modes have nothing to gate on. No mode-appropriateness flags — whether a concept warrants Quiz Me or Glimmer or Case Study has no answer.

The engine runs. Sessions are logged. The dashboard looks fine. Students engage. Nothing is learned, and the dashboard cannot see it, because engagement is all the dashboard was built to measure and engagement is all the specification gave it.

This is the IDK-IDK problem — the Khanmigo pattern from Chapter 1 — restated at the curriculum-design layer. A platform produced from "suggest 15 chapters" is a platform that will measure engagement as learning because there is nothing else for it to measure against. The failure is silent, which is the worst kind.

This chapter is about the question that should have come before "suggest 15 chapters." Not the architecture — you have that. The conversation that produces the inputs the architecture needs before anyone writes a line of code.

---

## What this book has been doing

I want to name something that has been true since Chapter 1 and that this chapter finally says out loud.

This book is a design conversation.

Every chapter has been doing the thing the chapter is now describing. Chapter 1 opened with a failure before any framework was introduced — the IDK-IDK incident, a real system producing a measurable harm, held up so the reader could feel the problem before being handed the solution. Chapter 4 walked the evidence base before any architecture chapter could cite it, because the architecture should not be trusted until the evidence that licenses it is visible. Chapters 5 through 10 delivered the four-layer architecture with the evidence at every decision point, in the sequence that makes each layer comprehensible given what precedes it — not in the sequence that would have been easiest to write. Chapter 11 named the gaps. And each chapter closed with what would change the author's mind, which is the only honest way to end a chapter making claims the evidence does not yet fully support.

That sequence is the design conversation. Intake before architecture. Evidence before specification. Honest inventory before the map. The methodology is not new material introduced in this chapter. It is the instrument the book has been operating with throughout. You have already done it. The architecture you now hold was produced by it.

A reader who learned the methodology by reading about it has acquired vocabulary. A reader who experienced it through twelve chapters has acquired a capability. The chapter's job is to make the capability explicit enough to run.

---

## Two things called Medhavy

There is a confusion that has been sitting since Chapter 1, and this is where it gets dissolved.

**Medhavy the platform** is what the developer builds. The four-layer architecture deployed at a specific URL — the production system serving medical students or education-policy graduate students, instrumented by GLP measurement, optimized by the within-learner bandit, with Ask AI and Quiz Me and Case Study and Glimmer running against a faculty-reviewed content layer.

**Medhavy the instrument** is what the domain expert uses to produce the specification the developer builds from. The design conversation tool — the intake-driven session that walks the commissioning party through learner profile, complexity threshold, evidence audit, four-layer specification, economics check, and honest inventory, and produces a document a developer can build from without a translation meeting.

They share a name because they share a structure. Both are conversations that produce learning trajectories. The platform's conversation is between AI and student about a concept. The instrument's conversation is between AI and domain expert about a curriculum. The shape of the question-by-question intake is the same. The output differs — student understanding in one case, buildable specification in the other.

![Two-column parallel structure ](images/13-the-design-conversation-fig-01.png)
*Figure 13.1 — Two-column parallel structure *

A Charles Fadel type who confuses the two will commission the wrong thing. He will ask the developer to build "Medhavy" without specifying which Medhavy or what the specification is. The developer will build the platform without the specification — the "suggest 15 chapters" outcome writ large. A developer who confuses the two will build the platform and assume the design conversation will happen later, somewhere else, by someone else. It will not. The design conversation does not happen later. It happens before the build or it does not happen at all. A platform configured against an unspecified curriculum is the platform that cannot learn.

---

## What the tool requires from the human

The most important thing to understand about the instrument is what it cannot do.

The instrument can produce the architecture. It can read the intake answers, infer the concept-map structure, name the phase gates that would be coherent given the stated learning outcomes, flag the prerequisite chains, propose the mode assignments, surface the measurement signals each phase gate requires, and produce the specification document in the format the developer needs.

What it cannot do is generate the domain expert's understanding of what students get wrong.

Sadler et al. 2013 — the middle-school physical science study from Chapter 10 — is the empirical anchor.[^1] The teachers who could identify the wrong answers their students would predictably give produced substantially larger learning gains than teachers who could not, controlling for subject-matter knowledge itself. The diagnostic move — knowing what *learners in this domain* get wrong — is what carries the effect. The LLM has training-data inferences about common misconceptions in well-documented subjects: Newtonian mechanics, Bayesian probability, photosynthesis. It does not have the domain expert's tacit knowledge of *this* population's specific bottlenecks. That knowledge is the input the tool requires and the input it cannot produce on its own.

The cleanest framing: the tool can produce the architecture but not the misconception map. The domain expert produces the misconception map and uses the tool to amplify it into the architecture. That is the labor separation.

![Two-box division of labor ](images/13-the-design-conversation-fig-02.png)
*Figure 13.2 — Two-box division of labor *

Cost collapse at the content layer shifted the binding constraint from production to expert knowledge — from *can we afford to write this* to *do we know what students get wrong here*. The same shift happens at the implementation layer. Cost collapse on code shifts the binding constraint from writing code to specifying what the code should do. What becomes valuable when production gets cheap — at both the content layer and the code layer — is the human's contextual knowledge of what to produce. The Sadler 2013 move has a mirror in the implementation. The instrument is the same kind of thing in both cases: a conversation that converts human judgment into structured input the cheap-production layer can act on.

---

## The six moves

The design conversation runs in six moves. They are the same six moves the book has been modeling since Chapter 1, now named.

**Move 1: Learner profile.** One specific person, not a category. Age. Prior knowledge. Prior misconceptions. Current capability gap. Motivation type — academic credential, professional qualification, intellectual project. Institutional context. The reader cannot be named is a reader the book cannot be written for. This is the discipline that produces Priya from Chapter 1 — not "adult learner in a BPO preparation program" but a nineteen-year-old in Hyderabad with an Anki deck and an Apollo Health interview in eleven days.

**Move 2: Complexity threshold.** Three questions from Chapter 2. Is adaptive sequencing required across concepts that cannot be pre-ordered? Is live instrumentation required — is the evidence of learning observable in the process, not just the final answer? Is a multi-layered capability build required? If all three answers are yes, the full architecture is warranted. If any answer is no, the right answer may be a simpler tool. The complexity threshold is not a gate against the architecture. It is the honest check that prevents the architecture from being commissioned for problems that do not need it.

**Move 3: Evidence audit.** Walk the evidence base relevant to the design choices the architecture will require. Distinguish what Khan uses, what Horvath uses, what both omit. Apply Hattie's 0.40 correctly — as a cost-effectiveness guideline, not a threshold. Apply the five-move audit from Chapter 4 to any claim that will bear structural weight. Produce the evidence ladder: which design choices are direct-evidence-supported, which are adjacent-evidence-supported, which are bets.

**Move 4: Four-layer specification.** Content layer — domain-specificity level, AI-generation policy, faculty review gate, minimum viable content per chapter. Curriculum design layer — concept map with nodes, prerequisite dependencies, Bloom's-level assignments, mode-appropriateness flags, phase-gate logic per mode per concept. Adaptive engine — bandit configuration, context features, reward signal, exploration strategy, cold-start defaults. Measurement layer — which GLP components are instrumented, what threshold values trigger phase-gate transitions or engine updates, what the consent architecture commits to and does not.

**Move 5: Economics check.** What audience size justifies the architecture at the available production budget? Where does the cost-collapse argument apply, and where does it leave the burden of proof unchanged? A specification that requires Project C investment at a Project A budget is a specification that does not get built. The economics check is the gate against over-commitment.

**Move 6: Honest inventory.** Three categories per design decision: adjacent evidence — what the literature on partial designs supports; direct evidence — what exists on the integrated claim under deployment conditions; bet — what the design commits to without sufficient evidence and what the deployment will test. A specification without an inventory is a specification that has not acknowledged what it is committing to without evidence. Which is the IDK-IDK problem at the design-conversation level.

![Horizontal six-step sequence ](images/13-the-design-conversation-fig-03.png)
*Figure 13.3 — Horizontal six-step sequence *

---

## What the map contains

The output the design conversation produces is a document. The structure per design decision:

**WHAT** — the specific decision. "Quiz Me phase-gate at section-read threshold of three minutes."

**WHY** — the reasoning anchored in evidence. Bastani 2025 for the guardrail-design decision.[^2] Cepeda 2006 for the spacing-interval decision.[^3] Sadler 2013 for the priority-weighting decision. The WHY field is where the evidence audit lands per decision.

**HOW** — the implementation specification. Exact field values, exact threshold numbers, exact mode-selection rules.

**ENVIRONMENT** — the dependencies. Which measurement signals the engine requires. Which content elements the curriculum requires from the content layer. The cross-layer interface specification.

**RESULTS expected** — pre-registered prediction of what the design produces. What the engine should converge on after N sessions. What the GLP signal should look like after the phase-gate transition.

**QUESTIONS** — the open bets per design decision. What this decision commits to without direct evidence. What the deployment will test.

The map is auditable. A developer reading it can implement. A Charles reading it can evaluate. A specification missing any field per design decision is incomplete in the same sense that a lab notebook with missing entries cannot pass review: the missing field cannot be reconstructed from the rest.

| Item | Meaning |
| --- | --- |
| Single-decision map template | six rows, each showing field name, a brief description of what belongs there, and a worked example drawn from the chapter (using the Quiz Me phase-gate example): WHAT |
| WHY | "Bastani 2025 |
| Cepeda 2006 | spacing requires prior encoding" |
| HOW | "Y1 temporal-engagement signal ≥ 3 min on section → Quiz Me unlocked |
| FSRS schedules first item 24 hr after gate opens" | exact implementation |
| ENVIRONMENT | "Requires Y1 from measurement layer |
| requires substrate text from content layer" | cross-layer dependencies |
| RESULTS expected | "Engine converges on 85%+ retention at 7-day probe within 3 sessions per concept" |
| QUESTIONS | "Does Y1 threshold correctly distinguish read vs. skimmed? Open Question 4 from Ch. 11" |

The test the map has to pass: can a developer who was not in the design conversation build from it without asking a question? If yes, the design conversation succeeded. If no, the specification is incomplete, and identifying which of the six moves failed to produce sufficient detail is the exact kind of diagnostic this book has been training the reader to do.

---

## The shared vocabulary

The design conversation produces something besides a specification document. It produces a shared vocabulary between the commissioning party and the developer.

Without the vocabulary, every new pairing has to reinvent the terms that the previous pairing invented. With it, the conversation can happen across teams, across institutions, across years. The commissioning party can say *"Socratic is wrong here because of the assistance dilemma"* — and mean the specific finding from the ITS literature that the hint-not-answer guardrail addresses. The developer can say *"we already have something close — here's what the context-anchoring layer does for the prerequisite-classification problem"* — and mean the specific architectural decision from Chapter 7. Both are talking about the same design decision in the same terms.

The lexicon owns thirteen terms: the IDK-IDK problem, the four layers, the four modes, the seven GLP signals, phase gates, the within-learner bandit, the GLP reward signal, ambient infrastructure, the conductor, the fluency trap, the cost-collapse asymmetry, the due-today counter, and Genuine Learning Probability. Appendix A specifies all thirteen. The chapter's claim about the vocabulary is operational: both readers should be able to say the same sentence about the same decision in the same vocabulary by the end of the book. If they cannot, something in the book failed to deliver.

---

## The build is the 20%

There is a framing in the agentic-coding discourse of 2025 that the chapter inherits without making a fetish of it. The senior engineer spends roughly 80% of her time on thinking — research, planning, designing the right solution, interpreting results — and roughly 20% on writing code. Addy Osmani puts the sharpest version of this in the agentic-coding context.[^4] Greg Brockman at OpenAI noted that AI went from writing 20% to 80% of code in a single month. The framing is now distributed enough to treat as a field formulation rather than a quotation from a single source.

The map the design conversation produces is the 80%. The Gru-assisted build — Claude Code, or any agentic-coding assistant, executing against the specification — is the 20%.

The structural parallel to Chapter 10 is the chapter's deepest claim. Cost collapse on content shifted the binding constraint to expert knowledge of what students get wrong. Cost collapse on code shifts the binding constraint to specification quality. A commissioning party can now have a production-grade intelligent textbook built at a cost that was unthinkable five years ago, provided he can produce the specification. The instrument's job is to help him produce it.

The implementation book — what the specification becomes when a developer builds against it — is the follow-up that does not yet exist. This book ends with the map. The next book begins with the build.

---

## What the conversation looks like

The worked case. Charles Fadel has content on 21st-century skills and curriculum redesign. He wants to commission an intelligent textbook for graduate students in education policy.

**Intake question 1: Who is the learner?**

Charles answers: graduate students in education policy programs, mid-career, classroom or administrative experience, working toward a credential, skeptical of jargon, have read either too much Hattie or too little.

The instrument captures: motivation = professional credential plus intellectual project; prior knowledge = uneven and practitioner-weighted; misconception risk = treating Hattie's 0.40 as a binary threshold; institutional context = credentialed graduate program.

**Intake question 2: What capability are they being built toward?**

Charles answers: they have to be able to evaluate a proposed curriculum reform — examining the evidence base, the audience, the cost, the institutional fit — and decide whether to support it. Evaluate level is the real target.

The instrument captures: Bloom's primary level = Evaluate; target capability = evidence-base assessment plus audience-fit reasoning plus cost-benefit comparison plus institutional-fit assessment.

**Intake question 3: What is the deployment context?**

Charles answers: asynchronous, part-time, laptop at night, course already exists as a Canvas shell with PDFs and discussion forums.

The instrument captures: deployment = LMS-embedded; asynchronous; existing course structure.

**The learner profile the intake produces:**

*The learner is a 38-year-old assistant principal at a Title I middle school in a state with active AI-in-classroom legislation. She enrolled in the master's program because she keeps being asked to evaluate vendor proposals and she does not trust her own evidence-evaluation. She has read Hattie's first book and an old copy of Marzano. She has not read Horvath. She studies at night on a laptop after her kids are asleep. She has 90 minutes per session, three sessions a week. Her current evidence-evaluation move is "trust the colleague who recommended it."*

**Complexity threshold:**

All three answers are yes. Adaptive sequencing is required — the prerequisite chain from effect-size literacy to audience-fit reasoning to cost-effectiveness comparison to institutional fit cannot be pre-ordered without losing learners who arrive at different starting points. Live instrumentation is required — the target capability is evaluative reasoning, observable in the process of working through cases, not in a single final answer. A multi-layered capability build is required. Full architecture warranted.

**Layer 2 specification, one module excerpted:**

Module 1 — "Effect Sizes and What They Don't Tell You."

Node 1.1: Effect size definition (Bloom: Understand; mode: Ask AI with context-anchoring; prerequisite: none). Node 1.2: Effect size magnitude interpretation (Bloom: Understand; mode: Quiz Me with priority weighting; prerequisite: 1.1). Node 1.3: Effect size versus practical significance (Bloom: Analyze; mode: Case Study on a pre-written faculty-reviewed case; prerequisites: 1.1, 1.2). Node 1.4: Cherry-picking the literature (Bloom: Evaluate; mode: Glimmer with backwards-faded scaffolding; prerequisites: 1.1, 1.2, 1.3).

Phase gates: Quiz Me on 1.2 gates on the temporal-engagement signal showing the learner has actually read 1.1. Case Study on 1.3 gates on the retrieval-strength-decay signal showing 1.1 and 1.2 have consolidated through a seven-day spacing interval. Glimmer on 1.4 gates on the cross-context transfer signal showing the learner can apply 1.3 to a case the Case Study mode did not cover.

![Four-node prerequisite graph for Module 1 ](images/13-the-design-conversation-fig-04.png)
*Figure 13.4 — Four-node prerequisite graph for Module 1 *

This is what one module looks like. The full specification covers roughly 80 nodes for an eight-week module, at this level of detail per node. The instrument generates the document. Charles audits it. The developer builds from it.

**Economics check:**

Target audience approximately 1,200 graduate students per cohort across partner programs. Production budget $120K. Budget tier between Project A and Project B. Subset feasible at this budget: all four layers at minimum viable scope; 80 concept nodes rather than 200; GLP instrumented at three components rather than seven; Case Study with pre-written content only; Glimmer with rubric review but no AI pre-grading.

**Honest inventory, excerpted:**

Ask AI with RAG-grounded context-anchoring: adjacent evidence (Bastani 2025, VanLehn 2011), bet on the specific context-anchoring claim. Quiz Me with priority weighting: adjacent evidence (Sadler 2013, spaced retrieval canon), bet. Glimmer with backwards-faded scaffolding for novice users: adjacent evidence (Belland et al. 2017), bet. Solo asynchronous AI-facilitated Case Study: adjacent evidence (Thistlethwaite 2012), bet.

The bets are named. The deployments that will test them are specified. The inventory is honest.

---

## What would change my mind

A deployment in which a developer outside the original team built a specified intelligent textbook from the map alone — without a translation meeting with the design conversation participants — and the build survived audit against the specification, would convert the chapter's claim from *current best reading* to *demonstrated capability*. If the developer could build only with translation meetings, the specification format is missing something the chapter has not identified. If the developer could build from the map but the build failed audit — if what got built was not what the specification described — the failure points to underspecification or to the developer's reading discipline. Either way the claim would have to be revised.

Whether the shared vocabulary holds across institutions rather than fragmenting per deployment is the book's own open question. If the Learning Engineering community adopts the lexicon, the conversation scales. If each new deployment re-invents the vocabulary, the methodology is captured rather than generalized. The chapter's claim about portability is falsifiable and not yet tested.

---

## Exercises

### Exercise 13.1 — Run a design conversation (Create)

Pick a real learning problem you would commission an intelligent textbook for. Run the design conversation:

(a) Conduct the intake. Specify the learner profile in one paragraph naming a specific person.
(b) Apply the complexity threshold test. Record the three answers.
(c) Walk the evidence audit. Identify three load-bearing citations.
(d) Specify the four-layer architecture for the deployment. Use the worked example in this chapter as the format.
(e) Run the economics check. Specify the budget tier and what subset of the architecture is feasible.
(f) Produce the honest inventory. Categorize each major design decision as adjacent-supported, direct-supported, or bet.

Hand the specification to a developer who was not in the session. Can they build from it without asking a question? If they ask a question, identify which of the six moves failed to produce sufficient detail and revise.

### Exercise 13.2 — Audit a specification (Evaluate)

Given the worked example from §8 of this chapter, or a specification you produce in Exercise 13.1, identify:

(a) Which layer is underspecified. Name the specific missing element.
(b) Which phase gates are missing. Specify what each missing gate should look like.
(c) Which measurement commitments are absent. Identify which GLP components are required to instrument the stated phase gates and which are not yet specified.
(d) What questions would a developer ask? List the questions and the specific specification gap each one indicates.

### Exercise 13.3 — Conduct the first three intake questions (Apply)

Charles Fadel has content on 21st-century skills and curriculum redesign. Run the first three intake questions for a design conversation on his intelligent textbook. For each question:

(a) Specify the question precisely.
(b) Specify what answer Charles would give. Be concrete — name the audience, the capability, the deployment context.
(c) Specify what the instrument captures from the answer.
(d) Identify what the specification still needs that the first three questions did not surface, and what the next intake question should ask to surface it.

### Exercise 13.4 — Test the shared vocabulary (Apply)

Pick a design decision from any chapter of this book. Write two sentences:

(a) A sentence Charles Fadel would say about the decision, using the lexicon from §6.
(b) A sentence a developer would say in response, using the same lexicon.

Then test the sentences. Hand them to someone who was not part of the book's construction — one practitioner, one developer. Can both parse the sentences using only the lexicon? If yes, the language scales. If no, identify the term that broke and specify what Appendix A needs to add.

### Exercise 13.5 — Specify a bet (Apply)

From the eight open questions in Chapter 11, pick the one most relevant to a deployment you would commission. Write:

(a) The bet in WHAT / WHY / HOW / ENVIRONMENT / RESULTS / QUESTIONS form.
(b) The specific instrumentation the deployment will use to test the bet.
(c) The pre-registered prediction. What result would confirm the bet? What result would falsify it?

A specification that names bets but does not specify how the deployment will test them is a specification that has not yet committed to learning.

---

## References

[^1]: Sadler, P. M., Sonnert, G., Coyle, H. P., Cook-Smith, N., & Miller, J. L. (2013). The influence of teachers' knowledge on student learning in middle school physical science classrooms. *American Educational Research Journal*, 50(5), 1020–1049. https://doi.org/10.3102/0002831213477680

[^2]: Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., & Mariman, R. (2025). Generative AI without guardrails can harm learning: Evidence from high school mathematics. *Proceedings of the National Academy of Sciences*, 122(26), e2422633122. https://doi.org/10.1073/pnas.2422633122

[^3]: Cepeda, N. J., Pashler, H., Vul, E., Wixted, J. T., & Rohrer, D. (2006). Distributed practice in verbal recall tasks: A review and quantitative synthesis. *Psychological Bulletin*, 132(3), 354–380. https://pubmed.ncbi.nlm.nih.gov/16719566/

[^4]: Osmani, A. (2025). The 80% problem in agentic coding. *Elevate Substack*. https://addyo.substack.com/p/the-80-problem-in-agentic-coding
