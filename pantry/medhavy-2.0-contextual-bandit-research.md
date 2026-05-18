# Contextual Bandits for Learning Mode Selection — Research Report
**Medhavy 2.0 Design Grounding**

---

## Executive summary

Medhavy 2.0 proposes a contextual bandit to select which of four learning modes — Ask AI, Quiz Me, Case Study, Glimmer — to surface to a student at the re-entry point after each session. This is not a novel idea: the research literature has been building toward exactly this application for over a decade, with the first production deployments appearing in 2019–2022. The evidence base is now sufficient to make confident design decisions on algorithm choice, feature vector construction, reward definition, and the cold-start problem. It is also sufficient to identify the failure modes that have sunk prior deployments and the design choices that avoided them.

The key findings are:

**On algorithm choice.** Thompson Sampling (TS) is the right baseline for Medhavy 2.0. It handles cold-start gracefully through its prior-based exploration, is more robust than LinUCB to noisy feedback and delayed rewards, and has the strongest theoretical guarantees in the educational setting. However, plain TS has a documented failure mode in small-cohort educational deployments: it under-explores in data-sparse conditions, converging too quickly on an apparently good arm before sufficient evidence has accumulated. The 2025 WAPTS algorithm (Song et al., 2025) addresses this directly and is the recommended implementation variant for Medhavy's typical course cohort sizes of 30–120 students.

**On reward definition.** The seven-day delayed retrieval accuracy signal proposed in the Medhavy 2.0 roadmap is theoretically correct — it directly measures what the platform is for — but creates a learning delay that will slow the bandit's convergence significantly, especially early in a course. The Impatient Bandit framework (Spotify / NeurIPS 2023; arXiv 2025) offers the right solution: combine the delayed ground-truth reward with shorter-term progressive signals (session completion, within-session performance, next-session Quiz Me accuracy) through a Bayesian filter. This lets the bandit learn from immediate signals while remaining anchored to the long-term outcome. Implementing this is the single most important design decision for 2.0.

**On feature vectors.** The Korbit/LinUCB deployment (Belfer et al., 2022) provides the closest published template to Medhavy's architecture and is the most useful empirical reference. Their feature vector — student performance on recent exercises, skip rate, video watch status, exercise difficulty, exercise type — maps almost directly onto Medhavy's available signals. The additions Medhavy should make are the FSRS Retrievability score (a better mastery signal than binary right/wrong history), the concept importance tier (which no prior system has had available), and Glimmer rubric history (a reasoning-quality signal with no analog in prior systems).

**On the cold-start problem.** Every published deployment reports cold-start as the dominant practical challenge. The standard solution — warm-starting the bandit from historical data before live deployment — is not available to Medhavy for new courses and new concept nodes. The recommended approach is a hierarchical prior: populate the prior from cross-student, cross-concept-node data as it accumulates across courses, so that a new student in a new course inherits the population-level prior rather than starting from uniform.

**On what the literature has not yet solved.** No published system has used a contextual bandit to select between qualitatively different learning mode types (retrieval practice vs. case study vs. generative assignment) for the same concept. All prior work selects between exercises of the same type — different problems, different difficulty levels, different orderings — within a single mode. Medhavy 2.0 is a genuinely novel deployment, not an application of a solved problem. The design can be well-grounded in the existing literature but cannot be validated against a prior comparable system.

---

## 1. What a contextual bandit is and why it is the right architecture

A multi-armed bandit (MAB) is a sequential decision-making framework where an agent chooses one of K actions (arms) at each timestep, observes a reward, and updates its policy to maximize cumulative reward over time. The tension between exploring uncertain arms (to gather information) and exploiting known good arms (to maximize immediate reward) is the core problem.

A *contextual* bandit extends this by making the arm selection depend on a feature vector describing the current state. Rather than asking "which arm is best on average?", it asks "which arm is best given what I know about this student and this concept right now?" This is the critical extension for education: the same mode that is optimal for a student with high Quiz Me accuracy and no Case Study history is not optimal for a student with low Quiz Me accuracy who has just submitted a Glimmer with a weak mechanism score.

