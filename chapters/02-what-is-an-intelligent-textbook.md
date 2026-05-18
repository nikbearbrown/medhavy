# Chapter 2 — What Is an Intelligent Textbook?

*The engagement dashboard said success. The student learned nothing.*

---

There is a fact about MIT that I find genuinely strange, and I want to start there because it tells you something important about what education actually is.

In April 2001, MIT announced it would publish virtually all of its course materials on the open web — lecture notes, problem sets, syllabi, exams — free, for anyone, forever. The pilot launched with 50 courses. By 2007 it covered the full MIT curriculum, over 1,800 courses. The people running the residential-degree industry watched this and predicted the obvious: giving away the content would erode demand for the credential. Why pay $80,000 a year for something you can get for free?

The opposite happened. Applications went up. Selectivity went up. MIT's brand became *more* valuable as the institution gave away what everyone had assumed was the moat. Surveys of incoming undergraduates found that more than half were aware of OpenCourseWare before choosing MIT, and roughly a third said it was a significant influence on their decision to attend.

<!-- → [INFOGRAPHIC: Timeline of MIT OCW from 2001 pilot (50 courses) to 2007 full curriculum (1,800+ courses), with MIT application volume indexed alongside — reader should see the two lines moving in the same direction, not opposite ones. Caption should name the counterintuitive result explicitly.] -->

Stop and think about what this means. The content was never the product. It had been available in textbook and library form for decades. What MIT was selling — at $80,000 a year — was the experience: the labs, the cohort, the apprenticeship under faculty, the social graph. OpenCourseWare *raised the visibility* of that experience. Prospective students looked at the course materials and concluded: this is a place I want to be, physically. The signal got louder when MIT gave away what everyone thought was the moat.

I kept running into this fact while building Medhavy and for a long time I did not quite know what to do with it. The obvious reading — *traditional universities survived disruption* — misses the point. The more accurate reading is: demand for what institutions still do uniquely went *up*. And the corollary, which is the thing I actually needed to understand, is this: an intelligent textbook is not in the content-replacement business. It is in the experience-construction business. Those are different products with different architectures. If you do not have a working theory of what the experience layer *is*, you will build a textbook that solves the wrong problem and then report engagement numbers as if you had solved the right one.

That last sentence is not abstract. It is what is happening right now, across the field, in two opposite directions simultaneously.

---

## The two failures

There are two ways to get the role of AI in education wrong, and the field has managed to commit both at once.

The first is no AI at all. Not because the technology is refused on principle — though sometimes it is — but because the structure of the job quietly selects against it. A professor of clinical pharmacology spends the first two weeks of every semester re-explaining beta-blocker mechanism to a new cohort. She has done it for fifteen years. By week three she grades 120 short-answer questions on beta-blocker mechanism, indistinguishable from last year's 120. By week six she is writing the next iteration of the case study for the cardiology block.

What did she not do during that time? She did not run the Socratic ambiguity exercise on the second-year student whose differential diagnosis was technically correct but whose reasoning had a structural gap that she — specifically she, with her fifteen years and her knowledge of that student — was the only person in the building who could see. She did not call the student whose oncology rotation had gone sideways. She did not sit with the new resident over coffee.

The work that is only available because she is in the building, with her judgment and her relationships and her time — that work got crowded out by work an algorithm could have done for roughly forty cents in API tokens. Nobody chose this. The short-answer grading, the lecture re-recording, the case construction — they fit in her queue. The Socratic work does not fit in a queue. It gets eaten.

