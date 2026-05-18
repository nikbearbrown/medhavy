# Research Notes — Chapter 7: The Adaptive Engine

*Load-bearing chapter. TIKTOC filename `08-the-adaptive-engine.md`. Bloom's level: Evaluate. Compiled 2026-05-17. These notes are a working synthesis for the chapter writer; every claim should be traceable to a pantry source or flagged `[verify]`.*

---

## A. Concept under examination — what the chapter teaches

The reader learns three things and is expected to be able to use them:

1. **What the adaptive engine actually is.** A contextual multi-armed bandit whose arms are the four learning modes (Ask AI, Case Study, Quiz Me, Glimmer), whose context is a feature vector describing where this learner is right now on this concept, and whose reward signal is a composite Genuine Learning Probability (GLP) estimate rather than session engagement. (Source: TIKTOC Ch 7 outline; `medhavy-1.5-feature-roadmap-complete.md` Appendix on Medhavy 2.0; `PEDAGOGY ARCHITECTURE.txt` §4 on the bandit selection mechanism.)
2. **Why within-learner generalization is the consequential design choice.** Most adaptive platforms learn across learners — they assume the population is similar enough that what worked for one student carries information for another. Medhavy's bandit learns *per learner*. This does not require the assumption that learners are similar (which is a load-bearing assumption empirical learning analytics literature has not been able to validate at scale), but it costs more sessions to converge. The design choice is a bet on convergence-versus-assumption.
3. **How a reward function silently drifts toward engagement when nobody is looking.** The casino owner watching through the security camera is the central image. An engine fed an engagement-shaped reward will optimize engagement — the math is correct, the loss function is correct, the platform is wrong. This is the failure mode the chapter exists to name and forestall.

The chapter's Bloom's level is Evaluate. The reader should be able to look at a vendor's adaptive engine and ask the three questions that diagnose whether it is optimizing for learning or drifting: *what is the reward signal, who is generalization happening across, and where in the system is the engagement vs. learning distinction enforced?*

---

## B. Specification move — pulling apart vague terms

This is the section where the chapter writer should spend effort. The terms "adaptive," "personalized," "intelligent," and "AI tutoring" are doing too many jobs.

- **Adaptive** in most platforms means "the user interface changes based on user behavior." In the bandit sense it means something stricter: the *policy* — the mapping from learner state to next action — is updated based on observed reward.
- **Personalized** in vendor copy almost always means "the system has a user account and remembers what you did." In the bandit sense it means "the policy that the engine applies to *this* user is statistically distinct from the policy it would apply to another user with the same nominal label." Personalization without the second is account state, not adaptation.
- **AI tutoring** in popular discourse often means "an LLM responds to the student." That is a content-generation choice. The adaptive engine is the *meta-question*: given that the system can do many things, what does it do *next*, and why?
- **Reward signal** is the most dangerous term, because it sounds technical and benign. Operationally it is the function the engine actively maximizes. If reward is "session length," the engine learns to extend sessions. If reward is "click-through to next mode," it learns to make the next-mode offer attractive. If reward is "delayed retrieval accuracy at seven days" (the proposed Medhavy reward; `medhavy-1.5-feature-roadmap-complete.md` Appendix), it learns to produce durable memory. The choice is the architecture.
- **Bandit** in the casino sense is a one-armed mechanical device that pays out probabilistically. In the algorithmic sense it is a stateless decision rule that selects an action and receives a reward. *Contextual bandit* extends this to actions that depend on observable context. The terminology is borrowed; the engineering is precise.

The reader must leave §B able to say: *the adaptive engine is a contextual bandit whose arms are modes, whose context is a learner-state feature vector, and whose reward is a measurable learning signal — not engagement, not satisfaction, not session length.*

---

## C. The casino and its formalization — the chapter's central mechanism

### C.1 The casino as opening hook

The hook the TIKTOC names: five slot machines, 1,000 tokens, no way to tell from looking which one pays best. Each pull buys both an immediate (small, noisy) payout and a small piece of information about the machine's underlying payout distribution. The dilemma is structural — every token spent learning is a token not spent earning, and every token spent earning is a token not spent learning. There is no schedule that perfectly resolves the tradeoff; there are only schedules with different regret profiles.

This is the dilemma Herbert Robbins formalized in 1952.

