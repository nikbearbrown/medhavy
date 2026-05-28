# Chapter 1: What Is Medhavy?

---

## Learning Objectives

By the end of this chapter, you will be able to:

1. **Name and explain the two failure modes in EdTech** — and articulate why both produce worse outcomes than either their proponents or critics typically acknowledge.
2. **Use MIT OpenCourseWare as evidence** to explain why content was never the product that education was selling.
3. **Describe the four layers of Medhavy's architecture** — the Book Library, Tic TOC, the Adaptive Engine, and the Measurement Layer — and explain what each one does and why it's structured that way.
4. **Distinguish between engagement metrics and learning evidence**, and explain why conflating them produces systems that look effective while failing students.
5. **State what Medhavy currently knows versus what it is in the process of figuring out** — and explain why that epistemic honesty is itself a design decision, not a limitation to be apologized for.

**Prerequisites:** None technical. You should have a general awareness that AI is being deployed in education and that the people responsible for institutions are asking questions about whether any of it works. You don't need to know how language models function, how reinforcement learning works, or what a causal graph is. Those things come later. Right now we need to establish what problem we're solving and why the existing solutions don't solve it.

**Where this fits:** This is the opening chapter of the Medhavy book. Everything that follows — the bandit algorithm, the GLP measurement framework, the causal graph program, the book library — is downstream of what this chapter establishes. If the architecture doesn't make sense, it's because the problem it's solving isn't yet clear. This chapter makes it clear.

---

## The Problem I Kept Running Into

Here is a fact about education that most of the people trying to fix it prefer not to examine too closely: we have had free, high-quality educational content available to anyone with an internet connection for over twenty years.

MIT put lectures online in 2001. Harvard followed. Khan Academy launched in 2006. By 2012, Coursera and edX were offering courses from Stanford, MIT, and Berkeley — full courses, professional production quality, for free. The entire syllabi of the world's most credentialed institutions have been sitting there, available to anyone who wanted them, for two decades.

And it didn't work.

Not in the way people predicted it would work. Not in the way the techno-optimists on the TED stage said it would work. MIT's enrollment did not collapse. Harvard's didn't either. If anything, demand for seats at exactly those institutions increased as their content became free. When MIT put lectures on the internet, what got more valuable wasn't the content — it was the experience of being at MIT.

I kept running into this fact as I was building Medhavy, and for a long time I didn't quite know what to do with it. The obvious interpretation is: "See, traditional universities survived disruption." But that's not what the data is showing. What the data is showing is something more specific and more uncomfortable for everyone in this space, including me.

Content was never the product.

If that sentence is right — and I believe it is — then an enormous fraction of what has been built under the banner of "EdTech" is solving the wrong problem.

---

## Two Failure Modes

There are two ways to get the role of AI in education wrong, and the field has managed to get both wrong simultaneously, in opposite directions.

**The first failure mode is no AI at all.**

In the traditional model, the professor does everything. Not just the genuinely irreplaceable things — the mentorship, the intellectual sparring, the career-trajectory-altering conversation — but also the automatable things. Answering "what does the Warburg Effect mean" for the fourteenth student that week who typed the same question into a message box. Generating retrieval practice. Writing five versions of the same quiz question at different difficulty levels. Explaining the same concept seventeen different ways across seventeen different office hours sessions, with seventeen different students, until the right framing clicks for that particular student's particular misconception.

These are tasks that AI does better than humans in specific ways: consistently, patiently, at 2am, for every student simultaneously, without exhaustion or frustration. A professor can explain something seventeen different ways, but the seventeenth explanation doesn't have the same energy as the first. An AI system doesn't have that problem.

When professors absorb the automatable work because there's no system to take it on, the irreducibly human work — the mentorship, the moment a student believes they can do something they didn't think they could — gets crowded out. It happens by accident, when there's time, which increasingly there isn't. The most valuable thing a professor can do for a student is the thing that's most vulnerable to being eaten by the least valuable work.

**The second failure mode is all AI.**

On the opposite end, EdTech has a long and unfortunate tradition of claiming that AI can be the teacher. Replace the lecture. Replace the mentor. Replace the relationship. The implicit argument underneath most of the platforms that have raised significant capital in the past decade is this: if we can deliver content cheaply at scale, we have solved education.

