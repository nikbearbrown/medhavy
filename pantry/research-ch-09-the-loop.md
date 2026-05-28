# Research: Chapter 9 — The Loop: Present, Measure, Adapt
## Medhavy: Is the Loop Worth It?

**Chapter one-line:** The reader learns what the contextual bandit is in plain language, what "adapt" actually means in practice, and why Canvas cannot close the loop Medhavy closes.
**Research date:** 2026-05-27

---

## 1. Primary Sources

### Foundational papers and texts

**Bandit literature (mechanism):**

- **Robbins, H. (1952). "Some Aspects of the Sequential Design of Experiments." *Bulletin of the American Mathematical Society* 58: 527-535.** The founding paper. Robbins introduces the multi-armed bandit as a sequential decision problem under uncertainty. The mathematical anchor for the entire field. Largely unknown outside statistics — ideal Wayback Machine candidate.
- **Auer, P., Cesa-Bianchi, N., & Fischer, P. (2002). "Finite-time Analysis of the Multiarmed Bandit Problem." *Machine Learning* 47: 235-256.** The UCB (Upper Confidence Bound) algorithm — the workhorse classical bandit algorithm. Mathematical guarantees on exploration-exploitation trade-off. Cited in essentially all bandit-in-education papers.
- **Thompson, W. R. (1933). "On the Likelihood That One Unknown Probability Exceeds Another in View of the Evidence of Two Samples." *Biometrika* 25: 285-294.** Thompson sampling — the Bayesian bandit algorithm, often outperforming UCB in practice. A 1933 paper that became foundational 80 years later.
- **Li, L., Chu, W., Langford, J., & Schapire, R. E. (2010). "A Contextual-Bandit Approach to Personalized News Article Recommendation." *Proceedings of the 19th International Conference on World Wide Web (WWW)*: 661-670.** The LinUCB paper. The contextual bandit's signature deployment: Yahoo News personalization. The reader should understand that the algorithm Medhavy uses is the same general class as the one that has personalized news, ads, and recommendations for 15+ years — proven at internet scale, now applied to learning.
- **Sutton, R. S., & Barto, A. G. (1998 / 2018, 2nd ed.). *Reinforcement Learning: An Introduction.* MIT Press.** The standard textbook. The slot-machine analogy that TIKTOC names as the bandit's plain-language frame is Sutton & Barto's pedagogical move. Chapter 2 of Sutton & Barto is the canonical reference for the explore/exploit framing.
- **Lattimore, T., & Szepesvári, C. (2020). *Bandit Algorithms.* Cambridge University Press.** The current research-level textbook. More rigorous than Sutton & Barto; not needed for the curriculum director but cite once for credibility.

**Educational deployments of bandits:**

- **Liu, R., & Koedinger, K. R. (2017). "Closing the Loop: Automated Data-Driven Cognitive Model Discoveries Lead to Improved Instruction and Better Learning." *Journal of Educational Data Mining* 9(1): 25-41.** Carnegie Mellon's work on closed-loop instruction. The most cited educational bandit / model-based adaptation work.
- **Lan, A. S., & Baraniuk, R. G. (2016). "A Contextual Bandits Framework for Personalized Learning Action Selection." *Educational Data Mining*.** Direct bandit-for-education application. The pedagogical-action-selection problem framed exactly as Medhavy frames it.
- **Clement, B., Roy, D., Oudeyer, P.-Y., & Lopes, M. (2015). "Multi-Armed Bandits for Intelligent Tutoring Systems." *Journal of Educational Data Mining* 7(2): 20-48.** French/INRIA team. Demonstrates exploration-exploitation in adaptive tutoring with positive learning gains.
- **Williams, J. J., et al. (2016). "AXIS: Generating Explanations at Scale with Learnersourcing and Machine Learning." *Learning @ Scale*.** Bandit-driven explanation selection at scale. Most accessible "bandit in real classrooms" reference for a non-technical reader.

**The cold-start problem:**

