# Chapter 3 — Ask AI: When the Student Needs to Think, Not Receive

**The reader learns what Ask AI is, why it is deliberately constrained, and when that constraint is the point.**

---

## Opening case

The most natural assumption about an AI tool in a textbook is that it answers questions. A student raises her hand, the AI answers. A student types into a box, the AI responds. That is what the technology can do. That is what every general-purpose chatbot the reader has ever used does.

**Ask AI [Humanitarians AI internal framework] does not answer questions.** This is not a limitation. It is the design.

A student who gets the answer from an AI has offloaded the cognitive work that produces learning. The answer is now the AI's. The student has read it. The student feels she understands. The schema that would have formed had she generated the answer herself has not formed. Two weeks later, in an unassisted exam, the borrowed competence collapses. This is the Bastani finding in Chapter 1, restated in the first person.

Ask AI is built to prevent this. It refuses to produce complete answers to conceptual questions inside its grounding corpus. It returns hints, clarifying questions, redirects to material the student has already encountered. The student has to do the retrieval. The student has to articulate the answer. The student is sometimes wrong; the student sometimes has to ask again; the friction is the feature.

The chapter's job: install the distinction between Ask AI and a chatbot, sharply enough that the reader cannot conflate them again. If she finishes this chapter still thinking of Medhavy as "a chatbot bolted onto a PDF" (a misconception the TIKTOC catalogs as the first and most common), the rest of the book does not work.

---

## What Ask AI actually does

Three architectural commitments hold the design together. Each one descends from a specific finding in cognitive science.

**Commitment 1: Grounded retrieval, not free generation.** Ask AI runs as a retrieval-augmented generation system — RAG, in the technical literature. The relevant plain-language version: when a student asks a question, the system retrieves passages from the textbook the student is reading (and only that textbook), and the language model is constrained to answer using those retrieved passages. The model cannot wander off-corpus. It cannot pull in confidently-stated facts from its training data that may or may not be true. The original RAG paper (Lewis et al., NeurIPS 2020) demonstrated that grounded answers are more accurate and more defensible than free-generated ones; the educational application of the same architecture is that the AI cannot teach the student anything the institution has not approved. The retrieval corpus is the curriculum. The model is forced to live inside it.

For a curriculum director, this commitment has a concrete consequence: a student using Ask AI on the AI+1 pharmacology Kindle cannot get the AI to explain a drug interaction the textbook does not cover, in language the textbook does not endorse, with a confidence the textbook does not justify. The boundary of the AI's behavior is the boundary of the institution's approved content. This is not a feature you can replicate by handing students a general-purpose chatbot.

**Commitment 2: Hints, not answers.** The system prompt that wraps the model commits it to a tutoring stance — ask clarifying questions, offer hints that redirect to the relevant passage, refuse to produce a complete worked solution. This is the architectural lever Bastani's GPT Tutor condition pulled, and it is the lever that bought the 17-percentage-point gap between GPT Base and GPT Tutor in Chapter 1. The commitment is not a soft preference; it is a refusal at the prompt level, enforced by every interaction.

The cognitive science underneath is older than RAG by 40 years. Slamecka and Graf demonstrated the generation effect in 1978: words that the learner *generates* are remembered better than words the learner *receives*. The mechanism is straightforward — generation forces retrieval, retrieval engages the existing schema, schema engagement strengthens the schema. Reception bypasses all three steps. The mechanism is the same whether the learner is generating a word, a sentence, an explanation, or a clinical decision. Ask AI's hints-not-answers commitment is the generation effect implemented in software. A hint redirects the student to a passage she has access to; producing the answer is now her cognitive work, not the AI's.

**Commitment 3: Calibrated assistance — the assistance dilemma.** Koedinger and Aleven, working on cognitive tutors at Carnegie Mellon, named the dilemma in a 2007 paper that should be required reading for anyone designing tutoring software. Too much help produces offloading; too little help produces shutdown. The curve is an inverted U. The optimal level of assistance is the level that keeps the student in productive struggle — the zone where she is doing real cognitive work and not stuck so badly that she abandons the attempt. Ask AI's hint sequences are designed to walk that curve. First a Socratic question; if the student is still stuck, a more pointed question; if she is still stuck, a hint that names where in the textbook to look; rarely, a hint that names the partial answer. The system escalates only when the student demonstrates she is engaged and stuck, not when she demonstrates impatience.

