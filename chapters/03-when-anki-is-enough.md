# Chapter 3 — When Anki Is Enough

---

## Learning Objectives

By the end of this chapter, you will be able to:

1. **(Evaluate)** Apply a complexity threshold test to a learning problem and determine whether the full intelligent textbook architecture is warranted or whether simpler tools are the correct answer.
2. **(Analyze)** Identify the three conditions under which intelligent textbook complexity earns its cost: multi-layered capability build, live instrumentation requirement, and adaptive sequencing across concepts that cannot be pre-ordered.
3. **(Apply)** Map a specific learner profile and learning goal to the minimum viable tool set.
4. **(Evaluate)** Distinguish between "this tool is insufficient" and "this tool is the wrong tool."

**Prerequisites:** Chapter 1. You need the four-layer sketch (Book Library / Tic TOC / Adaptive Engine / Measurement Layer) and the *engagement-vs-learning* diagnostic. You do not yet need the specifications of any individual layer; Chapter 4 begins those.

**Skippable?** Technically yes. If you already know your learning problem needs the full architecture, you can move directly to Chapter 3. You will lose two things: a calibration check that prevents over-deployment, and the case of Priya — a learner whose life depends on a simpler tool than the one this book describes. I would rather you read the chapter.

---

## Where this fits the conductor frame

This chapter belongs almost entirely to the first of the three questions. Priya is the learner; the instructor barely appears; the organization does not appear at all, because there is no procurement to satisfy. The chapter is the clearest case in the book of the learner-first ordering producing an answer the field defaults will not produce — Anki, a Kindle book, and a Humanitarians AI volunteer on a Zoom call. The full four-layer platform would be the wrong instrument. The conductor's discipline is to know that.

What this chapter specifies for the conductor is the *decision rule* — the complexity threshold test. Three questions, conjunctive, all three answered yes before the platform's instruments earn their cost. The chapter is naming when the conductor reaches for the simpler arrangement and when she reaches for the heavier one. Crucially, the conductor still exists in Priya's case: somebody is watching what Anki produces, deciding when to switch to a role-play with the volunteer, adjusting the next twenty-minute session. The intelligent textbook is whatever the conductor is conducting.

The chapter runs the experiment by making the threshold test itself a contestable instrument, not a settled law. The book is committing to the test as the current best diagnostic and naming it as the workshop's own construction, subject to revision. That is the experiment-as-product posture: a working instrument, openly held, transparent about its provenance.

---

## Priya

Priya is nineteen. She has lived for six years in a Homes of Hope residence in Hyderabad — a non-governmental residence for children whose families could not keep them safely. She speaks Telugu at home, Hindi when she has to, and English in the careful, partial way of somebody who learned it in school and never had the practice to make it fluent. She has a smartphone. She has free wireless at the residence. She is not poor in the sense that English-speaking readers usually mean when they reach for the word; she is in a residence that feeds her, gives her a bed, and gives her access to the curriculum the Indian school system runs. She is poor in the specific sense that the three most accessible jobs in Hyderabad's employment market — BPO customer service (Concentrix, Genpact, Tech Mahindra), hospital support (Apollo, Yashoda, Continental), NGO administration — *all* require functional English.

The door is closed. She knows it is closed. She has six weeks before her first interview at Concentrix and she has about five hundred job-functional English words to learn, durable enough to use under fifteen-minute walk-in interview pressure without freezing. Greetings. The four canonical question patterns *Tell me about yourself / Why this company / What is your strength / Why should we hire you*. The BPO-specific vocabulary — *queue*, *call disposition*, *first call resolution*, *TAT*, *SLA*. The medical-support vocabulary in case Apollo calls back instead — *triage*, *outpatient*, *referral*, *discharge summary*.

(*Priya is a composite vignette drawn from real learner profiles at Homes of Hope residences in Hyderabad — the same composite used as the running learner-vignette in the spinoff book* Homes of Hope Plus One. *The narrative power of the case does not require pretending she is a single individual; it requires faithfulness to the constraints real Homes of Hope residents face.*)

