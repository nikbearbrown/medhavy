# Chapter 9 — The Loop: Present, Measure, Adapt

**One-line capability:** The reader learns what the contextual bandit
is in plain language, what *adapt* actually means in practice, and why
Canvas cannot close the loop Medhavy closes.

---

## The thing Medhavy actually does

Medhavy is not a smarter way to present content. It is a system that
learns, per student per concept, which interventions produce genuine
learning and surfaces those interventions more frequently. The
technical name for the system is a contextual bandit. The plain-
language name is *an experiment that runs continuously, per student
per concept, with learning outcomes as the success signal*.

That sentence is the chapter's transfer test. If you can say it to a
dean — *what Medhavy does that Canvas cannot is present differently
based on each student's learning signals, measure whether the
difference helped, and update its approach, like a tutor with perfect
memory and infinite patience running experiments per student per
concept* — you have the chapter. The rest of this is justification,
worked example, and honest limits.

The loop has four steps and they have to all be present for the loop
to close:

1. **Present differently.** Not just a different explanation of the
   same concept, but a different *pedagogical approach* drawn from an
   evidence-based library. Socratic versus didactic. Problem-first
   versus concept-first. Spaced versus massed. Retrieval practice
   versus generative assignment. Each is a different cognitive
   operation. The four modes from Act One are the units of variation.

2. **Measure whether it helped.** Not engagement metrics. The seven
   signals from Chapter 8. The behavioral traces that distinguish
   genuine learning from borrowed certainty.

3. **Adapt.** The contextual bandit updates its policy for this
   student-concept pair. Interventions that produced learning
   signal get more weight. Interventions that did not get less.

4. **Repeat.** The loop runs continuously across the term, the
   concept map, and the student population.

Canvas can do step one in a limited way (different assignments to
different students) and step three not at all (no algorithm reads the
signals and updates policy). Anki can do step two for retrieval-
strength decay and nothing else. A general-purpose chatbot can do
neither. The loop requires measurement and adaptation in the same
system, and the measurement has to be the seven-signal kind, not the
engagement kind. That is the architecture-level reason a bolt-on tool
cannot do what Medhavy does.

---

## What "present differently" actually means

The most common misreading of *adaptive learning* is that the system
gives different students different *explanations of the same concept*
— a wordier version for the struggling student, a tighter version for
the strong one. Medhavy is not doing that.

Medhavy's interventions are drawn from a library of pedagogical
approaches with established evidence bases. John Hattie's *Visible
Learning* (2009, revised 2023) is the most-cited synthesis of what
teaching moves work, ranked by effect size on student outcomes
(Hattie, *Visible Learning*, Routledge). John Dunlosky and colleagues
in 2013 published a careful evidence-grounded ranking of study
techniques in *Psychological Science in the Public Interest*: spaced
practice and retrieval practice came out on top; rereading and
highlighting came out near the bottom (Dunlosky, Rawson, Marsh, Nathan,
and Willingham, *Psychological Science in the Public Interest*, 14(1),
2013). The US Department of Education's Institute of Education
Sciences practice guide (Pashler et al., 2008) gives the parallel
synthesis aimed at practitioners.

The bandit chooses among interventions from this library. Not among
arbitrary content; not among LLM-generated variations on the same
explanation. Among interventions with named pedagogical logic and
established evidence. A struggling student on a concept might get
more Quiz Me (spaced retrieval, top-ranked technique in Dunlosky) and
less Ask AI; a stronger student on the same concept might unlock
Case Study earlier and spend more time in Glimmer. The within-mode
variation is also evidence-bounded: Socratic versus didactic Ask AI
variants; massed versus spaced Quiz Me schedules; case difficulty
levels.

