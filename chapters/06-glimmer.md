# Chapter 6 — Glimmer: The Mode for Defended Generation

**One-line capability:** The reader learns what Glimmer is, what
cognitive operation it serves that the other three modes cannot, and
how the five-dimension defense and AI pre-grading reviewer make
generative assessment possible at scale without producing a class of
students who outsource their thinking.

---

## The operation at the top of the taxonomy

Chapter 5 introduced the gap that Case Study addresses: the boards
measure recall; practice requires judgment under ambiguity. Glimmer
addresses the same gap from a different angle. Where Case Study trains
the student to decide what to do when the situation is unclear,
Glimmer trains the student to *produce* something — a protocol, a plan,
a design — that did not exist before, and to defend it. The cognitive
operation is generation, not application. It sits at the top of
Bloom's revised taxonomy: Create.

The assignment type is not new. The dissertation, the design project,
the case write-up. Professional education has been doing generative
defended work for a hundred years. What is new is the architecture
around it: AI as pre-grading reviewer, five specific dimensions of
defense, and a destination the student does not know about until the
term is almost over.

A Glimmer in Medhavy is a generative, open-ended assignment. The
student produces something that did not exist before — a clinical
protocol, a deprescribing plan, a public-health surveillance design.
There is no single correct answer. The grade is on the reasoning, not
on the output. [Humanitarians AI internal framework — Medhavy
proprietary mode design]

That the grade is on the reasoning is the load-bearing claim. A
generative assignment graded on the artifact — does the protocol look
plausible, does the plan list the right components — invites
offloading. A general-purpose chatbot can produce an artifact that
looks plausible. What it cannot reliably produce is a defense of that
artifact along the five dimensions Glimmer asks the student to
defend it along. The dimensions are designed so that the work the
student must do is precisely the work an LLM cannot yet do for them.

---

## The five dimensions

Glimmer evaluates the student's reasoning along five dimensions. These
are Medhavy's framing; the underlying components draw on adjacent
literature on argumentation (Stephen Toulmin, *The Uses of Argument*,
1958), feedback (John Hattie and Helen Timperley, *Review of Educational
Research*, 77(1), 2007), and process-level evaluation of reasoning.
The integration is Medhavy's. [Humanitarians AI internal framework —
the five-dimension rubric is proprietary; the underlying argumentation
and feedback literature is not.]

### WHY — did the student frame the problem before solving it?

A deprescribing plan that opens with "the patient is on too many drugs"
has not framed anything. A plan that opens with "this patient's primary
clinical risk is a fall, the primary contributor to fall risk is the
combination of A, B, and C, and the deprescribing priority follows from
that risk hierarchy" has framed the problem. WHY resists offloading
because the framing is domain-specific and current LLMs produce generic
framing absent explicit human direction. Ask an LLM to write a
deprescribing plan for an elderly patient and it will produce something
that reads as competent. Ask it to frame the *specific* risk hierarchy
for *this* patient with *these* comorbidities and the output gets
noticeably weaker.

### Usefulness — would the output be useful to a real practitioner?

A theoretically defensible plan that ignores the realities of the
outpatient clinic is not useful. A plan that names the realities and
works within them is. Usefulness resists offloading because real-
world utility judgment requires familiarity with the practice context
— what the clinic actually has time for, what the patient will
plausibly do at home, what the receiving physician will read and act
on. Generic competence at writing protocols does not translate to
context-grounded utility judgment.

### Mechanism — did the student explain the causal steps?

Not "we reduced the diuretic dose" but "we reduced the diuretic dose
because the patient's volume status had stabilized after the change in
blood pressure medication, which we expect to reduce the workload on
the remaining kidney function via the following mechanism." Mechanism
resists offloading because mechanistic causal explanation in a specific
clinical context is something current LLMs do unevenly — fluent but
often hollow. The fluent sentence is easy. The mechanism that actually
holds together when an attending asks "why" three times is harder.

### Defensibility — can the student defend the choice against the reasonable counter-argument?

If the obvious objection is "but this patient was previously on
warfarin for a reason," does the plan address that reason?
Defensibility resists offloading because anticipating counter-arguments
requires the student to hold both the position and the objection in
mind simultaneously. The student has to know enough about the patient
and the domain to predict what the reasonable critic will say. An LLM
will generate counter-arguments if asked. Predicting which
counter-arguments are the relevant ones is the skill.

### Specificity — did the student commit to specifics?

Not "monitor closely" but "obtain a CBC and BMP at one week and again
at three weeks; specific values that would trigger a change are X and
Y." Specificity resists offloading because vague answers from an LLM
are easy; concrete, defensible specifics in this clinical context are
not. The plan that names the lab, the interval, and the trigger value
is the plan that can be executed. The plan that says "monitor closely"
is the plan that produces an angry phone call from the receiving
clinician.

Each dimension is designed to require something a current LLM is
weaker at than a fluent paragraph: domain-grounded framing, contextual
utility, mechanistic causal explanation, anticipation of
counter-argument, concrete commitment. None of these is a trick. They
are the features of clinical reasoning that the dissertation defense
has been testing for a hundred years.

---

## The AI pre-grading reviewer

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
reasoning before they hand it in. The first version of the
deprescribing plan goes to the AI reviewer, which asks: "You explained
why you removed the second antihypertensive, but the patient was
started on it for a reason. What would you tell the prescribing
physician?" The student revises. The faculty member sees the revised
version.

The single-question discipline is the part that breaks the most
expensive faculty habit: the urge to mark up every weak sentence. The
empirical literature is unambiguous that comprehensive markup
underperforms targeted process-level questions. Faculty already know
this, in some way, when they discuss feedback theory. They forget it
when they pick up a pen and start writing in the margins. The AI does
not have the pen-in-hand habit; it asks one question and stops.