The contextual bandit sits between full supervised learning (which requires labeled examples of optimal decisions) and full reinforcement learning (which requires a complete model of the environment and can plan ahead). For Medhavy, full RL is overkill — the action space is four arms, the state transitions are well-understood, and the reward signal is interpretable. The bandit is the right level of complexity.

The formal setup for Medhavy:

- **Arms** (K = 4): Ask AI, Quiz Me, Case Study, Glimmer
- **Context** (x): feature vector describing (student, concept node) pair at decision time
- **Reward** (r): a signal that measures learning quality following the selected mode
- **Policy** (π): a mapping from context to arm selection, updated from observed (context, arm, reward) triples
- **Objective**: maximize expected cumulative reward across all (student, concept) pairs over the course

---

## 2. Algorithm choice: Thompson Sampling vs. LinUCB

The two algorithms that dominate the educational bandit literature are LinUCB (Li et al., 2010, originally developed for news article recommendation) and Thompson Sampling (Thompson, 1933; Agrawal and Goyal, 2012). Both have been deployed in production educational systems. Their properties differ in ways that matter for Medhavy.

### LinUCB

LinUCB maintains a linear model of expected reward as a function of the context vector for each arm, with an upper confidence bound (UCB) added to the estimated reward to incentivize exploration. At each decision, it selects the arm with the highest UCB-adjusted expected reward. The theoretical regret bound is O(√T), meaning cumulative suboptimality grows no faster than the square root of the number of timesteps.

LinUCB was used by Korbit (Belfer et al., 2022) — the closest published deployment to Medhavy's architecture — and produced a 64% success rate in simulation versus 58% for random and 60% for a heuristic policy. In their RCT, LinUCB produced superior completion rates and student engagement compared to the heuristic baseline.

LinUCB's weakness for Medhavy is its sensitivity to noisy rewards and its behavior when the linear reward assumption is violated. Educational reward signals are noisy (a student's Quiz Me accuracy one week later is influenced by many factors beyond which mode they engaged with), and the relationship between context features and reward is unlikely to be linear across all four mode types simultaneously.

### Thompson Sampling

Thompson Sampling maintains a posterior distribution over the reward parameters for each arm and selects arms by sampling from these posteriors, naturally balancing exploration (arms with high uncertainty get selected proportionally to that uncertainty) and exploitation (arms with high mean reward get selected proportionally to that mean). It requires no explicit UCB tuning parameter.

The 2025 INFORMS paper on contextual Thompson Sampling for learner skill gain optimization (the mathematics tutoring platform deployment) used TS and found that it "recommends exercises associated with greater skill improvement and adapts effectively to differences across learners." Critically, TS is documented to be more robust than UCB-based methods to noisy feedback and delayed rewards — both of which are structural features of Medhavy's setting (Song et al., 2025; Chapelle and Li, 2011).

**Recommendation: Thompson Sampling as the base algorithm, with WAPTS modification for Medhavy's small-cohort setting.**

### The WAPTS modification for small cohorts

Standard Thompson Sampling has a documented failure mode in educational settings with small cohorts and many arms: it can converge to an apparently good arm before sufficient evidence has accumulated, particularly when one arm produces immediate positive signals (Quiz Me completion is easy to measure; Glimmer reasoning quality requires multi-round AI interrogation and is measured with delay). In a cohort of 30–120 students, this convergence-before-evidence problem is acute.

Song et al. (2025) introduced WAPTS specifically for educational platforms with exactly this problem. WAPTS modifies standard TS by introducing a dynamic weighting parameter that prevents under-exploration when sample sizes are small. It is guided by "lenient regret" — rather than insisting on finding the single best arm, it prioritizes reliably identifying a subset of high-performing arms. In Medhavy's terms: the goal is not to find the one best mode for every (student, concept) pair, but to reliably avoid offering clearly suboptimal modes.

