# Medhavy 1.5 — Feature Roadmap
**What we're building, what already exists, and why each feature earns its place**

*Internal document for engineering and product alignment*

---

## How to read this document

Medhavy is built on a specific claim: that different kinds of learning require different kinds of help, and that the right help at the right moment produces meaningfully better outcomes than any single mode of instruction. Each feature in 1.5 corresponds to a distinct cognitive operation — acquiring a representation, making it durable, applying it under ambiguity, generating something new with it. The research behind each is not decorative. It is the reason the feature exists in the form it does and not some other form.

This document covers:

- **What already exists** — the Ask AI mode, the context-aware chatbot that ships with the current Cancer Biology and Physics Vol. 1 textbooks
- **What 1.5 adds** — Quiz Me, Case Study, Glimmer, and Video and Animation
- **Why each feature is designed the way it is** — the research rationale, including the failure modes each design choice is trying to avoid
- **How the modes fit together** — the cognitive logic that makes the combination more than the sum of its parts

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

**What it does not do.** Ask AI does not make retrieved knowledge durable. It does not force the student to apply knowledge under ambiguity. It does not ask the student to generate anything novel. These are the jobs of the modes being added in 1.5.

---

## What 1.5 adds

The single Ask AI button becomes four. The interface presents: Ask AI, Quiz Me, Case Study, Glimmer. Video and Animation is not a fifth button — it is a representation-building layer that sits upstream of all four modes for a specific content class. Each mode is appropriate for a different moment in a student's relationship with a concept. Together they constitute a complete learning environment; none alone is sufficient.

---

### Video and Animation — representation building for dynamic concepts

**What it is.** For concept nodes whose content has spatial, temporal, or dynamic structure — processes that unfold over time, mechanisms with moving parts, phenomena that are defined by change — a 60 to 90-second video or animation appears at the top of the section before the reading begins. It is not a lecture. It is a schema-builder: a visual encoding of the concept that gives the student a mental model to hang the subsequent text on, and to retrieve, apply, and generate from in the modes that follow.

Video and Animation is not a replacement for any of the four modes. It is the advance organizer that makes them more productive for the content class where static text is structurally insufficient.

**The cost-effectiveness argument.** For fifty years, professional educational video production cost $75,000 to $150,000 per unit. That cost structure answered the question of who could afford to make educational video: institutions with audiences in the millions. Sesame Street amortized its investment at approximately $5 per child per year across its broadcast footprint. A medical school course with 80 students could not justify the same production cost. Personalization was not expensive — it was economically impossible.

AI production pipelines have collapsed that cost to approximately $5 per video unit while maintaining professional production quality — a reduction of 15,000 to 30,000 times by professional production assessment. This does not change whether educational video works. It changes the minimum viable audience required to justify production. At $150,000 per video, that threshold is tens of thousands of learners. At $5 per video, a single section of 30 students justifies production if the video produces any measurable learning gain at all. The question is no longer "does this justify the enormous additional cost?" It is "given that this costs essentially nothing to produce, when would we not produce it?"

The relevant claim for Medhavy is not "video is the best instructional medium." It is narrower: for a specific class of concepts, video can build the initial representation that makes Ask AI, Quiz Me, Case Study, and Glimmer more productive — and the production cost is now within reach of a platform serving a single course.

**The research case.** Richard Mayer's cognitive theory of multimedia learning — over 200 experiments across four decades — establishes the mechanism. Learning is better when relevant words and pictures are presented simultaneously rather than successively (the multimedia principle), when spoken words accompany visuals rather than printed words (the modality principle), and when extraneous material is excluded (the coherence principle). The modality effect produces effect sizes in the range of approximately 1.13 standard deviations in controlled conditions. The mechanism is dual-channel processing: visual and auditory information enter through separate cognitive pathways, distributing cognitive load and leaving more working memory available for integration and knowledge construction.