This framing matters because the most common reasonable objection
to adaptive systems is *I do not want an algorithm deciding what my
students see*. The honest answer: the algorithm chooses among
interventions that you, the institution, have decided are in the
evidence library. The bandit's choice is *from this menu, in what
proportion, for this student-concept pair, given the signal
evidence*. The bandit is not authoring pedagogy. It is selecting from
faculty-approved pedagogy with measurement-driven weighting.

The four modes are the stable arms. The within-mode content varies
within faculty-reviewed bounds. For Case Study, the bounds are
explicit and tight — every scenario is faculty-reviewed before
deployment — because plausible-confident-wrong in clinical content is
a safety problem. For Quiz Me, the bounds are looser, because
retrieval items are lower-stakes content. This is a design choice
with a clear safety logic.

---

## The contextual bandit in plain language

The slot-machine analogy is older than most learning technology. It
comes from Richard Sutton and Andrew Barto's textbook *Reinforcement
Learning: An Introduction* (1998, second edition 2018), which is the
field's standard reference. The image is this: you are in a casino
with a row of slot machines. Each machine has an unknown payout rate.
You have a finite number of pulls. The question is how to allocate
your pulls between *exploration* (trying machines you do not yet have
data on) and *exploitation* (playing the machine that has paid out
best so far).

The math of this problem starts with Herbert Robbins, a Columbia
statistician, who in 1952 published a short paper in the *Bulletin of
the American Mathematical Society* titled *Some Aspects of the
Sequential Design of Experiments* (Robbins, 1952). Robbins framed the
multi-armed bandit as a sequential decision problem under uncertainty.
The framework sat largely in statistics for forty years and then
became one of the most-deployed algorithmic ideas in technology, used
in the news article you read this morning (Yahoo News personalized
articles with LinUCB, Li, Chu, Langford, and Schapire, *WWW*, 2010),
the show your streaming service recommended last night (Netflix), the
ad you saw on a search results page (Microsoft, Google), and now,
increasingly, the next learning intervention you choose for your
students (Lan and Baraniuk, *Educational Data Mining*, 2016; Clement,
Roy, Oudeyer, and Lopes, *Journal of Educational Data Mining*, 7(2),
2015; Liu and Koedinger, *Journal of Educational Data Mining*, 9(1),
2017).

[**MARGIN — AI Wayback Machine.** Imagine asking Herbert Robbins,
Columbia, 1952: explain to a curriculum director, in language she can
use with her dean, what a multi-armed bandit is and why it is the
right way to think about choosing teaching interventions one student
at a time. Robbins would likely say: think about it as a decision
problem with two competing pressures. You want to give the student
what you know works best for students like her, based on what you
have observed so far. You also want to learn whether something else
might work better than what you currently believe. If you only do
the first thing, you never discover better options. If you only do
the second, you waste pulls on options that probably will not work.
The math of bandits tells you how to balance the two so that, over
time, you converge on the right answer per student per concept while
spending as few pulls as possible on bad options. That is what your
faculty have been doing on intuition for decades. The bandit makes
it systematic and traceable.]

For a learning system, the translation is direct. The *machines* are
interventions — modes, within-mode variants, intervention difficulty
levels. The *payouts* are the seven signals from Chapter 8,
aggregated into the GLP score and ultimately into the reward signal
the bandit optimizes. The *player* is the algorithm. The *pulls* are
the sessions the student spends with the system. The *unknown payout
rate* is the per-student per-concept truth: which interventions
actually produce learning signal for this specific student on this
specific concept.

The *contextual* part of *contextual bandit* is what makes the
mechanism appropriate for learning rather than for slot machines in
a casino. In a plain bandit, the payouts depend only on which machine
you pulled. In a contextual bandit, the payouts depend on the machine
*and the context* — for Medhavy, the context is the student's prior
signals, the concept's prerequisites, the moment in the term. LinUCB
(Auer, Cesa-Bianchi, and Fischer, 2002; extended by Li et al. 2010) is
the workhorse algorithm. Thompson sampling (Thompson, 1933, revived
in deployment in the 2010s) is the principal Bayesian alternative.
The specific algorithm Medhavy uses is an engineering choice. The
class of algorithm is settled and the math has rigorous guarantees.