The tools Priya has access to: her phone. Anki on the phone, free, open-source, runs offline.[^1] A Kindle book on Kindle Unlimited — *Homes of Hope Plus One* — published cheaply on KU specifically because the residence's library budget for English-language vocational books is essentially zero. And a Humanitarians AI volunteer — somebody in my network at Northeastern University's College of Professional Studies, often from the South Asian diaspora, often with industry experience in the BPO sector — who will spend forty-five minutes a week on Zoom with her over the six-week prep cycle. **Zero dollars of platform spend.**

You have just finished Chapter 1. Chapter 1 sketched a four-layer architecture: Book Library, Tic TOC, Adaptive Engine, Measurement Layer. The natural next move is to deploy that architecture for Priya. *Build a personalized adaptive English-acquisition platform for vocational learners in low-resource contexts. Tic TOC her curriculum. Instrument her sessions. Run a within-learner bandit across mode arms. Measure GLP.* I want to be very direct with you: that would be the wrong answer.

For Priya, **Anki is enough**. Not because the architecture is too expensive — though it would be, by orders of magnitude. Because *the structure of her learning problem does not require the architecture*. The right tool is a frequency-ordered Anki deck of 500 BPO-functional words, run daily on her phone before breakfast and again on the bus, with the Humanitarians AI volunteer doing the irreducibly human work the deck cannot encode. The volunteer is *not* a substitute for the platform. The volunteer is the part the platform could not do.

This chapter delivers the diagnostic that produces that answer. I am calling it the **complexity threshold test**. Three questions. All three must answer *yes* for the full architecture to be the right tool. If any one is *no*, simpler tools are sufficient. The chapter then runs the test on two cases — Priya and a medical student learning clinical reasoning — and shows the test producing opposite answers. By the end you will hold the diagnostic and be able to apply it.

A warning. The test is the book's own instrument; it does not exist in the prior literature in this exact form. The three components draw on established distinctions — adaptive sequencing from the ITS literature, live instrumentation from the learning-analytics literature, multi-layered capability build from the ill-structured-problem literature — but the conjunctive three-question form is the book's contribution. Treat it as a working instrument, subject to revision. The reflexive commitment in the workshop CLAUDE.md requires me to say that out loud.

---

## The complexity threshold test

Three questions. Conjunctive. All three must be *yes*.

### Question 1 — Does the learning problem require *adaptive sequencing across concepts that cannot be pre-ordered*?

Adaptive sequencing is what the Tic TOC + Adaptive Engine combination delivers in the four-layer architecture: the *next* thing the learner sees depends on what the learner just showed me about their state. The diagnostic for whether this is necessary:

*Can you write down, in advance, the order in which the concepts must be encountered, and is that order roughly the same for every learner?*

If **yes** — as it is for "the 500 most common BPO interview vocabulary words" or "the 1,200 most common Spanish phrases" or "the 400 questions in the Indian driver's license written-test bank" — adaptive sequencing is *not* necessary. A frequency-ordered deck delivers what is needed.[^2] The cards line up in the right order. Every learner with the same goal needs the same cards in approximately the same sequence.

If **no** — as it is for clinical reasoning, where the next concept the learner needs depends on which misconception they just revealed in the differential — adaptive sequencing *is* necessary. The Tic TOC + Engine apparatus earns its cost.

### Question 2 — Does the learning problem require *live instrumentation*?

Live instrumentation is what the Measurement Layer delivers: the GLP framework's seven friction components captured in real time, not after the fact. The diagnostic:

*Can the learning outcome be assessed adequately by a single end-of-period instrument — a test, an interview, a certification exam — or does the* process *of learning have to be observed continuously to produce the outcome?*

If the former — as it is for vocabulary acquisition (the test is whether Priya can use the word in conversation; either she can or she cannot) — live instrumentation is not necessary. The end-of-period instrument is the interview itself. The Concentrix HR manager will tell us, in fifteen minutes, whether Priya can use the words. No GLP measurement is needed; the assessment is intrinsic.

If the latter — as it is for the diagnostic reasoning that produces a clinician's judgment, where the *process* of arriving at a diagnosis is the thing being assessed, not just the diagnosis itself, and where in a post-2022 world the student may have offloaded the differential to a chatbot in seconds — live instrumentation is necessary. The artifact can no longer be trusted as sole evidence of the process that produced it (Chapter 5 develops this argument as *the decoupling problem*). The seven GLP components must be captured continuously.

