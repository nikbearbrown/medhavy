# Research Notes — Chapter 2: When Anki Is Enough

*Working pantry document for the Medhavy book project. Research underpinning Chapter 2 — the calibration chapter that prevents the rest of the book's architecture from being misapplied. Citation-dense. Companion to `quiz-me-research.md`, `quiz-me-habit-research.md`, `educational-media-economics-research.md`, the Homes of Hope Plus One book (Priya material), and `domain-specific-instruction-research.md`.*

*Compiled 2026-05-17 for the chapter-writer subagent. Maintained for revision.*

---

## Chapter summary

This chapter is the book's honest check. After Chapter 1 names two failure modes and sketches the four-layer architecture, an obvious problem arises: the architecture is expensive — in design time, in instrumentation, in measurement-layer engineering, in the cognitive load it asks of the learner — and it is the wrong answer for many learning problems. Some learners need a flashcard deck and a phone call from somebody who came from the job they are entering. Putting them in front of a full intelligent textbook is, in the most literal sense, malpractice: it imposes a cost they do not need to pay for a benefit they do not need to receive. The chapter delivers the *complexity threshold test* as the diagnostic. Three questions: (1) Does this learning problem require **adaptive sequencing across concepts that cannot be pre-ordered** — i.e., where the right next thing depends on what the learner just showed me about their state? (2) Does it require **live instrumentation** — i.e., does the learning evidence have to be captured continuously, in-context, for a measurement layer to function? (3) Does it require a **multi-layered capability build** — i.e., is the target outcome a composite of vocabulary, reasoning, judgment, and transfer that cannot be assembled from a single-mode tool? If the answer to all three is *no* — as it is for Priya, 19, six years in Homes of Hope Hyderabad, Telugu and basic English, needing a 500-word job-functional vocabulary to clear the door at a BPO interview — the right tool is Anki and a human volunteer from the sector she is entering. If the answer to all three is *yes* — as it is for a medical student learning clinical reasoning under diagnostic ambiguity — the full architecture is necessary. The chapter's load-bearing line: *the tool is not the problem; the context is the problem*. The same phone that is a TikTok delivery system for a girl scrolling at the residence is a vocabulary-acquisition engine for the same girl studying for a Concentrix interview. Same hardware. Different context. The intelligent textbook field has been arguing about the hardware. The right question is about the context.

---

## A. Conceptual foundations

### A.1 Why the chapter exists at all

Chapter 1 risks producing two unhelpful readings. The Charles Fadel reader may walk away thinking *the only honest move is the full four-layer architecture*. The developer reader may walk away thinking *the more layers the better*. Both are wrong. The complexity threshold test exists because the four-layer architecture is a *minimum viable architecture for problems that need it* — not a *default architecture* that should be the answer to every learning problem. The book's reflexive commitment (CLAUDE.md §4) requires the chapter to specify the conditions under which its own central proposal does not apply. Chapter 2 is that specification.

The structural error to prevent: an EdTech vendor reading Chapter 1, deciding their next product needs all four layers, and shipping the four-layer architecture into a context that does not need it. The result is over-engineering, over-instrumentation, over-cost — and, crucially, the *displacement of the simpler tool that was already working*. Priya does not need a measurement layer; she needs to know what "BPO" means and how to answer "Tell me about yourself" in fifteen seconds. Anki delivers the first; a Humanitarians AI volunteer who once worked at Concentrix delivers the second. The full architecture would interfere with both.

### A.2 The complexity threshold test — three questions, all must be *yes*

The test is conjunctive. All three must be true for the full architecture to be the right answer. If any one is *no*, simpler tools are sufficient.

**Question 1 — Does the learning problem require adaptive sequencing across concepts that cannot be pre-ordered?** Adaptive sequencing is what the Tic TOC + Adaptive Engine combination delivers: the *next* thing the learner sees depends on what the learner has just shown about their state. The diagnostic for whether this is necessary: *can you write down, in advance, the order in which the concepts must be encountered, and is that order the same for every learner?* If yes — as it is for "500 BPO-functional vocabulary words" or "the 1,200 most common Spanish phrases" — adaptive sequencing is not necessary. A frequency-ordered deck (`concept-sequencing-research.md` §1 on Zipf-frequency curriculum design; *Lemonade Stand Lessons* / Heyworth 2024) delivers what is needed. If no — as it is for clinical reasoning, where the next concept the learner needs depends on which misconception they just revealed — adaptive sequencing is necessary, and the Tic TOC + Engine apparatus earns its cost.

