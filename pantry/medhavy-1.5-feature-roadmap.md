# Medhavy 1.5 — Feature Roadmap
**What we're building, what already exists, and why each feature earns its place**

*Internal document for engineering and product alignment*

---

## How to read this document

Medhavy is built on a specific claim: that different kinds of learning require different kinds of help, and that the right help at the right moment produces meaningfully better outcomes than any single mode of instruction. Each feature in 1.5 corresponds to a distinct cognitive operation — acquiring a representation, making it durable, applying it under ambiguity, generating something new with it. The research behind each is not decorative. It is the reason the feature exists in the form it does and not some other form.

This document covers:

- **What already exists** — the Ask AI mode, the context-aware chatbot that ships with the current Cancer Biology and Physics Vol. 1 textbooks
- **What 1.5 adds** — Quiz Me, Case Study, and Glimmer
- **Why each feature is designed the way it is** — the research rationale, including the failure modes each design choice is trying to avoid
- **How the four modes fit together** — the cognitive logic that makes the combination more than the sum of its parts

The Medhavy 2.0 architecture — specifically the contextual bandit that will learn to select between modes per student per concept — is described in an appendix. Understanding what each mode does and why is a prerequisite for understanding what 2.0 is optimizing.

---

## The platform as it exists today

### Ask AI — the context-aware AI tutor

**What it is.** Every page of every Medhavy textbook has a chat panel. Students ask questions; the AI answers. Two things distinguish the Medhavy tutor from a general-purpose AI tool. First, it is RAG-grounded — it retrieves relevant passages from the current textbook and anchors its answers in that content. It cannot fabricate facts the textbook does not contain. Second, it is context-aware — it knows which chapter and section the student is reading when they ask, and it maintains a short-term memory of what the student has asked in the current session and a long-term learner profile across sessions.

The Cancer Biology textbook runs a Mixture-of-Experts routing layer that classifies each question and routes it to one of six expert personas — mechanism, diagnostics, treatment, definitions, navigation, and general — before calling GPT-4o-mini. The Physics Vol. 1 textbook extends this with a physics widget tool layer: when a student asks a quantitative question, the AI can generate an inline physics plot or chart directly in the chat response.

**The research case.** The most important finding in the AI tutoring literature is also the most counterintuitive: an AI tutor designed to be helpful can actively harm learning. Bastani et al. (2025, *PNAS*) ran a randomized controlled trial with approximately 1,000 high school students. Students with access to unguarded GPT-4 during practice sessions scored 48% higher than the control group during the practice period — and 17 percentage points *lower* on a subsequent exam without AI access. The students who used the AI most fluently during practice had offloaded the cognitive work that practice is supposed to build. Their performance during practice was the AI's performance, not theirs.

The same study ran a second condition: GPT-4 with teacher-designed guardrails that refused to give answers and instead provided structured hints. That group showed no harm — their exam scores were statistically indistinguishable from the no-AI control.

This is the design constraint that governs Ask AI. The tutor is not optimized to make the student feel helped. It is designed to make the student think. It asks clarifying questions before answering. It offers graduated explanations when a student is stuck rather than providing the final answer. It routes mechanism questions to a persona that explains the causal process, not the conclusion. The RAG grounding is not just an accuracy feature — it is a guardrail against the fluency trap, because the tutor can only answer from the textbook, which means the student is always being directed back to material they are supposed to be building a relationship with, not bypassing.

The context-awareness serves the same function. A student who has been asking about apoptosis for fifteen minutes and then asks "wait, what is the mitochondria again?" gets a different response than a student asking the same question cold. The tutor knows where the student is and what they have been working through, which means its Socratic moves are calibrated to actual gaps rather than generic pedagogy.

**What it does not do.** Ask AI does not make retrieved knowledge durable. It does not force the student to apply knowledge under ambiguity. It does not ask the student to generate anything novel. These are the jobs of the three modes being added in 1.5.

---

## What 1.5 adds

The single Ask AI button becomes four. The interface presents: Ask AI, Quiz Me, Case Study, Glimmer. Each mode is appropriate for a different moment in a student's relationship with a concept. The four together constitute a complete learning environment; none alone is sufficient.

---

### Quiz Me — spaced retrieval practice