**Citation to verify carefully:**
- Robbins, Herbert. 1952. "Some Aspects of the Sequential Design of Experiments." *Bulletin of the American Mathematical Society* 58 (5): 527–535. ([American Mathematical Society / Project Euclid](https://projecteuclid.org/journals/bulletin-of-the-american-mathematical-society/volume-58/issue-5/Some-aspects-of-the-sequential-design-of-experiments/bams/1183517370.full)) `[verify exact pagination and that this is the canonical formalization the field cites]`

Robbins's 1952 paper is the conventional citation for the formal multi-armed bandit problem, building on Wald's sequential analysis. The Sutton & Barto textbook (in pantry as `_lib_reinforcement_learning_an_introduction.md`, Ch 2: Multi-arm Bandits) frames the problem the same way — isolating exploration-exploitation as the simplest non-trivial reinforcement learning setting. Sutton & Barto present the canonical 10-armed testbed, ε-greedy, optimistic initial values, UCB1, and gradient bandits. Convergence proofs cited to Auer, Cesa-Bianchi & Fischer 2002 for UCB1.

### C.2 The translation — slot machines → modes

The Medhavy translation, line by line:

- **Five slot machines → four modes.** Ask AI, Case Study, Quiz Me, Glimmer. The choice space is small and pedagogically motivated (`PEDAGOGY ARCHITECTURE.txt` §3 — five approaches selected because they are implementable in a text-based conversation and produce distinguishable learner behavior). Medhavy 2.0 names four; the older five-approach formulation included Direct Instruction as a separate arm. Chapter should clarify whether Ask AI subsumes direct instruction or whether direct instruction is a fifth arm `[verify against current platform spec]`.
- **1,000 tokens → study sessions.** Tokens become finite. A medical student has a real budget — calendar weeks before boards, hours per evening — and the bandit's exploration costs come out of that budget. The chapter should make this concrete: a Glimmer session that fails because the engine was exploring is *time* the student did not spend on a Quiz Me round that would have worked.
- **Payout → genuine learning probability.** This is where the analogy works hardest. In the casino the payout is observable on the pull — coins come out, or they don't. In learning the payout is *delayed and inferred*. The bandit cannot read genuine learning off the screen; it must reconstruct it from the seven GLP friction signals (Y1–Y7) and from delayed retrieval probes seven days later. The latency between action and reward is the bandit's hardest engineering problem.

The analogy breaks down in three places — the chapter should name each:

1. **The payouts are stationary in the casino, non-stationary in learning.** A slot machine's expected value does not change as you pull it; a learner's expected return from Quiz Me *does* change as their FSRS state on a card matures. The Medhavy bandit is technically a non-stationary contextual bandit, which is harder than the textbook case.
2. **The arms in the casino are independent; the modes are coupled.** Pulling slot machine 3 tells you nothing about slot machine 4. But a Glimmer session changes the learner's representation, which changes the expected return from Quiz Me, which changes the expected return from Case Study. The arms feed each other. The textbook bandit framework does not address this directly; it is closer to a Markov Decision Process with the modes as actions and learner-state as the state. The chapter should name this honestly: *the bandit framing is a useful simplification, not the complete model*.
3. **The casino payout is the actual money.** The GLP signal is a probabilistic *estimate* of learning. The bandit is updating its policy on an estimate of an estimate. Estimation error in GLP becomes policy error in the bandit. This is one of the eight open bets.

### C.3 ε-greedy, UCB1, Thompson Sampling — the three algorithmic candidates

Quick technical summary, drawn from Sutton & Barto Ch 2 (`_lib_reinforcement_learning_an_introduction.md`) and the production-systems literature:

- **ε-greedy.** With probability 1−ε, pull the arm with the highest estimated mean reward (exploit). With probability ε, pull a random arm (explore). Pros: simple, interpretable. Cons: exploration is undiscriminating — once you have strong evidence that arm 3 is bad, you still pull it ε/k of the time. ε must be tuned; constant ε does not converge to optimal play.
- **UCB1 (Auer, Cesa-Bianchi & Fischer 2002).** Pull the arm that maximizes `mean + sqrt(2 ln(t) / n_i)`, where t is total pulls and n_i is the number of times arm i has been pulled. The square-root term is an exploration bonus that shrinks as the arm is sampled more. Pros: principled, no tuning parameter, regret bound O(log t). Cons: assumes stationary rewards; less effective in non-stationary or contextual settings without modification.
- **Thompson Sampling (Thompson 1933; modern revival Russo, Van Roy, Kazerouni, Osband & Wen 2018 *Foundations and Trends in Machine Learning* `[verify]`).** Maintain a posterior distribution over each arm's expected reward. At each step, sample from each posterior and pull the arm whose sample is highest. Pros: extends naturally to contextual bandits, handles non-stationarity through the prior, Bayesian semantics are interpretable. Cons: requires a parametric model of the reward distribution.
- **Medhavy 2.0's choice.** Thompson Sampling is the proposed implementation (`medhavy-1.5-feature-roadmap-complete.md` Appendix). The reasoning: Thompson scales to contextual bandits, handles the non-stationarity that learning introduces, and the Bayesian framing maps cleanly onto the "prior weights from evidence base, posterior from deployment data" architecture the book describes.

The Bayesian connection is worth foregrounding because the chapter writer can land it in plain English: a Thompson-Sampling bandit *is the engine being honestly uncertain about which mode works for this learner right now*. It doesn't pretend to know; it samples from its current best guess of what it knows, acts on that sample, then updates. That is the Bayesian discipline (`_lib_everything-is-predictable_-how-bayesian-statistics-explain-our-world.md`) operating inside the platform.

### C.4 The contextual bandit — wind speed becomes learner state

The Sutton & Barto presentation introduces the contextual bandit as the bridge from bandits to full reinforcement learning: "what if the payout depended on the wind speed?" In the slot machine version this is metaphorical; in Medhavy it is literal.

The Medhavy context vector, drawn from `medhavy-1.5-feature-roadmap-complete.md` Appendix and `PEDAGOGY ARCHITECTURE.txt`:

- **Learner history.** Prior mode-by-concept performance, GLP component scores, days since last session, total session count.
- **Concept prerequisites.** Where the focal concept sits in the prerequisite graph, mastery state (BKT-style) on prerequisite concepts (cross-reference `concept-sequencing-research.md` §2 on prerequisite sequencing).
- **Time since last session on this concept.** Drives FSRS retrievability estimate; high retrievability shifts the engine away from Quiz Me and toward Case Study or Glimmer.
- **Prior mode performance.** Which modes have produced GLP gain for this learner historically; which have produced engagement-without-learning patterns.
- **Concept-mode appropriateness flags.** Set by the curriculum design layer (Ch 8). Some concepts admit Glimmer; some do not. The flags constrain which arms are available before the bandit's policy runs.

The "wind speed" framing is the move the chapter should make: *the bandit is not picking the best mode in the abstract; it is picking the best mode given the wind*. And the wind is a vector, not a scalar.

---

## D. The within-learner vs. cross-learner design decision

This is the consequential paragraph of the chapter. The TIKTOC names it explicitly: *within-learner does not require the assumption that learners are similar, but needs more sessions to converge*.

### D.1 What cross-learner generalization assumes

Cross-learner bandits — the standard production-systems approach (Lindsey, Shroyer, Pashler & Mozer 2014 on personalized review; ASSISTments; Carnegie Learning) — pool data across learners. The implicit assumption: learner *i* and learner *j*, given similar context features, have similar expected mode-reward distributions. If the assumption holds, cross-learner pooling converges much faster than within-learner — every other learner's data contributes to the policy for this learner.

The empirical question: does the assumption hold? The cross-domain learning analytics literature has not produced a clean answer. The Yudelson, Koedinger & Gordon 2013 finding on Individualized BKT (in `concept-sequencing-research.md` §2.1) is the most relevant: per-student initial-knowledge and learn-rate parameters substantially improve prediction over population parameters. That is direct evidence that learners are *not* well-modeled by a shared population mean — at least on the dimensions BKT measures.

If the population is heterogeneous along dimensions the platform cannot easily observe (background knowledge, motivation, comprehension speed, anxiety responses to ambiguity), cross-learner pooling *transfers the noise from the population mean onto each individual*. The bandit's confidence becomes false confidence.

### D.2 What within-learner generalization costs

Within-learner bandits start from scratch for every new student. The bandit has no prior over the modes' expected returns for *this* learner; the first few sessions are pure exploration. The cost:

- **Cold start.** Until the bandit has seen 5–10 sessions, its mode selection is essentially random within the curriculum constraints. The early sessions may feel disorganized to the learner.
- **Convergence rate.** Within-learner convergence requires more total sessions than cross-learner. For a learner using the platform for a single semester, the bandit may still be exploring at the end of the term. The chapter should be honest about this.
- **Sample-efficiency hacks available.** Hierarchical priors (informed by the population distribution but learner-specific posterior); transfer learning from similar learners (named-similar by explicit curriculum tags rather than implicitly via shared population); domain priors from the evidence base on which modes work for which Bloom's levels (cross-reference Ch 6). These reduce the cold-start cost without recovering the strong cross-learner assumption.

### D.3 The honest tradeoff

Within-learner is the right choice when:

- The platform is high-stakes enough that incorrect personalization is costly (medical school; professional certification).
- The population is heterogeneous enough that pooled estimates would be statistically dominated by the wrong subgroup for any given learner.
- The platform is designed for sustained use (semester or longer), so the cold-start cost is amortized.

Cross-learner is the right choice when:

- Sessions are short and the platform is high-volume.
- The learner population is narrow enough that the homogeneity assumption is approximately true.
- The cost of incorrect adaptation is small (consumer language-learning apps).

Medhavy chooses within-learner. The chapter should say so plainly and name the bet: *we are betting that the convergence cost is worth paying for personalization that does not depend on the heterogeneity assumption*. This is bet #3 in the eight open bets (TIKTOC Ch 11 — within-learner generalization rate).

---

## E. The reward function — and the engagement trap

### E.1 What the engine is optimizing over

The state space is (mode × concept × time). Each cell is a (learner, mode, concept, session-window) tuple whose reward the engine estimates from the GLP signals (Ch 5) and the delayed retrieval probe.

The reward function specification, expanded from `medhavy-1.5-feature-roadmap-complete.md` Appendix and the GLP framework (Ch 5):

- **Primary reward: delayed retrieval accuracy at seven days.** A new Quiz Me item on concept *C*, offered seven days after the mode-decision session, scored by the learner's accuracy on that item. This is the most direct measurable proxy for durable learning the platform has.
- **Composite GLP signal.** A weighted combination of the seven Y-components (Y1 temporal engagement, Y2 error trajectory coherence, Y3 cross-context transfer, Y4 uncertainty calibration, Y5 social knowledge texture, Y6 retrieval strength decay, Y7 scaffolding response curve). These provide a denser, faster-updating signal than the seven-day probe alone — but require the measurement infrastructure Ch 5 specifies.
- **Initial weights from the evidence base.** The Ch 3 evidence audit supplies informed priors: spaced retrieval has strong evidence (Roediger & Karpicke 2006; Cepeda 2006/2008 in `quiz-me-research.md`); CBL has moderate evidence under specific conditions (Thistlethwaite 2012 BEME synthesis in `case-study-research.md`); Glimmer-style ill-structured problems have evidence for transfer but anxiety failure modes for novices (Jonassen 1997; Fiorella & Mayer 2016 in `glimmer-research.md`); Ask AI has Bastani 2025 as the cautionary data point — the wrong guardrail produces measurable harm (`ask-ai-research.md`).
- **Update from deployment data.** As the platform accumulates session data, the weights update. The within-learner discipline means each learner's weights are partly idiosyncratic — but the curriculum-level priors keep the engine from collapsing onto noise during cold start.

### E.2 The engagement trap, made explicit

The casino owner watching through the security camera. The chapter's central image, and the failure mode the entire book exists to forestall.

The mechanism: any platform that uses *session-derived* signals as reward — time on platform, click-through rate, return rate, self-reported satisfaction — and that learns to maximize those signals, will *converge to engagement-maximizing behavior regardless of whether the operators want it to*. The math does what the math is told. The operators may believe they are optimizing learning; the gradient is computed on engagement.

This is structurally identical to the recommender-system failure mode that produces social-media addiction. The platform is not malicious; the loss function is. (Cross-reference: the Khanmigo IDK-IDK incident from Ch 1; cross-reference: `glimmer-displacement-research.md` on the displacement failure mode in mode-design.)

The engagement trap appears in adaptive engines in three specific ways the chapter should walk through:

1. **Direct substitution.** The reward function literally is session length or click rate. The platform builders chose engagement as the metric. This is the obvious failure; it is rarer than the second and third.
2. **Proxy drift.** The reward function is nominally a learning signal but the implementation is engagement-shaped. "Quiz completion rate" sounds like learning; it is engagement once a learner figures out they can skip difficult items. "Time on page reading the explanation" sounds like learning; it is engagement when a learner gets distracted and leaves the tab open.
3. **Signal contamination.** The reward function is well-designed but the *measurement* of the signal leaks engagement information. If the seven-day retrieval probe is presented to the learner in a way that makes engagement-style responses (quick guessing, picking the first option) look like high accuracy, the engine learns to produce those responses upstream.

The defense, as the chapter should specify it:

- **Reward is composite, not single-signal.** The seven Y-components and the delayed probe together; no single channel can be gamed without showing up as inconsistency across channels.
- **Reward is measured downstream, not within-session.** The seven-day delay is the most important architectural commitment. An engine that gets immediate feedback from within-session signals will converge on within-session engagement.
- **Reward weights are audited.** A platform whose adaptive engine drifts is detectable by *looking at the weight history*. The chapter should specify that this audit is part of the deployment discipline, not a research nice-to-have.

### E.3 The right weights — open bet #6

The TIKTOC names this directly: *honest uncertainty: right weights are one of the book's eight open bets*. The chapter should enumerate the eight open bets in the reward function discussion, with the right reward function weights specifically as bet #6.

The eight open bets, drawn from TIKTOC Ch 11 outline:

1. Does context-anchoring alone convert GPT-Base failure to GPT-Tutor success? (Ask AI)
2. Does pre-written faculty-reviewed CBL produce reasoning gains comparable to group human-facilitated CBL when solo/asynchronous? (Case Study)
3. Does FSRS-style scheduling generalize to conceptual material? (Quiz Me)
4. Is the Quiz Me habit loop driven by the due-count or the algorithm? (Quiz Me habit)
5. Does backwards-faded scaffolding prevent the anxiety collapse in novice Glimmer users? (Glimmer)
6. **Does priority-weighted scheduling outperform recall-only scheduling — and what reward function weights produce best per-learner outcomes? (The bandit's reward weights themselves.)**
7. Does Level-3 domain specificity outperform Level-1 generic instruction enough to justify the production cost? (Content; Ch 9)
8. Does AI-generated educational content produce durable learning outcomes comparable to professionally produced content? (Content; Ch 9)

Bet #6 is the reward-function bet — and the chapter should treat it as the consequential one for the engine layer, alongside bet #2 (within-learner convergence — though TIKTOC currently bundles this implicitly into bets 2 and 6; the chapter writer should decide whether to make it a separate ninth bet or fold it in).

---

## F. Connection to existing pantry — what to cite by reference

The chapter should cite by filename and not re-research the following ground:

- `concept-sequencing-research.md` — BKT and DKT for prerequisite mastery state (§2.1); Pavlik & Anderson 2008 for the gain-per-minute objective function that maps cleanly onto a bandit reward (§3.4); the inner-loop/outer-loop frame from VanLehn 2006 (§2.3); the linear-combination vs. gating vs. bandit-over-priority-bands vs. expected-value-maximization functional forms (§6.2). The chapter should cite §6.2 directly when explaining what kind of object the Medhavy reward function is.
- `ask-ai-research.md` — Bastani 2025 PNAS finding as the cautionary data point on engagement-style optimization without learning; ITS effect sizes (+0.40 to +0.70) as the prior for what well-designed adaptation can produce.
- `case-study-research.md` — Thistlethwaite 2012 BEME synthesis as the evidence base for Case Study reward weights; the pre-written vs. on-demand case literature.
- `quiz-me-research.md` — Roediger & Karpicke 2006, Cepeda 2006/2008, FSRS algorithmic details for Quiz Me reward weights and for the seven-day delayed-probe rationale.
- `glimmer-research.md` and `glimmer-displacement-research.md` — Jonassen 1997, Fiorella & Mayer 2016 on generative learning; the anxiety failure mode in novice learners (scaffolding fading; bet #5).
- `PEDAGOGY ARCHITECTURE.txt` §4 — the bandit selection mechanism as currently specified in Medhavy 1.0; the cold-start strategy (pedagogy.default fallback for the first 2–3 sessions); the engagement-as-proxy honesty.
- `MVAL.txt` — the platform's internal Medhavy Value metric and its relationship to GLP. Use for the technical-implementation paragraph; the chapter is not a reference doc, so MVAL details belong in Appendix D not the chapter body.
- `medhavy-1.5-feature-roadmap-complete.md` — Thompson Sampling as the implementation choice; the seven-day delayed retrieval reward; the feature vector specification.
- `_lib_reinforcement_learning_an_introduction.md` — Sutton & Barto Ch 2 as the canonical textbook on bandits. Reference for ε-greedy, UCB1, contextual bandits, exploration-exploitation. The chapter should cite the textbook by section, not by name-drop.
- `_lib_everything-is-predictable_-how-bayesian-statistics-explain-our-world.md` — the Bayesian framing for Thompson Sampling and for the prior-posterior structure of within-learner convergence. The chapter should land the connection in plain English: *the engine is honestly uncertain, and Bayesian updating is the discipline that keeps the uncertainty honest*.

Cross-reference but do not duplicate the GLP framework specification (Ch 5 and Appendix C) — the chapter assumes the seven components and the ensemble architecture as inputs, not as objects to re-explain.

---

## G. Open questions, gaps, and verify flags for the chapter writer

### G.1 The Robert C. Gray reference

TIKTOC says: *Reference the Robert C. Gray multi-armed bandit explanation style: slot machines first, technical vocabulary second.* Search returns:

- The standard accessible bandit explanation in the popular CS / data-science writing tradition is associated with several authors (David Silver's RL lectures; Lilian Weng's blog post on bandits; Russo et al.'s tutorial; Sutton & Barto for the textbook canonical). I do not find an author named **Robert C. Gray** with a canonical bandit explanation by web search and within the pantry. The single match in the project is the TIKTOC itself.
- **`[VERIFY URGENT]`** — confirm with Nik the exact reference. Possible interpretations: (a) personal-correspondence reference; (b) misremembered name for another author (e.g., R. M. Gray of Stanford has work in information theory; Daniel Russo / Steven Scott / John White have written accessible bandit pieces); (c) a specific blog post or lecture series the chapter writer should match in *style* rather than cite as primary literature.
- **Recommended chapter move while verification is pending:** the chapter should adopt the style — slot machines as the lead, technical vocabulary as the follow-up — without naming Gray as the source, unless Nik can confirm the reference. Citing an unverifiable author by name is a Hard Rule #1 violation. The Sutton & Barto Ch 2 framing supplies the same pedagogical move; the chapter can land it from Sutton & Barto directly.

### G.2 Herbert Robbins 1952

Citation as given above (`Bulletin of the AMS` 58 (5): 527–535). The chapter writer should *verify*:

- Pagination (527–535 is the canonical citation; check Project Euclid).
- That Robbins is the right primary citation rather than (e.g.) Thompson 1933, who introduced the Bernoulli bandit problem two decades earlier. The conventional move in the RL literature is to credit Thompson for the original problem statement and Robbins for the sequential-experiment formalization that the modern theory uses. The chapter should name Thompson 1933 ("On the Likelihood that One Unknown Probability Exceeds Another in View of the Evidence of Two Samples," *Biometrika* 25: 285–294) as well as Robbins 1952 — both are foundational; using only Robbins is slightly misleading.

### G.3 Sutton & Barto

Sutton, Richard S., and Andrew G. Barto. 2018. *Reinforcement Learning: An Introduction*. 2nd ed. MIT Press. Pantry note `_lib_reinforcement_learning_an_introduction.md` is a chapter-by-chapter mapping. The bandit chapter (Ch 2) is the primary reference. Edition is 2018 (second edition); first edition was 1998. Available free online at [http://incompleteideas.net/book/the-book-2nd.html](http://incompleteideas.net/book/the-book-2nd.html).

### G.4 Auer, Cesa-Bianchi & Fischer 2002 (UCB1)

Auer, Peter, Nicolò Cesa-Bianchi, and Paul Fischer. 2002. "Finite-time Analysis of the Multiarmed Bandit Problem." *Machine Learning* 47 (2–3): 235–256. ([DOI: 10.1023/A:1013689704352](https://doi.org/10.1023/A:1013689704352)) `[verify pagination]`. This is the canonical citation for UCB1; the chapter should use it if UCB1 is named.

### G.5 Thompson 1933

Thompson, William R. 1933. "On the Likelihood that One Unknown Probability Exceeds Another in View of the Evidence of Two Samples." *Biometrika* 25 (3–4): 285–294. The historical primary source.

### G.6 Within-learner convergence rates

There is no published RCT comparing within-learner vs. cross-learner bandits on educational outcomes that I can identify in the pantry or by general web search. `[verify thoroughness with EDM and AIED proceedings]`. The closest is the Yudelson, Koedinger & Gordon 2013 individualized-BKT result, which shows the *prediction* gain from per-student parameters but not the *adaptation* gain from a per-student bandit. This is the bet — and the gap — the chapter should name honestly.

### G.7 The eight open bets — list discipline

The TIKTOC enumerates eight open bets. The chapter writer should:

1. State the eight bets at the end of §E (reward function discussion).
2. Cross-reference to Ch 11, which delivers the full epistemic inventory.
3. Resist the urge to add a ninth bet here. Within-learner convergence rate, the reward-function weights, and the GLP-as-reward signal-fidelity question all sit inside the engine layer; if the chapter wants to split them, it should propose the split for the Ch 11 author rather than introduce inconsistency between the chapters.

### G.8 The non-stationarity gap

The chapter should be explicit that the Medhavy bandit is technically a *non-stationary contextual bandit with coupled arms* — the slot-machine analogy carries the reader through the first two layers but breaks at the third. The textbook bandit theory (Sutton & Barto Ch 2) does not address coupled arms. The closest formal frame is a Partially Observable Markov Decision Process (POMDP) where the arms are actions and the learner's mastery state is the partially-observed state. Naming this gap is honest; pretending the textbook theory directly applies is not.

### G.9 The Bayesian framing — load-bearing or decorative?

The Thompson Sampling choice is technical; the Bayesian-framing connection to `_lib_everything-is-predictable_-how-bayesian-statistics-explain-our-world.md` is rhetorical. The chapter writer should decide:

- *Load-bearing version:* introduce the prior-posterior structure explicitly, explain that within-learner convergence is just Bayesian updating with a per-learner posterior, and that the engagement trap is what happens when the *prior* secretly encodes engagement-shaped beliefs. This makes the Bayesian connection do real work.
- *Decorative version:* one paragraph naming the connection and moving on. This is safer if the chapter is already long.

The TIKTOC tilts toward decorative — the load-bearing concept is the casino-and-formalization, not Bayes. Recommend decorative unless the chapter writer finds the load-bearing version produces a tighter chapter.

### G.10 The casino owner — verify the metaphor

"The casino owner watching through the security camera" is the central engagement-trap image the TIKTOC names. The chapter should land it precisely:

- *The casino* is the platform.
- *The gambler* is the learner.
- *The slot machines* are the modes.
- *The casino owner* is the platform's measurement system — and, by extension, whoever is deciding what reward signal the bandit optimizes.
- *The security camera* is the engagement dashboard. It sees what the casino owner wants to see: time on machine, repeat play, return visits.
- *What the security camera does not see* is whether the gambler is going home with money. In learning terms: whether durable knowledge actually accumulated.

The platform-as-casino metaphor is uncomfortable on purpose. It is the right discomfort to leave the reader with at the close of §E.

---

## H. What the worked example should do

The TIKTOC specifies: *A within-learner bandit session log for a medical student across six weeks of oncology study. Show engine's initial mode distribution (near-uniform — pure exploration). Week 2 update (this student responds to Quiz Me better than Ask AI on factual concepts). Week 4 (Glimmer underperforming — engine reduces weight). Week 6 (Case Study receiving higher allocation for application-level concepts). Walk through the reward function update at each step.*

Recommended structure:

- **Week 0.** Cold start. The bandit's posterior over (mode | concept | learner) is the platform-level prior. Mode allocations roughly: Ask AI 25%, Quiz Me 25%, Case Study 25%, Glimmer 25%, with curriculum-design-layer flags excluding modes inappropriate for the concept's Bloom level (e.g., Glimmer flagged off for foundational pharmacology concepts).
- **Week 2.** Student has done ~8–10 sessions across ~4 oncology concepts. Quiz Me on factual concepts (drug classes, mechanism types) has produced consistent seven-day retrieval gains for this student. Ask AI has produced *no* seven-day retrieval gain on factual concepts — the student asks, gets a fluent answer, and forgets. The posterior shifts: Quiz Me weight rises for factual concepts; Ask AI weight falls for factual concepts but remains high for *prerequisite-clarification* contexts (different concept type, different posterior cell).
- **Week 4.** Glimmer has been offered three times. Two sessions produced abandonment within the first ten minutes — Y7 (scaffolding response curve) shows the anxiety failure mode. The engine reduces Glimmer weight for this learner but does not zero it; the bandit retains exploration probability so that as the student's mastery grows the engine can re-test.
- **Week 6.** Concepts have advanced from Understand-level to Apply-level. Case Study allocations have grown for these — the engine has learned that on application-level concepts (treating a stage III tumor; choosing a chemotherapy regimen under comorbidity), Case Study produces both within-session GLP signal (Y3 cross-context transfer; Y2 error trajectory coherence) and seven-day retrieval gain. The reward function update for Case Study runs through both channels.

The worked example should show **at least one** of the GLP component updates explicitly — e.g., walk through how Y6 (retrieval strength decay) updates the Quiz Me posterior — so the reader sees what "the reward function update" actually computes.

Numbers should be illustrative; flag the worked example as a simulated trajectory not a deployed result (TIKTOC open question #4: simulated data cases — labeling policy). This is honest and necessary; deployed within-learner data at this granularity does not yet exist in publishable form.

---

## I. Assessable exercises — the TIKTOC names three

1. (Apply) Given a reward function specification and a four-week deployment log, calculate the engine's updated mode allocation for a specific learner-concept pair.
2. (Evaluate) An adaptive engine's session logs show increasing time-on-platform and decreasing GLP scores over six weeks. Diagnose the failure. What reward signal is the engine actually optimizing?
3. (Analyze) A platform claims to "personalize learning to each student." What question do you ask to determine whether it uses cross-learner generalization or within-learner optimization?

The exercises are well-targeted for an Evaluate-level chapter. The chapter writer should resist adding more — three is the right number.

Suggested **worked-answer sketches** for the chapter writer's reference (do not include in the final draft; for the writer to check that exercises are answerable):

- *Exercise 1 sketch.* The student gets the reward function in linear-combination form: R = w_1·Y1 + w_2·Y2 + ... + w_7·Y7 + w_d·D_7, where D_7 is the seven-day delayed-probe accuracy. The log gives them, per session, the realized Y-components and (where available) D_7. The Thompson-Sampling update is the Bayesian posterior over the per-arm reward distribution; the exercise has the student compute the sample-weighted posterior mean for each arm conditional on the context and report the resulting mode allocation as a softmax-like proportion. The exercise is doable on paper for k=4 arms and t=20 sessions.
- *Exercise 2 sketch.* Time-on-platform up, GLP scores down — diagnosis: the engine's reward function has a positive weight on a signal that correlates with engagement (likely Y1 misinterpreted as engagement when it should be calibration). Alternative: signal contamination — the GLP scoring is itself drifting. Student is expected to name both candidates and propose the diagnostic test.
- *Exercise 3 sketch.* The question: *"What does the platform do when a single learner's data is anomalous relative to the population? Does the engine continue to apply the population policy, or does it produce a policy local to this learner?"* If the answer is *"it applies the population policy with a learner-specific prior,"* the platform is cross-learner with regularization, not within-learner. The Yudelson 2013 result is the citation for why this matters.

---

## J. Bridge to Chapter 8

The TIKTOC bridge is correct: *The engine's learning depends on a well-specified curriculum. Chapter 8 delivers the curriculum design layer — why backward design is the instrument that produces the structured input the engine requires.*

The chapter writer should land this bridge in the final paragraph by making the engine's dependency explicit: *the bandit cannot pick a good arm if the curriculum has not specified what counts as a good outcome for this concept at this Bloom level. The next chapter delivers the layer that supplies that specification.*

---

## K. Word-count target and chapter shape

The TIKTOC names 5,000–8,000 words. The chapter is load-bearing; the upper end is appropriate. Recommended internal allocation:

- §1 Opening (the casino) — ~600 words. Concrete, specific, no jargon.
- §2 The formalization (Robbins, Sutton & Barto) — ~700 words. Light technical vocabulary; the second pass through the casino, this time with names.
- §3 The translation (slot machines → modes) — ~600 words. Where the analogy works; where it breaks.
- §4 Wind speed → context (the contextual bandit) — ~700 words. The feature vector spelled out.
- §5 Within-learner vs. cross-learner (the consequential decision) — ~1,000 words. The chapter's intellectual center.
- §6 The reward function and the engagement trap — ~1,200 words. The chapter's emotional center; the casino-owner image lives here.
- §7 The eight open bets, with bet #6 (right weights) foregrounded — ~600 words.
- §8 Worked example (six-week oncology trajectory) — ~800 words.
- §9 Exercises, what-would-change-my-mind, still-puzzling, bridge — ~600 words.

Total: ~6,800 words. Adjust as the chapter writer needs.

---

## L. What would change the chapter's reading

The chapter writer should land a specific "What would change my mind" at the close. Candidates:

- A within-learner bandit deployment study at six-month follow-up showing convergence rates worse than the cold-start cost predicts — i.e., even by the end of the term the per-learner posterior is too noisy to dominate the population prior. *That* would argue for hierarchical cross-learner pooling as the engineering default, with within-learner as a refinement.
- A reward-function audit showing that the seven-day delayed retrieval probe is being gamed (learners learn to recognize the probe items and pattern-match without genuine retrieval). *That* would force redesign of the probe and the reward signal.
- A randomized comparison of Thompson Sampling against a much simpler ε-greedy on the Medhavy deployment showing no statistical advantage to Thompson — *that* would argue for the simpler algorithm, since the simplicity carries deployment-discipline benefits the more complex algorithm lacks.

---

## M. Still puzzling

Open questions the chapter raises but does not resolve. Two to four; the TIKTOC anatomy requires this section.

1. The coupled-arms problem. The textbook bandit theory assumes independent arms. The modes are not independent; a Glimmer session changes the representation that Quiz Me operates on. The honest engineering frame is a POMDP, but the deployed system is a contextual bandit. How much performance is the platform leaving on the table by ignoring the coupling?
2. The delayed-reward problem. The seven-day retrieval probe is the most direct learning signal. Seven days is long for a bandit; the engine is updating slowly. What is the right balance between fast (within-session) GLP signals and slow (delayed) probe signals?
3. The convergence problem. Within-learner bandits converge slowly. What does the platform do for a learner whose session count is too low for convergence — fall back to the population prior, or accept noisy adaptation? The first re-introduces cross-learner generalization through the back door; the second is honest but operationally uncomfortable.
4. The audit problem. A bandit whose reward weights drift toward engagement is detectable in the weight history. Who is responsible for the audit? Is it part of the platform team, the curriculum design team, or an external party? This is a governance question the chapter raises; later books may resolve it.

---

*End of research notes for Ch 7. Estimated chapter word count from these notes: 5,500–7,000. Load-bearing flag: this chapter generates prerequisites for Ch 8 (curriculum input to engine) and Ch 11 (open bets). Hostile-reader review recommended before editorial.*