A curriculum director does not need to know which variant Medhavy
uses. A curriculum director does need to know that the algorithm
class is settled, that the deployments-at-scale exist for fifteen
years across multiple industries, and that the educational-deployment
literature (Liu and Koedinger, Lan and Baraniuk, Clement and
colleagues, J. J. Williams and colleagues' *AXIS* system, *Learning @
Scale* 2016) shows the bandit producing learning gains in pilots.
Whether those gains are *durable* learning gains — not just immediate-
performance gains — is the open empirical question, and Medhavy's bet
hinges on the choice of the reward signal.

---

## What makes Medhavy's loop different

Most deployed adaptive learning systems use *immediate accuracy* as
the reward signal. The student answered correctly; the system counts
that as a win; the policy updates toward whatever intervention
produced the correct answer.

This is the Bastani failure mode in plain view. If the reward signal
is immediate performance, an AI tutor that produces fluent immediate
performance — by giving the answer — looks like a successful
intervention. The policy updates toward intervention types that produce
immediate performance. The students get more of those interventions.
The downstream learning collapses. The dashboard says it worked.

Medhavy's reward signal, per TIKTOC's framing, is *delayed retrieval
accuracy at seven days*, computed via Quiz Me's scheduled retrieval
checks. [Humanitarians AI internal framework — the precise
operationalization of the reward signal is proprietary, but the
architectural commitment to delayed-outcome reward rather than
immediate-performance reward is the documented design choice.] The
seven-day delay is what makes the loop optimize for the Bjork-side of
the performance/learning distinction rather than the immediate-
performance side. It is also what makes the loop slower than it would
be if the reward were immediate. Both consequences are intentional.

This is the architectural difference between Medhavy's loop and the
adaptive learning systems that have been on the market for ten years.
The bandit is, by 2026 standards, a well-understood algorithm class.
The choice of *what to optimize* — what counts as a payout — is the
load-bearing decision. Engagement as payout produces engagement
optimization. Immediate accuracy as payout produces immediate-accuracy
optimization, which Bastani 2025 shows can be inversely correlated
with durable learning. Delayed retrieval as payout produces — the bet
is — durable-learning optimization.

This bet has theoretical support and limited empirical validation at
the scale Medhavy proposes to operate. Most published bandit-in-
education studies report on immediate metrics; few have measured
delayed retention. The book's honest framing: the bet is principled,
the components are evidence-based, the integration at this scale is
forthcoming evidence rather than completed evidence. You are an early
adopter if you adopt now. That is not a flaw of the system. It is the
honest state of the field in 2026.

---

## Worked example — one concept, one student, eight weeks

The TIKTOC chapter spec calls for a single eight-week trace of the
bandit's policy evolution for one concept and one student. Here it
is. The student is in a pharmacology course; the concept is
*beta-blockade clinical decision-making* — the same concept used as
the worked example in Chapters 5 and 6.

