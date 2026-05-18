# Research Note — Context-Aware AI Chatbots in Educational Platforms

*Working pantry document for the Medhavy book project. Substantive research underpinning the "Ask AI" chapter / sections, organized for direct quarrying into prose. Citation-dense.*

*Compiled 2026-05-17. Maintained for revision.*

---

## Preliminary: the distinction this note refuses to collapse

The evidence base for "AI tutors" is two literatures wearing one phrase. They share a name and almost nothing else.

**Class A — Intelligent Tutoring Systems (ITS).** Carnegie Learning's Cognitive Tutor, AutoTutor, ALEKS, ASSISTments. Mature literature dating to the 1980s. Rule-based, model-tracing or constraint-based, with handcrafted hint sequences and explicit student models. When well-designed, they produce effect sizes in the neighborhood of *d* ≈ 0.4–0.7 against conventional instruction (VanLehn 2011; Kulik & Fletcher 2016; Steenbergen-Hu & Cooper 2014, college sample). Their machinery is interpretable: a step has a designed hint sequence, a misconception triggers a designed remediation. The hard parts (authoring, scaling across domains) are well-named.

**Class B — Generative-AI chatbots.** Khanmigo, ChatGPT/Claude/Gemini used for tutoring, LearnLM, Tutor CoPilot, Bastani's GPT Tutor, Kestin et al.'s Harvard physics tutor. The literature begins in late 2022. Studies are still settling. Effect sizes range from *strongly negative* on durable learning when designed naively (Bastani et al. 2025, *PNAS*) to *very large positive* (~0.7–1.3 σ) when designed against research-based pedagogical principles in a single course (Kestin et al. 2025, *Scientific Reports*). The machinery is *not* interpretable in the ITS sense: the same prompt can produce a Socratic question one turn and a bottom-out answer the next.

**The medhavy-relevant point.** When a chapter or platform doc invokes "AI tutoring effect sizes," the first move is to name which class. ITS results from 1995–2020 *do not* automatically transfer to a generative chatbot in 2026. Generative-chatbot results from 2024–2025 are early, methodologically uneven, and dominated by single-course, single-cohort trials. The strongest negative finding to date — Bastani et al.'s −17 percentage-point exam gap from unguarded GPT-4 use during practice — is currently the most important data point for any production AI-tutor deployment.

Every effect size below is tagged `[ITS]` or `[GenAI]` or `[Both]`.

---

## 1. Effectiveness evidence

### 1.1 The ITS canon

**VanLehn 2011** [ITS] is the canonical meta-analysis on tutoring effectiveness. It reviewed experiments comparing human tutoring, computer tutoring, and no tutoring, dividing computer systems by interaction granularity (answer-based, step-based, substep-based). The widely-circulated "2-sigma" claim from Bloom (1984) for human tutoring did not survive VanLehn's review. He found *d* = 0.79 for human tutoring vs. no tutoring, and *d* = 0.76 for step-based ITS — essentially indistinguishable from human tutoring at the meta-analytic level. Answer-based CAI systems came in lower, around *d* = 0.31. The finding most relevant to medhavy is structural: step-grain interactivity matters more than whether the tutor is a human or a machine. The chatbot equivalent of "step-based" is requiring the student to externalize a reasoning step before the system advances. ([VanLehn 2011, *Educational Psychologist* 46(4), 197–221](https://www.tandfonline.com/doi/abs/10.1080/00461520.2011.611369))