**Question 2 — Does the learning problem require live instrumentation?** Live instrumentation is what the Measurement Layer delivers: the GLP framework's seven friction components captured in real time, not after the fact. The diagnostic: *can the learning outcome be assessed adequately by a single end-of-period instrument (a test, a job interview, a certification exam), or does the *process* of learning have to be observed continuously to produce the outcome?* If the former — as it is for vocabulary acquisition (the test is whether Priya can use the word in conversation; either she can or she cannot) — live instrumentation is not necessary. If the latter — as it is for the diagnostic reasoning that produces a clinician's judgment, where the *process* of arriving at a diagnosis is the thing being assessed, not just the diagnosis itself — live instrumentation is necessary.

**Question 3 — Does the learning problem require a multi-layered capability build?** Multi-layered capability is what the integration of Ask AI, Quiz Me, Glimmer, and Case Study delivers: the same learner is moved through different modes as their state changes. The diagnostic: *is the target outcome a single capability (vocabulary, procedural knowledge, declarative recall) or a composite of capabilities at different cognitive levels that cannot be built sequentially?* If single — as it is for "memorize the 500 most common BPO interview vocabulary words" — a multi-mode platform is not necessary. If composite — as it is for "demonstrate clinical reasoning under diagnostic ambiguity in a domain where retrieval, transfer, calibration, and case-pattern recognition all have to be operating simultaneously" — the architecture earns its cost.

**The decision rule.** If `(adaptive_sequencing == yes) && (live_instrumentation == yes) && (multi_layered_capability == yes)`, the full architecture is the right answer. Otherwise, simpler tools — Anki, a Kindle book, a volunteer call, a CBL session led by a human, a low-instrumentation LMS — are the right answer. The chapter's discipline: the book is for the case where all three are *yes*, and a substantial fraction of useful learning problems are not in that case.

### A.3 Priya's case — why the test resolves to "Anki is enough"

The opening case. Specification:

- **Who Priya is.** A composite vignette drawn from real learner profiles at Homes of Hope residences in Hyderabad (see HoH+1 book.md). Age 19. Six years in a Homes of Hope residence — a non-governmental orphanage / residence — in Secunderabad/Hyderabad. Speaks Telugu (first language), Hindi (functional), basic English. Has a smartphone. The three most accessible jobs in the Hyderabad employment market — BPO customer service (Concentrix, Genpact, Tech Mahindra), hospital support (Apollo, Yashoda, Continental), NGO administration — all require functional English. The door is closed if her English is not job-functional.
- **What she needs to learn.** Approximately 500 job-functional English words and phrases (greetings, the question patterns *"Tell me about yourself" / "Why this company?" / "What is your strength?"*, the BPO-specific vocabulary of *queue / call disposition / first call resolution / TAT / SLA*, the medical-support vocabulary of *triage / outpatient / referral / discharge summary*). She needs them durable enough to use in a fifteen-minute walk-in interview without freezing.
- **What tools she has.** A smartphone. Free wireless at the residence. A Kindle book (HoH+1 published cheaply on Kindle Unlimited, specifically because the residence's library budget for English-language vocational books is essentially zero). Anki on her phone (free, open-source, runs offline). A Humanitarians AI volunteer — a Northeastern University CPS Bear has organized — who once worked at a Hyderabad BPO and who will spend forty-five minutes per week on Zoom with her over a six-week prep cycle. Zero dollars of platform spend.
- **What the complexity threshold test says about her case.** Question 1: does she need adaptive sequencing? No. The 500 words can be ordered by frequency in the target corpus (BPO interview transcripts, customer service call recordings). Every learner with her goal needs the same words in roughly the same order. Question 2: does she need live instrumentation? No. The outcome is binary — she gets the offer or she doesn't. The end-of-period assessment is the interview itself. Question 3: does she need a multi-layered capability build? No. The capability is vocabulary acquisition under functional retrieval pressure. One mode — spaced retrieval practice — delivers it. *All three answers are no. Anki is enough.*

The chapter's discipline: this case is not a curiosity. It is the *majority* of useful learning problems in the world. Vocabulary acquisition for vocational English. Driver's license study. Certification exam prep (PMP, AWS, USMLE Step 1 first-pass memorization, NCLEX). Religious-text memorization. Foreign-language verb conjugation. The four-layer architecture is for the *minority* of problems that fail the test. The chapter's job is to make the developer reader and the Charles Fadel reader honest about that asymmetry.

### A.4 Why Anki actually works for Priya — three mechanisms

The chapter must show why the simpler tool is doing real work, not just being cheap. Three mechanisms from `quiz-me-research.md` and `quiz-me-habit-research.md`:

- **Retrieval practice.** Roediger & Karpicke 2006 (*Psychological Science* 17(3), 249–255) demonstrated the testing effect with educationally meaningful prose: at five-minute retention, repeated studying beats testing (83% recall vs. 71%); at one-week retention, the order reverses (40% recall after studying-only vs. 61% recall after three test trials). The mechanism is retrieval practice — the act of pulling information out of memory changes the memory. Anki is built on this mechanism. Priya is doing the work the mechanism predicts will produce durable retention. The meta-analytic effect, Adesope, Trevisan & Sundararajan 2017 (*Review of Educational Research* 87(3), 659–701), is **g = 0.51** for practice tests vs. re-studying — a moderate, well-replicated effect across 188 experiments and 272 effect sizes.
- **Spaced repetition.** Cepeda, Pashler, Vul, Wixted & Rohrer 2006 (*Psychological Bulletin* 132(3), 354–380) is the canonical meta-analysis on distributed practice. 839 assessments across 317 experiments and 184 articles. The finding: spaced reviews produce more durable retention than massed reviews, with the optimal interstudy interval (ISI) increasing as retention interval lengthens. The Anki algorithm (SM-2, FSRS) is an implementation of this scheduling principle. Priya is benefiting from the principle, not from the algorithm sophistication: a Leitner box with daily use would produce most of the same outcomes. (`quiz-me-research.md` §1 covers this distinction in full.)
- **Habit-loop adoption.** The largest single contributor to Anki's *outcomes* in real-world use is not algorithmic sophistication — it is the fact that students *use* it daily, voluntarily, on their phones. `quiz-me-habit-research.md` details the design that makes this so: the due-today counter as a Zeigarnik-closure mechanic, the streak as gentle commitment, the mobile-first review session, the shared-deck community that delivers ready-made decks for nearly every vocational target. Priya does not have to design her own deck. The Homes of Hope volunteer can hand her a deck of 500 cards and say *do them tomorrow morning before breakfast and again on the bus*.

These three mechanisms together explain why Anki produces real learning for the vocabulary acquisition problem. The chapter's discipline: this is not a soft "any tool can work if used well" claim. The mechanisms are specific. The evidence is robust. Anki is enough *because* it activates the right mechanisms for the right problem, not because it is good enough as a placeholder.

### A.5 The volunteer is the irreducibly-human part

This is the second load-bearing claim of the chapter, and the one that pulls the Medhavy thesis into Priya's case. Anki does the retrieval practice. The Humanitarians AI volunteer — Bear's network: students from Northeastern University's College of Professional Studies, often from the South Asian diaspora, often with industry experience in the BPO sector — does the irreducibly human work:

- **Modeling the register.** The volunteer says the words at the pace and accent the BPO interviewer will use. Anki cannot do this. Pre-recorded audio cannot either, because the interviewer's pace is responsive to the candidate's response. The volunteer's pace is responsive too.
- **Specifying the role.** The volunteer tells Priya what *"BPO industry"* means in the specific context of Concentrix vs. Genpact vs. Tech Mahindra — that one mostly handles US tech-support tickets, another handles UK financial services, a third handles healthcare claims processing. Anki cannot do this; the deck cannot know what Priya needs to know about her local job market.
- **Calling on Priya by name.** The volunteer recognizes Priya as a person from a context the volunteer also knows. *I came from the residence in Pune. I have done this interview. Here is what they will ask.* The relational signal — somebody who has come from the same situation, with the same constraints, and made it through — is the irreducibly human part. No chatbot can replace it because no chatbot has done it.

The Bastani 2025 finding (`ask-ai-research.md`) is the empirical confirmation of why this matters. The GPT Tutor wrapper — teacher-designed hints, no answer-giving — preserved learning. The GPT Base wrapper — raw chat, helpfulness-default — destroyed learning. The Tutor wrapper *encoded the teacher's pedagogical judgment*. The Base wrapper had no judgment to encode. For Priya, Anki is the GPT Tutor wrapper for vocabulary (constrained, retrieval-anchored, low-temperature). The volunteer is the pedagogical judgment Anki cannot encode. Without the volunteer, Anki is still useful — but the missing component is precisely the component that makes the architecture earn its name. *Human + AI, not human versus AI*. Priya's volunteer is the human. Anki is the AI. Neither works without the other.

### A.6 The tool is not the problem. The context is the problem.

This is the chapter's pivot line. The same smartphone that is a TikTok delivery system at 11 p.m. — eight hours scrolling, engagement metrics climbing, durable learning at zero — is a vocabulary acquisition engine at 7 a.m. with an Anki deck. Same hardware. Same network. Same girl. Different context.

The Horvath move ("phones are bad for learning, take them away") and the Khan move ("phones are great for learning, deploy chatbots") are arguing about the wrong variable. The variable is not the hardware. The variable is the wrapper around the hardware — what the platform commits the device to doing, and what the surrounding human relationships commit the platform to. Bear's TtT essays make this argument from inside the classroom. Medhavy's Chapter 2 makes it from inside Priya's life. The point is the same: the platform is opinionated. The model has no opinions of its own. *And the same is true of the device.*

The PISA 2022 finding (49-point math score gap at 5–7 hours of leisure digital device use; `01-what-is-an-intelligent-textbook_notes.md` §A) measures *unguarded* device use at saturating dosages. It does not measure what Priya is doing. Priya is doing low-dosage, high-discipline, retrieval-anchored, human-supported device use. The two cases are different by design. Conflating them is the Horvath-side category error the chapter must name without arguing it (Chapter 3 carries the argument).

---

## B. Domain examples and cases

### B.1 Priya (Anki is enough — all three answers are *no*)

Detailed in §A.3 and §A.5. The opening case. The chapter's central worked example.

### B.2 A second "Anki is enough" case — driver's license written test

The chapter benefits from a second instance to show the pattern is not specific to vocabulary acquisition. The Indian driver's license written exam: roughly 400 questions in a public bank, frequency-orderable, single-mode (declarative recall), end-of-period assessable (you pass or you don't), no live-instrumentation requirement. *All three threshold questions resolve to no.* A frequency-ordered Anki deck plus the official rulebook, used for two weeks before the test, produces a pass rate that the full architecture cannot meaningfully improve on. The marginal value of an adaptive engine and a measurement layer is essentially zero for this problem. The cost is real.