| Week | What the bandit has seen so far                              | What the bandit tried this week     | Signals captured                                      | Policy update                                        |
|------|---------------------------------------------------------------|-------------------------------------|-------------------------------------------------------|------------------------------------------------------|
| 1    | New student. No data. Uniform priors over modes.              | Ask AI (default for acquisition)    | Y1 strong, Y4 weak — student fluent but unconfident   | Note Y4 weakness; try Quiz Me next                   |
| 2    | Y4 still weak after Ask AI alone                              | Quiz Me (basic mechanism items)     | Y2 coherent, Y6 building from zero                    | Continue Quiz Me; retrieval strength is the gap      |
| 3    | Y6 strong on factual recall; Y3 not yet observable            | Quiz Me + Ask AI mix                | Y6 high; still no transfer evidence                   | Prerequisite gate met; unlock Case Study             |
| 4    | First Case Study scenario presented                            | Case Study (initial difficulty)     | Y3 emerging; Y7 strong response to graduated hints    | Case Study weighted up                               |
| 5    | Two more Case Studies completed; Quiz Me maintenance ongoing  | Case Study + maintenance Quiz Me    | Y3 high, Y6 high, Y4 improving                        | Pattern stabilizing; Case Study primary              |
| 6    | Stable signal profile across signals                           | Case Study primary; Ask AI fallback | All seven signals trending up                         | Policy converging                                     |
| 7    | Glimmer eligibility threshold met                              | First Glimmer attempt              | Y5 specific confusions visible in defense; Y3 high    | Glimmer added to weekly mix                          |
| 8    | Steady-state policy                                            | 40% Case Study, 35% Quiz Me, 20% Glimmer, 5% Ask AI | All seven signals positive; GLP score high      | Stable policy; faculty review the GLP profile        |

A few things to notice.

The first three weeks look more like exploration than personalization.
The bandit has no data on this student-concept pair. It defaults to
the modes appropriate for early acquisition (Ask AI), notices the
calibration weakness, tries the appropriate remediation (Quiz Me),
and waits for the retrieval signal to consolidate before unlocking
the higher-cognitive-load modes. Most published bandit-in-education
work calls these the *cold start* sessions. The first six sessions
for any new student-concept pair are largely exploratory by necessity.
The cold-start problem in recommendation systems is foundational
(Schein, Popescul, Ungar, and Pennock, *SIGIR*, 2002); the educational
form of it is the same problem in different clothing. During the
cold-start window, the institution should expect bandit choices to
look unconfident. They are unconfident. The mitigation is not
algorithmic; it is faculty awareness and override capability for early
students who appear to be at risk of mismatch.

The fourth-through-eighth weeks look more like the loop closing. The
bandit has enough signal to choose more confidently. The student's
policy diverges from the population average. A different student on
the same concept might end the eight weeks with a different policy:
heavy on Quiz Me if the retention problem is the bottleneck; heavy
on Glimmer if the student is unusually advanced; mostly Ask AI if
the student keeps stalling on prerequisite material. The per-student
per-concept granularity is the point. The bandit is doing what a
skilled human tutor would do with infinite patience and perfect
memory across every student in the program.

The same eight weeks, viewed through Canvas, would look like a flat
engagement profile. Time on page, click counts, module completions —
the student would look the same as the student next to her in week
one and the same as a student in a different policy in week eight.
The bandit was running eight weeks of measurement and adaptation;
Canvas's view never changed. This is the contrast that has the most
purchase with a budget committee: a bolt-on dashboard tool cannot
produce the diverging-policy picture, because it has no policy to
diverge.

---

## What Canvas cannot do that Medhavy can

This is the chapter's transfer-to-the-budget-meeting point and worth
saying as cleanly as possible.

- **Canvas administers; Medhavy experiments.** Canvas records what
  happened. Medhavy varies what happens, observes the variation's
  effect on the seven signals, and adjusts the next variation. The
  loop's closure requires measurement and policy in the same system.

- **Canvas's metrics measure engagement; Medhavy's signals measure
  cognitive process traces.** Chapter 7's argument. Engagement metrics
  cannot be the bandit's reward signal because they are decoupled
  from durable learning.

- **Canvas treats students as uniform; Medhavy's policy is per-student
  per-concept.** The same module presented to thirty students gets
  the same response in Canvas. The bandit's policy can be a
  different mix of modes for each student on each concept, updated
  weekly.

- **Canvas does not run experiments; Medhavy does.** The continuous-
  experimentation framing — every intervention is a controlled
  attempt at producing learning signal; the result updates the
  policy — is what makes Medhavy a *measurement and adaptation
  layer* rather than a smarter version of Canvas.