<!-- → [IMAGE: Two-column diagram — left column "Work that fits in a queue" (short-answer grading, lecture re-recording, case template construction, annotated bibliography), right column "Work that only exists because she is in the room" (Socratic ambiguity exercise, recognizing structural gap in a student's reasoning, the call after a rotation goes sideways, coffee with the new resident). Visual weight should favor the right column. Caption: the queue selects for the left column, which crowds out the right.] -->

This is the failure I have been writing about in the *Trust the Teacher* essays. The micro-mechanism: when a teacher's marginal hour is committed to work AI can do nearly as well, the teacher's highest-leverage hour — the hour AI genuinely cannot do — gets squeezed out. The technology is irrelevant. The structural problem is real with or without it. Refusing AI does not solve this. It accelerates it.

The second failure is the opposite, and it is the one currently raising capital. The implicit argument underneath most EdTech platforms of the past decade: if we can deliver content cheaply at scale, we have solved education. The AI tutor is the platform, the Socratic dialogue is the feature, the engagement dashboard is the evidence. Sal Khan, on the 2023 TED stage, called AI probably the biggest positive transformation that education has ever seen. Khanmigo was the deployment. By 2024–25 it was in 380+ district partnerships, serving over 700,000 students. From the engagement dashboard, this is a success.

Then Khan Academy's Chief Academic Officer, Kristen DiCerbo, described what the rest of the data looks like:

> *"I will tell you, we see more 'IDK IDK,' more passive kinds of interaction than we would like."*[^2]

Here is what IDK IDK looks like. A student opens the tutor. A quadratic equation appears. Khanmigo asks, in its patient Socratic register: *What do you think we'd compute first?* The student types *idk*. The system rephrases, lowers the abstraction, asks again. *Let's break this down. What's the discriminant?* The student types *i dont know*. The system tries a prerequisite recall move. *idk idk.* After three to five turns of this, Khanmigo leaks a more complete hint. The student copies. The student moves to the next problem.

Session log: time on platform, six minutes. Turns exchanged, eight. Problems completed, one. The engagement dashboard records a success.

<!-- → [TABLE: The IDK IDK session reconstructed as two dashboards side by side — left: "Engagement Dashboard" (time on platform: 6 min ✓, turns exchanged: 8 ✓, problems completed: 1 ✓, streak maintained: yes ✓, daily active: yes ✓), right: "What actually happened" (student never committed an answer the system could evaluate, model leaked hint under pressure, student copied and advanced, zero externalized reasoning, GLP estimate: near zero). The contrast should be visually stark — both sides populated, same session, opposite stories.] -->

The student learned nothing.

---

## The same model, two different wrappers

Here is the part that matters most, and the part that is hardest to hold onto when you are looking at a platform demo.

In 2025, Hamsa Bastani and colleagues published a randomized controlled trial in *PNAS* — roughly 1,000 Turkish high school students, grades 9–11, math practice sessions. Three conditions: a no-AI control, a standard ChatGPT-style chat interface they called GPT Base, and a tutor-designed wrapper with injected hints that refused to give complete answers, which they called GPT Tutor. The underlying model was the same in both AI conditions.[^3]

During practice, with AI access, the GPT Base group performed 48% above the no-AI control. The GPT Tutor group performed 127% above the control. Both numbers look like success.

On the post-practice exam — *without* AI access — the GPT Base group scored 17 percentage points *lower* than the no-AI control.

<!-- → [CHART: Bar chart with three grouped pairs — "During practice (with AI)" and "Post-practice exam (without AI)" for each condition: No-AI control (baseline 0% / baseline 0%), GPT Base (+48% during / –17% post), GPT Tutor (+127% during / ~0% post). The GPT Base post-practice bar should go below the baseline — visually below zero — so the reversal is impossible to miss. Caption: same model, same students, opposite outcomes. The variable is the wrapper.] -->

Read that again. In-session, the students felt smarter, performed better, looked engaged. On the durable-learning measure, the unguarded condition produced roughly half a standard deviation of damage relative to no AI at all. Not "AI is mildly suboptimal." Unguarded AI made students substantially worse than they would have been without it.

The GPT Tutor group was statistically indistinguishable from the control. Parity. The wrapper that prevented the damage was a teacher-designed system prompt that enforced hints, not answers. The model did not change. The wrapper did.

This is the load-bearing empirical fact of this book, and I want to be honest about its limits before I build on it: this is one study, one country, one subject domain, one age group. The finding needs replication. What it cannot be explained away as is a fluke of implementation quality or a bad AI product — the GPT Base condition used the same model that produced near-zero damage in the GPT Tutor condition. The variable is the platform's commitments. The model had none of its own.

The Kestin et al. 2025 Harvard physics RCT confirms the direction, if not the magnitude: a research-designed AI tutor produced effect sizes of $d \approx 0.7$–$1.3$ against in-class active learning.[^11] Same architecture logic. The wrapper is doing the pedagogical work. The model is a willing actor with no opinions of its own.

---

## The measurement error both sides share

Jared Cooney Horvath's *The Digital Delusion*[^6] catalogs real symptoms: test scores dropping after indiscriminate EdTech rollouts, PISA correlations between heavy device use and lower math scores, the smartphone-in-the-classroom distraction effect. He reads these as evidence that AI in education fails. Sal Khan reads growth from 40,000 to 700,000 students as evidence that AI in education works. They have reached opposite conclusions from the same measurement choice.

Both are using engagement-related metrics as the binding outcome variable. Khan reads engagement growth as success. Horvath reads engagement-correlated harm as failure. Neither is asking: *what would a measurement layer that captured learning instead of engagement actually tell us about either deployment?*

This is the structural error the chapter wants to name precisely, because it is what makes both failures invisible until it is too late. The engagement dashboard is not wrong about what it measures. It is measuring the wrong thing. And the gap between what it measures and what matters is exactly the IDK IDK gap — a student spending six minutes typing *idk* and copying hints, recorded as a successful session, because the system has no instrument for anything else.

The OCW experiment tells you content was never the binding constraint. The Bastani finding tells you the wrapper is the variable. These two facts together tell you what an intelligent textbook has to be: not a content delivery system, and not an engagement engine. It has to be a system that takes pedagogical positions. Opinions, in the code. Commitments, in the architecture.

---

## What "opinionated" means here

The platform is opinionated. The model has no opinions of its own.

Underneath every chatbot mode in the architecture I'm describing is a frontier LLM — GPT-4o, Claude Sonnet, the next one. The model is willing to be Socratic, willing to be didactic, willing to give the answer, willing to refuse. The same model that produced –17 percentage points in the Bastani GPT Base condition can produce parity or better in the GPT Tutor condition. The variable is the system prompt, the context-injection discipline, the phase-gate logic, the mode selection rule. The model is a willing actor with no opinions of its own.

The platform's opinions are visible in the design. Retrieval practice before re-reading. Generative work before extractive work. Case study after representation, not before. Socratic moves only when prerequisites are in place. The answer is never given before the student has externalized their reasoning step. Scaffolding fades on a measurable response curve. These are not the model's preferences. They are the platform's commitments, and they are where the evidence base actually gets deployed.

A platform with no opinions defaults to the model's training-distribution average behavior — which is the Bastani GPT Base condition. The model's average tutor produces –17 percentage points. *A platform without opinions will reliably reproduce that outcome.*

---

## The four-layer sketch

What does an opinionated platform look like, architecturally? I want to sketch it here the way you sketch a foundation on a napkin — rough, before the drawings exist. Chapters 4 through 10 build it properly.

Four layers. Each answers a different question. None of them does anything useful in isolation.

**The Book Library** answers: *what is this textbook teaching, at what grain?* The domain-specific content, structured at the level where it meets the actual learning task. The Sadler 2013 finding that pedagogical content knowledge is domain-particular in ways generic instructional design ignores lives here.[^10] A corpus without the next layer is just a corpus.

**Tic TOC**, the curriculum design layer, answers: *in what order, with what prerequisites?* Most professors received no formal training in curriculum design — not a criticism, a structural fact about how academic careers are built. Backward design (start from capability, work back to evidence, then to instruction and sequence) is rare in practice. This layer produces it. A curriculum without an engine is a static schedule.

**The Adaptive Engine** answers: *what mode does this student see for this concept at this moment?* Ask AI (context-anchored explanation, hints only). Quiz Me (spaced retrieval practice). Case Study (pre-written, faculty-reviewed CBL). Glimmer (generative, ill-structured, scaffolded assignment). The engine is a within-learner contextual selection, not a global "best mode" pick. An engine without a measurement layer is the IDK IDK trap — optimizing for the wrong thing, efficiently.

**The Measurement Layer** answers: *what does this student actually know, and how well do we trust the answer?* Not engagement — time on platform, clicks, turns, completions. Learning evidence. The Genuine Learning Probability framework Chapter 5 specifies in full: seven friction components that distinguish the engagement signal from the durable-encoding signal. A measurement layer without a book library is an instrument with nothing to instrument.

The Khanmigo failure, in this frame, is a missing measurement layer in disguise. The engine was optimizing for engagement because that was what it could see. Give it a measurement layer that distinguishes engagement from learning, and the same Socratic-tutor design produces a different signal — *this student spent six minutes typing "idk" and copying hints; the durable-learning estimate for this session is near zero* — and a different downstream behavior.

The integration is the architecture. That is the load-bearing claim. I am sketching here, not building.

<!-- → [DIAGRAM: Four-layer stack diagram — Book Library at base, Tic TOC above it, Adaptive Engine above that, Measurement Layer at top. Each layer labeled with its governing question (what is being taught / in what order / what mode now / what does the student know). Arrows showing data flow upward and selection flow downward. A fifth element outside the stack: the LLM, connected to the Adaptive Engine by a dotted line labeled "willing actor, no opinions." The point of the diagram is that the LLM is not in the stack — it is a dependency of one layer, not the architecture itself.] -->

---

## What would change my mind

I want to be explicit about this, because the chapter makes strong claims and strong claims should come with stated conditions for revision.

The central claim is that unguarded AI deployment in education produces measurable learning damage, and that the variable is the platform's pedagogical commitments, not the model. Three findings would force me to revise.

A rigorous, independently-evaluated, multi-site RCT of an unguarded generative-AI tutor — $N$ in the thousands, durable outcomes on transfer-bearing assessments, no measurement-layer instrumentation — that produced gains of $d > 0.4$. That would suggest the architecture commitment is not necessary: engagement alone is sufficient.

A failure of the Bastani PNAS finding to replicate across five attempts in different countries, age groups, and subject domains. That would substantially weaken the wrapper-as-variable claim the architecture rests on.

Evidence that bolt-on tools (LMS + chatbot + Anki + case library, used separately) produce equivalent learning outcomes to integrated platforms under the same GLP framework. The book bets integration is doing real work. If integration turns out to be a vanity, the central architectural claim is wrong.

I do not believe any of these will happen. But I should not be the only person testing whether they do.

---

## Exercises

### Exercise 2.1 — LLM exercise: Classify the failure mode

Paste the following scenario into an LLM of your choice and ask it to classify the failure mode and diagnose the measurement error. Then evaluate whether the LLM's analysis matches the framework developed in this chapter.

*Scenario:* A high school district has rolled out an AI tutoring platform. The dashboard reports: average 22 minutes per student per day; 84% of assigned modules completed; student satisfaction at 4.1/5. The district reports the deployment as a success. Six months later, the state math assessment shows scores down 0.18 standard deviations relative to the pre-deployment cohort.

After reviewing the LLM's output, write a one-page memo for the district superintendent that does three things: (a) classifies which failure mode this represents and names the specific mechanism that produced the outcome; (b) identifies the measurement choice that created the gap between the dashboard and the assessment; (c) names two diagnostic questions the district should ask the vendor before renewing the contract.

### Exercise 2.2 — LLM exercise: Build the two dashboards

Use an LLM to help construct two one-page artifacts about the IDK IDK incident described in this chapter.

Ask the LLM to generate: (a) an engagement dashboard that a Khanmigo-style platform might publish about the student's six-minute session — at least six metrics, designed to look like a success; (b) a learning-evidence dashboard for the same session, using the seven GLP components sketched in this chapter, showing what each component registers.

Review the LLM's output. In a closing paragraph (~150 words), name the single design decision that produces the gap between the two dashboards. Note any place where the LLM's dashboard construction reveals a gap in its understanding of the GLP framework — what did it get wrong, and why?

### Exercise 2.3 — LLM exercise: The MIT OCW counterfactual

The chapter argues that MIT OpenCourseWare increased applications rather than collapsing them, and uses this to claim that content was never the binding constraint of a college education.

Ask an LLM to generate the strongest possible objection to this argument. Then write a 500-word evaluation that does three things: (1) identifies which of the LLM's objections you find most compelling, and why; (2) names one specific kind of institution where the OCW evidence is *least* likely to generalize; (3) identifies one piece of evidence that, if it appeared, would force you to revise the chapter's central reading of OCW.

---

## Where Chapter 3 begins

You now have the two failure modes named, the third position introduced, and the four-layer architecture sketched. The natural move would be to specify the architecture in detail.

We are not going to do that yet. Before we specify the architecture, we have to answer an honest prior question: **for some learning problems, the right answer is a simpler tool, not the full architecture.** The four-layer architecture is expensive — in design time, in instrumentation, in cognitive load — and deploying it into a problem that does not need it is, in the most literal sense, malpractice.

Chapter 3 introduces the complexity threshold test: three questions that tell you whether the architecture earns its cost on a given problem. The motivating case is Priya, 19, six years in a Homes of Hope residence in Hyderabad, needing job-functional English for a BPO interview. For Priya, Anki is enough. Not because the architecture is too expensive for her circumstances. Because the *structure of her learning problem* does not require it.

Chapter 3 is the discipline that says: *not always, and here is how to know.* EdTech vendors will read Chapter 2 and decide their next product needs all four layers. Chapter 3 exists to prevent that error.

The platform is opinionated. The model has no opinions of its own. That sentence is the entire book.

---

## References

[^2]: DiCerbo, K. (2025). Quoted in Meyer, D. *RIP Khanmigo and EdTech Industry Dreams of AI Tutors*. Dan Meyer Substack. https://danmeyer.substack.com/p/rip-khanmigo-and-edtech-industry

[^3]: Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., & Mariman, R. (2025). Generative AI without guardrails can harm learning: Evidence from high school mathematics. *Proceedings of the National Academy of Sciences*, 122(26), e2422633122. https://doi.org/10.1073/pnas.2422633122

[^6]: Horvath, J. C. (2025). *The Digital Delusion: How EdTech Has Failed Our Schools — and How to Fix It*.

[^10]: Sadler, P. M., Sonnert, G., Coyle, H. P., Cook-Smith, N., & Miller, J. L. (2013). The influence of teachers' knowledge on student learning in middle school physical science classrooms. *American Educational Research Journal*, 50(5), 1020–1049.

[^11]: Kestin, G., Miller, K., Klales, A., Milbourne, T., & Ponti, G. (2025). AI tutoring outperforms in-class active learning: An RCT introducing a smart learning companion. *Scientific Reports*, 15. https://www.nature.com/articles/s41598-025-97652-6