The pattern generalizes: any learning problem whose target is *durable recall of a finite, pre-orderable, well-structured corpus* fails the complexity threshold test. The right tool is retrieval practice with spaced scheduling and a habit-loop interface. Anki is the existing best-in-class implementation. (The book does not need to *build* Anki.)

### B.3 The medical-school clinical-reasoning case (all three answers are *yes*)

The contrast case the chapter needs to make the threshold test legible. Specification:

- **Who.** A second-year medical student at a US allopathic school, beginning the cardiology block.
- **What they need to learn.** Differential diagnosis under ambiguity. The same chest-pain presentation may be acute coronary syndrome, pericarditis, dissection, pulmonary embolism, esophageal spasm, costochondritis, panic. The student needs to learn which features distinguish these, in what order to investigate them, how to update on each piece of evidence, and — most importantly — how to *recognize when their own reasoning is overconfident*. This is the Jonassen 1997 ill-structured problem (`glimmer-research.md`): multiple solutions, fewer manipulable parameters, uncertainty about which concepts are necessary.
- **What the complexity threshold test says.** Question 1: adaptive sequencing required? Yes — the next concept the student needs depends on which misconception they just revealed in the case discussion. There is no pre-orderable curriculum for "clinical reasoning" that works for every student. Question 2: live instrumentation required? Yes — the artifact (the differential diagnosis written on a scratch pad) cannot be trusted as sole evidence of the reasoning that produced it, particularly in a post-2022 world where the student may have offloaded the differential to a chatbot. The seven GLP friction components must be captured continuously: Y2 error trajectory, Y4 uncertainty calibration, Y5 social knowledge texture (did they consult the attending? did they discuss with peers?), Y7 scaffolding response. Question 3: multi-layered capability build required? Yes — clinical reasoning is the composite of retrieval (Quiz Me on the differential's components), inquiry (Ask AI for the prerequisite physiology), case pattern recognition (Case Study on prior presentations), and generative synthesis (Glimmer on a write-up that demonstrates the reasoning trace). *All three answers are yes. The full architecture is necessary.*

The contrast is the chapter's pedagogical move. Same threshold test. Two cases. Completely different answers. The reader walks away with the test as an instrument they can apply.

### B.4 A "fails on one axis" case

The chapter benefits from a case that fails the threshold on exactly one axis, to show the test's edge behavior. Candidate: corporate compliance training (e.g., annual HIPAA refresher for hospital administrative staff).

- Adaptive sequencing required? No — the content is pre-orderable.
- Live instrumentation required? Arguably no — the outcome is end-of-period (the post-test).
- Multi-layered capability build required? Arguably yes — the capability is recognition of compliance-relevant situations, which is closer to a multi-mode (declarative + pattern + transfer) capability than to pure vocabulary recall.

The chapter's call: this fails the conjunctive test (two of three are *no*). A well-designed Quiz Me with case scenarios — the existing best-practice corporate-LMS pattern — is sufficient. The full architecture is over-engineering. Sample edge cases like this earn the test's rigor; the test is useful precisely because it disqualifies problems that look complex but aren't.

### B.5 The vendor-overreach case

The third assessable exercise the chapter needs. The case: a well-meaning EdTech vendor visits Homes of Hope Hyderabad and proposes replacing Priya's Anki deck with their full adaptive platform. The platform offers personalized learning paths, real-time analytics, a chatbot tutor, and a teacher dashboard. The annual cost is $24,000 per cohort of 200 students. The chapter walks through the honest cost-benefit:

- **Marginal learning gain.** The platform offers adaptive sequencing across concepts that *do not need to be adaptively sequenced* (frequency-ordered vocabulary). Marginal gain: ~zero. The platform offers live instrumentation against an end-of-period assessment (the interview). Marginal gain: ~zero. The platform offers a multi-layer build for a single-mode capability (vocabulary recall under retrieval pressure). Marginal gain: ~zero.
- **Marginal cost.** $120/student/year for capability the threshold test says is not needed. Plus the cost of displacing the volunteer relationship by adding a chatbot tutor: the platform's tutor will not say *"I came from the residence in Pune. Here is what they will ask."* The platform's chatbot will produce GPT Base behavior (`ask-ai-research.md`). Net effect: cost up, durable learning down.
- **The honest answer.** The vendor's offer is well-intentioned and structurally wrong for this problem. The Charles Fadel reader who can read this analysis is the reader the book is trying to produce.

---

## C. Connections and dependencies

### C.1 Within-book connections

- **Backward to Chapter 1.** Chapter 1 ended with the architecture sketch. Chapter 2 immediately pulls back: *the architecture is not the universal answer*. The reader who skipped Chapter 2 (Bloom level: Evaluate; load-bearing: no, but loses calibration) will get a sharper version of the architecture and may over-deploy it. The chapter is skippable; readers who skip it lose calibration. The bridge from Chapter 1 to Chapter 2: *Before the architecture is introduced, the reader needs the honest check: for some learning problems, the right answer is a simpler tool*.
- **Forward to Chapter 3.** The complexity threshold test claims certain tools work for certain problems. Chapter 3 ("The Evidence Base") delivers the evidence — for retrieval practice, for spaced repetition, for ITS, for CBL, for generative assignment. Chapter 2 anchors Chapter 3 by giving the reader a worked-out case where they know which evidence applies (Anki: retrieval practice + spaced repetition + habit-loop) and which doesn't (ITS, CBL, generative assignment are not the right mechanisms for Priya).
- **Forward to Chapter 7 (Adaptive Engine).** When the engine selects a mode for a learner, the threshold test is the *outer envelope* of the engine's decision space. If the threshold test fails — i.e., the problem doesn't need the architecture — the engine should not be making mode-selection decisions; the system should be running pure Quiz Me. Chapter 7 names this as the engine's *zero-information state* baseline.
- **Forward to Chapter 10 (Economics).** The economics chapter quantifies the cost of the architecture and the cost of the simpler alternatives. Chapter 2 is the qualitative version of the economics argument: the *minimum viable* tool is the right tool when it is sufficient. Chapter 10 makes the quantitative case.

### C.2 Cross-pantry dependencies

- **`quiz-me-research.md`** carries the retrieval-practice canon (Roediger & Karpicke 2006, Adesope 2017, Pan & Rickard 2018), the spacing-effect canon (Cepeda 2006/2008), the FSRS/SM-2 scheduling-algorithm distinction, the medical-application evidence (USMLE / Anki / Step 1 first-pass). **Use this note for any specific number on retrieval-practice or spacing-effect magnitudes.** Chapter 2 cites *g* = 0.51 (Adesope) and the Roediger-Karpicke immediate-vs.-delayed reversal; both are anchored there.
- **`quiz-me-habit-research.md`** carries the habit-loop design literature (Fogg, Eyal, Wood), the gamification and Zeigarnik-closure mechanics, the daily-due-count adoption pattern, the shared-deck community as the social layer. **Use this note for why Priya keeps using Anki**, not just why it works in principle.
- **`educational-media-economics-research.md`** carries the Sesame Street precedent for high-quality educational media at low per-learner cost ($5/child/year), and the minimum-viable-audience cost-collapse argument. Chapter 2 uses this lightly — *the high-quality-cheap pattern is not new, Sesame Workshop did it in 1969* — to defang the implicit "but cheap means low-quality" objection.
- **`domain-specific-instruction-research.md`** carries the Sadler 2013 Level-3 specificity argument and the PCK (pedagogical content knowledge) literature. Chapter 2 borrows the *Level-3 specificity* framing for what the Homes of Hope volunteer provides — knowledge of the specific Hyderabad BPO market that no generic platform can encode. The framing is "this volunteer carries the pedagogical content knowledge the platform cannot."
- **Homes of Hope Plus One `book.md`, Unit 2 ("AI as Work Tool")** carries the Priya vignette as a composite, and specifically the *GPT Base vs. GPT Tutor* framing applied to Priya's case (the "two girls" cover-letter example). Chapter 2 should pull the Priya framing from HoH+1 verbatim where useful and cite the cross-book reference.
- **`_lib_humanitarians_ai_course_template.md`** carries the Humanitarians AI volunteer-network context (Bear's Northeastern CPS students, the volunteer recruitment pipeline, the Zoom-call cadence). Chapter 2 uses this to anchor the volunteer's existence as a real, deployable resource, not a thought experiment.
- **`ask-ai-research.md`** carries the Bastani GPT Base / GPT Tutor distinction. Chapter 2 references this once — to make the analogy that *Anki is the constrained wrapper, the volunteer is the pedagogical judgment* — without re-citing the full study (Chapter 3 does that).

### C.3 Cross-book connections

- **Homes of Hope Plus One** is the spinoff book that uses Priya as the running learner-vignette throughout. Medhavy's Chapter 2 is the *theoretical* version of the case HoH+1 makes practically. The chapter should reference HoH+1 directly: "The Priya case is developed in book-length form in *Homes of Hope Plus One*; the relevant Unit 2 chapter on AI as work tool is the deepest pull on the GPT Base / GPT Tutor framing in Priya's voice."
- **Trust the Teacher (Bear's prior book).** TtT's Ch 5 on the professional tool and Ch 6 on the AI dividend are the philosophical companions to Chapter 2. TtT argues that the teacher does the irreducibly human work; Medhavy Ch 2 argues that the volunteer does the irreducibly human work for Priya. Same shape, different scale.

---

## D. Current state of the field

The field has not produced a defensible answer to *"when is the full architecture overkill?"* The default behavior of EdTech vendors is to up-sell. The default behavior of academic researchers is to study the most complex available platform and report its effects. The default behavior of districts and NGOs purchasing platforms is to assume that more features mean better outcomes. The complexity threshold test is the book's attempt to fix this — to give buyers, builders, and grant-makers a diagnostic that says *no, you do not need the full thing for this problem*.

### D.1 The vocabulary-acquisition literature

The Anki / Quizlet / Memrise literature on vocabulary acquisition for second-language learners is mature and the effect sizes are large. Nakata 2011 (*ReCALL* 23(1), 17–38) reviews computer-assisted vocabulary learning and reports effect sizes for spaced-repetition flashcard apps in the *d* = 0.5–1.0 range against re-reading or paper-flashcard control. The dropoff between paper flashcards and digital flashcards is small; the dropoff between either and re-reading is substantial. For Priya's problem, the existing best-practice tool (Anki, Quizlet) plus the shared-deck community plus the volunteer is the field-tested answer. The field does not need a new platform for vocabulary acquisition. The field needs to stop building one.

### D.2 The certification-exam-prep literature

USMLE Step 1 first-pass memorization, NCLEX, PMP, AWS certifications — all of these are dominated by Anki-deck communities. The medical-student Anki community (AnKing, Boards & Beyond) has produced shared decks with hundreds of thousands of users and learning outcomes that the residency match has stabilized around. There is no peer-reviewed RCT comparing the AnKing deck to a counterfactual full-architecture platform — but the revealed preference of two decades of medical students is overwhelming. The complexity threshold test predicts this: certification recall is single-mode, frequency-orderable, end-of-period-assessed. The simple tool is the right tool.

### D.3 The middle — where the threshold test is ambiguous

A real frontier in the literature is *vocational training that sits between pure vocabulary acquisition and full clinical reasoning*. Examples: customer service training for a complex software product, where the agent has to learn product-specific terminology *and* learn to diagnose customer problems. Phlebotomy training, where the student has to learn vocabulary *and* learn procedural skills under live patient interaction. The threshold test on these cases is harder to apply — and the chapter should acknowledge this. The honest position: the test is a diagnostic, not a determination. A case that fails the test on one axis (single-mode) but is structurally borderline (the procedural skill component is real but small) is a judgment call. The chapter does not claim the test settles all cases. It claims the test settles enough cases to keep the architecture honest.

### D.4 The "second mover" pattern

The field's current trajectory: every commercial EdTech platform is racing to add AI tutoring, adaptive sequencing, and live analytics, because that is what the market signals as "modern." A countervailing pattern: the simplest tools (Anki, Khan Academy's pre-2023 content, the FSRS algorithm) continue to outperform the more elaborate platforms on the actual problems their users are trying to solve. The Sal Khan acknowledgment that Khanmigo "has failed to catch on with students" (`01-what-is-an-intelligent-textbook_notes.md` §A.3) is partly a usability finding and partly the complexity threshold test in action: the students who need a vocabulary deck or a problem set with retrieval practice are not reaching for a Socratic chatbot, because that is not what their problem requires. The platform is over-engineered for the median user's median problem.

---

## E. Teaching considerations

### E.1 The chapter's pedagogical move

The reader is being asked to acquire a diagnostic instrument — the complexity threshold test — and to apply it. This is an Evaluate-level Bloom's task. The pedagogical sequence:

1. **Open with the case** that calibrates the reader (Priya). Concrete. Specific. Named.
2. **Name the diagnostic** (the three questions). State each question. Specify what each question is asking.
3. **Apply the diagnostic to the case** (run Priya through the test, show all three answers are *no*).
4. **Show the contrast case** (medical student clinical reasoning, all three answers are *yes*).
5. **Hand the instrument to the reader** (the assessable exercises: corporate onboarding, surgical residency, professional certification exam — let them apply the test).
6. **Close with the load-bearing line** ("the tool is not the problem; the context is the problem") and the bridge to Chapter 3.

### E.2 What to avoid

- **Do not patronize Priya.** The chapter is about a girl who is using exactly the right tool, intelligently, with discipline, to solve exactly the right problem. The voice has to honor that. She is not a "low-resource case" the architecture happens not to apply to. She is the *test* of the architecture's honesty.
- **Do not make the volunteer disappear.** The chapter's deeper claim — that Anki is necessary but not sufficient, and the volunteer is the irreducibly human part — is what prevents the chapter from being read as "EdTech is fine, just use a flashcard app." It is not. EdTech is fine for vocabulary, **and the human relationship is doing work the platform cannot encode**. The two halves of the chapter must stay together.
- **Do not lean on cost.** The chapter risks becoming an "EdTech is too expensive" essay. It is not that. The chapter is an "EdTech is over-engineered for problems it is not designed for" essay. The cost argument is downstream. The fit argument is primary.
- **Do not over-claim the test's coverage.** The test is a useful diagnostic in three cases out of four. The fourth case — the ambiguous middle — the test does not settle. The chapter should say so. The reflexive commitment requires this.

### E.3 Voice and register

- The chapter has more warmth than Chapter 1. Chapter 1 is a diagnosis. Chapter 2 is a portrait. The Priya material has dignity in it; the voice should match.
- The complexity threshold test reads as a checklist. Resist the temptation to soften it into prose. The reader needs the test as a tool they can apply. Three named questions. State them as questions. Apply them in order.
- The closing line — *the tool is not the problem; the context is the problem* — is the chapter's load-bearing claim. It belongs at the end.

---

## F. Library files — what existing pantry covers

- **`quiz-me-research.md`** — retrieval practice (Roediger & Karpicke 2006; Adesope et al. 2017, g = 0.51), spacing effect (Cepeda et al. 2006, *Psychological Bulletin* 132(3), 354–380), FSRS / SM-2 scheduling algorithm distinction, medical-education adoption evidence, the learning-vs.-performance distinction (Soderstrom & Bjork 2015). **Use this note for all retrieval-practice and spacing-effect mechanism citations.** Chapter 2 cites three numbers from this note: the Roediger-Karpicke immediate-vs.-delayed retention reversal, the Adesope g = 0.51, and the Cepeda meta-analysis size (839 assessments, 317 experiments).
- **`quiz-me-habit-research.md`** — the habit-loop design literature (Fogg 2009/2019, Eyal 2014, Wood 2019), gamification mechanics, Zeigarnik closure effect, the shared-deck community (AnKing, Boards & Beyond, the South-Asian-diaspora language-learning Anki communities). **Use this note for why Priya keeps using Anki.** Chapter 2 references the daily-due-count mechanic and the shared-deck pattern without re-citing the literature.
- **`educational-media-economics-research.md`** — Sesame Street precedent ($5/child/year, *d* = 0.29 cognitive effect, Mares & Pan 2013 *Journal of Applied Developmental Psychology* 34(3), 140–151), cost-collapse asymmetry, minimum-viable-audience framing. **Use lightly** to defang the "cheap means low-quality" objection.
- **`domain-specific-instruction-research.md`** — Sadler 2013 Level-3 specificity, PCK literature. **Use for the framing that the volunteer carries domain knowledge the platform cannot encode.**
- **`ask-ai-research.md`** — Bastani GPT Base / GPT Tutor distinction. Chapter 2 references once for the *constrained wrapper vs. unconstrained model* analogy; the full citation lives in Chapter 3.
- **`glimmer-research.md`** — Jonassen 1997 ill-structured problem solving framing. Chapter 2 uses *ill-structured problem* once to anchor what clinical reasoning is and why it requires the full architecture.
- **`concept-sequencing-research.md`** — frequency-based curriculum design, BKT/DKT, prerequisite chaining. Chapter 2 references the *frequency-orderable curriculum* concept without going deep.
- **`_lib_humanitarians_ai_course_template.md`** — Humanitarians AI volunteer network context (Northeastern CPS, recruitment pipeline). Chapter 2 anchors the volunteer's existence as real.
- **Homes of Hope Plus One `book.md` and chapters/02-ai-as-work-tool.md, 01-professional-register.md** — the Priya vignette in full, the GPT Base / GPT Tutor framing applied to Priya, the BPO target market. **Use this as primary source for Priya's voice and circumstance.**

---

## G. Gaps and flags

### G.1 Verification flags

- **Priya is explicitly a composite.** The HoH+1 chapters labeled Priya as a composite vignette ("Both girls here are composite vignettes. Priya, our running learner-vignette, is one of them"). Chapter 2 must inherit this convention — Priya is not a single real student, and the chapter should disclose this on first appearance, ideally in a footnote or parenthetical, exactly as HoH+1 does. The narrative power of the case does not require pretending she is a single individual; it requires faithfulness to the constraints real Homes of Hope residents face.
- **The volunteer arrangement is real, scaled small.** Humanitarians AI volunteer matching is Bear's network and is operational; the specific cadence (forty-five minutes/week, six-week cycle) is the design the chapter proposes, not a published program description. The chapter should say this clearly — the volunteer program is real, the specific cadence is the proposed deployment shape — without overclaiming the scale.
- **The complexity threshold test is the book's own instrument.** It does not exist in the prior literature in this exact form. The chapter should name it as such. The three components draw on established distinctions (adaptive sequencing from the ITS literature; live instrumentation from the learning-analytics literature; multi-layered capability build from the ill-structured-problem literature), but the conjunctive three-question form is the book's contribution. Frame it as a working instrument, subject to revision.

### G.2 Conceptual flags

- **The chapter risks an unintended condescension toward the architecture.** Saying "for many problems, simpler is better" is true; saying it without conviction about the cases where the architecture *is* the right answer could read as ambivalence about the rest of the book. The chapter's tone has to be *confident calibration*: the architecture is necessary for the cases that need it, and Chapter 2's job is to specify which those are.
- **The chapter risks an unintended elitism toward Priya.** A reader from a US graduate-program background may read Priya as a "constrained-resource" case where the architecture's expense is the binding constraint. That reading misses the actual point. Even if Priya had a $500,000 platform budget, the threshold test still says Anki is enough for vocabulary acquisition. The constraint is not the budget; the constraint is the structure of the problem. The chapter must make this explicit.
- **The chapter should not pretend the test is a complete answer.** Some learning problems are in the ambiguous middle. The chapter should name a class of these (vocational training that mixes vocabulary and procedural skill, e.g., phlebotomy training) and say honestly that the test is a diagnostic, not a determination, in those cases.

### G.3 Hostile-reader objections to anticipate

- *"You are letting the architecture off the hook by saying it isn't for everyone."* The chapter's response: the architecture is for the problems that need it. The book's job is to make those problems clear. Not every learning problem needs the architecture. The book's reflexive commitment requires the chapter to say so.
- *"Anki is a 22-year-old desktop app with a clunky interface. You can't possibly be recommending it as state-of-the-art."* The chapter's response: AnkiDroid and AnkiMobile are actively maintained; FSRS is current research; the AnKing medical deck is used by a large fraction of US medical students. The product is not new and the product is not exciting; that is not the same as the product being wrong.
- *"The volunteer-call model doesn't scale."* The chapter's response: that is a separate question. Chapter 10 (Economics) addresses scale. Chapter 2 makes the qualitative case that *for the problems where the simpler tool is enough, scaling is not the binding constraint either* — Anki scales for free, and human volunteers scale at the rate networks like Humanitarians AI can recruit them. The four-layer architecture has a scale cost the simpler model does not.

### G.4 What would change my mind for this chapter

- A rigorous RCT showing that a fully-instrumented adaptive platform produces durable vocabulary retention *significantly* better than Anki + a human tutor for a population structurally similar to Priya's (low-resource, high-motivation, single-mode capability goal). The chapter bets this RCT does not exist and will not produce that result. If it does, the threshold test needs revision — possibly toward a fourth question (adaptive optimization across learners with different motivational profiles).
- Evidence that the AnKing deck and similar shared-deck communities do *not* in fact produce the medical-student board-pass-rate effects they are credited with — i.e., that the revealed-preference pattern is illusion or selection effect. The chapter relies on the Anki / medical-school pattern as the canonical example of "simple tools, right problem, durable outcomes." If that turns out to be confounded, the case for Priya weakens by analogy.
- A demonstration that the complexity threshold test produces false-negative classifications (i.e., that some problems the test classifies as "simple tool sufficient" actually require the full architecture). The chapter does not claim the test is complete. But systematic false negatives would be a problem the chapter should address.

### G.5 Still puzzling

- What is the threshold test's behavior at the boundary of well-structured and ill-structured problems? The Jonassen 1997 distinction is conceptually clear and operationally fuzzy. The chapter uses the distinction without resolving the fuzziness.
- Is the volunteer-relationship effect specific to the Humanitarians AI / Homes of Hope network, or does it generalize? The chapter bets generalization — that any network that pairs a learner with somebody who has done the target job will produce the same value. The bet is plausible but unproven.
- How does the threshold test interact with motivation? Priya is highly motivated (the door is closed, the job is the way out). The threshold test does not address motivation directly. A reader might worry that "Anki is enough" relies on Priya's motivation in a way the test does not capture. The chapter should acknowledge this — motivation is a hidden variable the test does not yet instrument.

---

*End of research notes. Approx. 5,400 words. For Chapter 2 author use.*