**Kulik & Fletcher 2016** [ITS] meta-analyzed 50 controlled evaluations of ITS, finding a median effect of *g* = 0.66 (50th percentile → 75th percentile improvement on average). The key moderator: effects were substantially larger on locally-developed tests than on standardized tests, meaning instructional-test alignment is doing serious work in the reported numbers. This is the "teach to the test" warning translated into ITS terms — and it applies *a fortiori* to AI tutors that can be steered toward whatever assessment they will be graded against. ([Kulik & Fletcher 2016, *Review of Educational Research* 86(1), 42–78](https://journals.sagepub.com/doi/abs/10.3102/0034654315581420))

**Steenbergen-Hu & Cooper 2013** [ITS] is the cold-water finding. Their meta-analysis of ITS in K–12 mathematics (26 reports, 34 independent samples, 1997–2010) found essentially null effects: *g* = 0.01 to *g* = 0.09 on mathematics achievement overall, with *g* = −0.18 for samples of low-achieving K–12 students. Their separate analysis of college students gave *g* ≈ 0.37–0.43, closer to the Kulik–Fletcher range. The K–12 result is a structural warning: ITS that work in college often fail in K–12, where motivation, prior knowledge, and classroom integration look very different. ([Steenbergen-Hu & Cooper 2013, *Journal of Educational Psychology* 105(4), 970–987](https://psycnet.apa.org/record/2013-31551-001); [college companion 2014](https://www.researchgate.net/publication/263918046))

**AutoTutor (Graesser et al.)** [ITS, dialog-based]. A natural-language ITS that pre-dates LLMs by two decades. AutoTutor produces *d* ≈ 0.7–0.8 average for deep comprehension (range 0.4–1.5 across versions and measures). Why/AutoTutor on Newtonian physics produced *d* = 0.75–1.22. This matters for medhavy because AutoTutor is the closest ITS analog to a chatbot — it conducts a turn-based natural-language dialog, asks questions, and gives hints. Its results show what's *possible* from a tightly-scripted dialog tutor, and provide the historical baseline against which generative chatbots should be benchmarked. ([Graesser, Chipman, Haynes & Olney 2005, AutoTutor overview](https://link.springer.com/article/10.3758/BF03195563); [Nye, Graesser & Hu 2014, *IJAIED*, 17-year review](https://link.springer.com/article/10.1007/s40593-014-0029-5))

**ASSISTments (Roschelle, Feng, Heffernan and colleagues)** [ITS, online homework]. The Maine RCT (~2,800 7th-graders) produced *g* ≈ 0.22 on a state math assessment — about three-quarters of a school-year of additional learning, with larger effects for lower-prior-achievement students. A North Carolina replication (63 schools) found *g* ≈ 0.10 a year after the intervention. ([Roschelle et al. 2016, *AERA Open*](https://files.eric.ed.gov/fulltext/ED631720.pdf); [Murphy et al. WestEd replication](https://www.wested.org/support/efficacy-of-assistments-online-homework-support-for-middle-school-mathematics-learning/)) The relevant lesson for medhavy is that scaled, math-homework-grade ITS effects in real classrooms are real but modest — call it *g* ≈ 0.1–0.2 in the wild — and substantially smaller than the *g* ≈ 0.66 from controlled evaluations.

### 1.2 The generative-AI evidence to date

**Bastani, Bastani, Sungu, Ge, Kabakcı & Mariman 2025** [GenAI]. The single most consequential rigorous finding to date on the generative-AI side. RCT in a Turkish high school, ~1,000 students in grades 9–11, math practice sessions. Three conditions: no AI, GPT-4 with a standard chat interface ("GPT Base"), and GPT-4 with a teacher-designed hint-giving wrapper that refused to give answers ("GPT Tutor"). During practice: GPT Base students scored 48% higher than the no-AI group, GPT Tutor students scored 127% higher. On a subsequent exam *without AI access*: GPT Base students scored 17% lower than the no-AI control; GPT Tutor students were statistically indistinguishable from the no-AI control. The mechanism is fluency in the presence of the tool that does not transfer to skill in its absence. ([Bastani et al. 2025, *PNAS* 122(26), e2422633122](https://www.pnas.org/doi/10.1073/pnas.2422633122); [Wharton summary](https://knowledge.wharton.upenn.edu/article/without-guardrails-generative-ai-can-harm-education/))

This is the finding that should sit at the center of any responsible AI-tutor deployment. Three claims fall out of it. First, performance during a learning episode is not learning — Bjork's distinction between performance and learning (§2.4 below) has now been demonstrated empirically for LLM-mediated practice. Second, the *guardrails design* is the variable, not the model — same GPT-4 underneath, two prompt wrappers, opposite outcomes. Third, the harm from naïve deployment is not subtle: −17% on the exam is roughly half a standard deviation of damage relative to no AI at all.

**Wang, Ribeiro, Robinson, Loeb, Demszky 2024** [GenAI, hybrid]. Tutor CoPilot — an AI assistant for live human tutors rather than a direct student-facing chatbot. RCT with 900 tutors and 1,800 K–5 students from historically underserved communities. Mastery of learning objectives rose by ~4 percentage points overall, and by ~9 percentage points for students working with tutors rated as lower-quality at baseline. The lift is concentrated where tutor expertise is thinnest. This is one of the few large RCTs of generative AI in actual K–12 instruction and the most credible evidence for the "AI as scaffold for the weaker human" use case. ([Wang et al. 2024, arXiv:2410.03017](https://arxiv.org/abs/2410.03017))

**Kestin, Miller, Klales, Milbourne & Ponti 2025** [GenAI]. Harvard physics RCT, Physical Sciences 2, N = 233 (Fall 2023). Custom AI tutor designed with the same research-based pedagogical principles as the in-class active-learning sessions (segmented content, formative checks, deliberate misconception traps). Students learned roughly twice as much in less time on the AI tutor than in the active-learning class; reported effect sizes of *d* ≈ 0.7–1.3. The catch: this is one institution, one course, one professor, one custom-built tutor, and the comparison is to a single active-learning session rather than the full course. The result is large and credible *for what it measures*, but its generalization to "any AI tutor is twice as good as active learning" is exactly the inference the paper does not support. ([Kestin et al. 2025, *Scientific Reports* (Nature) 15, online 3 June 2025](https://www.nature.com/articles/s41598-025-97652-6); [Harvard Gazette coverage](https://news.harvard.edu/gazette/story/2024/09/professor-tailored-ai-tutor-to-physics-course-engagement-doubled/))

**Khanmigo evaluations** [GenAI, mostly vendor-sourced]. Khan Academy reports rapid growth (40,000 → 700,000 students in the 2024–25 school year across 380+ district partners), high satisfaction ratings, and a 4-star Common Sense Media rating ([Khan Academy 2024 efficacy blog](https://blog.khanacademy.org/khan-academy-efficacy-results-november-2024/); [Common Sense Media review](https://www.commonsensemedia.org/ai-ratings/khanmigo)). What does *not* yet exist in peer-reviewed form: a large, independent RCT with a no-Khanmigo control measuring durable learning outcomes outside the Khan Academy ecosystem. Two qualitative academic evaluations have appeared:
- A Computer-Assisted Language Learning evaluation found Khanmigo supported authentic learning experiences but did not always tailor to learner needs and did not support metacognitive skills ([ERIC EJ1435677](https://files.eric.ed.gov/fulltext/EJ1435677.pdf)).
- A SWOT/acceptability study identified personalization and learner independence as strengths and technical/ethical/cultural-sensitivity issues as limitations ([ERIC EJ1483352](https://files.eric.ed.gov/fulltext/EJ1483352.pdf)).

I could not locate a finalized WestEd evaluation of Khanmigo in peer-reviewed publication at the time of this note — `[verify]`. WestEd has done independent evaluation of ASSISTments (above) and has been listed as a Khanmigo evaluation partner in press materials, but the specific Khanmigo report number / publication needs to be checked before citation in chapter prose.

**Lee, Sarkar, Tankelevitch, Drosos, Rintel, Banks & Wilson 2025** [GenAI, knowledge-work survey]. Microsoft Research / CMU survey of 319 knowledge workers on 936 first-hand examples of GenAI use. Reported reductions in cognitive effort were dominant — 72% "less effort" or "much less effort" on Knowledge tasks, 79% on Comprehension, 69% Application, 72% Analysis, 76% Synthesis, 55% Evaluation. The critical finding for medhavy: *higher confidence in GenAI was associated with less critical thinking; higher self-confidence was associated with more critical thinking.* The shift, where critical thinking persisted, was *away from generation* and *toward verification, integration, and stewardship*. Survey self-report has well-known limits, but the directionality matches the Bastani objective-test finding. ([Lee et al. 2025, CHI 2025](https://dl.acm.org/doi/full/10.1145/3706598.3713778); [Microsoft Research PDF](https://www.microsoft.com/en-us/research/wp-content/uploads/2025/01/lee_2025_ai_critical_thinking_survey.pdf))

**LearnLM UK RCT (2025)** [GenAI]. An exploratory UK classroom RCT comparing LearnLM (Google's pedagogically-tuned chatbot) against human tutoring. Students using LearnLM solved 5.5 percentage points more novel problems on subsequent topics than students working with human tutors alone (66.2% vs. 60.7%). LearnLM was instructed to produce Socratic responses aimed at guiding self-correction without revealing answers. Supervising tutors reported high-quality Socratic dialog, though they noted persistence of Socratic questioning sometimes outlasted student patience. ([arXiv:2512.23633](https://arxiv.org/html/2512.23633v1))

### 1.3 Direct comparison: context-aware vs. general chatbot

This is the most relevant question for medhavy and the literature does not yet answer it cleanly. The strongest indirect comparisons:

- Bastani's GPT Tutor (with teacher-designed concept-anchored hints injected into the prompt) vs. GPT Base (raw ChatGPT). Same model, different context wrapping. Outcome: GPT Tutor preserves learning; GPT Base destroys it. This is the closest existing analog to "context-aware vs. general." [GenAI]
- Kestin's Harvard physics tutor (with course-specific scaffolding and misconception lists baked in) vs. nothing of the same scaffolding without AI. The course-aware version produced the *d* ≈ 0.7–1.3 result. [GenAI]
- The general survey of RAG-based educational chatbots (Modran et al. 2025, *Applied Sciences*; Sebastian, Mosquera & Cancela 2025, *Computers and Education: Artificial Intelligence*) reports the field's standing concern: most RAG-tutor studies measure user satisfaction and reported usefulness rather than durable learning outcomes. *"There is a lack of studies that report the actual effects regarding the very purpose for which educational RAG chatbots have been developed, which is considered an appalling weakness in the evaluation of RAG chatbots in the educational domain"* (Modran et al. 2025). [GenAI] ([Modran et al. 2025, *Applied Sciences*](https://www.mdpi.com/2076-3417/15/8/4234))

Medhavy's bet — that context-anchoring an AI tutor to the current concept, section, and chapter improves learning — is consistent with Bastani's findings and with the ITS literature on hint design, but is not yet established by a head-to-head RCT in the generative-AI literature. This is a real research opportunity, not a settled claim.

---

## 2. Best practices for implementation

### 2.1 Socratic vs. direct-answer prompting

The empirical picture, briefly: Socratic-style guardrails *help when they hold*, and the failure mode is models breaking guardrail under pressure.

- Favaretto et al. 2024 [GenAI] benchmarked a Socratic chatbot against a "basic" chatbot and a random-response chatbot for critical thinking development. Socratic outperformed both, particularly for reflection ([arXiv:2409.05511](https://arxiv.org/abs/2409.05511)).
- LearnLM UK RCT (above) [GenAI]: Socratic LearnLM outperformed human tutors on novel-problem transfer by 5.5 pp.
- Bastani GPT Tutor [GenAI]: the operative design choice was "provide teacher-designed hints instead of giving away answers." This is Socratic-style discipline implemented at the prompt layer.
- A *Frontiers in Education* comparative study (2025) on Socratic ChatGPT vs. human tutors for critical thinking ([doi 10.3389/feduc.2025.1528603](https://www.frontiersin.org/journals/education/articles/10.3389/feduc.2025.1528603/full)) found mixed results — gains in some critical-thinking subdimensions, neutral on others. The takeaway: Socratic dialog does not universally beat direct instruction, but the conditions under which it loses are conditions where the student lacks the prerequisite knowledge to answer the questions productively.

The robust generalization across these studies: *Socratic prompting works when the student has the prerequisites to engage productively with the questions. When the prerequisite is missing, the Socratic tutor needs to detect the gap and switch modes — usually toward direct re-explanation of the prerequisite — rather than continuing to question.* This is the design move that Khanmigo's documented prompt structure attempts and that the next generation of tutoring systems will need to make robust.

### 2.2 Hint design — the Aleven/Koedinger/McLaren tradition

This is where ITS literature transfers directly to chatbot design.

**Aleven, McLaren, Roll & Koedinger** [ITS] documented over a decade that students misuse on-demand hints. Log data from the Cognitive Tutor Geometry showed that students frequently click through hint sequences to reach "bottom-out" hints (the ones that give away the answer) without reading the earlier hints that explain *why* the answer is what it is ([Aleven, McLaren, Roll & Koedinger 2006/2016, *IJAIED*](https://link.springer.com/article/10.1007/s40593-015-0089-1)). The Help Tutor, an auxiliary system designed to teach students to seek help productively, modified students' help-seeking behavior but did not, in their primary studies, produce reliable downstream learning gains.

**Koedinger & Aleven 2007** [ITS] formalized the "assistance dilemma": for any given learner state, there is an optimum amount of assistance. Below it, the student fails. Above it, the student offloads rather than learns. The optimum is curvilinear and depends on prior knowledge — low-knowledge and high-knowledge students benefit from different amounts of assistance than medium-knowledge students ([Koedinger & Aleven 2007, *Educational Psychology Review* 19(3), 239–264](https://link.springer.com/article/10.1007/s10648-007-9049-0)).

For a generative chatbot, the operational translation is: **a single fixed prompt cannot be optimal across all students**. Effective context injection includes *student state* (where they are in the curriculum, what they have demonstrated mastery of, where they have struggled) and not only *content state* (which section they're reading).

### 2.3 "I don't understand" response strategies

This is the practitioner question — when a student says *"I don't get it"*, what should the chatbot do?

The ITS-derived menu, in order of increasing assistance level:
1. **Specify the confusion.** Ask which part. ("Is it the symbol notation or the conceptual move?") A productive Socratic move; works when the student has enough scaffolding to localize their confusion.
2. **Graduated re-explanation.** Re-explain at a lower level of abstraction. Cognitive-tutor hint sequences are typically 3–5 hints, the last of which is bottom-out.
3. **Prerequisite recall.** Pull the prior concept the current concept depends on. Specify it, check understanding, return.
4. **Analogy injection.** Bring in a concrete instance the student already understands and map it to the abstract concept.
5. **Worked example.** Show one fully worked-out instance, then ask the student to do a near-transfer one.

Khanmigo's public-facing materials describe most of these moves, in particular variants of 1, 2, and 3 ([Khan Academy 2024, 7-step prompt engineering](https://blog.khanacademy.org/khan-academys-7-step-approach-to-prompt-engineering-for-khanmigo/)). The peer-reviewed RCT evidence that any *specific* sequence outperforms any other for generative chatbots is — at the time of this note — thin. The ITS literature on hint sequences (Aleven et al.) is the most rigorous evidence base, and it transfers in principle, not yet established by replication in generative-chatbot studies.

### 2.4 Guardrails against cognitive offloading

The two cleanest implementations on the record:

- **Bastani GPT Tutor.** System prompt forced the model to give teacher-designed hints rather than answers; the model could explain why a student's step was wrong without producing the next step. Outcome: parity with no-AI control on exam performance — i.e., the offloading harm was zeroed out. [GenAI]
- **Khanmigo.** Documented system prompt ("never give the answer; ask what the student thinks the next step is") implements the same discipline. Practitioner-reported failure mode: *"persistent prompting would lead to Khanmigo offering a more complete answer"* — i.e., the guardrail leaks under pressure ([Common Sense Media review](https://www.commonsensemedia.org/ai-ratings/khanmigo)). [GenAI, vendor-sourced]

The Bjork "desirable difficulties" principle ([E. Bjork & R. Bjork 2011/2020](https://www.waddesdonschool.com/wp-content/uploads/2021/02/Desriable-Difficulties-in-theory-and-practice-Bjork-Bjork-2020.pdf)) is the underlying pedagogical theory: the conditions that *feel easier* (massed practice, re-reading, having someone hand you the answer) typically produce weaker long-term retention than conditions that feel harder (spaced practice, retrieval practice, working through difficulty). An AI tutor that optimizes for the student's *moment-to-moment subjective experience* (smooth, low friction, no struggle) optimizes for the precise wrong objective. The Bastani PNAS finding is the empirical confirmation of this prediction for generative AI tutors specifically. [Both ITS and GenAI implication]

Design principles that fall out:
- The chatbot's job is not to be liked. It is to produce durable learning.
- "Working through" rather than "looking up" is the desirable difficulty.
- A reasoning step the student takes is worth more than a reasoning step the chatbot completes.
- The student should externalize the answer to the chatbot, not receive it from the chatbot, before progressing.

---

## 3. Context injection (the medhavy-specific question)

### 3.1 What "context" can mean

For a textbook-anchored chatbot, the candidate contexts are layered:

1. **Section title only.** Cheap, low-bandwidth. Lets the chatbot know roughly what topic. Insufficient against hallucination.
2. **Current paragraph or selected passage.** What the student is literally looking at. The minimum for "ground the answer in *this* explanation, not a generic one."
3. **Chapter so far.** Lets the chatbot use the chapter's specific definitions, examples, and notation.
4. **Prerequisites graph.** Pull the conceptual dependencies the current section assumes. Lets the chatbot diagnose "your confusion is upstream of where you are."
5. **Student state.** What the student has read, what exercises they got right/wrong, what they have asked about before. The ITS *student model* in generative-tutor form.
6. **Full book.** Maximal coherence, maximal context-window cost, maximal "lost in the middle" exposure.

### 3.2 RAG in educational chatbots

RAG (retrieval-augmented generation) is the dominant architectural pattern for textbook-anchored chatbots. The core promise: retrieve the relevant chunk(s) of the textbook at query time, inject them into the prompt, and constrain the model to answer from them.

Surveys ([Modran et al. 2025, *Applied Sciences*](https://www.mdpi.com/2076-3417/15/8/4234); [Sebastian, Mosquera & Cancela 2025, *Computers and Education: AI*](https://www.sciencedirect.com/science/article/pii/S2590291125004796); [Liu et al. 2025, *C&E:AI* systematic review](https://www.sciencedirect.com/science/article/pii/S2666920X25000578)) make three consistent claims:

- RAG meaningfully reduces hallucination relative to base-LLM tutoring by anchoring outputs to source material.
- Most educational RAG implementations report user-experience metrics (satisfaction, perceived helpfulness) rather than learning outcomes.
- The methodological maturity of educational RAG evaluation is roughly where ITS evaluation was in the mid-1990s.

Practitioner implementations of note:
- **RAGMan** (introductory programming): reported 78% of users self-reporting improved learning outcomes — note: self-report, not measured learning.
- **Tutor CoPilot** (Wang et al. 2024): grounded its expert-pedagogical reasoning in Bridge-distilled "think-aloud" transcripts of experienced tutors, injected into the LLM as context. The 4 pp / 9 pp mastery effect is the strongest evidence to date that *what you put in the context* meaningfully shapes downstream student learning.

### 3.3 How much context is "enough"?

The empirical picture is settled in one direction only: **more context is not uniformly better**.

The "lost in the middle" phenomenon ([Liu et al. 2023, arXiv:2307.03172](https://arxiv.org/abs/2307.03172)) is now an established property of every frontier model tested ([Chroma 2025 context-rot report](https://www.morphllm.com/context-rot)). Performance follows a U-shaped curve along the position of the relevant information in the prompt: high at the beginning, high at the end, *significantly degraded — sometimes 30 percentage points lower — in the middle*. Adding more tokens does not improve performance once the needed information is buried.

Worse, "context rot" — measurable degradation of output quality as input length grows, even when the relevant information is at the edges and the window isn't full — is present in all 18 frontier models that Chroma tested in 2025, including GPT-4.1, Claude Opus 4, and Gemini 2.5. A 200K-token window does not guarantee good performance at 50K tokens of context.

For medhavy this implies a design discipline rather than a fixed answer:
- **Inject the current paragraph or section unconditionally.** This is the minimum.
- **Inject specific prerequisites on demand**, retrieved by RAG against an explicit prerequisites graph, rather than dumping the chapter so far into context.
- **Avoid full-chapter dumps** unless the question genuinely requires cross-section synthesis; even then, summarize rather than concatenate.
- **Place high-value context at the beginning and end of the prompt**, with the user query at the very end where attention is strongest.
- **Treat student state as separable context** (a structured summary, not a transcript) to prevent transcript bloat from degrading retrieval against textbook content.

There is no widely-replicated "optimal context length for tutoring" number in the literature; the practitioner heuristic of "smallest context that contains everything the chatbot needs to answer this question correctly" is what the empirical evidence supports.

### 3.4 Khanmigo and Duolingo as reference implementations

**Khanmigo** ([7-step prompt engineering blog](https://blog.khanacademy.org/khan-academys-7-step-approach-to-prompt-engineering-for-khanmigo/)) reports a system that injects: a system prompt enforcing the Socratic posture, the activity the student is on (problem statement, expected answer, expected misconceptions), prior turns in the conversation, and selected Khan Academy course material. This is closer to "section + prerequisites + student state" than "full book." Specific prompt details are vendor-controlled and have not been published in academic form. [GenAI, vendor-sourced]

**Duolingo Max / Lily / Oscar** ([Duolingo blog series](https://blog.duolingo.com/ai-and-video-call/); [Duocon 2024 announcement](https://investors.duolingo.com/news-releases/news-release-details/duolingo-introduces-ai-powered-innovations-duocon-2024)) extracts user-relevant facts from prior calls via a separate LLM pass, stores them as long-term memory, and injects a relevant subset into each new call. Content moderation happens after every turn. Character is consistent across sessions because the character's prompt and memory are persistent context, not regenerated each turn. The model used is GPT-4 underneath. This is the production-tested template for: *long-term student memory as a separate, summarized context source*. [GenAI, vendor-sourced]

### 3.5 Context window pollution

The failure modes practitioners encounter with naïve full-context injection:

- **Distractor interference.** The model attends to semantically-similar-but-irrelevant material in the context and answers from it rather than from the relevant chunk.
- **Recency bias.** With long prompts, the model over-weights the most recent turns and under-weights the system prompt or the retrieved textbook chunk.
- **Token cost.** Linear in the worst case, quadratic in attention cost. Practically, this is a deployment-cost question, not just a quality question.
- **Instruction drift.** With many injected instructions, the model selectively follows some and ignores others. Guardrail prompts ("don't give the answer") are exactly the kind of instruction most vulnerable to dilution.

The takeaway: a *thoughtfully-curated short context* with the relevant textbook passage, a clear system prompt, and a structured student-state summary is likely to outperform a *full-chapter-dumped long context*. This is now a measurable empirical claim, not a stylistic preference.

---

## 4. Failure modes

### 4.1 Cognitive offloading

The strongest in-education demonstration is Bastani et al. 2025 (above): −17% exam performance for unguarded GPT-4 practice. The Lee et al. 2025 Microsoft Research survey provides converging knowledge-work evidence (perceived effort reductions in the 55–79% range across Bloom levels). The pattern is consistent: the experience of using AI feels efficient; the underlying skill is not being built. [GenAI]

The Bjork "performance ≠ learning" distinction is now an empirical line in the AI-tutoring literature, not just a learning-science framework.

### 4.2 Hallucination in subject-matter content

LLMs hallucinate in mathematics and other subject-matter domains in ways that are formally unavoidable. Theoretical analyses ([Banerjee et al. 2024, *arXiv:2409.05746*, "LLMs Will Always Hallucinate"](https://arxiv.org/html/2409.05746v1)) argue that hallucinations are a structural property of the architecture, not a fixable bug.

Empirical studies in education are starting to surface:

- **Erroneous-feedback study** [GenAI, math tutoring]. Within an adaptive learning platform, 252 learners received LLM-generated feedback with errors in 0%, 50%, or 100% of feedback instances. Learners receiving feedback with errors in *all* instances still achieved learning gains comparable to error-free feedback — *but* they spent more time on tasks, reported lower perceived accuracy and usefulness, and reported higher confusion. The students were learning despite the errors, partly by working around them. This is a both-edges finding: hallucinations are less catastrophic than naïve worst-case framing suggests, *and* they impose a cognitive tax the student pays. ([L@S 2025 paper, dl.acm.org/doi/10.1145/3698205.3729555](https://dl.acm.org/doi/10.1145/3698205.3729555))

RAG mitigates but does not eliminate hallucination — the model can still introduce errors when synthesizing across retrieved chunks or when interpreting an ambiguous chunk.

For medhavy, the operational implication: subject-matter accuracy needs to be *measured* on the chatbot's actual outputs against the actual textbook, not assumed because RAG is in place.

### 4.3 The fluency trap

A specific sub-failure-mode worth naming separately. Students report subjective experiences of *learning more* while objectively learning less. This is what Bastani's design measures: confidence rose with GPT Base, exam scores fell. Lee et al.'s knowledge-work survey reports the same pattern via a different methodology: confidence in GenAI was negatively correlated with critical-thinking engagement.

The chapter-relevant implication: student satisfaction is not a proxy for student learning, and a chatbot tuned to satisfaction will systematically undermine learning. The medhavy platform's product metrics should distinguish these two, not collapse them.

### 4.4 Vetting failure

Students cannot reliably evaluate AI output quality in domains where they are not yet expert ([Selwyn 2022, *European Journal of Education* 57(4)](https://onlinelibrary.wiley.com/doi/10.1111/ejed.12532), and ongoing critical work). The expertise required to detect a hallucinated proof, a wrong attribution, or a subtly-confused explanation is exactly the expertise the student is using the tutor to acquire. In other words: the student is least equipped to vet the chatbot precisely where they most need to.

Tracking this as a structural concern matters for the medhavy book's chapter on AI tutoring, because the "you can just ask the AI" pitch evades the vetting question. The Stanford HAI 2024 work ([How Harmful Are AI's Biases on Diverse Student Populations?](https://hai.stanford.edu/news/how-harmful-are-ais-biases-on-diverse-student-populations)) extends this: students from minoritized groups face additional vetting load when the AI generates stereotyped or reductive content about them or their backgrounds.

### 4.5 Equity-of-deployment

The Stanford HAI / Faye-Marie Vassel work ([Stanford HAI 2024](https://hai.stanford.edu/news/how-harmful-are-ais-biases-on-diverse-student-populations)) documents bias in generated narratives about learners, including stereotyped portrayals along race, gender, and intersectional lines. Two papers from this group: "The Psychosocial Impact of Gen AI Harms" (AAAI Spring Symposium Best Special Paper) and "Laissez-Faire Harms: Algorithmic Biases in Generative Language Models" (arXiv preprint). The recommendation pattern: socio-technical evaluation, not just technical bias metrics. Centering users' social identities in design, not as an afterthought.

The Steenbergen-Hu & Cooper finding [ITS] that K–12 ITS effects on low-achieving students were *negative* (*g* = −0.18) is a warning that the generative-chatbot literature has not yet directly engaged with: deploying a tutoring system that works for one population can actively harm another. Bastani et al.'s exam result was on a Turkish high-school population; there is no comparable RCT yet on US K–12, US college, US K–12 by demographic stratum, or non-Anglophone contexts. [GenAI gap]

---

## 5. Key citations consolidated

*Chicago author-date style. Class tag in brackets after the citation indicates whether the source applies to Intelligent Tutoring Systems [ITS], generative-AI chatbots [GenAI], or both [Both].*

Aleven, Vincent, Bruce M. McLaren, Ido Roll, and Kenneth R. Koedinger. 2016. "Help Helps, But Only So Much: Research on Help Seeking with Intelligent Tutoring Systems." *International Journal of Artificial Intelligence in Education* 26(1): 205–223. https://link.springer.com/article/10.1007/s40593-015-0089-1 [ITS]

Banerjee, Sourav, Ayushi Agarwal, and Saloni Singla. 2024. "LLMs Will Always Hallucinate, and We Need to Live With This." arXiv preprint 2409.05746. https://arxiv.org/html/2409.05746v1 [GenAI]

Bastani, Hamsa, Osbert Bastani, Alp Sungu, Haosen Ge, Özge Kabakcı, and Rei Mariman. 2025. "Generative AI Without Guardrails Can Harm Learning: Evidence from High School Mathematics." *Proceedings of the National Academy of Sciences* 122(26): e2422633122. https://www.pnas.org/doi/10.1073/pnas.2422633122 [GenAI]

Bjork, Elizabeth L., and Robert A. Bjork. 2011. "Making Things Hard on Yourself, But in a Good Way: Creating Desirable Difficulties to Enhance Learning." In *Psychology and the Real World: Essays Illustrating Fundamental Contributions to Society*, edited by M. A. Gernsbacher et al., 56–64. https://bjorklab.psych.ucla.edu/wp-content/uploads/sites/13/2016/04/EBjork_RBjork_2011.pdf [Both — learning-science principle]

Chroma Research. 2025. "Context Rot: How Increasing Input Tokens Impacts LLM Performance." Technical report. https://www.morphllm.com/context-rot [GenAI]

Favaretto, Manuel et al. 2024. "Enhancing Critical Thinking in Education by means of a Socratic Chatbot." arXiv preprint 2409.05511. https://arxiv.org/abs/2409.05511 [GenAI]

Graesser, Arthur C., Patrick Chipman, Brian C. Haynes, and Andrew Olney. 2005. "AutoTutor: A Tutor with Dialogue in Natural Language." *Behavior Research Methods* 36: 180–192. https://link.springer.com/article/10.3758/BF03195563 [ITS, dialog-based]

Kestin, Greg, Kelly Miller, Anna Klales, Tessa Milbourne, and Gregorio Ponti. 2025. "AI Tutoring Outperforms In-Class Active Learning: An RCT Introducing a Novel Research-Based Design in an Authentic Educational Setting." *Scientific Reports* 15 (June 3). https://www.nature.com/articles/s41598-025-97652-6 [GenAI]

Khan Academy. 2024. "Khan Academy's 7-Step Approach to Prompt Engineering for Khanmigo." Khan Academy Blog. https://blog.khanacademy.org/khan-academys-7-step-approach-to-prompt-engineering-for-khanmigo/ [GenAI, vendor-sourced]

Koedinger, Kenneth R., and Vincent Aleven. 2007. "Exploring the Assistance Dilemma in Experiments with Cognitive Tutors." *Educational Psychology Review* 19(3): 239–264. https://link.springer.com/article/10.1007/s10648-007-9049-0 [ITS]

Kulik, James A., and J. D. Fletcher. 2016. "Effectiveness of Intelligent Tutoring Systems: A Meta-Analytic Review." *Review of Educational Research* 86(1): 42–78. https://journals.sagepub.com/doi/abs/10.3102/0034654315581420 [ITS]

Lee, Hao-Ping (Hank), Advait Sarkar, Lev Tankelevitch, Ian Drosos, Sean Rintel, Richard Banks, and Nicholas Wilson. 2025. "The Impact of Generative AI on Critical Thinking: Self-Reported Reductions in Cognitive Effort and Confidence Effects From a Survey of Knowledge Workers." *Proceedings of the 2025 CHI Conference on Human Factors in Computing Systems.* https://dl.acm.org/doi/full/10.1145/3706598.3713778 [GenAI]

Liu, Nelson F., Kevin Lin, John Hewitt, Ashwin Paranjape, Michele Bevilacqua, Fabio Petroni, and Percy Liang. 2023. "Lost in the Middle: How Language Models Use Long Contexts." arXiv preprint 2307.03172. https://arxiv.org/abs/2307.03172 [GenAI]

Modran, Horia Alexandru, et al. 2025. "Retrieval-Augmented Generation (RAG) Chatbots for Education: A Survey of Applications." *Applied Sciences* 15(8): 4234. https://www.mdpi.com/2076-3417/15/8/4234 [GenAI]

Nye, Benjamin D., Arthur C. Graesser, and Xiangen Hu. 2014. "AutoTutor and Family: A Review of 17 Years of Natural Language Tutoring." *International Journal of Artificial Intelligence in Education* 24: 427–469. https://link.springer.com/article/10.1007/s40593-014-0029-5 [ITS, dialog-based]

Roschelle, Jeremy, Mingyu Feng, Robert F. Murphy, and Craig A. Mason. 2016. "Online Mathematics Homework Increases Student Achievement." *AERA Open* 2(4): 1–12. https://files.eric.ed.gov/fulltext/ED631720.pdf [ITS]

Sebastian, Lucia, J. M. Mosquera, and Diego Cancela. 2025. "Exploring the Use of Retrieval-Augmented Generation Models in Higher Education: A Pilot Study on AI-Based Tutoring." *Computers and Education: Artificial Intelligence.* https://www.sciencedirect.com/science/article/pii/S2590291125004796 [GenAI]

Selwyn, Neil. 2022. "The Future of AI and Education: Some Cautionary Notes." *European Journal of Education* 57(4): 620–631. https://onlinelibrary.wiley.com/doi/10.1111/ejed.12532 [Both — critical theory]

Stanford HAI. 2024. "How Harmful Are AI's Biases on Diverse Student Populations?" Stanford Institute for Human-Centered AI. https://hai.stanford.edu/news/how-harmful-are-ais-biases-on-diverse-student-populations [GenAI]

Steenbergen-Hu, Saiying, and Harris Cooper. 2013. "A Meta-Analysis of the Effectiveness of Intelligent Tutoring Systems on K–12 Students' Mathematical Learning." *Journal of Educational Psychology* 105(4): 970–987. https://psycnet.apa.org/record/2013-31551-001 [ITS]

Steenbergen-Hu, Saiying, and Harris Cooper. 2014. "A Meta-Analysis of the Effectiveness of Intelligent Tutoring Systems on College Students' Academic Learning." *Journal of Educational Psychology* 106(2): 331–347. https://www.researchgate.net/publication/263918046 [ITS]

VanLehn, Kurt. 2011. "The Relative Effectiveness of Human Tutoring, Intelligent Tutoring Systems, and Other Tutoring Systems." *Educational Psychologist* 46(4): 197–221. https://www.tandfonline.com/doi/abs/10.1080/00461520.2011.611369 [ITS]

Wang, Rose E., Ana T. Ribeiro, Carly D. Robinson, Susanna Loeb, and Dora Demszky. 2024. "Tutor CoPilot: A Human-AI Approach for Scaling Real-Time Expertise." arXiv preprint 2410.03017. https://arxiv.org/abs/2410.03017 [GenAI, hybrid human–AI]

WestEd. 2020. "Efficacy of ASSISTments Online Homework Support for Middle School Mathematics Learning: A Replication Study." https://www.wested.org/support/efficacy-of-assistments-online-homework-support-for-middle-school-mathematics-learning/ [ITS]

---

## Open questions for the chapter author

1. The single biggest open question: **is context-anchoring (RAG to current section + prerequisites) sufficient to convert a Bastani-style "GPT Base" failure into a Bastani-style "GPT Tutor" success, or does the guardrail discipline have to be separate from the context injection?** The literature treats these as separate variables; medhavy's design effectively bundles them. A planned A/B inside medhavy could be a publishable result.

2. **Does Khanmigo work?** No independent RCT measuring durable learning outcomes outside the Khan Academy ecosystem is yet in print. The vendor-sourced satisfaction and growth data are real but do not answer the learning question.

3. **What is the right "student model" for a generative chatbot?** ITS student models are structured (skill mastery vectors, error catalogs). Generative-chatbot student models are typically a summary in natural language. Whether structured beats unstructured for downstream learning is an open empirical question.

4. **Equity stratification.** The Steenbergen-Hu *g* = −0.18 for low-achieving K–12 students in ITS, and the Stanford HAI bias findings for generative AI, both indicate that aggregate effect sizes hide differential impact. Whether medhavy's design preferentially helps or harms specific learner populations is not yet measurable; building the measurement in from the start is recommended.

5. **The vendor-RCT gap.** Almost every named system (Khanmigo, Duolingo Max, LearnLM) has vendor-sourced effectiveness claims and a partial, often-friendly research literature. The medhavy book should name this gap explicitly and not treat vendor blog posts as equivalent to peer-reviewed RCTs.

---

*End of pantry research note. Move material into chapter drafts as relevant; do not cite this file in the book — cite the primary sources directly.*
