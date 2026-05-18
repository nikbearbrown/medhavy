# Research Notes — Chapter 11: What the Platform Does Not Know Yet

*Research note for the Medhavy book project. Companion to all nine primary pantry research notes (ask-ai, case-study, quiz-me, quiz-me-habit, glimmer, glimmer-displacement, concept-sequencing, domain-specific, educational-media-economics) and to the Medhavy-internal `05_what_doesnt_it_know_yet.md` chapter draft. Compiled 2026-05-17 for the Chapter Writer pipeline. Author: research subagent for Nik Bear Brown.*

> **Reader's compass.** The TIKTOC flags this chapter as the one that requires the author's voice more than any other. The flag applies to the *chapter*. This research note is the evidence base behind it — what adjacent evidence exists for each of the eight open questions, what direct evidence does *not* yet exist, and what a published RCT designed to test the question would look like. The note is voice-neutral. The chapter author should arrive at the personal bet on top of this evidence layer, not in place of it. The Montaigne register the chapter opens in is its own reflexive instrument: a register willing to name what it does not yet know. That register is not a hedge. It is the strongest possible epistemic position for the third act of a book that has just delivered a complete architecture — the architecture is honest exactly because the gaps are visible. *Que sais-je?* is the right question. The answer is "less than the architecture suggests, but more than the field admits."

---

## §1. The opening case — the Montaigne register

### 1.1 The form, anchored `[foundational-theory]`

