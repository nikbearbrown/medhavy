# Chapter 0 — Introduction

*Four characters. One logged success. One student who learned nothing.*

---

A student types `idk idk` into an AI tutoring system, presses return, and the platform logs her as engaged.

She is not engaged. She is not learning. She has found the easiest path through a system that mistakes motion for progress, and the system — the most expensively deployed AI education product in human history — rewarded her for it.

That is the moment this book starts. Not with a theory. With a failure. A real one, at a real scale, noticed publicly by the people who built and paid for the product. Kristen DiCerbo, Khan Academy's Chief Learning Officer, said it plainly: the Khanmigo deployment was producing more *I don't know, I don't know* and more passive engagement than they wanted. The IDK-IDK pattern. The metric says success. The learning says otherwise.

![Screenshot or reconstruction of a Khanmigo session log](images/00-introduction-fig-01.png)
*Figure 1.1 — Screenshot or reconstruction of a Khanmigo session log*

I want to stay with that moment a little longer, because it is more interesting than it looks.

---

## The Thing That Makes the Failure Interesting

Here is what did not happen: the AI failed to explain the concept. Here is what did not happen: the content was wrong, or the interface was broken, or the student lacked internet access. The system worked. The student interacted with it. The session completed. By every metric the platform was designed to measure, something good occurred.

The failure was not a bug. It was a feature behaving as designed — and the design had a mistake in it.

The mistake is this: the system was measuring a proxy for learning and calling it learning. Engagement is a proxy. Keystrokes are a proxy. Completed sessions are a proxy. They correlate with learning under some conditions, and not others, and the conditions under which they stop correlating are exactly the conditions that a student who has figured out the path of least resistance will produce. The student did not game the system. The system gamed itself. It defined success as a thing that looks like success, and then it produced the thing.

![Diagram showing a measurement loop where the proxy](images/00-introduction-fig-02.png)
*Figure 1.2 — Diagram showing a measurement loop where the proxy*

Now here is the question that runs through this entire book: *What would you have to build instead?*

Not "what feature would you add." Not "what would you prompt differently." What would the entire architecture have to look like if you took seriously — not as a slogan, but as a design constraint — that the goal is verified capability development in the learner, and not the appearance of it?

---

## What I Mean by Verified Capability

Feynman had a test he used on himself. He would pick up a new subject — topology, or Brazilian Portuguese, or the Aztec calendar system — and he would not consider himself to have understood a thing until he could explain it to a reasonably smart person who had not studied it. Not summarize it. Not recall the key terms. Explain it. Generate a new example. Show where the idea breaks. Predict what would happen in a case he had not seen before.

That is a demanding test. It is also, I think, the right test. And it is almost entirely different from the tests most educational platforms actually run.

Most platforms test recognition: does the student pick the right answer from a set of candidates? Some platforms test reproduction: can the student recall a definition or a procedure? A few platforms test application: given a new problem, can the student use the concept? Almost no platforms test what Feynman's test requires, which is generative understanding — can the student produce something new with the concept that the student has never seen before?

![Horizontal bar chart or pyramid showing the distribution](images/00-introduction-fig-03.png)
*Figure 1.3 — Horizontal bar chart or pyramid showing the distribution*

The reason this matters is not philosophical. It is practical. The student who has achieved generative understanding of a concept will perform differently in a clinical setting, or an engineering problem, or a hiring interview than the student who has achieved recognition-level memory of the same concept. They look identical on most assessments. They perform very differently when the situation is novel.

The book is about how to build a system that can tell the difference.

---

## The Two Failure Modes the Field Has Produced

The field of educational technology has been arguing for fifteen years about whether AI in education works. The argument is, on careful inspection, not actually about the evidence. Both sides have evidence. The argument is about which evidence to read.

One side reads the positive cases: the ITS literature showing large effect sizes for intelligent tutoring systems, the Bastani 2025 *PNAS* finding that a well-designed AI tutoring prompt produced substantial learning gains, the spaced repetition literature showing durable retention effects. This side concludes that AI in education is a solved problem and the main task is deployment.

The other side reads the negative cases: the Horvath analysis showing that increased EdTech spending correlates negatively with PISA scores across OECD nations, the smartphone-ban studies showing measurable learning gains when devices are removed, the finding that the students most harmed by poorly designed digital tools are the ones who were already struggling. This side concludes that EdTech is, in the net, harmful and the main task is restraint.

Both sides are reading real evidence. Both sides are wrong about what to do with it.