Sal Khan, in a 2023 TED Talk, called AI "probably the biggest positive transformation that education has ever seen." The platform behind that claim, Khanmigo, was Khan Academy's AI tutor — a Socratic dialogue system that would guide students to answers rather than giving them directly.

Three years later, Kristen DiCerbo, Khan Academy's Chief Learning Officer, described what the usage data actually showed. Students were typing "IDK IDK" — I don't know, I don't know — into the Socratic prompts and moving on. The system logged them as engaged. They were not learning. The chatbot had been mistaken for the teacher, and the data used to evaluate the system was measuring the wrong thing.

The IDK IDK finding is not a Khan Academy problem. It is a measurement problem that the entire field shares. When you measure engagement — clicks, time-on-platform, completion rates — you get systems optimized to produce engagement. Engagement is not learning. It is a behavioral trace that sometimes correlates with learning and sometimes doesn't, and when you build your reward signal out of it, you get systems that are very good at producing the trace without producing the thing.

Both failure modes make the same underlying error: they don't distinguish between what AI should do and what humans should do.

The first failure mode hands automatable work to humans, burning the time and energy that should go toward what only humans can do. The second failure mode hands irreplaceable human work to AI, produces a system that looks like it's working because the engagement metrics go up, and discovers years later that the students weren't learning.

Medhavy is my attempt to build something that gets this distinction right — or at least to build the infrastructure for figuring out where the line actually is, because I don't think anyone has proven it with evidence yet. That includes me.

---

## What AI Does Well in Education (and Why This Matters)

Before I explain what Medhavy is, I need to establish what AI actually does well in educational contexts, because a lot of the skepticism I hear from professors and administrators conflates "AI cannot replace human mentorship" with "AI has nothing useful to offer." These are not the same claim.

Here is what AI does well:

It delivers the same explanation seventeen different ways without losing patience. It answers questions at 2am when the student can't sleep before an exam and you, the professor, are asleep. It generates retrieval practice calibrated to what this specific student got wrong last week, not what the average student in the course struggles with. It produces a spaced repetition schedule — the evidence-based practice of reviewing material at increasing intervals to drive it from working memory into long-term memory — that no human being has the bandwidth to manage for 200 students simultaneously.

It rewrites the Prompt Engineering textbook so the examples use tools and workflows that art and design students recognize, rather than the software engineering examples that make sense to CS students but feel like a foreign language to everyone else. It creates the version of the frog-counting video that uses cats instead of frogs, for the cat-obsessed eight-year-old who couldn't connect with the original, at a cost that makes that kind of personalization economically viable when it previously wasn't.

What AI does well, in short, is the information transfer layer. Content delivery, personalized to the learner, at any time, with infinite patience. This layer is real and it is valuable. It was consuming enormous amounts of human time that should have been spent elsewhere. The fact that AI is not the whole of education does not mean the information transfer layer is nothing.

The question Medhavy is built around is: if AI handles the information transfer layer reliably, what can humans stop doing that they shouldn't have been doing in the first place — and what space does that open up for the work only humans can do?

---

## What Humans Do That AI Cannot

I want to be specific about this, because "human connection matters" is the kind of sentence that sounds profound and means nothing without examples.

I teach a course called Branding & AI. At the end of the semester, students present their final projects. One semester, a student named Manisha Sahu walked into her presentation and pitched AdverseAI — a real product with a working demo, a live website, a full brand, a coherent positioning strategy. She had built it. The two professors in the room were her "sharks" — not a metaphorical audience, but actual evaluators asking actual questions about whether the product made sense, whether the market existed, whether the assumptions held.

That moment — Manisha standing in front of people who know how this works, defending a thing she made — is not content delivery. I cannot describe what happened in that room in terms of information transfer. What happened was that a student discovered she could do something she didn't know she could do, in a context where someone who knew better told her it was real. That discovery is not available at 2am from a chatbot. It requires presence, accountability, and a relationship that developed over a semester.

This is what the Irreducibly Human curriculum, which Medhavy is designed to protect time for, names precisely. The professor's job is not to be a content delivery system with office hours. The professor's job is to be the person in the room when a student becomes capable of something they weren't capable of before.