**What it is.** Quiz Me is a flashcard-register spaced repetition system scheduled by FSRS (Free Spaced Repetition Scheduler), the open-source algorithm now default in Anki. Items are generated from the concept node map that the professor builds during the Tic TOC curriculum design session. When a student opens Quiz Me for a concept, the system presents a set of items — drawn from the current concept node, recent related nodes, and prerequisite nodes where mastery is below threshold — and the student attempts retrieval, rates their recall (Again / Hard / Good / Easy), and the algorithm schedules the next review based on a predicted retrievability model.

The interface is designed explicitly as a flashcard session, not a quiz. There is no score at the end of a session. There is a completion event — "Done for today" when the due-count reaches zero. Tomorrow's count is already scheduled.

**The research case.** The testing effect is the most reliably replicated finding in cognitive psychology. Roediger and Karpicke (2006) showed that students who retrieved information from memory performed substantially better on a one-week delayed test than students who spent the same time re-reading — even though the re-readers showed higher performance immediately after the study session. Adesope, Trevisan, and Sundararajan's 2017 meta-analysis of 188 experiments found a pooled effect of g = 0.51 for practice tests versus re-studying, and g = 0.93 versus no activity. These are among the largest and most consistent effects in the educational psychology literature.

The spacing principle adds further gains independent of retrieval. Cepeda et al.'s 2006 meta-analysis of 317 experiments established that distributing practice across time produces more durable retention than massing it, and Cepeda et al. (2008) showed that the optimal inter-study interval scales with the retention horizon — a student who needs to retain a concept for a fourteen-week semester should review it at a different interval than a student reviewing for a next-day exam. FSRS implements this scaling. Unlike SM-2 (the previous standard in Anki), FSRS represents each item with three latent variables — Difficulty, Stability, and Retrievability — and trains its scheduling parameters on hundreds of millions of review logs, producing approximately 20-30% fewer reviews for the same target retention rate.

In medical education specifically, Kerfoot and colleagues ran a series of randomized controlled trials of spaced retrieval practice delivered to urology residents and medical students. Their 2010 Annals of Surgery trial showed that spaced education generated transfer — improved performance on novel diagnostic skill items, not just the practiced items — with effects persisting to long-term follow-up. Medical students in cohort studies who used Anki extensively showed substantially better course exam performance than those who did not, with mature-card counts explaining over a third of the variance in scores in one cohort study.

**The design choices that matter most and why.**

The decision to use a flashcard register rather than a quiz register is not aesthetic. Habit research (Wood, 2019; Lally et al., 2010) establishes that daily voluntary use of a study tool requires a habit loop: a consistent cue, a low-friction action, and a satisfying completion event. The Zeigarnik effect — the cognitive pressure created by an unfinished open task — is the mechanism behind the due-count counter. A visible count of cards due today creates an open task the brain wants to close. This is why the due-count is displayed on the home screen, in the chapter navigation, and as a badge on the app icon. When the count reaches zero, the session is done. The closure event is the reward. A quiz register that ends with a score produces assessment anxiety and study-session pacing rather than daily maintenance behavior.

The interleaving of prerequisite items alongside current-concept items is grounded in Rohrer and Taylor's (2007) finding that interleaved practice produced 74% accuracy on delayed tests versus 49% for blocked practice — despite the blocked group performing better during the practice sessions themselves. The mechanism is discrimination learning: interleaving forces the student to identify which concept or tool the current item requires, which is exactly the cognitive operation clinical reasoning and problem-solving demand. Including 20-30% prerequisite items in every session also serves a diagnostic function: when a student consistently fails prerequisite items, the system has evidence that the current concept's difficulties are upstream, not local.

The priority score — `priority = α × prerequisite_depth + β × importance_tier + γ × (1 - fsrs_retrievability) + δ × frequency_tier` — is the answer to the failure mode where pure recall-based scheduling under-trains foundational concepts. A student who reviews consistently can master a rare biochemical pathway while losing access to a foundational clinical concept, simply because the foundational concept's FSRS score looks fine while the rare pathway keeps failing. The importance and frequency tiers, set by the professor at Tic TOC time, inject domain knowledge into the scheduling algorithm that recall data alone cannot capture. The aviation pedagogy principle governs high-importance concepts specifically: regardless of FSRS predictions, any concept node tagged `importance_tier = 'high'` is reviewed at least every 14 days. Rare-but-critical content — anaphylaxis recognition, sepsis criteria, the conditions where a standard management algorithm does not apply — gets mandatory scheduling rather than recall-dependent scheduling.

