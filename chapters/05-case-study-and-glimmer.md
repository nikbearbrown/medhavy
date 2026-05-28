# Chapter 5 — Case Study and Glimmer: The Two Modes Nobody Explains

**One-line capability:** The reader learns what Case Study and Glimmer
are, why they exist as separate modes, and what cognitive operation each
one serves that Ask AI and Quiz Me cannot.

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

Case Study and Glimmer are Medhavy's two answers to this gap. They are
not enhancements to Ask AI and Quiz Me. They are different modes —
different cognitive operations — that exist precisely because the first
two modes cannot do what these two do. Ask AI gets the student to a
first understanding. Quiz Me makes that understanding durable. Then the
student needs to deploy it when the situation is unclear, and to produce
something original and defend it. Those are the two modes nobody on the
vendor call ever explained to you.

This chapter explains them.

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
Chapter 6 returns to — that immediate performance and durable learning
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

### Why pre-written and faculty-reviewed

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
you buy Medhavy. Chapter 10 makes the timeline concrete.

### The graduated assistance ladder

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
in software, using the seven signals (Chapter 7) to detect when the
student needs more support and when more support would be harmful.

[Humanitarians AI internal framework — the specific ladder structure
and hint-escalation rules are proprietary. The underlying assistance-
dilemma mechanism is Koedinger and Aleven's.]

### When Case Study is the right mode

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

### When Case Study is not the right mode

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

## Glimmer — what it is

A Glimmer in Medhavy is a generative, open-ended assignment. The
student produces something that did not exist before — a clinical
protocol, a deprescribing plan, a public-health surveillance design.
There is no single correct answer. The grade is on the reasoning, not
on the output. [Humanitarians AI internal framework — Medhavy
proprietary mode design]

This is the cognitive operation at the top of Bloom's revised taxonomy:
Create. The assignment type — generative, defended, original — has been
a mainstay of professional education for a century. The dissertation,
the design project, the case write-up. What is new is the architecture
around it: AI as pre-grading reviewer, five specific dimensions of
defense, and a destination the student does not know about until the
term is almost over.

### The five dimensions

Glimmer evaluates the student's reasoning along five dimensions. These
are Medhavy's framing; the underlying components draw on adjacent
literature on argumentation (Stephen Toulmin, *The Uses of Argument*,
1958), feedback (John Hattie and Helen Timperley, *Review of Educational
Research*, 77(1), 2007), and process-level evaluation of reasoning.
The integration is Medhavy's. [Humanitarians AI internal framework —
the five-dimension rubric is proprietary; the underlying argumentation
and feedback literature is not.]

The five dimensions, in plain language:

- **WHY.** Did the student frame the problem before solving it? A
  deprescribing plan that opens with "the patient is on too many drugs"
  has not framed anything. A plan that opens with "this patient's
  primary clinical risk is a fall, the primary contributor to fall
  risk is the combination of A, B, and C, and the deprescribing
  priority follows from that risk hierarchy" has framed the problem.
  WHY resists offloading because the framing is domain-specific and
  current LLMs produce generic framing absent explicit human direction.

- **Usefulness.** Would this output be useful to a real practitioner?
  A theoretically defensible plan that ignores the realities of the
  outpatient clinic is not useful. A plan that names the realities and
  works within them is. Usefulness resists offloading because real-
  world utility judgment requires familiarity with the practice context.

- **Mechanism.** Did the student explain the causal steps? Not "we
  reduced the diuretic dose" but "we reduced the diuretic dose because
  the patient's volume status had stabilized after the change in
  blood pressure medication, which we expect to reduce the workload
  on the remaining kidney function via the following mechanism."
  Mechanism resists offloading because mechanistic causal explanation
  in a specific clinical context is something current LLMs do
  unevenly — fluent but often hollow.

- **Defensibility.** Can the student defend the choice against the
  reasonable counter-argument? If the obvious objection is "but this
  patient was previously on warfarin for a reason," does the plan
  address that reason? Defensibility resists offloading because
  anticipating counter-arguments requires the student to hold both
  the position and the objection in mind simultaneously.

