# Chapter 5 — Case Study: The Mode for Judgment Under Ambiguity

**One-line capability:** The reader learns what Case Study is, what
cognitive operation it serves that Ask AI and Quiz Me cannot, and what
institutional commitments are required to deploy it without producing
plausible-confident-wrong reasoning at scale.

---

## The gap the boards do not measure

In 2010, the Carnegie Foundation published *Educating Physicians*. Three
authors — Molly Cooke, David Irby, and Bridget O'Brien — spent five years
visiting US and Canadian medical schools. Their conclusion was not
flattering and it has not aged out. Medical schools, they wrote, train
students for well-structured problems: the multiple-choice item with a
single correct stem, the four-option vignette where one answer is right
and three are distractors. Clinical practice does not look like that.
Clinical practice is the seventy-eight-year-old who came in with vague
abdominal pain and goes home with a working diagnosis that the attending
will revisit in twelve hours. Two years earlier the same foundation had
said the same thing about engineering: curricula privilege analytical
problem sets where the answer exists; practice requires synthesis,
judgment, accountability under uncertainty (Sheppard, Macatangay, Colby,
and Sullivan, *Educating Engineers*, 2008).

This is the gap. You already know it. You watch students who pass the
boards arrive at their first clinical rotation looking confident and
brittle. They know what beta blockade does. They cannot decide whether
this patient should get a beta blocker. The recall is intact. The judgment
is not yet built.

David Jonassen named the distinction in 1997. A well-structured problem
has a single correct path and a single correct answer. An ill-structured
problem has multiple acceptable paths, competing constraints, and no
clean stopping rule (Jonassen, *Educational Technology Research and
Development*, 45(1), 1997). The instructional design implications are
different. The cognitive operations are different. You cannot get the
second by drilling more of the first.

Case Study is the first of Medhavy's two answers to this gap. (The
second, Glimmer, is the subject of Chapter 6.) Case Study and Glimmer
are not enhancements to Ask AI and Quiz Me. They are different modes —
different cognitive operations — that exist precisely because the first
two modes cannot do what these two do. Ask AI gets the student to a
first understanding. Quiz Me makes that understanding durable. Then the
student needs to deploy it when the situation is unclear. That is what
Case Study trains. Producing something original and defending it is a
further step, and that is Glimmer.

This chapter explains Case Study.

---

## Case Study — what it is

A Case Study in Medhavy is a pre-written, faculty-reviewed clinical or
domain scenario presented to the student after they have demonstrated
understanding of the underlying concepts. The student works through the
case with the AI as facilitator. The AI asks questions, prompts the
student to articulate reasoning, offers graduated hints when the student
stalls. The AI does not give the answer. [Humanitarians AI internal
framework — Medhavy proprietary mode design]

That last sentence is the load-bearing one. A general-purpose chatbot
handed the same case scenario will tell the student what to do if asked.
Case Study will not. The design commitment is to facilitate the student's
reasoning, never to substitute for it. This commitment is what converts a
case scenario from a fluent demonstration into a learning event.

The mechanism beneath the commitment is older than Medhavy. Howard
Barrows, at McMaster's medical school, formalized problem-based learning
in the 1970s on a simple observation: students who acquire knowledge in
the context of a problem retrieve it better when a similar problem arises
in practice (Barrows and Tamblyn, *Problem-Based Learning*, 1980). Susan
Williams in 1992 sharpened the mechanism: the case is the retrieval cue.
Without a case context, knowledge stays inert (Williams, *Journal of the
Learning Sciences*, 2(4), 1992). Cindy Hmelo-Silver's 2004 meta-review
gave the empirical picture: problem-based learning underperforms direct
instruction on immediate factual recall and outperforms it on delayed
transfer and application (Hmelo-Silver, *Educational Psychology Review*,
16(3), 2004). The pattern matches Bjork's larger finding — which
Chapter 7 returns to — that immediate performance and durable learning
are not the same thing.

