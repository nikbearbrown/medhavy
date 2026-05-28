# Medhavy: Is the Loop Worth It?
## A Decision Guide for Institutional Decision-Makers

**Working title:** Medhavy: Is the Loop Worth It?
**Subtitle candidate:** When AI+1 on Kindle Is Enough — and When It Isn't
**Author:** Nik Bear Brown · ni.brown@neu.edu · Humanitarians AI
**Series:** Standalone (Book One of a two-book set; Book Two = user guide for deployers)
**Document:** Full TIKTOC.md — compiled from all phase outputs
**Version:** 1.0
**Status:** Pre-draft — chapter specs ready for Cowork

---

## Document structure

1. Book Concept and Thesis
2. Learner Profile
3. Book Type and Deployment Specification
4. Field Positioning
5. Three-Act Learning Arc
6. Prerequisite Map
7. Learning Outcomes by Chapter
9. Chapter-by-Chapter TOC
9. Chapter Anatomy Template
10. Hard Topics, Contested Claims, Aging Risk
11. Open Questions

---

# PART 1 — BOOK CONCEPT AND THESIS

## Book concept summary

> This book teaches **institutional decision-makers** — deans, department
> chairs, curriculum directors, instructional design leads — what Medhavy
> actually is and whether their deployment warrants adding it, by
> translating four proprietary modes (Ask AI, Quiz Me, Case Study, Glimmer)
> and three conceptual foundations (Irreducibly Human, AI+1, Frictional
> Framework) out of jargon and into plain-language decisions. It fills the
> gap left by vendor marketing (which names features without explaining
> them), general AI-in-education literature (which covers the landscape
> without addressing Medhavy specifically), and the existing Medhavy
> manuscript (which is written for builders, not buyers). It succeeds if
> the reader finishes able to make a confident, evidence-based choice:
> Canvas + Kindle / AI+1 as-is, or Canvas + Kindle / AI+1 + Medhavy.

**One-sentence logline:**
AI+1 is a better textbook — but a better textbook is not always enough,
and this book tells you exactly when it isn't.

**The thesis in one paragraph:**
Medhavy is not a better textbook. It is a measurement and adaptation
layer — a loop that presents content differently to different learners,
measures whether the difference helped, and adapts based on what it
learns. AI+1 on Kindle, with Brutalist slides and Canvas, is a complete,
high-quality learning stack for most deployments. Medhavy earns its cost
when three things are simultaneously true: the deployment needs to present
content differently to different learners at scale, someone needs to know
whether the variation is working (not just whether students are engaged),
and the institution is willing to act on what the measurement reveals.
If those three conditions are not all present, Medhavy is overhead.
If they are, it is the only tool that closes the loop.

## The loop — the book's central concept

Canvas cannot close this loop. Kindle cannot close it. A good AI+1
textbook cannot close it. The loop is:

**Present differently → Measure whether it helped → Adapt → Repeat**

"Present differently" means interventions: not just different explanations
of the same concept, but different pedagogical approaches — Socratic
versus didactic, problem-first versus concept-first, retrieval practice
versus generative assignment. These are not cosmetic variations. They
are different cognitive operations with different evidence bases and
different appropriate deployment conditions.

"Measure whether it helped" is not engagement analytics. Canvas gives
you time-on-page, clicks, and completion rates. Medhavy measures the
Frictional Framework's seven signals — behavioral traces that genuine
learning leaves behind that performance does not. The difference between
a student who learned something and a student who felt like they learned
something is invisible to Canvas. It is visible to Medhavy.

"Adapt" is the contextual bandit — the algorithm that learns, per student
per concept, which interventions produce genuine learning and surfaces
those interventions more frequently. This is not a recommendation engine.
It is an experiment that runs continuously, per learner, per concept,
with learning outcomes as the reward signal.

---

# PART 2 — LEARNER PROFILE

## Primary reader (one specific person)

A curriculum director at a mid-size university health sciences program.
She has a budget line for educational technology, a Canvas instance, and
a growing stack of AI+1 textbooks her faculty have adopted. A vendor has
proposed adding Medhavy. She has read the feature sheet. She does not
understand what Ask AI is, does not know what Quiz Me does that Anki
doesn't, has never heard of Glimmer or the Frictional Framework, and
cannot tell whether Medhavy is a chatbot bolted to a PDF or something
architecturally different. She needs to make a budget decision in six
weeks.

## Prior knowledge assumed

- Active institutional responsibility for curriculum or technology decisions
- Basic familiarity with Canvas or equivalent LMS
- Awareness that AI tutoring tools exist (even if skeptical)
- Has heard "spaced repetition" or "adaptive learning" without understanding
  the mechanisms
- Can read a vendor proposal but has no framework for evaluating it

## Prior knowledge NOT assumed

- Knowledge of what Ask AI, Quiz Me, Case Study, or Glimmer are
- Understanding of the Frictional Framework, GLP, or the seven signals
- Familiarity with Irreducibly Human, AI+1, or Brutalist as frameworks
- Research literacy (the book translates evidence, not presents it)
- Technical understanding of LTI, bandits, or RAG

## Prior misconceptions

1. "Medhavy is a chatbot bolted to a textbook" — architecturally wrong;
   the four modes are not a chatbot; Ask AI is the closest and it is
   deliberately constrained in ways a chatbot is not
2. "Intelligent textbook = adaptive quiz generator" — Quiz Me is one of
   four modes; the other three do things quizzes cannot
3. "If students are engaged, they are learning" — the Frictional Framework
   exists precisely because this is false; the book must correct this
   without alienating the reader
4. "AI+1 already does what Medhavy does" — AI+1 is a better textbook;
   Medhavy is a measurement and adaptation layer; these are different products
5. "More modes = more better" — the book must explain when simpler is
   correct; Anki is sometimes the right answer

## Motivation type

Professional and institutional. The reader is making a real budget
decision with real consequences. The book must feel like a trusted
colleague who has done the research, not like a vendor pitch or an
academic paper.

---

# PART 3 — BOOK TYPE AND DEPLOYMENT SPECIFICATION

**Primary type:** Decision-support book, organized as a practitioner
handbook. Each chapter is self-contained and answers one decision
question the reader is actually asking. Reader can enter at the chapter
that matches their current question.