- **Specificity.** Did the student commit to specifics? Not "monitor
  closely" but "obtain a CBC and BMP at one week and again at three
  weeks; specific values that would trigger a change are X and Y."
  Specificity resists offloading because vague answers from an LLM
  are easy; concrete, defensible specifics in this clinical context
  are not.

Each dimension is designed to require something a current LLM is
weaker at than a fluent paragraph: domain-grounded framing, contextual
utility, mechanistic causal explanation, anticipation of counter-
argument, concrete commitment. None of these is a trick. They are the
features of clinical reasoning that the dissertation defense has been
testing for a hundred years.

### The AI pre-grading reviewer

After a student submits a Glimmer, the AI asks one targeted question
about the weakest of the five dimensions. Not a comprehensive critique.
One question.

This is on purpose. John Hattie and Helen Timperley's 2007 synthesis
of effective feedback distinguished four levels: task, process, self-
regulation, and self. The strongest learning effects came from
process-level feedback — feedback about the reasoning, not the output.
Comprehensive feedback at the task level (annotated paragraphs, line
edits) produced weaker learning gains than a single well-aimed question
at the process level (Hattie and Timperley, *Review of Educational
Research*, 77(1), 2007).

The AI pre-grading reviewer is the process-level feedback move at
scale. It is not a substitute for faculty grading; faculty still grade
the final Glimmer. It is a layer that gets the student to revise their
reasoning before they hand it in. The first version of the deprescribing
plan goes to the AI reviewer, which asks: "You explained why you
removed the second antihypertensive, but the patient was started on it
for a reason. What would you tell the prescribing physician?" The
student revises. The faculty member sees the revised version.

### The emergent term project

The first Glimmer in week three of the course looks like an
isolated assignment. The second, in week six, looks like a slightly
larger assignment in the same domain. By week ten the student is told,
plainly: the Glimmers you have been doing build into a term portfolio,
and the integrated portfolio is the final assessment.

The students did not know this in week three. Medhavy's design choice.
The pedagogical bet: announced portfolios produce student-strategic
output (what does the rubric want?), while emergent portfolios produce
work the student took seriously for its own sake at each step. The
direct empirical literature on this exact design is thin; the closest
adjacent work is on hidden-purpose effects on intrinsic motivation in
the self-determination theory tradition [verify — Deci and Ryan,
*Self-Determination Theory*, 2017]. Medhavy is making a pedagogical
bet that has theoretical support but not direct evidence.
[Humanitarians AI internal framework — the emergent term project
design is proprietary.]

### When Glimmer is not the right mode

When the student does not yet have proficiency in the domain. Patricia
Alexander's Model of Domain Learning describes three stages —
acclimation, competence, proficiency — and the cognitive operations
appropriate to each [verify — Alexander, *Educational Researcher*,
2003, on Model of Domain Learning]. A generative open-ended assignment
in week three of pharmacology, when the student has just barely
acquired vocabulary, does not produce learning. It produces anxiety.
The student knows they do not know enough; the assignment confirms it;
the next assignment feels worse.

Medhavy's response is backwards-faded scaffolding, adapted from
Alexander Renkl and Robert Atkinson's faded worked-example research
in algebra (Renkl and Atkinson, *Educational Psychologist*, 38(1),
2003). Early in the domain, the Glimmer comes with most of the
structure provided — only the final step is the student's. As the
student progresses, the structure fades. By proficiency stage, the
Glimmer is fully open. The phase gate prevents premature deployment.
The fade is also a Medhavy design choice; the worked-example research
gives theoretical support, but the adaptation from algebra to clinical
reasoning is itself an extrapolation. [Humanitarians AI internal
framework — the backwards-faded scaffolding for clinical Glimmer is
proprietary.]

---

## Worked example — the same student, four stages

Beta blockade in pharmacology. One student. Four stages of the
four-mode sequence.

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

**Stage 4 — Glimmer.** Design a clinical protocol for initiating
beta blockade in patients with concurrent COPD and reduced ejection
fraction, including monitoring parameters, escalation criteria, and
de-escalation triggers. Defend every decision against the obvious
counter-argument. The student produces a protocol. The AI pre-grading
reviewer asks one targeted question — her Specificity is weak; the
monitoring intervals are vague. She revises. The faculty member
grades the revised version. The protocol joins her term portfolio,
which she will recognize in week ten as her integrated assessment.