WAPTS demonstrated earlier and more reliable identification of effective treatments compared to standard TS across cohort sizes of N=50, N=300, and N=1000. At N=50 — close to a typical Medhavy course cohort — standard TS showed substantially delayed convergence, while WAPTS reached reliable arm identification significantly faster.

One caveat documented in the WAPTS paper: in rare cases, WAPTS's deterministic re-weighting can downweight a truly optimal arm to near-zero probability after early negative outcomes, preventing recovery. The recommended safeguard — periodic forced exploration or allocation resets — should be built into the implementation.

---

## 3. The reward definition problem

This is the most consequential design decision in the entire bandit architecture, and it is the one most likely to be treated as an implementation detail rather than a product decision. It should not be.

### The fundamental tension

Medhavy's goal is durable retention. The cleanest possible reward signal is therefore: seven days after selecting mode M for concept C, offer a Quiz Me item on concept C and record accuracy. This is what the Medhavy 2.0 roadmap proposes, and it is theoretically correct.

The problem is that a seven-day delay between action and reward slows learning dramatically. A bandit that only updates from seven-day-delayed signals needs many more (student, concept) pairs to converge than one using immediate signals. In a fourteen-week course with 80 students and 40 concept nodes, the bandit sees at most 80 × 40 = 3,200 (student, concept, action, reward) triples — but only 3,200 / 7 ≈ 457 per week, and the delayed rewards for the first week only arrive in week two. The bandit is learning from approximately 457 observations per week with seven-day delays. Standard TS will converge slowly under these conditions.

### The Impatient Bandit solution

Spotify's research team (Maystre et al., NeurIPS 2023; arXiv updated 2025) developed the Impatient Bandit framework precisely for this problem, in the context of podcast recommendation where the long-term reward (user engagement over 60 days) is delayed but shorter-term signals are available progressively. Their solution has direct application to Medhavy.

The Impatient Bandit uses a Bayesian filter to combine:

1. **Progressive intermediate signals** — shorter-term outcomes observable before the delayed reward arrives
2. **The delayed ground-truth reward** — the long-term outcome the system is actually optimizing for

The Bayesian filter forms a probabilistic belief about the expected delayed reward based on all intermediate signals observed so far. Even if the first few intermediate signals are insufficient to perfectly infer the delayed reward, they can be sufficient to reveal that one arm is clearly outperformed by others — allowing the bandit to shift allocation away from that arm without waiting for the full reward.

The key theoretical quantity is the **Value of Progressive Feedback (VPF)**: an information-theoretic metric that captures how much information the short-term signals contain about the long-term reward. Higher VPF means the bandit can learn faster from progressive signals without sacrificing alignment with the long-term goal.

**The Medhavy progressive signal hierarchy.** For each mode, the following signals are available progressively before the seven-day delayed accuracy reward:

For Quiz Me:
- Session completion (immediate)
- Per-card accuracy within session (immediate)
- Card rating distribution (Again/Hard/Good/Easy) (immediate)
- Next-session FSRS Retrievability update (next session, typically 1-3 days)

For Case Study:
- Session duration >3 minutes (immediate)
- Assistance level reached (1-4) (within session)
- AI-assessed reasoning quality — poor/developing/proficient (within session)

For Glimmer:
- Draft submission (immediate)
- AI interrogation round count (within session)
- Revision quality — met threshold boolean (within 24-48 hours)

For Ask AI:
- Session duration (immediate)
- Number of turns (immediate)
- Question type — clarifying/probing/claim-making (immediate)

The VPF for Quiz Me signals is likely high — same-session card accuracy is strongly predictive of next-session retention. The VPF for Glimmer signals is likely moderate — draft submission and revision quality predict long-term concept mastery, but with more noise. The VPF for Case Study signals is the most uncertain and should be treated as an open empirical question for the first semester of 1.5 data.

