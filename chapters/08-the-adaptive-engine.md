# Chapter 8 — The Adaptive Engine

*The math is two pages. Everything else is upstream of the math.*

---

You walk into a casino with 1,000 tokens. Five slot machines. You cannot tell from looking which one pays best. You can only find out by playing.

Every token you spend has two costs. The first is obvious — you spent a token, and you got back whatever the machine returned, which is usually less. The second cost is invisible at the time but rules everything: you spent a token on *that* machine rather than on a different one. If the machine you skipped is the one that pays best, every token you spend somewhere else is a token you cannot spend learning that.

This is the exploration-exploitation problem. It is one of the oldest problems in statistics, stated clearly by Herbert Robbins in 1952 in the *Bulletin of the American Mathematical Society*, though William Thompson had already solved a version of it in 1933 in *Biometrika* and the field did not notice for eighty years. The core tension is permanent: every time you play the machine you know is probably best, you are choosing not to learn something about the machines you are less sure about. Information has value. Using what you know has value. You cannot maximize both at once.

The simplest rule that actually works is called Thompson sampling. Instead of keeping a single estimate of each machine's expected payout, you keep a *distribution* — a probability cloud over what the payout probably is. At each pull, you draw a sample from each cloud and pick the machine with the highest sample. If a machine has been pulled many times and paid well, its cloud is tight and high. If a machine has been pulled twice and paid poorly, its cloud is wide and low — wide enough that a sample might still come out high, which means the machine gets another chance. After each pull, the cloud updates. The bad machine's cloud shrinks and shifts down. The good machine's cloud sharpens. You never stop exploring; you just explore in proportion to your uncertainty.

![Three panels showing the same five slot machines](images/08-the-adaptive-engine-fig-01.png)
*Figure 8.1 — Three panels showing the same five slot machines*

Now replace the slot machines with Ask AI, Case Study, Quiz Me, and Glimmer. Replace the tokens with a student's study sessions. Replace the payout with genuine learning. You have the adaptive engine. The math is identical. The architecture decisions — what counts as a payout, whose data the engine learns from, what the engine is categorically not allowed to maximize — are everything else.

---

## The casino owner watching the cameras

Before the architecture, a picture worth holding.

A casino owner sits in a back room watching the floor through a security camera. The camera shows him time on machine, repeat plays, return visits. What it does not show him is whether anyone is going home with money. He cannot see the wallets. He can only see the bodies.

If his only data is what the camera sees, and he optimizes his casino on what he can see, he will end up with a casino that is very good at keeping people in seats and very bad at paying out. Not because he is malicious. Because the camera is the measurement, and the optimization is faithful to the measurement. He may sincerely believe he is running a fair casino. The gradient does not care what he believes.

This is the failure mode EdTech platforms fall into, and it does not require anyone to behave badly. It requires only that the reward signal be engagement-shaped. Once the engine is pointed at session length, click-through rate, or return visits, the math will find every way those signals can be inflated that does not require genuine learning — and will use them. The Khanmigo IDK-IDK incident from Chapter 2 is this failure at the mode layer. The present chapter names it at the engine layer, where the optimization is happening.

Engagement features appear in the Medhavy engine's context vector — days since last session, total Ask AI turns on a concept, mode completion rate. These tell the engine what the student has tried. They are *inputs* to the decision, not *targets* of the decision. The difference between engagement-as-context and engagement-as-reward is the difference between a navigator who looks at the currents to know which way to steer and a navigator who optimizes for the strength of the current under the hull. Same measurement. Opposite architecture.

![Two-column diagram ](images/08-the-adaptive-engine-fig-02.png)
*Figure 8.2 — Two-column diagram *

The engine is allowed to optimize for one thing: the weighted composite of the seven GLP signals and a delayed retrieval probe administered seven days after each session. Not session length. Not return visits. Not student-reported satisfaction, which is an engagement signal wearing a different hat. The delayed retrieval probe is the most important single architectural commitment in the engine, because it is the one that forces the optimization target seven days into the future, past the point where engagement and learning come apart.

---

## What the engine is picking among

Four modes. Ask AI, Case Study, Quiz Me, Glimmer. Chapter 6 developed each one. For the bandit, they are four arms with different expected return profiles that depend on context.

The context vector is approximately eighteen features grouped into four families.

The first family is mastery and retrievability: the FSRS retrievability score for the concept (the predicted probability the student can recall it right now), the stability score (how quickly retrievability would fall to threshold), prerequisite mastery as a mean across upstream concepts in the prerequisite graph, and a recency-weighted difficulty signal from the last Quiz Me session. These tell the engine where the student is on the concept and how fast they are forgetting it.

