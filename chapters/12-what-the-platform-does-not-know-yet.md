# Chapter 12 — What the Platform Does Not Know Yet

*Que sais-je?*

---

Michel de Montaigne struck a medallion in 1576. On it, three words: *Que sais-je?* What do I know? The question was his operating discipline. He invented the essay — *essai*, French for *attempt* — as a form built on making the act of trying visible rather than disguising the trying as already-arrived. *I am myself the matter of my book.* He wrote about himself in order to arrive at provisional truths, in a period when all knowing seemed treacherous.

The architecture I have delivered in Chapters 1 through 10 is settled enough to deploy and measure. It is not settled enough to defend without measurement. The deployment is the *essai*. This chapter is the honest inventory.

I have to be in this chapter in a way I have not been in the others. The preceding chapters delivered an argument — evidence cited, architecture built, recommendations made. This chapter is the inventory I would have to produce if someone asked me, out loud, what Medhavy currently knows and what it does not. A book that has just delivered a complete architecture has to be willing to name the gaps. Anything less is the IDK-IDK problem at the book level: the metric says confidence, the learning says otherwise.

So I am here, in the first person, naming bets I am personally making.

---

## Adjacent, Direct, Assertion — Three Rungs

Before the inventory, a frame for reading it.

**Adjacent evidence** is evidence on mechanisms or partial designs that are components of the integrated claim but do not test the integrated claim itself. ITS effect sizes are adjacent evidence for the adaptive-engine claim. Spacing-effect meta-analyses are adjacent for the Quiz Me FSRS claim. These studies are real, well-conducted, and relevant. They do not test the thing I am actually claiming.

**Direct evidence** is evidence on the integrated claim under deployment conditions. Bastani 2025 is direct evidence for the AI-tutor-with-guardrails claim under the specific Bastani guardrail design. It is the cleanest direct evidence the field currently has for anything like what this platform does.

**Assertion** is a claim made without either. Most published EdTech claims live at adjacent. Most EdTech marketing lives at assertion.

The honest call: the architecture chapters cite adjacent evidence for design decisions. The deployment chapters will report direct evidence. The current state of the Medhavy claim is adjacent everywhere except where Bastani directly tests it. When a vendor white paper claims "our platform improves learning outcomes by 40%," the audit is three questions: adjacent or direct? If direct, what was the comparison condition? If direct with a comparison, what was measured — engagement, immediate performance, or delayed transfer? Most vendor claims fail at question one. Most surviving claims fail at question three.

The eight open questions that follow are the bets the deployment is built to test. Each one gets: what the bet is, what adjacent evidence supports it, what direct evidence does not yet exist, and what the deployment can do about it.

<!-- → [INFOGRAPHIC: the three-rung epistemic ladder rendered as a vertical diagram — bottom rung: Assertion (no evidence, claim floats free); middle rung: Adjacent (real evidence on components, does not test the integrated claim); top rung: Direct (integrated claim tested under deployment conditions, Bastani 2025 as the only named example); for each rung, one example from EdTech marketing and one from the Medhavy architecture — reader should be able to place any claim they encounter on this ladder in about five seconds] -->

---

## The Eight Bets

**Bet 1 — Does context-anchoring alone convert GPT-Base failure to GPT-Tutor success?**

Bastani et al. 2025 found that GPT-4 without guardrails harmed durable learning by 17 percentage points on the unassisted exam. GPT-4 with teacher-designed refuse-the-answer guardrails did not. Medhavy's Ask AI mode uses RAG-grounded context-anchoring as its primary guardrail: the model retrieves from the current textbook section plus prerequisites and answers within that scope. Bastani's guardrail varied answer-refusal behavior. Medhavy's varies retrieval scope. These are different mechanisms. The bet is that context-anchoring alone — without explicit answer refusal — is sufficient to convert Base-condition harm to Tutor-condition neutrality or gain.

No published RCT has tested context-anchored AI tutoring against unguarded AI tutoring on a delayed unassisted exam. The Bastani design dimension was *refuse-the-answer*. Medhavy's is *retrieve-from-curriculum*. The comparison has not been run. The deployment can approximate it via within-learner randomization across concept nodes — some concepts receive context-anchored Ask AI, others receive minimal-guardrail Ask AI, with delayed retention measured against both.

If the signal is null, the architecture needs refuse-and-hint scaffolding layered on top of context-anchoring. That would be a meaningful redesign.

**Bet 2 — Does pre-written faculty-reviewed CBL produce reasoning gains comparable to group human-facilitated CBL when solo and asynchronous?**