**Implementation recommendation:** Implement progressive reward estimation from session-level signals, weighted by empirically estimated VPF for each mode, combined with the seven-day delayed accuracy signal as ground truth. Start with a simple linear Bayesian filter and upgrade to the full Impatient Bandit model once sufficient (student, concept, mode, signal) data has accumulated across multiple course cohorts.

---

## 4. Feature vector design

### What the Korbit deployment used

Belfer et al. (2022) used the following features in their LinUCB context vector:

- Student's performance on the previous exercise in the learning unit (right/wrong)
- Student's skip rate in the learning unit (fraction of exercises skipped)
- Whether the student watched the video covering the learning unit (binary)
- Exercise difficulty (historic success rate across all students)
- Exercise type (one-hot encoding of solution form and application context)

Their prediction model achieved 66% accuracy versus a 60% majority-class baseline — modest but sufficient for the bandit to outperform the heuristic policy. The lesson is that a feature vector does not need to be comprehensive to be useful; it needs to capture the dimensions most predictive of the reward signal.

### Medhavy's feature vector

Medhavy has access to substantially richer state information than Korbit, because the concept node map and the multi-mode signal layer produce a far more detailed student state representation. The recommended feature vector groups into four categories:

**Mastery and retrievability signals** (from Quiz Me):
- FSRS Retrievability (R) for the focal concept node — the predicted probability the student can recall the concept right now (0 to 1)
- FSRS Stability (S) for the focal concept node — the number of days at which R would fall to the target threshold; a proxy for how well-consolidated the concept is
- Prerequisite mastery score — mean R across all upstream concept nodes in the prerequisite graph
- Days since last Quiz Me session on this concept (log-transformed to handle long tails)
- Fraction of most recent Quiz Me session ratings that were "Again" or "Hard" (recency-weighted difficulty signal)

**Reasoning quality signals** (from Case Study and Glimmer):
- Most recent Case Study assistance level reached (1-4) on this concept — higher means the student needed more scaffolding
- Most recent Glimmer rubric score for mechanism dimension — the most reliably predictive rubric dimension for concept mastery
- Most recent Glimmer rubric score for specificity dimension
- Number of Glimmer submissions completed on this concept (0, 1, 2+)

**Engagement recency signals** (from all modes):
- Days since last Case Study session on this concept
- Days since last Glimmer submission on this concept
- Days since last Ask AI session on this concept
- Total Ask AI turns on this concept (log-transformed)

**Concept-level features** (from Tic TOC):
- Importance tier (encoded as 0/0.5/1 for low/medium/high)
- Frequency tier (encoded as 0/0.5/1)
- Prerequisite depth in the concept node graph (integer)
- Whether the concept node has a video (binary)
- Video watch completion rate for this student on this concept (0 to 1, or 0 if no video)

**Practical notes on this vector:**

Several features will be zero for new students or new concept nodes (cold-start). The recommended handling is hierarchical priors: populate uninformed features with population-level estimates from prior cohorts rather than zeros. A student with no Glimmer history on a concept inherits the population-level distribution of Glimmer outcomes for concepts with similar importance tier and prerequisite depth — not a zero, which the bandit would interpret as "this student has failed at Glimmer here."

Feature dimensionality should be kept at or below approximately 15-20 active features for the Thompson Sampling linear model to remain stable at Medhavy's cohort sizes. The full feature list above has approximately 18 features; this is at the upper end of what will be reliably estimable from a single course cohort and should be reduced if convergence is slow.

---

## 5. The cold-start problem

Cold-start appears in three forms in Medhavy, each requiring a different solution.

### New student cold-start

A student who has just joined the platform has no Quiz Me history, no Case Study history, no Glimmer submissions. Their feature vector is largely zero or uninformative. Standard TS will explore broadly, which is theoretically correct but may mean the first several weeks offer suboptimal mode selections.

