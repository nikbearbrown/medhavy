# Research Notes — Chapter 1: What Is an Intelligent Textbook?

*Working pantry document for the Medhavy book project. Research underpinning Chapter 1 — the load-bearing opener that names both failure modes (no-AI, all-AI), establishes the third position, and sketches the four-layer architecture. Citation-dense. Companion to `ask-ai-research.md`, `educational-media-economics-research.md`, and `glimmer-displacement-research.md`.*

*Compiled 2026-05-17 for the chapter-writer subagent. Maintained for revision.*

---

## Chapter summary

This chapter performs three moves in sequence. First, it shows that content was never the product the residential-degree industry was selling — MIT OpenCourseWare gave away the content for free in 2001, and twenty-four years later the field has not collapsed. Demand for the residential experience went up, not down. The corollary: an intelligent textbook is not in the content-replacement business either; it is in the experience-construction business. Second, it names the two failure modes the field is committing simultaneously. The "no-AI" failure mode is the one Horvath catalogs accurately: professors absorbing automatable work (re-explaining the same concept to the next student, building the next quiz, marking the next short-answer assignment) until the irreducibly human work — Socratic provocation, judgment under ambiguity, the small encounters that move a learner from "doing the assignment" to "becoming somebody") — gets crowded out by accident, not by design. The "all-AI" failure mode is the one Khan's *Brave New Words* under-counts: a chatbot becomes the relationship, the student types "I don't know, I don't know," the system logs the turns as engagement, and the most ambitious AI tutoring deployment in history reports growth from 40,000 to 700,000 students while Khan Academy's own Chief Academic Officer publicly acknowledges *"I will tell you, we see more 'IDK IDK,' more passive kinds of interaction than we would like."* Both failure modes share an underlying measurement error: they treat engagement as a proxy for learning. Third, the chapter introduces the third position — not a Solomon-split compromise between Khan and Horvath, but a different question. *What would you have to build if you took all the evidence seriously?* The answer the rest of the book elaborates is a four-layer architecture (Book Library / Tic TOC / Adaptive Engine / Measurement Layer) whose central commitment is that the **integration of layers is the architecture**, not the layers themselves. The closing line — *the platform is opinionated; the model has no opinions of its own* — is the chapter's load-bearing claim, and the load-bearing claim of the book.

---

## A. Conceptual foundations

### A.1 Content was never the product — what MIT OpenCourseWare actually proved