Four modes. Four cognitive operations. Acquire → retain → apply →
generate. The sequence is the spine of what Medhavy does.

---

## Common misconceptions

**"Case Study is just an essay assignment with an AI grader."** No.
The AI does not grade the Case Study; the AI facilitates the discussion
and surfaces the student's reasoning. The faculty review happens on
the scenario itself, before the student ever sees it. The AI's role
is during the case, asking questions and offering graduated hints,
not at the end producing a score.

**"Glimmer is a fancy essay rubric."** It is an open-ended assignment
with an AI pre-grading reviewer and a five-dimension feedback
architecture. The rubric is not the innovation; the process-level
single-question feedback move is. A rubric grades the artifact. Glimmer
grades the reasoning visible through the artifact, and the AI reviewer
gets the student to improve the reasoning before the artifact is
graded.

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

**"Glimmer can replace the dissertation defense."** No. Glimmer is a
process-level, AI-pre-graded, term-scale assignment. The dissertation
defense is a high-stakes oral evaluation in front of human experts.
Glimmer produces a portfolio that contributes to evaluation; it does
not replace the evaluation.

---

## What would change my mind

If a multi-site randomized study showed that students completing
Glimmer assignments performed no better on delayed transfer
assessments — six months out, in clinical reasoning scenarios they
had not seen — than students completing conventional essay
assignments, the chapter's central claim about Glimmer's cognitive
operation would need substantial revision. The five-dimension
framework's defense is that it targets cognitive operations
distinguishable from those a conventional essay rubric targets.
Direct empirical confirmation of that distinguishability does not
yet exist. A null result on delayed transfer would be a strong
counter-finding.

---

## Still puzzling

- The emergent term project is theoretically motivated by intrinsic
  motivation research, but the specific design — students discover
  the portfolio in week ten — has no direct empirical study. Does it
  produce more authentic work than an announced portfolio? Plausible.
  Unproven.

- Backwards-faded scaffolding has solid empirical support in algebra
  (Renkl and Atkinson) but the adaptation to clinical reasoning is
  Medhavy's extrapolation. Does the fade structure generalize? It is
  reasonable to expect so. It is not yet measured.

- The five Glimmer dimensions resist current LLM offloading. They will
  not resist forever. As models improve at mechanistic causal
  explanation and counter-argument anticipation, the five dimensions
  will erode as anti-offload defenses. What replaces them when that
  happens?

- The faculty-review gate is a safety commitment. What does it cost
  the institution in faculty time, and what is the break-even point
  at which the gate is too expensive to maintain at the depth required?

---

## Bridge

The four modes cover the full cognitive sequence — acquire, retain,
apply, generate. The question is whether your institution needs all
four, and whether you can tell whether they are working. That
requires measurement. Canvas measures engagement: clicks, time on
page, completion, scores. It does not measure learning. Chapter 6 is
about that gap. It is the hardest chapter in this book to write
without sounding like a vendor pitch, because you have spent a career
treating engagement as a learning proxy and you were not wrong to do
so. The tool was not built for the question you now need it to answer.

---

## Exercises

1. **(Understand)** For one concept in your curriculum, describe in
   one paragraph what a student who has completed Ask AI and Quiz Me
   on that concept can reliably do. Then describe what they still
   cannot do. For each of the two gaps you name, identify whether
   Case Study or Glimmer addresses it, and why.

2. **(Apply — to your own deployment)** Identify one faculty member
   in your program who has the domain expertise to write and review
   Case Study scenarios for a high-priority learning objective.
   Estimate the time required, per scenario, for them to author the
   case and complete the Socratic-laddering review (where the
   scenario's hint sequence is specified). Estimate the format
   they would need to produce. Write a one-paragraph proposal you
   could send them.

3. **(Evaluate)** In your deployment, what percentage of your
   learning objectives require students to apply knowledge under
   ambiguity without a single correct answer? Those are Case Study
   candidates. What percentage require students to produce something
   original and defend it? Those are Glimmer candidates. Write the
   two percentages and a one-paragraph defense of each estimate.
   If the combined percentage is under twenty, you have evidence
   that your deployment may not need these two modes. If it is
   over fifty, you have evidence that it might.