The dilemma is empirically real. ASSISTments, the math-tutoring system Heffernan and colleagues have run at scale since the early 2000s, has measured hint-ladder effects in randomized trials and found exactly the inverted-U Koedinger and Aleven predicted. Productive struggle is not a slogan; it is a measurable cognitive state, and the assistance level that produces it is a tunable parameter. Ask AI's hint design is tuned against the same parameter, calibrated to the specific textbook the student is reading.

A useful image for the three commitments together: the master craftsman watching the apprentice from across the workshop. Tetsuro Matsuzawa documented this pattern formally in chimpanzee nut-cracking — the adult is present, the juvenile is working, the adult does not intervene unless the juvenile demonstrates engagement plus stuckness; the adult never simply *does it for* the juvenile. The pedagogical pattern is older than humans; Ask AI is one software implementation of it.

---

## The Bastani finding applied to Ask AI

Chapter 1 made the architectural argument in the negative — unguarded AI can produce learning harm because the wrapper around the model is the variable. Ask AI is the positive instance. It is the architecture Bastani's GPT Tutor condition prefigured, productionized with RAG grounding to a specific textbook and integrated into a curriculum.

Run the comparison cleanly. In Bastani, the GPT Base condition produced harm because the model gave students complete answers; students offloaded the cognitive work; the schema did not form; in the unassisted exam, the borrowed competence collapsed. The GPT Tutor condition produced no harm (and no clear gain over no-AI control) because the prompt-engineered guardrail prevented the offloading without producing a strong enough generation effect to outpace the control group's pencil-and-paper practice.

Ask AI extends GPT Tutor in two ways. First, RAG grounding — the model is constrained to the textbook, not just to a tutoring style. Bastani's GPT Tutor could still draw on its general training; Ask AI cannot. Second, integration with the rest of the loop — the bandit (Chapter 8) decides when to deploy Ask AI versus when to deploy Quiz Me, Case Study, or Glimmer; the measurement layer (Chapter 7) feeds back whether the chosen mode is producing learning evidence; the next session adjusts. Bastani's GPT Tutor was a four-session intervention with no measurement-driven adaptation. Ask AI is the same architectural commitment extended into a continuous, measured, adapted process.

The chapter is not promising that Ask AI produces learning gains. The Bastani evidence is for the *guardrail* — it shows that the guardrail prevents harm and matches no-AI control. The case for gains over the control group depends on the loop, which is the topic of Chapter 8. What the chapter is promising is the same thing the Bastani study demonstrated: *the architectural commitment to hints-not-answers is the difference between harm and not-harm.* Ask AI makes that commitment. A general-purpose chatbot does not. The choice between them is the choice between two different deployment outcomes.

---

## When Ask AI is the right mode

Ask AI is the *acquisition* mode in the four-mode sequence. It is designed for the student who has no schema for a concept yet, or who has a partial schema and is still building it. The cognitive operation is: encounter the concept, articulate what you do and do not understand, generate a hypothesis about the mechanism, encounter feedback in the form of redirecting questions, repair the hypothesis, try again. The student is acquiring a representation.

Concrete examples from the health sciences:

- A first-year nursing student encountering pharmacology for the first time, asking "what is beta blockade?" The schema is not present; the textbook chapter has the material; Ask AI's job is to redirect the student to the passage on sympathetic activity and ask her what she thinks would happen if those receptors were blocked. The student generates the answer; the schema starts forming.

- A pharmacy student encountering ACE inhibitors after weeks of studying the renin-angiotensin system. The schema is partial — the student knows the cascade in abstract but has not connected it to the clinical effect. Ask AI's job is to ask what mechanism the student would predict from her understanding of the cascade, and to redirect her back to the chapter when her prediction does not match the observed clinical effect.