Michel de Montaigne (1533–1592) published the first two volumes of his *Essais* in 1580; the third followed in 1588, along with enlarged editions of the first two. *Essai* in French means "try" or "attempt" — the genre Montaigne invented is, by name, an *attempt at* truth rather than a *delivery of* truth ([Wikipedia: Essays (Montaigne)](https://en.wikipedia.org/wiki/Essays_(Montaigne)); [Britannica: Essays](https://www.britannica.com/topic/Essays-by-Montaigne); [Linda Hall Library biographical note](https://www.lindahall.org/about/news/scientist-of-the-day/michel-de-montaigne/)).

His motto, struck on a medallion he commissioned in 1576, is **"Que sais-je?"** — *what do I know?* The motto is the operating premise of the form. Montaigne's much-discussed skepticism is not a destination; it is a method. He writes about himself ("*I am myself the matter of my book*") to arrive at provisional truths about humanity in a period of ideological strife when all knowing seemed treacherous. The essay form's foundational move is to make the act of trying visible rather than to disguise the trying as already-arrived.

**For the chapter.** This is the load-bearing analogy. The book has just delivered (Chapters 1–10) the architecture as if it were settled. Chapter 11 reframes: it is settled *enough to deploy and measure*, not settled enough to defend without measurement. The deployment is the *essai*. The eight open questions are the trying. Montaigne is the right register because the architecture is a trial in his sense — a serious-but-revisable attempt to act on the current best reading of the evidence while remaining willing to be wrong.

This is also why the chapter cannot be written as a literature review. The literature review is the architecture chapters' move. Chapter 11's move is the author's first-person inventory of what he is personally betting on, with the architecture as the bet and the deployment as the test. A contributor cannot write this. It will read as false. The voice that earned the architecture must own the gaps.

### 1.2 What this register lets the chapter do

The Montaigne posture lets the chapter make claims it could not otherwise make in a textbook:

- *"I do not yet know."* In the register of the literature review, "I do not yet know" reads as a deficiency in the review. In the *essai* register, it reads as the author honestly distinguishing what the evidence supports from what he is committing to act on without sufficient evidence.
- *"My current reading is."* The Cornelius-White / Hattie / Sadler effect sizes are real. The integrated four-layer claim is a *current reading* of how those effect sizes compose. The composition has not been tested.
- *"What would change my mind."* Every chapter in the book carries a "what would change my mind" sentence. Chapter 11 is the one where that sentence stops being a chapter footer and becomes the chapter's structure.

The Montaigne register is, in this specific sense, the *most* defensible epistemic position the book can take in its final act — because the alternative is the IDK-IDK problem the book opened by diagnosing. A textbook that finishes by asserting the architecture works as designed, without evidence the integrated claim has been tested, *is* the engagement-measured-as-learning failure the book argued against. The reflexive move is non-negotiable.

---

## §2. The eight open questions — what is and is not yet known

Each subsection follows the same structure: (a) the question stated precisely; (b) what adjacent evidence exists; (c) what direct evidence does *not* yet exist; (d) what a published RCT designed to test it would look like.

### 2.1 Open Question 1 — Does context-anchoring alone convert GPT-Base failure to GPT-Tutor success?

**(a) The question.** Bastani et al. 2025 found that GPT-4 without guardrails harmed learning (−17 pp on the unassisted exam) while GPT-4 with teacher-designed *refuse-the-answer-give-hints* guardrails did not. The Medhavi Ask AI mode uses **RAG-grounded context-anchoring** (the model is constrained to retrieve from the current textbook section + prerequisites) as its primary guardrail rather than refuse-and-hint scaffolding. Does context-anchoring *alone* convert the GPT-Base failure outcome to the GPT-Tutor success outcome — or does context-anchoring need to be combined with refuse-and-hint scaffolding to do so?

**(b) Adjacent evidence.** Bastani 2025 (*PNAS* 122(26): e2422633122) is the closest direct evidence. The Khanmigo undergraduate physics study ([Journal of Teaching and Learning 2024](https://jtl.uwindsor.ca/index.php/jtl/article/view/10052)) found no significant learning-outcome difference between Khanmigo and Google-search groups, but did not vary the guardrail design within Khanmigo. ITS meta-analytic effect sizes for well-designed systems (ES +0.40 to +0.70; VanLehn 2011) suggest *some* combination of design choices produces learning gains — but the literature does not isolate *context-anchoring* as an independent variable.

**(c) What direct evidence does not exist.** No published RCT has tested context-anchored AI tutoring (RAG-grounded, no answer-refusal) against unguarded AI tutoring on a delayed unassisted exam. The Bastani design dimension that varied was *refuse-the-answer* behavior, not *retrieve-from-curriculum* grounding. These are different mechanisms.

**(d) What the RCT would look like.** Three arms: GPT-4 unguarded; GPT-4 with RAG-grounded context-anchoring to the current curriculum (no answer refusal); GPT-4 with both. Held constant: same content, same students, same practice tasks, same delayed-exam measurement. Primary outcome: delayed exam score without AI access. Pre-registered hypothesis: Bastani's Base-condition harm is partially mediated by context-anchoring; the magnitude of mediation is the finding. This is the design the Medhavy cancer-textbook deployment could approximate via within-learner randomization across concept nodes — not a true RCT, but a quasi-experimental design with within-subject controls.

### 2.2 Open Question 2 — Does pre-written faculty-reviewed CBL produce reasoning gains comparable to group human-facilitated CBL when solo/asynchronous?

**(a) The question.** Thistlethwaite et al. 2012 (BEME Guide No. 23, *Medical Teacher* 34(6): e421–e444) synthesized 104 studies of CBL in health-professional education and found consistent evidence of reasoning gains in the *group, human-facilitated* format. The Medhavi Case Study mode is *solo, asynchronous, AI-facilitated* on pre-written faculty-reviewed cases. Does the AI-facilitated solo format produce reasoning gains comparable to the group-facilitated format?

**(b) Adjacent evidence.** Thistlethwaite's BEME review documents satisfaction and self-reported reasoning gains; modest evidence on skill-application tasks. Dochy et al. 2003 (*Learning and Instruction* 13(5): 533–568) on PBL found −0.22 SD on knowledge breadth, +0.46 SD on skills application. Koedinger & Aleven 2007 on the assistance dilemma (*Educational Psychology Review* 19(3): 239–264) establishes that there is an optimal level of scaffolding that depends on prior knowledge and that the optimum is curvilinear. The Medhavi graduated-assistance ladder is designed to operationalize this. Whether the AI can actually deliver assistance at the optimal level *without a human in the loop* is the gap.

**(c) What direct evidence does not exist.** No published RCT compares solo AI-facilitated CBL against group human-facilitated CBL on a delayed transfer measure. Most CBL evidence is on the group format. The cognitive mechanism the literature credits — surfacing alternative interpretations through peer reasoning — is exactly what is missing in the solo format. The AI substituting for the peer group is an unverified mechanism replacement.

**(d) What the RCT would look like.** Three arms: solo AI-facilitated CBL on faculty-reviewed cases; group human-facilitated CBL on the same cases; control (read the cases, no facilitation). Outcome: skill-application performance on novel clinical scenarios at 4 weeks and 12 weeks. Within the AI arm, vary the assistance ladder — minimum, calibrated, maximum — to test the assistance-dilemma prediction. Pre-registered hypothesis: AI-facilitated solo CBL produces skill-application gains intermediate between control and group, with the gap narrowing for high-prior-knowledge students. Medical education is the natural deployment context.

### 2.3 Open Question 3 — Does FSRS-style scheduling generalize to conceptual material?

**(a) The question.** FSRS (Free Spaced Repetition Scheduler) is the open-source algorithm now default in Anki, trained on hundreds of millions of review logs from primarily *vocabulary and factual* material. It represents each item with three latent variables — Difficulty, Stability, Retrievability — and produces ~20–30% fewer reviews for the same target retention vs. SM-2. Does this scheduling generalize to *conceptual* material — definitions of *forces*, of *retrieval interference*, of *complement cascade regulation* — where retrieval is more than recognition of a paired associate?

**(b) Adjacent evidence.** Cepeda et al. 2006 (*Psychological Bulletin* 132(3): 354–380) meta-analysis of 317 experiments established the spacing principle holds across verbal recall tasks; Cepeda et al. 2008 (*Psychological Science* 19(11): 1095–1102) showed optimal inter-study interval scales with retention horizon. Kerfoot et al. 2010 (*Annals of Surgery* 252(2): 350–359) showed spaced retrieval in medical education generates *transfer* to novel diagnostic items, not just retention of practiced items. Roediger & Karpicke 2006 (*Psychological Science* 17(3): 249–255) shows the testing effect generalizes across material types.

**(c) What direct evidence does not exist.** FSRS itself has not been validated on conceptual material at scale. The hundreds of millions of review logs that trained FSRS are dominated by language-learning and factual-recall use cases (the dominant Anki populations: med students and language learners — but the language-learning cards dominate the corpus). Whether the Difficulty / Stability / Retrievability latent representation captures the dynamics of conceptual retrieval (where partial retrieval is meaningful and a Hard rating may indicate partial-mechanism understanding rather than partial-trace strength) is unknown.

**(d) What the RCT would look like.** Within-learner: same Quiz Me item set across both a vocabulary domain and a conceptual domain, with FSRS scheduling vs. equally-spaced fixed scheduling, on delayed retention at 30 / 60 / 90 days. The hypothesis to test: FSRS's review-reduction efficiency claim (~20–30% fewer reviews at the same retention) holds in vocabulary, may attenuate or invert for conceptual material. This is testable within Medhavy v1.5 by varying the scheduling algorithm across cohorts and observing the delayed retention at the GLP Y6 (retrieval strength decay) signal.

### 2.4 Open Question 4 — Is the Quiz Me habit loop driven by the due-count or the algorithm?

**(a) The question.** Anki users adopt the system as a daily habit; ~30%+ of US med students use it consistently. The system has two distinct components: the FSRS scheduling algorithm (cognitive optimization), and the visible due-count + completion event (habit loop). Which is doing the load-bearing work in driving daily voluntary use?

**(b) Adjacent evidence.** Wood 2019 (*Good Habits, Bad Habits*) establishes the cue-action-reward structure of habit formation; Lally et al. 2010 (*European Journal of Social Psychology* 40(6): 998–1009) on habit-formation time courses. The Zeigarnik effect (Zeigarnik 1927) — open tasks create cognitive pressure to close — is the mechanism behind the due-count counter; closing the count is the reward that reinforces the habit. Cohort studies in medical education show mature-card counts explaining over a third of the variance in course exam scores (Deng, Gluckstein & Larsen 2015 in radiology; Schimmelpfennig et al. 2024 USMLE Step 1 cohort).

**(c) What direct evidence does not exist.** No published study has dismantled Anki's habit loop to isolate the algorithm contribution from the due-count contribution. The argument from analogy (the Eyal/Wood/Fogg habit literature) is suggestive but not specific to the testing-effect tool. The Medhavi 1.5 design hypothesizes that the **due-count is the load-bearing UI** and the algorithm is a small contributor to whether students adopt the tool at all — but this is a design bet, not a tested claim.

**(d) What the RCT would look like.** Two-by-two within-learner: FSRS-scheduling vs. simple-fixed-interval-scheduling × visible-due-count vs. no-due-count UI. Primary outcome: daily session frequency over 8 weeks. Secondary outcome: delayed retention. Pre-registered hypothesis: the visible-due-count effect on daily session frequency is larger than the FSRS algorithm effect on retention. If true, the design implication is large: the UI element is the load-bearing piece, and platforms that ship sophisticated scheduling without the habit-loop UI are over-investing in algorithm and under-investing in interface.

### 2.5 Open Question 5 — Does backwards-faded scaffolding prevent the anxiety collapse in novice Glimmer users?

**(a) The question.** Pekrun's 2006 control-value theory of achievement emotions (*Educational Psychology Review* 18(4): 315–341) predicts that students with high task value and low perceived control land in the *anxiety* quadrant, not the *engagement* quadrant. USMLE-trained medical students have spent 2+ years optimizing for closed-problem recognition; their first Glimmer (an ill-structured creative assignment) frequently lands them in anxiety. The Glimmer design mitigates with backwards-faded scaffolding (Renkl & Atkinson 2003, *Educational Psychologist* 38(1): 15–22): week 1 supplies framing, week 2 supplies framing partially, week 3 is fully open. Does this fading actually prevent the anxiety collapse, or does the collapse happen at the fully-open transition regardless?

**(b) Adjacent evidence.** Belland, Walker, Kim & Lefler 2017 (*Review of Educational Research* 87(2): 309–344) meta-analysis of computer-based scaffolding in STEM (144 studies, *g* = 0.46) establishes that *scaffolded* ill-structured work produces cognitive gains; the fading is the design choice the meta-analysis identifies as critical. Puntambekar & Hübscher 2005 (*Educational Psychologist* 40(1): 1–12) and van de Pol, Volman & Beishuizen 2010 (*Educational Psychology Review* 22(3): 271–296) on contextualized, fading scaffolding. Jonassen 1997 on ill-structured problems.

**(c) What direct evidence does not exist.** No published study tests backwards-faded scaffolding specifically with USMLE-trained medical students on a Glimmer-style assignment over a multi-week trajectory with anxiety as a measured outcome. The Medhavi v1.5 deployment is designed to produce this data — but as of 2026 has not produced it at sample size sufficient to detect the predicted effect.

**(d) What the RCT would look like.** Two arms (within-learner across cohort or assignment): backwards-faded scaffolding vs. constant-low-scaffolding. Outcomes: (1) abandonment rate in weeks 2–3; (2) self-reported anxiety on the Achievement Emotions Questionnaire; (3) Glimmer rubric scores at weeks 5–11. Pre-registered hypothesis: the faded condition produces lower abandonment, lower anxiety, and equivalent or higher rubric scores at week 11. The fading-vs-no-fading comparison is the cleanest mechanism test.

### 2.6 Open Question 6 — Does priority-weighted scheduling outperform recall-only scheduling?

**(a) The question.** Pure FSRS schedules on predicted retrievability. The Medhavi Quiz Me schedule adds priority weights: `priority = α × prerequisite_depth + β × importance_tier + γ × (1 − retrievability) + δ × frequency_tier`. The importance and frequency tiers are set by the professor at Tic TOC time — they inject domain knowledge the recall data alone cannot capture. The aviation pedagogy principle: any concept tagged `importance_tier = 'high'` is reviewed at least every 14 days regardless of FSRS prediction. Does priority-weighted scheduling produce better learning outcomes than pure recall-driven scheduling?

**(b) Adjacent evidence.** The pedagogical content knowledge literature (Shulman 1986; Sadler et al. 2013) establishes that domain-expert knowledge of *what matters* is a distinct and powerful predictor of student outcomes. The aviation pedagogy literature (FAA practical test standards; Salas et al. 2006 on crew resource management training) establishes that high-stakes rare events get mandatory scheduling rather than recall-dependent scheduling, with measurable safety outcomes. The Bayesian Knowledge Tracing (BKT) and Deep Knowledge Tracing (DKT) literatures use prior knowledge structure to weight learning estimates.

**(c) What direct evidence does not exist.** No published study directly compares priority-weighted scheduling against recall-only scheduling in a spaced-retrieval educational tool. The closest is the comparison of Anki SM-2 vs. FSRS, which holds priority weighting constant (both are recall-driven) and only varies the recall prediction. The mechanism the chapter argues — that recall-based scheduling under-trains foundational concepts because they get easy quickly and the algorithm downschedules them — is theoretically sound and empirically unverified at scale.

**(d) What the RCT would look like.** Two arms: FSRS-only scheduling vs. FSRS + priority weights (importance and prerequisite-depth tiers set by domain experts). Same content, same students, same retention horizon. Outcomes: (1) retention of high-importance items at 90 days; (2) overall retention at 90 days; (3) review-time efficiency. Pre-registered hypothesis: priority weighting produces higher retention on high-importance items with no degradation on overall retention. The risk: priority weighting may degrade overall efficiency (more reviews on items the algorithm would have scheduled less aggressively). The tradeoff is what the experiment is for.

### 2.7 Open Question 7 — Does Level-3 domain specificity outperform Level-1 generic instruction enough to justify the production cost?

**(a) The question.** The domain-specific instruction literature distinguishes Level 1 (generic instruction), Level 2 (generic + domain capstone), Level 3 (domain-specific throughout, generic backbone). Level 3 plausibly captures the bulk of transfer-appropriate-processing benefits and motivation benefits but costs ~1.5–2× production over Level 1. Does the learning gain justify the production cost?

**(b) Adjacent evidence.** Walkington 2013 (*Journal of Educational Psychology* 105(4): 932–945) on interest-personalization in Algebra I found transfer from personalized practice to non-personalized assessment — the strongest single piece of evidence in the interest-personalization literature. Walkington & Bernacki 2019 (*IJAIED* 29(1): 58–88) on deep vs. surface personalization found *d* = 0.39 for deep personalization for high-engagement students; *d* = −0.43 favoring surface for low-engagement students — *depth-matching matters more than depth itself*. Hulleman & Harackiewicz 2009 (*Science* 326(5958): 1410–1412) on utility-value writing prompts found improved course grades for low-performing students at zero marginal cost. Transfer-appropriate processing theory (Morris, Bransford & Franks 1977; Roediger, Gallo & Geraci 2002) predicts encoding-test match drives retrieval.

**(c) What direct evidence does not exist.** No published RCT compares Level-1 vs. Level-3 instruction on the *same skill* in the *same population* with *delayed transfer* outcomes and *production-cost accounting*. The closest is Walkington 2013, but that compared *no* personalization vs. *one variant* of personalization in a single ITS — not three levels of domain specificity at scale across multiple subjects. The honest read: the direction of the effect is supported; the magnitude that would justify the production cost is unknown.

**(d) What the RCT would look like.** Three arms × two retention horizons: Level-1 generic, Level-2 generic+capstone, Level-3 domain-specific-throughout. Outcomes: (1) near-transfer (within-domain application) at 30 days; (2) far-transfer (cross-domain application) at 90 days; (3) cost per 0.1 SD gain. Pre-registered hypothesis: Level-3 produces larger near-transfer gains and equivalent-or-worse far-transfer gains than Level-1; the cost-per-0.1-SD breakdown determines whether Level-3 production cost is justified at any given audience scale.

### 2.8 Open Question 8 — Does AI-generated educational content produce durable learning outcomes comparable to professionally produced content?

**(a) The question.** The cost-collapse argument (Chapter 10) is established at the unit-production level. Whether AI-generated content *of the same design quality* as Sesame-Street-class professional production produces *equivalent durable learning outcomes* is the open bet on which the cost-collapse argument depends.

**(b) Adjacent evidence.** Mayer's CTML meta-analyses on individual principles (Mayer 2014 handbook; Schroeder & Cenkci 2018; Schneider et al. 2018; Adesope & Nesbit 2012) establish what design features predict learning across hundreds of experiments. Yan et al. 2024 (*BJET* systematic scoping review) found AI-generated lesson plans rated comparable to human on structure but systematically lower on differentiation and contextual awareness. Bryant et al. 2024 (arXiv:2504.05449) found educators preferred AI-generated plans on surface quality and human plans on fit-to-student-need. Singhal et al. 2023 (Med-PaLM, *Nature* 620: 172–180) found high accuracy with clinically meaningful hallucination rates.

**(c) What direct evidence does not exist.** No published RCT compares AI-generated educational content matched on Mayer's twelve principles against professionally produced equivalents with delayed retention and transfer outcomes as primary endpoints. The peer-reviewed evidence base for AI-generated educational content as a *learning* (not engagement) intervention is genuinely sparse and is dominated by vendor or preprint work from 2024–2025. Independent benchmarks of cost-to-produce-equivalent-quality do not yet exist in the peer-reviewed literature.

**(d) What the RCT would look like.** Two arms: AI-generated content matched on Mayer's twelve principles (with explicit prompting for temporal contiguity, spatial contiguity, signaling, segmenting, coherence) vs. professionally produced equivalent on the same concepts. Outcomes: (1) immediate post-test; (2) delayed retention at 30/90 days; (3) transfer to novel application items; (4) production-cost-per-0.1-SD breakdown. Pre-registered hypothesis: AI-generated content matches professional production on immediate post-test, falls behind on delayed retention and transfer, with the gap larger for high-complexity content. This is the **single most important RCT the field could run** to settle the cost-collapse claim's quality-equivalent layer.

---

## §3. Adjacent vs. direct vs. assertion — the epistemic ladder

The chapter's central epistemic move: distinguish three categories.

- **Adjacent evidence.** Evidence on mechanisms or partial designs that are components of the integrated claim but do not test the integrated claim itself. ITS effect sizes are adjacent evidence for the bandit-engine claim. Spacing-effect meta-analyses are adjacent for the Quiz Me FSRS claim. CTML principles are adjacent for the Video and Animation claim.
- **Direct evidence.** Evidence on the integrated claim under deployment conditions. Bastani 2025 is direct evidence for the AI-tutor-with-guardrails claim under the specific Bastani guardrail design. No direct evidence exists for the integrated four-layer architecture claim — the platform has not been tested as a unit against a control.
- **Assertion.** Claims made without either adjacent or direct evidence. The chapter should be ruthless about calling these out when they appear in the EdTech literature.

The chapter's call: most published EdTech claims live at *adjacent*; most published EdTech *marketing* lives at *assertion*. The Medhavy book's contribution is to be honest about which category each chapter's claim sits in. The architecture chapters cite *adjacent* evidence for design decisions; the deployment chapters (when they arrive) will report *direct* evidence. The current state of the Medhavy claim is *adjacent everywhere except where Bastani directly tests it*.

The recurrent diagnostic the chapter trains in the reader: when a vendor white paper claims "our platform improves learning outcomes by 40%," ask three questions. (1) Adjacent or direct? (2) If direct, what was the comparison condition? (3) If direct with a comparison, what was measured — engagement, immediate performance, or delayed transfer? Most vendor claims fail at question 1. Most surviving claims fail at question 3.

---

## §4. The student consent architecture as a design decision

### 4.1 The regulatory floor — FERPA and COPPA in 2026 `[verify]`

The student consent architecture is a design decision with learning consequences, not just a compliance overhead. The 2026 regulatory floor:

- **FERPA (Family Educational Rights and Privacy Act, 1974).** In March 2025, the U.S. Department of Education required all state agencies to certify FERPA compliance by April 30, 2025 — an unprecedented enforcement mandate ([Statvix 2026 analysis](https://statvix.com/coppa-and-ferpa-in-2026-protecting-student-data-in-the-age-of-ai/); [studentprivacy.ed.gov](https://studentprivacy.ed.gov/)). Mid-2025 commentary noted that FERPA lacks clear cybersecurity requirements despite schools relying on hundreds of EdTech tools; experts urge modernization with vendor security obligations. AI use under FERPA requires institutions to interpret how AI accesses, uses, and stores student data — the regulation has not been amended for AI specifically but enforcement has expanded ([ArentFox Schiff AI Law Blog](https://www.afslaw.com/perspectives/ai-law-blog/the-development-ai-and-protecting-student-data-privacy)).
- **COPPA (Children's Online Privacy Protection Act, 1998; 2025 amendments).** Major revision in 2025 with new rules **effective June 23, 2025** and full compliance required by **April 22, 2026**. The 2025 amendments shifted the default from opt-out to opt-in consent. Updated consent verification methods and requirements for explicit parental consent before sharing data with third parties fundamentally change how schools handle data from students under 13 ([SchoolAI compliance guide](https://schoolai.com/blog/ensuring-ferpa-coppa-compliance-school-ai-infrastructure); [AI Governance Group blog](https://aigovernancegroup.com/blog/bridging-edtech-education-compliance-gap)).
- **State law.** As of 2025, 121+ state laws protect student privacy beyond FERPA.

**Verification.** Confirm the COPPA April 22, 2026 deadline and the specific 2025 FERPA enforcement actions at draft time — both regulations have been moving through 2025–2026. The chapter should state effective dates with `[verify YYYY-MM]` flags.

### 4.2 The student-controlled epsilon — the Medhavy architecture

The Medhavi consent design (from `05_what_doesnt_it_know_yet.md`):

- **Null arm.** Turn off the AI entirely. Download the Kindle. Take the content and leave. This is how education worked for five hundred years. The null arm has dignity.
- **Low epsilon.** Mostly receive what the system currently believes is best, with occasional exploration. Low risk, low disruption — the student who wants to benefit from what the system knows without being a research participant.
- **Full RCT.** Higher exploration rate and active contribution to the research program. The student willing to try things the system hasn't tried.
- **Change settings at any time.** No student is trapped. The data from sessions before they left is still informative. The act of leaving is itself data.

The student-controlled epsilon is genuinely novel as an experimental design. Most educational RCTs assign treatment; students who opt into full RCT here are motivated participants whose engagement signal is cleaner than a randomly assigned cohort. Students who hold at low epsilon are revealing risk tolerance. The traditional RCT treats attrition as a validity threat; this architecture treats it as a measurement.

**Learning-consequences argument.** The chapter must make the case that consent architecture has learning consequences, not just ethical/regulatory consequences. The argument: a student who *chose* the AI-on condition has a different learning trajectory than a student who was *assigned* it, even with identical exposure. Motivation, self-determination theory (Ryan & Deci 2000), and the self-fulfilling-prophecy literature predict this. The consent architecture is not orthogonal to learning; it is upstream of it.

### 4.3 What the design commits to and what it does not

The Medhavi architecture commits to:

- **Outcome data** — Quiz Me ratings, mode selections, dwell times, mastery threshold crossings, GLP component values per concept.
- **Process data** — switching behavior between modes, abandonment events, recovery events after Quick Catch-Up.
- **Pseudonymized aggregate data** for cross-cohort comparison.

The architecture commits *not* to collect:

- **Identified outcome data without explicit consent** — even within-platform, identified outcomes route through the consent gate.
- **Behavioral data outside the learning system** — keystroke dynamics outside Quiz Me sessions, mouse-tracking outside Glimmer composition, ambient phone sensors. The platform does not act as a generic surveillance tool just because it could.
- **Inference about non-learning attributes** — gender inference, socioeconomic inference, mental-health inference from textual content. Yan et al. 2024 documents that these are real risks of LLM-in-education deployments; the architecture commits not to act on them.

The "must be disclosed" layer: what data is collected, what is not, what the GLP components measure, and how switching is treated. The disclosure is itself part of the consent. A consent architecture without disclosed measurement commitments is consent in name only.

---

## §5. Switching behavior as signal

From `05_what_doesnt_it_know_yet.md`: the most interesting data the consent architecture generates is not the steady-state choices. It is the switching behavior.

- A student who **starts at low epsilon and moves to full RCT** mid-semester is showing the system earned their trust or curiosity about what else the engine might try.
- A student who **starts engaged and downloads the Kindle at week eight** is showing that something stopped working, *or* that they got what they needed and are done. Both possibilities are signal.
- A student who **turns off the AI entirely the week before the exam** is showing their mental model of what the system is for.
- A student who **switches from Quiz Me to Glimmer mid-session** is showing the mode-selection signal the within-learner bandit should be updating on.

None of this is available in a traditional RCT, which treats switching as a compliance problem. The bandit does not need stable treatment assignment — it adapts continuously. The switching behavior is part of the evidence stream.

**For the chapter.** The adaptive engine's job is not to *prevent* switching. It is to *read* switching. A learner who switches to a mode the engine did not predict is providing the highest-information signal possible — the engine's prior was wrong. The system should update aggressively on switch events. The architecture decision the chapter exposes: switching is signal, not failure.

---

## §6. The honest preliminary report — the worked example

The TIKTOC's worked example: the Medhavy cancer textbook deployment at six weeks. What the data show. What they do not show. Which of the eight open questions has preliminary evidence. Which is still genuinely open.

The chapter should treat this as a *deployment report that a researcher could use as a preprint* — not polished findings, but honest preliminary evidence with appropriate uncertainty. The structure of the worked example:

- **What the platform has collected.** Sample size, distribution across mode choices, distribution across consent settings, completion rates, switching rates.
- **What signal the GLP components are producing.** Component-by-component, what the variance looks like and whether the variance is informative.
- **Which of the eight open questions has preliminary evidence.** Most likely: open questions 4 (due-count vs. algorithm), 6 (priority weighting), and possibly 3 (FSRS in conceptual material) have early signal from six weeks of deployment. Open questions 1 (context-anchoring), 2 (solo CBL), 5 (Glimmer scaffolding), 7 (Level-3 specificity), 8 (AI vs. professional content) require longer deployment.
- **Calibrated uncertainty.** The Bogatz/Ball methodological move: state what would have to be true for the preliminary signal to mean what it appears to mean, and state what would have to be true for it to be artifactual.
- **What the next six weeks will test.** Pre-registered, not post-hoc. The Schein-of-an-RCT move: even if the platform is not running a formal RCT, the next-period predictions are committed in writing.

The chapter's epistemic move is to make the *gap between adjacent evidence and direct evidence* visible at the granularity of the integrated platform claim. This is the position consistent with the book — every other architecture chapter has cited adjacent evidence for design decisions; Chapter 11 is the chapter that names which decisions are *bets* awaiting direct evidence.

---

## §7. Consolidated citations and pantry cross-reference

### 7.1 Existing pantry sources (cite by filename)

- All nine primary pantry research notes — each of the eight open questions draws on the corresponding research note for adjacent evidence. The chapter is a *synthesis* of which questions remain open across the architecture.
- `05_what_doesnt_it_know_yet.md` (Medhavi-internal early draft) — heavy use for §4 (consent architecture), §5 (switching behavior), and §6 (deployment report structure). The 5-unknown list there maps onto the 8-question list here; the chapter should reconcile.
- `medhavy-1.5-feature-roadmap-complete.md` — current platform features that produce the data underlying the worked example.
- GLP preprint — for the seven-component framework underlying the deployment report.

### 7.2 New citations introduced in this note (Chicago author-date, link-bearing)

Belland, Brian R., Andrew E. Walker, Nam Ju Kim, and Mason Lefler. 2017. "Synthesizing Results From Empirical Research on Computer-Based Scaffolding in STEM Education: A Meta-Analysis." *Review of Educational Research* 87(2): 309–344.

Bryant, et al. 2024. "Connecting Feedback to Choice: Understanding Educator Preferences in GenAI vs. Human-Created Lesson Plans in K-12 Education." Preprint, arXiv:2504.05449. [https://arxiv.org/html/2504.05449v1](https://arxiv.org/html/2504.05449v1)

Lally, Phillippa, Cornelia H. M. van Jaarsveld, Henry W. W. Potts, and Jane Wardle. 2010. "How are Habits Formed: Modelling Habit Formation in the Real World." *European Journal of Social Psychology* 40(6): 998–1009.

Montaigne, Michel de. 1580 [1991]. *The Complete Essays.* Trans. M. A. Screech. London: Penguin Classics. Wikipedia overview: [https://en.wikipedia.org/wiki/Essays_(Montaigne)](https://en.wikipedia.org/wiki/Essays_(Montaigne)). Britannica reference: [https://www.britannica.com/topic/Essays-by-Montaigne](https://www.britannica.com/topic/Essays-by-Montaigne).

Morris, C. D., J. D. Bransford, and J. J. Franks. 1977. "Levels of Processing Versus Transfer Appropriate Processing." *Journal of Verbal Learning and Verbal Behavior* 16(5): 519–533.

Pekrun, Reinhard. 2006. "The Control-Value Theory of Achievement Emotions." *Educational Psychology Review* 18(4): 315–341.

Renkl, Alexander, and Robert K. Atkinson. 2003. "Structuring the Transition From Example Study to Problem Solving in Cognitive Skill Acquisition." *Educational Psychologist* 38(1): 15–22.

Ryan, Richard M., and Edward L. Deci. 2000. "Self-Determination Theory and the Facilitation of Intrinsic Motivation, Social Development, and Well-Being." *American Psychologist* 55(1): 68–78.

Salas, Eduardo, Dana E. Sims, and C. Shawn Burke. 2006. "Crew Resource Management: A 25-Year Perspective." *Annual Review of Psychology* 57: 165–193.

U.S. Department of Education. 2025. "FERPA Compliance Certification." Federal regulatory action, March–April 2025. Guidance at [https://studentprivacy.ed.gov/](https://studentprivacy.ed.gov/). Verify enforcement specifics at draft time.

Federal Trade Commission. 2025. "COPPA Final Rule Amendments." Effective June 23, 2025; full compliance April 22, 2026. Verify text and effective dates at draft time. Practitioner summary: [https://statvix.com/coppa-and-ferpa-in-2026-protecting-student-data-in-the-age-of-ai/](https://statvix.com/coppa-and-ferpa-in-2026-protecting-student-data-in-the-age-of-ai/).

VanLehn, Kurt. 2011. "The Relative Effectiveness of Human Tutoring, Intelligent Tutoring Systems, and Other Tutoring Systems." *Educational Psychologist* 46(4): 197–221.

Wood, Wendy. 2019. *Good Habits, Bad Habits: The Science of Making Positive Changes That Stick.* Farrar, Straus and Giroux.

Yan, Lixiang, et al. 2024. "Practical and ethical challenges of large language models in education: A systematic scoping review." *British Journal of Educational Technology* 55(1): 90–112.

Zeigarnik, Bluma. 1927. "Das Behalten erledigter und unerledigter Handlungen." *Psychologische Forschung* 9: 1–85.

---

*End of research note for Chapter 11. ~5,400 words.*