The gate — Quiz Me for section N is locked until the student has engaged with section N for at least three minutes or has scrolled to the end — addresses Bastani's finding directly. Retrieval practice requires something to retrieve. A student who attempts Quiz Me before reading the section will either guess randomly (producing noise in the FSRS model that will degrade future scheduling) or succeed through surface heuristics (which the algorithm reads as mastery and downschedules, leaving real gaps undetected). The gate is not a restriction. It is a quality control measure for the signal the system is generating.

**Backlog management.** When a student falls behind and the due-count exceeds 50, the system surfaces a Quick Catch-Up mode covering the 15 highest-priority items only. Presenting a 60-minute backlog session to a student who has missed a week produces abandonment, not recovery. The Quick Catch-Up is the recovery path.

---

### Case Study — clinical reasoning under ambiguity

**What it is.** Case Study presents a pre-written, professor-approved clinical or domain scenario anchored to the concept node the student is currently working on. The scenario is genuinely ambiguous — it does not have a single correct answer telegraphed in the setup. The AI facilitates discussion using a graduated assistance ladder, moving from broad evidential questions ("What in the case points one direction or another?") to partial scaffolding ("Here is one reasoning chain a clinician might use — what would you push back on?") to synthesis ("Here is the consensus reading — now reconstruct the reasoning that produced it"). The AI never gives the answer. When a student asks for it directly, the response is consistent: "I can't do that — the reasoning is the point. Let's try a different angle."

Cases are authored by the professor and approved before any student sees them. AI-generated cases are not permitted in 1.5.

**The research case.** Case-Based Learning has a substantial evidence base in health professional education. Thistlethwaite et al.'s 2012 BEME systematic review of 104 studies across medical, dental, nursing, and pharmacy programs found consistent evidence that CBL produces student satisfaction and self-reported clinical reasoning gains, with modest evidence of advantages on skill-application tasks. The Dochy et al. (2003) meta-analysis of problem-based learning found a consistent trade-off: PBL produced a modest negative effect on knowledge breadth (approximately -0.22 SD versus lecture) and a substantial positive effect on skills application (approximately +0.46 SD). CBL and PBL are not the same — CBL assumes preparation, uses faculty-curated cases, and operates at shorter time scales — but the trade-off is similar. Case-based work consistently produces better application and worse recall than direct instruction, which is exactly the right trade given that Quiz Me handles the recall side of the equation.

The design of the graduated assistance ladder follows Koedinger and Aleven's assistance dilemma framework (2007), the most important empirical principle governing when to help and when to hold back in an intelligent tutoring context. Their finding: there is an optimal amount of assistance for any given learner state. Too little, and the student fails and disengages. Too much, and the student offloads rather than learns. The optimum is curvilinear and depends on prior knowledge. The ladder operationalizes this: the system starts at the minimum effective level of scaffolding and escalates only when the student demonstrates genuine engagement at the current level, not simply when time has passed.

The mastery-based adjustment — students below 0.6 mastery on the concept node start at Level 1 and proceed slowly; students above 0.8 start at Level 3 — implements Kalyuga et al.'s (2003) expertise reversal effect: instructional supports that help novices hurt experts. A scaffolded hint that is necessary for a struggling student is patronizing and wasteful for a proficient one. The Case Study facilitation calibrates its starting point based on what the Quiz Me and Ask AI signals say about where the student actually is.

**Why cases must be pre-written and professor-approved.** The prohibition on AI-generated cases is not a temporary conservatism. It reflects a specific risk that is documented in the medical LLM literature. Singhal et al.'s evaluation of Med-PaLM (2023, *Nature*) found that even a model achieving 86% accuracy on USMLE-style questions — the best available at time of publication — produced wrong answers in roughly one in seven cases, delivered with the same fluent confidence as correct ones. A case scenario that contains a plausible-sounding but incorrect clinical claim — a wrong first-line treatment, an outdated staging criterion, a fabricated drug interaction — does not fail loudly. It fails silently, propagating as a student misconception that may persist through clinical training. Pre-written, faculty-reviewed cases have bounded failure modes: the review process catches errors, and the review standard (similar to AAMC MedEdPORTAL's peer review criteria) is established practice in medical education. AI-generated cases have unbounded failure modes, and the cost of a wrong answer in clinical content is asymmetric.

**What the session logs capture.** Case Study sessions are logged at a granularity that serves the 2.0 bandit's training data: which assistance level the student reached, how many AI turns preceded each escalation, whether the student disengaged before three minutes, and the AI-assessed reasoning quality of the student's final response (poor / developing / proficient). These signals distinguish "the student found this case too hard" from "the student found this case unengaging" from "the student worked through this productively" — three outcomes that warrant different next-mode selections from the bandit.