- A medical student preparing for a pathophysiology exam, working through the citric acid cycle. The student understood it in undergraduate biochemistry and has forgotten the details. Ask AI's job is to prompt retrieval — "what enters the cycle, what leaves it, where does the energy come from?" — and redirect to the textbook when retrieval fails. The schema is dormant; Ask AI is reactivating it.

In each case, the right cognitive operation is generation under uncertainty, with the textbook as scaffold and the AI as Socratic prompt. The student is doing the work. The AI is making sure she has somewhere productive to do it.

Lauren Resnick, working at the Learning Research and Development Center in Pittsburgh through the 1980s and 90s, called this pattern "accountable talk" — students articulate their reasoning, the partner (teacher, peer, or in this case software) responds with questions that hold the reasoning accountable to evidence and to its own internal logic. Ask AI is a one-on-one software implementation of accountable talk. Resnick built her framework for classroom discussion; the architectural commitments transfer cleanly to the tutoring context because the cognitive operation — articulate, justify, respond — is the same.

---

## When Ask AI is NOT the right mode

Three failure cases, each one important enough that the chapter has to name them. The four-mode sequence is a sequence, not a menu; using Ask AI for a job another mode is designed for produces frustration without learning.

**Failure case 1: Factual recall on well-understood concepts.** A senior nursing student who has demonstrated understanding of beta blockade six times and is rehearsing for the NCLEX in three months. She wants to retrieve the names of three beta-1 selective agents. She does not need to be Socratically redirected to the chapter she has already mastered. Ask AI applied here is patronizing — it asks the student to generate when she has nothing left to generate; the work is retrieval, not acquisition. The right mode is Quiz Me (Chapter 4), which is designed for durable retrieval and uses spaced repetition to schedule recall practice at increasing intervals. Asking Ask AI here is using a Socratic seminar to do flashcard work.

**Failure case 2: Application under clinical ambiguity.** A nursing student presents the case of a 72-year-old patient with new-onset atrial fibrillation, hypertension, mild renal impairment, and asthma. Should beta blockade be initiated? The student knows the mechanism; she knows the side-effect profile; she is being asked to *decide* under multiple competing considerations with no single right answer. Ask AI's hints-not-answers stance is the wrong tool — there is no single answer in the textbook for the AI to redirect her to. The right mode is Case Study (Chapter 5), which presents a faculty-reviewed clinical scenario with a graduated assistance ladder calibrated for ambiguous decision-making. Using Ask AI here produces the student demanding "just tell me yes or no" and the AI continuing to ask her what she observes about the patient — both parties frustrated, neither learning.

**Failure case 3: Generative work.** A pharmacy student is asked to design a patient-education protocol for a newly diagnosed hypertensive patient who reads at a fourth-grade level, speaks Spanish primarily, and has expressed distrust of medical professionals. The task is *generative* — the student is producing something that did not exist before, calibrated to a specific context, defended by reasoning about competing constraints. Ask AI cannot replace this work. The right mode is Glimmer (Chapter 5), which is designed for open-ended generative assignments with an AI pre-grading reviewer that asks one targeted question about the weakest dimension of the student's work. Ask AI applied to a Glimmer-shaped task produces the student asking the AI to generate the protocol and the AI refusing — at which point the student often leaves and uses a general-purpose chatbot. The institutional mismatch (wrong mode for the cognitive operation) becomes a wrapper-failure (student exits the guarded tool for an unguarded one).

The principle: **Ask AI is the first mode in the sequence, not the only mode.** It does one cognitive operation — acquisition under uncertainty with grounded scaffolding — well. It does not do retention, application under ambiguity, or generative work. Asking it to do those jobs produces the failure modes above. The other three modes exist because the cognitive operations are different.

---

## What Ask AI cannot do

Worth being explicit about the boundaries, because vendor marketing tends to overpromise.

Ask AI cannot make knowledge durable. Generation effect helps; spaced retrieval helps more, especially across weeks and months. The student who used Ask AI to acquire a schema in week 3 will lose much of it by week 8 if nothing else is scheduled. Quiz Me is what makes the schema stick.