Mares and Pan's meta-analysis of 24 studies across 15 countries involving more than 10,000 children found an overall effect size of 0.29 standard deviations for educational television on learning outcomes, rising to 0.41 for children in low-socioeconomic environments. These are effects for broadcast, standardized content — not optimized for the individual learner's prior knowledge state. The theoretical ceiling for well-designed, context-specific educational video is substantially higher.

Tversky, Morrison, and Bétrancourt (2002) provide the critical domain qualification: animation outperforms static graphics specifically for content involving continuous change over time. This is not a general endorsement of video. It is a specific prediction about when video earns its place. The benefit concentrates in domains where the concept is a process — where the learning target is understanding a sequence of events, a causal mechanism, or a spatial relationship that changes over time.

Physics is the paradigm case, which is why the Physics Vol. 1 textbook already serves students with interactive D3 simulations. Projectile motion, wave interference, centripetal acceleration, simple harmonic motion — these are motion phenomena. A student who reads that "the x and y components of projectile motion are independent" has a verbal encoding. A student who watches the parabolic path decompose into independent horizontal and vertical components has a spatial encoding the verbal one cannot replace. Video is not generally superior to text for physics. It is structurally necessary for the subset of physics content where the concept is defined by motion.

The Cancer Biology content has a parallel case. The cell cycle, the complement cascade, signal transduction pathways, apoptosis — these are dynamic processes. A static diagram shows the stages. A 90-second animation showing the sequence, the checkpoints, the molecular events at each transition, builds a mental model that the diagram leaves implicit. The student who has the mental model can engage with Quiz Me items about mechanism, Case Study scenarios about cell cycle dysregulation, and Glimmer prompts about therapeutic intervention points in a qualitatively different way than the student who has only the diagram.

**Where video sits in the learning flow.** The four modes all operate on representations the student already holds. Ask AI elaborates a representation. Quiz Me makes it durable. Case Study applies it under ambiguity. Glimmer generates something new from it. For concepts with dynamic structure, a student who arrives at the section without an adequate initial representation will find Ask AI less productive, Quiz Me harder than it should be, and Case Study confusing in ways that look like reasoning failures but are actually encoding gaps.

A video at the top of the section gives the student the schema that makes the subsequent text, Ask AI interactions, and Quiz Me sessions coherent. It is the Ausubel advance organizer in motion: a representation-building tool that makes new information assimilable rather than arbitrary.

This positioning has a testable prediction: Quiz Me accuracy in sessions following a video-introduced concept should be higher than for equivalent concepts introduced by text alone, controlling for concept difficulty. Medhavy's signal layer makes this test straightforward to run within the platform. No external RCT is required — the comparison is within-student, across concept nodes matched on importance tier and prerequisite depth, using the `learning_signals` table the platform is already building.

**The production model.** The Brutalist pipeline governs production. Three governing files define everything before generation begins: a coding constitution for the active renderer (CLAUDE.md), a visual constitution specifying color, typography, and motion vocabulary (DESIGN.md), and a project state document with a human-populated intent layer and an AI-populated technical layer (PROJECT.md). The human specifies what the concept is, what the student should understand, and what the design register should be. The AI generates within the schema. The human verifies before any output is accepted.

This is not autonomous AI video production. Labor separation is structural: creative judgment about what a student needs to understand from a 90-second animation of the complement cascade is a human decision. Executing that judgment at production quality for $5 in API credits is an AI execution task.

The design constraints that Mayer's coherence principle demands are enforced at the DESIGN.md layer before generation begins: no background elements without pedagogical function, no decorative motion, no transitions that do not mark conceptual boundaries, every visual element labeled that the voiceover references, processes shown in comprehensible time rather than accelerated for production aesthetics. These are not aesthetic preferences. They are design rules that follow from the evidence base, and they are the difference between video that builds a mental model and video that consumes cognitive resources without depositing learning. The coherence principle is both the strongest endorsement of educational video in the literature and its most serious risk: poorly designed video that violates coherence can produce worse outcomes than well-designed text with diagrams. The cost collapse does not eliminate this risk. It creates the temptation to produce carelessly. The production pipeline's governing documents are the technical answer to that temptation.

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