Thistlethwaite et al. 2012 synthesized 104 studies of case-based learning in health-professional education and found consistent evidence of reasoning gains in the group, human-facilitated format. Medhavy's Case Study mode is solo, asynchronous, AI-facilitated on pre-written faculty-reviewed cases. The cognitive mechanism the literature credits — surfacing alternative interpretations through peer reasoning — is exactly what is missing in the solo format. The AI substituting for the peer group is an unverified mechanism replacement.

This is the open question I am least confident about. Honestly. The case-based literature credits peer reasoning with the reasoning gains, and the AI is not a peer. The bet is that the AI-facilitated solo format captures most of the reasoning gain at much lower deployment cost. I am also prepared to be wrong about this in a way that would require redesigning the Case Study mode to incorporate a peer-substitute layer that does not currently exist.

**Bet 3 — Does FSRS-style scheduling generalize to conceptual material?**

FSRS, the open-source scheduling algorithm now default in Anki, was trained on hundreds of millions of review logs from primarily vocabulary and factual material. It produces roughly 20–30% fewer reviews for the same target retention compared to SM-2. Medhavy Quiz Me uses FSRS scheduling on conceptual material — definitions of *force*, *retrieval interference*, *complement cascade regulation* — where retrieval is more than recognition of a paired associate. Whether the Difficulty / Stability / Retrievability latent representation captures the dynamics of conceptual retrieval is unknown.

The bet is that the FSRS efficiency claim attenuates on conceptual material — same retention at maybe 5–15% fewer reviews instead of 20–30%, with the difference appearing in how Hard ratings get interpreted. That is a falsifiable prediction. If FSRS holds its full efficiency on conceptual material, the bet is wrong in a direction that helps the platform. If FSRS underperforms a simple fixed-interval schedule on conceptual material, the bet is wrong in a direction that requires algorithmic rethinking.

**Bet 4 — Is the Quiz Me habit loop driven by the due-count or the algorithm?**

Anki has two distinct components: the scheduling algorithm (cognitive optimization) and the visible due-count plus completion event (habit loop). The bet is that the due-count is the load-bearing UI and the algorithm is a small contributor to whether students adopt the tool at all. This is a design bet, not a tested claim. Wood 2019 on cue-action-reward structure, Lally et al. 2010 on habit-formation timecourses, and the Zeigarnik effect on cognitive pressure from open tasks are the adjacent evidence. No published study has dismantled Anki's habit loop to isolate the algorithm contribution from the due-count contribution.

The deployment test is a two-by-two within-learner: FSRS-scheduling versus simple-fixed-interval-scheduling, crossed with visible-due-count versus no-due-count UI. Primary outcome: daily session frequency over eight weeks. The bet is that the visible-due-count effect on daily session frequency is larger than the FSRS algorithm effect on retention. If true, the design implication is large: the UI element is the load-bearing piece, and platforms that ship sophisticated scheduling without the habit-loop UI are over-investing in algorithm and under-investing in interface.

This is the question with the best chance of yielding clear signal within six weeks of deployment, because the daily-session-frequency outcome is fast.

**Bet 5 — Does backwards-faded scaffolding prevent the anxiety collapse in novice Glimmer users?**

Pekrun's 2006 control-value theory of achievement emotions predicts that students with high task value and low perceived control land in the anxiety quadrant, not the engagement quadrant. USMLE-trained medical students have spent two years optimizing for closed-problem recognition. Their first Glimmer — an ill-structured creative assignment — frequently lands them in anxiety. The Glimmer design mitigates with backwards-faded scaffolding: week one supplies framing, week two supplies framing partially, week three is fully open. Belland et al. 2017 meta-analysis of computer-based scaffolding in STEM (144 studies, g = 0.46) establishes that scaffolded ill-structured work produces cognitive gains and identifies fading as the critical design choice. No published study tests backwards-faded scaffolding specifically with USMLE-trained medical students on a Glimmer-style assignment with anxiety as a measured outcome.

The bet: the faded condition produces lower abandonment, lower anxiety, and equivalent or higher rubric scores at week eleven. If the fading does not prevent the anxiety collapse, the implication is that the transition from supported to unsupported is the failure mode regardless of how smooth the fade, and the redesign would have to keep some structural scaffolding present at week eleven rather than removing it entirely.

**Bet 6 — Does priority-weighted scheduling outperform recall-only scheduling?**

Pure FSRS schedules on predicted retrievability. Medhavy Quiz Me adds priority weights:

$$\text{priority} = \alpha \cdot \text{prerequisite\_depth} + \beta \cdot \text{importance\_tier} + \gamma \cdot (1 - \text{retrievability}) + \delta \cdot \text{frequency\_tier}$$

