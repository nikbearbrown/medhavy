# Chapter 2 — What Is an Intelligent Textbook?

---

## Learning Objectives

By the end of this chapter, you will be able to:

1. **(Understand)** Explain why content was never the product education was selling — using the MIT OpenCourseWare experiment and the Khanmigo IDK-IDK data as the evidence.
2. **(Analyze)** Distinguish between the "no AI" failure mode and the "all AI" failure mode, and name the specific mechanism by which each produces worse outcomes than its proponents acknowledge.
3. **(Understand)** Describe the four-layer architecture of an intelligent textbook and explain why the integration of layers is the architecture, not the layers themselves.
4. **(Evaluate)** Identify which failure mode a given EdTech deployment represents, using the engagement-vs-learning distinction as the diagnostic.

**Prerequisites:** None technical. You should have a general awareness that AI is being deployed in education and that the people responsible for institutions are asking questions about whether any of it works.

---

## Where this fits the conductor frame

This chapter principally serves the learner — the first of the three questions, in the order Chapter 1 fixed. The IDK-IDK pattern is what failing Question 1 looks like when the engagement dashboard cannot see the failure. The instructor and the organization are present in the chapter, but only as the audiences that have been mistakenly served first in the field's typical deployments. Diagnosing those failures is what makes the learner-first ordering legible as an argument rather than a slogan.

What the chapter specifies for the conductor is the set of failure modes the conductor is conducting *against*. Two opposite errors — *no AI at all* and *all AI for everything* — produce the same downstream signature: the artifact looks right, the engagement metric registers, the cognitive work does not happen. Naming both failures, together, is the precondition for the conductor's instrument selection in later chapters; without that diagnostic, the conductor reaches for whatever the field defaults to.

The chapter runs the experiment by treating the IDK-IDK data and the MIT OCW finding as evidence about what the field has not yet measured well. The honest reading — that content was never the binding constraint and engagement was never the same thing as learning — is the open commitment the rest of the book will test. Transparency about the failure precedes any claim to a remedy.

---

## A student types "idk idk" into the most ambitious AI tutoring deployment in history

The student is somewhere in the United States. A district has rolled Khanmigo into the math curriculum. The student is sitting in front of a quadratic equation. Khanmigo asks, in the patient Socratic register the system was designed to maintain: *What do you think we'd compute first?* The student types *idk*. The system rephrases, lowers the abstraction, asks again. *Let's break this down. What's the discriminant?* The student types *i dont know*. The system tries a prerequisite recall move. *idk idk.* After three to five turns of this — sometimes more — Khanmigo leaks a more complete hint. The student copies. The student moves to the next problem.

The session log records the encounter. Time on platform: six minutes. Turns exchanged: eight. Problems attempted: one. From the engagement dashboard, the student is doing well. From the engagement dashboard, Khan Academy is doing well — the deployment grew from 40,000 students in 2023 to over 700,000 across 380+ district partners by the 2024–25 school year.[^1] From the engagement dashboard, the most ambitious AI tutoring deployment in history is a success.

In an interview made available through Dan Meyer's reporting in mid-2025, Khan Academy's Chief Academic Officer, Kristen DiCerbo, told the field what the rest of the data looks like:

> *"I will tell you, we see more 'IDK IDK,' more passive kinds of interaction than we would like."*[^2]

This is not a Khan Academy problem. It is a *measurement* problem the entire field shares. And it is not a problem about whether AI is good or bad. The same model — GPT-4, the same weights, the same temperature — can produce learning gains in the upper range of human tutoring effects in one wrapper and produce **seventeen percentage points of damage on a post-practice exam** in another.[^3] The variable is not the model. The variable is what the platform around the model is committed to.

Most platforms are not committed to anything in particular. That is the problem this book is about.

---

## Content was never the product

Before we name the failure modes, we have to defuse the move that lets both failure modes get committed at all. The move is this: *if I publish enough content cheaply enough, I have moved the needle on education.* That assumption has been load-bearing for two decades of EdTech, and it is wrong in a specific, documented, twenty-four-year-old way.