**Recommended solution:** Start all new students in a fixed mode sequence for the first two weeks — Ask AI for the first session on any concept, Quiz Me for the second, Case Study for the third, Glimmer for the fourth — then hand off to the bandit. This gives the bandit initial observations across all four arms before it starts selecting, which is the warm-start the published literature consistently recommends.

### New concept node cold-start

A concept node that has never been encountered by any student has no prior reward data for any arm. Even a student with a rich history on other concept nodes provides no direct information about which mode works best for this specific concept.

**Recommended solution:** Hierarchical generalization from concept-level features. Concepts with similar importance tier, prerequisite depth, and content class (dynamic process vs. definitional vs. procedural) should have similar arm reward distributions. The bandit's prior for a new concept node should be populated from the empirical reward distributions of structurally similar concept nodes seen in prior cohorts, not from a uniform prior.

### New course cold-start

For the first cohort to use a new textbook or a new semester of an existing textbook, there is no prior data from which to populate priors. The bandit starts from scratch.

**Recommended solution:** The fixed two-week mode sequence described above, followed by WAPTS-modified Thompson Sampling with conservative exploration weights. Instructors should expect the first semester to be primarily a data-collection period for the bandit rather than an optimization period, and this expectation should be communicated explicitly.

---

## 6. The reward contamination problem

This is a failure mode not prominently discussed in the educational bandit literature but directly relevant to Medhavy's design.

The seven-day Quiz Me accuracy reward conflates two things: the effect of the mode selected at time T, and everything else that happened between time T and time T+7. A student who does Ask AI at time T, then does a Quiz Me session at T+2, then reads the chapter again at T+5, then takes the seven-day accuracy test at T+7 — the accuracy test reflects the cumulative effect of all three interventions, not just the Ask AI. The bandit attributes the reward to the selected arm (Ask AI) even though much of the effect came from subsequent actions.

This is the standard multi-step reward attribution problem in RL. In the bandit formulation — which assumes each arm's reward is immediate and independent of subsequent actions — it is technically a violation of the bandit's modeling assumptions.

**Practical mitigations:**

1. Define the reward window narrowly: measure accuracy at T+7 on a new Quiz Me item that has not appeared before. The novelty constraint ensures the accuracy reflects retention of the concept, not memory of the specific item.
2. Control for intervening Quiz Me sessions: the feature vector should include whether the student engaged with Quiz Me on the focal concept in the T to T+7 window, so the bandit can partially adjust for this confound in its reward model.
3. Accept the contamination and trust the average: across many (student, concept, mode) observations, the contamination should average out. Arms that produce better seven-day accuracy even with contamination are genuinely better. This is the pragmatic assumption that justifies the bandit formulation despite the technical violation.

The third approach is what the published literature implicitly uses. The first two are refinements worth implementing but not prerequisites for launch.

---

## 7. What the deep RL literature adds (and why Medhavy should not use it yet)

The 2023 machine learning paper on deep reinforcement learning for pedagogical support (Rowe et al., 2023/2024, *Machine Learning*) showed that a deep RL agent trained on student trajectories in a narrative math tutoring game produced a pedagogical policy that better supported lower-performing students than a hand-designed policy. The RL policy was more aggressive about using hints and scaffolding for struggling students and faster at removing scaffolding as performance improved — a pattern consistent with the expertise reversal effect from the cognitive science literature.

This is promising and relevant. Deep RL can learn pedagogical policies that no human designer would have specified from first principles, and it can do so from the same kind of signal data Medhavy is building.

**Why Medhavy 2.0 should not use deep RL.** Deep RL requires substantially more data than a contextual bandit to converge to a reliable policy. The cited paper used thousands of student trajectories in a controlled environment. Medhavy's initial cohorts will produce hundreds of trajectories, not thousands. Deep RL trained on insufficient data produces policies that are difficult to interpret, difficult to debug, and potentially harmful in ways that are not visible until they manifest in student outcomes. The contextual bandit is the right level of complexity for the current data volume. Deep RL is the natural upgrade path once Medhavy has accumulated multiple semesters of cross-cohort data — probably at 2.5 or 3.0, not 2.0.