- **Schein, A. I., Popescul, A., Ungar, L. H., & Pennock, D. M. (2002). "Methods and Metrics for Cold-Start Recommendations." *SIGIR*.** The foundational paper on the cold-start problem in recommender systems. Directly applicable: the bandit's "first six sessions are exploratory" framing is the cold-start problem in education-specific clothing.

**The evidence library (interventions the bandit chooses among):**

- **Hattie, J. (2009 / 2023). *Visible Learning.* Routledge.** Meta-analyses of 800+ educational interventions ranked by effect size. The reader has heard of this. The book should reference Hattie as the "evidence library" concept — there is a body of literature on what teaching moves work, and the bandit picks among them.
- **Dunlosky, J., Rawson, K. A., Marsh, E. J., Nathan, M. J., & Willingham, D. T. (2013). "Improving Students' Learning with Effective Learning Techniques: Promising Directions from Cognitive and Educational Psychology." *Psychological Science in the Public Interest* 14(1): 4-58.** The ranked list of study techniques by evidence base. Spaced practice and retrieval practice are top-rated. Critical context: the bandit is not inventing pedagogical interventions; it is selecting among interventions with established evidence bases for *this specific student-concept pair*.
- **Pashler, H., et al. (2008). *Organizing Instruction and Study to Improve Student Learning.* IES Practice Guide.** The US Department of Education's evidence-grounded recommendations. Useful for "the bandit's choices are within an evidence-based menu."

**The bandit-as-experiment frame:**

- **Box, G. E. P., Hunter, W. G., & Hunter, J. S. (1978 / 2005, 2nd ed.). *Statistics for Experimenters.* Wiley.** The classical text on designed experiments. Useful for framing the bandit as continuous experimentation per student per concept.
- **Kohavi, R., Tang, D., & Xu, Y. (2020). *Trustworthy Online Controlled Experiments.* Cambridge University Press.** Modern A/B testing in deployment. Microsoft's playbook. Useful for the "Medhavy is an experiment that runs continuously" framing.

### Key empirical cases

- **Yahoo News article-selection deployment (2010+).** The original LinUCB at scale. Public; documented in the Li et al. (2010) paper. Useful as the "bandits work in the real world" anchor.
- **Microsoft Research and Netflix recommendation systems.** Both use contextual bandits at production scale. The reader has consumed bandit output daily for years.
- **DataShop (Carnegie Mellon).** Open data on closed-loop instruction in mathematics and chemistry. Most relevant deployed-in-education case.
- **Mostafavi, B., & Barnes, T. (2017+) work on bandit-driven hint selection in ITSs.** Multiple papers; the deployed-in-education-and-it-works existence proof.

---

## 2. The Core Concept — State of the Field

### What is settled

The mathematics of bandits is settled. UCB, Thompson sampling, and LinUCB have rigorous theoretical guarantees. The algorithms work in deployment at massive scale (Yahoo, Netflix, Microsoft, every major recommendation system). The exploration-exploitation trade-off is well-understood.

That contextual bandits *can* personalize instructional decisions is settled at the algorithm level. That they *do* produce improved learning outcomes in deployment is established in small-to-medium pilots (Liu, Lan, Clement, Williams cited above) but not at the scale at which Medhavy proposes to operate.

The cold-start problem is settled as a real phenomenon. The first N interactions for a new user are exploratory by necessity; performance during this period is below steady-state. The mitigation strategies (prior-informed initialization, population-level priors, conservative exploration) are well-developed.

### What is disputed

Whether contextual bandits in education produce *durable* learning gains, as opposed to immediate-performance gains, is genuinely disputed. Most published bandit-in-education studies report on immediate metrics. Few have measured delayed retention. (This is the same gap Bastani 2025 exposed for AI tutoring more generally.) The Medhavy claim — that the bandit using GLP signals as reward will produce durable learning — is theoretically motivated by the choice of reward signal but not yet empirically validated at scale.

