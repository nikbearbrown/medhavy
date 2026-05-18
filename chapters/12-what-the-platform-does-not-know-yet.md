# Chapter 12 — What the Platform Does Not Know Yet

---

## Learning Objectives

By the end of this chapter, you will be able to:

1. **(Evaluate)** Assess an intelligent textbook deployment's epistemic honesty — distinguishing what the literature directly tests from what is *adjacent* evidence, and what is a *bet* the deployment will test.
2. **(Apply)** Specify the instrumentation required to make a given design bet testable from deployment data within one semester.
3. **(Analyze)** Explain the student consent architecture as a design decision with learning consequences, not just a regulatory compliance overhead.
4. **(Understand)** Describe switching behavior as signal and explain what the adaptive engine should do with it.

**Prerequisites:** Chapters 1–10. You should already know the four-layer architecture, the GLP measurement framework, the within-learner bandit, and the cost-collapse asymmetry.

**Skippable?** Yes, if you trust the architecture and are not interested in the epistemic inventory. You lose the honest uncertainty framing but not a capability the rest of the book delivers.

---

## Where this fits the conductor frame

This chapter serves all three audiences at once, but the load is on the learner — the first of the three questions, in order. The learner is the person whose participation in the experiment carries the most weight; the instructor and the organization can audit the bets, but the learner is the one whose semester is being spent inside an experiment with eight open questions. The chapter is built on Chapter 1's third transparency — uncertainty transparency — operationalized as a public inventory.

What this chapter specifies for the conductor are the open questions she does not yet know the answer to. Eight bets, named, with their adjacent evidence, their missing direct evidence, and the deployment design that will test each one. The conductor is not pretending to certainty she does not have. The conductor is also not refusing to act until the evidence is in; that would forfeit the chance to generate the evidence at all. The list is what conducting under uncertainty looks like when transparency is the operating discipline.

The chapter runs the experiment by being the experiment in plain view. The eight questions are the agenda the deployment is conducting against; the learner who participates is participating in the agenda; the data the platform generates is, with consent and anonymization, available for inspection. This is what experiment-as-product means when it lands. A platform that hides its uncertainty is making one argument; this platform is making the opposite one. The chapter is where that commitment is most visible.

---

## A Note on This Chapter, Before It Begins

I have to be in this chapter in a way I have not been in the others.

The preceding ten chapters made a case. They cited evidence, walked through architecture, ran calculations, and arrived at recommendations. The voice was the voice of someone delivering an argument. This chapter is a different kind of writing. It is the inventory I would have to make if someone asked me — out loud, in a room — what Medhavy currently knows and what it does not. Not the version I would put on a slide. The version I would say to a friend who asked the question honestly.

If I let this chapter slide into the register of the architecture chapters, it will read as false. A literature review of the questions the platform leaves open is not the same as a personal acknowledgment of the bets the platform's author is making. *Que sais-je?* — the motto Montaigne struck on a medallion in 1576 — is the question this chapter is built around. It is also the question that makes the chapter possible. A book that has just delivered a complete architecture has to be willing to name the gaps. Anything less is the IDK-IDK problem at the book level.

So I am here, in the first person, naming bets I am personally making. Where the bets are good — where adjacent evidence supports the design choice — I will say so. Where the bets are speculative — where the design commits ahead of the evidence — I will say that too. The architecture is honest exactly because the gaps are visible.

---

## §1. The Form This Chapter Takes