The evidence, read together, does not say *AI in education works* or *AI in education doesn't work*. It says something more specific and more useful: **certain designs work for certain learning tasks for certain populations under certain conditions, and other designs produce the IDK-IDK pattern.** The question is not whether. The question is which design, for which task, for which learner, under which conditions.

That is not a political question. It is an engineering question. This book is the engineering answer.

| what each side is actually measuring" — the point being that both columns are real | the resolution is in the third column |
| --- | --- |
| contrasting the positive evidence base (ITS effect sizes, Bastani 2025, spaced repetition) against the negative evidence base (Horvath PISA correlations, smartphone-ban studies, struggling-student harm findings) | third |

---

## The Two Failure Modes, Named

I want to name the failure modes precisely, because the rest of the book is organized around avoiding them.

**The no-AI failure:** the system delivers content and measures whether the learner encountered it. Video watched. Page turned. Module completed. Nothing in the system distinguishes between a learner who watched the video and understood it and a learner who played the video at 2x speed while checking their phone. The measurement is logistical, not cognitive. The learner's capability state is invisible to the system, and the system's adaptation to that state is therefore zero.

**The all-AI failure:** the system surrounds the learner with AI assistance so thoroughly that the learner never performs the cognitive operations that produce learning. The AI explains. The AI scaffolds. The AI catches every error before it can teach anything. The learner produces outputs that look correct because the AI is doing the cognitive work. The IDK-IDK pattern is one version of this failure. A learner who produces beautiful essays with AI assistance without ever developing their own ability to reason through an argument is another version. A medical student who passes pharmacokinetics exams with AI support and then cannot reason through drug interactions in clinic is the version that gets people killed.

Both failure modes are the result of measuring the wrong thing. The no-AI failure measures encounter. The all-AI failure measures output. Neither measures capability. A system that measures capability — specifically, the probability that the learner can perform the target cognitive operation independently, without assistance, in a novel situation — is what the book is building toward.

I call that measure the Genuine Learning Probability. Chapter 6 develops it in full. The short version: it is a composite signal constructed from multiple behavioral observations across multiple modes of engagement, updated continuously as the learner interacts with the system, and treated as a probability rather than a score precisely because it is uncertain and should be honest about that uncertainty.

![Comparison of the no-AI failure mode and the](images/00-introduction-fig-04.png)
*Figure 1.4 — Comparison of the no-AI failure mode and the*

---

## The Conductor Frame

Here is the central claim of the book, stated plainly.

The intelligent textbook is not a product. It is a conductor. And a conductor is not an instrument — it is what decides which instruments play, in what combination, for which learner, at which moment, and what to do with what it hears back.

The instruments are things like: a Socratic dialogue mode that pushes a learner to construct understanding by answering questions. A direct explanation mode that delivers clear exposition for a learner who is stuck and needs information before they can think. A case study mode that places a concept in a realistic context and asks the learner to apply it. A generative challenge mode — what I call Glimmer in the chapter on the four modes — that asks the learner to produce something novel with a concept they have been building.

Each instrument has things it does well and things it does badly. The Socratic mode, which is what Khanmigo defaults to, is excellent at building understanding for a learner who already has enough context to reason from. It is actively harmful for a learner who lacks the foundational knowledge to reason productively — who is not "stuck" but "lost," and who needs information, not questions. A system that defends Socratic mode as the right mode for every learner on every concept has made an architectural decision that will produce excellent results for some learners and IDK-IDK for others.

The conductor's job is to know which instrument to reach for, when to switch, and how to tell whether the switch worked.

![Conductor-and-orchestra metaphor rendered as a system diagram ](images/00-introduction-fig-05.png)
*Figure 1.5 — Conductor-and-orchestra metaphor rendered as a system diagram *

That requires measurement. Which brings us back to Genuine Learning Probability. A conductor who cannot hear the orchestra cannot conduct. A platform that cannot observe capability state cannot adapt. The measurement layer is not a nice-to-have — it is the thing that makes the rest of the architecture possible.

---

## The Simplicity Trap

I want to pause here and name something the book is explicitly not arguing.

The conductor frame is not an argument that every learning problem requires the full conductor-and-orchestra apparatus. Some learning problems are simple enough that a much simpler arrangement is correct, and deploying the full architecture would be waste at best and harm at worst.