In April 2001, MIT President Charles M. Vest announced that MIT would publish virtually all of its course materials on the open web, free, for any user, for any purpose.[^4] The pilot launched in September 2002 with materials from 50 courses; by 2007 the platform reached the full MIT curriculum, over 1,800 courses. This was unprecedented in the residential-degree industry, where course materials had functioned as a partial moat around tuition revenue. The hypothesis, from inside and outside MIT, was that giving away the content would erode demand for the credential.

The opposite happened. By the time MIT ran its OCW user-survey work in the late 2000s, surveys of incoming MIT undergraduates were reporting that more than half were aware of OCW prior to choosing MIT, and roughly **one-third of those said OCW was a significant influence on their decision to attend MIT**.[^5] Applications did not collapse. They rose. Selectivity rose. MIT's brand became more, not less, valuable as the institution gave away what everyone had assumed was the moat.

(The "one-third" figure carries an institutional self-report caveat — both citations are MIT-internal, and there is no peer-reviewed third-party replication. The directional finding — *applications did not collapse and OCW became part of MIT's brand* — is uncontested. The exact share has the caveat.)

Why did this happen? Because the product MIT was selling — and selling at roughly $80K/year — was never the content. The content had been available, in textbook form and library form, for decades. What MIT sold was the experience: the labs, the cohort, the credentialing, the apprenticeship under faculty, the social graph that would later become the alumni network. OCW raised the *visibility* of the experience. Prospective students saw the materials. They concluded: *this is a place I want to be physically*. The signal MIT was emitting got louder when MIT gave away what everyone thought was the moat.

**The corollary is the part that matters.** If content was not the binding constraint of a college education, an intelligent textbook is not in the content-replacement business either. It is in the **experience-construction business**. The work it is doing is not "deliver the explanation cheaper than the textbook did." The work it is doing is "construct the experience around the explanation that produces durable learning evidence." Those are different products with different architectures.

I kept running into this fact as I was building Medhavy and for a long time I didn't quite know what to do with it. The obvious reading — *traditional universities survived disruption* — misses the point. The more accurate reading — *demand for what institutions still do uniquely went up* — is the framing the entire rest of this book is built on. The intelligent textbook lives in the part of the institution that survived the content-disintermediation experiment. If you do not have a working theory of what that part *is*, you will build a textbook that solves the wrong problem and report engagement numbers as if you had solved the right one.

(A narrow reading of the OCW finding: MIT is a luxury good, and luxury goods do not lose price elasticity by giving away parts. That reading is fair. The argument here extends only to the claim that *content* is not the binding constraint of high-quality education; it does not extend to claims about institutions whose value is signaling-dominated. The intelligent textbook is not in the signaling business.)

---

## The no-AI failure mode: irreducibly human work crowded out by accident

There are two ways to get the role of AI in education wrong, and the field has managed to commit both simultaneously, in opposite directions. The first failure mode is *no AI at all*. It is the failure Jared Cooney Horvath catalogs cleanly in *The Digital Delusion*[^6], and it is also the failure I have been writing about from inside the classroom for a year in the *Trust the Teacher* essays. It is the failure that happens when a professor absorbs the automatable work because there is no architecture to take it on, and the irreducibly human work gets crowded out by accident, not by design.

The shape is unglamorous, which is why it has been hard to see. A professor of clinical pharmacology spends the first two weeks of every semester re-explaining beta-blocker mechanism to the new cohort. She has done it for fifteen years. The explanation is good. By week three she grades 120 short-answer questions on beta-blocker mechanism, indistinguishable from the 120 from last year. By week six she is writing the next iteration of the case study for the cardiology block. By the end of the semester, she has spent her six most senior cognitive hours on work that an Anki deck, a grading rubric, and a CBL case template would have absorbed at roughly $0.40 in OpenAI tokens.

What did the professor not do during those six hours? She did not run the Socratic ambiguity exercise on the second-year student whose differential diagnosis was technically right but whose reasoning had a structural gap she was the only person in the building who could see. She did not call the student whose oncology rotation she had heard had gone sideways. She did not write the IRB amendment that would have let her involve the third-year students in the new study. She did not sit with the new resident over coffee.

The work that is *only* available because she is in the building, with her judgment, her relationships, her authority, and her time — **that** work got crowded out by the work that an algorithm could have done.

This is the irreducibly-human displacement my *Trust the Teacher* essays make from inside the classroom. The micro-mechanism is precise: when a teacher's marginal hour is committed to work AI can do nearly as well, the teacher's *highest-leverage hour* — the hour AI cannot do — gets squeezed out. The squeezing happens by accident. Nobody chose it. The professor would prefer to spend her six hours on Socratic work. The structural reality of her job — short-answer grading, lecture re-recording, case construction — selects for the work that fits in her queue.

Horvath catches the symptom — test scores dropping after indiscriminate EdTech rollouts; the PISA correlation between heavy device use and lower math scores; the smartphone-in-the-classroom distraction effect — and assigns the cause to *the technology* or *the AI*. The closer diagnosis: the AI is doing the wrong subset of the teacher's job because the platform that delivered it did not know which subset to give it, and did not know how to give the rest *back to the teacher*. The hammer problem Horvath catches is real. Horvath then proposes putting the hammer down. The Medhavy thesis: it isn't a hammer being misused; it is a hammer being held by an architecture that didn't notice the wood needed sawing too.

This is the no-AI failure mode in one sentence: **the most valuable thing a teacher can do for a student is the thing most vulnerable to being eaten by the least valuable work the teacher has to do.** Refusing the AI doesn't solve this. It accelerates it.

---

## The all-AI failure mode: chatbot as relationship, IDK-IDK as engagement

The second failure mode is the opposite. EdTech has a long and unfortunate tradition of claiming the AI can be the teacher — replace the lecture, replace the mentor, replace the relationship. The implicit argument underneath most of the platforms that have raised significant capital in the past decade: *if we can deliver content cheaply at scale, we have solved education.* Sal Khan, on the 2023 TED stage, called AI *"probably the biggest positive transformation that education has ever seen."* The platform behind that claim, Khanmigo, was Khan Academy's AI tutor — a Socratic dialogue system designed to guide students to answers rather than give them directly. Khan's book *Brave New Words* (2024) is the long-form case.

Three years later, Khan Academy's own Chief Academic Officer described what the usage data was actually showing. The IDK-IDK pattern. The Socratic guardrail leaking under student pressure — Common Sense Media's review of Khanmigo notes that *"persistent prompting would lead to Khanmigo offering a more complete answer."*[^7] Sal Khan himself has now publicly acknowledged that Khanmigo *"has failed to catch on with students."*[^8]

The mechanism is precise. A student opens the tutor. They get a problem. They get a Socratic prompt. They type *"i dont know."* The system rephrases, lowers the abstraction, asks again. The student types *"idk."* The system tries the prerequisite recall move. *"idk idk."* Under the gentle persistence the system is designed to maintain, the model leaks the answer or a more complete hint. The student copies. The student moves to the next problem. The session log records: time on platform, turns exchanged, problems attempted, problems completed.

From the dashboard view, this student is **engaged**. From the learning view — durable retention, transfer to novel problems, the seven friction components of the GLP framework Chapter 5 will detail — this student has done close to zero work.

We are not guessing about the magnitude of this failure. The Bastani et al. 2025 PNAS finding is the cleanest empirical confirmation in the literature. In a Turkish high school RCT — roughly 1,000 students, grades 9–11, math practice sessions — researchers ran three conditions: a no-AI control, a "GPT Base" condition with a standard ChatGPT-style chat interface, and a "GPT Tutor" condition with a teacher-designed prompt wrapper that injected hints and refused to give complete answers. The underlying model was the same in both AI conditions.

During practice, with AI access, the GPT Base group performed 48% above the no-AI control. The GPT Tutor group performed 127% above the control. Both numbers look like wild success. On the post-practice exam, *without* AI access, the GPT Base group scored **17 percentage points lower** than the no-AI control. The GPT Tutor group was statistically indistinguishable from control.[^3]

Read those numbers again. In-session, the students felt smarter, performed better, looked engaged. On the durable-learning measure, the unguarded condition produced roughly half a standard deviation of *damage* relative to no AI at all. *Not* "AI is mildly suboptimal." Unguarded AI in that context made students substantially worse than they would have been without it. The wrapper that prevented the damage was a teacher-designed system prompt enforcing hints-not-answers. The model didn't change. The opinions did.

**The structural error in both Khan and Horvath is the same error**: both are using engagement-related metrics as the binding outcome variable. Khan reads engagement growth (40K → 700K students, 380+ districts) as success. Horvath reads engagement-correlated harm (PISA score declines at high digital-device dosage) as failure. They've made the same measurement choice. They've reached opposite conclusions from it. Neither is asking the question: *what would a measurement layer that captured learning instead of engagement actually tell us about either deployment?*

---

## The third position: what taking all the evidence seriously demands

The third position is not a Solomon-split between Khan's optimism and Horvath's pessimism. It is not *"they're both half right."* It is the refusal of the shared measurement error.

Here is the specific commitment that produces it: **build the measurement infrastructure first, then let the architecture follow from what the measurement reveals.** This is the move Bogatz & Ball made for Sesame Street in 1969–1971. They built the assessment instrument first, designed the show against measurable readiness skills, then ran the trial. Mares & Pan's 2013 fifteen-country meta-analysis put the cognitive-outcomes effect at *d* = 0.29, at roughly $5 per child per year reaching about 156 million children annually.[^9] The Sesame Street machinery is not an AI deployment. It is the canonical example of what high-quality educational media — *measured before claimed, optimized over decades, scaffolded around a stable curricular target* — is capable of. The intelligent textbook field has spent fifty-five years failing to repeat that move.

The third position starts there. It says: *the question is not whether AI in education helps or harms. The question is what would you have to build if you took all the evidence seriously — the Khanmigo failure data, the Bastani PNAS finding, the ITS literature, the spaced-repetition canon, the case-based learning evidence, the generative-assignment evidence, the smartphone-distraction literature, the Sesame Street precedent. All of it. What architecture falls out?*

The answer this book elaborates is a four-layer architecture. I'm going to sketch it here, briefly, the way a builder sketches a foundation on a napkin before the drawings exist. The full architecture is Chapters 4 through 10. Chapter 5 — the load-bearing chapter on the measurement layer — is the one downstream chapters depend on most. What follows is the napkin.

---

## The four-layer architecture (a sketch — Chapters 4–10 deliver it)

The intelligent textbook has four layers. Each layer answers a different question. None of them does anything useful in isolation. **The integration is the architecture.** That is the load-bearing claim.

**Layer 1 — the Book Library.** What is the domain-specific content the student is engaging with? At what grain does that content meet the actual task? The book library answers: *what is this textbook teaching, and is it teaching it at the right level of specificity?* The Sadler 2013 "Level-3 specificity" finding[^10] — that pedagogical content knowledge is domain-particular in ways generic instructional design ignores — lives in this layer.

**Layer 2 — Tic TOC, the curriculum design layer.** What are the concept dependencies, the prerequisite chains, the phase gates? Most professors received no formal training in curriculum design. This is not a criticism; it is a structural fact about how academic careers are built. Backward design — start from what students should be able to do, work backward to what evidence demonstrates the capability, then to the instruction and sequence — is rare in practice. Tic TOC is the instrument that produces it. The layer answers: *in what order does the student encounter the material, and what must they have mastered before encountering this concept?*

**Layer 3 — the Adaptive Engine.** What mode does the student see for this concept at this moment? *Ask AI* — context-anchored explanation, hints only. *Quiz Me* — spaced retrieval practice. *Case Study* — pre-written, faculty-reviewed CBL. *Glimmer* — generative, ill-structured, scaffolded assignment. The engine is a within-learner contextual bandit, not a global "best mode" pick. The layer answers: *what intervention is right for this learner, on this concept, given what we have observed about this learner's state?*

**Layer 4 — the Measurement Layer.** What is the engine actually optimizing for? *Not* engagement — time on platform, clicks, turns, completions. *Learning evidence.* The Genuine Learning Probability (GLP) framework Chapter 5 specifies in full: seven friction components — temporal engagement pattern, error trajectory coherence, cross-context transfer, uncertainty calibration, social knowledge texture, retrieval strength decay, scaffolding response curve. The layer answers: *what does this student now know, and how well do we trust the answer?*

The Khanmigo failure, in this frame, is **a missing measurement layer in disguise**. The engine was optimizing for engagement because that was what it could see. Give it a measurement layer that distinguishes engagement from learning, and the same Socratic-tutor design produces a different signal — *this student spent six minutes typing "idk" and copying hints; the durable-learning estimate for this session is near zero* — and a different downstream behavior.

The integration is what makes this an architecture. None of the four layers does anything useful in isolation. A book library without a Tic TOC is a corpus. A Tic TOC without an adaptive engine is a static curriculum. An adaptive engine without a measurement layer is the IDK-IDK trap — a system optimizing for the wrong thing, very confidently, very efficiently. A measurement layer without a book library is an instrument with nothing to instrument.

I am sketching here, not building. Chapters 4 through 10 do the building.

---

## The platform is opinionated. The model has no opinions of its own.

This is the chapter's load-bearing line. It is also the line the rest of the book either earns or fails to earn. The decomposition:

**The model has no opinions.** Underneath every chatbot mode in the architecture is a frontier LLM — GPT-4o, Claude Sonnet, Gemini 2.5, the next one. The model is willing to be Socratic, willing to be didactic, willing to give the answer, willing to refuse to give the answer. The same model can produce the Bastani GPT Base outcome (–17 percentage points) or the Bastani GPT Tutor outcome (parity with control). The variable is not the model. It is the wrapper — the system prompt, the context-injection discipline, the phase-gate logic, the mode selection rule. The model is a willing actor with no opinions of its own.

**The platform is opinionated.** The platform makes the pedagogical commitments that decide what the model does in any given moment. The opinions are visible in the design: *retrieval practice before re-reading. Generative work before extractive work. Case study after representation, not before. Socratic moves only when prerequisites are in place. Scaffolding fades on a measurable response curve. The answer is never given before the student has externalized their reasoning step.* These are not the model's preferences. They are the platform's commitments — and the place where the evidence base of Chapter 3 actually gets deployed.

**The corollary.** A platform with no opinions — a chatbot wrapper whose system prompt says "be a helpful tutor" and otherwise lets the model decide — defaults to the model's training-distribution average behavior, which is the Bastani GPT Base condition. The model's "average tutor" produces –17 percentage points. *A platform without opinions is a platform that will reliably reproduce that outcome.*

You can hold this in one sentence: **the platform is opinionated; the model has no opinions of its own.** Everything in the rest of the book is the elaboration of those opinions and the architecture that makes them operational.

---

## Worked example: the engagement dashboard vs. the learning-evidence dashboard

Let me walk through what each dashboard would have shown for the IDK-IDK incident. Same student. Same six minutes. Two completely different reads.

*Illustrative case. The student is a composite drawn from Khan Academy's own usage descriptions and Common Sense Media's published review; the dashboard contents are constructed to make the comparison legible.*

**What the engagement dashboard showed.** Time on platform: 6 minutes. Turns exchanged with Khanmigo: 8. Problems attempted: 1. Problems "completed" (the student moved on without abandoning the session): 1. Mode used: Socratic dialogue. Daily active: yes. Streak: maintained. From this dashboard, the session is a success. Aggregated across hundreds of thousands of students, the dashboard reports 40K → 700K growth, 380+ district partners, four-star Common Sense Media rating.[^7] The dashboard is doing the job it was built to do.

**What a learning-evidence dashboard would have shown.** Take the seven GLP components Chapter 5 will specify, and ask what each one would register for this session:

| GLP component | What the session shows | Reading |
|---|---|---|
| Y1 Temporal Engagement | Minimal externalization; no scaffolding climb | Near-zero learning signal |
| Y2 Error Trajectory | No errors generated — the student never committed to an answer the system could evaluate | No coherent arc; nothing to update on |
| Y3 Cross-Context Transfer | Untestable — nothing was encoded to transfer | Undefined |
| Y4 Uncertainty Calibration | *"idk"* is meta-cognitive information the system did not exploit | Information left on the floor |
| Y5 Social Knowledge | No peer, teacher, or expert contact in the session | Absent |
| Y6 Retrieval Strength Decay | No encoding occurred; decay is not the right measure | Not applicable |
| Y7 Scaffolding Response | System offered scaffolding; student did not climb the ladder | Negative signal |

Composite GLP for this session: **near zero**.

The gap between the two dashboards is the chapter's diagnostic. **Engagement dashboard says success. Learning-evidence dashboard says zero.** That gap is the IDK-IDK failure. The system that produced it was the most ambitious AI tutoring deployment in history. Charles Fadel readers know this case in the abstract; you now know it in the specific.

This is the chapter's meta-lesson. *Every* deployment in this space has an engagement dashboard. *Almost no* deployment in this space has a learning-evidence dashboard. The architecture this book describes exists, in substantial part, to make the second dashboard possible. Until it is possible, every claim about "AI in education works" or "AI in education fails" is a claim about the engagement dashboard. The honest answer to either claim is *we are measuring the wrong thing*.

---

## Common misconceptions

Three readings the chapter wants to head off before the architecture chapters.

**Misconception 1: "If AI tutoring doesn't work, just don't use AI tutoring."**

Plausible. The Bastani GPT Base finding is real. The Khanmigo IDK-IDK failure is real. The PISA correlations are real. If unguarded AI in classrooms produces durable damage, the cleanest move is to refuse the AI entirely. Why isn't that the answer?

Because the no-AI failure mode is also real. *Trust the Teacher* documents what happens when the professor absorbs the automatable work and the irreducibly human work gets squeezed out: not by ideology, but by the structure of the queue. Refusing AI doesn't restore the high-leverage hour. It just leaves the short-answer-grading hour in place, and the high-leverage hour gets eaten anyway. The "just don't use AI" position only works if you can show the no-AI status quo is producing the irreducibly human work at scale. It isn't. Horvath catches the symptoms of the all-AI failure and prescribes a treatment that does not address the no-AI failure he himself documents.

**Misconception 2: "The Bastani finding shows AI is bad, full stop."**

Plausible. The –17 percentage point figure is large. The temptation is to read it as a verdict on AI tutoring as a category. The full reading is sharper. *Same model, two wrappers, opposite outcomes.* The GPT Tutor condition — same GPT-4 underneath — produced parity with the no-AI control. The Kestin et al. 2025 Harvard physics RCT, with a research-designed AI tutor, produced effect sizes of *d* ≈ 0.7–1.3 against in-class active learning.[^11] The finding is not "AI is bad." It is: **the wrapper is the variable, and most deployments are running the unguarded wrapper.** The architecture this book describes is the specification of a non-unguarded wrapper.

**Misconception 3: "MIT OCW proves content can be free without harming institutions; therefore AI tutoring will go the same way."**

Plausible-adjacent and wrong. OCW substituted content for content (textbook → online lecture notes) without claiming to substitute experience for experience. An AI tutor *does* claim to substitute experience for experience — the chatbot replaces the office-hours conversation, the patient tutor, the curious peer. That is a different kind of claim. The MIT OCW evidence undercuts the *content* version of educational disintermediation; it has nothing direct to say about the *experience* version. Reading the OCW outcome as a green light for AI tutoring is the same category error that lets vendors cite the ITS literature to support generative-AI deployments. They are different literatures.

---

## Exercises

### Exercise 1.1 — Classify the failure mode (Apply)

You read about a high school district that has rolled out an AI tutoring platform. The dashboard reports: average 22 minutes per student per day on the platform; 84% of assigned modules completed; student satisfaction survey at 4.1/5. The district reports the deployment as a success. The state-administered standardized math assessment, six months later, shows scores down 0.18 standard deviations relative to the pre-deployment baseline cohort.

Write a one-page memo for the district superintendent that does three things: (a) classifies which failure mode this represents — *no AI*, *all AI*, or *neither* — and names the specific architectural decision that produced the outcome; (b) identifies the measurement choice that produced the gap between the dashboard and the assessment; (c) names two diagnostic questions the district should ask the vendor before renewing the contract.

### Exercise 1.2 — Build the two dashboards (Analyze, produces something)

Take the IDK-IDK incident from the chapter. Construct two artifacts:

(a) A one-page **engagement dashboard** that a Khan Academy-style platform might publish about this student's session. Include at least six metrics. Make the dashboard look like a success.

(b) A one-page **learning-evidence dashboard** that the same session would produce under the GLP framework sketched in this chapter. Include all seven GLP components. Show what each component registers.

In a closing paragraph (~150 words), name the *single* design decision that produces the gap between the two dashboards.

### Exercise 1.3 — The MIT OCW counterfactual (Evaluate)

The chapter argues that MIT OpenCourseWare increased applications rather than collapsing them, and uses this to claim that content was never the binding constraint of a college education.

Write a 500-word evaluation that does three things: (1) states the strongest narrow reading of the OCW finding that does *not* extend to "content is not the product" (the chapter offers one — the luxury-good reading; you may offer others); (2) names one specific kind of educational institution where the OCW evidence is most likely to generalize, and one where it is least likely; (3) identifies one piece of evidence that, if it appeared, would force you to revise the chapter's central reading of OCW.

---

## What would change my mind

The chapter's central claim is that the right question is not whether AI in education helps or harms — it is *what would you have to build if you took all the evidence seriously*, and the answer is a four-layer architecture organized around learning measurement rather than engagement measurement. Three findings would force me to revise:

A rigorous, independently-evaluated, multi-site RCT of an unsafeguarded Khanmigo-style generative-AI tutor — *N* in the thousands, durable learning outcomes on transfer-bearing assessments at delay, no measurement-layer instrumentation — that produced gains of *d* > 0.4. That would suggest the architecture commitment is not necessary: engagement alone would be sufficient. A failure of the Bastani PNAS finding to replicate across five attempts in different countries, age groups, and subject domains would substantially weaken the wrapper-as-variable claim that the architecture rests on. Or: evidence that bolt-on tools (LMS + chatbot + Anki + case library) produce equivalent learning outcomes to integrated platforms under the same GLP framework. The book bets integration is doing real work; if integration turns out to be a vanity, the central architectural claim is wrong.

---

## Still puzzling

1. If engagement is not learning, why is engagement so persistent as the dominant outcome metric? The institutional answer — *engagement is cheap to measure, learning is expensive* — is true but incomplete. There is a deeper economic reading: engagement is what platforms can *sell* to districts, and learning is what districts cannot purchase without an instrument they do not yet have. Chapter 1 does not resolve this; Chapter 10 returns to it.

2. Why did MIT OCW not trigger the wave of content-disintermediation imitation that commentators predicted? Twenty-four years on, content moats in higher education are still partly intact. The cleanest reading is that institutions learned to compete on the *experience layer*. A more interesting reading is that the institutions that didn't learn this are quietly in trouble and the rest of the field has not yet noticed.

3. Is the four-layer architecture stable across domains? The illustrative case is Medhavy's cancer textbook — high-stakes, high-feedback. Does the same architecture work for a humanities seminar where the right answer is contested and "uncertainty calibration" is doing different conceptual work than it does for clinical pharmacology? The book bets yes. Chapter 11 returns to this honestly.

4. What if the IDK-IDK pattern is not a Khan Academy implementation problem but a deeper property of how students *adapt* to any unsafeguarded chatbot — a strategy the GPT Tutor wrapper merely delays rather than prevents? If so, the architectural commitment to phase-gated externalization may need to be stronger than the chapter argues.

---

## Bridge to Chapter 2

You now have the failure modes named, the third position introduced, and the four-layer architecture sketched. The natural next move would be to specify the architecture in detail.

We are not going to do that yet. Before we specify the architecture, we have to do an honest check: **for some learning problems, the right answer is a simpler tool, not the full architecture.** The four-layer architecture is expensive — in design time, in instrumentation, in cognitive load — and shipping it into a learning problem that does not need it is, in the most literal sense, malpractice. Chapter 2 introduces the **complexity threshold test** — three questions that tell you whether the architecture earns its cost on a given problem — and the case that motivates it: Priya, 19, six years in a Homes of Hope residence in Hyderabad, needing job-functional English for a BPO interview. For Priya, Anki is enough. Not because the architecture is too expensive for her circumstances. Because the *structure of her learning problem* does not require it.

Chapter 3 then delivers the evidence base that every architecture chapter will cite. Chapter 4 begins the architecture proper.

If you are tempted to skim Chapter 2 because you already know the architecture is the right answer for your problem — pause. The complexity threshold test exists because the structural error to prevent is *not* over-skepticism. It is over-deployment. EdTech vendors will read Chapter 1 and decide their next product needs all four layers. Chapter 2 is the discipline that says: *not always, and here is how to know.*

**The platform is opinionated. The model has no opinions of its own.** That sentence is the entire book. Everything that follows is the elaboration.

---

## References

[^1]: Khan Academy. (2024). *Khanmigo Efficacy Results, November 2024*. Khan Academy Blog. https://blog.khanacademy.org/khan-academy-efficacy-results-november-2024/

[^2]: DiCerbo, K. (2025). Quoted in Meyer, D. *RIP Khanmigo and EdTech Industry Dreams of AI Tutors*. Dan Meyer Substack. https://danmeyer.substack.com/p/rip-khanmigo-and-edtech-industry [verify — primary venue likely EdSurge or Education Next 2024–2025 interview; quote consistent across Meyer, itutorsoft, CompleteAI Training]

[^3]: Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., & Mariman, R. (2025). Generative AI without guardrails can harm learning: Evidence from high school mathematics. *Proceedings of the National Academy of Sciences*, 122(26), e2422633122. https://doi.org/10.1073/pnas.2422633122

[^4]: MIT News. (2001, April 4). *MIT to Make Nearly All Course Materials Available Free on the World Wide Web*. https://news.mit.edu/2001/ocw

[^5]: D'Oliveira, C., & Lerman, S. *MIT OpenCourseWare: From 2001 to 2011*. MIT Faculty Newsletter. https://web.mit.edu/fnl/volume/221/d'oliveira_lerman.html. See also MIT OCW. (2011). *Evaluation Summary 2011*. https://ocw.mit.edu/about/site-statistics/11_Eval_Summary_112311_MITOCW.pdf [MIT-internal self-report — directional claim uncontested; specific share has institutional-self-report caveat]

[^6]: Horvath, J. C. (2025). *The Digital Delusion: How EdTech Has Failed Our Schools — and How to Fix It*. [Publisher and exact pagination [verify] before final draft.]

[^7]: Common Sense Media. *Khanmigo AI Rating*. https://www.commonsensemedia.org/ai-ratings/khanmigo

[^8]: Khan, S. (2025). Quoted in *Sal Khan acknowledges Khanmigo "has failed to catch on with students"*. CompleteAI Training. https://completeaitraining.com/news/sal-khan-says-his-ai-tutoring-chatbot-has-failed-to-catch/

[^9]: Mares, M. L., & Pan, Z. (2013). Effects of Sesame Street: A meta-analysis of children's learning in 15 countries. *Journal of Applied Developmental Psychology*, 34(3), 140–151.

[^10]: Sadler, P. M., Sonnert, G., Coyle, H. P., Cook-Smith, N., & Miller, J. L. (2013). The influence of teachers' knowledge on student learning in middle school physical science classrooms. *American Educational Research Journal*, 50(5), 1020–1049.

[^11]: Kestin, G., Miller, K., Klales, A., Milbourne, T., & Ponti, G. (2025). AI tutoring outperforms in-class active learning: An RCT introducing a smart learning companion. *Scientific Reports*, 15. https://www.nature.com/articles/s41598-025-97652-6

---

*Chapter 2: When Anki Is Enough →*