In April 2001, MIT President Charles M. Vest announced that MIT would publish "virtually all" of its course materials on the open web, free for any user, for any purpose. The pilot launched in September 2002 with materials from 50 courses; the platform reached the full MIT curriculum (over 1,800 courses) by 2007. This was unprecedented in the residential-degree industry, where course materials had functioned as a partial moat around tuition revenue. ([MIT News 2001](https://news.mit.edu/2001/ocw); [Wikipedia, MIT OpenCourseWare](https://en.wikipedia.org/wiki/MIT_OpenCourseWare))

The hypothesis at the time, from inside and outside the institution, was that giving away the content would erode demand for the credential. The opposite happened. By the time MIT ran its OCW user survey work in the late 2000s, the survey of incoming MIT undergraduates was reporting that **over half of incoming freshmen were aware of OCW prior to choosing MIT, and roughly one-third of those said OCW was a significant influence on their decision to attend MIT** ([D'Oliveira & Lerman, MIT Faculty Newsletter](https://web.mit.edu/fnl/volume/221/d'oliveira_lerman.html); [MIT OCW Evaluation Summary 2011](https://ocw.mit.edu/about/site-statistics/11_Eval_Summary_112311_MITOCW.pdf)). MIT applications did not collapse. They rose. The selectivity of the institution increased, not decreased, over the OCW era.

Why did this happen? Because the product MIT was selling — and selling at roughly $80K/year — was never the content. The content had been available, in textbook form and library form, for decades. What MIT sold was the experience: the labs, the cohort, the credentialing, the apprenticeship under faculty, the social graph that would later become the alumni network. OCW raised the **visibility** of the experience by making the content downstream evidence of the institution's seriousness. Prospective students saw the materials. They concluded: this is a place I want to be physically. The signal MIT was emitting got louder when MIT gave away what everyone thought was the moat.

**What this proves.** Content is not the binding constraint of a college education. It probably wasn't the binding constraint of high-quality K–12 education either; the *Sesame Street* literature suggests $5/child/year of well-designed content can produce *d* = 0.29 cognitive gains (Mares & Pan 2013, see `educational-media-economics-research.md`), but high-quality education at scale has always required the surrounding scaffolding — the teacher in the room, the parent at the table, the peer group at the desk, the cohort at the lab bench.

**What this does not prove.** OCW does not prove that AI tutoring will go the same way. The cases are not isomorphic: OCW substitutes content for content (textbook → online lecture notes) without claiming to substitute experience for experience. An AI tutor *does* claim to substitute experience for experience — the chatbot replaces the office-hours conversation, the patient tutor, the curious peer. That is a different kind of claim. The MIT OCW evidence undercuts the *content* version of educational disintermediation; it has nothing direct to say about the *experience* version.

**Why this matters for Chapter 1.** It defangs the most common objection a Charles Fadel reader will arrive with: *"If we publish good content, it will erode the institution that hosts it."* OCW is the twenty-four-year-old natural experiment that says: no, it doesn't. Demand for institutions migrates toward what institutions still do uniquely. The intelligent textbook design question becomes: what is the residential institution still doing uniquely once the content is free? Answer: the experience, the measurement, the credentialing. The intelligent textbook is *in the experience-construction business*, not in the content-replacement business. That framing is the entire book in one sentence.

### A.2 The no-AI failure mode — irreducibly human work crowded out by accident

The "no-AI" failure mode is the failure Horvath cleanly diagnoses in *The Digital Delusion* and the failure Bear's *Trust the Teacher* essays cleanly diagnose from inside the classroom. It does not need to be dramatic. The standard form: a professor of clinical pharmacology spends the first two weeks of every semester re-explaining beta-blocker mechanism to the new cohort. She has done it for fifteen years. The explanation is good. By week three, she is asked to grade short-answer questions on beta-blocker mechanism — 120 of them, indistinguishable from the 120 from last year. By week six, she is asked to write the next iteration of the case study for the cardiology block. The professor has done all of this competently, and in the doing has spent her *six most senior cognitive hours of the semester* on work that an Anki deck, an AI grading rubric, and a CBL case template would have absorbed at roughly $0.40 in OpenAI tokens.

What did the professor not do during those six hours? She did not run the Socratic ambiguity exercise on the second-year student whose differential diagnosis was technically right but whose reasoning had a structural gap she was the only person in the building who could see. She did not call the student whose oncology rotation she heard had gone sideways. She did not write the IRB amendment that would have let her involve the third-year students in the new study. She did not sit with the new resident over coffee. The work that is *only* available because she is in the building, with her judgment, her relationships, her authority, and her time — that work got crowded out by the work that an algorithm or a model could have done.

This is the irreducibly-human displacement Bear's `glimmer-displacement-research.md` lays out in technical form. The micro-mechanism: when a teacher's marginal hour is committed to work that AI can do nearly as well, the teacher's *highest-leverage hour* — the hour AI cannot do — gets squeezed out. The squeezing happens by accident, not by design. Nobody chose it. The professor would prefer to spend her six hours on Socratic work. The structural reality of her job — short-answer grading, lecture re-recording, case construction — selects for the work that fits in her queue.

Horvath catalogs this failure beautifully and then misnames the cause. He identifies the symptom (test scores dropping after EdTech rollouts; the PISA correlation between heavy device use and lower math scores; the smartphone-in-the-classroom distraction effect) and assigns responsibility to *the AI* or *the technology*. The closer diagnosis: the AI is doing the wrong subset of the teacher's job because the platform that delivered it didn't know which subset to give it, and didn't know how to give the rest *back to the teacher*. The hammer problem is real. Horvath catches it. He then proposes putting the hammer down. The Medhavy thesis: it isn't a hammer; it is a hammer being held by an architecture that didn't notice the wood needed sawing too.

### A.3 The all-AI failure mode — chatbot as relationship, IDK-IDK as engagement

The all-AI failure mode is the failure Khan's *Brave New Words* under-counts. It is the failure Khan Academy itself has now publicly acknowledged. In June 2025 (verify exact date), Khan Academy's Chief Academic Officer Kristen DiCerbo told reporters: *"I will tell you, we see more 'IDK IDK,' more passive kinds of interaction than we would like"* ([reported in *RIP Khanmigo and EdTech Industry Dreams of AI Tutors*, Dan Meyer Substack](https://danmeyer.substack.com/p/rip-khanmigo-and-edtech-industry); see also [Sal Khan acknowledges Khanmigo "has failed to catch on with students"](https://completeaitraining.com/news/sal-khan-says-his-ai-tutoring-chatbot-has-failed-to-catch/)). The Common Sense Media review of Khanmigo notes that *"persistent prompting would lead to Khanmigo offering a more complete answer"* — i.e., the Socratic guardrail leaks under student pressure ([Common Sense Media review](https://www.commonsensemedia.org/ai-ratings/khanmigo)).

The mechanism is precise. A student opens Khanmigo. They get a problem. They get a Socratic prompt: *"What do you think the first step might be?"* They type *"i dont know."* The system rephrases, lowers the abstraction, asks again. The student types *"idk."* The system tries the prerequisite recall move. *"idk idk."* Eventually — under the gentle persistence the system is designed to maintain — the model leaks the answer or offers a more complete hint. The student copies. The student moves to the next problem. The session log records: time on platform, turns exchanged, problems attempted, problems completed. From the dashboard view, this student is **engaged**. From the learning view — durable retention, transfer to novel problems, the seven friction components of the GLP framework that Chapter 5 will detail — this student has done close to zero work.

The Bastani et al. 2025 PNAS finding is the cleanest empirical confirmation of this mechanism (`ask-ai-research.md` covers this in depth; the citation is anchored here for Chapter 1 use). In a Turkish high school RCT (~1,000 students, grades 9–11, math practice), unguarded GPT-4 access during practice produced **48% higher in-session performance** than the no-AI condition; the safeguarded "GPT Tutor" condition produced **127% higher in-session performance**. On the post-practice exam *without AI access*, the GPT Base group scored **17 percentage points lower** than the no-AI control; the GPT Tutor group was statistically indistinguishable from control. The in-session metric reported success. The durable-learning metric reported half a standard deviation of damage. ([Bastani et al. 2025, *PNAS* 122(26), e2422633122](https://www.pnas.org/doi/10.1073/pnas.2422633122))

The structural error in both Khan and Horvath: both are using engagement-related metrics as the binding outcome variable. Khan reads engagement growth (40K → 700K students, 380+ district partners) as success ([Khan Academy 2024 efficacy blog](https://blog.khanacademy.org/khan-academy-efficacy-results-november-2024/)). Horvath reads engagement-correlated harm (PISA score declines at high digital-device dosage) as failure ([OECD PISA 2022 Volume I](https://www.oecd.org/en/publications/pisa-2022-results-volume-i_53f23881-en.html)). Both have made the same measurement choice. They have just reached opposite conclusions from it. Neither is asking the question: *what would a measurement layer that captured learning instead of engagement actually tell us about either deployment?*

### A.4 The third position — what taking all the evidence seriously demands

The third position is not a balanced average of Khan's optimism and Horvath's pessimism. It is the position that follows from a specific commitment: **the only honest move is to build the measurement infrastructure first, then let the architecture follow from what the measurement reveals**. This is the move Bogatz & Ball made for Sesame Street in 1969–1971 (`educational-media-economics-research.md`): they built the assessment instrument first, designed the show against measurable readiness skills, then ran the trial. It is the move the rest of the EdTech field has spent fifty-five years failing to repeat.

The four-layer architecture is what falls out of this commitment. Each layer answers a different question:

- **Book Library** — what is the domain-specific content the student is engaging with? At what level of Sadler-2013-style Level-3 specificity (`domain-specific-instruction-research.md`) does that content meet the actual task? The Library layer answers: *what is this textbook teaching, and is it teaching it at the right grain?*
- **Tic TOC** — what is the curriculum design? What are the concept dependencies, the prerequisite chains, the phase gates? The Tic TOC layer answers: *in what order does the student encounter the material, and what must they have mastered before encountering this concept?* This is the concept-sequencing and BKT/DKT territory (`concept-sequencing-research.md`).
- **Adaptive Engine** — what mode (Ask AI / Quiz Me / Glimmer / Case Study) does the student see for this concept at this moment? This is a within-learner contextual bandit, not a global "best mode" pick. The Engine layer answers: *what intervention is the right one for this learner, on this concept, given what we have observed about this learner's state?*
- **Measurement Layer** — what is the engine actually optimizing for? Not engagement (time on platform, clicks, turns, completions). Learning evidence — the seven GLP friction components (TIKTOC §Ch 5): Y1 Temporal Engagement, Y2 Error Trajectory, Y3 Cross-Context Transfer, Y4 Uncertainty Calibration, Y5 Social Knowledge, Y6 Retrieval Strength Decay, Y7 Scaffolding Response. The Measurement layer answers: *what does this student now know, and how well do we trust the answer?*

The integration is the architecture. None of the four layers does anything useful in isolation. A Book Library without a Tic TOC is a corpus. A Tic TOC without an Adaptive Engine is a static curriculum. An Adaptive Engine without a Measurement Layer is the IDK-IDK trap — a system optimizing for the wrong thing, very confidently, very efficiently. A Measurement Layer without a Book Library is an instrument with nothing to instrument. The Khanmigo failure is **a missing Measurement Layer in disguise**: the engine was optimizing for engagement, because that was what it could see.

### A.5 "The platform is opinionated. The model has no opinions of its own."

This is the chapter's load-bearing line. It is also the line the rest of the book either earns or fails to earn. The decomposition:

- **The model has no opinions.** Underneath every chatbot mode in the architecture is a frontier LLM — GPT-4o, Claude Sonnet, Gemini 2.5, the next one. The model is willing to be Socratic, willing to be didactic, willing to give the answer, willing to refuse to give the answer. The same model can produce the Bastani GPT Base outcome (–17 percentage points) or the Bastani GPT Tutor outcome (parity with no-AI control). The variable that determines which outcome happens is not the model. It is the wrapper — the system prompt, the context-injection discipline, the phase-gate logic, the mode selection rule. The model is a willing actor with no opinions of its own.
- **The platform is opinionated.** The platform makes the pedagogical commitments that decide what the model does in any given moment. The opinions are visible in the design: *retrieval practice before re-reading, generative work before extractive work, case study before Socratic, Socratic only when the prerequisites are in place, scaffolding fades on a measurable response curve, the answer is never given before the student has externalized their reasoning step*. These are not the model's preferences. They are the platform's commitments — and they are the place where the evidence in `ask-ai-research.md`, `quiz-me-research.md`, `case-study-research.md`, `glimmer-research.md`, and `concept-sequencing-research.md` is actually deployed.
- **The corollary.** A platform that has no opinions — a chatbot wrapper with a system prompt that says "be a helpful tutor" and otherwise lets the model decide — defaults to the model's training-distribution average behavior, which is the Bastani GPT Base condition. The model's "average tutor" produces –17 percentage points. A platform without opinions is a platform that will reliably reproduce that outcome.

This is the chapter's promise to the reader who has been told that AI in education is either revolutionary or catastrophic. The honest answer: it depends entirely on what the platform around the model is committed to, and most platforms are not committed to anything in particular. The book is the design specification for being committed to something in particular.

---

## B. Domain examples and cases

### B.1 The Khanmigo IDK-IDK incident as worked example

The chapter's opening case. Specification:

- **What the student does.** A high-school student is solving a quadratic equation using Khanmigo's Socratic mode. They get stuck on the discriminant. The system asks: *"What do you think we'd compute first?"* The student types *"idk."* The system rephrases: *"Let's break this down. What's the formula for the discriminant?"* The student types *"i dont know."* The system tries the prerequisite recall: *"What's a discriminant in general?"* The student types *"idk idk."* After three to five turns, the system either offers a more complete hint (the Common Sense Media-documented guardrail leak) or the student abandons and moves on.
- **What the engagement dashboard showed.** Time on platform: ~6 minutes. Turns exchanged: ~8. Problems attempted: 1. The student is logged as engaged. The dashboard reports a successful tutoring session.
- **What a learning-evidence dashboard would have shown.** Y1 Temporal Engagement: minimal externalization, no scaffolding response. Y2 Error Trajectory: no errors generated, because the student did not commit to an answer the system could evaluate. Y3 Cross-Context Transfer: untestable; nothing was learned, so there is nothing to transfer. Y4 Uncertainty Calibration: undefined; the student said "I don't know," which is information about meta-cognition, but not in a form the system used. Y5 Social Knowledge: no peer or teacher contact. Y6 Retrieval Strength Decay: no encoding occurred, so decay is not the right measure. Y7 Scaffolding Response: the scaffolding was offered, and the student did not climb the ladder. *The composite GLP score for this session is near zero.*
- **The gap.** Engagement dashboard says success. Learning evidence dashboard says zero. The gap is the IDK-IDK failure. The system that produced it was the most ambitious AI tutoring deployment in history. Charles Fadel readers know this case in the abstract; this chapter makes them know it in the specific.

### B.2 The MIT OpenCourseWare counter-case

The chapter needs a positive case that is *not* an AI deployment, to make the point that the right question is not "is AI in education good or bad" but "is the platform architecture committed to what learning actually requires." MIT OCW is that case.

- **What MIT did.** Published essentially the entire MIT undergraduate and graduate curriculum, free, in the open, in 2001–2007. No login wall. No ad model. No platform layer. Just the materials.
- **What happened to MIT enrollment.** Did not collapse. Applications rose. Selectivity rose. Half of incoming freshmen knew OCW; a third said it influenced their MIT choice ([D'Oliveira & Lerman](https://web.mit.edu/fnl/volume/221/d'oliveira_lerman.html)).
- **What happened to MIT's brand.** OCW became a substantial component of MIT's global identity. The institution became more, not less, valuable as it gave away the content.
- **What this teaches the chapter.** The thing that erodes when content goes free is *not* the institution. It is the assumption that content is what the institution sells. The intelligent textbook is in the same business MIT is in — building the experience around the content — not in the business of selling the content. This is the framing the book hands to the Charles Fadel reader: *you are not building a textbook that sells better than other textbooks. You are building an experience that produces better learning evidence than other experiences.*

### B.3 The Sesame Street parallel

A second positive case the chapter can reach for, drawing on `educational-media-economics-research.md`:

- **What Sesame Workshop did.** Built the assessment instrument first (Bogatz & Ball 1970–1971), designed the show against measurable readiness skills, ran the trial. Effect size on cognitive outcomes for the 15-country meta-analysis: *d* = 0.29 (Mares & Pan 2013, *Journal of Applied Developmental Psychology* 34(3), 140–151).
- **What it cost.** Roughly $5 per child per year in inflation-adjusted dollars, reaching ~156 million children annually through co-productions.
- **Why this matters for the chapter.** The Sesame Street machinery is *not* an AI deployment. It is the canonical example of what high-quality educational media — measured before claimed, optimized over decades, scaffolded around a stable curricular target — is capable of. The intelligent textbook field has not yet produced its Sesame Street. The four-layer architecture is the bet about what such a thing would have to look like.

### B.4 A hostile case the chapter must acknowledge

A reader trained by *The Digital Delusion* will arrive with the PISA 2022 figure: *students who spend 5–7 hours per day on digital devices for leisure score about 49 points lower in mathematics than students who spend up to one hour per day, even after adjusting for socioeconomic profile* ([OECD PISA 2022 Volume I](https://www.oecd.org/en/publications/pisa-2022-results-volume-i_53f23881-en.html)). The chapter cannot ignore this. The chapter's honest acknowledgement: the PISA finding is real, it is large, and it is exactly the kind of evidence Horvath uses to argue that classroom technology harms learning. The chapter's qualification: PISA measured *leisure* digital-device use, not *learning-instrumented* device use. The finding describes indiscriminate high-dosage exposure. It does not describe what a constrained, evidence-anchored, measurement-equipped platform produces. Chapter 3 ("The Evidence Base") makes this argument in full; Chapter 1 anticipates it.

---

## C. Connections and dependencies

### C.1 Within-book connections

- **Forward to Chapter 2 ("When Anki Is Enough").** Chapter 1 establishes that the four-layer architecture is *one possible architecture*. Chapter 2 honors the reader by acknowledging that for some learning problems — Priya's vocabulary acquisition, certain forms of corporate onboarding, well-structured certification prep — the right answer is a simpler tool, not the full architecture. The complexity threshold test is the diagnostic.
- **Forward to Chapter 3 ("The Evidence Base").** Chapter 1 asserts that engagement is not learning. Chapter 3 specifies the evidence base for that assertion — including the Bastani PNAS finding, the Roediger-Karpicke retrieval-practice literature, the Thistlethwaite CBL synthesis, and Hattie's 0.40 hinge — and shows how each piece of evidence anchors a specific architectural decision later in the book.
- **Forward to Chapter 4 ("The Four Layers").** Chapter 1 sketches the four-layer architecture. Chapter 4 makes the integration claim precise: why bolt-on tools cannot produce the integrated signal, what each layer must do for the others to function, what the data exchanges between layers look like.
- **Forward to Chapter 5 ("The Measurement Layer").** Chapter 1 names "engagement vs. learning" as the diagnostic. Chapter 5 operationalizes it as the seven GLP friction components and the ensemble architecture that makes them gaming-resistant.

### C.2 Cross-pantry dependencies

- **`ask-ai-research.md`** carries the Bastani PNAS 2025 citation in full, the Khanmigo qualitative findings, and the ITS-vs-GenAI distinction. Chapter 1 uses the Bastani finding as the central empirical anchor for the all-AI failure mode and pulls the Khanmigo IDK-IDK quote (Kristen DiCerbo) from the same note.
- **`educational-media-economics-research.md`** carries the Sesame Street evidence base and the MIT OCW data is anchored here in the present note (it does not appear in the existing economics note, which focuses on Sesame Street and Mayer CTML rather than higher-ed open content). Chapter 1 uses the MIT OCW data as the opening positive case and the Sesame Street data as the methodological exemplar.
- **`glimmer-displacement-research.md`** carries the no-AI failure mode framing (irreducibly-human work crowded out, AI displacement framing, Renkl scaffolding fading, van Merriënboer). Chapter 1 uses this as the conceptual backbone for the no-AI section without re-citing every paper.
- **`concept-sequencing-research.md`**, **`quiz-me-research.md`**, **`case-study-research.md`**, **`glimmer-research.md`**, **`domain-specific-instruction-research.md`** are the architecture-layer notes the chapter previews but does not yet deploy. Chapter 1 names them as "the evidence base" without rendering it.

### C.3 Cross-book connections

- **Trust the Teacher (Bear's prior book).** Chapter 1 is the Medhavy book's version of TtT's Chapter 1 ("The Ban"). Where TtT treats the no-AI failure mode at length, Medhavy can compress that material and devote more length to the all-AI failure mode and to the architecture sketch. The two books complement each other: TtT is the *case for the teacher*, Medhavy is the *case for the platform that lets the teacher do what only the teacher can do*.
- **Homes of Hope Plus One (Priya's book, also in this workshop).** The Priya case introduced in Chapter 2 is the Medhavy-side framing of a learner Bear has already written for in HoH+1 Unit 2 ("AI as Work Tool"). Chapter 1 does not deploy Priya yet — but it can foreshadow her by naming, in passing, that the architecture being sketched is not the right answer for every learner; that calibration arrives in Chapter 2.

---

## D. Current state of the field

The field is currently making two opposite mistakes simultaneously and producing two opposite literatures that do not talk to each other.

### D.1 The Khan-side literature — engagement-as-success

Vendor-sourced and vendor-adjacent claims. Khanmigo growth (40K → 700K students, 380+ district partners) is real but is reported as an outcome rather than as an input ([Khan Academy 2024 efficacy blog](https://blog.khanacademy.org/khan-academy-efficacy-results-november-2024/)). The same vendor sources acknowledge — as DiCerbo has — that the *quality* of those interactions is below expectations. The first generation of generative-AI tutoring deployments (2022–2025) has produced one rigorous positive RCT (Kestin et al. 2025, Harvard physics, *d* ≈ 0.7–1.3 in a single course), one rigorous negative RCT for unsafeguarded deployment (Bastani et al. 2025, Turkish high-school math, –17 pp), and a substantial body of self-report and satisfaction data that does not yet adjudicate durable learning. The field's net knowledge state: the same model, with different prompt wrappers, can produce either outcome. The wrapper is the variable. The literature has only just begun to specify what makes a good wrapper.

### D.2 The Horvath-side literature — correlational harm

The PISA 2022 finding (49-point math score gap at 5–7 hours of daily leisure digital device use, ([OECD 2023](https://www.oecd.org/en/publications/pisa-2022-results-volume-i_53f23881-en.html))), the smartphone-in-the-classroom distraction literature, the Stroebe / Felisoni / Kuznekoff-Titsworth body of work on attention and academic performance, and the meta-analytic synthesis Horvath cites at +0.29 ES are all real. They describe the average outcome of indiscriminate high-dosage classroom technology deployment in conditions where the technology was added without architecture and without measurement. They do not describe what a constrained, evidence-anchored, measurement-equipped platform would produce. Horvath conflates these — the "nearly every context" claim in the book overreaches. Chapter 3 specifies this in detail.

### D.3 The middle that does not yet exist

Between these two literatures is the architectural research the book is trying to call into being: the work that specifies how the layers integrate, what the measurement layer must capture, what the mode-selection rule looks like under realistic data conditions. There are early signs. Tutor CoPilot (Wang et al. 2024, arXiv:2410.03017) shows what context-injection of expert pedagogical reasoning can do for downstream student learning (4–9 percentage-point mastery lift for students working with lower-quality tutors). The GLP preprint (Frictional / Irreducibly Human series) sketches the measurement framework. The Bastani PNAS finding is the empirical proof that wrapper design dominates model choice. None of these are integrated. The book's claim is that the integration is the architecture.

### D.4 The field's measurement gap

The single most consequential field-level fact: there is no widely-deployed measurement framework that distinguishes engagement from learning at the instrumentation level. LMSs report time-on-platform, page views, quiz completion rate, chat interactions. Adaptive platforms report problem accuracy and response time. ITS systems report per-step assistance use. None of these is a learning measurement; all are engagement-or-performance proxies. The GLP framework (TIKTOC §Ch 5) is the book's proposal for what such a measurement layer would have to capture. It is not yet validated in deployment. Chapter 1 names the gap; Chapter 5 specifies the proposal.

---

## E. Teaching considerations

### E.1 The chapter's audience pivot

Two readers, one chapter:

- **The Charles Fadel type** arrives with content and conviction, often skeptical of AI-in-education claims (he has watched OECD data and is sympathetic to Horvath) and uncertain whether to commission a platform. The chapter has to validate that skepticism *and* convince him there is a third position that is not naïve. The MIT OCW case is for him: the example of an institutional move that proved most assumptions about content-and-credential erosion wrong.
- **The developer who got handed `API.md`** arrives with a working chatbot integration and no model of what the platform is *for*. The chapter has to give them the categories that will make sense of their build decisions — engagement vs. learning, the four layers, opinionated platform vs. opinion-less model. The Khanmigo case is for them: it is the deployment most of them have already heard of, and it is the case where the wrapper design was the failure mode.

### E.2 What to avoid

- Do not open with the architecture. The architecture is the answer; the chapter has to earn the architecture by first specifying what question it answers. Open with the IDK-IDK incident.
- Do not pretend the field has settled the debate. The Bastani PNAS finding is one RCT in one Turkish high school. The Kestin finding is one course at Harvard. The literature is early. The chapter's authority comes from honesty about what the evidence supports, not from forcing more certainty than the data gives.
- Do not over-claim what the four-layer sketch can do at this point in the book. Chapter 1 is the *sketch*. Chapter 4 is the architecture. Chapter 5 specifies the measurement layer. The Charles Fadel reader who tries to commission a build off Chapter 1 alone is doing what Khan did. The chapter should tell them, gently, that the rest of the book exists for a reason.
- Do not lean on Hattie. The 0.40 hinge will appear in Chapter 3 *under critique* — as a cost-effectiveness guideline, not an absolute binary. Chapter 1 should not cite the 0.40 figure as if it settles anything. It does not.

### E.3 Voice and register

The chapter is the book's first encounter with the reader. It needs the voice to land. Three notes:

- **The first paragraph is the IDK-IDK paragraph.** Specific. Named. The student is real (Khanmigo deployment, Khan Academy's own CAO acknowledging the pattern). No abstraction.
- **The "third position" move is delivered in plain prose, not in a framework.** The reader earns the framework over the next eleven chapters. Chapter 1 hands them the question.
- **The closing line — "The platform is opinionated. The model has no opinions of its own" — is the chapter's load-bearing claim and the book's load-bearing claim.** It should be the chapter's literal last line, after the bridge to Chapter 2.

### E.4 The reader's first decision point

After Chapter 1, the reader makes a small commitment: *Yes, I want to know what the architecture is.* The chapter does not need to deliver the architecture. It needs to make that commitment honest by giving the reader (a) the failure modes named, (b) the third position introduced, (c) a clear bridge to Chapter 2's calibration check, and (d) Chapter 3's promise of the evidence base.

---

## F. Library files — what existing pantry covers

Section-by-section guide to which existing pantry files cover what, so the chapter author does not duplicate research:

- **`ask-ai-research.md`** — Bastani PNAS 2025 in full (page-numbered citation, study design, results), Khanmigo qualitative findings including the DiCerbo "IDK IDK" acknowledgment, ITS-vs-GenAI distinction (Class A / Class B), VanLehn 2011 step-grain interactivity finding, the Socratic-vs-direct-prompting evidence base, the context-injection / RAG / "lost in the middle" findings. **Use this note for any specific number from the AI-tutor literature.** This Chapter 1 note carries the *framing* of the all-AI failure mode; `ask-ai-research.md` carries the *citations*.
- **`educational-media-economics-research.md`** — Sesame Street evidence base (Bogatz & Ball 1970–1971, Mares & Pan 2013, Kearney & Levine 2019), the $5/child/year cost figure, Mayer's CTML twelve principles, cost-collapse asymmetry framing, the "measurement before claims" methodological lesson. **Use this note for the Sesame Street comparator case and Mayer CTML.** Chapter 1 only needs the framing; the depth lives there.
- **`glimmer-displacement-research.md`** — the AI displacement framing, irreducibly-human-work-crowded-out argument, scaffolding-fading literature (Renkl, van Merriënboer), studio-critique displacement evidence. **Use this note for the no-AI failure mode mechanism.** Chapter 1's no-AI section is a one-paragraph compression of this literature.
- **`_lib_co-intelligence__living_and_working_with_ai.md`** (Mollick) — human + AI framing, the "co-intelligence" register, the Bastani citation and Mollick's gloss on it. **Use this for the "human + AI not human vs. AI" framing** if Chapter 1 needs it.
- **`Computational Skepticism Substack` (Bear's published Horvath review, named in TIKTOC)** — the worked example for Chapter 3, but Chapter 1 can reference it once when introducing the Horvath-side reading.
- **`concept-sequencing-research.md`**, **`quiz-me-research.md`**, **`case-study-research.md`**, **`glimmer-research.md`**, **`domain-specific-instruction-research.md`** — the architecture-layer evidence base. **Chapter 1 names these as "the evidence base" without rendering them.** They are Chapter 3's job to deploy.

---

## G. Gaps and flags

### G.1 Verification flags (must resolve before draft is final)

- **MIT OCW prospective-student survey citation [verify].** The "half of incoming freshmen aware of OCW, one-third say significant influence on choice" figure is consistent across the MIT Faculty Newsletter article (D'Oliveira & Lerman) and the MIT OCW Evaluation Summary 2011 PDF. Both sources are MIT-internal. There is no peer-reviewed third-party replication. The chapter should cite the MIT OCW Evaluation Summary 2011 PDF as the primary source (it is the institutional record) and flag that this is self-reported and MIT-internal. The directional claim — *MIT applications did not collapse and OCW became part of the brand* — is uncontested. The specific "one-third" figure has the institutional-self-report caveat.
- **Kristen DiCerbo "IDK IDK" quote [verify exact venue and date].** The quote is widely reported and consistent across multiple secondary sources (Dan Meyer Substack, itutorsoft, CompleteAI). The primary venue appears to be an interview or panel discussion — verify the exact source (likely an EdSurge or Education Next interview circa 2024–2025) before citing. The Khan Academy CAO is the right institutional voice; the chapter should attribute by title as well as name.
- **Bastani PNAS 2025 citation — full.** The note above cites *PNAS* 122(26), e2422633122. Verify the exact page number when the chapter goes to draft; the version of record is the canonical citation, not the SSRN preprint or the institutional PDF.

### G.2 Conceptual flags

- **The "third position" framing must not become a Solomon-split.** Chapter 1 must resist the rhetorical temptation to write *"Khan and Horvath are both half right."* Both are using the wrong measurement. The third position is not a compromise; it is a refusal of the shared measurement error. Voice discipline: when the chapter feels like it is being "balanced," it is probably being lazy.
- **The architecture sketch must not over-claim.** Chapter 1 names four layers as a sketch. It does not claim the four-layer architecture is the only possible architecture, or that the layers are the *right* four. (The book's reflexive commitment, §4 of CLAUDE.md, requires this.) Chapter 1 should say: *here is the architecture this book elaborates; here are the bets it makes; here is what would have to be true for the bets to be wrong.* The "What would change my mind" section at the bottom of Chapter 1 is the place for this.

### G.3 Hostile-reader objections to anticipate

- *"You are reading the Khanmigo failure as evidence of architecture failure when it might just be evidence that AI tutoring doesn't work at all."* The chapter's response: Bastani PNAS 2025 is the disproof. Same GPT-4, two wrappers, two opposite outcomes. The model is not the variable. The wrapper is.
- *"You are reading the MIT OCW outcome as proof that content is not the product when the actual finding is that MIT is a luxury good and luxury goods don't lose price elasticity from giving away parts."* The chapter's response: this is a fair narrow reading of the OCW case, and the chapter should acknowledge it. The argument extends only to the claim that *content* is not the binding constraint; it does not extend to claims about institutions whose value is signaling-dominated. The intelligent textbook is not in the signaling business.
- *"You are setting up Khan as a strawman."* The chapter's response: the quotes are Khan's. The growth numbers are Khan's. The CAO acknowledgment is Khan's own. The chapter is not arguing against a position Khan does not hold; it is arguing against a position Khan has now publicly walked back. Take Khan's own current reading at face value.
- *"You are setting up Horvath as a strawman."* The chapter's response: Chapter 3 will engage Horvath at length. Chapter 1 names Horvath only as the canonical articulation of the no-AI failure mode's correct diagnosis (and the correct response to it, the chapter argues, is not putting the technology down). The serious engagement with Horvath's overreach claim ("nearly every context") is Chapter 3's territory.

### G.4 What would change my mind for this chapter

The chapter's claim is: *the right question is not whether AI in education helps or harms; the right question is what would you have to build if you took all the evidence seriously, and the answer is a four-layer architecture organized around learning measurement rather than engagement measurement.*

Specific evidence that would force revision:

- A rigorous RCT (multi-site, multi-cohort, *N* in the thousands, independent evaluators) of a Khanmigo-style unsafeguarded generative AI tutor that produced durable learning gains *d* > 0.4 on transfer-bearing assessments without measurement-layer instrumentation. This would suggest the architecture commitment is not necessary — engagement alone is sufficient.
- A failure of the Bastani PNAS finding to replicate. The current result is one RCT in one country. If five replications across high school math, college science, and adult professional learning all fail to reproduce the GPT Base / GPT Tutor divergence, the wrapper-as-variable claim weakens significantly.
- Evidence that the four-layer integration is not necessary — i.e., that bolt-on tools (LMS + chatbot + Anki + case-study library) produce equivalent learning outcomes to integrated platforms when measured against the same GLP framework. The book bets that integration is doing real work. If integration turns out to be a vanity, the book's central architectural claim is wrong.

### G.5 Still puzzling (questions the chapter raises but does not resolve)

- If engagement is not learning, why is engagement so persistent as the dominant outcome metric in EdTech reporting? The institutional explanation is that engagement is cheap to measure and learning is expensive to measure. The technical explanation lives in Chapter 5. But there is a third reading — that engagement is what platforms can *sell* to school districts, and learning is what districts cannot purchase without a measurement instrument they do not yet have. Chapter 1 cannot resolve this; the question is partly economic and partly epistemic.
- Why did the MIT OCW case not trigger a wave of imitation that disintermediated content the way commentators predicted? Twenty-four years on, content moats are still partly intact across higher education. The cleanest reading is that content was never the moat. A more interesting reading is that institutions have learned to compete on the *experience layer* of OCW's logic — selectivity, alumni networks, lab access, faculty apprenticeship — and to leave the content moat largely unguarded because they have learned the content was the cover, not the moat. This is the kind of structural reading the chapter gestures at without resolving.
- Is the four-layer architecture stable across domains? The illustrative case in the book is Medhavy's cancer textbook, which is a high-stakes, high-feedback domain. Does the same architecture work for a humanities seminar, where the right answer is contested and the measurement layer's "uncertainty calibration" component is doing different conceptual work than it does for clinical pharmacology? The book bets yes. Chapter 11 ("Open Questions") returns to this.

---

*End of research notes. Approx. 5,800 words. For Chapter 1 author use.*