There is a character in this book named Priya. She is nineteen, six years in a residential program in Hyderabad, learning English vocabulary to qualify for entry-level employment in three sectors where that qualification changes her economic trajectory. For Priya, the right intelligent textbook is probably Anki — a well-designed spaced-repetition flashcard system — combined with a weekly volunteer conversation session on Zoom. The vocabulary acquisition evidence is clear, the spaced-repetition evidence is strong, the conversational practice evidence is strong. The conductor's job in Priya's case is to make sure the Anki deck is well-constructed and to watch the retention data to decide when she is ready to use the vocabulary in conversation. That is the full architecture. Anything more elaborate would be absorbing resources that should be going to the volunteer's time.

There is also a character named Ash. Ash is a first-year medical student working through pharmacokinetics. The failure modes for Ash are not that the material is unengaging or that the vocabulary is unfamiliar. The failure modes are subtle: Ash can produce the right numerical answer through a procedure he has memorized without understanding why the procedure works, which means the right answer on the exam and the wrong reasoning in clinic. The transfer requirement is high. The consequence of non-transfer is mortality. For Ash, the Anki-plus-volunteer arrangement is the wrong answer. The full conductor architecture — with carefully designed phase gates between modes, within-learner adaptive decisions about when to push and when to scaffold, and measurement that specifically targets the difference between procedural recall and generative understanding — is what the problem requires.

Most actual learning problems land between Priya and Ash. The book's architecture scales: Chapters 3 through 9 describe the full system, and the complexity threshold test in Chapter 3 is the tool for deciding how much of it any specific problem actually needs.

![Horizontal spectrum from "Priya" (left) to "Ash" (right)](images/00-introduction-fig-06.png)
*Figure 1.6 — Horizontal spectrum from "Priya" (left) to "Ash" (right)*

---

## The Economics Change Everything Except the Target

There is a fact about the economics of intelligent textbooks that I want to name early because it changes the shape of several later chapters.

For decades, the high-quality intelligent tutoring systems that produced the large effect sizes in the ITS literature cost somewhere between $100 and $1,000 per student-hour to produce. That is not a typo. The Carnegie Learning ITS systems, the LISP Tutor, the Cognitive Tutors — these were expensive precisely because building the knowledge model, the constraint set, and the feedback logic required thousands of hours of expert labor per concept. The effect sizes were real. The deployment was limited to the institutions that could afford the production cost.

The cost has collapsed. Not reduced — collapsed. The combination of large language models capable of generating pedagogically sound content, AI-assisted curriculum design, and cloud infrastructure has moved the marginal cost of generating an intelligent textbook's content layer to a range that does not require a research grant or a venture round. The Sesame Street principle — that high-quality educational content production requires the resources of a major television studio — no longer governs the production cost.

What the cost collapse does not change is the target. The goal is still verified capability development, not the appearance of it. The cost collapse makes it possible to build intelligent textbooks for subjects and populations that could not previously be served. It does not make it easier to build one that actually works. A poorly designed AI-generated intelligent textbook at low cost is still a poorly designed intelligent textbook. The IDK-IDK pattern runs on cheap infrastructure just as readily as on expensive infrastructure.

This is why the architecture matters. The cost collapse gives us the resources to deploy widely. The architecture determines whether the deployment produces learning.

![Line chart showing production cost per student-hour for](images/00-introduction-fig-07.png)
*Figure 1.7 — Line chart showing production cost per student-hour for*

---

## What This Book Is

This book is a design specification.

Not a survey of the field. Not a cheerleading document for AI in education. Not a warning about it. A specification: if you wanted to build a platform that avoided the failure modes the field has already demonstrated, and captured the gains the evidence supports, here is what the architecture would have to do, in the order the decisions depend on each other.

The vocabulary the book teaches is small: *conductor*, *instrument*, *four modes*, *seven signals*, *Genuine Learning Probability*, *within-learner bandit*, *cost-collapse asymmetry*, *IDK-IDK pattern*, *experiment-as-product*. Each term gets defined where it first appears. The book's Lexicon in Appendix A is the single-page index if you need to find a definition quickly.

The book is for two readers. The first is the domain expert — the experienced teacher, the curriculum designer, the person who has content and conviction and needs to know what she is commissioning when she commissions an intelligent textbook. The second is the developer who has been handed an API specification and needs to build what the first reader will use. After reading this book, both readers should be able to hold the same conversation about the same decisions in the same terms. That shared language is the book's primary product.

---

## A Disclosure About How This Book Was Written

This book is about AI in education. It was also written in collaboration with AI tools. I want to be specific about what that means.