The second family is reasoning quality: the most recent Case Study assistance level (higher means more scaffolding was needed, which is information about where the reasoning is loose), and the most recent Glimmer rubric scores — particularly the mechanism dimension, which from internal data is the most reliable predictor of whether conceptual understanding is present rather than borrowed. These tell the engine what the student can do with the concept, not just whether they can recall it.

The third family is engagement recency: days since last Case Study, days since last Glimmer, days since last Ask AI turn. Not as reward — as context. If the student has not done a Case Study in three weeks, that is a fact about their recent learning history, not a target variable.

The fourth family is concept-level features from the curriculum design layer: importance tier, frequency tier (how often the concept appears in downstream material), Bloom level, whether a video exists and at what completion rate. These are not about the learner; they are about the concept's place in the structure. The bandit needs both.

Eighteen features is at the upper end of what a Thompson-sampling linear model can reliably estimate at typical cohort sizes of 30–120 students. Korbit, the closest published deployment to Medhavy's architecture, used a five-feature vector and achieved 66% prediction accuracy against a 60% majority-class baseline — sufficient for the bandit to outperform a heuristic rule on learning outcomes. The number of features is not what makes the engine work. Capturing the dimensions most predictive of the reward is what makes the engine work.

| Feature name | What it tells the engine | Failure mode if used as reward instead of context |
| --- | --- | --- |
| four row groups (Mastery & Retrievability, Reasoning Quality, Engagement Recency, Concept-Level Features | It makes the underlying reasoning visible instead of implied. | The pattern becomes easy to misuse or overlook. |
| each with 4–5 rows. | A concrete checkpoint for applying the chapter concept. | The pattern becomes easy to misuse or overlook. |

---

## Within-learner, not cross-learner — and why it matters

Most adaptive platforms pool data across learners. The logic is sound: if two students with similar background, similar prior performance, and similar course history tend to respond similarly to the same mode, why not use one student's data to improve the engine's estimate for the other? Cross-learner generalization converges much faster. Every other learner's sessions contribute. The cold-start problem — the first few weeks when the engine has almost no data about this particular person — is much less severe.

The empirical question is whether the assumption that makes cross-learner pooling valid actually holds: that two students with similar observable features are similar enough in their learning paths that one's response to a mode is informative about the other's.

Yudelson, Koedinger and Gordon showed in 2013, using the ASSISTments dataset, that per-student initial-knowledge and learn-rate parameters substantially improved prediction over population parameters. Learners are not well-modeled by a shared mean on the dimensions that matter. If the population is heterogeneous along dimensions the platform cannot easily observe — background knowledge, anxiety responses to ambiguity, the specific misconceptions they brought from prior instruction — then cross-learner pooling transfers the population noise onto each individual. The engine becomes confident in a policy that is really about some other subgroup whose data dominated the pooled estimate.

Medhavy makes the opposite bet. Each student's bandit starts from a population-informed prior, but the posterior updates on that student's data alone. The within-learner discipline does not require the assumption that learners are similar.

The cost is real. Cold start is genuinely worse. Until the bandit has seen five to ten sessions per concept, its mode selection is close to random within the curriculum's constraints. The recommended palliative — used in the Korbit deployment — is a fixed two-week warm-up sequence in which every student encounters every mode at least once before the bandit takes primary control. Convergence is also slower through the end of the term. A student may finish a semester with the bandit still actively exploring on the less-frequent concepts.

This is not a bug concealed as a feature. It is the honest version of personalization: *we do not yet have enough data about you to be confident, and we will not pretend we do.* The alternative — a policy that has converged quickly on a cross-learner average and applies it with high confidence to every learner — may look more polished. What it actually is, for the students whose learning paths differ from the population mean, is a system that is confidently wrong.

The 2025 WAPTS modification of Thompson sampling is specifically designed for the small-cohort, slow-convergence case. It does not resolve the fundamental cold-start problem, but it reduces convergence time without reintroducing the cross-learner heterogeneity assumption. Hierarchical priors, informed by the population distribution but updated learner-specifically, are available as an additional palliative. The bet on within-learner optimization is bet #3 on the book's open-bets list. A six-month follow-up study showing that per-learner posteriors are too noisy at term's end to dominate the population prior would force the architecture to add cross-learner pooling back in.

---

## The reward function — and why it is the architecture

Here is what the engine actually optimizes.

Primary: delayed retrieval accuracy at seven days. A new Quiz Me item on the concept, offered seven days after the mode-decision session, scored by the student's accuracy on that item. This is the most direct measurable proxy for durable learning the platform has.

Secondary: the seven GLP components from Chapter 5 — temporal engagement pattern, error trajectory coherence, cross-context transfer, uncertainty calibration, social knowledge texture, retrieval strength decay, scaffolding response curve. These update faster than the seven-day probe and provide a denser signal, at the cost of being less direct. The initial weights on the GLP components come from the evidence base in Chapter 3: spaced retrieval has strong evidence from Roediger and Karpicke (2006) and Cepeda and colleagues (2006, 2008); case-based learning has moderate evidence under specific conditions; ill-structured generative assignments have evidence for transfer but documented anxiety failure modes for novices; Ask AI without guardrails has the Bastani 2025 PNAS finding as the cautionary data point — 17 percentage points lower on the post-practice exam for the unguarded condition versus no AI at all.

As deployment data accumulates, the weights update. The within-learner discipline means each learner's weights are partly idiosyncratic; the curriculum-level priors prevent the engine from collapsing onto noise during cold start. The Spotify Impatient Bandit framework, published at NeurIPS 2023, provides the filtering architecture: a Bayesian filter combines within-session progressive signals with the delayed probe, so the bandit can learn from fast signals while remaining anchored to the long-term reward. Medhavy 2.0 adopts this pattern.

The dangerous trap comes in three forms, and a builder who watches for only the first will get caught by the other two.

The first is *direct substitution*: the reward function literally is session length or click rate. This is the obvious failure. It is rarer in serious products because anyone who has thought about it knows to avoid it.

The second is *proxy drift*: the reward is nominally a learning signal but the implementation is engagement-shaped. Quiz completion rate sounds like learning. It becomes engagement once students figure out they can skip difficult items. Time on page reading an explanation sounds like learning. It becomes engagement when a student leaves the tab open while doing something else. The proxy was sensible when designed. It corroded under contact with student incentives.

The third is *signal contamination*: the reward function is well-designed but the measurement leaks engagement information. If the seven-day retrieval probe can be gamed — if students recognize the probe items and pattern-match without genuine retrieval — the engine will learn to produce those patterns upstream. The probe corrupts the reward. The reward corrupts the policy. The policy corrupts the probe.

![Three small loop diagrams, one per failure mode,](images/08-the-adaptive-engine-fig-03.png)
*Figure 8.3 — Three small loop diagrams, one per failure mode,*

The defense is architectural, not algorithmic.

Reward is composite, not single-signal. No single channel can be gamed without showing up as inconsistency across the seven GLP components. A Y1 (engagement) score climbing while Y3 (cross-context transfer) and Y6 (retrieval strength decay) flatten is a visible pattern.

Reward is measured downstream. The seven-day delay is the structural commitment that prevents within-session optimization. An engine that gets immediate feedback from within-session signals will converge on within-session behavior. The delay is uncomfortable. The alternative is worse.

Reward weights are audited. A platform whose engine drifts toward engagement is detectable in the weight history. The weights are not the engine's private state — they belong to whoever is responsible for the platform's pedagogical integrity. The chapter does not specify whether that is the platform team, the curriculum designers, or an external party. That is a governance question the field has not answered.

---

## What one student's six weeks looks like

Let me run through an illustrative trajectory — simulated numbers, real shape — so the loop is visible as a sequence rather than a structure.

A second-year medical student enters a six-week oncology deployment. The bandit's prior is population-level from the previous cohort. The two-week warm-up sequence runs first: Ask AI on new concepts, Quiz Me on recall, Case Study on application-level content, Glimmer deferred until foundational mastery is established. The bandit is observing.

By week two, the first update is clean. On factual concepts — drug class membership, mechanism type, common toxicities — Quiz Me produces consistent seven-day retrieval gains. Ask AI on the same factual concepts produces *no* seven-day gain. The student asks a question, receives a fluent answer, closes the tab, and seven days later cannot retrieve the content. The Y6 signal (retrieval strength decay) is definitive. The bandit shifts: Quiz Me weight rises sharply on factual concepts. Ask AI weight falls *for factual concepts* but stays high in a different cell — prerequisite clarification, where the student is using Ask AI to rescue an upstream concept whose retrievability has decayed below threshold before starting a Case Study. The engine has learned something the cross-learner literature would not surface: for this student, Ask AI is a prerequisite-rescue mode, not a new-concept mode. In aggregate, Ask AI's return on factual concepts is moderate. Per-learner, for this student, it splits cleanly.

By week four, Glimmer has been offered three times on Apply-level concepts. Two of the three sessions ended in abandonment within ten minutes. The Y7 signal (scaffolding response curve) is unambiguous: when offered a partial hint, the student's next attempt did not improve. That is the anxiety-failure signature for novice Glimmer users. The bandit reduces Glimmer weight for this student on Apply-level concepts where the prerequisite Case Study has not yet been completed. It does not zero Glimmer — the WAPTS modification keeps a floor of exploration probability. As mastery grows, the engine will re-test. *Reducing weight, not eliminating it,* is what keeps the engine honest about its own uncertainty.

By week six, concepts have advanced to the Apply level. Case Study is now producing both within-session Y3 gain and seven-day Y6 gain. The student's assistance level across four cases has dropped from level 3 (full prompts at every step) to level 1 (initial framing only). The composite reward has updated through both channels. Case Study allocation on application-level concepts rises to approximately 55%.

Six weeks. Forty-eight sessions. The bandit's posterior is no longer uniform, and it is not yet converged. The student finishes with a per-concept mode allocation that is statistically distinct from the population prior *and* from her own week-zero starting point. That is what within-learner adaptation produces. It is not magic. It is a small loop run honestly.

![Four stacked area charts, one per mode (Ask](images/08-the-adaptive-engine-fig-04.png)
*Figure 8.4 — Four stacked area charts, one per mode (Ask*

---

## What the engine cannot do without the layer upstream

The engine is downstream of the curriculum design layer in a way the chapter should be explicit about, because the failure mode is quiet and everything looks fine until it is not.

The bandit picks among modes. What it cannot do is decide what counts as a good outcome for a specific concept at a specific Bloom level. That is not a learning question. It is a design question. The mode-appropriateness flags — *Glimmer is appropriate here, not here* — are inputs to the engine, not outputs. The prerequisite graph is an input. The concept's importance tier, its Bloom level, its membership in the chapter's outcome hierarchy — all inputs. The bandit operates within a space the curriculum designer specified.

If the space is badly specified — if the prerequisite graph has gaps, if the Bloom-level assignments are ambiguous, if the mode-appropriateness flags are wrong — the engine will optimize faithfully within a broken structure. It will converge. The policy it converges on will be technically correct and pedagogically incoherent. The engine has no way to know this, because the structure is the input and the input is trusted.

This is why the curriculum design layer is not a detail. It is the layer that determines what the engine can possibly learn to do well. An adaptive engine operating inside a well-specified concept map and a well-designed reward function will find the best policy the system allows. An adaptive engine operating inside an inherited course syllabus — prerequisite assumptions never made explicit, Bloom levels never assigned, mode appropriateness never specified — will find the best policy the noise allows.

The casino analogy has a last turn. The best Thompson sampling in the world cannot help you if someone has quietly changed which machines pay out, and the casino you are in is not the one you were told about. The algorithm is correct. The problem is upstream.

---

## Exercises

### Exercise 8.1 — LLM exercise: Diagnose the reward function

Paste the following specification to an LLM and ask it to diagnose which failure mode the reward function represents — direct substitution, proxy drift, or signal contamination — and to propose a corrected specification.

*Specification:* An intelligent textbook for undergraduate computer science uses the following reward function: $R = 0.4 \cdot \text{(session completion rate)} + 0.4 \cdot \text{(within-session quiz accuracy)} + 0.2 \cdot \text{(seven-day retrieval)}$. After four weeks of deployment, students whose engine has converged on high-completion modes show declining cross-context transfer and retrieval strength decay over time, while their session-completion and within-session accuracy scores continue to climb.

Evaluate the LLM's diagnosis against the chapter's three failure modes. If the LLM proposes a corrected weight specification, evaluate whether the correction addresses the structural problem or only the surface symptom. What would you need to observe in the GLP signals over the following four weeks to know whether the correction worked?

### Exercise 8.2 — LLM exercise: The cross-learner vs. within-learner distinction

Ask an LLM to explain the difference between cross-learner generalization and within-learner optimization in an adaptive engine, and to identify which design choice is more appropriate for a short, high-stakes course (eight weeks, medical board preparation) versus a long, low-stakes course (a year-long undergraduate survey).

Evaluate the LLM's response against the chapter's framing. Does it correctly identify the convergence-rate cost of within-learner optimization? Does it correctly identify the heterogeneity assumption that cross-learner pooling buys? Write a paragraph naming the one thing the LLM got right and the one thing it missed.

### Exercise 8.3 — LLM exercise: Specify a context vector

Choose a learning domain you know well. Ask an LLM to specify a context vector for an adaptive engine in that domain — mastery signals, reasoning-quality signals, engagement-recency signals, concept-level features.

Audit the LLM's specification: for each feature it proposes, identify whether it is being proposed as context (an input to the decision) or as reward (a target of the optimization). If any features are engagement-shaped, note whether the LLM recognizes this and marks them appropriately as context-only. Write a paragraph on the single feature you would add that the LLM missed, and explain what it would tell the engine.
