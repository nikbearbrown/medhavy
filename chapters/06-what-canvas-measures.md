# Chapter 6 — What Canvas Measures and What It Misses

**One-line capability:** The reader learns the specific gap between
engagement analytics and learning evidence — and why that gap is the
adoption decision's hinge.

---

## The dashboard says it worked

Open the Canvas analytics for any course you have run in the last five
years. You will see numbers. Time on page. Click count. Module
completion percentage. Quiz score. Submission rate. The numbers are
accurate. They are visualized cleanly. They tell you, with what looks
like precision, who is engaged and how much.

You have made decisions on these numbers. So have your faculty. So has
every dean who has ever sat through an instructional-technology budget
meeting. You were not wrong to use them. The numbers are what the tool
was designed to give you, and the tool was designed well.

This chapter is not an argument against Canvas. Canvas was built to
administer courses. It administers them well — assignments collected,
grades computed, deadlines tracked, completion logged. The argument is
that *administration metrics* and *learning evidence* are different
categories of measurement, and the gap between them has widened in the
last three years to the point where it is now a decision-relevant
problem for any program adopting AI tools.

It is also the hardest argument to make to a curriculum director who
has used these numbers competently for a decade. So let me name the
move clearly, on the page, before making it: I am not going to tell
you the metrics you have been using are wrong. I am going to tell you
they answer a different question than the one you now need to ask.

---

## What Canvas actually measures

Canvas's standard analytics, distilled to their five most-used
metrics:

- **Time on page.** How long a student's session was active on a given
  resource. Useful for: detecting non-engagement (the student never
  opened the module). Misses: whether the time was spent thinking, or
  whether the tab was open in the background while the student watched
  a video on another screen.

- **Click count.** Number of interactions per session. Useful for:
  catching students who never engage with interactive elements.
  Misses: whether clicks reflected thought or reflexive scrolling.

- **Module completion rate.** Percentage of required elements marked
  done. Useful for: tracking workflow progress. Misses: whether the
  student understood what they completed; whether they could do it
  again unaided.

- **Quiz score.** Percentage correct on a Canvas quiz. Useful for:
  immediate performance check. Misses: whether the performance came
  from study, from looking at the textbook, from another open browser
  tab, or from a tool the student used between question and answer.

- **Submission rate.** Whether assignments are turned in on time.
  Useful for: workflow management. Misses: who wrote the submission.

Each metric is accurate for what it captures. Each metric misses
something you currently need to know. The miss is not Canvas's fault.
The miss is what happens when you use an administration tool to answer
a learning question.

A long-running tradition in education research has made this point.
Neil Selwyn, in 2015, wrote about *learning analytics* as a sociological
phenomenon: what gets measured in education is what is easy to count,
and what is easy to count drives what gets treated as evidence (Selwyn,
*Learning, Media and Technology*, 40(1), 2015). Ben Williamson's *Big
Data in Education* (2017) is the book-length version. Verbert and
colleagues, in the human–computer interaction literature, surveyed
learning-analytics dashboards in 2014 and found that most of them
visualize engagement; very few have validated outcome links (Verbert
et al., *Personal and Ubiquitous Computing*, 18(6), 2014). The picture
across that literature is consistent: engagement analytics are
accurate measurements of engagement and they are weak predictors of
learning. Both of those things have been true for at least a decade.
What changed recently is the consequences of the gap.

---

## The performance-learning paradox

The cognitive psychology research has a name for the gap and a
mechanism for it. The name is the performance/learning distinction. The
mechanism is something Robert Bjork has been arguing for thirty years.

The argument is counterintuitive enough that it bears stating slowly.
Conditions that produce better *immediate performance* often produce
*worse durable learning*. Conditions that produce worse immediate
performance often produce better durable learning. Bjork called these
second conditions *desirable difficulties* — spacing, interleaving,
generation, varied conditions of practice — slow on the way in, sticky
on the way out (Bjork, 1994, *Memory and Metamemory Considerations in
the Training of Human Beings*, in Metcalfe and Shimamura, *Metacognition*;
Bjork and Bjork, *Psychology and the Real World*, 2011).

The most accessible contemporary restatement is Soderstrom and Bjork's
2015 review in *Perspectives on Psychological Science*, which collected
twenty years of evidence that immediate performance is an unreliable
proxy for durable learning. Karpicke and Roediger's 2008 finding in
*Science* is the cleanest single experiment: students who tested
themselves once outperformed students who restudied four times — at a
one-week delay. After the study session, the restudy group looked
ahead. A week later, the testing group held its knowledge and the
restudy group had lost most of it (Karpicke and Roediger, *Science*,
319, 2008). The performance after the session was inverse to the
durable learning.