**Why cases must be pre-written and professor-approved.** The prohibition on AI-generated cases is not temporary conservatism. It reflects a specific risk documented in the medical LLM literature. Singhal et al.'s evaluation of Med-PaLM (2023, *Nature*) found that even a model achieving 86% accuracy on USMLE-style questions — the best available at time of publication — produced wrong answers in roughly one in seven cases, delivered with the same fluent confidence as correct ones. A case scenario containing a plausible-sounding but incorrect clinical claim — a wrong first-line treatment, an outdated staging criterion, a fabricated drug interaction — does not fail loudly. It fails silently, propagating as a student misconception that may persist through clinical training. Pre-written, faculty-reviewed cases have bounded failure modes. AI-generated cases have unbounded failure modes, and the cost of a wrong answer in clinical content is asymmetric.

**What the session logs capture.** Case Study sessions are logged at a granularity that serves the 2.0 bandit's training data: which assistance level the student reached, how many AI turns preceded each escalation, whether the student disengaged before three minutes, and the AI-assessed reasoning quality of the student's final response (poor / developing / proficient). These signals distinguish "the student found this case too hard" from "the student found this case unengaging" from "the student worked through this productively" — three outcomes that warrant different next-mode selections from the bandit.

---

### Glimmer — generative creative assignment

**What it is.** Glimmer is a creative, non-trivial assignment anchored to a specific concept node. There is no correct answer. The student produces something that did not exist before: a proposed clinical protocol, a mechanism explanation applied to a novel context, a critique of an existing approach, a design for an intervention. The assignment is graded on five dimensions: WHY (is the problem framing specific and contextual, not generic?), Usefulness (is there a real application pathway?), Mechanism (are the causal steps specified, not just the outcome?), Defensibility (can the student argue for this against alternatives?), and Specificity (are measurements, quantities, and concrete details present?).

Before the instructor grades the submission, the AI pre-grading reviewer reads it, identifies the weakest dimension, and asks the student one targeted interrogation question about it. Not "be more specific" — a precise question about the specific gap: "You claim that X will produce Y, but you don't explain the mechanism by which this occurs. Walk me through the specific causal steps between X and Y." The student responds. If the response meets threshold on defensibility and specificity, the submission is released to the instructor. If not, the AI asks one follow-up question — a maximum of two rounds of AI interrogation before instructor review regardless.

Eight to twelve Glimmers across a course compose into a term project the student does not know they are building until weeks ten and eleven, when the system reveals that all prior submissions are now a portfolio and a synthesis assignment unlocks.

**The research case.** The Glimmer is an ill-structured problem in the Jonassen (1997, 2000) sense: it has no single correct solution, no agreed evaluation criteria, and requires the student to specify the problem before solving it. The evidence base for ill-structured problem-solving instruction — particularly Belland, Walker, Kim and Lefler's 2017 meta-analysis of computer-based scaffolding for STEM cognitive outcomes (g = 0.46, 144 studies) — establishes that scaffolded ill-structured work produces meaningful cognitive gains when the scaffolding is contextualized, fades appropriately as competence grows, and addresses conceptual rather than purely procedural support. The Glimmer's rubric is the scaffolding. The AI pre-grading reviewer is the contextualized, targeted feedback mechanism that the scaffolding-fading literature identifies as the high-effect intervention: not "here is what is wrong" but "here is one specific question about the weakest part of your reasoning — answer it."

The AI reviewer's design follows the Graham, Hebert, and Harris (2015) meta-analysis of formative assessment in writing, which found that questioning-style feedback — asking the writer questions about their work rather than telling them what is wrong — produced effect sizes of approximately d = 0.40 to 0.50 on revision quality. Hattie and Timperley's (2007) landmark review of feedback establishes that process-level and self-regulation-level feedback produce the largest effects, while task-level feedback (here is the right answer) produces small effects and self-level feedback (you are doing well / poorly) produces near-zero or negative effects. The AI reviewer operates entirely at the process and self-regulation levels: "walk me through your causal reasoning" is a self-regulation prompt; "what observation would change your recommendation" is a process prompt. The AI never produces task-level feedback.