The choice of reward signal is the most consequential design decision and is *what makes Medhavy's loop different* from existing adaptive systems. Most deployed adaptive systems use immediate accuracy as the reward signal. Medhavy proposes delayed retrieval at seven days (per TIKTOC's Ch 8 worked example exercise). This is a credible bet but a bet.

Whether per-student per-concept bandits are the right granularity is also debated. Coarser granularity (per-student) sacrifices specificity; finer granularity (per-student per-subconcept) requires more data than most courses produce. Medhavy's choice is a middle ground.

### What has changed recently (last 5 years)

- **LLM-driven content generation has changed the "arms" available to the bandit.** Previously, the bandit chose among a fixed menu of pre-authored interventions. Now interventions can be generated on the fly. This is power and risk. Medhavy's four-mode architecture treats the modes as the stable arms; the within-mode content is LLM-generated under faculty review for high-stakes content (Case Study).
- **Off-policy evaluation has matured.** Researchers can now estimate counterfactual learning outcomes ("what would have happened if we'd shown a different intervention") from logged data, which lets institutions audit the bandit's policy choices.
- **Equity concerns about adaptive systems have intensified.** A bandit that "adapts" to a student's behavioral signature can entrench disadvantage if early signals are noisy. Recent literature (e.g., on fairness in adaptive learning) is required reading for the chapter's honest-limits section.

---

## 3. Application Domain Examples

1. **Pharmacology — anticoagulation reasoning across 8 weeks.** The TIKTOC worked example. Bandit explores all four modes weeks 1–2 with no clear winner. Quiz Me producing strong Y6 signal by week 3 — student is retaining the warfarin-vs.-DOAC mechanism. Ask AI's Y4 signal showing borrowed certainty on edge cases — student gives confident wrong answers when the case is ambiguous. By week 6, bandit's policy has shifted to Case Study for this concept-student pair. The reader can see the loop in action.
2. **Nursing — sepsis recognition over a semester.** The bandit detects that Ask AI works well for the underlying immunology (Y1 strong) but produces poor Y3 (transfer) — the student knows the mechanism but cannot apply it to a clinical scenario. Bandit shifts toward Case Study for the application layer. Different signal per learning objective, different policy.
3. **Medical education — ECG interpretation.** Massive variance in baseline ability. Bandit's cold-start problem is acute: the first six sessions of ECG practice produce noisy signals. Mitigation: population-level priors from previous cohorts; conservative exploration; faculty override for early students who appear to be at risk of the bandit's mismatch. The chapter should describe this concretely as one of the honest limits.
4. **Pharmacy — interaction-recognition across drug classes.** Bandit notices a student who has mastered statin-drug interactions (high Y3) but is failing on antibiotic interactions (low Y3). Bandit's policy diverges by drug class: maintenance Quiz Me for statins, intensive Case Study for antibiotics. The bandit's per-student per-concept granularity matters here.
5. **Health sciences research methods — statistical reasoning.** The bandit notices a cohort-level pattern: students who started with Ask AI for confidence intervals show better Y6 (durable retention) than those who started with Quiz Me. The bandit updates its initialization policy for future students at this learning objective. This is the meta-loop: the bandit improving its own priors over cohorts.

---

## 4. The Book's Thesis Connection

This is the final chapter of Act Two — the chapter where the reader sees the three pieces (modes, signals, loop) integrated. The book's thesis becomes operational: Medhavy is not a smarter textbook; it is a measurement-and-adaptation layer; the contextual bandit *is* that layer.

The thesis-specific work:

1. **The loop in concrete terms.** Present (intervention chosen from evidence-based menu) → Measure (seven signals on that intervention's effect) → Adapt (bandit updates policy for this student-concept pair) → Repeat. The reader has now seen the present (Ch 3–5), the measure (Ch 6–7), and gets the adapt here. The integration is the chapter's argument.
2. **What "present differently" actually means.** TIKTOC is clear: not just different explanations, but different pedagogical approaches (Socratic vs. didactic, problem-first vs. concept-first, retrieval practice vs. generative assignment) — each with its own evidence base. The chapter must distinguish "cosmetic variation in wording" from "structurally different cognitive operations." The latter is what the bandit chooses among.
3. **The third condition for adoption.** TIKTOC's three-condition test: (1) present differently at scale, (2) need to know whether variation is helping, (3) willing to act on what measurement reveals. Chapter 9 carries the weight of condition (3). The institution must be willing to let an algorithm adjust per-student per-concept treatment based on signal evidence. Some institutions are not. The chapter should name this honestly.
4. **The honest limits.** Cold start is real. The first six sessions are exploratory; some students will get suboptimal interventions during this window. Faculty override is necessary. The reward signal (delayed retrieval at seven days) is a bet, not a proven specification. The bandit's policy is not transparent in the conventional sense — it is auditable but not deterministically explainable. Each of these is honest and must be on the page.

The chapter must not oversell. The bandit is not magic; it is a particular algorithm with known properties and known limits. The reader is being asked to invest in a measurement-and-adaptation infrastructure that will produce its value over months and years, not immediately. The TIKTOC worked example (eight weeks of one concept, bandit policy converging by week 8) is the right pacing argument.

The transfer to Act Three (Ch 9–11): once the reader understands the loop, they can ask whether their deployment needs it. Ch 9 is the answer to "do I?". Ch 8 is the answer to "what is it?".

---

## 5. The AI Wayback Machine — Candidate Figures

1. **Herbert Robbins (preferred — academic, lesser-known, foundational).** Columbia / UNC / Rutgers. His 1952 paper invented the multi-armed bandit as a sequential-design problem. Robbins is famous in statistics, essentially unknown outside it. Satisfies: lesser-known, foundational, academic. Example prompt: "You're Herbert Robbins, 1952. Explain to a curriculum director, in language she can use with her dean, what a 'multi-armed bandit' is and why it's the right way to think about choosing teaching interventions one student at a time."
2. **Susan Athey (contemporary, woman, accessible).** Stanford. Bandit / causal-inference researcher; deployed bandits in policy contexts (public-sector personalization). Satisfies: woman, lesser-known in education circles but extremely well-respected in statistics. Example prompt: "You're Susan Athey. A curriculum director wants to know what could go wrong with using a contextual bandit to choose interventions for students. What three failure modes would you warn her about?"
3. **Tze Leung Lai (non-Anglo, lesser-known outside statistics).** Stanford; Hong Kong-born. Foundational contributions to sequential analysis and adaptive design. Less famous than Robbins but his theoretical contributions are central to modern bandit theory. Satisfies: non-Western, lesser-known. Example prompt: "You're Tze Leung Lai. The chapter explains a contextual bandit applied to choosing pedagogical interventions per student. What does the math actually guarantee, and what doesn't it guarantee?"

**Diversity assessment:** Robbins (male, white, 1950s) is the strongest pedagogical choice — directly relevant, ideal "you've heard of bandits but not of him" framing. Athey (woman, contemporary, accessible) is the strongest diversity-and-relevance choice. Lai provides the non-Western option. Across the four chapters, the best combination is Hmelo-Silver (Ch 5, woman), Elizabeth Bjork (Ch 6, woman), Immordino-Yang (Ch 7, woman, non-Western heritage), and Robbins (Ch 8, foundational lesser-known). This meets both diversity criteria (multiple women, one non-Western) while maximizing pedagogical fit.

---

## 6. Pedagogical Delivery Research

Chapter 9 is the most technically demanding chapter for a non-technical reader. The risk is that "contextual bandit" sounds like a black box. Three pedagogical moves help:

- **The slot-machine analogy, used carefully.** Sutton & Barto's framing — a row of slot machines with unknown payouts; you have limited pulls; how do you balance trying new machines (explore) with playing the best one you've found (exploit)? — is the right entry point. But it must be made specific to learning: the "machines" are interventions; the "payouts" are learning signals; the "player" is the algorithm; the "pulls" are sessions with a student.
- **One concept, one student, eight weeks.** TIKTOC's worked example. This is the chapter's central pedagogical device. A timeline showing the bandit's policy evolving for one student-concept pair will do more than three pages of algorithmic description. The reader can see the loop close.
- **Resist explaining the algorithm.** The curriculum director does not need to understand UCB vs. Thompson sampling vs. LinUCB. They need to understand *what the algorithm is doing* (selecting among evidence-based interventions based on signal evidence) and *what it requires from the institution* (a stable concept map, an evidence library of interventions, willingness to act on policy outputs). The book should make the mechanism legible without making the math required.

The exercises shift the reader to their own deployment. Exercise 1 ("who currently performs the adapt function in your deployment?") is the chapter's most important exercise. The honest answer for most institutions: nobody systematically; instructors adjust based on exam results six weeks too late. Recognizing this gap is the foundation of the adoption case.

Pedagogical hazard to flag: the reader may conflate "contextual bandit" with "AI recommendation engine" and import all their concerns about social-media algorithms. The chapter must distinguish. The bandit's reward signal is *delayed learning outcomes*, not engagement. This is the architectural commitment that separates Medhavy from systems that optimize for clicks. Hammer this distinction.

---

## 7. Representation and Display Research

Per TIKTOC, the worked example is mandatory. The chapter's worked example is the eight-week single-concept bandit timeline. This warrants a multi-row temporal table:

**One Concept, One Student, Eight Weeks — Bandit Policy Evolution (Draft):**

| Week | What bandit sees | What bandit tried | Signals captured | Bandit policy update |
|---|---|---|---|---|
| 1 | New student, no data | Ask AI (uniform random init) | Y1 high, Y4 weak | Note Y4 weakness |
| 2 | Y4 still weak after Ask AI | Quiz Me | Y2 coherent (good), Y6 building | Try Quiz Me again |
| 3 | Y6 strong on factual recall | Quiz Me + Ask AI mix | Y3 not yet observable | Unlock Case Study |
| 4 | Case Study attempted | Case Study (first time) | Y3 emerging, Y7 strong response | Case Study weighted up |
| 5 | Two more Case Studies | Case Study + Quiz Me maintenance | Y3 high, Y6 high, Y4 improving | Pattern stabilizing |
| 6 | Stable signal profile | Case Study primary | All signals trending up | Policy converging |
| 7 | Glimmer eligibility check | First Glimmer attempt | Y5 specific confusions visible | Glimmer trial |
| 8 | Steady-state policy | 40% Case Study, 35% Quiz Me, 20% Glimmer, 5% Ask AI | All seven signals positive | Stable; faculty review GLP score |

**Second representation — the loop as a flow diagram.** Present → Measure → Adapt → Repeat as a four-node loop with the inputs labeled: interventions in (from the evidence library); signals in (from the seven Yn); policy out (per student per concept); learning outcome out (the goal). This is the chapter's defining image and should appear in the book.

**Third representation — comparing per-student policies.** Two students, same concept, different bandit policies after eight weeks. Student A: heavy on Case Study (had calibration trouble; needed reasoning practice). Student B: heavy on Quiz Me (had retention trouble; needed spaced retrieval). The bandit produced different treatment for different students. This is what "adapt" means concretely. Side-by-side bars or pie charts make the point.

**Fourth representation — what Canvas would see for the same eight weeks.** Engagement metrics indistinguishable. This closes the Ch 6 callback: the bandit was doing eight weeks of measurement and adaptation; Canvas's view was a flat engagement profile. The contrast image is the chapter's most powerful pedagogical artifact.

---

## 8. Open Questions and Research Gaps

**Flag heavily as proprietary:**

- **The reward signal specification.** TIKTOC names "delayed retrieval accuracy at seven days" as the reward in the chapter's third exercise. The actual operationalization in Medhavy is proprietary. The book commits to the framing; the implementation is internal.
- **The intervention library.** The exact set of "arms" the bandit chooses among (Socratic vs. didactic Ask AI variants; massed vs. spaced Quiz Me variants; case difficulty levels; Glimmer prompt classes) is Medhavy's. Outside literature does not specify this menu.
- **The cold-start mitigation.** The book promises "the first six sessions are exploratory" but the specific exploration policy is proprietary.
- **The bandit's specific algorithm.** Almost certainly LinUCB or Thompson sampling with neural-network contextual embeddings, but Medhavy has not published the specification. The book should treat this as an engineering choice, not a contested claim.

**Non-proprietary gaps:**

- **Delayed-outcome learning evidence at scale.** Most published bandit-in-education studies report immediate metrics. Medhavy's claim depends on durable learning gains. This is the most important empirical gap in the field, not specific to Medhavy.
- **Equity-of-adaptation evidence.** Whether adaptive systems entrench or reduce disadvantage is genuinely contested. Limited published evidence; mostly theoretical concerns. The chapter should name this honestly as a risk the institution adopts.
- **The "willing to act" condition.** TIKTOC's Open Question #3 names this explicitly. What does it actually take, organizationally, for an institution to act on what the loop reveals? The book has no published case studies of institutions that had the data and acted; nor of institutions that had it and did not. This is a research gap the book can flag.
- **Interpretability of bandit policies.** A faculty member can read the GLP dashboard (Ch 7) but the bandit's *why this student got Case Study this week* is harder to surface. Counterfactual explanations are a research area; not yet a deployed feature.

**Highest-priority gap (chapter and book):** A published, replicated demonstration of a per-student per-concept adaptive learning system improving *delayed* retention or transfer outcomes at semester scale. The Medhavy bet hangs on this; the broader field has not yet produced this evidence. The book's most honest framing: Medhavy is the most theoretically principled bet currently available; the evidence is still forthcoming. The reader should know they are an early adopter.

---

## 9. Sourcing Notes

**Lead with Sutton & Barto for the analogy, Robbins for the foundation, Li 2010 for the contextual extension, and Lan & Baraniuk 2016 for the education application.** That sequence is the citation backbone.

**The evidence-library framing** — that the bandit chooses among evidence-based interventions, not arbitrary content — is critical to defang the "AI deciding what my students see" objection. Cite Hattie (2009/2023), Dunlosky et al. (2013), and Pashler et al. (2008) for this. These are the names a curriculum director may have heard.

**Avoid math.** The chapter's tone is "trusted colleague explaining how the algorithm works in plain language," not "introduction to multi-armed bandits." If a curriculum director wants the math, point them at Sutton & Barto Chapter 2 in a footnote.

**Cross-chapter overlap:**
- **Ch 1:** The Bastani finding's lesson — what AI does depends on the wrapper — applies here. The bandit's reward signal is the wrapper's commitment.
- **Ch 4 (Quiz Me) and Ch 5 (Case Study):** The interventions the bandit selects among are the four modes detailed in Act One. Cross-reference.
- **Ch 6:** Canvas measures engagement; Medhavy's loop needs learning evidence. Direct callback.
- **Ch 7:** The seven signals are the bandit's reward signal. Direct setup; this chapter does not re-explain the signals, it uses them.
- **Ch 9:** "Willing to act on what the measurement reveals" — the third adoption condition. The chapter sets up the question that Ch 9 answers.
- **Ch 10:** What the institution must provide for the loop to operate — concept map, evidence library, faculty review. The chapter previews these requirements.

**Aging risk:** The bandit literature is decade-stable at the algorithm level. Specific Medhavy implementation choices may iterate. The book's commitment is to the architectural principle (measurement-driven, evidence-bounded, per-student per-concept adaptation), not to a specific algorithmic variant.

**Tone reminder per TIKTOC:** The reader is making a budget decision. The chapter must leave them able to say to a dean, in plain language: "What Medhavy does that Canvas can't: it presents content differently based on each student's learning signals, measures whether the change helped, and updates its approach — like a tutor who has perfect memory and infinite patience, running experiments per student per concept, with delayed learning outcomes as the success metric." That sentence is the chapter's transfer test.
