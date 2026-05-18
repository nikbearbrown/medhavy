# Research Notes — Appendix D: Contextual Bandits — Implementation Notes

*Technical implementation appendix for the Medhavy book. Synthesizes existing pantry content (`07-the-adaptive-engine_notes.md`, `MVAL.txt`, `medhavy-1.5-feature-roadmap-complete.md`, `PEDAGOGY ARCHITECTURE.txt`, `_lib_reinforcement_learning_an_introduction.md`, `_lib_everything-is-predictable_-how-bayesian-statistics-explain-our-world.md`, `concept-sequencing-research.md`) with targeted literature on Thompson Sampling vs UCB1 vs ε-greedy in educational bandits, the LinUCB / contextual-bandit canon, and cold-start strategies. Compiled 2026-05-17 for Cowork to compile against pantry.*

> **Critical flag at top.** TIKTOC §Appendix D lists `Contextual Bandits.txt` as a primary pantry source. **That file does not exist in `books/medhavy/pantry/`.** The pantry scan (2026-05-17) returns no `Contextual Bandits.txt` artifact. The Ch 4 notes (`04-the-four-layers_notes.md` §H, flag #3) name the same gap. The substantive content TIKTOC expected from that file is reconstructed below from `07-the-adaptive-engine_notes.md` (the most thorough bandit reconstruction in pantry, 6,245 words), supplemented by `MVAL.txt`, `medhavy-1.5-feature-roadmap-complete.md` Appendix on Medhavy 2.0, and `PEDAGOGY ARCHITECTURE.txt` §4. **Action requested of the author:** confirm whether `Contextual Bandits.txt` exists in a private location and should be copied to pantry, or approve this reconstruction as the canonical source for Appendix D.

> **Second critical flag.** TIKTOC §Appendix D says "MVAL (Medhavy Value) — the platform's internal value metric and its relationship to GLP." The actual pantry artifact `MVAL.txt` is *not* a value metric. It is a **Minimum Viable Analytical Log** protocol — six fields (WHAT/WHY/HOW/ENVIRONMENT/RESULTS/QUESTIONS) governing how researchers log experiments and pipeline runs. The "Medhavy Value" framing in TIKTOC §App D appears to be a misnomer or earlier-draft name. Appendix D should either (a) drop the MVAL section entirely (it does not belong in a bandit-implementation appendix) or (b) reframe MVAL as the *audit discipline* that produces the data the bandit's offline evaluation requires. This note adopts framing (b) below. **Action requested of the author:** confirm.

---

## A. Appendix scope — what this appendix delivers and to whom

Appendix D is the technical implementation reference for the developer reading the book. The Charles Fadel type can skip it; the developer who got handed `API.md` and is now configuring the adaptive engine cannot. The appendix has to deliver, in roughly 4,000–5,500 words:

1. **The bandit formulation, named precisely.** Arms = the four (or five) modes. Context = a feature vector specified to field-level granularity. Reward = the composite Genuine Learning Probability signal plus the seven-day delayed retrieval probe. The developer should be able to read the appendix and start implementing without a meeting with the curriculum team.
2. **The exploration-strategy decision, defended.** Why Thompson Sampling rather than ε-greedy or UCB1. Why not LinUCB (Li, Chu, Langford & Schapire 2010), the standard contextual-bandit baseline. What the platform deployment is committing to and what alternatives the appendix is closing off.
3. **The cold-start strategy, specified.** What the engine does on session 1, session 2, session 3 of a new learner. Where the prior comes from. When the per-learner posterior begins to dominate the population prior. How long convergence takes (honest estimate, with the bet acknowledged).
4. **The update mechanics, walked through.** A pseudocode-level specification of what happens after a session ends. Which fields update. Which thresholds trigger phase-gate transitions. Where the audit hooks live so the platform team can verify the engine is not drifting toward engagement.
5. **The open bets, named.** The reward function weights, the convergence rate, the coupled-arms problem, the delayed-reward problem. The appendix is an implementation reference, not a hedging exercise — but the bets that affect implementation choices have to be visible to the developer who is making those choices.

The appendix is *not* the place to re-argue the within-learner vs. cross-learner design decision (that is Chapter 7's chapter-level argument). The appendix accepts the design decision and specifies what it costs to implement.

---

## B. The contextual bandit formulation — what the developer is implementing

### B.1 Arms

The arms of the Medhavy bandit are the **four learning modes**: Ask AI, Case Study, Quiz Me, Glimmer. (`PEDAGOGY ARCHITECTURE.txt` §3 documents the pedagogical justification; `medhavy-1.5-feature-roadmap-complete.md` §"What 1.5 adds" specifies the mode-by-mode interaction design.)

A historical note the developer should know: the older Medhavy 1.0 internal documents and `PEDAGOGY ARCHITECTURE.txt` enumerate *five* approaches (direct instruction, Socratic questioning, case-based learning, spaced retrieval, project-based learning). The 1.5 / 2.0 deployment collapsed Direct Instruction and Socratic into Ask AI (as routing modes within a single arm — the Cancer Biology textbook's Mixture-of-Experts persona layer realises this internally). The chapter writer of Ch 6 already addresses this; the appendix should note it once and move on:

- For the deployed 1.5 platform, **k = 4** arms.
- For deployments that surface direct instruction as a distinct arm, **k = 5**.
- The bandit's complexity scales linearly with k for ε-greedy and UCB1 and depends on the posterior parameterisation for Thompson Sampling — k = 4 or k = 5 is well within the regime where any of the three algorithms converges.

A second note on arm availability: the **mode-appropriateness flags** set by the curriculum design layer (Ch 8; `08-the-curriculum-design-layer_notes.md` §C.4) constrain which arms are eligible *before* the policy runs. For a foundational-pharmacology concept tagged at Bloom-level Understand, the Glimmer arm is flagged off; the bandit selects from {Ask AI, Quiz Me, Case Study}. This is implemented as a hard mask, not a soft prior — the engine never selects an arm the curriculum layer has not approved for the concept-Bloom-level cell.

### B.2 Context

The context vector at decision time *t* for learner *l* on concept *c* is a feature vector x_{l,c,t} drawn from five sources (synthesised from `medhavy-1.5-feature-roadmap-complete.md` Appendix on Medhavy 2.0, `PEDAGOGY ARCHITECTURE.txt` §4, and `07-the-adaptive-engine_notes.md` §C.4):

| Feature family | Specific fields | Source |
|---|---|---|
| Learner history | total session count; days since last Medhavy session; sliding-window GLP component scores Y1–Y7; prior mode-by-concept performance vectors | `medhavy-1.5-feature-roadmap-complete.md` §"the contextual bandit" |
| Concept prerequisites | FSRS-style mastery state on each prerequisite concept; prerequisite-depth in the curriculum DAG; aggregated GLP score on prerequisite concepts | `concept-sequencing-research.md` §2 (BKT/DKT); curriculum design layer (Ch 8) |
| Time since last session on this concept | days; FSRS retrievability estimate ([0, 1]); whether a Video and Animation has been watched | `medhavy-1.5-feature-roadmap-complete.md` §"Quiz Me" |
| Prior mode performance | per-arm: mean reward, sample count, variance; per-arm-by-Bloom-level: same | `PEDAGOGY ARCHITECTURE.txt` §4 |
| Concept-mode appropriateness flags | one bit per arm; set by Ch 8 curriculum layer | `08-the-curriculum-design-layer_notes.md` §C.4 |

The total feature vector for the deployed system runs to **roughly 30–50 dimensions** depending on how many GLP components and prerequisite slots are instantiated. This is comfortably in the regime where LinUCB (linear contextual bandit; Li, Chu, Langford & Schapire 2010 `[verify]`) is operationally feasible, and well below the dimensionality where neural contextual bandits become necessary.

### B.3 Reward signal — the composite, specified

The reward signal is the single most consequential design decision in the entire engine (`07-the-adaptive-engine_notes.md` §E names this; the chapter argues it for thousands of words). The appendix's job is to translate that argument into a specification the developer can implement.

The reward function the platform is committing to:

```
R(arm = m | learner = l, concept = c, time = t) = 
    w_d · D_7(l, c, t+7) +
    Σ_{i=1..7} w_i · Y_i(l, c, m, t)
```

Where:

- **D_7** is the **seven-day delayed retrieval accuracy**: a new Quiz Me item on concept *c* presented seven days after the mode-selection session at time *t*, scored {0, 1}. `medhavy-1.5-feature-roadmap-complete.md` §"the contextual bandit" specifies this as the platform's anchor reward signal — *"This directly measures what the platform is for."*
- **Y_1..Y_7** are the seven GLP friction components: Y1 temporal engagement, Y2 error trajectory coherence, Y3 cross-context transfer, Y4 uncertainty calibration, Y5 social knowledge texture, Y6 retrieval strength decay, Y7 scaffolding response curve. These are specified in detail in Appendix C (the GLP technical specification) and reconstructed in `05-the-measurement-layer_notes.md` §A; the appendix here treats them as named inputs.
- **w_d, w_1..w_7** are the reward function weights. **The right weights are open bet #6 of the book's eight open bets** (Ch 11 enumerates them; `07-the-adaptive-engine_notes.md` §E.3 names this directly).

Two implementation notes:

1. **Initial weights from the evidence base.** The Ch 3 evidence audit produces informed priors. Roediger & Karpicke 2006 / Cepeda 2006/2008 / FSRS empirical fit license heavy weight on D_7 for factual concepts. Thistlethwaite 2012 BEME synthesis licenses moderate weight on Y3 (cross-context transfer) for application-level concepts. Bastani et al. 2025 PNAS licenses a *negative* weight on the engagement-correlated tail of Y1 (i.e., long session time without commensurate Y4 calibration improvement should *reduce* reward, not increase it). The platform team should publish the initial weight vector and update it transparently — drift in the weight history is the auditable signal that the engine is staying honest.
2. **The latency between action and reward is the bandit's hardest engineering problem.** D_7 arrives seven days late. The seven-component Y signal arrives within-session. The implementation has two reward-update streams operating on different schedules; the policy update has to handle both. `07-the-adaptive-engine_notes.md` §M (Still puzzling) names this honestly — it is open even at the chapter level.

---

## C. Exploration strategy — Thompson Sampling, UCB1, ε-greedy, LinUCB

### C.1 The three textbook algorithms

From Sutton & Barto Ch 2 (`_lib_reinforcement_learning_an_introduction.md`):

- **ε-greedy.** With probability 1−ε, pull the arm with the highest current estimated mean reward; with probability ε, pull a random arm. Simple, interpretable, no convergence guarantee under constant ε (the standard fix is decaying ε_t = c/t or similar). Empirically often hard to beat in practice ([Vermorel & Mohri 2005, "Multi-armed Bandit Algorithms and Empirical Evaluation"](https://link.springer.com/chapter/10.1007/11564096_42) — `[verify]` — finds simple ε-greedy outperforms more sophisticated algorithms on most settings).
- **UCB1** (Auer, Cesa-Bianchi & Fischer 2002, *Machine Learning* 47: 235–256, DOI 10.1023/A:1013689704352 `[verify pagination]`). Pull arm *i* maximising `mean_i + sqrt(2 ln(t) / n_i)`. Provably O(log t) regret. Assumes stationary rewards. UCB1 was designed for the non-contextual bandit; extension to the contextual case is LinUCB.
- **Thompson Sampling** (Thompson 1933, *Biometrika* 25(3–4): 285–294, the original; modern revival Russo, Van Roy, Kazerouni, Osband & Wen 2018, *Foundations and Trends in Machine Learning* "A Tutorial on Thompson Sampling" `[verify]`). Maintain a posterior over each arm's expected reward; at each step, sample one realisation from each arm's posterior and pull the arm with the highest sample. Bayesian-interpretable, extends naturally to contextual rewards, handles non-stationarity through the prior.

### C.2 LinUCB — the contextual bandit baseline

The Medhavy bandit is *contextual*. The textbook ε-greedy / UCB1 / Thompson algorithms are stateless — they ignore the context vector x_{l,c,t} entirely. The standard production contextual bandit is **LinUCB** (Li, Chu, Langford & Schapire, 2010, "A Contextual-Bandit Approach to Personalized News Article Recommendation," *Proc. WWW 2010* — [arXiv:1003.0146](https://arxiv.org/abs/1003.0146)). LinUCB models the expected reward of arm *a* given context *x* as a linear function θ_a · x and maintains a per-arm covariance matrix that produces an exploration bonus shrinking as the arm is sampled more in similar contexts.

LinUCB is the canonical citation the developer will look for when reading "contextual bandit" in this appendix. The appendix should name it explicitly. The Medhavy team's proposed implementation (Thompson Sampling) is the **Bayesian sibling** of LinUCB — sometimes called *Linear Thompson Sampling* or *Bayesian linear contextual bandit*. Agrawal & Goyal 2013 ("Thompson Sampling for Contextual Bandits with Linear Payoffs," *ICML 2013*) `[verify]` proved regret bounds for Thompson Sampling in the contextual setting comparable to LinUCB's.

### C.3 The empirical comparison literature — what the field actually finds

The empirical comparison literature on the three algorithms in production settings, as of 2024–2026:

- **Thompson Sampling outperforms UCB1 in most real-world deployments.** Chapelle & Li 2011 ("An Empirical Evaluation of Thompson Sampling," *NIPS 2011*) is the canonical empirical paper. Thompson Sampling has matched or beaten UCB1 in nearly every published industrial bandit deployment (Yahoo, Microsoft, Netflix).
- **ε-greedy is competitive in practice.** [Vermorel & Mohri 2005](https://link.springer.com/chapter/10.1007/11564096_42) is the early result; many recent comparisons replicate this (e.g., [Towards Data Science empirical comparison](https://towardsdatascience.com/a-comparison-of-bandit-algorithms-24b4adfcabb/)). Simple heuristics with carefully chosen ε frequently outperform sophisticated theoretical algorithms on real datasets. The 2024 ε-Exploring Thompson Sampling (ε-TS) hybrid (Jin et al.) combines the two and reports better regret bounds than vanilla TS `[verify]`.
- **UCB1 underperforms in many empirical comparisons.** Multiple recent papers ([ResearchGate 2024 empirical comparison](https://www.researchgate.net/publication/385430456_Performance_Comparison_of_UCB_TS_and_-Greedy_TS_Algorithms_through_Simulation_of_Multi-Armed_Bandit_Machine); [extremelearning.com.au comparison](https://extremelearning.com.au/improving-ucb1-algorithm/)) show UCB1 trailing both Thompson Sampling and well-tuned ε-greedy at moderate sample sizes (n < 5,000). The "with 100 sockets both the UCB and Optimistic Greedy algorithms perform worse than the Epsilon Greedy algorithm" finding from a recent comparison is representative — UCB1's exploration bonus dominates when n is small and dominates again when n is very large but is poorly calibrated in the intermediate regime that matters most for production.
- **Educational-bandit-specific empirical work is thinner than the field would want.** The two most-cited papers on educational bandits — Clement, Roy, Oudeyer & Lopes 2015 ("Multi-Armed Bandits for Intelligent Tutoring Systems") and [Lan & Baraniuk 2016, "A Contextual Bandits Framework for Personalized Learning Action Selection," EDM](https://people.umass.edu/~andrewlan/papers/16edm-bandits.pdf) — establish that contextual bandits *work* for ITS personalisation but do not provide head-to-head comparisons of Thompson Sampling vs. UCB1 vs. ε-greedy on educational reward signals. The current empirical evidence base in EdTech is weaker than the production-systems literature.

### C.4 Why Thompson Sampling for Medhavy — the rationale, defended

`medhavy-1.5-feature-roadmap-complete.md` Appendix names Thompson Sampling as the proposed implementation. `07-the-adaptive-engine_notes.md` §C.3 defends the choice. The appendix should land the rationale in four reasons:

1. **Thompson Sampling extends to contextual bandits cleanly.** The Bayesian linear regression structure (one posterior per arm over the weight vector θ_a) is the same shape as LinUCB, which means the engineering effort is the same. The platform is not paying a complexity tax for the algorithm choice.
2. **Thompson Sampling handles non-stationarity through the prior.** A learner's expected return from Quiz Me changes as their FSRS state on a card matures — the Medhavy bandit is *technically* a non-stationary contextual bandit (`07-the-adaptive-engine_notes.md` §C.2). UCB1 assumes stationary rewards; the deployment-time fix (sliding-window UCB, discount factors) is a hack. Thompson Sampling's posterior decay (via discount factor on the precision matrix, or via prior re-injection) is the principled non-stationary update.
3. **The Bayesian semantics are the discipline the engagement-trap defence requires.** `07-the-adaptive-engine_notes.md` §E.2 is the chapter's emotional centre — the casino owner watching through the security camera. Thompson Sampling's posterior is *honestly uncertain* — it doesn't pretend to know which arm is best; it samples from its current belief and updates. The Bayesian framing (`_lib_everything-is-predictable_-how-bayesian-statistics-explain-our-world.md`) maps cleanly onto the "prior weights from evidence base, posterior from deployment data" architecture that the chapter argues for. The algorithm choice and the philosophical commitment are the same choice.
4. **The within-learner discipline benefits from posterior priors.** Each learner is their own experiment. The platform's prior over (mode | concept | Bloom-level) supplies the cold-start informed prior; the per-learner posterior accumulates as sessions accumulate. This is the natural shape for hierarchical Bayesian modelling — the population-level posterior informs each learner-level prior — which makes the cold-start cost (§D below) much smaller than it would be under cross-learner pooling.

**The honest counter-argument** the appendix should name: a randomised comparison of Thompson Sampling against well-tuned ε-greedy on the actual Medhavy deployment, on the actual reward signal, has not been run. The 2025 empirical literature on educational bandits is thin enough that the choice is partly evidence-based and partly bet. `07-the-adaptive-engine_notes.md` §L names this as a candidate "what would change my mind" trigger: *a randomised comparison of Thompson Sampling against a much simpler ε-greedy on the Medhavy deployment showing no statistical advantage to Thompson — that would argue for the simpler algorithm, since the simplicity carries deployment-discipline benefits the more complex algorithm lacks.*

---

## D. Cold start — what the engine does for a new learner

### D.1 The cold-start problem, named precisely

A new Medhavy learner arrives with **no within-learner posterior**. The Bayesian linear contextual bandit has nothing to update; its first action is sampled from the **prior** over per-arm reward distributions. Under within-learner generalisation (the design choice Ch 7 argues for), every new learner re-incurs this cost.

The cost is real:

- **The first session has near-uniform mode allocation** within the curriculum-layer flags. The bandit's posterior is the prior; the prior gives no preference among approved arms.
- **Convergence requires sessions.** `07-the-adaptive-engine_notes.md` §D.2 estimates the bandit needs "5–10 sessions" before its mode selection begins to differentiate from random. The exact convergence rate depends on the variance of the reward signal (which depends on the GLP scoring infrastructure's reliability — Ch 5's load-bearing concern).
- **For a learner using the platform for a single semester, the bandit may still be exploring at term's end.** The appendix should be honest about this. It is open bet #3 in the eight open bets (or arguably a ninth bet — `07-the-adaptive-engine_notes.md` §G.7 raises the bookkeeping question).

### D.2 Cold-start strategies — three families, recommended one

The literature on cold-start in contextual bandits offers three families of solution (synthesised from [Pal & Mukherjee 2025 on bug-cold-start contextual MAB](https://link.springer.com/article/10.1007/s10515-025-00508-6); [Bouneffouf, Bouzeghoub & Gancarski 2014, arXiv:1405.7544](https://arxiv.org/abs/1405.7544); [BiUCB 2017 IEEE](https://ieeexplore.ieee.org/document/8023425/); [cluster-based bandits for cold-start, SIGIR 2021](https://dl.acm.org/doi/abs/10.1145/3404835.3463033); [transferable contextual bandits with prior observations](https://par.nsf.gov/servlets/purl/10282308); [Bayley et al. 2025 LLM-initialised bandits under noisy priors](https://genai-personalization.github.io/assets/papers/GenAIRecP2025/7_Bayley.pdf)):

1. **Uniform-random allocation for K sessions.** The simplest fallback. The bandit explores uniformly across approved arms for the first K sessions (typical K = 5–10), then switches to its updated policy. Easy to implement; predictable cold-start behaviour; produces noisy but unbiased reward observations across all arms.
2. **Evidence-based informed prior.** The platform team specifies the prior parameters from the Ch 3 evidence base. For example: the per-arm prior on the Quiz Me return for a learner on a factual-recall concept is centred on Roediger & Karpicke 2006's effect size; the per-arm prior on Glimmer for a novice on a complex concept is centred *low* with high variance to reflect the anxiety failure mode (Jonassen 1997 / Fiorella & Mayer 2016). The bandit's first-session selection is then a Thompson sample from these evidence-based priors, not uniform.
3. **Pedagogy.default fallback.** `PEDAGOGY ARCHITECTURE.txt` §4 names this explicitly: *"A new learner has no interaction history. The bandit has nothing to update. The system falls back to the pedagogy.default value in the tenant registry — typically direct instruction, because it is the lowest-risk approach when prior knowledge is unknown. After two or three sessions, the bandit has enough signal to start differentiating."* This is the **current Medhavy 1.0 / 1.5 production behaviour**.

**Recommendation for the appendix:** Medhavy 2.0 should implement option (2) — the evidence-based informed prior — with option (3) (pedagogy.default) as the hard fallback for the *very first session* of the very first concept a learner encounters. Option (1) (uniform random) is the wrong default because the evidence base already licenses a non-uniform prior; ignoring that licence is throwing away information.

The implementation specification:

- **Session 1.** Sample from the per-arm evidence-based prior conditioned on the curriculum layer's Bloom-level tag for the concept. For Bloom-level Remember / Understand: prior centred on Quiz Me with moderate weight on Ask AI. For Apply / Analyze: centred on Case Study. For Create: centred on Glimmer with high prior variance (the anxiety failure mode is the consequential downside).
- **Sessions 2–5.** Bandit operates with the updated per-learner posterior. Variance is still high; allocation is still close to the prior; the engine is *learning the learner*.
- **Session 6+.** The per-learner posterior begins to dominate the prior. The bandit's allocation begins to differentiate meaningfully across learners.

The appendix should name the convergence-rate honestly: **within-learner convergence is slow on purpose, because the alternative (cross-learner pooling) requires the population-similarity assumption that the architecture exists to refuse.**

### D.3 Hierarchical Bayesian sharpening — the recommended cold-start refinement

A refinement the appendix should propose for the developer: **hierarchical priors**. The platform-level posterior over reward function weights (informed by all learners' deployment data, marginalised over individuals) becomes the prior for each new learner's per-learner posterior. This is the standard hierarchical Bayesian construction (Gelman et al. *Bayesian Data Analysis* Ch 5 `[verify]`).

The hierarchical sharpening preserves the within-learner discipline — each learner's *posterior* is still per-learner — while reducing the cold-start cost by **informing the prior from the population**. This is *not* cross-learner generalisation in the sense Ch 7 critiques (the population mean does not get applied to individuals); it is *prior sharpening* from population data. The distinction matters because the architecture is committed to within-learner adaptation, and hierarchical priors are the way to make within-learner adaptation tractable at one-semester time horizons without violating the commitment.

**Implementation note:** the hierarchical update can be applied per concept-Bloom-level cell. Quiz Me's prior for a Remember-level concept is updated separately from Quiz Me's prior for an Apply-level concept. The platform's per-cell posterior over (arm | Bloom-level | concept-class) becomes the prior for each new learner's per-learner per-cell posterior. The architecture is bandit-on-top-of-hierarchical-Bayesian-regression, not a flat contextual bandit.

---

## E. Update mechanics — what happens at end of session

### E.1 The two reward streams

The Medhavy bandit has **two reward update streams** operating on different schedules:

1. **Within-session GLP composite.** At session end (time *t*), the seven GLP components Y_1..Y_7 are computed for the session that just completed. The composite within-session reward `R_within = Σ_i w_i · Y_i` is computed. The bandit's posterior over (θ_a | x_{l,c,t}) is updated with the observation `(arm = m, x = x_{l,c,t}, reward = R_within)`. This update happens immediately at session end.
2. **Seven-day delayed retrieval probe.** At time *t + 7 days*, a new Quiz Me item on concept *c* is presented to learner *l*. The accuracy on that item produces `D_7 ∈ {0, 1}`. The bandit's posterior is *re-updated* with the observation `(arm = m_{previous}, x = x_{l,c,t}, reward = w_d · D_7)`. This is a delayed update on the same decision the within-session update already processed.

The two updates compose: the bandit's posterior over θ_a is the conjunction of all within-session and delayed-probe observations the platform has accumulated for learner *l*. The seven-day delayed update can be implemented as a Bayesian posterior update with a delayed observation — there is no methodological complication, just an engineering one (the platform has to remember every decision for at least seven days and route the delayed-probe observation back to the right decision).

### E.2 Pseudocode — what the developer is implementing

A skeleton of the per-session update loop, for the developer who wants to verify they have understood the appendix:

```
on session_end(learner_l, concept_c, mode_m, session_t):
    # 1. Compute within-session GLP components
    Y_1, ..., Y_7 = compute_glp_components(session_log)
    R_within = sum(w_i * Y_i for i in 1..7)
    
    # 2. Schedule the delayed-probe
    schedule_probe(learner_l, concept_c, mode_m, session_t, due_at = t + 7 days)
    
    # 3. Update the per-learner per-arm posterior (Thompson Sampling, Bayesian linear)
    x = build_context_vector(learner_l, concept_c, session_t)
    posterior[mode_m].update(x, R_within)
    
    # 4. Log to the analytical-log discipline (MVAL, see §F)
    log_mval_entry(WHAT=..., WHY=..., HOW=..., 
                   ENVIRONMENT=..., RESULTS=R_within, QUESTIONS=...)
    
    # 5. Audit hook
    if drift_audit_due():
        flag_weight_history_for_review()

on delayed_probe_complete(learner_l, concept_c, mode_m, session_t, D_7):
    x = recall_context_vector_at(learner_l, concept_c, session_t)
    posterior[mode_m].update(x, w_d * D_7)
    # Same posterior update structure as within-session; delayed observation
```

The two posterior updates compose linearly — that is the load-bearing benefit of the linear (Bayesian regression) parameterisation. Sample-efficiency depends on the prior strength (informed via §D's evidence-based prior) and the within-session signal reliability (Ch 5's measurement layer responsibility).

### E.3 Mode-selection at session start

The complementary loop, for completeness:

```
on session_start(learner_l, concept_c):
    eligible_arms = curriculum_layer.mode_flags(concept_c, learner_l.bloom_level)
    x = build_context_vector(learner_l, concept_c, now())
    samples = {m: posterior[m].sample(x) for m in eligible_arms}
    selected_mode = argmax(samples)
    return selected_mode
```

Thompson Sampling at its operational simplest: sample once per arm from the per-arm Bayesian-regression posterior, pull the arm with the highest sample. The `posterior[m].sample(x)` call returns a draw from the marginal posterior over expected reward conditioned on context. For a Bayesian linear regression posterior over θ_m, the marginal posterior over θ_m · x at a new context x is Gaussian with computable mean and variance — sampling is one Cholesky solve.

---

## F. The audit discipline — MVAL as the analytical-log standard, *not* a value metric

`MVAL.txt` is **not** the platform's internal value metric (TIKTOC §App D appears to misname it). MVAL is the **Minimum Viable Analytical Log** protocol: a six-field discipline (WHAT, WHY, HOW, ENVIRONMENT, RESULTS, QUESTIONS) that every research log entry must contain. The protocol is reviewed by "Dev the Dev" and is documented in `MVAL.txt` v1.1 (March 2026).

The appendix should still discuss MVAL — but as the **audit discipline that produces the data the bandit's offline evaluation requires**, not as a value metric.

The connection to the bandit:

1. **The reward function is auditable.** Every weight update, every shift in the per-learner posterior, every drift in the population-level prior — all are logged with the MVAL six-field discipline. The platform team can answer the question *"why does this learner's posterior now favour Glimmer for application-level concepts?"* by inspecting the MVAL entries that wrote the posterior updates.
2. **Failures are not optional entries.** `MVAL.txt`'s Failure Artifact Protocol: *"A failed experiment that is not logged is worse than a failed experiment — it is a failed experiment that will be repeated."* For the bandit, this means: a session in which the engine's mode selection produced obvious underperformance gets logged with the same rigour as a successful session. The drift audit (the platform's defence against the engagement trap) consumes both classes of entries.
3. **The closure illusion is the bandit's failure mode.** MVAL's discipline against the "done = no open questions" failure maps directly onto the bandit's most dangerous failure mode: convergence to a policy that the platform team has stopped questioning. A bandit whose reward weights have drifted toward an engagement-shaped signal is *exactly* the case MVAL's QUESTIONS field exists to surface — the platform team should be writing, every audit cycle, "is the current reward function still measuring what we said it measures?"

**Appendix-level recommendation:** the developer implementing the bandit should treat the MVAL log-entry generator as a load-bearing piece of the bandit's deployment infrastructure, not as a research nice-to-have. The bandit without the audit is the engine that drifts silently.

---

## G. Open bets, named precisely

The chapter author (Ch 7) names six bets that touch the engine; the appendix consolidates them with implementation-implication tags.

| # | Bet | Implementation implication |
|---|-----|---------------------------|
| 1 | Right weights for w_d, w_1..w_7 | The deployed weight vector is published and audited; updates are logged via MVAL; the platform team commits to publishing weight history on a deployment-defined cadence |
| 2 | Within-learner convergence rate | The cold-start strategy (§D) is the implementation lever; if the per-learner posterior fails to converge inside one semester, the hierarchical sharpening (§D.3) is the fallback |
| 3 | GLP-as-reward signal fidelity | The Ch 5 measurement layer is the binding constraint; the bandit cannot exceed the reliability of the signal it consumes |
| 4 | Thompson Sampling vs. ε-greedy on Medhavy | The deployment should include a randomised holdout running ε-greedy as a comparator; this is the only way to test the algorithm choice empirically |
| 5 | Coupled-arms problem | The bandit framing treats arms as independent; in reality a Glimmer session changes the representation Quiz Me operates on; the implementation can ignore this initially but should plan for a POMDP-style refinement |
| 6 | Delayed-reward balance | The relative weight of within-session Y composite vs. seven-day D_7 is the load-bearing tuning parameter; the cold-start prior on these weights should come from the evidence base, the deployed posterior should be auditable |

The appendix should be honest about which of these can be settled by implementation choices, which by deployment data, and which require external evidence the platform cannot itself generate.

---

## H. Cross-reference to existing pantry — cite by exact filename

The appendix should cite by filename, not re-research the underlying ground:

- `07-the-adaptive-engine_notes.md` — primary source for the entire technical reconstruction (6,245 words). The appendix is a tighter, implementation-focused version of this note; it should not re-argue the within-learner vs. cross-learner design choice (that is the chapter's job).
- `medhavy-1.5-feature-roadmap-complete.md` — primary source for the platform's specification of Thompson Sampling as the implementation choice, the seven-day delayed retrieval reward, and the context vector composition (§"Appendix — Medhavy 2.0").
- `PEDAGOGY ARCHITECTURE.txt` — primary source for the bandit selection mechanism as currently specified in Medhavy 1.0 (§4), the cold-start `pedagogy.default` fallback, and the honest acknowledgment that the current outcome signals are engagement proxies that need to be replaced with GLP.
- `MVAL.txt` — the analytical-log discipline (§F above). Note the TIKTOC misnomer and the §F reframing.
- `concept-sequencing-research.md` — BKT/DKT for the prerequisite-mastery context features (§2.1); Pavlik & Anderson 2008 for the gain-per-minute objective function (§3.4); the functional-form discussion (§6.2) for the reward function's linear-combination shape.
- `_lib_reinforcement_learning_an_introduction.md` — Sutton & Barto Ch 2 as the canonical bandit reference; ε-greedy, UCB1, and the 10-armed testbed.
- `_lib_everything-is-predictable_-how-bayesian-statistics-explain-our-world.md` — the Bayesian framing for Thompson Sampling and for the prior-posterior structure of within-learner convergence.
- `ask-ai-research.md` — Bastani 2025 as the canonical cautionary data point on engagement-style optimisation; the negative weight on the engagement-correlated tail of Y1 in the reward function.

The appendix should *not* re-cite primary sources already established in Ch 7. The chapter argues; the appendix implements.

---

## I. Gaps, flags, verify items

### I.1 Top flags for the appendix author

1. **`Contextual Bandits.txt` does not exist in pantry.** TIKTOC names it; the file is not present. Action: confirm with Nik whether to copy from a private location, or approve §B–§E above as canonical reconstruction. (Already raised as flag #1 above.)
2. **MVAL is misnamed in TIKTOC §App D.** It is the analytical-log protocol, not a value metric. Action: confirm reframing in §F. (Already raised as flag #2 above.)
3. **Robert C. Gray bandit reference (Ch 7 carryover).** Pantry README flag #7. The appendix should *not* cite Gray; the bandit framing in this appendix is drawn from Sutton & Barto and the production-systems literature (Chapelle & Li, Russo et al., Agrawal & Goyal, Li-Chu-Langford-Schapire).
4. **Auer, Cesa-Bianchi & Fischer 2002 pagination.** Standard citation; verify pagination before final draft.
5. **Russo, Van Roy, Kazerouni, Osband & Wen 2018 *FnT in ML* — exact volume and pagination.** Standard Thompson Sampling tutorial reference; verify.
6. **Agrawal & Goyal 2013 ICML.** Standard contextual TS reference; verify.
7. **The ε-Exploring Thompson Sampling 2024 reference.** Cited from the Towards Data Science empirical comparison; the underlying paper (Jin et al.) should be located and verified before naming the result in the appendix.

### I.2 Open questions for the appendix to surface (not resolve)

- **Coupled-arms / POMDP refinement.** The textbook bandit treats arms as independent; the modes are not. The appendix should name this as a known limitation and as a candidate refinement for a future Medhavy 3.0.
- **Delayed-reward weighting.** The relative weight of within-session signal vs. seven-day probe is one of the platform's binding tuning parameters; the appendix should name it as an open bet.
- **Hierarchical prior governance.** The recommended hierarchical Bayesian construction (§D.3) raises a governance question: who updates the population-level posterior, on what cadence, with what audit gate? The platform team should specify this in deployment documentation; the appendix should flag the unresolved governance question.
- **The MVAL-bandit coupling.** The audit discipline depends on the bandit team running MVAL logs at session-update granularity. This is a substantial engineering commitment; the appendix should be honest that the audit only works if the discipline is enforced.

### I.3 What would change the reading

The appendix's recommendations would substantively revise if:

- A deployment-scale randomised comparison of Thompson Sampling against ε-greedy on the Medhavy 2.0 platform showed no statistical advantage to Thompson at six-month follow-up. *That* would argue for ε-greedy as the deployed default (simplicity carries deployment-discipline benefits the more complex algorithm lacks).
- The hierarchical Bayesian construction (§D.3) failed to converge the per-learner posterior within one semester even with population-level prior sharpening. *That* would argue for either (a) cross-learner pooling as the engineering default with within-learner posterior as a refinement, or (b) accepting noisier adaptation with explicit user-facing communication ("the engine is still learning you").
- An audit of the reward function weight history revealed that the platform's deployed weights had drifted toward engagement-shaped signals despite the architectural commitment. *That* would force a redesign of either the audit discipline or the reward function itself.

---

## J. Suggested appendix shape — section-by-section word allocation

Recommended internal allocation for the appendix author (target 4,000–5,500 words):

- §A Scope (200 words)
- §B Bandit formulation — arms, context, reward (~900 words)
- §C Exploration strategy — TS / UCB1 / ε-greedy / LinUCB, with the rationale (~900 words)
- §D Cold start — three strategies, hierarchical refinement, recommendation (~700 words)
- §E Update mechanics — pseudocode, two reward streams, mode selection (~700 words)
- §F MVAL as audit discipline (with the TIKTOC misnomer flagged) (~400 words)
- §G Open bets (~400 words)
- §H–§I Cross-references + flags + still-puzzling (~400 words)

Total: ~4,600 words. Within the 4,000–5,500 target.

---

## K. Connection to other appendices

- **Appendix C (GLP Technical Specification)** supplies the Y_1..Y_7 components the reward function consumes. The bandit appendix should reference Appendix C for the formal specification rather than reconstruct it.
- **Appendix E (Medhavi Hub Architecture)** specifies the database schema where the per-learner posterior is persisted, the API surface that publishes the engine's mode selection, and the analytics tables that hold the MVAL log entries. The bandit appendix and the architecture appendix are intentionally complementary — the bandit specifies *what* gets stored and updated; the architecture specifies *where* and *how*.
- **Appendix B (Causal Knowledge Graph)** supplies the prior on which interventions work for which outcomes — i.e., the evidence base that informs the per-arm cold-start prior in §D. The Hattie-DAG framing gives the appendix a principled source for the initial weight vector.

---

*End of Appendix D research note. ~4,700 words. Next step: hand to Cowork for compilation as `books/medhavy/chapters/D-contextual-bandits.md`.*