Ask AI cannot force application under ambiguity. The Socratic move only works when the answer is grounded in a passage the student has access to. When the situation requires weighing competing considerations with no textbook-correct answer, Ask AI has no anchor to redirect to. Case Study is what produces application under ambiguity.

Ask AI cannot produce generative capability. The work of designing a novel patient-education protocol, writing a clinical reasoning narrative, defending a treatment plan to a skeptical colleague — none of this is hint-redirection territory. Glimmer is the mode for generative work, and it operates on different cognitive science (process feedback, dimensional scoring, emergent portfolio).

Ask AI cannot replace the human instructor. If the student is so stuck that the assistance dilemma's lower bound has been crossed — shutdown, abandonment, the student closing the app — the right intervention is a human. The book is not arguing software can replace teachers; it is arguing software can extend the reach of teachers to deployment scales where the human alone cannot keep up. When the human is available and the class is small, the human is the better tool; this is the entire argument of Chapter 2.

The honest summary: Ask AI is *one* commitment, designed to do *one* cognitive operation, at the right *one* moment in the four-mode sequence. The institution that adopts Medhavy is buying a system in which Ask AI is the first of four interlocked tools. The institution that wants to use Ask AI as the whole system has misunderstood the design.

---

## Worked example: two responses to "What is beta blockade?"

A first-year medical student opens her AI+1 cardiopharmacology Kindle and asks the question. Two responses below — one from an unguarded chatbot, one from Ask AI. Same student, same question, different architecture.

**Unguarded chatbot response:**

> "Beta blockade refers to the pharmacologic antagonism of beta-adrenergic receptors. Beta-1 receptors, predominantly located in cardiac tissue, mediate increased heart rate and contractility in response to sympathetic stimulation. Beta-2 receptors, located in bronchial smooth muscle and vascular smooth muscle, mediate bronchodilation and vasodilation respectively. Beta blockers competitively antagonize these receptors, producing decreased heart rate, decreased myocardial contractility, decreased cardiac output, and — at higher doses — bronchoconstriction. Clinically, selective beta-1 blockers (metoprolol, atenolol, bisoprolol) are preferred in patients with reactive airway disease to minimize beta-2 effects, while non-selective beta blockers (propranolol, nadolol) are used in conditions where beta-2 blockade is also desired, such as portal hypertension. Common side effects include bradycardia, fatigue, sexual dysfunction, and masking of hypoglycemic symptoms in diabetic patients. Beta blockade is contraindicated in decompensated heart failure (though useful in compensated heart failure as a long-term therapy)..."

(The response continues for another 200 words. It is accurate. It is fluent. It is comprehensive.)

What the student does: reads, nods, highlights one phrase, moves on. Time on page: 4 minutes 12 seconds. Self-reported comprehension: high. Schema formed: weak. The student has consumed the chatbot's schema; she has not built her own. Two weeks later, on an unassisted exam, the question "what would you predict happens to heart rate when you block beta-1 receptors?" produces the answer "decreased" with confidence — but the question "why" produces a long pause. The "why" was the chatbot's; the student never generated it.

**Ask AI response:**

> "Before I get there — what did you observe in the chapter on sympathetic activation about what happens to heart rate when norepinephrine binds beta-1 receptors? And what would you predict happens if we block those receptors with a competitive antagonist?"

What the student does: re-reads the prerequisite section (3 minutes). Returns to Ask AI. Articulates her prediction: "I think the heart rate goes down because the receptors that increase heart rate are blocked." Ask AI responds: "Good — that's the core mechanism. Now what does the textbook say about the difference between beta-1 and beta-2 effects? Why does it matter for a patient with asthma?"

The student now retrieves a second piece of information, articulates a connection, and constructs the link between mechanism and clinical implication. Time on page: 11 minutes 30 seconds. Self-reported comprehension: medium ("I had to look stuff up"). Schema formed: strong. Two weeks later, the same exam question produces the same answer with the same confidence — and the "why" is available because the student generated it.

The student who received the question had to think. The student who received the answer did not have to. That is the design. That is the entire chapter compressed into two paragraphs.

