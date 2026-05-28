# Chapter 7 — The Four Modes


## TL;DR

- The platform's job is not just to deploy modes.
- The chapter moves through Ask AI — and why the wrapper is the variable, Case Study — the bet the evidence does not fully cover, Quiz Me — three threads that must not be collapsed, Glimmer — the anxiety failure, and its cure, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

*The platform's job is not just to deploy modes. It is to know which mode to deploy when.*

---

Here is a mistake that follows a predictable pattern, and I want you to see the pattern before I name the modes.

A school deploys a chatbot. Students who use it score higher on practice problems. The school is satisfied. The end-of-year exam arrives, and the students who used the chatbot score lower than students who did not. The school is surprised.

A school deploys a flashcard system. Students build streaks, clear their daily queues, feel productive. The shelf exam arrives, and the students cannot apply the concepts to patient scenarios they have not seen before. The school is surprised again.

A school deploys an open-ended creative assignment platform — what this book calls Glimmer. Sixty percent of students abandon it in week two. Nobody is quite sure why.

The pattern: **each tool works for something. Each tool fails when it is the only tool.** The chatbot makes practice easy, which is exactly the wrong thing to optimize when practice is supposed to be difficult. The flashcard system builds recall of practiced items, which is not the same as the ability to reason about unpracticed cases. The creative platform asks students to specify a problem before they have the conceptual framework to specify anything, which produces not learning but paralysis.

The name for this pattern is Maslow's hammer: if the only tool you have is a hammer, everything looks like a nail. The chapter works through four tools — Ask AI, Case Study, Quiz Me, Glimmer — and for each one does the same two things. It names what the tool is good for and it names its characteristic failure when it is the tool for everything. The phase gates are what the platform uses to deploy the right tool at the right time. They are the conductor's decision algorithm made explicit.

---

## Ask AI — and why the wrapper is the variable

Ask AI is the conversational mode. The student asks a question. The platform responds. The structure is close to a general-purpose chatbot, with two constraints that change everything: **context-anchoring**, where the model receives the current section, the student's prerequisite history, and the learner's state as injected context; and a **hint-not-answer guardrail**, where the model is constrained to ask questions and provide hints rather than supply the answer.

The evidence for what Ask AI can do sits in two literatures that must not be collapsed.

The first is the Intelligent Tutoring Systems literature from 1990 to 2020. VanLehn's 2011 meta-analysis is the canonical result: step-based ITS — systems that give feedback at each reasoning step, not just on the final answer — produce *d* = 0.76 against conventional instruction, statistically indistinguishable from human tutoring at *d* = 0.79.[^1] Answer-based computer-assisted instruction produces *d* = 0.31. The structural finding is worth holding: step-grain interactivity matters more than whether the tutor is human or machine. The machine that intervenes at each step is nearly as effective as the human who does the same thing. AutoTutor, a dialog-based natural-language tutoring system for Newtonian physics and computer literacy, produced *d* = 0.7–0.8 on deep comprehension — the closest ITS analog to a chatbot.[^2]

The second is the generative-AI literature from 2024 to 2025. I described the Bastani PNAS 2025 study in Chapter 4. The result is worth restating here in mode terms. Same GPT-4. Two prompt wrappers. GPT Base — the unguarded chatbot — produced a 48% in-session performance gain and a 17-percentage-point durable-learning loss. GPT Tutor — the teacher-designed wrapper — produced a 127% in-session gain and a statistically null durable-learning effect.[^3] The model did not change. The wrapper changed. The wrapper is the variable.

The pattern is bimodal. Unguarded AI produces negative durable outcomes. Pedagogically designed AI produces outcomes in the upper range of the ITS literature. The same technology, opposite results, depending entirely on what the wrapper tells the model to do.

![Two-column split ](images/07-the-four-modes-fig-01.png)
*Figure 7.1 — Two-column split *

Ask AI in Medhavy bets on the second pattern.