Case Study is Medhavy's operationalization of this body of work at scale.
That word *at scale* is doing work too. A program with thirty nursing
students and one experienced clinical educator does not need Medhavy
Case Study. The educator already runs case discussions in seminar; she
knows her students; she calibrates her hints in real time. A program
with three hundred students across five sections and three rotating
instructors cannot run case discussions with that fidelity. Case Study
is the four-instructor consistency problem solved in software.

[**MARGIN — AI Wayback Machine.** Imagine asking Cindy Hmelo-Silver,
Rutgers and Indiana University, who has spent thirty years studying how
problem-based learning actually works: a curriculum director says her
faculty think PBL is too expensive and the boards still test factual
recall — how should she justify case-based instruction to a skeptical
dean? Hmelo-Silver would likely say: stop arguing about board scores.
Both groups score about the same. The argument is about what students
can do six months later when the situation is unclear and a patient is
waiting. That is the measurement that matters and that is the measurement
the boards do not give you.]

---

## Why pre-written and faculty-reviewed

Why not let the AI generate the case scenario on demand? It would be
cheaper. It would scale instantly. It would feel modern.

Because in clinical domains, a plausible-sounding wrong claim is a
patient-safety risk. A large language model writing a cardiology case
can produce a clinically incoherent vignette that reads fluently: a
dosage that is wrong by a factor of ten, a drug interaction that does
not exist, a presentation that no human patient has ever had. The
student reasoning through this case learns the wrong reasoning. Repeat
across a cohort and you have produced a class of clinicians with
plausibly-confident misconceptions.

This is not a hypothetical risk. The American Association of Medical
Colleges and parallel guidance documents in 2024–2025 explicitly
recommend faculty review of any AI-generated clinical scenario before
student exposure [verify — AAMC AI in medical education guidance,
2024–2025]. The empirical evidence on whether AI-generated cases harm
learning is thin (no large RCT has been run). The safety-engineering
argument does not require the empirical evidence. In safety-critical
domains, you do not field the system that might produce
plausible-confident-wrong outputs and wait for the harm signal.

Medhavy's design choice: every Case Study scenario is authored or
reviewed by a faculty member who owns the content. The AI facilitates
the discussion within the reviewed scenario. The AI does not invent the
clinical facts. This is a process commitment, not a feature toggle.
A program that wants to deploy Case Study has to commit to the faculty
review pipeline. That commitment is part of what you are buying when
you buy Medhavy. Chapter 11 makes the timeline concrete.

The review is not a single pass. The faculty member authors or selects
the scenario, then specifies the Socratic-laddering rules: which question
the AI opens with, which hints it offers if the student stalls, which
considerations it surfaces if the student misses them. Without this
specification, the AI defaults to its own facilitation pattern, which
may or may not match the pedagogical intent of the case. The faculty
member is not handing over the case to the AI; she is configuring the
AI's role inside the case.

---

## The graduated assistance ladder

Inside a single Case Study session, the AI does not start by asking the
hardest question. It starts broadly — "what do you notice about this
patient's presentation?" — and escalates only when the student
demonstrates engagement with the previous level. If the student is
producing nothing, the AI moves down a rung. If the student is moving
fast and confident, the AI does not over-scaffold.

This is the assistance dilemma. Kenneth Koedinger and Vincent Aleven
named it precisely in 2007: too much help produces offloading — the
student lets the system do the thinking; too little help produces
shutdown — the student gives up. There is no universal correct hint
density. The optimal level depends on the student, the concept, and
the moment (Koedinger and Aleven, *Educational Psychology Review*, 19,
2007).