The emergent term project design is grounded in writing-process pedagogy (Murray, 1972; Elbow, 1973; Flower and Hayes, 1981): the final form of a substantial piece of work emerges from accumulation, and writers discover what they think by producing what they do not yet think. The pedagogical argument is that a student who knows they are building a term project optimizes for the grade on the project. A student who experiences each Glimmer as an interesting low-stakes weekly exercise optimizes for the exercise. The connective tissue — the synthesis that emerges in weeks ten and eleven — is more authentic when it is genuinely discovered rather than planned.

The five-dimension rubric maps onto the AAC&U VALUE rubrics for Critical Thinking and Inquiry and Analysis — dimensions that cannot be satisfied by quotation or length, only by demonstration of reasoning quality. A student cannot score well on Mechanism by writing more, only by specifying more precisely. Defensibility cannot be faked by hedging — hedging is the opposite of a defensible claim. Specificity catches the expert-novice gap that Chi, Feltovich, and Glaser (1981) documented: novices categorize problems by surface features; experts by deep principles. A specific Glimmer response is one that has reorganized surface features into principled application.

**The anxiety failure mode and how it is mitigated.** Pekrun's (2006) control-value theory of achievement emotions predicts a specific failure mode for open-ended creative assignments: students who cannot see the destination (low perceived control) and care about their grade (high value) land in the anxiety quadrant, not the engagement quadrant. The USMLE-trained medical student population that Medhavy primarily serves has spent two or more years optimizing for closed-problem recognition tasks. Their first encounter with a Glimmer will frequently be experienced as evidence they cannot do the work.

Three mitigations are built into the design. First, early-semester Glimmers are heavily anchored to specific observations or cases from the textbook — the student is not operating in fully open space until week five or later. Second, the AI pre-grading reviewer's first response always acknowledges something the student did well before asking the interrogation question. Control is restored incrementally, not all at once. Third, the Glimmer surfaces in the interface as "Glimmer available" rather than "Glimmer overdue" — the framing is opportunity, not obligation.

The scaffolding-fading literature (Puntambekar and Hübscher, 2005; van de Pol, Volman, and Beishuizen, 2010) establishes that the early weeks of an ill-structured assignment should function as backwards-faded worked examples: week one presents a Glimmer with the framing pre-supplied, asking only that the student fill in mechanism and specificity; week two supplies the framing partially; week three is the first fully open Glimmer. This mirrors Renkl and Atkinson's (2003) backwards-faded worked-example sequence for cognitive skill acquisition.

---

## How the modes fit together

The modes are not interchangeable alternatives. They correspond to distinct cognitive operations that learning research has established as necessary, sequential, and mutually insufficient.

**Video and Animation** builds the initial representation for concepts whose structure cannot be fully conveyed by text alone. It is the entry point for the content class where the concept is a process — where understanding requires seeing the thing move, not reading a description of the movement. Without this foundation, the four modes that follow are operating on an incomplete schema.

**Ask AI** elaborates and extends the representation. A student who has watched a 90-second animation of the complement cascade and then asks "what happens if C3 is deficient?" is having a qualitatively more productive conversation than a student asking the same question with only a static diagram as their mental model. Ask AI is the entry point for concepts without dynamic structure, and the elaboration layer for those with it.

**Quiz Me** makes the representation durable. A student who has a representation — built through video, reading, and Ask AI — has a fragile encoding. Retrieval practice, spaced over time, converts fragile encodings into robust ones. This is the mechanism that produces knowledge that survives an exam without a textbook, a clinical rotation without a reference, a board certification without time to review.

**Case Study** applies the representation under ambiguity. A student who can retrieve a concept reliably has not necessarily learned to deploy it in a real situation. Clinical cases present the concept in a context where the right application is not obvious, where competing interpretations are legitimate, and where the reasoning process is the learning outcome rather than the correct answer.