---

## 8. Instructor transparency and human override

The published literature on educational bandits has largely ignored the instructor's role in the system. The Korbit deployment was "fully automated" — instructors were not shown the bandit's decisions and could not override them. This is appropriate for a MOOC with tens of thousands of students where instructor oversight is structurally impossible. It is not appropriate for a 30-to-120-student university course where the instructor has contextual knowledge about individual students that no feature vector captures.

The relevant principle from the broader human-AI interaction literature: algorithmic systems that make consequential decisions about individuals should include a human review layer, both for ethical reasons and for performance reasons — the instructor knows things the bandit cannot know from logged signals (a student is going through a personal crisis, a student has a learning disability that affects their Glimmer performance, a student is strategically sandbagging Quiz Me to avoid Case Study).

**Recommended design for Medhavy:**

1. The bandit's mode suggestion is visible to the instructor on the dashboard as a "suggested mode" per student per concept, updated weekly.
2. The instructor can override the bandit's suggestion for any student at any time, with a required reason (free text). Override data is logged and fed back into the bandit as a signal.
3. The instructor dashboard shows, per concept node, which modes the bandit has been offering and the resulting accuracy trends — a simple visualization that makes the bandit's behavior interpretable without requiring the instructor to understand Thompson Sampling.
4. The bandit's exploration policy slightly downweights arms the instructor has consistently overridden for a student, incorporating instructor judgment as a soft constraint rather than a hard one.

This design is consistent with the Tutor CoPilot research (Wang et al., 2024) showing that AI-augmented human judgment outperforms either alone — and with the Rowe et al. finding that RL-based tutors produced the largest gains for lower-performing students, precisely the students where instructor judgment is most valuable.

---

## 9. The equity concern

The RL-in-education literature has repeatedly documented that adaptive systems can amplify rather than reduce equity gaps if not carefully designed. The mechanism is straightforward: a bandit trained on historical data from high-performing students will develop a policy optimized for high performers. If the feature vector does not adequately capture the specific barriers faced by lower-performing students, the bandit will offer them the mode that works for students who look like them in the feature space — which may be the mode designed for students who already have strong prior knowledge.

The Rowe et al. (2023) finding is relevant here: their RL agent outperformed the hand-designed policy specifically for lower performers, suggesting that learned policies can be more sensitive to learner differences than human-designed defaults. But this requires the feature vector to include signals that differentiate lower-performing students in informative ways, not just aggregate accuracy.

Medhavy's recommended mitigations:

1. Include Quiz Me session rating distribution (Again/Hard fraction) rather than just accuracy — this captures struggle behavior that aggregate accuracy misses.
2. Log and monitor arm selection distribution by student performance quartile, and flag cases where the bandit has converged to a single arm for a student. A student who gets offered Quiz Me in 90% of sessions is not benefiting from the multi-mode architecture.
3. The mandatory 14-day floor for high-importance concept review (the aviation pedagogy principle from the 1.5 spec) applies regardless of bandit policy — this protects lower performers from the bandit skipping critical concepts because their performance profile suggests they "already know it."

---

## 10. The minimum viable bandit for 2.0 launch

Given the constraints — new platform, small cohorts, no prior data, four qualitatively distinct arms — the following is the minimum viable bandit for 2.0:

**Phase 1 (first semester of 2.0 deployment):**
- Two-week fixed mode sequence for all new students on all new concepts
- WAPTS-modified Thompson Sampling with a reduced feature vector (8-10 features: FSRS R, prerequisite mastery, days since each mode was last used, importance tier)
- Progressive reward: session-level completion and within-session accuracy as immediate signals, seven-day Quiz Me accuracy as delayed ground truth
- Instructor override visible in dashboard; override data logged
- No personalization to individual students yet — bandit operates at the concept-node level, finding the best population-level mode ordering for each concept