---

### Glimmer — generative creative assignment

**What it is.** Glimmer is a creative, non-trivial assignment anchored to a specific concept node. There is no correct answer. The student produces something that did not exist before: a proposed clinical protocol, a mechanism explanation applied to a novel context, a critique of an existing approach, a design for an intervention. The assignment is graded on five dimensions: WHY (is the problem framing specific and contextual, not generic?), Usefulness (is there a real application pathway?), Mechanism (are the causal steps specified, not just the outcome?), Defensibility (can the student argue for this against alternatives?), and Specificity (are measurements, quantities, and concrete details present?).

Before the instructor grades the submission, the AI pre-grading reviewer reads it, identifies the weakest dimension, and asks the student one targeted interrogation question about it. Not "be more specific" — a precise question about the specific gap: "You claim that X will produce Y, but you don't explain the mechanism by which this occurs. Walk me through the specific causal steps between X and Y." The student responds. If the response meets threshold on defensibility and specificity, the submission is released to the instructor. If not, the AI asks one follow-up question — a maximum of two rounds of AI interrogation before instructor review regardless.

Eight to twelve Glimmers across a course compose into a term project the student does not know they are building until weeks ten and eleven, when the system reveals that all prior submissions are now a portfolio and a synthesis assignment unlocks.

**The research case.** The Glimmer is an ill-structured problem in the Jonassen (1997, 2000) sense: it has no single correct solution, no agreed evaluation criteria, and requires the student to specify the problem before solving it. The evidence base for ill-structured problem-solving instruction — particularly Belland, Walker, Kim and Lefler's 2017 meta-analysis of computer-based scaffolding for STEM cognitive outcomes (g = 0.46, 144 studies) — establishes that scaffolded ill-structured work produces meaningful cognitive gains when the scaffolding is contextualized, fades appropriately as competence grows, and addresses conceptual rather than purely procedural support. The Glimmer's rubric is the scaffolding. The AI pre-grading reviewer is the contextualized, targeted feedback mechanism that the scaffolding-fading literature identifies as the high-effect intervention: not "here is what is wrong" but "here is one specific question about the weakest part of your reasoning — answer it."

The AI reviewer's design follows the Graham, Hebert, and Harris (2015) meta-analysis of formative assessment in writing, which found that questioning-style feedback — asking the writer questions about their work rather than telling them what is wrong — produced effect sizes of approximately d = 0.40 to 0.50 on revision quality. Hattie and Timperley's (2007) landmark review of feedback establishes that process-level and self-regulation-level feedback produce the largest effects, while task-level feedback (here is the right answer) produces small effects and self-level feedback (you are doing well / poorly) produces near-zero or negative effects. The AI reviewer operates entirely at the process and self-regulation levels: "walk me through your causal reasoning" is a self-regulation prompt; "what observation would change your recommendation" is a process prompt. The AI never produces task-level feedback.

The emergent term project design is grounded in writing-process pedagogy (Murray, 1972; Elbow, 1973; Flower and Hayes, 1981): the final form of a substantial piece of work emerges from accumulation, and writers discover what they think by producing what they do not yet think. The pedagogical argument is that a student who knows they are building a term project optimizes for the grade on the project. A student who experiences each Glimmer as an interesting low-stakes weekly exercise optimizes for the exercise. The connective tissue — the synthesis that emerges in weeks ten and eleven — is more authentic when it is genuinely discovered rather than planned.

The five-dimension rubric maps onto the AAC&U VALUE rubrics for Critical Thinking and Inquiry and Analysis — dimensions that cannot be satisfied by quotation or length, only by demonstration of reasoning quality. This is the key property the rubric needs: a student cannot score well on Mechanism by writing more, only by specifying more precisely. Defensibility cannot be faked by hedging — hedging is the opposite of a defensible claim. Specificity catches the expert-novice gap that Chi, Feltovich, and Glaser (1981) documented: novices categorize problems by surface features; experts by deep principles. A specific Glimmer response is one that has reorganized surface features into principled application. A non-specific one has not.