AI tools — primarily Claude — generated draft passages, surfaced primary-source candidates for verification, and produced first-pass syntheses of the evidence base. The conductor frame is mine. The architectural decisions are mine. The judgment calls about what to include and what to exclude are mine. Where an AI-generated passage landed in the published prose, it landed because I read it, verified it, and accepted it. Where it landed wrong, that error belongs to me.

The AI did not select the central argument. It did not order the chapters. It did not decide where to push back on Horvath and where to extend Khan. It did not write the composite cases — Priya and Ash are built from situations I have seen close-up, and the AI's role was sentence-level revision, not characterization. It did not write the "what would change my mind" sections that close each chapter, because those are the most personal sections in the book and I wanted to write them without an intermediate language-model pass.

The pattern of disclosure I have just walked through — what the AI did, what it did not, where the human judgment lives — is the pattern the Genuine Learning Probability framework in Chapter 6 specifies for student work. It is the pattern the AI-generation policy in Chapter 10 specifies for AI-assisted content production. I would not feel comfortable asking the platform's users to disclose what I was not willing to disclose myself.

---

## One Note on a Specific Finding

Chapter 4 leans heavily on the Bastani 2025 *PNAS* result. The headline finding: students who used a Socratic-prompt-wrapped GPT scored 17 percentage points lower on a no-AI post-test than students who used a tutor-prompt-wrapped GPT, using the same underlying model. Different prompting. Same model. Very different learning outcomes.

That finding is the cleanest single piece of evidence the field has produced about how the conductor's design decisions — specifically, the decision about which mode to deploy — affect learning outcomes. It is one study, one population, one subject, one moment in 2024. It needs replication. Chapter 12 names this explicitly as one of the eight open questions.

If Bastani 2025 does not replicate, the central argument does not collapse. The argument about why the conductor's design decisions matter does not depend on a single study. But the anchor shifts, and I want to be honest that it is an anchor.

---

## The Question

Kristen DiCerbo said it publicly: *We see more IDK IDK than we would like.*

The people who built the most ambitious AI education deployment in human history noticed the failure mode it was producing, named it clearly, and said out loud that they did not know how to solve it within their current architecture. That is not a failure of honesty. That is the clearest possible signal that the current architecture has a mistake in it.

What would you have to build instead?

That is the question. The rest of the book is the answer.

---

## LLM Exercises

The following exercises are designed to be completed with AI assistance. For each, your task is not to produce a polished output but to have a conversation that surfaces your own thinking.

**Exercise 0.1 — Reproduce the Failure**
Ask an AI tutoring system to help you understand a concept you genuinely do not know. Before the session, write down what you think understanding would look like — what you would be able to do if you actually learned it. After the session, test yourself against that description without AI help. Write one paragraph: what did the session produce, and what is the gap between that and the capability you described beforehand?

**Exercise 0.2 — The Conductor's Decision**
You are designing an AI tutoring system for a learner who is trying to understand compound interest for the first time. The learner has completed two sessions and consistently produces correct numerical answers but cannot explain why the formula works.
- Ask an AI: "What does this behavioral pattern suggest about the learner's current capability state?"
- Then ask: "What mode of engagement would you recommend next, and why?"
- Evaluate the AI's reasoning. Does it name the failure mode? Does it distinguish between procedural recall and generative understanding? Write two paragraphs: what the AI got right, and what it missed.

**Exercise 0.3 — Design Against the Failure Mode**
The IDK-IDK pattern is a system producing a metric that looks like success while the underlying capability does not develop.
- Name one other context — outside of education — where you have seen this pattern. (A product that measures engagement and calls it value. A management system that measures activity and calls it productivity.)
- Ask an AI to help you identify what measurement would have to change to catch the failure earlier.
- Write one paragraph: what is the measurement that would actually track what matters, and what makes it harder to collect than the proxy?

## Prompts

Use these prompts with Claude to generate interactive D3 v7 versions of the
figures in this chapter. Each produces a standalone HTML file you can open
in a browser and modify freely.

**Prerequisites:** Load `brutalist/CLAUDE.md` and `brutalist/DESIGN.md` into
your Claude project context before using these prompts. They define the stack,
naming conventions, color system, and typography the figures use.

---

### Figure 1.1 — Screenshot or reconstruction of a Khanmigo session log