The context-anchoring design is the load-bearing mechanism. The candidate contexts run from cheapest to most expensive: section title only; current paragraph; chapter to this point; prerequisites graph; student state; full book. More context is not uniformly better. Liu et al. 2023 documented the "lost in the middle" effect: performance follows a U-curve along the position of relevant information in a long context, with significant degradation when the relevant passage is buried in the middle.[^4] Dumping the full chapter into context degrades the answer.

The Medhavy discipline: inject the current paragraph unconditionally; inject specific prerequisites on demand, retrieved against the prerequisites graph; avoid full-chapter dumps unless the question genuinely requires cross-section synthesis; place high-value context at the beginning and end; treat student state as a structured summary, not a transcript.

| cost | coherence benefit | lost in the middle" risk | Medhavy deployment decision |
| --- | --- | --- | --- |
| Context-anchoring tiers | rows ranked cheapest to most expensive: section title only | current paragraph | chapter to this point |

I want to flag one honest gap. The literature has not yet separated context-anchoring from hint-not-answer discipline as independent variables. Bastani's GPT Tutor result bundled teacher-designed hints with instructions to withhold answers. Medhavy bundles them too. An A/B inside the platform that varied one while holding the other constant could be a publishable result. It is Chapter 11's open question, not a settled design choice.

On hints specifically: the ITS literature has a name for the central problem. Aleven and Koediger called it the *assistance dilemma* — there is an optimum amount of help, below which the student fails and above which the student offloads rather than learns.[^5] Students misuse on-demand hint sequences by clicking through to the bottom-out hint (the one that reveals the answer) without engaging the earlier ones. The optimum is curvilinear and depends on prior knowledge. A single fixed prompt cannot be optimal for all students. Hint level should be a function of prior knowledge, current concept, and prior performance on that concept. This is one of the inputs the engine described in Chapter 8 learns over.

---

## Case Study — the bet the evidence does not fully cover

Case Study is the application-stage mode. A faculty-curated, pre-written case is presented after the student has demonstrated understanding of the underlying concepts. The student works through it alone. The AI serves as a Socratic facilitator — asking questions, prompting re-examination of evidence, surfacing considerations the student has not yet raised. The case has a defined learning objective, a decision point, and a consequence. The assessable product is the defensibility of the student's reasoning, not the correctness of the verdict.

The evidence base is Thistlethwaite et al. 2012, a systematic review covering 104 papers across medicine, dentistry, veterinary, nursing, midwifery, and allied health.[^6] The honest read: CBL is consistently associated with positive student satisfaction and self-reported gains in clinical reasoning. Objective evidence for factual knowledge gains is equivocal — no clear advantage over lecture-based instruction on factual assessment. Evidence on clinical reasoning skills shows a favorable trend, but most studies are pre-post designs rather than RCTs.

The implication: CBL is well-supported as an *application-stage* move. It is not supported as a *content-acquisition* move. This is why Case Study is phase-gated behind Quiz Me — the student needs to have demonstrated retrieval strength on the underlying concepts before a case can do its work.

Now here is the gap I want to name on purpose, because the chapter's discipline requires it. The Thistlethwaite review is on *group, live, human-facilitated* CBL. Small-group discussion led by a clinical educator. Medhavy's Case Study mode is *solo, asynchronous, AI-facilitated*. That is three differences from the tested intervention. The case structure — decision point, consequence, defensibility of reasoning as the product — is what Thistlethwaite's evidence supports. The delivery mode is a research bet. The bet: the AI facilitator can implement the defensibility-of-reasoning criterion by asking the structured questions a good human facilitator would ask. The bet may pay off. It is not Thistlethwaite's claim. Chapter 11 flags this as an open question and means it.

One additional design constraint the evidence supports: pre-written, faculty-reviewed cases, not on-demand AI-generated ones. An unreviewed AI-generated case can introduce a clinical error, a misconception, or a misframing that the student learns alongside the intended concept. The faculty review gate is the residual constraint that AI cannot yet reliably automate.

---

## Quiz Me — three threads that must not be collapsed

Quiz Me is the spaced retrieval practice mode. The student works through retrieval items on current and prior concepts, scheduled by FSRS. This is the most evidence-dense mode in the platform — and the mode most frequently mis-cited in vendor writing.