**The anxiety failure mode and how it is mitigated.** Pekrun's (2006) control-value theory of achievement emotions predicts a specific failure mode for open-ended creative assignments: students who cannot see the destination (low perceived control) and care about their grade (high value) land in the anxiety quadrant, not the engagement quadrant. This is not a theoretical concern — Jonassen (2011) documents that ill-structured problems consistently produce higher reported anxiety than well-structured ones, with the gap largest for low-prior-knowledge learners. The USMLE-trained medical student population that Medhavy primarily serves has spent two or more years optimizing for closed-problem recognition tasks. Their first encounter with a Glimmer will frequently be experienced as evidence they cannot do the work.

Three mitigations are built into the design. First, early-semester Glimmers are heavily anchored to specific observations or cases from the textbook — the student is not operating in fully open space until week five or later. Second, the AI pre-grading reviewer's first response always acknowledges something the student did well before asking the interrogation question. Control is restored incrementally, not all at once. Third, the Glimmer surfaces in the interface as "Glimmer available" rather than "Glimmer overdue" — the framing is opportunity, not obligation.

The scaffolding-fading literature (Puntambekar and Hübscher, 2005; van de Pol, Volman, and Beishuizen, 2010) establishes that the early weeks of an ill-structured assignment should function as backwards-faded worked examples: week one presents a Glimmer with the framing pre-supplied, asking only that the student fill in mechanism and specificity; week two supplies the framing partially; week three is the first fully open Glimmer. This mirrors Renkl and Atkinson's (2003) backwards-faded worked-example sequence for cognitive skill acquisition. Whether Medhavy implements this fully in 1.5 or approximates it is a design decision — but the principle governs how the first three weekly Glimmer assignments should be structured.

---

## How the four modes fit together

The four modes are not interchangeable alternatives. They correspond to four distinct cognitive operations that learning research has established as necessary, sequential, and mutually insufficient.

**Ask AI** is for acquiring a representation. A student who does not yet have a schema for a concept needs explanation, elaboration, and the ability to ask clarifying questions. Ask AI serves this function. It is the entry point. Without a representation, there is nothing to retrieve, apply, or generate.

**Quiz Me** is for making the representation durable. A student who has a representation — who understood the lecture, read the chapter, got an explanation from Ask AI — has a fragile encoding. Retrieval practice, spaced over time, converts fragile encodings into robust ones. This is the mechanism that produces the kind of knowledge that survives an exam without a textbook, a clinical rotation without a reference, a board certification without time to review.

**Case Study** is for applying the representation under ambiguity. A student who can retrieve a concept reliably has not necessarily learned to deploy it in a real situation. Clinical cases and domain scenarios present the concept in a context where the right application is not obvious, where competing interpretations are legitimate, and where the reasoning process is the learning outcome rather than the correct answer. This is the cognitive operation that produces flexible, transferable knowledge rather than pattern-matched recall.

**Glimmer** is for generating something new from the representation. A student who can retrieve a concept and apply it to cases presented to them has not necessarily developed the capacity to use the concept as a tool for original thinking. Generative work — proposing, designing, specifying, defending — forces the student to reorganize their knowledge around principles rather than surface features. This is the operation that produces the expertise-level knowledge structure Chi and colleagues documented in expert physicists and clinicians: not more facts, but facts organized around deep principles that transfer to novel situations.

The Carnegie Foundation's studies of medical education (Cooke, Irby, and O'Brien, 2010) and engineering education (Sheppard, Macatangay, Colby, and Sullivan, 2008) reached the same diagnosis independently: professional education trains students for well-structured-problem performance while professional practice requires ill-structured-problem judgment. The four-mode architecture is Medhavy's answer to that gap — not by replacing the curriculum, but by ensuring that the full cognitive sequence is available alongside it.

---

## Appendix — Medhavy 2.0: the contextual bandit

The four modes described above generate signal data. In 1.5, the platform presents all four modes and lets the student choose. In 2.0, a contextual bandit learns which mode to surface at the natural re-entry point after each session — not by forcing the student's choice, but by making the right offer at the right moment.

The bandit is a class of reinforcement learning algorithm (Thompson Sampling is the proposed implementation) that, given a feature vector describing the student's current state on a concept node, selects the mode most likely to produce durable learning at this moment for this student. The feature vector includes FSRS retrievability, prerequisite mastery scores, concept importance tier, recency of Case Study and Glimmer engagement, and Glimmer rubric history.

The bandit cannot exist without 1.5's signal layer. Every case study escalation level, every Glimmer interrogation cycle, every Quiz Me card rating — these are the training data for the bandit's mode-selection policy. Without clean, complete, consistently-structured signals from 1.5, 2.0 learns from noise.