Alongside that: ethical modeling. Watching someone navigate a genuinely hard decision — one where legitimate values conflict and there is no clean answer — and seeing how they hold their principles under pressure. This requires a real human making a real decision with real stakes. A language model does not have stakes. It cannot model what it looks like to be accountable for a judgment call in a way that costs you something if you're wrong.

Causal reasoning under uncertainty. The judgment call that requires integrating multiple conflicting expert perspectives into a recommendation someone is accountable for, under conditions of incomplete information, in a domain where the right answer matters. Students learn to do this by watching people do it and eventually doing it themselves, with feedback from someone who can tell the difference between reasoning that worked and reasoning that happened to get a correct answer for the wrong reasons.

Embodied presence. The improvisation of a real classroom. The moment you read that a student's confusion is not conceptual but emotional — they're not confused about the material, they're afraid they're not capable — and you respond to what's actually happening rather than what they said.

These are not soft skills as the phrase is usually meant, implying less-than. They are irreducible cognitive and relational capacities that AI cannot substitute for — not because AI is insufficiently powerful, but because they require accountability, presence, and a relationship that develops over time with real stakes on both sides.

The design principle behind Medhavy is that these capacities should be protected from being consumed by automatable work. That's what the architecture is for.

---

## The Conductor Frame

I need to give you a working model of what Medhavy actually is before I describe the architecture, because the architecture will make more sense if you have the conceptual frame first.

Medhavy is not a textbook. Not a chatbot. Not a learning management system. Not an AI tutor.

Medhavy is the conductor.

The conductor doesn't play the instruments. She decides which instrument plays, when, and for how long — based on evidence about what the music needs at this moment, adjusted as the performance unfolds. She reads the signals from individual musicians and the ensemble and makes continuous decisions about emphasis, timing, and balance. The musicians are specialists; the conductor's job is to know when each specialist serves the whole.

In Medhavy's architecture:

- The specialist AI systems are the instruments — the Ask AI mode that provides context-aware explanation, the Case Study facilitator that presents clinical ambiguity in professor-approved scenarios, the Quiz Me engine that generates spaced retrieval practice, the Glimmer system that scaffolds creative non-trivial work
- The professor is the conductor's counterpart — they shaped the course, approved the content, own the pedagogical vision, and remain the irreplaceable human in the system
- The learner is who the concert is for

The conductor exists because the impact of AI on learning is obvious. The right implementation is not. The field doesn't know yet which instruments to play when, for which learner, on which concept. Medhavy is built to run that experiment systematically rather than assuming the answer.

---

## The Four Layers

### Layer 1: The Book Library

Medhavy currently has over sixty base textbooks spanning virtually every introductory college subject — mathematics, computer science, biology, chemistry, history, economics, statistics, psychology, writing, and more.

These are not generic content dumps. Each book is structured around a concept node map: the underlying network of ideas and the prerequisite relationships between them. Before you can understand concept B, you need to understand concept A. Before A, you need C and D. This map is the intellectual skeleton of the subject, and it's what allows Medhavy to know where a student is, what they're ready for, and what gap is responsible when they're struggling.

The base books are raw material. What gets delivered to students is an adaptation. Prompt Engineering for Art and Design students uses different examples than Prompt Engineering for Computer Science students. The concept graph is the same. The voice, the worked examples, the motivational framing, and the points of entry are different — designed for the specific person who needs to care about this material.

This matters because motivation is not decoration. A student who cannot connect the material to anything they already care about will not learn it, regardless of how well-structured the explanation is. The personalization in the book library is not about making content "fun." It is about making the on-ramp from what the student already understands to what they need to understand as short as possible.

The book library also solves a specific problem in the Medhavy architecture: the professor doesn't have to start from nothing. When a professor begins a Tic TOC session — which I'll describe next — they're working with a book that already has structure, concept maps, and learning outcomes. They're adapting and owning it, not generating it from scratch.

### Layer 2: Tic TOC — The Curriculum Design Engine