### Question 3 — Does the learning problem require a *multi-layered capability build*?

Multi-layered capability is what the integration of Ask AI, Quiz Me, Glimmer, and Case Study delivers in the four-layer architecture: the same learner is moved through different modes as their state changes. The diagnostic:

*Is the target outcome a single capability — vocabulary, procedural knowledge, declarative recall — or a composite of capabilities at different cognitive levels that cannot be built sequentially?*

If single — as it is for "memorize the 500 most common BPO interview vocabulary words" — a multi-mode platform is not necessary. One mode (spaced retrieval practice) activates the right mechanism.

If composite — as it is for "demonstrate clinical reasoning under diagnostic ambiguity in a domain where retrieval, transfer, calibration, and case-pattern recognition all have to be operating simultaneously" — the architecture earns its cost.

### The decision rule

```
if (adaptive_sequencing == yes
    AND live_instrumentation == yes
    AND multi_layered_capability == yes):
    deploy the full four-layer architecture
else:
    deploy simpler tools — Anki, a Kindle book,
    a volunteer call, an LMS-hosted Quiz Me,
    a pre-written CBL session
```

The discipline: the architecture is for the case where *all three* answers are *yes*. A substantial fraction of useful learning problems in the world are not in that case. The book is for the case that needs it. Chapter 2 is the chapter that says — out loud and on the record — that the case is not everywhere.

---

## Running the test on Priya

**Question 1 — Does Priya need adaptive sequencing?**

No. The 500 BPO-functional words can be ordered by frequency in the target corpus — interview transcripts, customer-service call recordings, BPO training scripts. The corpus is publicly available; freelance corpus linguists have already produced ordered lists. Every learner with Priya's goal needs the same words in roughly the same order. Variance in optimal sequence across learners is small relative to variance in within-learner retention. A frequency-ordered deck delivers what she needs.

**Question 2 — Does Priya need live instrumentation?**

No. The outcome is binary: she gets the offer or she doesn't. The Concentrix HR manager will tell us, in a fifteen-minute walk-in interview, whether the words are there. The assessment is intrinsic to the goal. We do not need to capture GLP signals across the six-week prep period to know whether learning happened. The interview will tell us.

**Question 3 — Does Priya need a multi-layered capability build?**