**Glimmer** generates something new from the representation. A student who can retrieve a concept and apply it to cases presented to them has not necessarily developed the capacity to use the concept as a tool for original thinking. Generative work — proposing, designing, specifying, defending — forces the student to reorganize knowledge around principles rather than surface features. This is the operation that produces the expertise-level knowledge structure Chi and colleagues documented in expert physicists and clinicians: not more facts, but facts organized around deep principles that transfer to novel situations.

The Carnegie Foundation's studies of medical education (Cooke, Irby, and O'Brien, 2010) and engineering education (Sheppard, Macatangay, Colby, and Sullivan, 2008) reached the same diagnosis independently: professional education trains students for well-structured-problem performance while professional practice requires ill-structured-problem judgment. The Medhavy mode architecture is the answer to that gap — not by replacing the curriculum, but by ensuring that the full cognitive sequence is available alongside it.

---

## Appendix — Medhavy 2.0: the contextual bandit

The modes described above generate signal data. In 1.5, the platform presents all modes and lets the student choose. In 2.0, a contextual bandit learns which mode to surface at the natural re-entry point after each session — not by forcing the student's choice, but by making the right offer at the right moment.

The bandit is a class of reinforcement learning algorithm (Thompson Sampling is the proposed implementation) that, given a feature vector describing the student's current state on a concept node, selects the mode most likely to produce durable learning at this moment for this student. The feature vector includes FSRS retrievability, prerequisite mastery scores, concept importance tier, recency of Case Study and Glimmer engagement, Glimmer rubric history, and — for concept nodes with dynamic structure — whether a video has been watched and how recently.

The bandit cannot exist without 1.5's signal layer. Every case study escalation level, every Glimmer interrogation cycle, every Quiz Me card rating, every video watch completion — these are the training data for the bandit's mode-selection policy. Without clean, complete, consistently-structured signals from 1.5, 2.0 learns from noise.

The reward signal — what the bandit is optimizing for — is delayed retrieval accuracy: seven days after the bandit selects a mode for concept C, a new Quiz Me item on concept C is offered. The student's accuracy on that item is the reward. This directly measures what the platform is for.

The 2.0 architecture, reward design decisions, and kickoff requirements are documented separately in the Medhavy 2.0 Strategic Roadmap.

---

## Key research citations

Adesope, Olusola O., Dominic A. Trevisan, and Narayankripa Sundararajan. 2017. "Rethinking the Use of Tests: A Meta-Analysis of Practice Testing." *Review of Educational Research* 87(3): 659–701.

Anderson, Daniel R., Aletha C. Huston, Kelly L. Schmitt, Deborah L. Linebarger, and John C. Wright. 2001. "Early Childhood Television Viewing and Adolescent Behavior: The Recontact Study." *Monographs of the Society for Research in Child Development* 66(1): i–147.

Ausubel, David P. 1960. "The Use of Advance Organizers in the Learning and Retention of Meaningful Verbal Material." *Journal of Educational Psychology* 51(5): 267–272.

Bastani, Hamsa, Osbert Bastani, et al. 2025. "Generative AI Can Harm Learning." *PNAS* 122(26): e2422633122.

Belland, Brian R., Andrew E. Walker, Nam Ju Kim, and Mason Lefler. 2017. "Synthesizing Results From Empirical Research on Computer-Based Scaffolding in STEM Education: A Meta-Analysis." *Review of Educational Research* 87(2): 309–344.

Cepeda, Nicholas J., Harold Pashler, Edward Vul, John T. Wixted, and Doug Rohrer. 2006. "Distributed Practice in Verbal Recall Tasks: A Review and Quantitative Synthesis." *Psychological Bulletin* 132(3): 354–380.

Cepeda, Nicholas J., Edward Vul, Doug Rohrer, John T. Wixted, and Harold Pashler. 2008. "Spacing Effects in Learning: A Temporal Ridgeline of Optimal Retention." *Psychological Science* 19(11): 1095–1102.