Most professors received no formal training in curriculum design. This is not a criticism; it is a structural fact about how academic careers work. You become expert in a domain through research and scholarship. You become a professor, in part, because of that expertise. But expertise in a domain is not the same as expertise in teaching that domain, and the training that would close that gap — backward design, assessment alignment, prerequisite mapping — is not part of most doctoral programs.

Backward design is the practice of building a course by starting with the end: what should students be able to do when the course is over? Then working backward to: what evidence would demonstrate that capability? Then: what instruction and practice produces that evidence? Then: what sequence of content and experience leads to that instruction?

It sounds obvious. Most courses are not built this way. Most courses are built by deciding what content to cover in what order, then assessing whether students can recall it.

Tic TOC is a backward design consultant. A professor spends approximately two hours in a structured interview. Tic TOC asks: what do you want your students to be able to do? What counts as evidence they can do it? What do they need to know first? Where do most students get stuck, and why?

The output of that session is a complete curriculum package: a syllabus with learning outcomes, a prerequisite map (which concepts must be understood before which), a student guide, an instructor guide, and an institutional guide. The professor has final say on every decision. But Tic TOC's structured questioning surfaces the implicit assumptions about prerequisite knowledge and the gaps between what professors think they're teaching and what students can actually demonstrate.

This output becomes three things:

- A book: the professor's textbook, adapted from the library base to their specific course design, with their name on it
- A Medhavy course: the adaptive learning environment built on the concept node map Tic TOC produced
- A Canvas course: the LMS integration that places the course where students already live

That third item matters more than it might seem. The most common reason students don't use educational technology is friction — the tool lives somewhere other than where the course already runs. Tic TOC's output integrates directly with the learning management system the institution uses, because the goal is to make Medhavy's adaptive layer available in the course environment, not to ask students to add a platform.