A bolt-on adaptive-learning add-on to Canvas can do some of this
poorly. The architectural commitment to measurement-first, evidence-
bounded, delayed-reward adaptation is what Medhavy is selling. The
add-on is selling adaptation against immediate-performance reward,
which is the Bastani failure mode at architecture scale.

---

## Honest limits

Five limits worth naming on the page.

**Cold start is real.** The first six sessions for a new student-
concept pair are exploratory by necessity. Performance during this
window is below steady-state. Faculty override during this window is
not a feature — it is a requirement. If your institution cannot
support faculty review of early-student bandit choices, you should
not adopt yet.

**The reward signal is a bet.** Delayed retrieval at seven days is the
right signal for the Bjork-side learning the chapter argues for. It
is also a bet that the seven-day window captures durable learning
better than the alternatives. Empirical validation at the deployment
scale Medhavy proposes is forthcoming, not completed. The reader is
buying the architectural principle on theoretical grounds.

**The bandit's policy is auditable but not deterministically
explainable.** A faculty member can read the dashboard and see what
the bandit chose, but the *why* of any particular choice — why this
student got Case Study this week instead of Quiz Me — is the kind of
counterfactual explanation that bandit policy outputs do not natively
produce. Counterfactual explanations for bandit decisions are an
active research area in 2026 and not yet a deployed feature. This
matters for transparency to students and to faculty.

**Equity-of-adaptation is a genuine open question.** A bandit that
adapts to a student's early signature can entrench disadvantage if
the early signals are noisy — particularly for students whose
engagement patterns differ from the population the priors were trained
on. The literature on fairness in adaptive learning is young and the
concerns are real. Medhavy's mitigation strategies (population-level
priors, conservative exploration, faculty override) are reasonable
but not proven. An institution adopting Medhavy is adopting this risk
explicitly.

**The institution has to be willing to act.** This is TIKTOC's third
adoption condition and the load-bearing one for Chapter 10. A bandit
that produces a clear policy signal — *this student is benefiting
from Case Study; this student needs more Quiz Me first* — is
worthless if the institution cannot or will not let the policy run.
Medhavy without the willingness to act on what the loop reveals is
expensive Canvas analytics. The reader needs to be honest with
themselves about this *before* the adoption decision. Chapter 10 is
the test.

---

## Common misconceptions

**"This is the same as adaptive learning systems we have seen for ten
years."** The class of algorithm is the same; the choice of reward
signal is different, and the reward signal is what determines what the
system optimizes for. Most existing adaptive systems optimize for
immediate accuracy. Medhavy optimizes for delayed retrieval signal.
The Bastani finding shows why this distinction matters.

**"The bandit is the AI part."** No. The bandit is a classical
algorithm — Robbins, 1952, with theoretical extensions in the 1990s
and 2000s. The AI part is in the modes (Ask AI uses an LLM as
Socratic tutor; the Case Study facilitator is LLM-driven within
faculty-reviewed scenarios). The loop's intelligence is the bandit
plus the seven-signal measurement layer. The AI is one ingredient,
not the architecture.

**"This is just A/B testing my students."** A/B testing splits the
population in two and compares averages. The bandit operates per
student per concept and converges on a policy specific to each pair.
It is more like *N-of-1 experiments* run continuously across the
student population, sharing priors where structure is shared and
diverging where it is not. It also has rigorous mathematical
guarantees on regret (the gap between the bandit's choices and the
optimal-policy choices) that A/B testing does not natively have.

**"My faculty already do this informally."** Yes — and TIKTOC's
chapter brief is honest that this is one of the modes the bandit
mimics. Skilled faculty adapt their teaching per student, in real
time, based on the seven signals they observe (without using those
terms). The bandit does the same thing across more students than any
faculty can hold in working memory, with traceable policy outputs,
on signal evidence rather than recollection. For a thirty-student
seminar with one skilled instructor, the bandit may add little. For
a three-hundred-student multi-section program, the bandit produces
information no instructor team can produce.