The mis-citation follows a pattern. Someone says: *"Quiz Me uses FSRS, an evidence-based algorithm for scheduling review at intervals that maximize durable retention."* That sentence is claiming three things simultaneously: that retrieval practice works as a mechanism, that spacing matters as a scheduling principle, and that FSRS is the right implementation of that principle. The first two are well-established. The third is established by a different kind of evidence than the first two, and collapsing them produces exactly the kind of inflated claim Chapter 4 taught you to audit.

The three threads, kept separate:

**Retrieval practice as mechanism.** Roediger and Karpicke 2006: at five minutes after study, repeated study beats testing. At one week, the order reverses — 40% retention after study-only, 61% after three test trials.[^7] The act of pulling information out of memory changes the memory. Adesope, Trevisan, and Sundararajan's 2017 meta-analysis: 188 experiments, practice tests versus re-studying *g* = 0.51, versus no activity *g* = 0.93, in classrooms specifically *g* ≈ 0.67.[^8] The mechanism is well-supported. Pan and Rickard 2018 established that the benefit extends to transfer — items the student did not directly practice — with a pooled effect *d* = 0.40 and larger effects in medical contexts specifically.[^9]

**Spacing as scheduling principle.** Cepeda et al. 2006: distributed practice consistently outperforms massed practice across 839 assessments. The optimal inter-study interval is a function of the retention interval, not a fixed value.[^10] Cepeda et al. 2008 showed the spacing advantage persists over retention intervals up to 350 days — the benefit does not decay over a year.[^11] The principle is well-supported.

**FSRS as implementation.** FSRS has been the default scheduler in Anki since November 2023. It represents each card with three latent variables: Difficulty, Stability (the number of days at which retrievability is predicted to fall to a target retention level), and Retrievability (the current predicted recall probability). After each review the user gives a 1–4 rating; the model updates Difficulty and Stability as a function of the rating, current Retrievability, and prior values. FSRS outperforms SM-2 on its own internal benchmarks: roughly 20–30% fewer reviews at equivalent target retention, with ±5.3% error against the target versus SM-2's ±16.2%.[^12]

Here is the honest limit: *"FSRS produces better scheduling"* is established. *"FSRS produces better learning"* is a reasonable bet from the better-scheduling claim, not a directly demonstrated RCT finding. The three should not be collapsed. Chapter 11 flags this as an open question.

![Three-tier vertical stack ](images/07-the-four-modes-fig-02.png)
*Figure 7.2 — Three-tier vertical stack *

---

Now here is the part that surprised me when I first looked at the operational data, and that I think the engineering instinct gets wrong.

Quiz Me's adoption depends not primarily on the algorithm's sophistication. It depends on the *habit-formation UI* — specifically the due-today counter that drives users to return to the app and clear their queue.

The Zeigarnik effect: unfinished tasks produce a cognitive tension state that motivates completion.[^13] A visible counter — *you have 47 cards due today* — creates and surfaces that tension. Anki users, and users in Medhavy's habit research, report the due-count as the load-bearing UI element. It is what they check. It is what they clear. It defines the habit loop.

The uncomfortable implication: the most consequential design decision in Quiz Me is the placement and visibility of one number on the screen, not the latent-variable architecture underneath it. If the counter is invisible or buried, the habit does not form. If the counter is clear and the queue feels clearable, the habit forms and the algorithm runs in the background doing its work. The algorithm matters for what happens once the student opens the session. The counter is what gets them to open it.

---

## Glimmer — the anxiety failure, and its cure

Glimmer is the ill-structured problem mode. At the session level the student receives a problem with multiple valid solutions, no agreed evaluation criteria, and a requirement to *specify the problem* before solving it: design a clinical protocol, draft a research proposal, write a critique of a published paper. At the term level the session-level pieces assemble into a substantial project the student did not know they were building. The emergence — the late revelation of the driving question — is a design choice borrowed from emergent-portfolio pedagogy.