**Phase 2 (second semester, once ~3,000+ (student, concept, action, reward) triples exist):**
- Upgrade to full per-student contextual feature vector (15-18 features)
- Bayesian filter combining progressive and delayed rewards (Impatient Bandit implementation)
- Hierarchical prior across concept nodes within the same importance tier
- Per-student arm selection distribution monitoring for equity audit

**Phase 3 (once multiple semesters of cross-course data exist):**
- Cross-course hierarchical prior: new course cohorts inherit priors from prior cohorts on similar concept nodes
- Consider upgrade to deep RL if data volume justifies it (typically >10,000 student-concept trajectories)

---

## 11. Open questions the literature does not resolve

These are the questions Medhavy 2.0 will be the first to answer. They cannot be answered from the existing literature because no prior system has done what Medhavy is doing.

**Can a contextual bandit meaningfully distinguish between qualitatively different learning mode types?** All prior published bandits select between instances of the same mode type — different exercises, different difficulty levels, different orderings. Medhavy selects between fundamentally different cognitive operations. It is possible that the reward signal (seven-day Quiz Me accuracy) is too coarse to differentiate the downstream effects of Ask AI versus Glimmer on the same concept. The first semester of data will answer this.

**What is the Value of Progressive Feedback for each mode?** The Impatient Bandit framework requires empirical estimation of how well each mode's session-level signals predict the delayed reward. This cannot be assumed; it must be measured from 1.5 signal data before the bandit can use it reliably.

**How much does concept-level importance tier improve bandit performance?** No prior educational bandit has had access to professor-assigned importance tiers as context features. The theoretical argument for including them is strong (high-importance concepts should be treated differently regardless of FSRS predictions), but the empirical magnitude of the effect is unknown.

**Does the bandit's policy generalize across student populations?** A policy learned from one cohort of medical students may not generalize to a different cohort, a different institution, or a different textbook. The cross-cohort generalization question is structurally important for Medhavy's scalability and has no good answer from the existing literature.

---

## Key citations

Agrawal, Shipra, and Navin Goyal. 2012. "Analysis of Thompson Sampling for the Multi-Armed Bandit Problem." *COLT 2012*.

Belfer, Robert, Ekaterina Kochmar, and Iulian Vlad Serban. 2022. "Raising Student Completion Rates with Adaptive Curriculum and Contextual Bandits." *AIED 2022*. arXiv:2207.14003.

Chapelle, Olivier, and Lihong Li. 2011. "An Empirical Evaluation of Thompson Sampling." *NeurIPS 2011*.

Li, Lihong, Wei Chu, John Langford, and Robert E. Schapire. 2010. "A Contextual-Bandit Approach to Personalized News Article Recommendation." *WWW 2010*.

Maystre, Lucas, et al. 2023. "Optimizing Audio Recommendations for the Long-Term: A Reinforcement Learning Perspective." *KDD 2023.*

Russo, Daniel J., et al. 2020. "A Tutorial on Thompson Sampling." *Foundations and Trends in Machine Learning* 11(1): 1–96.

Rowe, Jonathan P., et al. 2023. "Reinforcement Learning Tutor Better Supported Lower Performers in a Math Task." *Machine Learning* (Springer). arXiv:2304.04933.

Song, Haochen, et al. 2025. "Adaptive Experiments Under Data Sparse Settings: Applications for Educational Platforms." arXiv:2501.03999.

Thompson, William R. 1933. "On the Likelihood That One Unknown Probability Exceeds Another in View of the Evidence of Two Samples." *Biometrika* 25(3/4): 285–294.

Wang, Rose E., et al. 2024. "Tutor CoPilot: A Human-AI Approach for Scaling Real-Time Expertise." arXiv:2410.03017.

Maystre, Lucas, et al. (Spotify Research). 2025. "Impatient Bandits: Optimizing for the Long-Term Without Delay." arXiv:2501.07761; earlier version arXiv:2307.09943 (NeurIPS 2023).