There is more. Students' own judgments of learning are systematically
miscalibrated. They believe they have learned material they have not.
They prefer instructional conditions that produce less durable
learning. This last finding is decades old in cognitive psychology and
relevant here: the student's self-report of engagement and learning is
not a reliable signal either. The faculty member's intuition that an
engaged-looking class is a learning class is also not reliable. No one
in the room has the unaided ability to distinguish a student who is
learning from a student who is performing.

[**MARGIN — AI Wayback Machine.** Imagine asking Elizabeth Bjork at
UCLA — co-architect of the desirable-difficulties framework, less cited
than her husband Robert but every bit as foundational on the
performance/learning question: a curriculum director says her Canvas
dashboard shows her students are engaged and scoring well; what is she
missing? Elizabeth Bjork would likely say: she is missing the delay.
The dashboard tells her what students can do right now, with the
materials they used to study, in the conditions where they have just
practiced. The thing she needs to know is what they can do three months
from now, in a new context, with no resources to hand. That measurement
is not on the dashboard. It is not because the dashboard is bad. It is
because the measurement she needs is harder to take and the easy
measurements crowded it out.]

The Bjork distinction is uncontroversial in cognitive psychology. It
has been uncontroversial since the 1990s. What is new is not the
distinction. What is new is that an AI tool now sits between the
student and the assignment, and the AI tool will make the immediate
performance look excellent regardless of what the durable learning is.
The gap between performance and learning, which was always there, is
now industrially produced.

This is the Bastani finding.

---

## The Bastani finding

In 2024 and 2025, Hamsa Bastani and colleagues at Wharton ran a
randomized controlled trial in Turkish high schools. Roughly a thousand
students learning math were randomized into three groups: no AI access,
access to an unguarded GPT-4, and access to a GPT-4 wrapped in a
custom *GPT Tutor* interface designed to behave like a Socratic tutor
(Bastani et al., *Generative AI Can Harm Learning*, PNAS, 2025; see
also working paper 2024). The students were measured on practice
problems while they had AI access and again on a final exam without
AI access.

The findings, stated plainly:

- During practice, the unguarded GPT-4 group scored about forty-eight
  percent higher than the no-AI control. The dashboard, if there had
  been one, would have said the AI was working.

- On the final exam without AI, the unguarded GPT-4 group scored
  seventeen percentage points *below* the no-AI control. Same students.
  Same content. The group that had access to the unguarded AI was
  worse off than the group that had no AI at all.

- The GPT Tutor wrapper, which gave the same model but constrained it
  to behave like a tutor rather than an answer-giver, recovered most
  of the gap. The unassisted-exam scores for the wrapped-AI group were
  closer to the no-AI control than to the unguarded group.

- Throughout the practice phase, engagement metrics — time on task,
  problems attempted, completion rates — were essentially
  indistinguishable across the three groups.

[Bastani et al. 2025 PNAS; note the published correction at
10.1073/pnas.2518204122 for the 17-percentage-point figure — verify
exact phrasing of the correction before citing in the final published
version of this book.]

Pause on that last bullet. The engagement dashboard could not
distinguish a group that *gained* almost half a standard deviation
from a group that *lost* a comparable amount. The dashboard was
working as designed. It was not designed to see what the exam saw.

This is the load-bearing piece of evidence in the chapter. One
randomized trial, in one country, in one subject, with one specific
AI wrapper. The book takes Bastani as the strongest currently available
evidence for the claim, with explicit acknowledgment that replication
is pending. The cognitive-psychology backbone — the Bjork distinction,
the Karpicke and Roediger demonstration, the metacognition literature
on borrowed certainty — supports the finding mechanistically. Bastani
is the empirical anchor. The mechanism is older.

The chapter's claim is not that AI is harmful. The chapter's claim is
this: the same AI, with two different wrappers, produced opposite
learning outcomes, and the wrapper was the variable. Wrappers can
fail closed (the student gets help that produces learning) or fail
open (the student gets help that produces a transient performance gain
and durable un-learning). Canvas, by itself, cannot tell you which
wrapper your students are using or which outcome they are getting. The
measurement gap is the architecture problem.

---

## The decoupling problem

Before 2023, a well-written assignment was reasonable evidence that
the student could write it. After 2023, it is not. This is the
decoupling problem.