No. The capability is vocabulary acquisition under functional retrieval pressure. One mode — spaced retrieval practice — activates the right mechanism (which I'll specify in the next section). Asking her to also do Glimmer-style generative work on BPO vocabulary, or Case Study reasoning on customer-service scenarios, would not be wrong, exactly. It would be over-engineering. The marginal capability gain is small relative to the friction it adds to her daily review.

**All three answers are *no*. Anki is enough.**

---

## Why Anki actually works for Priya — three mechanisms

I want to show you why the simpler tool is doing real work, not just being cheap. There are three mechanisms, each well-evidenced.

**Mechanism 1: retrieval practice.** Roediger & Karpicke 2006 demonstrated the testing effect with educationally meaningful prose.[^3] Students who studied repeatedly recalled 83% of the material at five minutes, beating the 71% recall of students who took practice tests. At one week, the order reversed: 40% recall after studying-only versus 61% recall after three test trials. The mechanism is *retrieval practice* — the act of pulling information out of memory changes the memory. Anki is a retrieval-practice machine. Each card forces Priya to externalize the answer before the card flips. The meta-analytic effect, Adesope, Trevisan & Sundararajan 2017, is **g = 0.51 for practice tests vs. re-studying** across 188 experiments and 272 effect sizes.[^4] Moderate, well-replicated.

**Mechanism 2: spaced repetition.** Cepeda, Pashler, Vul, Wixted & Rohrer 2006 is the canonical meta-analysis on distributed practice.[^5] 839 assessments across 317 experiments. The finding: spaced reviews produce more durable retention than massed reviews; the optimal inter-study interval scales with the retention horizon. Anki's scheduling algorithm (SM-2 or FSRS) is an implementation of this scheduling principle. Priya benefits from the principle, not from the algorithm sophistication: a Leitner box with daily use would produce most of the same outcomes. The algorithm is a small contributor; the discipline of daily use is most of what matters.

**Mechanism 3: habit-loop adoption.** The largest single contributor to Anki's *outcomes* in real-world use is not algorithmic sophistication — it is the fact that students *use* Anki daily, voluntarily, on their phones. The due-today counter functions as a Zeigarnik-closure mechanic: an unfinished count on a phone screen is a tiny piece of unfinished business the brain wants to close. The streak is gentle commitment. The mobile-first review session is friction-minimum. And the shared-deck community has produced ready-made decks for nearly every vocational target — Priya does not have to *design* a deck. Somebody in the Anki community has already built a 500-card BPO-vocabulary deck; the Humanitarians AI volunteer can hand it to her and say *do these tomorrow morning before breakfast and again on the bus*.

These three mechanisms together explain why Anki produces real learning for vocabulary acquisition. **The mechanisms are specific. The evidence is robust. Anki is enough *because* it activates the right mechanisms for the right problem**, not because it is good enough as a placeholder.

---

## The volunteer is the irreducibly human part

This is the chapter's second load-bearing claim. Anki does the retrieval practice. The Humanitarians AI volunteer does the work Anki cannot encode.

Three specific things the volunteer does:

**Modeling the register.** The volunteer says the words at the pace and accent the BPO interviewer will use. Anki cannot. Pre-recorded audio cannot either — the BPO interviewer's pace is responsive to the candidate's response. The volunteer's pace is responsive too.

**Specifying the role.** The volunteer tells Priya what *"BPO industry"* means in the specific context of Concentrix vs. Genpact vs. Tech Mahindra — that one mostly handles US tech-support tickets, another handles UK financial services, a third handles healthcare claims processing. Anki cannot do this; no deck can know what Priya needs to know about her local job market. This is what Sadler 2013 calls Level-3 pedagogical content knowledge — domain-particular instructional knowledge that *generic* instructional design ignores.[^6] The volunteer carries the PCK the platform cannot encode.

**Calling on Priya by name.** The volunteer recognizes Priya as a person from a context the volunteer also knows. *I came from a residence in Pune. I have done this interview. Here is what they will ask.* The relational signal — somebody who has come from the same situation and made it through — is the irreducibly human part. No chatbot can replace it. Not because chatbots are insufficiently powerful, but because no chatbot has done it.

The Bastani 2025 finding from Chapter 1 is the empirical confirmation of why this matters. The GPT Tutor wrapper — teacher-designed hints, no answer-giving — preserved learning. The GPT Base wrapper — raw chat, helpfulness-default — destroyed learning. The Tutor wrapper *encoded the teacher's pedagogical judgment*. The Base wrapper had no judgment to encode. For Priya, **Anki is the GPT Tutor wrapper for vocabulary** — constrained, retrieval-anchored, low-temperature. The volunteer is the pedagogical judgment Anki cannot encode. Without the volunteer, Anki is still useful — but the missing component is precisely the component that makes the architecture earn its name.

*Human + AI, not human versus AI.* Priya's volunteer is the human. Anki is the AI. Neither works without the other.

---

## The contrast case: a medical student learning clinical reasoning

I want to run the same test on a problem where all three answers come back *yes*, so you can see the test producing opposite outputs on the same diagnostic. The contrast forces the test to be useful — a diagnostic that classifies everything as "simple tool sufficient" would be useless, and a diagnostic that classifies everything as "needs the full architecture" would be over-engineering by default.

**Who.** A second-year medical student at a US allopathic school, beginning the cardiology block.

**What they need to learn.** Differential diagnosis under ambiguity. The same chest-pain presentation may be acute coronary syndrome, pericarditis, dissection, pulmonary embolism, esophageal spasm, costochondritis, or panic. The student needs to learn which features distinguish these, in what order to investigate them, how to update on each piece of evidence, and — most importantly — how to *recognize when their own reasoning is overconfident*. This is the Jonassen 1997 *ill-structured problem*: multiple solutions, fewer manipulable parameters, uncertainty about which concepts are necessary.[^7]

**Question 1 — adaptive sequencing required?** Yes. The next concept the student needs depends on which misconception they just revealed in the case discussion. There is no pre-orderable curriculum for "clinical reasoning" that works for every student in every order. A student who has internalized the difference between pericarditis and ACS but is consistently failing to consider PE in the differential needs a different next case than a student who confidently lists PE but consistently miscalibrates her confidence in the diagnosis.

**Question 2 — live instrumentation required?** Yes. The artifact (the differential written on a scratch pad) cannot be trusted as sole evidence of the reasoning that produced it. Especially not in a post-2022 world where the student may have offloaded the differential to a chatbot in five seconds. The seven GLP friction components have to be captured continuously: Y2 error trajectory coherence (does the student's pattern of errors reveal a consistent misconception or random noise?), Y4 uncertainty calibration (does her confidence match her accuracy?), Y5 social knowledge texture (did she consult the attending? discuss with peers?), Y7 scaffolding response curve. The Chapter 5 measurement layer earns its cost on this problem.

**Question 3 — multi-layered capability build required?** Yes. Clinical reasoning is the composite of retrieval (Quiz Me on the differential's components), inquiry (Ask AI for the prerequisite physiology), case pattern recognition (Case Study on prior presentations), and generative synthesis (Glimmer on a write-up that demonstrates the reasoning trace). No one mode produces the capability. The integration is what produces clinical reasoning.

**All three answers are *yes*. The full architecture is necessary.**

Same diagnostic. Two cases. Completely different answers. That is the test working.

---

## Worked example: side-by-side, full pages

Two columns. Same diagnostic instrument. Two learners. The point of the worked example is that the test is not "what is the learner's budget" or "what tools does the learner have access to." The test is about the *structure of the learning problem*. Even if Priya had a $500,000 platform budget, the threshold test would still resolve to *Anki is enough* for vocabulary acquisition. The constraint is not the budget. The constraint is the structure of the problem.

| | **Priya — BPO interview vocabulary** | **Medical student — clinical reasoning** |
|---|---|---|
| **Goal** | 500 job-functional English words, durable enough to use in a 15-minute walk-in interview | Differential diagnosis under ambiguity, calibrated confidence, transfer across presentations |
| **Time horizon** | 6 weeks to first interview | 2 years to clinical rotations |
| **Assessment** | The interview itself (intrinsic, end-of-period, binary outcome) | Composite — written exam, OSCE, clinical evaluation, transfer-bearing case |
| **Q1: adaptive sequencing?** | No — pre-orderable by frequency | Yes — next concept depends on revealed misconception |
| **Q2: live instrumentation?** | No — end-of-period assessment is the goal | Yes — artifact decoupled from process; GLP capture required |
| **Q3: multi-layered build?** | No — single mode (retrieval practice) | Yes — retrieval, inquiry, case pattern, generative synthesis |
| **Test result** | All three *no* → simpler tools | All three *yes* → full architecture |
| **Right tool** | Anki + Kindle book + Humanitarians AI volunteer | Four-layer architecture |
| **Marginal cost of "upgrading"** | $120/student/year for capability not needed + displacement of volunteer relationship + GPT Base risk on chatbot tutor | None — the architecture is the floor |
| **Risk of "downgrading"** | None — the simpler tool *is* the right tool | High — the artifact-process decoupling produces unmeasured failure |

Notice the bottom rows. For Priya, "upgrading" to the full architecture has a real cost — and not the obvious one. The obvious cost is the $24,000/year platform fee per cohort of 200 students. The non-obvious cost is **the displacement of the volunteer relationship**. If you swap the Humanitarians AI volunteer for a chatbot tutor, the chatbot will not say *"I came from a residence in Pune. Here is what they will ask."* The chatbot will produce GPT Base behavior in the Bastani sense. Net effect: cost up, durable learning down.

This is the case Exercise 2.2 asks you to argue.

---

## The tool is not the problem. The context is the problem.

This is the chapter's pivot line.

The same smartphone that is a TikTok delivery system at 11 p.m. — eight hours scrolling, engagement metrics climbing, durable learning at zero — is a vocabulary acquisition engine at 7 a.m. with an Anki deck and a volunteer call scheduled for Saturday. Same hardware. Same network. Same girl. **Different context.**

The Horvath move (*phones are bad for learning, take them away*) and the Khan move (*phones are great for learning, deploy chatbots*) are arguing about the wrong variable. The variable is not the hardware. The variable is the *wrapper* around the hardware — what the platform commits the device to doing, and what the surrounding human relationships commit the platform to. The PISA 2022 finding — students who spend 5–7 hours per day on digital devices for leisure score about 49 points lower in mathematics than students who spend up to one hour, even after adjusting for socioeconomic profile — is real and important.[^8] It is also a description of *unguarded leisure device use at saturating dosages*. It is not a description of what Priya is doing. Priya is doing low-dosage, high-discipline, retrieval-anchored, human-supported device use. The two cases are different by design.

Conflating them is the category error Chapter 3 will name explicitly as the *Butter Knife Fallacy* — judging the scalpel's potential by observing its average misuse. The hardware is not the variable. The wrapper is the variable. *The platform is opinionated; the model has no opinions of its own.* The same is true of the device.

---

## Common misconceptions

**Misconception 1: "Anki is a 22-year-old desktop app with a clunky interface. You can't possibly be recommending it as state-of-the-art."**

Plausible. The visual aesthetic of the Anki desktop client is uncompromising in a way that does not photograph well in a product demo. AnkiDroid and AnkiMobile are actively maintained, FSRS is current research, and the AnKing medical deck is used by a large fraction of US medical students preparing for Step 1.[^9] The product is not new and the product is not exciting. That is not the same as the product being wrong. For frequency-orderable, end-of-period-assessable, single-mode-capability problems, the field's revealed preference over two decades is overwhelming. The medical-student community has converged on Anki for first-pass memorization. The right read is not "Anki is old and therefore wrong"; it is "the right tool for this problem looks like Anki because the problem has a stable, well-understood structure that Anki was built for."

**Misconception 2: "If Anki is enough for vocabulary acquisition, why is anyone building EdTech for vocabulary acquisition at all?"**

Plausible-adjacent. There is real EdTech being built for vocabulary acquisition — Memrise, Duolingo, Quizlet, Mango — and some of it is excellent. The honest reading is *Duolingo and Memrise added the things Anki does not do well*: gamification design that lowers the activation energy for daily use, professionally-recorded audio for accent modeling, branching narrative for engagement, social features for shared progress. For learners whose problem is *adoption* — they would benefit from spaced retrieval but will not open Anki — these platforms add real value, and the threshold test correctly classifies them as one-mode tools serving a one-mode problem. The structural argument is *not* "all vocabulary EdTech is over-engineered." It is "*adaptive, instrumented, multi-mode* vocabulary EdTech is over-engineered." Duolingo is not running a within-learner bandit across mode arms; it is running a spaced-retrieval engine wrapped in a habit-loop design. The test correctly returns *simpler tools sufficient* for both Anki and Duolingo on this problem.

**Misconception 3: "The volunteer-call model doesn't scale, so the chapter's recommendation is impractical."**

Plausible. That is a separate question. Chapter 10 addresses scale and economics in detail. Chapter 2's argument is qualitative: *for the problems where the simpler tool is enough, scaling is not the binding constraint either.* Anki scales for free, and human volunteers scale at the rate networks like Humanitarians AI can recruit them. Recruitment is rate-limiting; it is not the same constraint as platform engineering. Crucially, **the four-layer architecture has its own scale cost the simpler model does not** — the GLP measurement layer, the within-learner bandit, the content adaptation library, the Tic TOC curriculum design sessions. Comparing "Anki + volunteer at scale" to "four-layer architecture at scale" on a single dimension (recruitment) ignores the four dimensions where the four-layer architecture is the more expensive scaling problem.

---

## Exercises

### Exercise 2.1 — Apply the threshold test to three problems (Apply)

Apply the three-question complexity threshold test to each of the following learning problems. For each: state your answer to each question with one sentence of justification. State your final classification (*simpler tools sufficient* or *full architecture required*). Then specify the minimum viable tool set you would actually deploy.

(a) **Corporate compliance training.** A 4,000-employee hospital system is rolling out the annual HIPAA refresher for administrative staff. End-of-period assessment is a 25-question multiple-choice post-test. Required for accreditation. Twenty hours of CME budget per employee.

(b) **Surgical residency clinical decision-making.** A general surgery residency program wants to systematically improve residents' decision-making in the first 48 hours of a complex post-op course. The capability is judgment under ambiguity: when to escalate, when to wait, when to operate again. The assessment is composite: M&M conference performance, oral boards, attending evaluations.

(c) **AWS Solutions Architect Associate certification prep.** A self-funded mid-career engineer is preparing for the AWS SAA-C03 exam. The exam is multiple-choice with a fixed item bank. The candidate has 8 weeks. The capability is recall plus pattern-recognition on standardized scenarios.

Produce a deliverable: a one-page table with all three problems, all three answers per problem, the classification, and the tool set.

### Exercise 2.2 — Argue against a vendor (Evaluate, produces something)

A well-meaning EdTech vendor visits Homes of Hope Hyderabad and proposes replacing Priya's Anki deck with their full adaptive platform. The platform offers personalized learning paths, real-time analytics, a chatbot tutor, and a teacher dashboard. The annual cost is $24,000 per cohort of 200 students — $120 per student per year.

Write a 600-word memo to the Homes of Hope board doing three things: (1) walk through the complexity threshold test for Priya's problem, showing why all three answers are *no*; (2) name three specific marginal-gain claims the vendor would have to make for the spend to be justified, and assess whether each is supported by the literature you have so far (Chapter 3 delivers the full evidence base; Chapters 1–2 are sufficient for this exercise); (3) name the one non-obvious cost of "upgrading" — the displacement of the volunteer relationship — and argue, using the Bastani PNAS finding from Chapter 1, why this cost is structural, not optional.

### Exercise 2.3 — Move the test boundary (Analyze)

The chapter argues that vocabulary acquisition for vocational English is *clearly* a simpler-tools problem. Construct a thought experiment: what would have to change about Priya's learning problem to make the full four-layer architecture the right answer? You may modify the goal, the learner population, the time horizon, the assessment, or the surrounding context — but you must change something *real*, not stipulate it away.

Write a 500-word analysis identifying the *single most economical* modification — the smallest change to Priya's problem that flips the threshold test to *all three yes*. Defend why that modification is necessary and sufficient. Identify which of the three test questions is the easiest to flip, and which is the hardest. The exercise is meant to give you a feel for where the test's boundary actually lives.

---

## What would change my mind

The chapter's central claim is that the complexity threshold test correctly classifies a substantial majority of useful learning problems as *simpler tools sufficient*, and that the four-layer architecture is the right answer only when all three questions return *yes*. Three findings would force me to revise:

A rigorous RCT showing that a fully-instrumented adaptive platform produces durable vocabulary retention *significantly* better than Anki plus a human tutor for a population structurally similar to Priya's — low-resource, high-motivation, single-mode capability goal. The literature does not currently include such a study, and the test bets that if it ran, the platform would not win by enough to justify the spend. If the study ran and the platform won decisively, the test needs revision — possibly a fourth question about adaptive optimization across learners with different motivational profiles. Or: evidence that the AnKing deck and similar shared-deck communities do *not* in fact produce the medical-student board-pass-rate effects they are credited with. If the revealed-preference pattern turns out to be selection effect rather than instructional effect, the case for Priya weakens by analogy. Or: a demonstration that the complexity threshold test produces systematic false negatives — classifies problems as "simple tool sufficient" that, on careful study, actually require the architecture. One false negative would be a curiosity; a pattern would be a problem the chapter would have to address.

---

## Still puzzling

1. What is the test's behavior at the boundary of well-structured and ill-structured problems? The Jonassen 1997 distinction is conceptually clear and operationally fuzzy. The chapter uses the distinction without resolving the fuzziness. Phlebotomy training — vocabulary plus procedural skill under live patient interaction — fails the test on at least one axis but is structurally borderline. The chapter treats it as a judgment call; that is honest but not satisfying.

2. Is the volunteer-relationship effect specific to the Humanitarians AI / Homes of Hope network, or does it generalize? The chapter bets generalization — that any network pairing a learner with somebody who has done the target job produces the same value. The bet is plausible but unproven. The mechanism (Sadler 2013 PCK; the relational signal of having-come-from-the-same-context) is general; the *scale* at which it can be deployed is what remains uncertain.

3. How does the threshold test interact with motivation? Priya is highly motivated — the door is closed; the job is the way out. The test does not address motivation directly. A reader might worry that *Anki is enough* relies on Priya's motivation in a way the test does not capture. The chapter acknowledges this: motivation is a hidden variable the test does not yet instrument. Whether motivation should be a fourth question, or whether the existing three questions already implicitly handle it through "live instrumentation required," is an open design question.

4. What about cases that fail the test on exactly one axis? The chapter classifies these as *simpler tools sufficient* because the test is conjunctive. But corporate compliance training (Exercise 2.1a) is arguably borderline — single-mode declarative recall, end-of-period assessment, but with a capability component (pattern recognition of compliance-relevant situations) that is a little more than pure vocabulary. Does the conjunctive test correctly handle the one-axis-failure case, or does it produce false-positive *simpler tools* answers in the borderline middle?

---

## Bridge to Chapter 3

The complexity threshold test claims that certain tools work for certain problems. Anki works for Priya because retrieval practice plus spaced repetition plus habit-loop adoption activates the right mechanisms for vocabulary acquisition under retrieval pressure. The four-layer architecture works for the medical student because clinical reasoning is composite, ill-structured, and live-instrumented.

How do we know any of this? Where does the evidence sit? What did Horvath actually prove, what did he overreach on, what did Khan get right, what does Bastani PNAS 2025 license as a design decision, what does the ITS literature say that the generative-AI literature does not, what does Thistlethwaite 2012 license about case-based learning?

Chapter 3 delivers the evidence base. Every architecture chapter after Chapter 3 will cite rather than argue. The reader who has finished Chapter 3 will hold the diagnostic for spotting cherry-picked EdTech evidence claims when they encounter them — which they will, often, from vendors and from the literature. The book gets sharper from here.

---

## References

[^1]: Anki / AnkiDroid / AnkiMobile. Open-source spaced repetition flashcard software. https://apps.ankiweb.net/

[^2]: For the frequency-ordered curriculum-design principle, see the BPO interview corpus literature and the broader frequency-sequencing pedagogy summarized in [research note: `concept-sequencing-research.md`]. Heyworth, J. (2024). *Lemonade Stand Lessons*. [verify publication details].

[^3]: Roediger, H. L., III, & Karpicke, J. D. (2006). Test-enhanced learning: Taking memory tests improves long-term retention. *Psychological Science*, 17(3), 249–255. https://pubmed.ncbi.nlm.nih.gov/16507066/

[^4]: Adesope, O. O., Trevisan, D. A., & Sundararajan, N. (2017). Rethinking the use of tests: A meta-analysis of practice testing. *Review of Educational Research*, 87(3), 659–701.

[^5]: Cepeda, N. J., Pashler, H., Vul, E., Wixted, J. T., & Rohrer, D. (2006). Distributed practice in verbal recall tasks: A review and quantitative synthesis. *Psychological Bulletin*, 132(3), 354–380. https://pubmed.ncbi.nlm.nih.gov/16719566/

[^6]: Sadler, P. M., Sonnert, G., Coyle, H. P., Cook-Smith, N., & Miller, J. L. (2013). The influence of teachers' knowledge on student learning in middle school physical science classrooms. *American Educational Research Journal*, 50(5), 1020–1049.

[^7]: Jonassen, D. H. (1997). Instructional design models for well-structured and ill-structured problem-solving learning outcomes. *Educational Technology Research and Development*, 45(1), 65–94. https://doi.org/10.1007/BF02299613

[^8]: OECD. (2023). *PISA 2022 Results (Volume I): The State of Learning and Equity in Education*. OECD Publishing. https://www.oecd.org/en/publications/pisa-2022-results-volume-i_53f23881-en.html [49-point math gap at 5–7 hours/day vs. up to 1 hour leisure digital-device use, adjusted for SES]

[^9]: Bastani PNAS 2025 — full citation in Chapter 1, footnote 3. AnKing shared deck — community-maintained Anki deck for US medical school Step 1 preparation. https://www.ankingmed.com/ [verify current canonical URL]

---

*Chapter 3: The Evidence Base →*