The importance and frequency tiers are set by the professor at Tic TOC time — they inject domain knowledge the recall data alone cannot capture. The aviation pedagogy principle: any concept tagged importance\_tier = high is reviewed at least every fourteen days regardless of FSRS prediction. No published study directly compares priority-weighted scheduling against recall-only scheduling in a spaced-retrieval educational tool. The adjacent evidence is the pedagogical content knowledge literature — Shulman 1986, Sadler et al. 2013 — establishing domain-expert knowledge of what matters as a distinct predictor of student outcomes.

The bet: priority weighting produces higher retention on high-importance items with no degradation on overall retention. The risk is that priority weighting degrades overall efficiency by over-scheduling items the algorithm would have scheduled less aggressively. That tradeoff is what the experiment is for.

**Bet 7 — Does Level-3 domain specificity outperform Level-1 generic instruction enough to justify the production cost?**

The domain-specific instruction literature distinguishes Level-1 (generic), Level-2 (generic plus domain capstone), Level-3 (domain-specific throughout). Walkington and Bernacki 2019 found d = 0.39 for deep personalization for high-engagement students and d = −0.43 favoring surface personalization for low-engagement students — depth-matching matters more than depth itself. No published RCT compares Level-1 against Level-3 on the same skill in the same population with delayed transfer outcomes and production-cost accounting.

The bet: Level-3 produces larger near-transfer gains and equivalent-or-worse far-transfer gains than Level-1, with the cost-per-0.1-SD breakdown determining whether Level-3 production cost is justified at any given audience scale. The cost-collapse argument from Chapter 10 makes this bet much more interesting than it would have been in 2020. When Level-3 production cost falls, the magnitude of the near-transfer advantage required to justify Level-3 falls with it.

**Bet 8 — Does AI-generated educational content produce durable learning outcomes comparable to professionally produced content?**

The cost-collapse argument is established at the unit-production level. Whether AI-generated content of the same design quality as professionally produced content produces equivalent durable learning outcomes is the open bet on which the cost-collapse argument structurally depends. Yan et al. 2024 found AI-generated lesson plans rated comparable to human on structure but systematically lower on differentiation and contextual awareness. No published RCT compares AI-generated educational content matched on Mayer's twelve multimedia design principles against professionally produced equivalents with delayed retention and transfer outcomes as primary endpoints.

The bet: AI-generated content matches professional production on immediate post-test, falls behind on delayed retention and transfer, with the gap larger for high-complexity content. This is the single most important RCT the field could run, and Medhavy is structurally positioned to run a within-deployment version of it. The honest version of the cost-collapse argument from Chapter 10 hinges on the outcome.

<!-- → [TABLE: the eight bets as a reference table — columns: bet number and question (one clause), adjacent evidence (one citation), what direct evidence is missing (one clause), deployment test design (one clause), predicted outcome (one clause), what a wrong result would require — reader should be able to scan all eight in two minutes and know exactly which bets are closest to having evidence and which are furthest out] -->

---

## The Consent Architecture Is a Design Decision

I want to argue that consent architecture has learning consequences, not just regulatory consequences. This is not the standard framing. The standard framing treats consent as a compliance overhead. The standard framing is wrong.

Most educational RCTs assign treatment. Some students receive the intervention, some the control. Neither group chose. The ethics review asks: is the control degraded? If the treatment is believed to be better, is it ethical to withhold it?

Medhavy's design dissolves this question by letting the student choose their own exploration rate.

The null arm: turn off the AI entirely, download the Kindle, take the content and leave. This is how education worked for five hundred years. It has dignity. The low-epsilon arm: mostly receive what the system currently believes is best, with occasional exploration. The full-RCT arm: higher exploration rate and active contribution to the research program. Change settings at any time. Data from sessions before leaving is still informative. The act of leaving is itself data.

<!-- → [DIAGRAM: the four consent arms as a spectrum — left: Null arm (AI off, Kindle only, pure content delivery); center-left: Low epsilon (mostly current-best, occasional exploration, low disruption); center-right: Full RCT (higher exploration, research participant, highest information value); far right: Exit (download Kindle, leave — "act of leaving is data" labeled explicitly); arrows showing that movement between arms is permitted at any time and that switching is itself a measurement event, not a compliance failure] -->

Here is the design claim. A student who *chose* the AI-on condition has a different learning trajectory than a student who was *assigned* it, even with identical exposure. Ryan and Deci's self-determination theory argues that autonomy — the sense that the action is self-endorsed — is a basic psychological need whose satisfaction predicts engagement and persistence. A student who chose the AI-on condition is acting in an autonomy-supportive context. A student who was assigned it is not. The treatment is the same. The trajectory is not.

