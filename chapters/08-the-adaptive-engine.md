# Chapter 8: The Adaptive Engine

---

## Learning Objectives

By the end of this chapter, you will be able to:

1. **(Understand)** Explain what a contextual multi-armed bandit is, using the slot-machine framing, and translate that framing into the Medhavy mode-selection problem.
2. **(Analyze)** Distinguish between cross-learner generalization and within-learner optimization — and name the empirical assumption each one buys and pays for.
3. **(Apply)** Specify the reward signal for an intelligent textbook — which GLP components contribute, what the initial weights come from, and how the engine updates as deployment data accumulates.
4. **(Evaluate)** Diagnose whether an adaptive engine is optimizing for learning or drifting toward engagement, using three questions: what is the reward signal, who is generalization happening across, and where in the system is the engagement-vs-learning distinction enforced?
5. **(Analyze)** Identify the limits of the bandit framing — non-stationarity, coupled arms, delayed reward — and name what the textbook theory does *not* address.

**Prerequisites:** Chapters 5 (the measurement layer) and 6 (the four modes). The engine consumes what the measurement layer produces and selects among what the mode layer offers. If those two chapters are not solid, the engine will look like magic. It is not magic. It is a small loop with strong opinions about what it is allowed to optimize for.

**Where this fits:** This is the third architectural chapter and the last one focused on a single mechanism inside the platform. Chapter 8 turns to what the engine needs *upstream* — a curriculum specified well enough that the engine can tell a good outcome from a bad one. Chapter 9 turns to the substrate the modes operate on. Without this chapter, those two cannot make sense, because the engine is the place where the curriculum and the content meet the measurement.

---

## Where this fits the conductor frame

This chapter primarily serves the learner — the first of the three questions, in order — because the within-learner contextual bandit is the conductor's decision algorithm operating on this learner's evidence, not on a population average. The instructor's pedagogical vision and the organization's deployment constraints both pass through the engine, but what the engine produces is a sequence of instrument choices for one named person.

What this chapter specifies for the conductor is her decision algorithm at machine scale. The bandit is the conductor when the conductor cannot sit at every learner's elbow. The reward signal is where the conductor's values become formal — what counts as a payout, what does not, where the engagement-versus-learning distinction is enforced inside the code. The most dangerous term in the vocabulary, the chapter argues, is *reward signal*, precisely because it sounds technical and benign. The choice of reward is the architecture. Everything else is housekeeping.

The chapter runs the experiment by being explicit about what the engine is allowed to optimize for and what it is not. Engagement is excluded by construction; delayed retrieval and transfer are weighted heavily. This is a falsifiable commitment — a deployment that drifts toward session-length-optimization is a deployment that has failed the frame. The bandit's policy updates are themselves the experiment, run continuously, with the reward function published rather than hidden. Transparency about the optimization target is what distinguishes this conductor from one whose values are not interrogable.

---

## Five Slot Machines, 1,000 Tokens, No Way to Tell

You walk into a casino with 1,000 tokens. Five slot machines. You cannot tell from looking which one pays best. You can only find out by playing.

Every token you spend has two costs. The first is the obvious one — you spent a token, and you got back whatever the machine returned, which is usually less than a token. The second cost is invisible at the time but rules everything: you spent a token on *that* machine rather than on a different one. If the machine you skipped is the one that pays best, every token you spend somewhere else is a token you cannot spend learning that.

Now suppose you have a rule. Spend the first hundred tokens evenly across all five machines, watching the payouts. After the first hundred, pick the machine with the highest average payout so far, and spend the rest of your budget there.

This is a rule, and it produces a result, and the result is wrong in a way that does not show up until afterward. The first hundred tokens are not enough to know which machine is best. The averages are noisy. If machine 3 had a bad run in your first twenty pulls — through nothing but luck — you walked away from it, and you might have walked away from the best machine in the room. The rule paid for information up front and then stopped paying for information, even though information was still worth paying for.

Now suppose another rule. Always pick the machine with the highest average so far, but every now and then — say, one pull in twenty — pick a random machine instead. This is called ε-greedy ("epsilon-greedy"), where ε is the fraction of pulls you randomize. It is the simplest correct answer to the dilemma. It is also undiscriminating. Once you have strong evidence that machine 1 is bad, you still play it ε/5 of the time forever, because the rule does not distinguish "we are not sure about this machine" from "we are very sure this machine is bad."