**"The bandit will replace my faculty."** It will not. The faculty
review the GLP dashboard, override bandit choices when warranted,
author Case Study scenarios, grade Glimmer outputs, and remain the
meta-model. The bandit is an instrument that surfaces signal the
faculty currently cannot see. The faculty member at the dashboard is
doing the judgment work; the bandit is doing the data work.

---

## What would change my mind

If a published, replicated study showed that a contextual bandit
optimizing for *immediate accuracy* — the standard adaptive learning
configuration — produced equivalent or better delayed-retention
outcomes than a bandit optimizing for *delayed retrieval* signal, the
chapter's central architectural claim would be undermined. The
mathematical guarantees on the bandit would remain. The choice of
reward signal would lose its load-bearing role in the argument. The
chapter would have to argue for Medhavy on grounds other than the
reward-signal architecture — and those grounds (the four modes; the
seven-signal measurement layer) would still be there, but the loop
would no longer be the chapter's central distinguishing feature
relative to existing adaptive systems.

---

## Still puzzling

- The seven-day delay for the reward signal is the chapter's stated
  choice. Why seven and not three or fourteen? The Bjork research on
  spacing intervals gives ranges but not a single optimal. Medhavy's
  choice is reasonable; *optimal* is unknown.

- The intervention library is the menu the bandit chooses from. The
  exact set of within-mode variants — Socratic versus didactic Ask
  AI; case difficulty levels; Glimmer prompt classes — is proprietary
  and unspecified in this book. How wide is the menu, and how does
  its width affect the bandit's effectiveness?

- Counterfactual interpretability — *why did this student get Case
  Study this week* — is a real gap. The bandit's policy is auditable
  through its choices but not natively explainable through them. How
  much does this matter for student trust and faculty acceptance?

- Cohort-level learning by the bandit (the bandit's priors improve
  as more students complete the system) is the meta-loop. How does
  this interact with the cold-start problem for individual new
  students? In a stable institution running Medhavy for three years,
  the cold-start should shrink. The empirical curve is unknown.

---

## Bridge

You now have the full picture: four modes, seven signals, one loop.
Acquire, retain, apply, generate. Time, error, transfer, calibration,
texture, decay, scaffolding. Present differently, measure whether it
helped, adapt. The architecture is on the page. The question is no
longer *what is Medhavy*. The question is *does my deployment need
it*. Chapter 10 is the discipline that says: not always, and here is
how to know.

---

## Exercises

1. **(Analyze — application to your deployment)** In your current
   deployment, who performs the *adapt* function? Be specific. Is it
   an instructor who adjusts mid-term based on exam scores? A
   curriculum committee that revises the next year's syllabus? No
   one? Write the honest answer in one sentence. Then write what
   information that person uses to make the adaptation, and what
   information they currently do not have but would value. The
   gap between current-information and desired-information is one
   of the inputs to your adoption decision.

2. **(Apply — application to your deployment)** For one high-stakes
   concept in your curriculum — the same concept you named in
   Chapter 8's Exercise 2 — describe what the loop would need to
   measure to determine whether students are *genuinely* learning
   the concept versus producing performance that decouples from
   learning. Name the two or three of the seven signals that would
   be most relevant. Name what *adapt* would mean concretely for
   this concept: what intervention shifts would the bandit have
   available, and which ones would your faculty be willing to let
   it choose?

3. **(Evaluate — application to your deployment)** The bandit
   requires a reward signal. In Medhavy, the reward signal is
   delayed retrieval accuracy at seven days. In your current
   deployment, what is the equivalent? When you currently evaluate
   whether a course is *working*, what measurement are you actually
   looking at, on what time delay? Is that measurement available
   without Medhavy? If not, what would it cost — in faculty time,
   in student time, in instrument design — to produce it without
   adopting Medhavy?