![Tic TOC session flow — interview → concept node map → three outputs (book, Medhavy course, Canvas course). Caption: The professor's...](images/archive-01-what-is-medhavy-fig-01.png)
*Figure 0.1 — Tic TOC session flow*

### Layer 3: The Adaptive Engine (1.5 → 2.0)

Medhavy 1.5 is a four-mode learning environment. Each mode is a different kind of engagement with the material:

**Ask AI** — Context-aware explanation and question-answering, grounded in the concept map for this specific course. When a student asks what the Warburg Effect means, the answer is calibrated to where they are in the course, what they've covered, and what the professor approved as the conceptual frame for this course. Not a generic internet answer. A course-contextual one.

**Case Study** — Professor-approved clinical scenarios presenting genuine ambiguity. Not "here is the right answer explained through a story" but "here is a situation with legitimate competing values and incomplete information — what's your reasoning?" The professor approves the cases. The ambiguity is real.

**Quiz Me** — Spaced retrieval practice using FSRS (Free Spaced Repetition Scheduler), an evidence-based algorithm for scheduling review at the intervals that maximize durable retention. The questions are generated from the concept map, calibrated to what this student got wrong or uncertain on last time. Not random. Not the same quiz for every student.

**Glimmer** — A creative, non-trivial assignment that scaffolds forward without the student knowing where it's going. Each Glimmer session builds a piece of work that, over the term, assembles into a substantial project. The student doesn't experience this as "building a term project." They experience it as an interesting assignment this week. The cumulative product is the evidence of genuine integration — the kind of work you can only produce if you actually understand the material.

Every session in Medhavy 1.5 is logged: which section, which mode, how long, what type of question, how the student performed. This is the data generation layer. It is building the empirical record that Medhavy 2.0 needs.

Medhavy 2.0 will introduce the contextual bandit — an algorithm that reads this session data and decides which mode to offer, for which learner, on which concept, based on evidence about what has produced learning for learners like this one in situations like this one. The bandit learns which instrument to play when.

One design decision in the bandit architecture worth explaining here because it matters for how to evaluate Medhavy's claims: the bandit is within-learner, not between-learner.

The traditional approach to testing whether an intervention works is to divide students into groups — give group A the intervention, give group B something else, compare outcomes. This is a valid design, but it has a problem in educational technology: assigning individual students to pure random treatment raises ethical questions, and the statistical assumption that one student's treatment doesn't affect another's outcome (called SUTVA — the Stable Unit Treatment Value Assumption) is often violated in classroom settings, where students talk to each other, help each other, and share information about what worked.

Medhavy's bandit treats each learner as their own experiment. The question is not "does this mode work on average" but "what mode works best for this learner on this concept right now, given everything I've seen from them so far?" This satisfies SUTVA by design — students use the system alone, so one student's mode assignment doesn't affect another's outcomes. It is also ethically cleaner: no student is consigned to a pure control condition. Every student benefits from what the system learns.

### Layer 4: The Measurement Layer

This is where the IDK IDK problem gets addressed at the design level.

PostHog currently captures behavioral engagement data from Medhavy 1.5: which sections students visit, how long they spend, which modes they use, completion rates. This is the engagement layer — necessary but insufficient. It is the kind of data that shows students were typing "IDK IDK" while the system logged them as engaged.

The GLP framework — Genuine Learning Probability — is Medhavy's specification for what the reward signal should actually measure. It identifies seven behavioral components that genuine cognitive engagement leaves as traces in usage data:

1. **Error trajectory coherence** — Does a student's pattern of errors reflect a consistent underlying misconception that gets resolved, or random noise? Genuine learning produces coherent error arcs.
2. **Cross-context transfer** — Can the student apply a concept in a scenario that differs from the one where it was introduced? Transfer is one of the most reliable behavioral indicators of genuine understanding.
3. **Uncertainty calibration** — Does the student's expressed confidence match their accuracy? Students who know what they know and know what they don't know are calibrating genuinely; students who are confident regardless of accuracy are not.
4. **Retrieval strength decay** — How does performance on a concept change over time without intervening practice? Durable learning decays slowly; rote memorization decays fast.
5. **Scaffolding response curve** — When a student receives help, does their next independent attempt show improvement? Or do they require the same scaffolding again? The curve of response to support is a behavioral trace of whether understanding is developing or whether the student is using the scaffolding as a substitute for it.
6. **Question quality trajectory** — Do students' questions become more specific and conceptually sophisticated over time? Question quality is a behavioral proxy for genuine engagement with the underlying structure of a domain.
7. **Integration evidence** — Does the student's work show connections between concepts from different parts of the course? Integration across the concept map is a trace of the kind of understanding that can't be produced by recall alone.

These components are grounded in the neurobiological events that constitute learning — the synaptic changes, the consolidation processes, the transfer mechanisms that cognitive science has established over decades. They are not arbitrary. But the weights that should be assigned to each component, and how those weights should vary across learners and domains and concept types, are currently unknown.

This is not a gap I'm hiding. Figuring out those weights is part of the research program. The measurement layer is built to generate the data from which the weights can be learned.

![The measurement hierarchy — behavioral events (PostHog) → GLP components → reward signal → bandit update → mode selection. Caption: What...](images/archive-01-what-is-medhavy-fig-02.png)
*Figure 0.2 — measurement hierarchy*

---

## The Deep Analysis: Why the Measurement Problem Is Structural

The IDK IDK finding from Khanmigo is worth sitting with, because it illustrates something that goes beyond Khan Academy's specific implementation.

When Kristen DiCerbo described students typing "IDK IDK" into Socratic prompts and moving on, the system wasn't malfunctioning. It was functioning exactly as designed. The system was designed to measure engagement — whether students interacted with the prompts. Students interacted with the prompts. The system logged them as engaged.

The system was optimized for the wrong thing not because of a programming error but because of a measurement decision made earlier in the design process: the decision to use engagement as a proxy for learning.

This decision is almost universal in EdTech. The reason is straightforward: engagement is easy to measure. Every click, every second on platform, every completed lesson can be logged and reported. Learning — genuine learning, the kind that produces durable capability change — is hard to measure. It requires assessments that test transfer rather than recall, observations that track performance over time rather than in the moment of instruction, and methods that can distinguish understanding from familiarity with correct answers.

The field optimizes for what's measurable. What's measurable is engagement. So the field builds systems optimized for engagement.

Here is the uncomfortable implication: every platform claiming to show learning gains based on completion rates and engagement metrics is, in some important sense, making the same error Khanmigo made. Not necessarily in magnitude, but in kind. They are measuring the proxy and calling it the thing.

Medhavy is not immune to this pressure. The GLP framework is my attempt to specify a measurement approach that is genuinely grounded in learning theory rather than convenient to instrument. But the GLP weights are unknown, the framework hasn't been validated at scale, and I would be making the same error I'm describing if I claimed otherwise.

What Medhavy does differently is structural: it separates the measurement specification from the reward signal optimization, and it makes the current state of knowledge about both explicit. The system is built to learn the right weights from deployment data. That requires having the deployment data and the architecture to learn from it — which Medhavy 1.5 is generating and Medhavy 2.0 will use.

This is the honest version of "we're working on it." Not "our AI personalization engine produces superior outcomes" — a claim that would require evidence I don't have. But: here is the measurement problem, here is why existing solutions don't solve it, here is the architecture we've built to address it, and here is what we still need to figure out.

---

## What Medhavy Doesn't Know Yet

I want to be direct about this, because the book you're reading is, among other things, a critique of the EdTech field for claiming more than its evidence supports. I cannot hold the field to an epistemic standard and then fail to meet it myself.

Here is what Medhavy currently doesn't know:

**The right weights for the GLP reward signal.** The seven components are theoretically grounded. The per-learner weighting — how much uncertainty calibration should count relative to retrieval strength decay for this specific learner on this specific concept — hasn't been estimated from data yet. The architecture to learn these weights is built. The data is being generated. The learning hasn't happened.

**Which bandit arms work for which learners on which concepts.** This is the core question the 2.0 bandit is designed to answer. Medhavy 1.5 is generating session data. The bandit arrives in 2.0 with something to learn from. Right now, we have hypotheses about what the data will show — that Ask AI works better for initial concept acquisition, that Quiz Me drives consolidation, that Glimmer produces integration evidence. These are informed hypotheses. They are not findings.

**Whether book variant matters more than intervention mode.** My hypothesis is that book variant — the personalization of examples and framing — dominates for initial engagement, while intervention mode — which of the four modes a student uses — dominates for retention. This is testable with the library we have. It hasn't been tested yet.

**Whether content personalization produces durable learning gains or just engagement.** The cat version of the frog-counting video may produce genuine learning gains, or it may produce higher engagement without changing the learning outcome. There is an uncontrolled experiment running right now, in classrooms using Medhavy, without the measurement infrastructure to distinguish between these. Medhavy is building that infrastructure. It is not yet complete.

Here is what Medhavy does know:

**Behavioral engagement is not learning evidence.** The IDK IDK finding proved this at scale, and the theoretical reasons for the gap are well-established. Medhavy is built on this premise.

**SUTVA is satisfied by design.** In an online solo-use system, the within-learner bandit design avoids the contamination problems that make classroom RCTs difficult to interpret. This is a genuine methodological advantage, not a rhetorical one.

**The measurement problem is structural, not technical.** The field isn't measuring learning because measuring learning is hard and nobody wants to delay the launch. Medhavy is trying to measure learning because the alternative is building something that produces IDK IDK at scale and calls it pedagogy.

**The professor's intent is documented.** When Tic TOC produces a concept map, it creates a record of what the professor intended to teach, in what sequence, with what prerequisite assumptions. When Medhavy data shows students struggling on concept X, we can ask whether the prerequisite gap was flagged in Tic TOC and the professor overrode it — and trace the downstream consequences. That evidence chain exists nowhere else in EdTech at the moment.

---

## The Chapter in One Sentence

Medhavy handles what AI does well — information transfer, retrieval practice, content personalization, consistent patient explanation — so humans can do what only humans can do: transform a student's sense of what they're capable of.

Everything else is infrastructure for making that separation reliable rather than accidental.

---

## Chapter Summary

Here is what you can now do that you couldn't before reading this chapter:

**You can diagnose EdTech failures by type.** When you see a platform claiming AI will replace lectures, you can explain the mechanism by which that claim fails: it mistakes content for the product, optimizes for the measurable proxy, and produces engagement without learning. When you see a professor refusing any AI involvement in pedagogy, you can explain the cost: automatable work consuming the time and energy needed for irreplaceable human work.

**You can explain why content was never the product.** The MIT OpenCourseWare case isn't anecdote. It's a twenty-year natural experiment with a clear result: when content becomes free and abundant, the scarce valuable thing becomes transformation. Institutions that understood they were selling transformation got more valuable. Those that thought they were selling content are in trouble.

**You can describe Medhavy's four layers and what each one does.** The Book Library provides structured content adapted to specific learners. Tic TOC surfaces and formalizes the professor's pedagogical intent. The Adaptive Engine provides four modes of interaction calibrated to the learner's position in the concept map. The Measurement Layer attempts to track genuine learning rather than engagement proxies.

**You can explain the difference between engagement metrics and learning evidence.** Engagement metrics measure behavioral interaction. Learning evidence measures capability change — the ability to apply a concept in a new context, retrieve it after a delay, integrate it with other concepts. Systems optimized for engagement produce IDK IDK. Systems designed to produce learning evidence are harder to build and harder to validate, which is why the field mostly doesn't.

**The one mistake to watch for** when thinking about AI in education: assuming the problem is solved because the engagement metrics went up. They almost always go up. That's what engagement metrics do when you give students interactive technology. It tells you almost nothing about whether they learned.

**The Feynman test for this chapter:** Can you explain to someone else why Khan Academy's engagement data was misleading — not just that it was misleading, but the mechanism that produced the mismatch? If you can, you understand the measurement problem at the level this book requires.

---

## Connections Forward

This chapter established the problem and the architecture at a conceptual level. The next three chapters go inside each of the pieces.

Chapter 2 goes inside the Book Library and Tic TOC — how the concept node map is structured, how backward design actually works in practice, and what a Tic TOC session produces. The question Chapter 2 is built around: what does it mean to document instructional intent in a form that a system can use?

Chapter 3 goes inside the Adaptive Engine — the four modes in detail, the session logging architecture, and the specific design decisions behind the 1.5 → 2.0 transition. The question Chapter 3 is built around: what does a contextual bandit need to know before it can make a useful decision, and how do you build the experience that generates that knowledge?

Chapter 4 goes inside the Measurement Layer — the GLP framework in full, the neurobiological grounding for each component, and the causal graph program that will eventually produce validated estimates of the GLP weights. The question Chapter 4 is built around: what does "measuring learning" actually require, and how close are we?

If this chapter convinced you that the separation of AI work from human work is the right design principle, the next three chapters show you how that principle becomes an architecture. If this chapter raised questions you don't see answered, hold them — most of the hard questions are addressed in depth in what follows.

---

## A note about AI

Medhavy is being defined here as a platform — a substrate for thinking, working, and shipping. The model is part of the substrate. That makes the AI question different from the writing-craft AI question. You are not deciding whether to use the model. You are deciding what role the model plays inside an environment you built around it.

Where the model genuinely helps: drafting alternate definitions of the platform's purpose and pushing back on the one you wrote. The work of defining what a platform is for is largely the work of refusing distracting alternatives, and the model is useful as a generator of distractions you can name and reject.

Where the model does damage: producing the definition itself. A platform whose purpose was written by the model is a platform with no opinionated center, which is the failure mode every general-purpose platform shares.

The rule: the model can help you sharpen what you mean by Medhavy. It cannot tell you what Medhavy is for.

---

## Exercises

### Warm-Up

**1.1** The chapter names two failure modes in EdTech. For each one, write a single sentence that identifies (a) the error in assumptions and (b) the specific bad outcome that error produces. Do not quote the chapter — use your own words. *(Learning Objective 1)*

**1.2** MIT OpenCourseWare has had free lecture content available for over twenty years. Harvard and Stanford have similar programs. If content were the product education was selling, what outcome would you expect to see in enrollment at those institutions? What actually happened? What does the gap between prediction and outcome tell you about what the product actually is? *(Learning Objective 2)*

---

### Application

**1.3** A school district administrator tells you that their AI tutoring system is working because students spend 45 minutes per day on the platform and 87% complete their assigned lessons. Using the distinction between engagement metrics and learning evidence from this chapter, explain what the administrator knows from this data and what they don't. What evidence would you need to make a claim about learning? *(Learning Objective 4)*

**1.4** A professor is skeptical of Medhavy. Their concern: "If AI handles the explanation and the retrieval practice, students will never develop the struggle-through-difficulty capacity that comes from working with a human who pushes back." Using the conductor frame, explain how Medhavy's architecture addresses this concern — or honestly acknowledge where the concern might be valid. *(Learning Objective 3)*

**1.5** The chapter describes the Glimmer mode as building a term project "without the student knowing they're building it." What is the pedagogical purpose of this design decision? What problem does it solve? What risks does it introduce? *(Learning Objective 3)*

---

### Synthesis

**1.6** A colleague argues: "Medhavy is solving the wrong problem. The real issue in education is access — students who can't afford tuition, students in under-resourced districts, students for whom English is a second language. An adaptive learning system for professors at universities addresses none of this." Using the four-layer architecture, construct the strongest possible response to this critique. Then identify where the critique still has force even after your best response. *(Learning Objectives 1, 3)*

**1.7** The chapter claims that SUTVA — the Stable Unit Treatment Value Assumption — is "satisfied by design" in Medhavy's within-learner bandit architecture. Explain in plain language what SUTVA requires, why it is often violated in classroom experiments, and why Medhavy's design avoids the violation. *(Learning Objective 3)*

---

### Challenge

**1.8** The chapter is honest about what Medhavy doesn't know: the GLP weights, the bandit arm performance, whether content personalization produces durable gains. Design a research protocol — without building anything — that would allow you to answer one of these open questions. Specify: what you would measure, when, from whom, and what result would count as evidence that the question is answered. Be specific about what would count as a positive result and what would count as a negative one. *(Learning Objective 5)*

---

*Chapter 2: The Concept Map and the Curriculum →*


---

## AI Wayback Machine

**Sarvepalli Radhakrishnan** was Indian philosopher and statesman whose work on Indian philosophical traditions opened a global audience to texts that had been undervalued by Western academia.

**Run this:**

```
Who is Sarvepalli Radhakrishnan, and how does their work connect to platforms and Indian intellectual tradition we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Sarvepalli Radhakrishnan"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Sarvepalli Radhakrishnan's ideas to a specific platform decision.
- Add a constraint: "Answer including criticisms or limits of Sarvepalli Radhakrishnan's framework."

What changes? What gets better? What gets worse?

## Prompts

Use these prompts with Claude to generate interactive D3 v7 versions of the
figures in this chapter. Each produces a standalone HTML file you can open
in a browser and modify freely.

**Prerequisites:** Load `brutalist/CLAUDE.md` and `brutalist/DESIGN.md` into
your Claude project context before using these prompts. They define the stack,
naming conventions, color system, and typography the figures use.

---

### Figure 0.1 — Tic TOC session flow

Create a standalone D3 v7 HTML figure for "Tic TOC session flow". Use a horizontal process diagram with 4 to 5 ordered stages with directed connectors. Marks: rectangular stage nodes and arrow connectors. Channels: position for sequence or category, length for quantitative emphasis when bars are used, color for the primary highlighted item only, and direct text labels for accessibility. Use a zero baseline for quantitative bars. Include title, desc, role="img", aria-labelledby, ResizeObserver redraw, dark mode CSS variables, and reduced-motion safeguards. Deliver as one HTML file with inline CSS and the D3 7.9.0 CDN.

> Reference implementation: `d3/archive-01-what-is-medhavy-fig-01.html`

---

### Figure 0.2 — measurement hierarchy

Create a standalone D3 v7 HTML figure for "measurement hierarchy". Use a horizontal process diagram with 4 to 5 ordered stages with directed connectors. Marks: rectangular stage nodes and arrow connectors. Channels: position for sequence or category, length for quantitative emphasis when bars are used, color for the primary highlighted item only, and direct text labels for accessibility. Use a zero baseline for quantitative bars. Include title, desc, role="img", aria-labelledby, ResizeObserver redraw, dark mode CSS variables, and reduced-motion safeguards. Deliver as one HTML file with inline CSS and the D3 7.9.0 CDN.

> Reference implementation: `d3/archive-01-what-is-medhavy-fig-02.html`