**NOT:** A user guide (that is Book Two), a course textbook, or a
technical manual.

**Primary adoption context:**
Self-directed reading by an institutional decision-maker who has been
handed a Medhavy proposal and needs a framework to evaluate it.
Secondary: professional development for instructional design teams
considering AI+1 + Medhavy deployments.

**$1 Kindle format:** Yes — consistent with the AI+1 series pricing.

**What the book is NOT designed for:**
Students using Medhavy, developers building on Medhavy, researchers
studying educational technology, general readers interested in AI and
education.

---

# PART 4 — FIELD POSITIONING

## The gap this book fills

No existing resource tells an institutional decision-maker what Medhavy's
four modes actually are in plain language, how they differ from what
Canvas already does, when each one is warranted, and how to make the
adoption decision honestly — including the honest case for not adopting.

## Positioning statements

vs. the existing Medhavy manuscript (the builder's book):
"Unlike the Medhavy manuscript, which is written for people building an
intelligent textbook from scratch, this book is written for people
deciding whether to add Medhavy to a deployment they already have —
starting from 'I have Canvas and AI+1 Kindles' and ending at 'here is
my decision and why.'"

vs. general AI-in-education landscape reports:
"Unlike landscape surveys of intelligent textbook platforms, this book
does not compare Medhavy to ALEKS or Khanmigo — it explains what Medhavy
specifically does, in the vocabulary Medhavy uses, translated into
decision-maker language."

vs. vendor marketing:
"Unlike Medhavy's own feature documentation, this book names when
Medhavy is not the right answer — including the specific conditions
under which AI+1 on Kindle without Medhavy is the better choice."

---

# PART 5 — THREE-ACT LEARNING ARC

## Arc statement

This book takes the reader from **"I have a vendor proposal I cannot
evaluate"** to **"I have made a confident, evidence-based adoption
decision"** — by first establishing what the four modes actually are
and what problem each one solves (Act One), then explaining what
Medhavy measures that Canvas cannot and why that measurement matters
(Act Two), then giving the reader the decision framework and the
honest conditions under which Medhavy does and does not earn its cost
(Act Three).

## Act One — What Are These Four Things? (Chapters 1–6)

Starting state: Reader has heard Ask AI, Quiz Me, Case Study, Glimmer.
Does not know what any of them are. Cannot tell them apart from a
general-purpose chatbot.

Ending state: Reader understands what cognitive operation each mode
serves, what the evidence base for each one is, when each one is
appropriate, and — critically — when each one is NOT appropriate.

Inciting question: What is a "mode" and why are there four of them
instead of one?

**The pebble:** Chapter 1 opens with the most common failure mode in
AI-in-education deployments — students who look engaged, score well
in-session, and learn nothing durable. The Bastani 2025 finding in
plain language: same AI, different wrapper, opposite outcomes. The
reader who finishes Chapter 1 understands why "the AI is doing the
work" is the failure, and why Medhavy's four modes are each designed
to prevent a specific form of that failure.

## Act Two — What Does Medhavy Measure That Canvas Doesn't? (Chapters 7–9)

Starting state: Reader understands the four modes. Still does not
understand why measurement is the value proposition.

Ending state: Reader understands the difference between engagement
analytics (what Canvas provides) and learning evidence (what Medhavy's
Frictional Framework provides). Understands the seven friction signals
in plain language. Understands why the loop — present differently,
measure whether it helped, adapt — cannot be closed by Canvas alone.

Hardest moment: Chapter 7. The reader has spent a professional career
treating engagement as a proxy for learning. The book must correct
this without insulting them. The Bastani finding carries most of this
weight if presented correctly.

## Act Three — Is the Loop Worth It for My Deployment? (Chapters 10–12)

Starting state: Reader understands the modes and the measurement.
Now needs the decision framework.

Ending state: Reader can answer the three adoption questions:
(1) Does my deployment need to present content differently at scale?
(2) Do I need to know whether the variation is helping?
(3) Am I willing to act on what the measurement reveals?
If all three yes: Medhavy earns its cost. If any no: simpler stack.

Transfer test: The reader who finishes Chapter 12 can sit in a
budget meeting and explain — in plain language, without jargon —
what Medhavy does that Canvas doesn't, when it's worth adding,
and when it isn't.

---

# PART 6 — PREREQUISITE MAP

| Prerequisite | Safe to Assume? | Where Addressed |
|---|---|---|
| LMS familiarity (Canvas or equivalent) | Yes | Referenced throughout, not explained |
| Basic AI tool awareness | Probably | Chapter 1 establishes baseline |
| Understanding of spaced repetition | No | Chapter 3 (Quiz Me) explains from scratch |
| Knowledge of Bloom's taxonomy | No | Referenced in passing, not required |
| Research literacy | No | Evidence always translated, never cited raw |
| Understanding of AI+1 framework | No | Chapter 2 explains what AI+1 is |
| Understanding of Irreducibly Human | No | Introduced in Chapter 2, used throughout |
| Knowledge of Frictional Framework / GLP | No | Chapter 7 introduces from scratch |
| LTI or technical integration knowledge | No | Chapter 11 addresses without technical depth |

**Front-loading decision:** No prerequisites chapter. Every concept
introduced at first use in plain language. The reader does not need
to understand the research — they need to understand the decision.

---

# PART 7 — LEARNING OUTCOMES BY CHAPTER

| Chapter | Title | Bloom's Ceiling | Key outcome |
|---------|-------|-----------------|-------------|
| 1 | The Failure That Looks Like Success | Analyze | Identify the engagement-learning gap in a real example |
| 2 | AI+1 Is a Better Textbook. Is That Enough? | Evaluate | Assess whether AI+1 alone meets a specific deployment need |
| 3 | Ask AI: When the Student Needs to Think, Not Receive | Apply | Match Ask AI to appropriate deployment contexts |
| 4 | Quiz Me: Making Knowledge Stick | Apply | Distinguish spaced retrieval from quiz-taking; identify when Quiz Me adds value |
| 5 | Case Study and Glimmer: The Two Modes Nobody Explains | Understand | Explain what Case Study and Glimmer do that the other two modes cannot |
| 6 | What Canvas Measures and What It Misses | Analyze | Distinguish engagement analytics from learning evidence |
| 7 | The Seven Signals: What Genuine Learning Looks Like | Understand | Name the seven friction signals in plain language and connect each to a mode |
| 8 | The Loop: Present, Measure, Adapt | Analyze | Explain how the contextual bandit closes the loop Canvas cannot |
| 9 | When Kindle Is Enough | Evaluate | Apply the three-question complexity threshold to a real deployment |
| 10 | Adding Medhavy to Canvas: What Actually Changes | Apply | Specify what LTI integration adds and what it requires from the institution |
| 11 | The Adoption Decision | Create | Produce a justified adoption recommendation for a specific deployment context |

---

# PART 8 — CHAPTER-BY-CHAPTER TOC

---

## ACT ONE — WHAT ARE THESE FOUR THINGS? (Chapters 1–6)

---

### CHAPTER 1 — The Failure That Looks Like Success

**One-line:** The reader learns why AI in education can look like it's
working while actively harming learning — and why that failure is
architectural, not incidental.

**Opening:**
A university deploys an AI tutoring tool. Engagement metrics climb.
Students report satisfaction. Session completion rates hit 94%. The
end-of-term exam arrives. The students who used the AI most score
lower than students who used it least. The vendor's dashboard showed
success. The exam showed something else.

This is not a hypothetical. This is the Bastani 2025 PNAS finding,
translated into plain language. Same AI, two deployments, one wrapper
that refused to give answers, one that didn't. The no-guardrail group
scored 17 percentage points below the no-AI control on the unassisted
exam. The engagement metrics were indistinguishable between groups.

**Core content blocks:**
1. The engagement-learning gap — what it is, why it exists, why
   dashboards cannot see it; the Bastani finding in three sentences
2. The fluency trap — why AI-generated explanations feel like
   understanding without producing it; why this is the primary risk
   of adding AI to a learning stack without architecture
3. Why the wrapper is the variable — same AI, different outcomes,
   the only difference is what the platform commits the AI to doing;
   this is the book's foundational claim
4. What this means for the reader's decision — not "is AI bad" but
   "what commitments does any AI layer need to make, and does Medhavy
   make them"

**Worked example:**
The Bastani study as a case: two versions of the same deployment,
same students, same content, same AI model. Walk the reader through
what each group experienced, what each group's dashboard showed, and
what each group's exam revealed. The gap between the dashboard and
the exam is the problem this book solves.

**Exercises (3):**
1. (Analyze) Look at a set of Canvas analytics for a course you know.
   Identify three metrics that measure engagement. For each, name what
   genuine learning signal it would miss.
2. (Analyze) Describe a time when student engagement was high but
   learning was low. What would the dashboard have shown? What would
   a learning-evidence measurement have shown?
3. (Evaluate) Given the Bastani finding, what one commitment would
   you require any AI tool to make before adding it to your Canvas
   deployment?

**Bridge:** The failure is architectural. The fix is architectural.
The four modes are each a different architectural commitment.
Chapter 2 starts with the simplest question: do you even need them?

**Contributor notes:** The Bastani finding must be stated accurately
and accessibly. The reader will be skeptical — they have seen engagement
metrics that looked like learning. The chapter's job is not to convince
them AI is bad. It is to install a single distinction: engagement
evidence vs. learning evidence. Everything downstream depends on that.

---

### CHAPTER 2 — AI+1 Is a Better Textbook. Is That Enough?

**One-line:** The reader learns what AI+1 is, what it adds to a Kindle
or Canvas deployment, and the specific condition under which that is
not sufficient.

**Opening:**
Most educational technology fails because it tries to be three things
at once: a better textbook, a measurement system, and an adaptive
engine. AI+1 is explicitly the first thing only. It is a domain-specific,
practitioner-facing textbook written at the intersection of AI fluency
and human expertise. It is not a platform. It is not a measurement
system. It is not adaptive.

For a significant fraction of deployments, that is exactly enough.
This chapter explains when.

**Core content blocks:**
1. What AI+1 is — the framework in plain language: domain expert plus
   AI fluency; the Irreducibly Human taxonomy; what makes AI+1 different
   from a textbook that mentions AI
2. The standard AI+1 deployment stack — Kindle + Brutalist slides +
   Canvas; what each component does; why this is a complete learning
   environment for most purposes
3. The three questions that determine sufficiency — does the deployment
   need to present content differently to different learners at scale?
   Does someone need to know whether variation is helping? Is the
   institution willing to act on measurement? If any answer is no,
   stop here.
4. What Medhavy adds to this stack — the loop in plain language;
   not a replacement for AI+1 but a layer on top of it; the distinction
   between a better textbook and a measurement-and-adaptation layer

**Worked example:**
Two deployments side by side. Deployment A: 30 nursing students,
one instructor, AI+1 pharmacology textbook on Kindle, Canvas for
assignments. The instructor knows her students. She adapts in real
time. She does not need Medhavy. Deployment B: 300 students across
five sections, three instructors, no shared visibility into which
students are struggling with which concepts. The instructors cannot
adapt at scale. This deployment has the three conditions. This one
warrants the loop.

**Exercises (3):**
1. (Evaluate) Describe your current or most relevant deployment.
   Apply the three questions. Record your honest answers.
2. (Apply) For a deployment where all three questions are yes,
   name the specific information the loop would produce that Canvas
   currently cannot provide.
3. (Evaluate) For a deployment where one or more answers are no,
   explain why the simpler stack is not a compromise — why it is
   the correct answer for that context.

**Bridge:** The loop has four components. The next three chapters
explain the four modes — what each one does, when it works, and
when it doesn't. Start with Ask AI.

---

### CHAPTER 3 — Ask AI: When the Student Needs to Think, Not Receive

**One-line:** The reader learns what Ask AI is, why it is deliberately
constrained, and when that constraint is the point.

**Opening:**
The most natural assumption about an AI tool in a textbook is that
it answers questions. Ask AI does not answer questions. This is not
a limitation. It is the design.

A student who gets the answer from an AI has offloaded the cognitive
work that produces learning. The answer is now the AI's, not the
student's. Ask AI is designed to prevent this by giving hints, asking
clarifying questions, and redirecting students back to material they
are supposed to be building a relationship with — not bypassing.

**Core content blocks:**
1. What Ask AI actually does — RAG-grounded context awareness;
   the hints-not-answers guardrail; Socratic mode in plain language;
   why "it won't just tell me the answer" is the feature, not the bug
2. The Bastani finding applied to Ask AI — the unguarded chatbot
   is the failure mode this design prevents; the guardrail is what
   converts harm into learning
3. When Ask AI is the right mode — acquiring a representation;
   the student who has no schema for a concept yet; the entry point
   of the four-mode sequence
4. When Ask AI is NOT the right mode — for factual recall on
   well-understood concepts, it is patronizing; for application
   under ambiguity, it cannot replace a case; for generative work,
   it cannot replace Glimmer; Ask AI is the first mode, not the
   only mode
5. What Ask AI cannot do — it cannot make knowledge durable;
   it cannot force application under ambiguity; it cannot produce
   generative capability; these are the jobs of the other three modes

**Worked example:**
A medical student asks: "What is beta blockade?" Two responses shown
side by side — the unguarded chatbot response (complete, fluent,
forgettable) and the Ask AI response (a question back: "What did
you observe about heart rate in the prerequisite section?"). The
student who received the question has to think. The student who
received the answer doesn't have to.

**Exercises (3):**
1. (Apply) For a concept in your domain, write the Ask AI response
   to "Can you explain this to me?" — a question that requires the
   student to retrieve and articulate, not receive.
2. (Analyze) Identify a concept in your curriculum where Ask AI
   would be patronizing or inappropriate. Name the mode that would
   be better and why.
3. (Evaluate) In your deployment context, what percentage of student
   questions are "acquisition" questions (student has no schema yet)
   versus "retrieval" questions (student has a schema but is forgetting)?
   What does that ratio imply for how much Ask AI your students need?

**Bridge:** Ask AI gets the student to a fragile first understanding.
Quiz Me makes that understanding durable. Chapter 4.

---

### CHAPTER 4 — Quiz Me: Making Knowledge Stick

**One-line:** The reader learns what spaced retrieval practice is,
why it works, and when Quiz Me adds something that Anki or Canvas
quizzes do not.

**Opening:**
There is a finding in cognitive psychology so well-replicated that
it functions as a law: testing yourself on material produces more
durable learning than re-reading it, even when re-reading feels
more productive. Students who study by testing themselves perform
worse immediately and better at every subsequent measurement.

This is the testing effect, and it is the mechanism Quiz Me is built on.

**Core content blocks:**
1. The testing effect in plain language — why retrieving something
   from memory changes the memory; why re-reading feels good and
   produces less learning; the counterintuitive finding that worse
   practice performance predicts better retention
2. Spaced repetition — why distributing practice over time produces
   more durable retention than massing it; the FSRS algorithm in
   one sentence: the more you struggle to retrieve something, the
   longer it stays
3. What Quiz Me adds beyond Anki — the integration with the concept
   node map; priority weighting for high-importance concepts;
   the aviation pedagogy principle (safety-critical concepts reviewed
   regardless of recall score); the prerequisite interleaving that
   forces discrimination learning
4. When Quiz Me is NOT the right mode — for concepts requiring
   application under ambiguity, retrieval practice produces pattern
   matching, not reasoning; for generative capability, retrieval
   practice alone does not build what Glimmer builds
5. The habit loop — why the due-count counter is as important as
   the algorithm; why the completion event is the reward; why
   Quiz Me is designed as a maintenance habit, not an assessment

**Worked example:**
Two students preparing for a pharmacology board exam. Student A
re-reads their notes every Sunday. Student B runs Quiz Me for
12 minutes every morning. Two weeks before the exam, Student A
scores higher on a practice test. On exam day, Student B scores
higher. The testing effect in one scenario.

**Exercises (3):**
1. (Apply) Identify five concepts in your curriculum that require
   durable factual recall (drug names, anatomical structures, clinical
   criteria). These are Quiz Me candidates. Identify five that require
   reasoning under ambiguity. These are not.
2. (Analyze) Your institution uses Canvas quizzes for retrieval
   practice. What does Quiz Me's FSRS scheduling add that Canvas
   quizzes cannot provide? Name the specific mechanism.
3. (Evaluate) For a 15-week course, estimate how many Quiz Me
   sessions a student would complete if the habit formed in week 2
   versus week 6. What design choice most affects habit formation?

**Bridge:** Quiz Me makes factual and conceptual knowledge durable.
It does not teach students to use that knowledge when the situation
is ambiguous and the right answer is not obvious. That is Case Study's job.

---

### CHAPTER 5 — Case Study: The Mode for Judgment Under Ambiguity

**One-line:** The reader learns what Case Study is, what cognitive
operation it serves that Ask AI and Quiz Me cannot, and what
institutional commitments are required to deploy it without producing
plausible-confident-wrong reasoning at scale.

**Opening:**
Professional education trains students for well-structured-problem
performance. Professional practice requires ill-structured-problem
judgment. This is not a new observation. The Carnegie Foundation
documented it in medical education in 2010 and engineering education
in 2008. The gap has not closed.

Case Study is the first of Medhavy's two answers to that gap. It is
not an enhancement to Ask AI or Quiz Me. It is a different cognitive
operation entirely: judgment under ambiguity.

**Core content blocks:**
1. What Case Study is — a pre-written, faculty-reviewed clinical or
   domain scenario presented after the student has demonstrated
   understanding of underlying concepts; the AI facilitates discussion,
   never gives the answer
2. Why pre-written and faculty-reviewed — the prohibition on
   AI-generated cases; why a plausible-sounding wrong clinical claim
   in a case scenario is a patient safety risk; why the faculty review
   gate is a safety control, not a quality control
3. The graduated assistance ladder — why the case starts with broad
   evidential questions and escalates only when the student demonstrates
   engagement; the assistance dilemma in plain language: too much help
   produces offloading, too little produces shutdown
4. When Case Study is the right mode — application under ambiguity;
   the student who can retrieve a concept but cannot deploy it when
   the situation is unclear; the cognitive operation that produces
   flexible, transferable knowledge
5. When Case Study is not the right mode — the prerequisite gate;
   why a Case Study deployed before the underlying Quiz Me material
   is consolidated produces guessing, not reasoning

**Worked example:**
A second-year pharmacy student walks through three stages of the
four-mode sequence on beta blockade. After Chapter 3 (Ask AI): can
explain what beta blockade is. After Chapter 4 (Quiz Me): can
recall the mechanism reliably under timed conditions. After Case
Study (a sixty-four-year-old man with COPD, heart failure with
reduced ejection fraction, and a resting heart rate of fifty-two):
can defend a recommendation under ambiguity and revise it when the
AI surfaces a consideration she has not named. Stage 4 (Glimmer)
picks up in Chapter 6.

**Exercises (3):**
1. (Understand) For one concept in your curriculum, describe in one
   paragraph what a student who has completed Ask AI and Quiz Me can
   reliably do. Then describe what they still cannot do that Case
   Study would address. Name the specific form of ambiguity in the
   gap.
2. (Apply) Identify one faculty member in your program who has the
   domain expertise to write and review Case Study scenarios for a
   high-priority learning objective. Estimate the time required, per
   scenario, for them to author the case and complete the
   Socratic-laddering review.
3. (Evaluate) In your deployment, what percentage of your learning
   objectives require students to apply knowledge under ambiguity
   without a single correct answer? Those are Case Study candidates.

**Bridge:** Case Study covers judgment under ambiguity — the student
can already retrieve the concept and now learns to decide whether to
deploy it when the situation is unclear. The next mode is different
in kind. Glimmer asks the student to produce something original and
defend it. Chapter 6.

---

### CHAPTER 6 — Glimmer: The Mode for Defended Generation

**One-line:** The reader learns what Glimmer is, what cognitive
operation it serves that the other three modes cannot, and how the
five-dimension defense and AI pre-grading reviewer make generative
assessment possible at scale without producing a class of students
who outsource their thinking.

**Opening:**
Chapter 5 introduced the gap that Case Study addresses: the boards
measure recall; practice requires judgment under ambiguity. Glimmer
addresses the same gap from a different angle. Where Case Study
trains the student to decide what to do when the situation is unclear,
Glimmer trains the student to *produce* something — a protocol, a
plan, a design — that did not exist before, and to defend it. The
cognitive operation is generation, not application. It sits at the
top of Bloom's revised taxonomy: Create.

**Core content blocks:**
1. What Glimmer is — a generative, open-ended assignment where the
   student produces something that did not exist before; no single
   correct answer; graded on reasoning quality, not output
2. The five dimensions — WHY (problem framing), Usefulness,
   Mechanism (causal steps), Defensibility, Specificity; why each
   dimension is designed to resist AI offloading
3. The AI pre-grading reviewer — why it asks one targeted question
   about the weakest dimension rather than providing comprehensive
   feedback; the distinction between process-level and task-level
   feedback; why "one targeted question" breaks the most expensive
   faculty habit
4. The emergent term project — why students don't know they're
   building a portfolio until week 10; why hiding the destination
   produces more authentic work than announcing it; the honest
   admission that this is a pedagogical bet with theoretical support
   but thin direct evidence
5. When Glimmer is NOT the right mode — Alexander's Model of Domain
   Learning; for students without sufficient prior knowledge, Glimmer
   produces anxiety, not learning; backwards-faded scaffolding adapted
   from Renkl and Atkinson; the phase gate that prevents premature
   deployment

**Worked example:**
The same pharmacy student from Chapter 5, now at Stage 4. Assignment:
*Design a clinical protocol for initiating beta blockade in patients
with concurrent COPD and reduced ejection fraction, including
monitoring parameters, escalation criteria, and de-escalation triggers.
Defend every decision against the obvious counter-argument.* She
produces a four-page protocol. The AI pre-grading reviewer flags
Specificity weakness — the monitoring intervals are vague — and asks
one targeted question. She revises. The faculty member grades the
revised version. The protocol joins her term portfolio.

**Exercises (3):**
1. (Understand) For one Glimmer-style assignment in your curriculum,
   write a sample student artifact one paragraph long. Then write the
   one targeted question an AI pre-grading reviewer would ask about
   its weakest dimension. Name the dimension.
2. (Apply) Pick a learning objective in your program that currently
   ends in a written assignment graded on the artifact. Rewrite the
   assignment so the grade is on the reasoning, using the five
   dimensions.
3. (Evaluate) In your deployment, what percentage of your learning
   objectives require students to produce something original and
   defend it? Those are Glimmer candidates. Then identify one specific
   risk and one specific benefit of the emergent term-project design
   in your program's culture.

**Bridge:** The four modes cover the full cognitive sequence —
acquire, retain, apply, generate. The question is whether your
institution needs all four, and whether you can tell whether they're
working. That requires measurement. Chapter 7.

## ACT TWO — WHAT DOES MEDHAVY MEASURE THAT CANVAS DOESN'T? (Chapters 7–9)

---

### CHAPTER 7 — What Canvas Measures and What It Misses

**One-line:** The reader learns the specific gap between engagement
analytics and learning evidence — and why that gap is the adoption
decision's hinge.

**Opening:**
Canvas shows you who opened the module, how long they stayed,
whether they submitted the assignment, and what score they received.
None of those measurements tells you whether the student learned
anything they can use six weeks later without the textbook in front
of them.

This is not a criticism of Canvas. Canvas was designed to administer
courses, not to measure learning. The gap between administration
metrics and learning evidence is not a Canvas failure. It is a
category difference. Medhavy is built specifically for the second
category.

**Core content blocks:**
1. What Canvas actually measures — the five standard analytics:
   time on page, clicks, completion rate, quiz score, submission
   rate; what each one captures; what each one misses
2. The performance-learning paradox — Bjork's distinction in
   plain language: the student who scores well immediately after
   instruction and forgets by next week; why immediate performance
   is not a reliable predictor of durable learning; the Bastani
   finding as the most extreme demonstration
3. The decoupling problem — how generative AI made artifact-based
   assessment unreliable; why the essay that looks like understanding
   no longer necessarily is; what this means for Canvas's gradebook
4. What learning evidence actually requires — behavioral traces
   of genuine cognitive engagement; why these are different from
   performance metrics; introduction to the Frictional Framework
   concept (full detail in Chapter 8)

**Worked example:**
Two students, same Canvas analytics. Both logged 47 minutes on the
module. Both submitted the assignment. Both scored 88%. One student
learned. One student used AI to produce the assignment without
engaging the material. Canvas cannot tell them apart. The chapter
shows what Medhavy's measurement layer sees that Canvas does not.

**Exercises (3):**
1. (Analyze) Open your Canvas analytics for one course. List every
   metric available. For each, write one sentence on what it measures
   and one sentence on what genuine learning it cannot detect.
2. (Analyze) Describe the decoupling problem to a skeptical faculty
   member who trusts Canvas gradebook scores. What one piece of
   evidence would you show them? (Hint: the Bastani study.)
3. (Evaluate) For your deployment, name the highest-stakes assessment
   in the curriculum. Is that assessment currently based on artifact
   quality, engagement data, or learning evidence? What would change
   if it were based on learning evidence?

**Bridge:** If engagement analytics are insufficient, what does
learning evidence look like? Chapter 8 introduces the seven signals.

---

### CHAPTER 8 — The Seven Signals: What Genuine Learning Looks Like

**One-line:** The reader learns the Frictional Framework's seven
signals in plain language — what each one is, what it measures,
and which mode produces it.

**Opening:**
Genuine learning leaves traces. Not in the artifact the student
produces — AI can produce that without the student having learned
anything. In the behavior surrounding the artifact's production:
how time was distributed, whether errors followed a coherent pattern,
whether knowledge held up at a delay, whether a partial hint
activated something already developing.

These are the seven friction signals. They are not experimental.
They are behavioral consequences of the neurobiological events that
constitute genuine learning. They exist whether or not the platform
measures them. Medhavy measures them.

**Core content blocks:**
1. Why genuine learning leaves behavioral traces — the neurobiological
   argument in two paragraphs: prediction error drives encoding,
   consolidated traces produce durable retrieval; borrowed certainty
   bypasses both; the traces are the evidence of which path was taken
2. The seven signals in plain language (one paragraph each):
   - Y1 Temporal Engagement — harder material takes longer when
     processing is genuine; AI offloading decouples time from difficulty
   - Y2 Error Trajectory Coherence — real misconceptions produce
     coherent errors that update; guessing produces random errors
   - Y3 Cross-Context Transfer — genuine understanding applies to
     new contexts; surface learning does not
   - Y4 Uncertainty Calibration — genuine learners know what they
     don't know; AI-assisted students inherit the AI's confidence
     without the underlying knowledge
   - Y5 Social Knowledge Texture — genuine engagement produces
     specific confusions and real-time position changes; borrowed
     certainty produces smooth generic statements
   - Y6 Retrieval Strength Decay — genuine learning holds up at
     delay; borrowed performance collapses
   - Y7 Scaffolding Response Curve — genuine partial understanding
     responds to a partial hint; borrowed certainty needs the full
     answer
3. Which mode produces which signal — the mode-to-signal mapping
   in plain language; why the combination is what makes the GLP
   score robust
4. What the GLP score is NOT — not a grade; the instructor as
   meta-model; the GLP score adds evidence, it does not replace
   judgment

**Worked example:**
The two-student scenario from Chapter 7, now shown through the
seven signals. Student A (genuine learner) and Student B (AI-assisted)
produce identical Canvas analytics and identical assignments. The
seven-signal comparison shows where they diverge and which signals
are most diagnostic for each mode.

**Exercises (3):**
1. (Understand) For each of the seven signals, name one behavior
   you have observed in a student that would register as genuine
   learning on that signal — something specific you have seen in
   office hours, class discussion, or assignments.
2. (Apply) For your highest-risk assessment (the one where AI
   offloading would cause the most harm), identify which two or
   three signals would be most diagnostic. Name why.
3. (Evaluate) Which of the seven signals could you currently
   observe, even imperfectly, in your Canvas deployment without
   adding Medhavy? Which cannot be observed without Medhavy?

**Bridge:** The seven signals are what Medhavy measures. The loop
is what Medhavy does with that measurement. Chapter 9.

---

### CHAPTER 9 — The Loop: Present, Measure, Adapt

**One-line:** The reader learns what the contextual bandit is in
plain language, what "adapt" actually means in practice, and why
Canvas cannot close the loop Medhavy closes.

**Opening:**
Medhavy is not a smarter way to present content. It is a system
that learns, per student per concept, which interventions produce
genuine learning and surfaces those interventions more frequently.
The technical name for this is a contextual bandit. The plain-language
name is: an experiment that runs continuously, with learning outcomes
as the reward signal, and adapts based on what it finds.

**Core content blocks:**
1. The loop in concrete terms — present differently (interventions,
   not just explanations); measure whether it helped (the seven
   signals, not engagement metrics); adapt (the bandit updates its
   policy); repeat; why each step is necessary and what breaks
   without it
2. What "present differently" actually means — interventions as
   the unit of variation; the difference between "a different
   explanation" and "a different pedagogical approach"; the evidence
   library behind each intervention (Socratic vs. didactic, problem-first
   vs. concept-first, spaced vs. massed — each has a different
   evidence base and a different appropriate context)
3. The contextual bandit in plain language — the slot machine analogy;
   why the bandit explores and exploits simultaneously; why it runs
   per-student per-concept rather than using population averages;
   why this is the only design that respects learner heterogeneity
4. What Canvas cannot do that Medhavy can — Canvas administers
   courses; Medhavy runs experiments; the loop requires measurement
   and adaptation in the same system; bolt-on tools cannot close it
5. The honest limits — cold start problem in plain language; why
   the first six sessions are exploratory; what the institution
   needs to provide for the loop to work

**Worked example:**
One concept node across eight weeks of deployment. Week 1: bandit
has no data, explores all modes. Week 3: Ask AI producing Y2 signal
for this concept, Quiz Me producing Y6, Case Study not yet tried.
Week 6: Case Study unlocked after Quiz Me threshold met, producing
Y3 and Y7. Week 8: bandit's policy for this concept is taking shape
— 40% Case Study, 35% Quiz Me, 25% Ask AI for this student. Another
student's policy looks different. The bandit is doing what a skilled
human tutor would do if they had infinite patience and perfect memory.

**Exercises (3):**
1. (Analyze) In your deployment, who currently performs the "adapt"
   function? (An instructor who adjusts based on exam results?
   No one?) What information do they use? What information are
   they missing?
2. (Apply) For one high-stakes concept in your curriculum, describe
   what the loop would need to measure to determine whether students
   are genuinely learning versus performing. Which of the seven
   signals are relevant?
3. (Evaluate) The bandit requires a reward signal. In Medhavy, the
   reward is delayed retrieval accuracy at seven days. In your
   deployment, what would the equivalent be? Is that measurement
   currently possible without Medhavy?

**Bridge:** You now have the full picture: four modes, seven signals,
one loop. The question is whether your deployment needs it. Chapter 10.

---

## ACT THREE — IS THE LOOP WORTH IT FOR MY DEPLOYMENT? (Chapters 10–12)

---

### CHAPTER 10 — When Kindle Is Enough

**One-line:** The reader gets the complexity threshold test — three
questions that determine whether their deployment warrants Medhavy
or whether AI+1 on Kindle is the complete answer.

**Opening:**
The most expensive mistake in educational technology is solving the
wrong problem correctly. A deployment that does not need the loop,
given the loop, has spent money on overhead and added complexity
without adding learning value.

This chapter is the discipline that says: not always, and here
is how to know.

**Core content blocks:**
1. The three questions — stated clearly as the decision framework:
   (1) Does the deployment need to present content differently to
   different learners at scale? (2) Does someone need to know whether
   the variation is helping? (3) Is the institution willing to act
   on what the measurement reveals?
2. When all three are no — the AI+1 on Kindle deployment; what
   makes it complete; the nursing class of 30 with one instructor
   example; why adding Medhavy would be overhead, not value
3. When all three are yes — the conditions that make the loop
   worth closing; scale, heterogeneity, and accountability as the
   three drivers; the 300-student multi-section example
4. The partial cases — one yes, two no; two yes, one no; what
   each combination implies for the adoption decision
5. What "willing to act" actually requires — the institution has
   to be prepared to change something based on what the measurement
   reveals; Medhavy without the willingness to adapt is expensive
   Canvas analytics

**Worked example:**
Five deployments run through the three-question test. Each gets a
yes/no verdict and a one-sentence justification. The reader should
be able to run their own deployment through the test by the time
the examples are done.

**Exercises (3):**
1. (Evaluate) Run your primary deployment through the three
   questions. Record your honest answers and your reasoning.
2. (Evaluate) Identify the deployment in your institution where
   all three answers are most clearly yes. What would Medhavy
   need to show that deployment within one term to justify renewal?
3. (Create) Write a one-paragraph recommendation for or against
   adding Medhavy to a deployment of your choice. The recommendation
   must cite the three questions and must be honest about which
   answers were uncertain.

**Bridge:** If the answer is yes, what does adding Medhavy to
Canvas actually involve? Chapter 11.

---

### CHAPTER 11 — Adding Medhavy to Canvas: What Actually Changes

**One-line:** The reader learns what LTI integration means in
plain language, what changes for students, instructors, and the
institution, and what the institution needs to provide.

**Opening:**
Adding Medhavy to a Canvas deployment is not a technical project.
The LTI integration is straightforward. What takes time and requires
institutional commitment is the curriculum design layer — specifying
what the content map looks like, which concepts get which modes,
and what the measurement thresholds are.

**Core content blocks:**
1. LTI integration in plain language — what LTI is; what "single
   sign-on from Canvas" means for students; what "grade passback"
   means for instructors; why the technical setup takes days and
   the institutional approval takes months
2. What changes for students — the four-mode interface replaces
   (or supplements) the standard textbook experience; Quiz Me as
   a daily habit; Case Study and Glimmer as assignments that look
   different from traditional ones
3. What changes for instructors — the GLP dashboard versus the
   Canvas gradebook; what the instructor does with information
   Canvas did not provide; the instructor as meta-model for
   combining GLP scores with artifact quality
4. What the institution must provide — curriculum design (the
   concept map, prerequisite graph, mode assignments); faculty
   review for Case Study scenarios; willingness to act on what
   the measurement reveals
5. What Medhavy does not require from the institution — the
   institution does not need to understand the bandit algorithm;
   does not need to retrain faculty in pedagogy; does not need
   to replace Canvas

**Worked example:**
A pharmacology department adds Medhavy to one course section.
Walk through the six-week setup: LTI configuration (2 days),
institutional approval process (8 weeks, running in parallel),
concept map specification with the course instructor (3 sessions),
Case Study scenario review (2 faculty members, 4 hours each),
student onboarding (15 minutes first session). What the instructor
sees in week 8 that she could not see before.

**Exercises (3):**
1. (Apply) Identify the single faculty member in your program
   most likely to be an early adopter of Medhavy. What would
   their role in the setup be? What would they need from you?
2. (Apply) Map your institutional approval process for adding
   a new LTI tool. Who needs to sign off? What security and
   privacy review is required? How long does it typically take?
3. (Evaluate) For your institution, what is the realistic
   timeline from "decision to add Medhavy" to "first students
   in the loop"? Is that timeline acceptable given the deployment
   need?

**Bridge:** You have the framework. You have the implementation
picture. Chapter 12 is the decision.

---

### CHAPTER 12 — The Adoption Decision

**One-line:** The reader produces their justified adoption
recommendation — for or against, with specific reasoning — and
knows what success looks like if the answer is yes.

**Opening:**
This chapter does not make the decision for you. It gives you the
structure to make it yourself and the language to explain it to
a budget committee.

**Core content blocks:**
1. The decision framework assembled — the three questions, the
   mode-to-need matching, the institutional requirements, the
   timeline; a one-page decision tool the reader can use
2. What success looks like if the answer is yes — what to measure
   in the first term; what the GLP signals should show; what
   would justify renewal; what would not
3. What failure looks like — the three most common failure modes
   for Medhavy deployments: wrong deployment context (should have
   used Kindle only), insufficient curriculum design (the
   "suggest 15 chapters" failure), unwillingness to act on
   measurement (adding the loop without closing it)
4. The honest case for no — written as a genuine recommendation,
   not a hedge; specific deployment types where AI+1 on Kindle
   is the better answer and adding Medhavy would be overhead
5. Talking to the budget committee — the three sentences that
   explain what Medhavy adds that Canvas cannot provide; the
   one question that reveals whether the deployment is ready

**Worked example:**
A justified adoption recommendation written in the voice of the
book's primary reader — the curriculum director making the call
for her health sciences program. Shows the reasoning, the
conditions, the success criteria, and the honest acknowledgment
of what is not yet known.

**Exercises (3):**
1. (Create) Write your adoption recommendation. One page. Must
   answer: what deployment are you evaluating, what are your
   three-question answers, what would Medhavy add that Canvas
   cannot, what would success look like in the first term, and
   what would cause you to not renew.
2. (Create) Write the two-minute explanation of Medhavy for
   your budget committee. No jargon. No vendor language. Must
   include what it does that Canvas doesn't, and when it is
   not the right answer.
3. (Evaluate) If your answer is no, write the specific conditions
   under which you would revisit. What would have to change in
   your deployment context for the three-question answers to
   flip?

**Closing:**
AI+1 is a better textbook. For most deployments, that is enough.
For deployments that need to present differently, measure whether
it helped, and adapt — Medhavy closes the loop that Canvas leaves
open. The decision is yours. This book gave you the framework.
The rest is judgment, which is irreducibly human.

---

# PART 9 — CHAPTER ANATOMY TEMPLATE

Every chapter follows this structure:

1. Chapter title
2. One-line capability description
3. Opening case (failure-first or puzzle-first; no jargon before
   the problem is felt)
4. Core content blocks (4–5 per chapter; each ends with a
   decision-relevant implication)
5. Worked example (a real or realistic deployment scenario,
   not a hypothetical)
6. Exercises (3 per chapter; at least one requiring the reader
   to apply the chapter to their own deployment)
7. Chapter closing and bridge to next chapter

**Enforcement:** Draft chapters missing the opening case or the
worked example are incomplete. Both are load-bearing. The reader
must encounter a real scenario before they encounter a framework.

**Tone rule:** This book sounds like a trusted colleague who has
done the research and is giving a straight answer. It does not
sound like a vendor pitch, an academic paper, or a training manual.
Every claim is evidence-grounded. Every evidence citation is
translated into plain language before it is used.

---

# PART 10 — HARD TOPICS, CONTESTED CLAIMS, AGING RISK

## Hard chapters

**Chapter 7 (What Canvas Measures):** The reader has spent a
career using Canvas analytics as a proxy for learning. The chapter
must correct a deeply held professional habit without insulting the
reader. The Bastani finding is the load-bearing evidence — it must
be presented accurately and accessibly. Risk: if this chapter reads
as anti-Canvas or anti-technology, it will alienate the primary reader.

**Chapter 10 (When Kindle Is Enough):** The hardest chapter to write
honestly, because it argues against the book's own subject. Must
make the genuine case that a simpler stack is correct for many
deployments. Risk: if this chapter reads as a hedge or a disclaimer,
it undermines the book's credibility. It must read as a genuine and
confident recommendation for the simpler path when appropriate.

## Contested claims

| Claim | Status | Book's position |
|---|---|---|
| Bastani 2025 PNAS finding (unguarded AI harms learning) | One RCT, one country, one subject | Presented as the strongest available evidence; explicitly flagged as one study needing replication |
| FSRS outperforms SM-2 | Established on scheduling benchmarks; not an RCT on learning outcomes | Stated as scheduling efficiency; explicitly distinguished from learning-outcome evidence |
| Contextual bandit produces per-learner adaptation | Theoretically sound; limited deployed evidence at Medhavy scale | Presented as a bet with strong theoretical support; not as a proven outcome |
| GLP seven signals distinguish genuine learning from borrowed certainty | Strong theoretical basis; limited large-scale validation | Presented as the framework with honest acknowledgment of what direct evidence exists |

## Aging risk

| Content | Risk | Mitigation |
|---|---|---|
| Platform landscape comparisons (ALEKS, Khanmigo) | HIGH — moves fast | Frame as evidence-type comparisons, not platform rankings |
| LTI integration specifics | MEDIUM — spec stable, institutional processes change | Kept at principle level; direct to docs.claude.com for current specifics |
| Bastani 2025 as anchor finding | LOW-MEDIUM — needs replication | Explicitly flagged as one study; framed as "strongest currently available" |
| The four modes as Medhavy's architecture | LOW — these are stable by design | These are the stable core of the book |
| GLP signal evidence base | LOW — neurobiological basis is stable | Framed as mechanistic argument, not as current findings |

---

# PART 11 — OPEN QUESTIONS

| # | Question | Stakes | Deadline | Owner |
|---|---------|--------|----------|-------|
| 1 | Bastani finding presentation — how much detail is right for a non-research reader? Full study description or translated finding only? | Chapter 1 and 7 tone | Before Ch 1 draft | Author |
| 2 | Chapter 10 (When Kindle Is Enough) — is this chapter honest enough to recommend against Medhavy in plain language, including naming specific deployment types where it is wrong? | Book credibility | Before Ch 9 draft | Author |
| 3 | The "willing to act" condition — what does this actually require from an institution? Need concrete examples of institutions that had the data and didn't act. | Chapter 9 and 10 specificity | Before Ch 8 draft | Author |
| 4 | Brutalist slides — is this explained enough for a reader who has never encountered it? Does it need its own section in Chapter 2? | Chapter 2 completeness | Before Ch 2 draft | Author |
| 5 | GLP score — what does the reader actually see in the instructor dashboard? Need a realistic mock dashboard description or screenshot for Chapter 8. | Chapter 8 concreteness | Before Ch 7 draft | Author |
| 6 | The adoption decision in Chapter 12 — is the one-page decision tool a table, a flowchart, or prose? What format serves the primary reader best? | Chapter 12 utility | Before Ch 11 draft | Author |

---

*Full TIKTOC.md v1.0 — compiled from all phase outputs*
*All phases complete: Vision (i1–i4), Learning Architecture (l1–l4),*
*Chapter Architecture (c1), Build (g1)*
*Primary structural risk: Chapter 10 (When Kindle Is Enough) must*
*genuinely argue against the book's subject — this is the chapter*
*that earns the book's credibility*
*Primary reader test: a curriculum director with no research background*
*should be able to read any chapter and finish it knowing what to do*