The evidence base for what Glimmer is trying to do crosses three literatures. Fiorella and Mayer's 2016 catalogue of generative learning activities identifies self-explanation as the largest single-study effect (*d* ≈ 0.55 on both retention and transfer); teaching — Feynman's own discipline — as well-established; summarizing and drawing as domain-specific.[^14] Jonassen 1997 established the canonical distinction between well-structured and ill-structured problems: well-structured problems have constrained, convergent, finite-rule solutions; ill-structured problems have multiple solutions, uncertainty about which concepts are necessary, and no clean stopping criterion.[^15] Belland et al.'s 2017 scaffolding meta-analysis found *g* = 0.46 for computer-based scaffolding on STEM cognitive outcomes.[^16] Chen and Yang's 2019 meta-analysis found *g* = 0.71 for project-based learning versus traditional instruction, with duration and technology support as moderators.[^17]

I want to be honest about where the evidence ends and the bet begins. The Chen and Yang PBL effect size does not directly transfer to Glimmer's term-level design. In PBL the driving question is announced at the start. In Glimmer it is hidden until weeks 10 or 11. The surprise is a design bet borrowed from portfolio pedagogy, not from a meta-analyzed PBL effect. Chapter 11 names this directly.

What the evidence does license is the failure mode, which turns out to be the most important design constraint.

The failure is predictable. Sixty percent of students abandoning an ill-structured mode in week two is not unusual in the design-education literature when the scaffolding has not been built in. The mechanism: ill-structured problems require the learner to *specify the problem* before solving it. Specification requires a prior framework. A novice without framework cannot perform the specification move productively. The anxiety that follows is the metacognitive signal of *I cannot make progress and I do not know how to make progress* — which is a different state from *this is hard and I'm working through it*. The second state is generative. The first is not.

The design response is backwards-faded scaffolding, from Atkinson, Renkl, and Merrill 2003.[^18] The idea: present the problem initially with all steps worked out. The student studies the worked solution. Later versions of similar problems are presented with the *last step missing*, requiring the student to complete it. Then the *last two steps* missing. And so on, with the scaffolding fading from the back of the solution toward the front. By the time the student is solving from scratch, they have built the framework by working backwards from the end state. Each fading step asks the student to perform exactly one new cognitive operation in a context where every other operation is already supported. Cognitive load is bounded. The anxiety failure is prevented because the student is never asked to perform an operation they have no scaffold for.

![Horizontal sequence of five Glimmer sessions ](images/07-the-four-modes-fig-03.png)
*Figure 7.3 — Horizontal sequence of five Glimmer sessions *

Renkl on worked examples more broadly: worked examples produce reliably stronger learning than equivalent time on problem-solving alone, particularly for novices, with typical effect sizes of 0.5–1.0 standard deviations on near-transfer.[^19]

For Glimmer specifically: weeks 1–3 must include backwards-faded worked examples of the Glimmer rubric being satisfied. The student is not asked to produce a well-defended design from scratch in week 1. They are asked to evaluate a fully-worked example, then to complete the last move on a partially-worked one, then to take progressively more of the work on each successive Glimmer. The fading is the scaffolding.

There is a companion principle from Pea 2004, who pulled the term *scaffolding* back to Wood, Bruner, and Ross's original meaning: *temporary* support, calibrated to the learner's current need, withdrawn as competence grows.[^20] Permanent scaffolding is not scaffolding — it is dependency. The AI reviewer's questions must be *contingent* on what the learner produced, not a generic checklist applied every week regardless of what the student wrote. They must *reduce in support* as the learner's framing matures. And they must *transfer* — the learner who has done ten Glimmers should be able to ask themselves the reviewer's questions without the reviewer present.

---

## Phase gates — measurement decisions, not pedagogical ones

The chapter's structural argument is that phase gates are not pedagogical decisions in the usual sense. They are measurement decisions. Each gate uses a specific signal from the measurement layer as its criterion, and each gate is a falsifiable commitment — not a policy but a bet that can be revised as deployment evidence accumulates.