Ethan Mollick has written about this more clearly than anyone in the
faculty-facing literature. His 2024 book *Co-Intelligence* is the
trustworthy summary for a non-research reader. The argument is
straightforward: when a graduate-level essay can be produced in three
minutes by a model the student already has access to, the artifact —
the essay itself — is no longer reliable evidence of the student's
capability. The link between *student wrote essay* and *student can
write essay* has been broken at the population level (Mollick,
*Co-Intelligence: Living and Working with AI*, 2024).

You know this. Every faculty member teaching since 2023 has had the
experience of reading a beautifully written submission from a student
who cannot discuss the material orally. The discussion is the symptom.
The decoupling is the mechanism. The artifact stopped carrying
evidence of the process that produced it.

For Canvas's gradebook, this is a category problem. The gradebook
records artifact quality. Artifact quality used to be a strong
correlate of learning. It is now a weaker correlate. The score on
the assignment looks the same. What the score *means* has changed.

This is not a Canvas critique. Canvas faithfully records what was
submitted. The question is what the submission tells you. If it
tells you less than it used to about what the student can do, then
the gradebook tells you less than it used to about what your program
is producing. The question is not whether Canvas is broken. The
question is whether you can run a high-stakes professional program
on a measurement stack whose central artifact has been industrially
decoupled from its underlying signal.

---

## Worked example — two students, same dashboard

Two students take the same Canvas module on beta-blockade in
pharmacology. Same content. Same assignment. Same time window. Here
is what Canvas sees:

| Canvas metric                       | Student A | Student B |
|-------------------------------------|-----------|-----------|
| Time on module                      | 47 min    | 47 min    |
| Click count                         | 142       | 138       |
| Module completion                   | 100%      | 100%      |
| Module quiz score                   | 88%       | 88%       |
| Submitted assignment quality        | High      | High      |
| Six-weeks-later retention quiz      | 82%       | 31%       |
| What Canvas saw at time of module   | Indistinguishable | Indistinguishable |

Student A worked through the module, used the AI as a hints-only
tutor, was forced to retrieve and articulate, struggled productively
on the harder material, and left with a durable understanding.
Student B opened the module in one tab and an unguarded chatbot in
another, used the chatbot to write the assignment, scored the same on
the quiz because the questions were findable from the chatbot, and
left without having engaged the material at the level the module
asked for.

Six weeks later, in a clinical-reasoning scenario without resources to
hand, the two students performed differently. The Canvas record from
six weeks earlier said the same thing about both of them. Canvas was
not lying. It was reporting engagement, faithfully, and the engagement
was the same. The thing that differed — the underlying cognitive
process — was not in Canvas's measurement vocabulary.

This is the gap. What you need is not better engagement analytics.
Better click counts and more refined time-on-page numbers would not
distinguish these two students. What you need is a different category
of measurement: behavioral traces of the cognitive engagement itself,
not the engagement's surface signature. Whether the student's response
times scaled with problem difficulty in ways consistent with
processing. Whether their errors followed coherent patterns that
update with feedback. Whether they could recall the material at
delay, in a new context, after a partial hint.

Those are different measurements. Chapter 7 names them. The
Frictional Framework — Medhavy's term for the seven behavioral signals
that distinguish genuine learning from borrowed certainty — is the
chapter that follows this one. [Humanitarians AI internal framework;
named here, detailed next chapter; no outside-of-Medhavy primary
source uses *Frictional Framework* or *GLP score* in this exact
form.]

---

## Common misconceptions

**"Canvas is bad."** Canvas is good at what it was built for —
administering courses. The argument is not that Canvas should be
replaced. It is that the gradebook plus engagement analytics, used as
a learning-evidence stack, gives you a different answer than the one
you need when the question is *did the student learn this*. For
courses where artifact quality and module completion are sufficient
evidence, Canvas is fine. For programs where they are not, the gap
matters.

**"Better Canvas analytics will close the gap."** Maybe partially. The
sociological literature on learning analytics suggests engagement
metrics, however refined, are answering a different question than
learning metrics. Better click counts and more sophisticated time-on-
page measurements may improve at the margins. They do not address
the categorical gap. The Bastani finding's engagement profiles were
identical across groups with opposite learning outcomes. The gap is
not a resolution problem.