The reward signal — what the bandit is optimizing for — is delayed retrieval accuracy: seven days after the bandit selects a mode for concept C, a new Quiz Me item on concept C is offered. The student's accuracy on that item is the reward. This directly measures what the platform is for.

The 2.0 architecture, reward design decisions, and kickoff requirements are documented separately in the Medhavy 2.0 Strategic Roadmap.

---

## Key research citations

Adesope, Olusola O., Dominic A. Trevisan, and Narayankripa Sundararajan. 2017. "Rethinking the Use of Tests: A Meta-Analysis of Practice Testing." *Review of Educational Research* 87(3): 659–701.

Bastani, Hamsa, Osbert Bastani, et al. 2025. "Generative AI Can Harm Learning." *PNAS* 122(26): e2422633122.

Belland, Brian R., Andrew E. Walker, Nam Ju Kim, and Mason Lefler. 2017. "Synthesizing Results From Empirical Research on Computer-Based Scaffolding in STEM Education: A Meta-Analysis." *Review of Educational Research* 87(2): 309–344.

Cepeda, Nicholas J., Harold Pashler, Edward Vul, John T. Wixted, and Doug Rohrer. 2006. "Distributed Practice in Verbal Recall Tasks: A Review and Quantitative Synthesis." *Psychological Bulletin* 132(3): 354–380.

Chi, Michelene T. H., Paul J. Feltovich, and Robert Glaser. 1981. "Categorization and Representation of Physics Problems by Experts and Novices." *Cognitive Science* 5(2): 121–152.

Cooke, Molly, David M. Irby, and Bridget C. O'Brien. 2010. *Educating Physicians: A Call for Reform of Medical School and Residency.* Jossey-Bass / Carnegie Foundation.

Dochy, Filip, Mien Segers, Piet Van den Bossche, and David Gijbels. 2003. "Effects of Problem-Based Learning: A Meta-Analysis." *Learning and Instruction* 13(5): 533–568.

Graham, Steve, Michael Hebert, and Karen R. Harris. 2015. "Formative Assessment and Writing: A Meta-Analysis." *Elementary School Journal* 115(4): 523–547.

Hattie, John, and Helen Timperley. 2007. "The Power of Feedback." *Review of Educational Research* 77(1): 81–112.

Jonassen, David H. 1997. "Instructional Design Models for Well-Structured and Ill-Structured Problem-Solving Learning Outcomes." *Educational Technology Research and Development* 45(1): 65–94.

Kalyuga, Slava, Paul Ayres, Paul Chandler, and John Sweller. 2003. "The Expertise Reversal Effect." *Educational Psychologist* 38(1): 23–31.

Kerfoot, B. Price, Yulei Fu, Harley Baker, et al. 2010. "Online Spaced Education Generates Transfer and Improves Long-Term Retention of Diagnostic Skills." *Annals of Surgery* 252(2): 350–359.

Koedinger, Kenneth R., and Vincent Aleven. 2007. "Exploring the Assistance Dilemma in Experiments with Cognitive Tutors." *Educational Psychology Review* 19(3): 239–264.

Pekrun, Reinhard. 2006. "The Control-Value Theory of Achievement Emotions." *Educational Psychology Review* 18(4): 315–341.

Renkl, Alexander, and Robert K. Atkinson. 2003. "Structuring the Transition From Example Study to Problem Solving in Cognitive Skill Acquisition." *Educational Psychologist* 38(1): 15–22.

Roediger, Henry L., III, and Jeffrey D. Karpicke. 2006. "Test-Enhanced Learning." *Psychological Science* 17(3): 249–255.

Rohrer, Doug, and Kelli Taylor. 2007. "The Shuffling of Mathematics Problems Improves Learning." *Instructional Science* 35(6): 481–498.

Sheppard, Sheri D., Kelly Macatangay, Anne Colby, and William M. Sullivan. 2008. *Educating Engineers: Designing for the Future of the Field.* Jossey-Bass / Carnegie Foundation.

Singhal, Karan, et al. 2023. "Large Language Models Encode Clinical Knowledge." *Nature* 620: 172–180.

Thistlethwaite, Jill E., Diana Davies, et al. 2012. "The Effectiveness of Case-Based Learning in Health Professional Education. BEME Guide No. 23." *Medical Teacher* 34(6): e421–e444.

van de Pol, Janneke, Monique Volman, and Jos Beishuizen. 2010. "Scaffolding in Teacher–Student Interaction: A Decade of Research." *Educational Psychology Review* 22(3): 271–296.