**Quiz Me gated until section read.** The system does not surface retrieval practice for material the student has not demonstrated reading engagement with. Gating on the temporal engagement signal prevents the "quiz on material I haven't read" failure mode. Quiz Me items advance from *due* to *mastered* not when the student gets them right once but when the retest at the FSRS-scheduled interval shows storage strength has consolidated.

**Glimmer gated until concept built.** The system does not surface an ill-structured problem until prior performance shows hint-responsive understanding. A student whose scaffolding-response signal is low for a concept has no underlying framework, and the Glimmer would ask for specification work the student cannot perform productively. The gate prevents the anxiety collapse structurally.

**Case Study gated until representation is sufficient.** The student must be able to apply the concept outside the instructional context and the concept must be in storage rather than transient performance. Both conditions must be satisfied before the system surfaces a case.

**Ask AI not gated, but bounded.** Ask AI is always available — it is the entry mode. But the response is constrained by the prerequisites graph. If the student is asking about a concept whose prerequisites they have not built, the Ask AI response routes them to remediation rather than answering the surface question. The platform knows what the student does not know about their own gaps.

The phase-gate framework is a closed loop. The signal from the measurement layer informs the mode-selection decision. The mode selection generates the learning interaction. The learning interaction produces a new signal. The next decision uses the updated signal.

![Closed-loop cycle with four nodes ](images/07-the-four-modes-fig-04.png)
*Figure 7.4 — Closed-loop cycle with four nodes *

This is what makes the four modes a system rather than a menu. A menu lets the learner pick — and the learner will pick the mode that feels easiest, which is the fluency trap from Chapter 5 restated at the mode level. Unguarded access to Ask AI produces the Bastani GPT-Base outcome. Unguarded access to Quiz Me produces high session scores and poor 30-day retention. Unguarded access to Glimmer produces 60% abandonment by week two. The phase-gate system selects on the learner's behalf, using evidence the learner does not have direct access to. The platform's uncomfortable claim is that the platform knows things the student does not — and that using that knowledge to gate the mode is the design move.

I want to be honest about the one counter-argument this claim cannot dismiss. If a head-to-head deployment trial showed that a menu-based four-mode system — student chooses the mode each session — produced equivalent durable-learning outcomes to a phase-gated four-mode system, the gating discipline would be added cost without added signal. I do not expect this; the fluency-trap evidence and the menu-selection-bias argument both predict that the gated version outperforms. But the comparison has not been run, and a clean null result would be the empirical finding that forced a rewrite of this chapter. That is what an experiment-as-product commits to.

---

## What the modes look like on a single concept

Let me make this concrete by walking through one concept across four sessions. Composite, illustrative, not deployed data.

A medical student is working through linear versus nonlinear pharmacokinetics — specifically, Michaelis-Menten saturation behavior and what it means for drug dosing at high concentrations.

**Session 1.** The prerequisite graph flags that this concept depends on Michaelis-Menten enzyme kinetics, and the student's prior performance on that prerequisite shows high initial recall but sharp decay — the pattern of shallow encoding. Ask AI is context-anchored to the Michaelis-Menten section of the biochemistry textbook, hint-only mode. The student asks: *"Why does saturation matter for drug dosing?"* The Ask AI response asks back: *"What did the Michaelis-Menten kinetics tell you about reaction rate at high substrate concentrations?"* The student attempts the answer. The system logs the response, the confidence rating, and the surprise reaction when the student notices that the dosing implication is non-obvious.

**Session 2.** The reading-engagement gate confirms the student has worked through the pharmacokinetics section. Quiz Me surfaces 12 items on linear versus nonlinear behavior, scheduled by FSRS. The student clears the queue. The retest at seven days will confirm whether storage strength has consolidated.

The seven-day retest shows 85% retention on the core items. A transfer probe — the same concept framed in terms of phenytoin dosing rather than the textbook's lidocaine example — produces 70% performance, within the population norm. The student has demonstrated cross-context transfer on the underlying mechanism. Both the cross-context transfer signal and the retrieval-strength signal are now satisfied.