A measurement note for the curriculum director: the unguarded-chatbot interaction looks better on a Canvas dashboard (lower time-on-page, higher self-reported comprehension). The Ask AI interaction looks worse on the same dashboard. The seven friction signals (Chapter 7) are designed to flip the comparison — the longer time-on-page, the lower self-reported comprehension, and the evidence of retrieval activity register as Y1 (Temporal Engagement) and Y5 (Social Knowledge Texture). The chapter's point in advance: do not trust the dashboard. Trust the architectural commitment and the measurement layer designed to detect it.

---

## Exercises

1. **(Apply, to your own curriculum)** Pick one concept in your domain — a specific topic in pharmacology, anatomy, or pathophysiology that students reliably encounter for the first time at a known point in your curriculum. Write the Ask AI response to the question "Can you explain this to me?" The response should be a question (or two), grounded in a prerequisite the student has access to, that requires her to retrieve and articulate rather than receive. The exercise is to make sure you can write the move yourself — and to confirm you have something Ask AI can redirect to, which is a curriculum-design check.

2. **(Analyze)** Identify a concept in your curriculum where Ask AI would be the *wrong* mode — patronizing, paralyzing, or mismatched to the cognitive operation. State the concept, state why Ask AI would fail there, and name which mode (Quiz Me, Case Study, or Glimmer) would be the right tool. The exercise is testing whether you can see the four-mode sequence as a sequence, not a menu.

3. **(Evaluate, to your own deployment)** In your deployment, what proportion of student questions are *acquisition* questions — the student does not yet have a schema for the concept — versus *retrieval* questions — the student has a schema and is forgetting? The proportion is rarely 50/50, and the answer matters. If your deployment is heavy on acquisition (early in a curriculum, intro-level course, students with weak prior preparation), Ask AI does a lot of work. If your deployment is heavy on retrieval (advanced students, board prep, refresher courses), Ask AI does less work and Quiz Me does more. Estimate the proportion. The estimate matters more than the precision; the exercise is to get you thinking in terms of which mode each student question warrants.

---

## Common misconceptions

**"Ask AI is just a chatbot."** TIKTOC misconception #1, the chapter's primary lift. Ask AI is architecturally different from a chatbot: grounded retrieval, hints-not-answers, calibrated assistance. A chatbot has none of these commitments by default. The visual interface looks similar (a text box, a response area), but the behavior is not. If the reader finishes the chapter still thinking of Ask AI as a chatbot, she will conclude — wrongly — that her institution has already deployed something equivalent.

**"Hints are softer answers."** No. Hints redirect to material the student has access to. They do not partially answer. A hint says "look at the section on sympathetic activation"; it does not say "the answer is decreased heart rate, but I'll let you figure out why." The distinction is doing real work — partial answers still produce offloading; redirections do not.

**"Socratic means harder."** Socratic done badly is patronizing or paralyzing. Done well, it is *calibrated* — the assistance dilemma's optimum, the inverted U's peak. The Ask AI hint sequences are tuned to walk that curve. Students who report Ask AI is "hard" are often experiencing productive struggle, which is the intended state. Students who report Ask AI is "impossible" are experiencing the lower bound, which the system is designed to escalate past with progressively more pointed hints.

**"If students hate Ask AI, it's wrong."** Some students will hate Ask AI initially — they came in expecting an answer-giving chatbot, the way they have been trained by every other AI tool they have used. The chapter warns the reader: student satisfaction in early weeks is not the right metric. The right metric is whether retention at delay (Y6 in the friction-signal vocabulary) is better than what the alternative produces. Bjork's desirable difficulties principle — interventions that slow current performance often improve durable learning — predicts exactly this: Ask AI feels harder, produces better outcomes, and student satisfaction lags the outcomes by weeks.

---

## What would change my mind

The chapter's central claim is that the hints-not-answers architectural commitment, combined with RAG grounding, is the difference between an AI tool that supports learning and an AI tool that harms it. A finding that would revise this claim: a well-powered randomized trial showing that unguarded conversational AI access produces equivalent or better learning outcomes — measured on delayed, unassisted assessment — compared to a guarded Socratic interface, in a health-sciences population. The mechanistic argument (generation effect, assistance dilemma, RAG grounding) would survive, but the calibration would shift; the guardrail would become an optimization rather than a safety requirement. The current evidence (Bastani 2025 for the negative finding; ASSISTments and Peer Instruction for the positive structural finding) supports the chapter's claim; a contrary trial would warrant revisiting it.