The consent architecture is not orthogonal to learning. It is upstream of it. A platform that runs a traditional RCT — assigning treatment, measuring outcomes — is measuring a different mechanism than a platform that runs a chosen-treatment design.

The architecture collects outcome data (Quiz Me ratings, mode selections, dwell times, mastery threshold crossings, GLP component values per concept), process data (switching behavior between modes, abandonment events, recovery events), and pseudonymized aggregate data for cross-cohort comparison. It commits not to collect identified outcome data without explicit consent, behavioral data outside the learning system, or inferences about non-learning attributes — no gender inference, no socioeconomic inference, no mental-health inference from textual content. Yan et al. 2024 documents these as real risks of LLM-in-education deployments. The architecture commits not to act on them. The disclosure is part of the consent: a consent architecture without disclosed measurement commitments is consent in name only.

---

## Switching Is Signal, Not Failure

The most interesting data the consent architecture generates is not the steady-state choices. It is the switching behavior.

A student who starts at low epsilon and moves to full RCT mid-semester is showing something — possibly that the system earned trust, possibly curiosity about what else the engine might try. Either reading is information.

A student who starts engaged and downloads the Kindle at week eight is showing something else — possibly that something stopped working, possibly that they got what they needed and are done. Both are signal.

A student who turns off the AI entirely the week before the exam is showing their mental model of what the system is for.

A student who switches from Quiz Me to Glimmer mid-session is showing the mode-selection signal the within-learner bandit should be updating on.

None of this is available in a traditional RCT, which treats switching as a compliance problem. The bandit does not need stable treatment assignment — it adapts continuously. The switching behavior is part of the evidence stream. The adaptive engine's job is not to prevent switching. It is to read switching. A learner who switches to a mode the engine did not predict is providing the highest-information signal possible: the engine's prior was wrong. The system should update aggressively on switch events.

The traditional RCT treats attrition as a validity threat. This architecture treats it as a measurement.

<!-- → [INFOGRAPHIC: switching behavior taxonomy — four panels, one per switch type described in the section: (1) low-epsilon → full-RCT mid-semester (label: "trust signal or curiosity"); (2) engaged → downloads Kindle at week eight (label: "stopped working or finished"); (3) AI off the week before exam (label: "reveals mental model of platform purpose"); (4) Quiz Me → Glimmer mid-session (label: "highest-information signal: engine prior was wrong") — each panel shows what the bandit should do with the signal and how aggressively it should update] -->

---

## What Honest Reporting Looks Like

I want to commit to what the platform would publish at six weeks of deployment — not to report data that does not yet exist, but to make visible the structure of honest reporting.

The report is not "our platform improves learning outcomes by 40%." It is: here is what was collected, disaggregated so the reader sees the variance. Here is what each GLP component is producing. Y1 (temporal engagement) and Y6 (retrieval strength decay) produce clean signal early. Y3, Y4, Y5, and Y7 need more time. Here is which of the eight bets has preliminary evidence — Bet 4 (due-count versus algorithm) is fastest because the daily-session-frequency outcome is dense; Bet 6 (priority-weighted scheduling) gets preliminary signal on high-importance item retention by week eight; Bet 3 (FSRS on conceptual material) is mixed in a way consistent with the prediction. Here is calibrated uncertainty for each signal: what would have to be true for the signal to be real, and what would have to be true for it to be artifactual. Here is what the next period will test, committed in writing before that period begins.

That is the schein-of-an-RCT move: even though this is not a formal RCT, the next-period predictions are committed before the data arrives. Pre-registered, not post-hoc.

This is what the field needs more of. Platforms with engagement metrics for headlines rarely produce it.

<!-- → [TABLE: the honest reporting template as a reusable structure — rows: Sample and distribution, GLP component signal (component by component), Bets with preliminary evidence (which bets, what the signal shows), Calibrated uncertainty per signal (what would make it real vs. artifactual), Next-period pre-registered predictions — each row shows what an honest report contains vs. what a typical vendor white paper contains; the contrast column is the argument] -->

---

## What This Inventory Is For

The architecture is honest exactly because the gaps are visible. A platform that hides its uncertainty is making one argument about what it knows. A platform that publishes what it knows and what it does not is making the opposite argument.

Montaigne did not write *Que sais-je?* as an admission of failure. He wrote it as a discipline. The question forced him to keep looking, to resist the premature certainty that his period was producing in every direction. The field of educational technology in 2026 is producing that certainty in every direction. Every vendor claims to have solved the problem. Every platform logs engagement and calls it learning.

The discipline is to keep asking the question. What do I know. What is adjacent. What is direct. What is assertion. What does the deployment test.

The architecture earns the right to say it is honest. The gaps are where the science lives.