---

## The emergent term project

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

The bet is honest about its risk. If the emergent design produces no
authenticity advantage over an announced portfolio, the institution
has paid an information cost (students did not know what they were
building) for nothing. If it does produce the advantage, the cost was
the price of a stronger portfolio. The first cohorts of any program
deploying Glimmer are part of the evidence on this question.

---

## When Glimmer is not the right mode

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

## Worked example — completing the four-mode arc

Chapter 5 walked one student — a second-year pharmacy student
learning beta blockade — through three modes: Ask AI built her first
working model of the mechanism; Quiz Me made the mechanism durable
through three weeks of retrieval practice; Case Study put her in front
of a sixty-four-year-old man with COPD, heart failure with reduced
ejection fraction, and a resting heart rate of fifty-two, and asked
her to defend a recommendation. She arrived at a defensible reasoning
and revised it once when the AI surfaced a consideration she had not
named.

**Stage 4 — Glimmer.** The fourth assignment in the sequence:
*Design a clinical protocol for initiating beta blockade in patients
with concurrent COPD and reduced ejection fraction, including
monitoring parameters, escalation criteria, and de-escalation
triggers. Defend every decision against the obvious counter-argument.*

She produces a protocol. It runs four pages. It names the patient
population, the initiation dose for the two beta blockers she chose
to include, the monitoring interval, and the conditions under which
the dose escalates or the drug is discontinued.

The AI pre-grading reviewer reads the protocol and asks one targeted
question. Her Specificity is weak — the monitoring intervals are
vague, the trigger values are missing, and "monitor pulmonary
function" appears without a defined test or threshold. The question
is: *You wrote that pulmonary function should be monitored, but you
did not name the test, the interval, or the threshold that would
trigger a change in the protocol. A pulmonologist reading this would
not know what to order. What did you intend?*

She revises. The protocol now names spirometry at baseline and at one
month, with a 15% decline in FEV1 as the escalation trigger. The
faculty member grades the revised version. The protocol joins her
term portfolio, which she will recognize in week ten as her integrated
assessment.

Four modes. Four cognitive operations. Acquire → retain → apply →
generate. The sequence is the spine of what Medhavy does. The
generate step — Glimmer — is the one that produces the artifact a
program director can show a hospital partner when they ask what the
graduates can actually do.

---

## Common misconceptions

**"Glimmer is a fancy essay rubric."** It is an open-ended assignment
with an AI pre-grading reviewer and a five-dimension feedback
architecture. The rubric is not the innovation; the process-level
single-question feedback move is. A rubric grades the artifact. Glimmer
grades the reasoning visible through the artifact, and the AI reviewer
gets the student to improve the reasoning before the artifact is
graded.

**"Glimmer can replace the dissertation defense."** No. Glimmer is a
process-level, AI-pre-graded, term-scale assignment. The dissertation
defense is a high-stakes oral evaluation in front of human experts.
Glimmer produces a portfolio that contributes to evaluation; it does
not replace the evaluation.

**"The AI reviewer is the grader."** It is not. The AI asks one
process-level question and the student revises. The faculty member
grades the revised version. The pre-grading layer is what makes the
faculty grading worthwhile, because the faculty member is grading the
student's best reasoning, not their first draft. The AI is upstream of
the grade, not in the grade.

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

Separately: if a study showed that students whose Glimmers were
announced as a term portfolio from week one produced delayed-transfer
performance equal to or better than students under the emergent
design, the hidden-purpose pedagogical bet would lose its central
justification. The institution could keep the five-dimension
architecture and the AI reviewer and drop the emergent framing
without losing the chapter's main claim.

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
- The AI pre-grading reviewer's "one targeted question" rule is
  pedagogically sound. Whether the AI consistently identifies the
  *right* weakest dimension on a given student's submission is an
  empirical question about the seven signals (Chapter 8). The
  pedagogical commitment is one thing; the calibration of the
  detection is another.

---

## Bridge

The four modes cover the full cognitive sequence — acquire, retain,
apply, generate. The question is whether your institution needs all
four, and whether you can tell whether they are working. That
requires measurement. Canvas measures engagement: clicks, time on
page, completion, scores. It does not measure learning. Chapter 7 is
about that gap. It is the hardest chapter in this book to write
without sounding like a vendor pitch, because you have spent a career
treating engagement as a learning proxy and you were not wrong to do
so. The tool was not built for the question you now need it to answer.

---

## Exercises

1. **(Understand)** For one Glimmer-style assignment in your
   curriculum (or one you could imagine introducing), write a sample
   student artifact one paragraph long. Then write the one targeted
   question an AI pre-grading reviewer would ask about its weakest
   dimension. Name the dimension. Defend why it is the weakest of the
   five and not one of the other four.
2. **(Apply — to your own deployment)** Pick a learning objective in
   your program that currently ends in a written assignment graded on
   the artifact. Rewrite the assignment so the grade is on the
   reasoning, using the five dimensions. Identify which dimension is
   the load-bearing one for that specific objective. Write a one-
   paragraph note to the faculty member who currently grades that
   assignment explaining what changes about their grading workflow
   and what does not.
3. **(Evaluate)** In your deployment, what percentage of your
   learning objectives require students to produce something original
   and defend it? Those are Glimmer candidates. Write the percentage
   and a one-paragraph defense of the estimate. Then write what would
   change if you committed to the emergent term-project design.
   Identify one specific risk of the hidden-purpose framing in your
   program's culture, and one specific benefit. If you cannot name
   one of each, you have not yet thought hard enough about whether
   the emergent design is the right bet for your institution.