Create a standalone D3 v7 HTML file for Figure Screenshot or reconstruction of a Khanmigo session log. Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: screenshot or reconstruction of a Khanmigo session log showing a completed interaction flagged as "engaged" — visual contrast between the system's success indicator and the `idk idk` input that triggered it; caption should read something like "Logged: engaged. Actual state: unknown.". Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relationships in the brief. Use a zero baseline for bars or areas, direct labels where possible, and annotations named in the brief. Use only DESIGN.md color variables and the required serif/mono font split.

> Reference implementation: `d3/00-introduction-fig-01.html`

---

### Figure 1.2 — Diagram showing a measurement loop where the proxy

Create a standalone D3 v7 HTML file for Figure Diagram showing a measurement loop where the proxy. Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: diagram showing a measurement loop where the proxy metric (engagement/keystrokes/completed sessions) diverges from the target metric (capability development) — arrows showing how optimizing the proxy actively degrades the target; label the gap "the IDK-IDK zone". Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relationships in the brief. Use a zero baseline for bars or areas, direct labels where possible, and annotations named in the brief. Use only DESIGN.md color variables and the required serif/mono font split.

> Reference implementation: `d3/00-introduction-fig-02.html`

---

### Figure 1.3 — Horizontal bar chart or pyramid showing the distribution

Create a standalone D3 v7 HTML file for Figure Horizontal bar chart or pyramid showing the distribution. Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: horizontal bar chart or pyramid showing the distribution of educational platforms across four capability levels — recognition, reproduction, application, generative understanding — with approximate percentage of current platforms at each level; student should see the extreme skew toward recognition. Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relationships in the brief. Use a zero baseline for bars or areas, direct labels where possible, and annotations named in the brief. Use only DESIGN.md color variables and the required serif/mono font split.

> Reference implementation: `d3/00-introduction-fig-03.html`

---

### Figure 1.4 — Comparison of the no-AI failure mode and the

Create a standalone D3 v7 HTML file for Figure Comparison of the no-AI failure mode and the. Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: side-by-side comparison of the no-AI failure mode and the all-AI failure mode — what each measures (encounter vs. output), what each misses (capability), and the GLP as the third column showing what would actually need to be observed; visual should make clear that the two failures are mirror images of the same mistake. Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relationships in the brief. Use a zero baseline for bars or areas, direct labels where possible, and annotations named in the brief. Use only DESIGN.md color variables and the required serif/mono font split.

> Reference implementation: `d3/00-introduction-fig-04.html`

---

### Figure 1.5 — Conductor-and-orchestra metaphor rendered as a system diagram 

Create a standalone D3 v7 HTML file for Figure Conductor-and-orchestra metaphor rendered as a system diagram . Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: conductor-and-orchestra metaphor rendered as a system diagram — the conductor (adaptive engine) at center, four instruments (Socratic, direct explanation, case study, Glimmer) as nodes, with arrows showing signal flow: learner behavior → conductor → mode selection → learner response → conductor; make the feedback loop visible. Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relationships in the brief. Use a zero baseline for bars or areas, direct labels where possible, and annotations named in the brief. Use only DESIGN.md color variables and the required serif/mono font split.

> Reference implementation: `d3/00-introduction-fig-05.html`

---

### Figure 1.6 — Horizontal spectrum from "Priya" (left) to "Ash" (right)

Create a standalone D3 v7 HTML file for Figure Horizontal spectrum from "Priya" (left) to "Ash" (right). Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: horizontal spectrum from "Priya" (left) to "Ash" (right) with labeled markers for: complexity of failure modes, transfer requirement, consequence of non-transfer, appropriate architecture depth — reader should see that most problems cluster in the middle and that the spectrum determines which layers are warranted. Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relationships in the brief. Use a zero baseline for bars or areas, direct labels where possible, and annotations named in the brief. Use only DESIGN.md color variables and the required serif/mono font split.

> Reference implementation: `d3/00-introduction-fig-06.html`

---

### Figure 1.7 — Line chart showing production cost per student-hour for

Create a standalone D3 v7 HTML file for Figure Line chart showing production cost per student-hour for. Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: line chart showing production cost per student-hour for intelligent tutoring systems from 1985 to 2025 — dramatic drop after 2022 marked as "LLM cost collapse"; second line showing effect size from well-designed systems (flat/stable); the point being that cost collapsed while the quality target did not. Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relationships in the brief. Use a zero baseline for bars or areas, direct labels where possible, and annotations named in the brief. Use only DESIGN.md color variables and the required serif/mono font split.

> Reference implementation: `d3/00-introduction-fig-07.html`