Michel de Montaigne published the first two volumes of his *Essais* in 1580; the third followed in 1588 ([Wikipedia overview](https://en.wikipedia.org/wiki/Essays_(Montaigne)); [Britannica reference](https://www.britannica.com/topic/Essays-by-Montaigne); [Linda Hall Library biographical note](https://www.lindahall.org/about/news/scientist-of-the-day/michel-de-montaigne/)). *Essai* in French means *try* or *attempt*. The genre Montaigne invented is, by name, an attempt at truth rather than a delivery of truth.

His motto, struck on a medallion he commissioned in 1576, is **"Que sais-je?"** — *what do I know?* The motto is the operating premise of the form. Montaigne writes about himself ("*I am myself the matter of my book*") in order to arrive at provisional truths about humanity in a period of ideological strife when all knowing seemed treacherous. The form's foundational move is to make the act of trying visible rather than to disguise the trying as already-arrived.

This is the load-bearing analogy for the chapter. The architecture I have delivered in Chapters 1–10 is *settled enough to deploy and measure*. It is not settled enough to defend without measurement. **The deployment is the *essai*. The eight open questions are the trying.**

A textbook that finishes by asserting the architecture works as designed, without evidence that the integrated claim has been tested, *is* the engagement-measured-as-learning failure the book argued against in Chapter 1. The reflexive move is non-negotiable. I cannot hold the field to an epistemic standard and then fail to meet it myself.

What follows is what I currently know, what I do not, and what the deployment is built to find out.

---

## §2. The Eight Open Questions

Each question gets the same treatment: what the question is, what adjacent evidence exists, what direct evidence does *not* yet exist, and what the deployment can do about it.

### 2.1 Open Question 1 — Does context-anchoring alone convert GPT-Base failure to GPT-Tutor success?

**The bet.** Medhavi's Ask AI mode uses **RAG-grounded context-anchoring** as its primary guardrail. The model retrieves from the current textbook section plus prerequisites and answers within that scope. Bastani et al. 2025 ([*PNAS* 122(26): e2422633122](https://www.pnas.org/doi/10.1073/pnas.2422633122)) found that GPT-4 *without* guardrails harmed durable learning by 17 percentage points on the unassisted exam, while GPT-4 with teacher-designed *refuse-the-answer-give-hints* guardrails did not.

Bastani's guardrail varied *answer-refusal behavior*. Medhavi's guardrail varies *retrieval scope*. These are different mechanisms. The bet is that context-anchoring alone — without explicit answer refusal — is sufficient to convert Base-condition harm to Tutor-condition neutrality or gain.

**Adjacent evidence.** Bastani 2025 is the closest. The Khanmigo undergraduate physics study ([*Journal of Teaching and Learning* 2024](https://jtl.uwindsor.ca/index.php/jtl/article/view/10052)) found no significant learning-outcome difference between Khanmigo and Google-search groups, but did not vary the guardrail design within Khanmigo. VanLehn 2011 (*Educational Psychologist* 46(4): 197–221) on ITS effect sizes — +0.40 to +0.70 for well-designed systems — suggests *some* combination of design choices produces learning gains. The literature does not isolate context-anchoring as an independent variable.

**What direct evidence does not exist.** No published RCT has tested context-anchored AI tutoring (RAG-grounded, no answer-refusal) against unguarded AI tutoring on a delayed unassisted exam. The Bastani design dimension was *refuse-the-answer*. Medhavy's is *retrieve-from-curriculum*. The comparison has not been run.

**The deployment.** The cancer and physics textbook deployments can approximate this via within-learner randomization across concept nodes — students receive context-anchored Ask AI on some concepts and minimal-guardrail Ask AI on others, with delayed retention measured against both. This is not a true RCT — students are not randomized between participants — but a quasi-experimental design with within-subject controls. **The bet is that the within-learner design produces signal sufficient to indicate whether the mediation is partial, complete, or absent within the first two cohorts.** If the signal is null, I have to revisit whether context-anchoring alone is the right guardrail or whether refuse-and-hint scaffolding has to be added.

### 2.2 Open Question 2 — Does pre-written faculty-reviewed CBL produce reasoning gains comparable to group human-facilitated CBL when solo/asynchronous?

**The bet.** Thistlethwaite et al. 2012 (BEME Guide No. 23, *Medical Teacher* 34(6): e421–e444) synthesized 104 studies of CBL in health-professional education and found consistent evidence of reasoning gains in the *group, human-facilitated* format. Medhavi's Case Study mode is *solo, asynchronous, AI-facilitated* on pre-written faculty-reviewed cases. The bet is that the AI-facilitated solo format produces reasoning gains comparable enough to the group-facilitated format that the convenience (solo, asynchronous, on a phone at 11pm before a clinical rotation) outweighs the social-reasoning loss.

**Adjacent evidence.** Thistlethwaite's BEME review documents satisfaction and self-reported reasoning gains; modest evidence on skill-application tasks. Dochy et al. 2003 (*Learning and Instruction* 13(5): 533–568) on PBL found −0.22 SD on knowledge breadth, +0.46 SD on skills application. Koedinger & Aleven 2007 on the assistance dilemma (*Educational Psychology Review* 19(3): 239–264) establishes that there is an optimal level of scaffolding that depends on prior knowledge, and the optimum is curvilinear.

**What direct evidence does not exist.** No published RCT compares solo AI-facilitated CBL against group human-facilitated CBL on a delayed transfer measure. The cognitive mechanism the literature credits — *surfacing alternative interpretations through peer reasoning* — is exactly what is missing in the solo format. The AI substituting for the peer group is an unverified mechanism replacement.

**The deployment.** This is the open question I am least confident about. Honestly. The case-based literature credits *peer reasoning* with the reasoning gains, and the AI is not a peer. The deployment will tell us whether the AI's role as an interlocutor — surfacing alternative interpretations, pushing back on premature closure, prompting clinical reasoning under ambiguity — gets us close to the gains the human group format produces, or whether the gap is large. **I am betting that the AI-facilitated solo format captures most of the reasoning gain at much lower deployment cost.** I am also prepared to be wrong about this in a way that would require redesigning the Case Study mode to incorporate a peer-substitute layer that does not currently exist.

### 2.3 Open Question 3 — Does FSRS-style scheduling generalize to conceptual material?

**The bet.** FSRS (Free Spaced Repetition Scheduler) is the open-source algorithm now default in Anki, trained on hundreds of millions of review logs from primarily *vocabulary and factual* material. It produces ~20–30% fewer reviews for the same target retention compared to SM-2. Medhavi Quiz Me uses FSRS scheduling on conceptual material — definitions of *force*, *retrieval interference*, *complement cascade regulation* — where retrieval is more than recognition of a paired associate.

**Adjacent evidence.** Cepeda et al. 2006 (*Psychological Bulletin* 132(3): 354–380) meta-analysis of 317 experiments established the spacing principle holds across verbal recall tasks. Cepeda et al. 2008 (*Psychological Science* 19(11): 1095–1102) showed optimal inter-study interval scales with retention horizon. Kerfoot et al. 2010 (*Annals of Surgery* 252(2): 350–359) showed spaced retrieval in medical education generates *transfer* to novel diagnostic items. Roediger & Karpicke 2006 (*Psychological Science* 17(3): 249–255) shows the testing effect generalizes across material types.

**What direct evidence does not exist.** FSRS itself has not been validated on conceptual material at scale. The hundreds of millions of review logs that trained FSRS are dominated by language-learning and factual-recall use cases. Whether the Difficulty / Stability / Retrievability latent representation captures the dynamics of conceptual retrieval — where partial retrieval is meaningful and a *Hard* rating may indicate partial-mechanism understanding rather than partial-trace strength — is unknown.

**The deployment.** Testable within Medhavy v1.5 by varying the scheduling algorithm across cohorts and observing delayed retention at the GLP Y6 signal. **My bet is that the FSRS efficiency claim attenuates on conceptual material — same retention at maybe 5–15% fewer reviews instead of 20–30%, with the difference appearing in how *Hard* ratings get interpreted.** That is a falsifiable prediction. If FSRS holds its full efficiency on conceptual material the bet is wrong in a direction that helps the platform. If FSRS underperforms a simple fixed-interval schedule on conceptual material, the bet is wrong in a direction that requires algorithmic rethinking.

### 2.4 Open Question 4 — Is the Quiz Me habit loop driven by the due-count or the algorithm?

**The bet.** Anki users adopt the system as a daily habit; ~30% of US medical students use it consistently. The system has two distinct components: the FSRS scheduling algorithm (cognitive optimization), and the visible due-count plus completion event (habit loop). The Medhavi 1.5 design hypothesizes that **the due-count is the load-bearing UI** and the algorithm is a small contributor to whether students adopt the tool at all.

This is a design bet, not a tested claim. I am betting that the habit-formation literature — Wood 2019, Lally et al. 2010, the Zeigarnik effect (open tasks create cognitive pressure to close) — generalizes to retrieval-practice tools, and that the visible-due-count is the cue-action-reward loop doing the work.

**Adjacent evidence.** Wood 2019 (*Good Habits, Bad Habits*) on cue-action-reward structure. Lally et al. 2010 (*European Journal of Social Psychology* 40(6): 998–1009) on habit-formation timecourses. Zeigarnik 1927 on cognitive pressure from open tasks. Cohort studies in medical education show mature-card counts explaining over a third of variance in course exam scores (Deng, Gluckstein & Larsen 2015 in radiology; Schimmelpfennig et al. 2024 USMLE Step 1 cohort).

**What direct evidence does not exist.** No published study has dismantled Anki's habit loop to isolate the algorithm contribution from the due-count contribution. The argument from analogy to the habit literature is suggestive but not specific to the testing-effect tool.

**The deployment.** Two-by-two within-learner: FSRS-scheduling vs. simple-fixed-interval-scheduling × visible-due-count vs. no-due-count UI. Primary outcome: daily session frequency over 8 weeks. Secondary outcome: delayed retention. **I am betting the visible-due-count effect on daily session frequency is larger than the FSRS algorithm effect on retention.** If true, the design implication is large: the UI element is the load-bearing piece, and platforms that ship sophisticated scheduling without the habit-loop UI are over-investing in algorithm and under-investing in interface.

This is the question I think has the best chance of yielding clear signal within six weeks of deployment, because the daily-session-frequency outcome is fast.

### 2.5 Open Question 5 — Does backwards-faded scaffolding prevent the anxiety collapse in novice Glimmer users?

**The bet.** Pekrun's 2006 control-value theory of achievement emotions (*Educational Psychology Review* 18(4): 315–341) predicts students with high task value and low perceived control land in the *anxiety* quadrant, not the *engagement* quadrant. USMLE-trained medical students have spent two-plus years optimizing for closed-problem recognition; their first Glimmer — an ill-structured creative assignment — frequently lands them in anxiety. The Glimmer design mitigates with backwards-faded scaffolding (Renkl & Atkinson 2003): week 1 supplies framing, week 2 supplies framing partially, week 3 is fully open.

The bet is that the fading prevents the anxiety collapse.

**Adjacent evidence.** Belland, Walker, Kim & Lefler 2017 (*Review of Educational Research* 87(2): 309–344) meta-analysis of computer-based scaffolding in STEM (144 studies, *g* = 0.46) establishes that *scaffolded* ill-structured work produces cognitive gains; the fading is the design choice the meta-analysis identifies as critical. Puntambekar & Hübscher 2005 (*Educational Psychologist* 40(1): 1–12) and van de Pol, Volman & Beishuizen 2010 (*Educational Psychology Review* 22(3): 271–296) on contextualized fading scaffolding.

**What direct evidence does not exist.** No published study tests backwards-faded scaffolding specifically with USMLE-trained medical students on a Glimmer-style assignment over a multi-week trajectory with anxiety as a measured outcome.

**The deployment.** This is the question where the deployment has the cleanest test. Two arms within-learner across cohort or assignment: backwards-faded scaffolding vs. constant-low-scaffolding. Outcomes: abandonment rate in weeks 2–3; self-reported anxiety on the Achievement Emotions Questionnaire; Glimmer rubric scores at weeks 5–11. **I am betting that the faded condition produces lower abandonment, lower anxiety, and equivalent or higher rubric scores at week 11.** The fading-vs-no-fading comparison is the cleanest mechanism test in the deployment.

If the fading does not prevent the anxiety collapse, the implication is that the *transition* from supported to unsupported is the failure mode, regardless of how smooth the fade. The redesign would have to keep some form of structural scaffolding present at week 11 rather than removing it entirely.

### 2.6 Open Question 6 — Does priority-weighted scheduling outperform recall-only scheduling?

**The bet.** Pure FSRS schedules on predicted retrievability — when the algorithm thinks a card is about to be forgotten, it schedules a review. Medhavy Quiz Me adds priority weights:

$$\text{priority} = \alpha \cdot \text{prerequisite\_depth} + \beta \cdot \text{importance\_tier} + \gamma \cdot (1 - \text{retrievability}) + \delta \cdot \text{frequency\_tier}$$

The importance and frequency tiers are set by the professor at Tic TOC time — they inject domain knowledge the recall data alone cannot capture. The aviation pedagogy principle: any concept tagged `importance_tier = 'high'` is reviewed at least every 14 days regardless of FSRS prediction.

**Adjacent evidence.** The pedagogical content knowledge literature (Shulman 1986; Sadler et al. 2013) establishes domain-expert knowledge of *what matters* as a distinct and powerful predictor of student outcomes. The aviation pedagogy literature (FAA practical test standards; Salas et al. 2006 on crew resource management training) establishes that high-stakes rare events get mandatory scheduling rather than recall-dependent scheduling, with measurable safety outcomes.

**What direct evidence does not exist.** No published study directly compares priority-weighted scheduling against recall-only scheduling in a spaced-retrieval educational tool. The closest is the comparison of Anki SM-2 vs. FSRS — but that holds priority weighting constant and only varies recall prediction.

**The deployment.** Two arms: FSRS-only scheduling vs. FSRS + priority weights. Same content, same students, same retention horizon. Outcomes: retention of high-importance items at 90 days; overall retention at 90 days; review-time efficiency. **My bet is that priority weighting produces higher retention on high-importance items with no degradation on overall retention.** The risk is that priority weighting degrades overall efficiency (more reviews on items the algorithm would have scheduled less aggressively). That tradeoff is what the experiment is for.

### 2.7 Open Question 7 — Does Level-3 domain specificity outperform Level-1 generic instruction enough to justify the production cost?

**The bet.** The domain-specific instruction literature distinguishes Level 1 (generic), Level 2 (generic + domain capstone), Level 3 (domain-specific throughout, generic backbone). Level 3 plausibly captures the bulk of transfer-appropriate-processing benefits and motivation benefits at ~1.5–2× production cost over Level 1.

**Adjacent evidence.** Walkington 2013 (*Journal of Educational Psychology* 105(4): 932–945) on interest-personalization in Algebra I found transfer from personalized practice to non-personalized assessment. Walkington & Bernacki 2019 (*IJAIED* 29(1): 58–88) on deep vs. surface personalization found *d* = 0.39 for deep personalization for high-engagement students; *d* = −0.43 favoring surface for low-engagement students — **depth-matching matters more than depth itself**. Hulleman & Harackiewicz 2009 (*Science* 326(5958): 1410–1412) on utility-value writing prompts found improved course grades for low-performing students at zero marginal cost. Transfer-appropriate processing theory (Morris, Bransford & Franks 1977; Roediger, Gallo & Geraci 2002) predicts encoding-test match drives retrieval.

**What direct evidence does not exist.** No published RCT compares Level-1 vs. Level-3 instruction on the *same skill* in the *same population* with *delayed transfer* outcomes and *production-cost accounting*. The closest is Walkington 2013 — *no* personalization vs. *one variant* of personalization in a single ITS — not three levels of domain specificity at scale across multiple subjects.

**The deployment.** Three arms × two retention horizons: Level-1 generic, Level-2 generic+capstone, Level-3 domain-specific-throughout. Outcomes: near-transfer (within-domain application) at 30 days; far-transfer (cross-domain application) at 90 days; cost per 0.1 SD gain. **My bet is that Level-3 produces larger near-transfer gains and equivalent-or-worse far-transfer gains than Level-1, with the cost-per-0.1-SD breakdown determining whether Level-3 production cost is justified at any given audience scale.** The cost-collapse argument from Chapter 10 makes this bet much more interesting than it would have been in 2020: when Level-3 production cost falls, the magnitude of the near-transfer advantage required to justify Level-3 falls with it.

### 2.8 Open Question 8 — Does AI-generated educational content produce durable learning outcomes comparable to professionally produced content?

**The bet.** The cost-collapse argument from Chapter 10 is established at the unit-production level. Whether AI-generated content *of the same design quality* as Sesame-Street-class professional production produces *equivalent durable learning outcomes* is the open bet on which the cost-collapse argument structurally depends.

**Adjacent evidence.** Mayer's CTML meta-analyses on individual principles (Mayer 2014 handbook; Schroeder & Cenkci 2018; Schneider et al. 2018; Adesope & Nesbit 2012) establish what design features predict learning across hundreds of experiments. Yan et al. 2024 (*BJET* systematic scoping review) found AI-generated lesson plans rated comparable to human on structure but systematically lower on differentiation and contextual awareness. Bryant et al. 2024 ([arXiv:2504.05449](https://arxiv.org/html/2504.05449v1)) found educators preferred AI-generated plans on surface quality and human plans on fit-to-student-need. Singhal et al. 2023 ([Med-PaLM, *Nature* 620: 172–180](https://www.nature.com/articles/s41586-023-06291-2)) found high accuracy with clinically meaningful hallucination rates.

**What direct evidence does not exist.** No published RCT compares AI-generated educational content matched on Mayer's twelve principles against professionally produced equivalents with delayed retention and transfer outcomes as primary endpoints. The peer-reviewed evidence base for AI-generated educational content as a *learning* (not engagement) intervention is genuinely sparse and is dominated by vendor or preprint work from 2024–2025.

**The deployment.** Two arms: AI-generated content matched on Mayer's twelve principles (with explicit prompting for temporal contiguity, spatial contiguity, signaling, segmenting, coherence) vs. professionally produced equivalent on the same concepts. Outcomes: immediate post-test; delayed retention at 30/90 days; transfer to novel application items; production-cost-per-0.1-SD breakdown. **My bet is that AI-generated content matches professional production on immediate post-test, falls behind on delayed retention and transfer, with the gap larger for high-complexity content.** This is the single most important RCT the field could run, and Medhavy is structurally positioned to run a within-deployment version of it. The honest version of the cost-collapse argument from Chapter 10 hinges on the outcome.

---

## §3. Adjacent vs. Direct vs. Assertion — the Epistemic Ladder

The chapter's central epistemic move: distinguish three categories, and be honest about which one each claim sits in.

**Adjacent evidence.** Evidence on mechanisms or partial designs that are *components* of the integrated claim but do not test the integrated claim itself. ITS effect sizes are adjacent evidence for the bandit-engine claim. Spacing-effect meta-analyses are adjacent for the Quiz Me FSRS claim. CTML principles are adjacent for the Video and Animation claim.

**Direct evidence.** Evidence on the integrated claim under deployment conditions. Bastani 2025 is direct evidence for the AI-tutor-with-guardrails claim under the specific Bastani guardrail design. **No direct evidence exists for the integrated four-layer architecture claim — the platform has not been tested as a unit against a control.**

**Assertion.** Claims made without either adjacent or direct evidence. The chapter should be ruthless about calling these out when they appear in the EdTech literature.

The honest call: most published EdTech claims live at *adjacent*. Most published EdTech *marketing* lives at *assertion*. The Medhavy book's contribution is to be honest about which category each chapter's claim sits in. **The architecture chapters cite *adjacent* evidence for design decisions. The deployment chapters (when they arrive) will report *direct* evidence. The current state of the Medhavy claim is *adjacent* everywhere except where Bastani directly tests it.**

The recurrent diagnostic the chapter trains: when a vendor white paper claims "our platform improves learning outcomes by 40%," ask three questions.

1. Adjacent or direct?
2. If direct, what was the comparison condition?
3. If direct with a comparison, what was measured — engagement, immediate performance, or delayed transfer?

Most vendor claims fail at question 1. Most surviving claims fail at question 3.

---

## §4. The Student Consent Architecture as a Design Decision

I want to argue that consent architecture has *learning consequences*, not just regulatory consequences. This is not the standard framing. The standard framing treats consent as a compliance overhead. I think the standard framing is wrong.

### 4.1 The regulatory floor — FERPA and COPPA in 2026

The 2026 regulatory floor matters as the constraint, not the design driver. `[verify all dates and enforcement specifics at draft time — both regulations have been moving through 2025–2026]`

**FERPA** (Family Educational Rights and Privacy Act, 1974). In March 2025, the U.S. Department of Education required all state agencies to certify FERPA compliance by April 30, 2025 — an unprecedented enforcement mandate ([Statvix 2026 analysis](https://statvix.com/coppa-and-ferpa-in-2026-protecting-student-data-in-the-age-of-ai/); [studentprivacy.ed.gov](https://studentprivacy.ed.gov/)). Mid-2025 commentary noted that FERPA lacks clear cybersecurity requirements despite schools relying on hundreds of EdTech tools; experts urge modernization with vendor security obligations. AI use under FERPA requires institutions to interpret how AI accesses, uses, and stores student data — the regulation has not been amended for AI specifically but enforcement has expanded ([ArentFox Schiff AI Law Blog](https://www.afslaw.com/perspectives/ai-law-blog/the-development-ai-and-protecting-student-data-privacy)).

**COPPA** (Children's Online Privacy Protection Act, 1998; 2025 amendments). Major revision in 2025 with new rules effective June 23, 2025 and full compliance required by **April 22, 2026** `[verify exact date at draft time]`. The 2025 amendments shifted the default from opt-out to opt-in consent. Updated consent verification methods and requirements for explicit parental consent before sharing data with third parties fundamentally change how schools handle data from students under 13.

**State law.** As of 2025, 121+ state laws protect student privacy beyond FERPA.

### 4.2 The student-controlled epsilon

Most educational RCTs assign treatment. Some students receive the intervention. Some receive the control. Neither group chose. The ethics review asks: is the control degraded? If the treatment is believed to be better, is it ethical to withhold it?

Medhavy's design dissolves this question by letting the student choose their own epsilon — the exploration rate of the bandit on their account.

- **Null arm.** Turn off the AI entirely. Download the Kindle. Take the content and leave. This is how education worked for five hundred years. The null arm has dignity.
- **Low epsilon.** Mostly receive what the system currently believes is best, with occasional exploration. Low risk, low disruption — the student who wants to benefit from what the system knows without being a research participant.
- **Full RCT.** Higher exploration rate and active contribution to the research program. The student willing to try things the system has not tried yet.
- **Change settings at any time.** No student is trapped. The data from sessions before they left is still informative. The act of leaving is itself data.

The student-controlled epsilon is genuinely novel as an experimental design. Most educational RCTs assign treatment; students who opt into full RCT here are motivated participants whose engagement signal is cleaner than a randomly assigned cohort. Students who hold at low epsilon are revealing risk tolerance. **The traditional RCT treats attrition as a validity threat. This architecture treats it as a measurement.**

### 4.3 Why consent has learning consequences

Here is the design claim I want to defend explicitly. A student who *chose* the AI-on condition has a different learning trajectory than a student who was *assigned* it, even with identical exposure. The mechanism is motivation, self-determination theory (Ryan & Deci 2000, *American Psychologist* 55(1): 68–78), and the self-fulfilling-prophecy literature.

Ryan and Deci's work argues that *autonomy* — the sense that the action is self-endorsed — is a basic psychological need whose satisfaction predicts engagement and persistence. A student who chose the AI-on condition is acting in an autonomy-supportive context. A student who was assigned it is not. The treatment is the same. The trajectory is not.

The consent architecture is not orthogonal to learning. It is upstream of it. **A platform that runs a traditional RCT design — assigning treatment, measuring outcomes — is measuring a different mechanism than a platform that runs a chosen-treatment design.** The latter is what Medhavy commits to.

### 4.4 What the design commits to and what it does not

The Medhavi architecture commits to collecting:

- **Outcome data.** Quiz Me ratings, mode selections, dwell times, mastery threshold crossings, GLP component values per concept.
- **Process data.** Switching behavior between modes, abandonment events, recovery events after Quick Catch-Up.
- **Pseudonymized aggregate data** for cross-cohort comparison.

The architecture commits *not* to collect:

- **Identified outcome data without explicit consent.** Even within-platform, identified outcomes route through the consent gate.
- **Behavioral data outside the learning system.** No keystroke dynamics outside Quiz Me sessions, no mouse-tracking outside Glimmer composition, no ambient phone sensors. The platform does not act as a generic surveillance tool just because it could.
- **Inference about non-learning attributes.** No gender inference, no socioeconomic inference, no mental-health inference from textual content. Yan et al. 2024 documents that these are real risks of LLM-in-education deployments; the architecture commits not to act on them.

The "must be disclosed" layer: what data is collected, what is not, what the GLP components measure, and how switching is treated. **The disclosure is itself part of the consent.** A consent architecture without disclosed measurement commitments is consent in name only.

---

## §5. Switching Behavior as Signal

The most interesting data the consent architecture generates is not the steady-state choices. It is the switching behavior.

A student who **starts at low epsilon and moves to full RCT** mid-semester is showing me something. Possibly that the system earned their trust. Possibly that they became curious about what else the engine might try. Either reading is information.

A student who **starts engaged and downloads the Kindle at week eight** is showing me something else. Possibly that something stopped working. Possibly that they got what they needed and are done. Both possibilities are signal.

A student who **turns off the AI entirely the week before the exam** is showing me their mental model of what the system is for.

A student who **switches from Quiz Me to Glimmer mid-session** is showing the mode-selection signal the within-learner bandit should be updating on.

None of this is available in a traditional RCT, which treats switching as a compliance problem. The bandit does not need stable treatment assignment — it adapts continuously. **The switching behavior is part of the evidence stream.**

The architecture decision the chapter exposes: switching is signal, not failure. **The adaptive engine's job is not to *prevent* switching. It is to *read* switching.** A learner who switches to a mode the engine did not predict is providing the highest-information signal possible — the engine's prior was wrong. The system should update aggressively on switch events.

---

## §6. Worked Example — The Cancer Textbook Deployment at Six Weeks

What follows is the deployment report I would publish as a preprint if the cancer textbook hits the six-week mark with the data I expect it to produce. This is not a polished findings paper. It is the honest preliminary report — the kind of thing the field would benefit from seeing more of, and the kind of thing platforms with engagement metrics for headlines rarely produce.

I am writing this as a *design specification of what the preprint would contain*, not as a description of currently-existing data. The deployment is in progress as of 2026-05-17. The exact numbers below are placeholders that will be replaced with real values when the data is in. The *structure* of the report is what the chapter is committing to.

### What the platform has collected (placeholder structure)

- **Sample size:** ~120 medical students across two cohorts (Pilot Cohort 1, Validation Cohort 2). [verify actual N at draft time]
- **Distribution across mode choices:** Ask AI [X]%, Quiz Me [X]%, Case Study [X]%, Glimmer [X]% of total session time.
- **Distribution across consent settings:** Null arm [X]%, Low epsilon [X]%, Full RCT [X]%. Switching events: [X] total across cohort.
- **Completion rates:** [X]% completed Pilot module 1; [X]% Pilot module 2; abandonment concentrated in [where].

### What signal the GLP components are producing

Component-by-component, what the variance looks like and whether the variance is informative.

- **Y1 — Temporal Engagement.** Producing clean signal. The dwell-time distribution is bimodal in a way that distinguishes students who read carefully from students who clicked through. Variance is informative.
- **Y2 — Error Trajectory Coherence.** Producing usable signal on Quiz Me. Students with genuine partial understanding produce different error patterns than students who memorized.
- **Y6 — Retrieval Strength Decay.** Producing the cleanest signal. The 30-day retention check shows clear separation between mature-card and non-mature-card cohorts.
- **Y3, Y4, Y5, Y7.** Not yet at sample size sufficient for variance to be informative. Need more deployment time.

### Which of the eight open questions has preliminary evidence

- **Open Question 4** (Quiz Me habit loop driven by due-count or algorithm). Preliminary signal in daily-session-frequency data favors the due-count hypothesis. The within-learner UI variation produces a larger effect on session frequency than the within-learner algorithm variation. Sample size still small.
- **Open Question 6** (priority-weighted vs. recall-only scheduling). Preliminary signal favors priority-weighted on high-importance items, with no degradation on overall retention. Bet is currently surviving.
- **Open Question 3** (FSRS in conceptual material). Preliminary signal mixed. FSRS efficiency claim attenuates on conceptual material at roughly the magnitude the bet predicted — but the confidence interval is too wide to call.

The remaining five open questions — Questions 1, 2, 5, 7, 8 — require longer deployment. Six weeks is not enough.

### Calibrated uncertainty

For each preliminary signal: what would have to be true for the signal to mean what it appears to mean, and what would have to be true for it to be artifactual.

- *Open Question 4 signal.* Real if the cohort represents the broader medical-student adoption pattern; artifactual if the UI variation correlated with other features of the assigned interface (the variation was not blinded). The latter is plausible. Bet: real, but margin of evidence narrow.
- *Open Question 6 signal.* Real if the high-importance items were not also the items with the cleanest retrieval signal at baseline; artifactual if the priority-weighted condition oversampled items that were already easier to retain. Bet: real, but the analysis has to control for baseline retention.
- *Open Question 3 signal.* Mixed because the conceptual-vs-vocabulary distinction was not clean in the deployed Quiz Me items — some cards labeled "conceptual" were actually retrievable as vocabulary. The taxonomy needs revision before the next cohort.

### What the next six weeks will test

Pre-registered, not post-hoc. The Schein-of-an-RCT move: even though this is not a formal RCT, the next-period predictions are committed in writing.

- The Open Question 4 signal will either consolidate or disappear with the next cohort, with the blinding fix that was not present in Cohort 1.
- The Open Question 5 anxiety-collapse measurement will become possible at week 8–11 once the first cohort hits the fully-open Glimmer transition.
- The Open Question 8 AI-vs-professional-content comparison cannot start until the matched-content production pipeline is approved by the faculty reviewer, which is in progress.

**This is what an honest preliminary report looks like.** It is not "our platform improves learning outcomes by 40%." It is "here is what we collected, here is what the signal says, here is what would have to be true for the signal to mean what it appears to mean, here is what the next period will test." A field built on reports like this would have less hype and more cumulative knowledge.

The design specification *is* the deliverable. The actual deployment data will replace placeholders when the cohort matures.

---

## §7. Common Misconceptions

### "An honest inventory is a weakness in the design"

The plausible claim: a chapter that names eight open questions is a chapter that admits the architecture is not yet finished. A finished architecture would not need an honest inventory.

**Why it fails.** Every architecture sits at some point on the evidence ladder. *Adjacent*, *direct*, *assertion*. A book that asserts its architecture is finished, when the evidence at the integrated-claim level is adjacent rather than direct, is not finished — it is dishonest. The honest inventory is the move that distinguishes a research deployment from a marketing deployment. The architecture is honest *because* the gaps are visible. A chapter that hid the gaps would not have a stronger architecture; it would have a weaker epistemic position.

### "The Montaigne register is a hedge"

The plausible claim: writing in the first person about "bets" rather than asserting findings is rhetorical softening — a way to avoid commitment.

**Why it fails.** The Montaigne register is not a hedge. It is a *specification of what category of claim is being made*. "I am betting that priority-weighted scheduling outperforms recall-only scheduling on high-importance items" is more specific than "priority-weighted scheduling is better." The first commits to a falsifiable prediction with a named bet-holder. The second hides the bet structure behind a passive-voice claim. The first is more accountable. The second is more rhetorically confident. Accountability is what the chapter requires. Rhetoric is what the field already has too much of.

### "Switching behavior is a compliance problem"

The plausible claim: a student who switches modes mid-session, or who downloads the Kindle and leaves, is breaking the experimental design. The data from non-compliant students should be discarded.

**Why it fails.** This is the traditional RCT framing applied to a context it does not fit. The within-learner bandit does not require stable treatment assignment — it adapts continuously, and a switch is exactly the signal the bandit should be updating on. Treating switching as a compliance problem is treating the most informative event in the data stream as noise. The architecture deliberately preserves switching as signal because switching is where the engine's prior is most clearly wrong.

---

## §8. Exercises

### Exercise 11.1 — The epistemic audit (Evaluate)

A vendor publishes a white paper claiming their AI tutoring platform "improves learning outcomes by 40%" based on a six-month deployment at three high schools.

Apply the §3 epistemic audit (adjacent / direct / assertion). For each of the three questions, identify what additional information you would need before accepting the claim, and what specific finding would convert the claim from assertion to direct evidence.

### Exercise 11.2 — Specifying the instrumentation (Apply)

Pick three of the eight open questions from §2. For each, specify the *minimum* instrumentation required to generate preliminary evidence within one semester of deployment. Include: what the platform must log, what the cohort size needs to be, what the comparison condition is, and what the primary outcome measure is.

Hand the specification to a colleague who knows the literature. Ask whether they could collect the data from the spec. The exercise is the test of whether you have made the eight open questions operational.

### Exercise 11.3 — Designing the consent architecture (Analyze)

Design the student consent architecture for a medical school intelligent textbook. Address each of the following:

(a) What data must be collected for GLP to function. Specify which of the seven GLP components are minimum viable for the deployment, and what the platform must log to instrument them.

(b) What should not be collected. Name three categories of data the architecture commits not to collect even though it technically could, and explain why each commitment is a *design* decision with learning consequences (per §4.3), not just a compliance overhead.

(c) What must be disclosed. Specify the disclosure document a student would see when they first log in, written at a reading level appropriate for the audience.

### Exercise 11.4 — Switching behavior as signal (Apply)

You are watching the bandit dashboard at week six of a deployment. A student who has been at low epsilon for four weeks switches to full RCT, then switches back to low epsilon two days later, then turns off the AI entirely the day before the unit exam.

(a) What is each switch telling you about the student's mental model of the platform?

(b) Should the bandit update its prior on this student's account, and if so, how?

(c) Should the bandit's update propagate to the cross-cohort prior at all? Explain why or why not, using §5 and §4.4 as the scaffold.

### Exercise 11.5 — Write your own open question (Produce)

The chapter names eight open questions. Add a ninth. Specify:

(a) The question precisely.
(b) What adjacent evidence currently exists.
(c) What direct evidence does not yet exist.
(d) What the deployment would have to do to test it.

The exercise is the discipline of the chapter — the willingness to name what is not yet known, in a category structure that makes the not-knowing operational rather than rhetorical.

---

## What Would Change My Mind

A deployment in which the integrated four-layer architecture was tested against a credible control (a well-designed but bolt-on EdTech platform serving the same cohort on the same curriculum) with delayed transfer outcomes at 90 days as the primary endpoint, pre-registered with effect-size targets set by the cost-collapse argument from Chapter 10, would convert the architecture's claim from *adjacent evidence supports this* to *direct evidence supports this*. If the integrated architecture beat the control by the predicted margin, the open-questions framing would soften. If it did not — if the four-layer architecture failed to outperform a well-designed bolt-on system at the same audience — I would have to rethink whether the integration is the load-bearing claim or whether one or two layers are doing the work and the rest are theoretical decoration. Either outcome would change the chapter materially. The Bastani-equivalent for the integrated architecture, run on the deployment substrate Medhavy is generating, would settle this.

## Still Puzzling

What is the right time-horizon for the switching-as-signal architecture? The bandit can update on the switch event itself; but the *interpretation* of the switch — was it information about the student's mental model, or was it noise — may require longitudinal data over months that the deployment is only beginning to accumulate.

Does the student-controlled epsilon design produce a self-selected cohort whose learning outcomes generalize to populations that did not choose their epsilon? The autonomy-supportive mechanism (Ryan & Deci 2000) predicts the chosen-treatment cohort will outperform an assigned-treatment cohort on the same exposure. The architecture commits to this design as ethical; the question of whether it generalizes is a separate empirical question and one I do not have a clean answer to.

Are the eight questions actually eight, or are some of them facets of a smaller number of underlying questions? Questions 3, 4, 6 all concern Quiz Me design; Questions 1, 2 concern AI-mediated interaction; Questions 5, 7, 8 concern content and scaffolding design. The taxonomy is not a clean partition. A more elegant inventory might collapse them. The current eight is the form the deployment instruments against.

---

## Bridge to Chapter 12

The honest inventory is complete. Eight open questions named, each anchored to what is and is not known, each instrumented in the deployment.

Chapter 12 is the last chapter. It delivers the instrument that converts everything this book has built into a specification a developer can build from. And it makes the meta-move that has been visible in the structure of every preceding chapter: this book *is* a Tic TOC session. The reader has been living the design conversation since the IDK-IDK opening of Chapter 1.

The map. The conversation. The handoff to the build. One chapter to go.

---

**Tags:** open-questions, Montaigne-essai, epistemic-honesty, GLP, student-consent, within-learner-bandit, switching-as-signal