The graduated ladder is Medhavy's response to this dilemma at scale.
A skilled human tutor solves the assistance dilemma in real time by
reading the room. Medhavy's ladder is an attempt to do the same thing
in software, using the seven signals (Chapter 8) to detect when the
student needs more support and when more support would be harmful.
[Humanitarians AI internal framework — the specific ladder structure
and hint-escalation rules are proprietary. The underlying assistance-
dilemma mechanism is Koedinger and Aleven's.]

---

## When Case Study is the right mode

When the student can already retrieve the concept under timed conditions
but cannot decide whether to deploy it when the situation is unclear.
When the learning objective is application under ambiguity. When the
right answer is not a fact but a defended judgment.

In pharmacology: not "what does beta blockade do" — that is Quiz Me.
Case Study: a sixty-four-year-old man, history of COPD, heart failure
with reduced ejection fraction, a heart rate of fifty-two at rest.
Should he be on a beta blocker, which one, at what dose, and what
would change your answer? There is more than one defensible reasoning
path. There is also a wrong reasoning path. The work is in the defense,
not in the recall.

In nursing: not "what is sepsis" — that is Quiz Me. Case Study: a
seventy-eight-year-old post-surgical patient with a respiratory rate
that has crept from sixteen to twenty-two over four hours, mental
status that the night nurse called "a little foggier than yesterday,"
and a urine output that has dropped without obvious cause. Is this
patient septic? What do you do in the next ten minutes? The well-
structured form of this question is on the boards. The ill-structured
form is the floor.

---

## When Case Study is not the right mode

When the student does not have the underlying mechanism. A Case Study
deployed before the prerequisite Quiz Me material is consolidated
produces guessing, not reasoning. The student matches surface features
to cases they vaguely remember and arrives at an answer with no
mechanism beneath it. The AI then either reveals the answer (offload)
or refuses (shutdown). Both outcomes are pedagogical failures.

Medhavy enforces this with a prerequisite gate: a Case Study unlocks
only after the relevant Quiz Me concepts have hit a retention threshold.
This is a design choice with cost — the student cannot leap to the
clinical case before the basics are durable. The choice prevents the
worked-example boundary condition that John Sweller and Graham Cooper
identified in 1985: novices learn more from studying solutions than
from attempting novel problems they have no schema for (Sweller and
Cooper, *Cognition and Instruction*, 2(1), 1985). Case Study is for
post-novice work. Before that, the student is on Ask AI and Quiz Me.

---

## Worked example — Ask AI to Quiz Me to Case Study

Beta blockade in pharmacology. One student. Three stages of the
four-mode sequence. (The fourth stage — Glimmer — is taken up at the
end of Chapter 6.)

**Stage 1 — Ask AI.** The student is a second-year pharmacy student
who has heard the term *beta blocker* in cardiology lecture but does
not yet have a working mental model. She asks: "Can you explain beta
blockade to me?" Ask AI does not lecture her. It asks: "What did you
notice about heart rate in the prerequisite section on adrenergic
receptors?" She has to retrieve. She articulates that adrenergic
stimulation increases heart rate. Ask AI builds from there with
further questions. By the end of the session, she has constructed an
explanation. The construction is the work.

**Stage 2 — Quiz Me.** Over the next three weeks, Quiz Me schedules
retrieval practice on beta blockade: the mechanism at the receptor
level, the cardiac and noncardiac effects, the principal drug names,
the major contraindications. The first retrievals are effortful. By
week three, the student can answer the core facts under timed
conditions without prompting. The mechanism is durable. She can
explain it. She can recall it.

**Stage 3 — Case Study.** A sixty-four-year-old man with COPD, heart
failure with reduced ejection fraction, a resting heart rate of
fifty-two. Should this patient be on a beta blocker? She knows what
beta blockade does. The case asks her to decide whether it is
appropriate, which one, at what dose, and what would change her
answer. The AI facilitates. It asks: "What did you weigh first?"
She names the heart failure indication, then the COPD concern, then
the bradycardia concern. She arrives at a reasoning that names the
trade-off and commits to a recommendation. She defends the
recommendation. The AI surfaces one consideration she did not name.
She revises. The work is judgment under ambiguity, not recall.

Three modes. Three cognitive operations. Acquire → retain → apply. The
sequence is the spine of what Medhavy does up to and including the
mode this chapter is about. Chapter 6 takes the same student into the
fourth mode.

---

## Common misconceptions

**"Case Study is just an essay assignment with an AI grader."** No.
The AI does not grade the Case Study; the AI facilitates the discussion
and surfaces the student's reasoning. The faculty review happens on
the scenario itself, before the student ever sees it. The AI's role
is during the case, asking questions and offering graduated hints,
not at the end producing a score.

**"We already do case-based learning. Why would we need Case Study?"**
You do, and you may not need Case Study for the deployment you are
currently running. The Case Study question is a scale question. If
your case discussions are run by experienced faculty in small groups
with real-time facilitation, Medhavy adds little. If your case
discussions are uneven across instructors, asynchronous, or do not
exist for some learning objectives because you cannot staff them,
Medhavy Case Study is the consistency-at-scale move.

**"AI-generated cases are the same as faculty-written ones."** They
are not, and the difference is not a quality argument — it is a
safety argument. In clinical domains, plausible-confident-wrong is a
patient-safety risk. The faculty review gate is not a quality
control; it is a safety control. Programs that deploy AI-generated
cases without faculty review are accepting a risk that current AAMC
and parallel guidance documents say not to accept.

---

## What would change my mind

If a multi-site randomized study showed that students completing
faculty-reviewed Case Study sessions performed no better on delayed
transfer assessments — six months out, in clinical reasoning scenarios
they had not seen — than students completing AI-generated case
scenarios without faculty review, the safety-engineering argument
would still hold but the pedagogical argument would weaken
substantially. The chapter's claim is that faculty review protects
against a class of failure that empirical evidence cannot yet
quantify, and that the cost of that protection is justified by the
asymmetry between the harms of plausible-confident-wrong reasoning
and the cost of an extra faculty pass. A null delayed-transfer result
would not eliminate the safety argument; it would force a much
harder conversation about whether the faculty-review cost is
proportionate.

---

## Still puzzling

- The faculty-review gate is a safety commitment. What does it cost
  the institution in faculty time, and what is the break-even point
  at which the gate is too expensive to maintain at the depth required?
  Chapter 11 estimates the timeline. The cost-benefit at scale is not
  yet measured.
- The graduated assistance ladder depends on the seven signals
  (Chapter 8) being calibrated to the discipline. Cardiology hint
  density that works for second-year pharmacy students may
  systematically over- or under-scaffold for second-year nursing
  students at the same retention level. The signals are designed to
  be discipline-portable; whether they are remains an open empirical
  question.
- The prerequisite gate prevents premature Case Study deployment, but
  the threshold for "consolidated enough" is itself a design choice.
  Set too low, students arrive at Case Study guessing. Set too high,
  the integration of recall and judgment is delayed. The right
  threshold is probably concept-specific.

---

## Bridge

Case Study covers judgment under ambiguity — the student can already
retrieve the concept, and now learns to decide whether to deploy it
when the situation is unclear. The next mode is different in kind.
Glimmer asks the student to produce something original — a protocol,
a plan, a design — and defend it along five specific dimensions. The
cognitive operation is generation, not application. The architecture
around the assignment — AI as pre-grading reviewer, the five-dimension
defense, the emergent term project — is what makes it possible at
scale. Chapter 6 is about that.

---

## Exercises

1. **(Understand)** For one concept in your curriculum, describe in
   one paragraph what a student who has completed Ask AI and Quiz Me
   on that concept can reliably do. Then describe what they still
   cannot do that Case Study would address. Identify the specific
   form of ambiguity in the gap — competing constraints, missing
   information, multiple defensible paths — and name which one Case
   Study would train.
2. **(Apply — to your own deployment)** Identify one faculty member
   in your program who has the domain expertise to write and review
   Case Study scenarios for a high-priority learning objective.
   Estimate the time required, per scenario, for them to author the
   case and complete the Socratic-laddering review (where the
   scenario's hint sequence is specified). Estimate the format they
   would need to produce. Write a one-paragraph proposal you could
   send them.
3. **(Evaluate)** In your deployment, what percentage of your
   learning objectives require students to apply knowledge under
   ambiguity without a single correct answer? Those are Case Study
   candidates. Write the percentage and a one-paragraph defense of
   the estimate. If the figure is under ten, you have evidence that
   Case Study may not yet be the right Medhavy commitment for your
   program. If it is over thirty, the prerequisite-gate plumbing
   becomes the operational question — see Chapter 11.