**Session 3.** Case Study gates open. The system surfaces a pre-written, faculty-reviewed case on warfarin-amiodarone interaction: the clinical decision of which dose adjustment to make and what monitoring schedule to follow, given the bleeding risk if the dose is not adjusted. The AI facilitator asks: *"What did your previous analysis of CYP3A4 inhibition predict about the half-life change?"* The student's reasoning is the assessable product. Whether the verdict is right matters less than whether the reasoning is defensible.

**Session 4.** Week 8. The scaffolding-response signal for the underlying concepts is in the hint-responsive range. Glimmer surfaces: *design a dosing protocol for a patient with renal impairment, on warfarin, requiring amiodarone for atrial fibrillation.* The rubric: name the drug-drug interactions and their direction; specify the monitoring schedule and the decision rule for dose adjustment; defend the choice of starting dose given the renal function. The AI reviewer asks contingent questions — if the student named CYP3A4 inhibition but not P-glycoprotein, the reviewer asks *"what else might be at play?"* rather than *"you missed P-gp."* The scaffolding is the design; the contingency is what makes it scaffolding rather than a checklist.

Each mode did something none of the others could. Ask AI diagnosed a prerequisite gap and forced an articulation. Quiz Me built storage strength with scheduled spacing. Case Study anchored the concept in clinical consequence. Glimmer required the student to specify the problem themselves and defend the solution. All four together produced a capability no one of them would have produced alone. This is what the chapter means by *system rather than menu*.

---

## Exercises

The following exercises are for practice with large language models in an educational context. Use an LLM of your choice for each.

1. **(Phase gate design — LLM exercise)** Choose a learning objective in a domain you know well and describe it to an LLM. Ask the LLM to design a four-mode sequence for that objective: which mode comes first, what evidence would trigger the transition to each subsequent mode, and what failure mode each transition prevents. Then push back: ask the LLM to identify the weakest phase gate in its own design and specify what measurement signal would tell you whether that gate is doing its job. Evaluate whether the LLM treats the gates as pedagogical preferences or as falsifiable measurement commitments.

2. **(Failure diagnosis — LLM exercise)** Present the following scenario to an LLM: a Glimmer deployment in an introductory biochemistry course shows 60% of students abandoning the mode in week two. Ask the LLM to diagnose the failure mode and specify a scaffolding correction. Evaluate whether the LLM identifies the anxiety failure mechanism (students unable to specify the problem before solving it), the backwards-faded design response, and the specific phase gate that should have been in place. Where did the LLM reach for a generic "add more scaffolding" recommendation without specifying what the scaffolding must do?

3. **(Evidence-layer separation — LLM exercise)** Ask an LLM to evaluate the claim: *"Quiz Me uses FSRS, an evidence-based algorithm for scheduling review at intervals that maximize durable retention, so Quiz Me's learning gains are well-validated."* Ask the LLM to separate the three evidential layers — mechanism, principle, implementation — and name which layer each supporting study belongs to. Then ask it to identify the specific claim the FSRS internal benchmarks support versus the claim they do not. Does the LLM correctly distinguish scheduling evidence from learning-outcome evidence, or does it collapse them?

4. **(Ask AI guardrail design — LLM exercise)** Present the Bastani PNAS 2025 finding to an LLM — GPT Base versus GPT Tutor, same model, opposite outcomes — and ask it to design a context-anchoring specification for an Ask AI deployment in a subject of your choice. The specification should name three context-injection decisions, explain what each one prevents, and identify the measurement signal that would tell you whether the combined guardrail is working as intended. Evaluate whether the LLM treats the wrapper as the variable or defaults to model selection as the primary design lever.

---

## References

[^1]: VanLehn, K. (2011). The relative effectiveness of human tutoring, intelligent tutoring systems, and other tutoring systems. *Educational Psychologist*, 46(4), 197–221. https://doi.org/10.1080/00461520.2011.611369

[^2]: Graesser, A. C., et al. (2005). AutoTutor: A tutor with dialogue in natural language. *Behavior Research Methods, Instruments, & Computers*, 36(2), 180–192.