**"This is an anti-AI argument."** It is not. The Bastani study's
own finding is that the same AI, with a measurement-aware wrapper,
produced learning. The AI is not the variable. The architecture
around the AI — what the system commits the AI to doing, and what the
system measures about the result — is the variable. The decision is
not *should I add AI to my Canvas deployment*. The decision is *if I
am adding AI, what architectural commitments does the tool make about
the measurement gap*.

**"My faculty can tell which students are learning."** Some faculty
can, some of the time, for some students. The cognitive psychology
literature on judgments of learning is settled: no one — including
the students themselves — can reliably distinguish learning from
performance without a delayed, unaided measurement. Your faculty's
intuitions are accurate where they have rich direct contact with
students. In larger sections, in asynchronous courses, in programs
where students rotate through many instructors, those intuitions are
operating on thinner data than the faculty realize.

**"Grades capture learning."** Grades capture artifact quality and
performance during assessment. Artifact quality is decoupled. Assessment
performance is the immediate-measurement side of the Bjork
distinction. Grades are signals; they have value; they no longer carry
the durable-learning signal they used to carry, and they were never
the primary carrier of it.

---

## What would change my mind

If Bastani 2025 fails to replicate — if a comparable RCT in a
different subject and country, with comparable methodology, shows that
engagement metrics under AI access do track learning outcomes — the
chapter's central empirical claim weakens substantially. The
cognitive-psychology backbone (the Bjork distinction) would remain.
The case for measurement-aware AI architecture would remain. But the
sharpest demonstration of the gap — same engagement, opposite learning
— would no longer be in evidence, and the chapter would need to lean
harder on the older Bjork and Karpicke evidence, which is less vivid
to a non-research reader. The Bastani finding does most of the
rhetorical work; if it falls, the chapter is harder to write.

---

## Still puzzling

- Canvas and competing LMS vendors have announced AI-augmented
  analytics features for 2024–2026 release. Will these features
  measure learning, or will they measure engagement with AI-augmented
  precision? The architectural question — engagement-first or
  learning-first — is the determining variable, and it is not yet
  clear which choice the major vendors are making.

- The decoupling problem's magnitude is empirically disputed. Some
  studies estimate that more than thirty percent of college-writing
  assignments now show LLM signatures; others estimate lower. The
  qualitative point is settled; the precise size is not. How much
  does the size matter for the institutional decision?

- The student's own judgment-of-learning miscalibration is
  well-documented in laboratory settings. How much it generalizes to
  the AI-augmented study environment — where the *borrowed certainty*
  source is more fluent and more confident than any prior study aid —
  is not yet directly measured. Plausibly worse than the lab estimates.
  Plausibly not.

- The aggressive version of this chapter's claim is that any
  performance-based assessment, in an environment where AI is
  available, no longer reliably measures learning. That version is
  not yet established. The conservative version — that the gap has
  widened enough to justify a different measurement category for
  high-stakes programs — is what the evidence currently supports.

---

## Bridge

If engagement evidence is not learning evidence, what does learning
evidence look like? It looks like behavioral traces of cognitive
engagement — patterns in how time was distributed, whether errors
formed coherent and updating sequences, whether knowledge held at
delay and in a new context, whether a partial hint unlocked a
partial understanding. These are not new ideas in cognitive
psychology. They have been documented, separately, for decades. What
Medhavy did was name a specific set of seven such signals and build
a measurement layer around them. Chapter 7 introduces the seven
signals in plain language, one at a time, and shows which mode
produces which signal.

---

## Exercises

1. **(Analyze)** Open the Canvas analytics for one of your current
   courses. List every metric the dashboard shows you. For each metric,
   write one sentence on what it measures, and one sentence on what
   genuine learning it cannot detect. Star the metrics you have used
   to make decisions in the last year.

2. **(Analyze — application to your deployment)** Imagine you have ten
   minutes with a skeptical senior faculty member who trusts the
   Canvas gradebook and does not see the gap. What single piece of
   evidence — the Bastani finding is the chapter's suggestion — would
   you walk them through? Write the two-minute explanation. The
   explanation cannot use the phrase *desirable difficulties* or
   *performance/learning distinction*. It has to land without jargon.

3. **(Evaluate — application to your deployment)** Identify the
   single highest-stakes assessment in your curriculum. It might be a
   board prep exam, a capstone, a clinical-readiness check. Ask: is
   that assessment currently scored on artifact quality, on engagement
   data, or on learning evidence? Write the honest answer in one
   sentence. Then write what would have to change about the
   assessment if you switched the scoring basis to learning evidence,
   and what your faculty would have to give up to make the switch.