A better rule, the one most introductory treatments land on, is UCB1 — *upper confidence bound*. At each pull, pick the machine whose average payout plus a bonus is highest. The bonus is large when the machine has been pulled a few times (we are not sure yet, so we add a generous margin) and small when the machine has been pulled many times (we have a tight estimate, so the margin shrinks). The math is in [Auer, Cesa-Bianchi & Fischer 2002](https://doi.org/10.1023/A:1013689704352). The discipline is in plain English: *spend more on machines you are uncertain about*. Uncertainty is information you have not yet collected. Pulling the machine collects it.

There is one more rule, older than UCB1 and in some ways simpler, that turns out to be the one the platform uses. You keep a distribution over what each machine's payout probably is — not a single number, a probability cloud. At each pull, you draw a sample from each cloud and pick the machine with the highest sample. If a machine has been pulled ten times and paid out well, its cloud is tight and high. If a machine has been pulled once and paid out badly, its cloud is wide and low — wide enough that a sample might come out high anyway, and that machine gets another chance. After the pull, the cloud updates. The bad-machine cloud shrinks and shifts downward. The good-machine cloud sharpens. The rule is called *Thompson sampling*. [William Thompson published it in 1933](https://www.jstor.org/stable/2332286) in *Biometrika*, two decades before [Herbert Robbins formalized the sequential-experiment problem in 1952](https://projecteuclid.org/journals/bulletin-of-the-american-mathematical-society/volume-58/issue-5/Some-aspects-of-the-sequential-design-of-experiments/bams/1183517370.full) in the *Bulletin of the American Mathematical Society*. The casino literature credits Robbins for the problem statement most modern theory is built on; Thompson's rule predates the problem and was rediscovered in the 2010s when people noticed it outperformed everything else in production deployments.

Now replace the slot machines with Ask AI, Case Study, Quiz Me, and Glimmer. Replace the tokens with a student's study sessions. Replace the payout with whatever the platform decides to call "genuine learning." You have the adaptive engine. The math is two pages. The architecture decisions — *what counts as a payout, what the engine generalizes across, what the engine is not allowed to learn* — are the rest of this chapter.

---

## What "Adaptive" Actually Has to Mean

Before the engine can do anything, we have to be precise about a small handful of words that are doing too much work in EdTech marketing.

**Adaptive.** In most platforms this means "the interface changes when the user does something." A quiz that gets harder when you answer right is adaptive in that loose sense. In the bandit sense, adaptive means something stricter: the *policy* — the mapping from learner state to next action — updates based on observed reward. The interface change is a consequence. The policy change is the thing.

**Personalized.** In vendor copy, personalization almost always means "the system has a user account and remembers what you did." That is account state. In the bandit sense, personalization means the policy applied to *this* user is statistically distinct from the policy applied to another user with the same nominal label. If two students with the same background, the same course, and the same prior performance get the same mode recommendations, the platform is not personalized. It is shared with named seats.

**AI tutoring.** This phrase has come to mean "an LLM responds to the student," which is a content-generation choice. The adaptive engine is the meta-question that sits one layer above it: given that the platform can do many things — generate, retrieve, scaffold, scenario — what does it do next, and why?

**Reward signal.** The most dangerous term in the vocabulary because it sounds technical and benign. Operationally, the reward signal is the function the engine *actively maximizes*. If reward is "session length," the engine learns to extend sessions. If reward is "click-through to next mode," it learns to make the next-mode offer attractive. If reward is "delayed retrieval accuracy at seven days," it learns to produce durable memory. **The choice of reward is the architecture.** Everything else is housekeeping.

**Bandit.** In the casino sense, a one-armed mechanical device that pays out probabilistically. In the algorithmic sense, a stateless decision rule that selects an action and receives a reward. *Contextual* bandit extends this to actions that depend on observable context — Sutton & Barto's famous "what if the payout depended on wind speed?" framing in [Chapter 2 of their textbook](http://incompleteideas.net/book/the-book-2nd.html). The terminology is borrowed. The engineering is precise.

By the end of this section the reader should be able to say: *the adaptive engine is a contextual bandit whose arms are modes, whose context is a learner-state feature vector, and whose reward is a measurable learning signal — not engagement, not satisfaction, not session length.* Hold that sentence. The rest of the chapter unpacks it and then makes it harder.

---

## The Translation — From Slot Machines to Modes

Line by line, the casino picture becomes the Medhavy engine.

**Five slot machines become four modes.** Ask AI, Case Study, Quiz Me, Glimmer. The choice space is small and pedagogically motivated. Chapter 6 made the case for each one and named the failure mode each one runs into when used in isolation. The bandit's job is not to find one universal best mode — there is no such thing — but to figure out, for *this* learner at *this* point in *this* concept, which mode is most likely to produce learning right now.

**1,000 tokens become study sessions.** This matters more than it looks. A medical student preparing for boards has a real budget — calendar weeks, hours per evening, alertness windows after clinical rotations. Every Glimmer session the engine offers that fails to produce learning is time the student did not spend on a Quiz Me round that might have worked. Exploration in the casino costs tokens; exploration in the engine costs *the learner's remaining time before the test*. The chapter should not pretend this is cheap.

**Payout becomes the learning signal.** This is where the analogy strains hardest, and where I want to be honest about three places it breaks.

*The casino's payouts are stationary; learning is not.* A slot machine's expected value is the same on pull 1 and pull 1,000. A learner's expected return from Quiz Me changes as their [FSRS](https://github.com/open-spaced-repetition/fsrs4anki) retrievability on a concept matures. The bandit Medhavy needs is technically a *non-stationary* contextual bandit, which is harder than the textbook case.

*The casino's arms are independent; the modes are coupled.* Pulling slot 3 tells you nothing about slot 4. But a Glimmer session changes the learner's representation, which changes the expected return from a Quiz Me on the same concept, which changes the expected return from a Case Study afterward. The arms feed each other. The cleanest formal frame for that is a Markov decision process where the arms are actions and learner state is the state — which is full reinforcement learning, not the bandit subset. The honest engineering position is *the bandit is a useful simplification, not the complete model*.

*The casino's payout is the money in your pocket. The platform's payout is an estimate of an estimate.* The casino pays out on the pull — coins or no coins. The engine cannot read genuine learning off the screen. It reconstructs learning from the seven GLP components (Chapter 5) plus a delayed retrieval probe seven days later. The latency between action and reward is the bandit's hardest engineering problem, and estimation error in GLP becomes policy error in the bandit. We will come back to this; it is bet #6 in the open-bets list.

So: the engine is a non-stationary contextual bandit with coupled arms and delayed, noisy rewards. The textbook says "bandit." The reality is more demanding. Naming the gap is part of the discipline.

---

## Wind Speed Becomes Learner State — The Context Vector

The Sutton & Barto presentation of the contextual bandit asks a small question that turns out to do all the work: *what if the payout depended on the wind speed?* In the casino, this is metaphor — the wind makes the machines pay out differently. In Medhavy, the wind is the learner.

The bandit is not picking the best mode in the abstract. It is picking the best mode *given the wind*. And the wind is a vector, not a scalar.

The context vector for Medhavy 2.0, drawn from the platform's [feature roadmap](#) and the broader bandit-in-education literature, groups into four families:

**Mastery and retrievability signals.** The FSRS retrievability score for the concept — the predicted probability the student can recall it right now. The FSRS stability — how many days from now retrievability would fall to threshold. Prerequisite mastery — the mean retrievability across upstream concepts in the prerequisite graph. Days since the last Quiz Me on this concept, log-transformed because that distribution has long tails. The fraction of the last session's card ratings that were "Again" or "Hard" — a recency-weighted difficulty signal.

**Reasoning quality signals.** The most recent Case Study assistance level reached on this concept — higher means the student needed more scaffolding, which is information about where their reasoning is loose. The most recent Glimmer rubric scores — particularly the mechanism dimension, which from internal data appears to be the most reliable predictor of conceptual mastery. The number of completed Glimmer submissions on this concept (zero, one, two-plus).

**Engagement recency.** Days since last Case Study on this concept. Days since last Glimmer submission. Days since last Ask AI turn. Total Ask AI turns on this concept, log-transformed. These are not engagement-as-reward — using them as reward would invite exactly the trap Section E warns about — they are engagement-as-context, which tells the engine *what the student has tried* without telling the engine *to make the student try more*.

**Concept-level features.** Importance tier (low, medium, high) from the curriculum design layer. Frequency tier — how often the concept comes up in downstream material. Prerequisite depth in the concept graph. Whether the concept has a video. The student's completion rate on that video, if it exists.

The total is approximately eighteen features, which is at the upper end of what a Thompson-sampling linear model can reliably estimate at typical Medhavy course-cohort sizes of 30–120 students. If convergence is slow, the recommended cut is to reduce dimensionality first, before tuning algorithmic parameters. Korbit, the closest published deployment to Medhavy's architecture, used [a five-feature vector and achieved 66% prediction accuracy against a 60% majority-class baseline](https://www.semanticscholar.org/paper/Korbit%3A-Personalized-Pedagogy-At-Scale-Belfer-Mello/), which was sufficient for the bandit to outperform a heuristic policy on student outcomes. Comprehensive feature vectors are not what makes the engine work. Capturing the dimensions most predictive of reward is what makes the engine work.

The "wind speed" framing is the move worth holding: **the engine does not pick the best mode in the abstract; it picks the best mode given the wind**. And the wind blows differently for different students on different concepts at different times.

---

## Within-Learner, Not Cross-Learner — The Consequential Decision

Here is the engineering decision the rest of this book is downstream of. Most adaptive platforms — ASSISTments, Carnegie Learning, the bulk of the published intelligent tutoring system literature — learn *across* learners. Their bandits, regression models, or knowledge-tracing systems pool data across the student population. The implicit assumption is that two students with similar context features have similar expected reward distributions. If the assumption holds, cross-learner pooling converges much faster than within-learner — every other learner's data contributes to the policy applied to this learner.

The empirical question is whether the assumption holds.

The cleanest evidence comes from individualized Bayesian knowledge tracing. [Yudelson, Koedinger and Gordon (2013)](https://link.springer.com/chapter/10.1007/978-3-642-39112-5_18) showed that per-student initial-knowledge and learn-rate parameters substantially improved prediction over population parameters in the ASSISTments dataset. That is direct evidence that learners are *not* well-modeled by a shared population mean — at least on the dimensions BKT measures. If the population is heterogeneous along dimensions the platform cannot easily observe — background knowledge, motivation, comprehension speed, anxiety responses to ambiguity — cross-learner pooling *transfers the noise from the population mean onto each individual*. The bandit's confidence becomes false confidence. The engine pretends to know more than it does. Worse, it pretends to know things about *this* learner that are really things about some other subgroup whose data dominated the mean.

Medhavy makes the opposite bet. The engine learns per-learner. Each student's bandit starts from a population-informed prior — we are not throwing out everything we have learned from prior cohorts — but the posterior updates on this learner's data alone. The within-learner discipline does not require the assumption that learners are similar. It pays for that with a slower convergence rate.

The cost is real, and the chapter should not soften it.

*Cold start.* Until the bandit has seen five to ten sessions, its mode selection is essentially random within the curriculum's mode-appropriateness constraints. The early weeks may feel disorganized to the learner. The recommended palliative — used in the Korbit deployment and proposed in the Medhavy 2.0 roadmap — is a fixed two-week warm-up sequence in which every student gets every mode at least once before the bandit takes over.

*Convergence rate.* Within-learner convergence requires more total sessions than cross-learner. A student using the platform for a single semester may end the term with the bandit still actively exploring. This is uncomfortable. It is also honest: the alternative is to pretend the per-learner adaptation has converged when it has not, which is exactly the failure mode the within-learner design exists to prevent.

*Sample-efficiency hacks remain available.* Hierarchical priors — informed by the population distribution but updated learner-specifically. Transfer from named-similar learners, where the similarity is marked by explicit curriculum tags rather than implicit in a shared population mean. Domain priors from the evidence base on which modes work for which Bloom's levels (Chapter 6). The 2025 [WAPTS modification of Thompson sampling](https://arxiv.org/abs/2503.21908) is specifically designed for the small-cohort, slow-convergence case the platform faces. These reduce cold-start cost without recovering the heterogeneity assumption.

Within-learner is the right choice when the platform is high-stakes enough that incorrect personalization is costly, when the population is heterogeneous enough that pooled estimates would be statistically dominated by the wrong subgroup, and when sessions accumulate over months rather than days. Cross-learner is the right choice when sessions are short and high-volume, the learner population is narrow, and the cost of incorrect adaptation is small. **Medhavy is built for the first case. It pays for the second case's speed by giving it up.**

This is bet #3 on the eight-open-bets list (Chapter 11). The chapter should say so plainly: *we are betting that the convergence cost is worth paying for personalization that does not depend on the heterogeneity assumption*. If the bet is wrong, we will see it in the deployment data and the architecture will have to change.

---

## The Reward Function — and the Casino Owner Watching

Now the consequential paragraph.

The state space the engine optimizes over is (mode × concept × time). Each cell is a tuple of (learner, mode, concept, session window) whose reward the engine estimates from the GLP signals and a delayed retrieval probe. The reward function is a weighted combination of (a) a primary delayed-retrieval signal, (b) the seven GLP components from Chapter 5, and (c) some lighter-weight progressive signals that arrive within or shortly after the session.

The primary reward is delayed retrieval accuracy at seven days. A new Quiz Me item on the concept, offered seven days after the mode-decision session, scored by the learner's accuracy on that item. This is the most direct measurable proxy for durable learning the platform has. The composite GLP signal — Y1 temporal engagement pattern, Y2 error trajectory coherence, Y3 cross-context transfer, Y4 uncertainty calibration, Y5 social knowledge texture, Y6 retrieval strength decay, Y7 scaffolding response curve — provides a denser and faster-updating signal that is less direct but more frequent. The initial weights come from the evidence base in Chapter 3: spaced retrieval has strong evidence (Roediger & Karpicke 2006; Cepeda 2006/2008); CBL has moderate evidence under specific conditions ([Thistlethwaite 2012](https://doi.org/10.3109/0142159X.2012.680939)); Glimmer-style ill-structured problems have evidence for transfer but anxiety failure modes for novices ([Jonassen 1997](https://doi.org/10.1007/BF02299613); Fiorella & Mayer 2016); Ask AI has the [Bastani PNAS 2025 finding](https://doi.org/10.1073/pnas.2422633122) as the cautionary data point — the wrong guardrail produces 17 percentage points lower performance on the post-practice exam for the GPT-Base group versus the no-AI control. As the platform accumulates session data, the weights update. The within-learner discipline means each learner's weights are partly idiosyncratic; the curriculum-level priors keep the engine from collapsing onto noise during cold start.

That is the architecture, in the abstract. Here is what can go wrong.

Picture a casino owner in a back room watching the floor through a security camera. The camera shows him time on machine, repeat plays, return visits. What it does not show him is whether anyone is going home with money. He cannot see the wallets. He can only see the bodies in front of the machines. If his only data is what the camera sees, and he optimizes his casino on what he can see, he will end up with a casino that is very good at keeping people in seats and very bad at paying out — because he never measured the payout. He measured the proxy that *correlates* with payout in the easy case and *anti-correlates* with it in the hard case, and the math of his optimization will exploit exactly the anti-correlation.

Now look at the platform. Any engine that uses session-derived signals as reward — time on platform, click-through rate, return rate, self-reported satisfaction — *and learns to maximize them* will converge to engagement-maximizing behavior regardless of whether the operators want it to. The math does what the math is told. The operators may believe they are optimizing learning. The gradient is computed on engagement. This is structurally the same failure mode as the [recommender systems that produce social media addiction](https://www.sciencedirect.com/science/article/abs/pii/S0747563220304040). The platform is not malicious. The loss function is. Cross-reference the Khanmigo IDK-IDK incident from Chapter 1 — that was this failure mode at the mode layer; this section names it at the engine layer.

It appears three different ways in adaptive engines, and a builder who only watches for one will get caught by another.

**Direct substitution.** The reward function literally is session length or click rate. The platform builders chose engagement as the metric. This is the obvious failure. It is rarer in serious products than the other two because builders know to avoid the obvious.

**Proxy drift.** The reward function is nominally a learning signal but the implementation is engagement-shaped. "Quiz completion rate" sounds like learning. It becomes engagement once a learner figures out they can skip difficult items. "Time on page reading the explanation" sounds like learning. It becomes engagement when a learner gets distracted and leaves the tab open. Proxy drift is what happens when a sensible signal collides with a learner's actual incentives.

**Signal contamination.** The reward function is well-designed but the *measurement* of the signal leaks engagement information. If the seven-day retrieval probe is presented in a way that lets engagement-style responses — quick guessing, picking the first option — look like high accuracy, the engine will learn to produce those responses upstream. The probe corrupts the reward, and the reward corrupts the policy, and the policy corrupts the probe.

The defense is not algorithmic. It is architectural.

*Reward is composite, not single-signal.* The seven Y-components and the delayed probe together. No single channel can be gamed without showing up as inconsistency across channels — a Y1 (engagement) score climbing while Y3 (transfer) and Y6 (retrieval decay) flatten is a visible pattern, not a hidden one.

*Reward is measured downstream, not within-session.* The seven-day delay is the most important architectural commitment in the engine. An engine that gets immediate feedback from within-session signals will converge on within-session behavior. The Spotify research team published the [Impatient Bandit framework](https://research.atspotify.com/2023/12/impatient-bandits-optimizing-for-the-long-term-without-delay/) at NeurIPS 2023 to address exactly this — a Bayesian filter that combines short-term progressive signals with the delayed ground-truth reward, so the bandit can learn from immediate signals while remaining anchored to the long-term outcome. Medhavy 2.0 adopts this pattern. The progressive signals update the bandit fast. The seven-day probe is the anchor that keeps the fast updates from drifting.

*Reward weights are audited.* A platform whose adaptive engine drifts is detectable by *looking at the weight history*. The weights are not the engine's private state. They are part of the deployment discipline, like a financial audit, and they belong to whoever is responsible for the platform's pedagogical integrity. The chapter does not specify whether that is the platform team, the curriculum design team, or an external party. That is a governance question, raised here and left open for the field.

The casino owner watching through the security camera is the central image of this chapter. It is uncomfortable on purpose. The architecture of the engine is built to keep the camera from being the only thing that decides what gets optimized.

---

## The Eight Open Bets — and Why Bet #6 Lives Here

The book has been honest from the first chapter that several of its load-bearing design decisions are bets. Not guesses; bets. Each one is supported by adjacent evidence and falsifiable by a specific kind of deployment study. Chapter 11 enumerates all eight. The chapter on the adaptive engine is where one of them — the right reward function weights — lives most visibly.

The eight bets, in the order the architecture surfaces them:

1. Does context-anchoring (RAG to the current section and prerequisites) alone convert GPT-Base failure to GPT-Tutor success? (Ask AI; Chapter 6.)
2. Does pre-written, faculty-reviewed CBL produce reasoning gains comparable to group human-facilitated CBL when used solo and asynchronously? (Case Study; Chapter 6.)
3. Does FSRS-style scheduling, developed for declarative recall, generalize to conceptual material? (Quiz Me; Chapter 6.)
4. Is the Quiz Me habit loop driven by the due-count UI or by the underlying scheduling algorithm? (Quiz Me habit; Chapter 6.)
5. Does backwards-faded scaffolding prevent the anxiety collapse in novice Glimmer users? (Glimmer; Chapter 6.)
6. **Does priority-weighted scheduling outperform recall-only scheduling — and what reward-function weights produce the best per-learner outcomes?** (The bandit's reward weights, including the within-learner convergence-rate question. This chapter.)
7. Does Level-3 domain specificity outperform Level-1 generic instruction enough to justify the production cost? (Content; Chapter 9.)
8. Does AI-generated educational content produce durable learning outcomes comparable to professionally produced content? (Content; Chapter 9.)

Bet #6 is the engine's central uncertainty. The weights in the reward function are informed by the evidence base. They are not derived from it. There is no published RCT that delivers the right weights for a four-mode adaptive engine on a multi-week medical-education deployment, because there is no prior four-mode adaptive engine to derive them from. The platform's first deployments are the experiment that will produce the weights. The discipline is to write the initial weights down, to deploy with them, to measure GLP and seven-day retrieval, and to update the weights from the deployment data — and to make the weight history publicly auditable, so that the field can see whether the weights are drifting toward engagement.

This is the honest version of "we are personalizing learning." Not *we know the right weights and we apply them*. But *we have written the weights down, we know they are not yet right, and the platform is built to learn them while showing its work*.

---

## Worked Example — Six Weeks of Oncology

A medical student, second year, taking an oncology rotation that runs across six weeks of Medhavy sessions. The engine is in its 2.0 form. The seven GLP components are instrumented. The bandit is Thompson-sampling with WAPTS modification, hierarchical prior populated from the prior cohort's data on the same concept set. The reward function combines progressive within-session signals with the seven-day delayed retrieval probe, weighted by the [Impatient Bandit](https://research.atspotify.com/2023/12/impatient-bandits-optimizing-for-the-long-term-without-delay/) Bayesian filter.

What follows is a simulated trajectory. The numbers are illustrative. The shape of the trajectory is the point.

**Week 0 — Cold start.** The student has just been enrolled. The bandit's posterior over (mode | concept | learner) is the platform-level prior: roughly Ask AI 25%, Quiz Me 25%, Case Study 25%, Glimmer 25%, with curriculum-design-layer flags excluding Glimmer for the foundational pharmacology concepts (drug classes, mechanism types) where the Bloom level is Remember or Understand. The student is offered Ask AI first on each new concept, Quiz Me second, Case Study third per the two-week warm-up sequence. The bandit is watching, not yet deciding.

**Week 2 — First update.** The student has done eight sessions across four oncology concepts. On factual concepts — *drug class membership*, *mechanism type*, *common toxicities* — Quiz Me has produced consistent seven-day retrieval gains. Ask AI has produced *no* seven-day retrieval gain on the same factual concepts. The student asks Ask AI a question, gets a fluent answer, closes the tab, and seven days later cannot retrieve the content. The Y6 component (retrieval strength decay) is clean on this: Ask AI sessions on factual concepts produce within-session understanding that does not consolidate. The posterior shifts. Quiz Me weight rises sharply on factual concepts for this learner. Ask AI weight falls *for factual concepts* but remains high in another posterior cell — *prerequisite clarification*, where the student is using Ask AI not to learn the focal concept but to refresh an upstream concept whose mastery has decayed. The engine has learned that for this learner, Ask AI is a *prerequisite-rescue* mode, not a *new-concept* mode. This is the kind of distinction the cross-learner literature does not surface, because the average student's Ask-AI return is moderate across both contexts.

**Week 4 — Glimmer abandonment.** Glimmer has been offered three times — for concepts at the Apply level: predicting drug-drug interactions, designing a chemo regimen for a comorbid patient. Two of the three Glimmer sessions ended in within-ten-minute abandonment. The Y7 component (scaffolding response curve) tells the story cleanly: when offered a partial hint, the student's next attempt did *not* improve, which is the anxiety-failure signature for novice Glimmer users that the Chapter 6 evidence base predicts. The bandit reduces Glimmer weight for this learner *on Apply-level concepts where the prerequisite Case Study has not yet been completed*. It does not zero Glimmer — the WAPTS modification keeps a floor of exploration probability so that as the student's mastery grows, the engine can re-test whether Glimmer becomes productive. This is the kind of restraint a fixed rule does not have. *Reducing weight, not eliminating it,* is what keeps the engine honest about its own uncertainty.

**Week 6 — Case Study allocation rises.** Concepts have advanced from Understand-level to Apply-level — *managing chemotherapy in a patient with renal impairment*, *adjusting a regimen when a patient develops neutropenia*. On these application-level concepts, Case Study has produced both within-session Y3 (cross-context transfer) and seven-day Y6 gain. The student's case-study assistance level has been dropping over the four cases — from level 3 (full prompts at every step) to level 1 (initial framing only). The reward function update runs through both channels: the within-session progressive signals (assistance level falling, mechanism dimension of the Glimmer-style sub-rubrics rising) and the seven-day probe (the student retrieves the previous case's reasoning correctly when given a structurally similar new case). Case Study allocation rises to roughly 55% on application-level concepts for this learner.

The fourth concept-mode-time cell — Ask AI for *clarification of upstream prerequisites during a case study* — has also risen, but coupled to Case Study, not as a standalone arm. The bandit has learned that for this learner, the productive Ask AI session is the one embedded inside a Case Study workflow, not the one in isolation.

Six weeks. Forty-eight sessions. Two hundred-odd GLP component scores. Seven seven-day retrieval probes per concept. The bandit's posterior is no longer uniform. It is also not yet converged. The student finishes the rotation with a per-concept mode allocation that is statistically distinct from the population mean *and* from her own week-0 prior. That is what within-learner adaptation produces. It is not a magic outcome. It is what falls out of a small loop run honestly.

Three things to note. *The bandit never optimized for engagement.* Engagement-recency features entered as context — *the student has not used Glimmer in 14 days* — not as reward. The bandit's only reward signal was the composite GLP and the delayed retrieval probe. *The bandit did not converge.* By week 6 the posterior was still actively exploring, particularly on the long tail of less-frequent concepts the student saw only once or twice. *The bandit found a distinction the cross-learner literature would have missed.* The Ask-AI-as-prerequisite-rescue cell is not present in any aggregated cross-learner policy, because in aggregate, Ask AI's return on factual concepts is moderate. Per-learner, for this learner, the return splits cleanly.

---

## Common Misconceptions

**"The bandit learns what works."**

It learns what is rewarded. Those are the same thing only when the reward function tracks what works. If the reward function is wrong — if it weights engagement signals too heavily, if the delayed retrieval probe is gameable, if the GLP weights are miscalibrated — the bandit will converge confidently on the wrong policy. The bandit is a faithful optimizer of whatever you feed it. The architecture choice is upstream of the algorithm.

**"More data fixes a bad reward signal."**

It does not. More data with a bad reward signal converges harder onto the bad policy. The casino owner with a billion hours of security camera footage does not learn whether anyone went home with money. He learns, with great statistical confidence, exactly what makes people sit at machines longer. Reward signal precision dominates data quantity. If you have a choice between a clean reward signal at modest scale and a noisy reward signal at massive scale, the clean signal at modest scale wins.

**"Personalization means the system knows what the student wants."**

In Medhavy, personalization means the system has *evidence about what produces learning for this student* and is allowed to act on that evidence. Wants and produces-learning are not the same thing. The bandit deliberately does not optimize for student-stated preference because student-stated preference is an engagement signal under another name. The platform is opinionated about this. Chapter 1 established why.

**"The bandit replaces the curriculum designer."**

It does not. The bandit is a policy over a constrained action space. The curriculum designer constrains the action space (mode-appropriateness flags, prerequisite graph, Bloom-level assignments) — Chapter 8 unpacks how. Without the curriculum, the bandit's exploration is uncontrolled and frequently inappropriate. With the curriculum, the bandit's exploration is bounded by what the domain expert has determined is sensible. The bandit and the curriculum designer are not competing for the same job.

**"Thompson sampling is the smart choice; epsilon-greedy is the dumb choice."**

Thompson sampling has Bayesian semantics, extends naturally to contextual bandits, handles non-stationarity through priors, and outperforms epsilon-greedy in most production deployments. It is also more expensive to implement, harder to debug, and requires a parametric model of the reward distribution. There is a real argument — one a working RCT against the Medhavy deployment could settle — for using a simpler algorithm whose deployment discipline benefits from the simplicity. The chapter's *What would change my mind* names this directly. The choice of Thompson sampling is supported by the evidence, but it is not the only defensible choice.

---

## Exercises

### Warm-up

**1.** In your own words, explain why the engagement trap is *structural* rather than *intentional*. What property of the reward function makes it true that "no malicious operator is required" for an engine to converge on engagement maximization?

**2.** A friend says: "Bandits are exploration-exploitation; that just means they balance trying new things against doing what's already working." Refine this sentence so that it is precise enough to describe what a *contextual* bandit does. What does the word *contextual* add?

### Application

**3.** *(Apply.)* You are handed a reward-function specification for a different intelligent textbook (computer science, undergraduate). The reward is a linear combination of:

- $R = w_1 \cdot \text{(session completion)} + w_2 \cdot \text{(within-session quiz accuracy)} + w_3 \cdot \text{(seven-day retrieval)}$

The initial weights are $w_1 = 0.4$, $w_2 = 0.4$, $w_3 = 0.2$. The deployment has run for four weeks. The platform's GLP layer reports that students whose engine has converged on high-completion-rate modes show declining Y3 (cross-context transfer) and Y6 (retrieval strength decay) over time, while their session-completion and within-session-accuracy scores climb. Diagnose the failure. What is the engine actually optimizing? Specify the weight change you would propose, and explain what you expect to see in the GLP signals over the following four weeks.

**4.** *(Evaluate.)* A vendor tells you their adaptive engine "personalizes learning to each student" and that "every student gets a unique learning path." What two questions do you ask to determine whether the engine uses cross-learner generalization or within-learner optimization? For each question, write the answer that would tell you it is cross-learner.

### Synthesis

**5.** *(Analyze; producing.)* Pick a learning domain you know well — your own discipline, a topic you teach, a hobby you have studied. Specify, in 400–600 words, what the *context vector* would look like for an adaptive engine in that domain: which mastery signals, which reasoning-quality signals, which engagement-recency signals, which concept-level features. For each feature you propose, name what it would tell the engine and what failure mode it would invite if used as reward rather than as context.

### Challenge

**6.** *(Evaluate.)* The chapter argues that the seven-day delayed retrieval probe is the most important architectural commitment in the engine. Describe a deployment situation in which this claim would be wrong — a class of learners, a content domain, or a use case where a faster-feedback reward signal would produce better learning outcomes than a seven-day-delayed one. What is the test that would distinguish your case from the chapter's claim?

---

## What Would Change My Mind

A within-learner bandit deployment study at six-month follow-up showing convergence rates worse than the cold-start cost predicts — by the end of the term, the per-learner posterior is too noisy to dominate the population prior on outcome prediction. That would argue for hierarchical cross-learner pooling as the engineering default, with within-learner as a refinement layer. The bet on heterogeneity would have been wrong, and the architecture would have to add cross-learner generalization back in, carefully.

Alternatively: a randomized comparison of Thompson sampling against a much simpler ε-greedy bandit on a Medhavy deployment, showing no statistically significant outcome difference. That would argue for the simpler algorithm. The deployment-discipline benefits of simplicity — fewer hyperparameters, easier to audit, easier to teach to a curriculum designer — would dominate the marginal sophistication advantage. The chapter would still hold the within-learner choice; only the algorithmic choice would change.

A third: a reward-function audit showing that the seven-day delayed retrieval probe is being gamed — learners recognize the probe items and pattern-match to them without genuine retrieval. That would force redesign of the probe and the reward signal. The engine would not change. The measurement layer that feeds it would.

---

## Still Puzzling

The coupled-arms problem. Textbook bandit theory assumes independent arms. The Medhavy modes are coupled — a Glimmer session changes the representation that Quiz Me operates on. The honest engineering frame is a partially observable Markov decision process, where the arms are actions and the learner's mastery state is the partially observed state. The deployed system is a contextual bandit. How much performance is the platform leaving on the table by ignoring the coupling? Not known. The bet is that the simplification is worth it for the deployment discipline benefits; the bet is also testable.

The delayed-reward problem. Seven days is long for a bandit. The Impatient Bandit framework lets the engine learn from progressive signals while remaining anchored to the delayed probe, but the optimal weighting between progressive and delayed signals is itself a hyperparameter that has to be learned from data the platform does not yet have at scale.

The convergence problem. Within-learner bandits converge slowly. For a learner whose session count is too low for convergence, the platform has to choose between falling back to the population prior — which reintroduces cross-learner generalization through the back door — or accepting noisy adaptation. The first is operationally easier and architecturally inconsistent. The second is honest and uncomfortable. The chapter does not resolve this.

The audit problem. A bandit whose reward weights drift toward engagement is detectable in the weight history. Who is responsible for the audit? Platform team, curriculum design team, external party? This is a governance question the chapter raises and leaves open. It is the kind of question the second edition of this book may have to answer, after the field has watched a few deployments succeed or fail.

---

## Chapter Closing / Bridge to Chapter 8

The engine is a small loop. Pick a mode. Observe the reward. Update the policy. Repeat. The math is two pages. The architecture decisions — what counts as a reward, who the engine generalizes across, where the engagement-versus-learning distinction is enforced — are everything else, and they are upstream of the math.

There is one more thing the engine is downstream of, though, and the chapter has been leaning on it without naming it. The bandit cannot pick a good arm if the curriculum has not specified what counts as a good outcome for this concept at this Bloom level. The mode-appropriateness flags are not the engine's choice; they are an input. The prerequisite graph is not the engine's choice; it is an input. The concept's importance tier, its frequency tier, its membership in the chapter's outcome hierarchy — all inputs.

The next chapter delivers the layer that produces those inputs. It is the layer most authors want to skip, the one most platforms wing, and the one that — when it goes wrong — silently breaks everything downstream, including this one.

---

*Suggested next chapter: 8 — The Curriculum Design Layer.*