---

## Still puzzling

- Do students develop "Ask AI literacy" over a semester? Some institutional reports suggest students learn to engage productively with Socratic questioning over time and dislike unguarded chatbots by the end of the term. Others report students never adapt and switch to general-purpose chatbots whenever possible. The variance is probably explained by institutional commitment (graded vs. optional use) and instructor messaging, but the evidence is anecdotal.

- How sufficient are prompt-level guardrails compared to system-level architecture? Bastani's GPT Tutor was prompt-only. Ask AI adds RAG grounding. Whether the RAG grounding is doing material work or whether the prompt alone would suffice in production is an open empirical question — and the answer matters for cost (RAG is more expensive than a prompt) and for how to assess vendors who claim similar capabilities.

- What happens at the boundary of the corpus — when a student asks Ask AI a question the textbook does not cover? The current behavior is to acknowledge the boundary and redirect to a human (instructor, advisor). Whether students accept that boundary or route around it is an institutional governance question, not a technical one.

- Cross-domain transfer. Most of the empirical literature on Socratic tutoring is in math and physics. Whether the same hint-ladder design works in clinical reasoning, which has structurally different uncertainty than math problems, is plausible but undertested.

---

## AI Wayback marginal callout — Allan Collins

> *Allan Collins, working at Northwestern through the 1980s and 90s, formalized what he called "cognitive apprenticeship" — the explicit teaching of expert thinking patterns by modeling, coaching, and progressively fading the scaffolding. The pattern's lineage runs through master craftsmen who never told the apprentice the answer; the apprentice learned by working, failing, watching, and trying again. Collins's contribution was naming the structural moves — modeling, coaching, scaffolding, fading, articulation, reflection — and showing how each could be implemented deliberately in a curriculum. Ask AI's hints-not-answers design is the "coaching" and "scaffolding" moves implemented in software, with the explicit "fading" step that Collins emphasized: the system gives more pointed hints when the student demonstrates engagement and shuts up when the student demonstrates competence. The handoff to the learner is not an afterthought. It is the design.*

---

## Bridge to Chapter 4

Ask AI gets the student to a first, fragile understanding of a concept. The student has generated the answer; the schema is forming. But schemas decay. The student who can articulate beta blockade in week 3 will not necessarily be able to articulate it in week 9, and certainly not at the board exam 14 months from now, unless something else happens in between.

That something else is retrieval practice — testing yourself on the material at intervals that match the natural forgetting curve. It is the most replicated finding in cognitive psychology, it is a hundred years older than Ask AI, and it is the mechanism the next mode is built on. Chapter 4. Quiz Me.

---

*Sources cited in this chapter: Lewis, P., Perez, E., Piktus, A., et al. (2020). Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks. NeurIPS 2020. arXiv:2005.11401. · Slamecka, N. J., & Graf, P. (1978). The generation effect. JEP: Human Learning and Memory, 4(6), 592–604. · Koedinger, K. R., & Aleven, V. (2007). Exploring the Assistance Dilemma. Educational Psychology Review, 19(3), 239–264. · Sweller, J. (1988). Cognitive load during problem solving. Cognitive Science, 12(2), 257–285. · Paul, R., & Elder, L. (2006). The Thinker's Guide to Socratic Questioning. · Mazur, E. (1997). Peer Instruction: A User's Manual. Crouch & Mazur (2001). American Journal of Physics. · Bastani et al. (2025) PNAS. · Resnick, L. B. (1999). Making America Smarter: A Surprising Plan for Raising Student Achievement. · Matsuzawa, T., et al. (2006). Cognitive Development in Chimpanzees. Springer. · Collins, A., Brown, J. S., & Newman, S. E. (1989). Cognitive apprenticeship. In Resnick (Ed.), Knowing, Learning, and Instruction.*