Chi, Michelene T. H., Paul J. Feltovich, and Robert Glaser. 1981. "Categorization and Representation of Physics Problems by Experts and Novices." *Cognitive Science* 5(2): 121–152.

Cooke, Molly, David M. Irby, and Bridget C. O'Brien. 2010. *Educating Physicians: A Call for Reform of Medical School and Residency.* Jossey-Bass / Carnegie Foundation.

Dochy, Filip, Mien Segers, Piet Van den Bossche, and David Gijbels. 2003. "Effects of Problem-Based Learning: A Meta-Analysis." *Learning and Instruction* 13(5): 533–568.

Graham, Steve, Michael Hebert, and Karen R. Harris. 2015. "Formative Assessment and Writing: A Meta-Analysis." *Elementary School Journal* 115(4): 523–547.

Hattie, John, and Helen Timperley. 2007. "The Power of Feedback." *Review of Educational Research* 77(1): 81–112.

Jonassen, David H. 1997. "Instructional Design Models for Well-Structured and Ill-Structured Problem-Solving Learning Outcomes." *Educational Technology Research and Development* 45(1): 65–94.

Kalyuga, Slava, Paul Ayres, Paul Chandler, and John Sweller. 2003. "The Expertise Reversal Effect." *Educational Psychologist* 38(1): 23–31.

Kerfoot, B. Price, Yulei Fu, Harley Baker, et al. 2010. "Online Spaced Education Generates Transfer and Improves Long-Term Retention of Diagnostic Skills." *Annals of Surgery* 252(2): 350–359.

Koedinger, Kenneth R., and Vincent Aleven. 2007. "Exploring the Assistance Dilemma in Experiments with Cognitive Tutors." *Educational Psychology Review* 19(3): 239–264.

Mares, Marie-Louise, and Zhongdang Pan. 2013. "Effects of Sesame Street: A Meta-Analysis of Children's Learning in 15 Countries." *Journal of Applied Developmental Psychology* 34(3): 140–151.

Mayer, Richard E. 2009. *Multimedia Learning.* 2nd ed. Cambridge: Cambridge University Press.

Pekrun, Reinhard. 2006. "The Control-Value Theory of Achievement Emotions." *Educational Psychology Review* 18(4): 315–341.

Puntambekar, Sadhana, and Roland Hübscher. 2005. "Tools for Scaffolding Students in a Complex Learning Environment." *Educational Psychologist* 40(1): 1–12.

Renkl, Alexander, and Robert K. Atkinson. 2003. "Structuring the Transition From Example Study to Problem Solving in Cognitive Skill Acquisition." *Educational Psychologist* 38(1): 15–22.

Roediger, Henry L., III, and Jeffrey D. Karpicke. 2006. "Test-Enhanced Learning." *Psychological Science* 17(3): 249–255.

Rohrer, Doug, and Kelli Taylor. 2007. "The Shuffling of Mathematics Problems Improves Learning." *Instructional Science* 35(6): 481–498.

Sheppard, Sheri D., Kelly Macatangay, Anne Colby, and William M. Sullivan. 2008. *Educating Engineers: Designing for the Future of the Field.* Jossey-Bass / Carnegie Foundation.

Singhal, Karan, et al. 2023. "Large Language Models Encode Clinical Knowledge." *Nature* 620: 172–180.

Sweller, John. 1988. "Cognitive Load During Problem Solving: Effects on Learning." *Cognitive Science* 12(2): 257–285.

Thistlethwaite, Jill E., Diana Davies, et al. 2012. "The Effectiveness of Case-Based Learning in Health Professional Education. BEME Guide No. 23." *Medical Teacher* 34(6): e421–e444.

Tversky, Barbara, Julie Bauer Morrison, and Mireille Bétrancourt. 2002. "Animation: Can It Facilitate?" *International Journal of Human-Computer Studies* 57(4): 247–262.

van de Pol, Janneke, Monique Volman, and Jos Beishuizen. 2010. "Scaffolding in Teacher–Student Interaction: A Decade of Research." *Educational Psychology Review* 22(3): 271–296.