[^3]: Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., & Mariman, R. (2025). Generative AI without guardrails can harm learning: Evidence from high school mathematics. *Proceedings of the National Academy of Sciences*, 122(26), e2422633122. https://doi.org/10.1073/pnas.2422633122

[^4]: Liu, N. F., et al. (2023). Lost in the middle: How language models use long contexts. arXiv:2307.03172. https://arxiv.org/abs/2307.03172

[^5]: Koedinger, K. R., & Aleven, V. (2007). Exploring the assistance dilemma in experiments with cognitive tutors. *Educational Psychology Review*, 19(3), 239–264.

[^6]: Thistlethwaite, J. E., et al. (2012). The effectiveness of case-based learning in health professional education. A BEME systematic review: BEME Guide No. 23. *Medical Teacher*, 34(6), e421–e444. https://doi.org/10.3109/0142159X.2012.680939

[^7]: Roediger, H. L., III, & Karpicke, J. D. (2006). Test-enhanced learning: Taking memory tests improves long-term retention. *Psychological Science*, 17(3), 249–255. https://pubmed.ncbi.nlm.nih.gov/16507066/

[^8]: Adesope, O. O., Trevisan, D. A., & Sundararajan, N. (2017). Rethinking the use of tests: A meta-analysis of practice testing. *Review of Educational Research*, 87(3), 659–701.

[^9]: Pan, S. C., & Rickard, T. C. (2018). Transfer of test-enhanced learning: Meta-analytic review and synthesis. *Psychological Bulletin*, 144(7), 710–756. https://pubmed.ncbi.nlm.nih.gov/29733621/

[^10]: Cepeda, N. J., Pashler, H., Vul, E., Wixted, J. T., & Rohrer, D. (2006). Distributed practice in verbal recall tasks: A review and quantitative synthesis. *Psychological Bulletin*, 132(3), 354–380. https://pubmed.ncbi.nlm.nih.gov/16719566/

[^11]: Cepeda, N. J., et al. (2008). Spacing effects in learning: A temporal ridgeline of optimal retention. *Psychological Science*, 19(11), 1095–1102.

[^12]: FSRS (Free Spaced Repetition Scheduler). Open Spaced Repetition project. https://open-spaced-repetition.github.io/ See also: Expertium benchmark. https://expertium.github.io/Benchmark.html

[^13]: Zeigarnik, B. (1927). Über das Behalten von erledigten und unerledigten Handlungen. *Psychologische Forschung*, 9, 1–85.

[^14]: Fiorella, L., & Mayer, R. E. (2016). Eight ways to promote generative learning. *Educational Psychology Review*, 28(4), 717–741. https://doi.org/10.1007/s10648-015-9348-9

[^15]: Jonassen, D. H. (1997). Instructional design models for well-structured and ill-structured problem-solving learning outcomes. *Educational Technology Research and Development*, 45(1), 65–94.

[^16]: Belland, B. R., Walker, A. E., Kim, N. J., & Lefler, M. (2017). Synthesizing results from empirical research on computer-based scaffolding in STEM education. *Review of Educational Research*, 87(2), 309–344.

[^17]: Chen, C. H., & Yang, Y. C. (2019). Revisiting the effects of project-based learning on students' academic achievement: A meta-analysis investigating moderators. *Educational Research Review*, 26, 71–81.

[^18]: Atkinson, R. K., Renkl, A., & Merrill, M. M. (2003). Transitioning from studying examples to solving problems: Effects of self-explanation prompts and fading worked-out steps. *Journal of Educational Psychology*, 95(4), 774–783. https://doi.org/10.1037/0022-0663.95.4.774

[^19]: Renkl, A. (2014). Toward an instructionally oriented theory of example-based learning. *Cognitive Science*, 38(1), 1–37. https://doi.org/10.1111/cogs.12086

[^20]: Pea, R. (2004). The social and technological dimensions of scaffolding and related theoretical concepts for learning, education, and human activity. *Journal of the Learning Sciences*, 13(3), 423–451.
