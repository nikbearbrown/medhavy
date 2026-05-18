# Research Notes — Appendix B: The Causal Knowledge Graph: Mapping What Works

*Research note for the Medhavy book project. Compiled 2026-05-17 for the appendix-writer pipeline. Author: research subagent for Nik Bear Brown.*

*This appendix is the most research-heavy of the five — it sits at the intersection of the Hattie corpus, Pearl's causal-inference framework, and a piece of internal Medhavy architecture (the "Adherence Classifier") that does not yet have public-facing documentation. The appendix's intellectual ancestors are the in-pantry `Causal Graphs_ A Testable Architecture for Pedagogical Research Using AI-Mediated Instruction.txt` (the primary source, hereafter "the Causal Graphs draft") and the Chernozhukov–Hansen–Kallus–Spindler–Syrgkanis *Applied Causal Inference Powered by ML and AI* textbook (the canonical DAG / SEM reference in pantry).*

---

## A. Concept under examination — what the appendix teaches

The reader arrives at Appendix B having read the architecture (Chapters 4–9) and the open-questions chapter (Chapter 11). They know that the adaptive engine (Chapter 7) is a contextual bandit whose reward weights have to come from somewhere. They know that the curriculum design layer (Chapter 8) supplies the prerequisite structure. They know that the measurement layer (Chapter 5) supplies the seven Y-component GLP signal. What they do not yet know is *where the engine's prior on which-intervention-helps-when comes from*, and *how the platform protects itself from confusing "delivered the intervention" with "the intervention worked."*

Appendix B teaches three things and is expected to leave the reader able to use them:

1. **What the Hattie corpus is and is not.** *Visible Learning* in its 2026 form is the Visible Learning MetaX database, a continuously updated synthesis of ~2,100 meta-analyses covering ~132,000 individual studies and ~300 million students worldwide ([visiblelearningmetax.com](https://www.visiblelearningmetax.com/research_methodology); [Corwin/Sage press release](https://uk.sagepub.com/en-gb/eur/press/corwin-launches-visible-learningtm-metax-platform-the-largest-global-database-of-evidence)). The classic 252-influence ranking ([visible-learning.org](https://visible-learning.org/hattie-ranking-influences-effect-sizes-learning-achievement/)) is the public-facing summary; the platform itself catalogues 320+ factors as of the 2023 *Visible Learning: The Sequel* edition. The 0.40 hinge point is *not* a sharp decision boundary; it is the average effect across the database. The reader should leave §A able to say: *the corpus is a ranked list of associations; the appendix's job is to turn it into a graph of testable causes.*
2. **The Intervention / Diagnostic / Context taxonomy.** Hattie's variables are not the same kind of object. Some are things a platform can *do* (corrective feedback, worked examples, retrieval practice — *interventions*). Some are things a platform can *measure* but not directly manipulate (prior knowledge, self-efficacy, metacognitive monitoring — *diagnostics* or *intermediate states*). Some are background conditions the platform must *condition on* but cannot alter (socioeconomic status, classroom climate, prior schooling — *context*). The flat ranked list hides these distinctions; the taxonomy makes them visible. The categorization is the move that converts effect-size rankings into a DAG.
3. **What the Adherence Classifier adds — and why.** The Causal Graphs draft names the engineering problem: stochastic LLM output makes treatment definition feel impossible, but treatment can be re-recovered post-hoc by *classifying what was actually delivered*. The Adherence Classifier is the architectural commitment to that move. It is the layer that turns "the engine called for high-specificity corrective feedback" into a verified, codeable fact about what the chatbot actually produced. Without it, the bandit is updating its policy on what it *intended* to do, not on what it *did*. The classifier is how SUTVA-by-design is recovered from a stochastic policy executor.

The appendix's Bloom's level is Analyze. The reader should be able to look at a vendor's claimed personalization scheme and ask: *what taxonomy of variables are you using; which edges in your graph are confirmed and which are merely plausible; how are you verifying that your treatments are actually being delivered as specified?*

---

## B. Specification move — pulling apart vague terms

This is where the appendix should spend effort, because every term in the appendix's title is doing too much work.

- **Causal Knowledge Graph.** Vendor usage often means "a knowledge graph of educational facts plus some arrows." In the appendix's sense, it is something narrower and stronger: a directed acyclic graph in Pearl's sense ([Pearl 2009, *Causality*](https://www.cambridge.org/core/books/causality/B0046844FAE10CBF274D4ACBDAEB5F5B); [Chernozhukov et al. textbook §6.2 and §7.2 in pantry](file:///pantry/_lib_applied-causal-inference-powered-by-ml-and-ai.md)), with nodes for variables and edges encoding hypothesized causal influence — *and* an annotation on each edge specifying whether the mechanism is convergent in the literature, contested between competing mechanisms, or under suspicion of being a reversed (outcome-as-cause) relationship.
- **Mapping what works.** "What works" is the slogan of evidence-based education (the What Works Clearinghouse, the EEF Toolkit, Hattie's own ranking) and it hides the question *works at what, for whom, in which sequence, conditional on what else?* The flat-list "what works" answer is the very thing the appendix is trying to replace with a structured "what causes what, under which conditions" answer.
- **Intervention.** Specifically: a *manipulable* policy that the platform can execute consistently across learners. "Feedback" is not an intervention specification. "Corrective feedback delivered within 30 seconds of error detection, referencing the specific success criterion violated, with one example of the correct approach" is. This is the operational-definition move from the Causal Graphs draft §3.1 — and it is the move every node has to pass before it earns its place as an *intervention node* rather than a *diagnostic* or *context* node.
- **Diagnostic.** A variable the platform can measure but not directly set. Prior knowledge is the canonical example — the platform can elicit it via a calibration quiz, but cannot *make* it true. Self-efficacy is a diagnostic — measurable via confidence ratings or behavioral proxies, but not directly intervened on. Diagnostics are read inputs to the bandit's context vector; they are not arms.
- **Context.** Variables that influence outcomes but sit outside the platform's manipulable surface — socioeconomic status, school climate, hours of sleep, parental education. These are conditioned-on backdoor candidates in Pearl's sense ([Chernozhukov et al. §7.3](file:///pantry/_lib_applied-causal-inference-powered-by-ml-and-ai.md)). The platform's job is to ensure its inferences are not confounded by them — not to change them.
- **Adherence Classifier.** A specific architecture: a downstream model (probably an LLM-based judge with a calibrated rubric) that, given a logged tutor–student interaction and a *treatment specification*, returns a score along several dimensions: was the specification delivered? How well? Where did the delivery deviate? Crucially: was the dimension the bandit was experimentally manipulating (e.g., feedback specificity) actually expressed in the realized utterance, and not corrupted by some other dimension (e.g., feedback warmth) that covaries in untyped LLM output? The classifier is to LLM-mediated education what an *implementation fidelity coder* is to a classroom RCT ([Iowa Reading Research Center 2024](https://irrc.education.uiowa.edu/blog/2024/11/how-does-fidelity-implementation-relate-student-reading-outcomes); [Michigan Education Corps 2023](https://mieducationcorps.org/2023/10/27/fidelity-in-education/)) — except that it can run on every interaction at scale.

The reader must leave §B able to say: *Hattie's ranked variables are not all the same kind of thing; the appendix's first job is to sort them by manipulability; the second is to specify a graph; the third is to put a fidelity check between policy and reward.*

---

## C. The Hattie corpus — what it is, what it isn't `[primary-source-heavy]`

### C.1 The current state of the database

The number to use, anchored to the public MetaX research-methodology page:

> "Visible Learning research examines and synthesizes more than 2,100 meta-analyses comprising more than 132,000 studies involving 300 million students around the world" ([visiblelearningmetax.com/research_methodology](https://www.visiblelearningmetax.com/research_methodology); [Corwin Visible Learning MetaX press release, SAGE](https://uk.sagepub.com/en-gb/eur/press/corwin-launches-visible-learningtm-metax-platform-the-largest-global-database-of-evidence)).

The public ranked list at the Visible Learning Plus site is currently **252 influences** ([visible-learning.org Hattie ranking](https://visible-learning.org/hattie-ranking-influences-effect-sizes-learning-achievement/)) — last bulk-updated in 2023 to incorporate the *Visible Learning: The Sequel* (Routledge, 2023) data. *The Sequel* reports a synthesis of ~2,100 meta-analyses involving over 400 million students ([visible-learning.org/2023/01/visible-learning-the-sequel-2023/](https://visible-learning.org/2023/01/visible-learning-the-sequel-2023/); [Taylor & Francis monograph page](https://www.taylorfrancis.com/books/mono/10.4324/9781003380542/visible-learning-sequel-john-hattie)). MetaX is the continuously-updated platform that supersedes the static ranking — and as of 2026 the Visible Learning content team has been correcting errors in the MetaX entries on the fly (notably the February 2025 revision to the *Collective Teacher Efficacy* effect size, which drew critical commentary from Pedro De Bruyckere on [theeconomyofmeaning.com](https://theeconomyofmeaning.com/2025/02/08/did-the-effect-of-collective-teaching-efficacy-just-dropped-or-did-john-hatties-team-made-a-mistake/)).

**Recommended citation block for the appendix:**

> Hattie, J. (2023). *Visible learning: The sequel: A synthesis of over 2,100 meta-analyses relating to achievement*. Routledge. [ISBN 9781032462035](https://www.routledge.com/Visible-Learning-A-Synthesis-of-Over-800-Meta-Analyses-Relating-to-Achievement/Hattie/p/book/9780415476188). Continuously updated as Visible Learning MetaX, [visiblelearningmetax.com](https://www.visiblelearningmetax.com/) (accessed 2026-05-17).

The appendix should cite both the book (canonical version of record) and the MetaX platform (current state), because a non-trivial fraction of the appendix's reasoning depends on the *current* effect-size figure for a variable, not the 2009 or 2017 figure. The corpus is a moving target. This is honest reporting; pretending otherwise is the failure mode the Causal Graphs draft is reacting against.

### C.2 The 0.40 hinge — what it means and what it doesn't

The 0.40 hinge point originates in Hattie 2009 *Visible Learning* (Routledge), where 0.40 is reported as the *average* effect size across all the meta-analyses Hattie reviewed. Hattie translated 0.40 into "the effect typically achieved by one year of schooling" — a translation that has not survived close scrutiny ([Wecker et al. 2017](https://www.bzfe.de/inhalt/wecker-fischer-2017-37123.html) `[verify exact citation: Wecker, C., Vogel, F., & Hetmanek, A. (2017). Visualizing the effects of an effect-size hierarchy: A novel pitfall. *Zeitschrift für Erziehungswissenschaft* 20(2), 245–263]`; [ASCD: Interpreting Education Research and Effect Sizes](https://www.ascd.org/el/articles/interpreting-education-research-and-effect-sizes)).

The honest reading of the hinge, which the appendix should adopt:

- 0.40 is a *summary statistic* of an extremely heterogeneous database — not a decision threshold for practice.
- The hinge functions reasonably as a *cost-effectiveness guideline* (interventions that produce ≤0.40 at high cost are not good buys), but **never** as a binary classification rule.
- Below-0.40 effects can be very important in specific contexts: small effects on equity-relevant outcomes, small effects on rare but consequential events, small effects that compound across years.
- Above-0.40 effects can be artefactual: pre-post designs systematically inflate effect sizes (Kraft 2020, [*Educational Researcher* 49(4), 241–253](https://doi.org/10.3102/0013189X20912798) `[verify]`); short-window interventions with researcher-developed tests routinely outperform long-window interventions with standardized tests.

This is consistent with Chapter 3's treatment of the same point (see `03-the-evidence-base_notes.md` §A.3). The appendix should not re-litigate the hinge debate — it should establish that the appendix's project takes the corpus seriously as a hypothesis-generation source *without* treating the ranking as a verdict.

### C.3 Methodological critiques the appendix must acknowledge

Four critiques that the appendix should name briefly and then move past, since they motivate the move from rankings to graphs but do not need to be re-fought in full:

1. **The averaging-across-heterogeneous-meta-analyses critique** — Adrian Simpson's body of work, most prominently Simpson 2017 ([*Educational Researcher* 46(8), 425–432, DOI 10.3102/0013189X17738324](https://doi.org/10.3102/0013189X17738324)) and Simpson 2018 (*Review of Educational Research* 88(2)). Simpson's central argument: treating standardized effect sizes as universally comparable across designs, populations, outcomes, and retention intervals is a methodological error large enough to invalidate the ranking exercise. ([statmodeling.stat.columbia.edu/2018/09/01/john-hatties-visible-learning-much-trust-influential-review-education-research/](https://statmodeling.stat.columbia.edu/2018/09/01/john-hatties-visible-learning-much-trust-influential-review-education-research/) — Gelman's substack on the issue).
2. **The "pseudoscience" critique** — Bergeron & Rivard 2017 ([*McGill Journal of Education* 52(1), 237–246, ResearchGate PDF](https://www.researchgate.net/publication/325983161_A_critique_of_John_Hattie's_theory_of_Visible_Learning)). The argument: Hattie's selection of meta-analyses and effect-size combination decisions yield a corpus where positive effects are over-represented; Bergeron specifically critiques the *direction-flipping* convention (taking the absolute value of effects to ensure positive numbers) and the inclusion of small, unusual studies on equal footing with large RCTs.
3. **The statistical-mechanics critique** — Pierre-Jérôme Bergeron 2017 (and the related Topphol commentary; see `[verify Topphol citation: A.K. Topphol, 2012, on common language effect size errors]`) and the Snook et al. 2009 critique ([*New Zealand Journal of Educational Studies* 44(1)](https://www.researchgate.net/publication/249077017_Critic_of_Hattie's_book_Visible_Learning) `[verify exact pagination]`). Hattie himself acknowledged a calculation error in the *Common Language Effect* (CLE) figures throughout *Visible Learning* 2009; the Cohen's *d* values remain ([Wikipedia: Visible Learning](https://en.wikipedia.org/wiki/Visible_learning); Topphol 2012 in *Nordic Studies in Education*).
4. **The Nordic critique on educational theory** — Eacott in *Nordic Psychology* 73(3), 2021 ([DOI 10.1080/19012276.2021.1962731](https://www.tandfonline.com/doi/abs/10.1080/19012276.2021.1962731)). Argues the meta-analytic ranking project reduces complex educational phenomena to single-dimensional measurement, missing the constitutive role of context and meaning-making in learning.

The appendix should grant the critiques without granting the conclusion that the corpus is worthless. The corpus is the largest systematic synthesis of educational research in existence; it remains the right hypothesis-generation source for a DAG construction project. What the appendix changes is the *use* — from ranking-as-verdict to ranking-as-prior.

### C.4 The independence implication — the central methodological error

The Causal Graphs draft (in pantry) names this clearly:

> "A ranked list implies independence. It suggests that a school can select the top five interventions, implement them, and receive the sum of their effect sizes. This is not how educational causation works. A student's response to feedback depends on whether the feedback references criteria they understand — which depends on how clearly the teacher communicated learning intentions — which depends on whether the student believes the teacher is competent. These are not additive independent causes. They are a causal chain in which each link is a precondition for the next."

This is the appendix's central pedagogical move. The flat list is wrong not because the effect sizes are wrong but because the *implied model* — that variables act independently on the outcome — is wrong. A DAG makes the dependence structure explicit. Whether the dependence structure is correct is then a testable scientific question, not an assumption silently embedded in the visualization.

---

## D. The Intervention / Diagnostic / Context taxonomy — the appendix's main classification move

### D.1 Why the taxonomy

The Causal Graphs draft §3.1 names three criteria for node selection: manipulability, causal role, and temporal ordering. These three criteria sort the Hattie variables into the three taxonomy buckets the appendix is built around.

The taxonomy is not new in principle — Pearl's framework distinguishes manipulable variables (intervention candidates), mediating variables (intermediate states), and exogenous/context variables (conditioning candidates) ([Chernozhukov et al. §6.2 on DAGs and §7.2 on intervention; *Causality* Pearl 2009, Ch 3 on do-calculus](file:///pantry/_lib_applied-causal-inference-powered-by-ml-and-ai.md)). The appendix's contribution is applying this taxonomy systematically to the Visible Learning corpus, where the categorical distinction has historically been collapsed.

### D.2 The three categories, with example variables

**Intervention nodes.** Variables a platform or teacher can directly vary at the level of an instructional decision. Sortable Hattie variables: *Feedback* (d ≈ 0.72), *Teacher clarity* (d ≈ 0.75), *Worked examples* (d ≈ 0.57), *Spaced practice* (d ≈ 0.65), *Direct instruction* (d ≈ 0.59), *Goal setting* (d ≈ 0.50), *Reciprocal teaching* (d ≈ 0.74), *Mastery learning* (d ≈ 0.58), *Concept mapping* (d ≈ 0.64), *Retrieval practice* (d ≈ 0.50–0.70 depending on operationalization; the Hattie corpus underestimates the laboratory effect because the field deployments included are noisier than the Roediger & Karpicke laboratory work). These are the candidate arms or arm-features for an adaptive engine.

**Diagnostic nodes (intermediate / proximal-outcome states).** Variables the platform measures as state but cannot directly set. Sortable Hattie variables: *Self-efficacy* (d ≈ 0.92 — but probably a proximal outcome rather than a cause; the literature on Bandura's construct treats it as a mediator), *Metacognitive strategies* (d ≈ 0.60 — partly an intervention if it's taught, partly a diagnostic if it's measured), *Prior achievement* (d ≈ 0.65 — a diagnostic; you can't intervene on prior achievement, only on current instruction), *Student self-assessment* (d ≈ 1.33 — almost certainly a *reversed candidate* per the Causal Graphs draft §3.3; students who can accurately self-assess are students who have already learned the material).

**Context nodes (exogenous inputs).** Variables that condition outcomes but sit outside the platform's manipulable surface. Sortable Hattie variables: *Socioeconomic status* (d ≈ 0.52 — but this is a *correlate* of achievement, not an intervention on a school's part), *Prior knowledge* (d ≈ 0.94 — exogenous to the current instructional decision), *Collective teacher efficacy* (d ≈ 1.34 in Sequel; school-level, not learner-level — exogenous from the platform's perspective even if it is intervention-amenable for a school leader), *Class size* (d ≈ 0.21 — a context variable for a tutoring system that operates at *n* = 1 by design).

### D.3 Reversed candidates — the most consequential cleanup

The Hattie ranking contains several variables whose top-rank effect sizes are almost certainly artefacts of confusing outcomes with causes:

- *Self-reported grades / Student expectations* (d ≈ 1.33). Students who can accurately predict their grades have already learned the material. The variable is a *measure* of the outcome distribution, not a cause of it.
- *Student self-assessment* (d ≈ 1.33). Same issue: accurate self-assessment is downstream of mastery, not upstream of it.
- *Piagetian programs* (d ≈ 1.28). Almost certainly an artifact of selection — programs marketed under that name were delivered to populations selected for high motivation and prior knowledge.

The Causal Graphs draft §3.1 names these as *reversed candidates* and proposes removing them from the intervention set pending analysis. The appendix should adopt this convention and *show the move*: take the top-ranked variable (Student self-reported grades, d = 1.33), explain why ranking it as an intervention generates the *include-the-outcome-as-a-feature* collider error in any DAG, and remove it.

### D.4 The Adaptive Engine's reward-weight prior — what the taxonomy gives Chapter 7

The taxonomy is not just a cleanup move; it is the layer that produces the *informed prior* on the bandit's reward weights (cross-reference `07-the-adaptive-engine_notes.md` §E.1). Specifically:

- The intervention nodes become the arms or arm-features of the bandit (modes, mode-mode interactions, feedback specificity dials).
- The diagnostic nodes become the learner-state feature vector — the context the contextual bandit conditions on (the "wind speed" in the Sutton & Barto sense; see Chapter 7 §C.4).
- The context nodes become covariate adjustments — either conditioned on in the policy (the bandit's policy depends on them) or used as offsets in the reward-update (the engine does not give itself credit for learning gains that were already in the population).

The Hattie effect size for an intervention becomes the prior on its reward weight — *adjusted* for the manipulability move (only the intervention-class portion of the effect size makes it into the prior) and *conditioned on* the context of deployment (the prior for a medical-student deployment uses the medical-education slice of the corpus where available).

This is the load-bearing connection between Appendix B and Chapter 7. The appendix should be explicit: *the Hattie corpus enters the bandit through the prior, the taxonomy enters through the feature-vector specification, and the DAG enters through the structural assumption about which features condition on which others*.

---

## E. The DAG framework — making the dependence structure testable

### E.1 What a DAG is, briefly

A directed acyclic graph in Pearl's sense ([Pearl 2009 *Causality*](https://www.cambridge.org/core/books/causality/B0046844FAE10CBF274D4ACBDAEB5F5B); [Chernozhukov et al. *Applied Causal Inference Powered by ML and AI* §6.2 and §7.2](file:///pantry/_lib_applied-causal-inference-powered-by-ml-and-ai.md)) is a graph whose nodes are random variables and whose directed edges encode the assumption that the parent variable directly influences the child variable. The acyclicity constraint (no variable is its own ancestor) is what makes the structure factorizable: the joint distribution of all variables can be written as the product of conditional distributions, each conditioning a variable on its parents.

The do-calculus, developed by Pearl, provides the rules for converting between observational quantities (P(Y | X) — the conditional distribution of Y given that we *see* X) and interventional quantities (P(Y | do(X)) — the conditional distribution of Y given that we *set* X). The distinction is the heart of causal inference ([Pearl & Mackenzie 2018, *The Book of Why*](https://www.penguinrandomhouse.com/books/595514/the-book-of-why-by-judea-pearl-and-dana-mackenzie/)). The do-calculus tells us when observational data can be used to estimate interventional quantities and when it cannot.

For the appendix, the key Pearl moves to introduce in plain English:

- **Three rungs of causal reasoning** (Pearl & Mackenzie 2018, *The Book of Why*; [Smitha Milli's Causal Ladder explainer](http://smithamilli.com/blog/causal-ladder/); [Bareinboim et al.'s technical formulation of Pearl's hierarchy](https://causalai.net/r60.pdf)):
  - *Rung 1: Association* — observation. "Students who get more feedback tend to score higher." Tells us P(Y | X). Insufficient for action.
  - *Rung 2: Intervention* — doing. "If I intervene to give this student more feedback, what happens to their score?" P(Y | do(X)). The platform's level when it executes a randomized policy.
  - *Rung 3: Counterfactual* — imagining. "Given that this student got feedback and scored an 85, what would they have scored without feedback?" P(Y_x | X = x', Y = y'). Required for personalization at the individual level.

  Information at a lower rung is insufficient for questions at a higher rung — but the higher rungs require correspondingly more assumptions. The Medhavy bandit operates at rung 2 by design (random assignment within the platform); rung 3 reasoning enters when the engine personalizes for a specific learner whose deployment history is partial.
- **Backdoor paths and the backdoor criterion** ([Chernozhukov et al. §7.3](file:///pantry/_lib_applied-causal-inference-powered-by-ml-and-ai.md)): a path between treatment and outcome that does not go through the treatment's effect on the outcome but contributes to the observed correlation. The backdoor criterion specifies which variables to condition on to block such paths. In observational educational data, backdoor paths from confounders to outcome through treatment are the rule, not the exception — which is why randomized assignment (the Medhavy architecture's core advantage) matters so much.
- **Colliders and selection bias.** A collider is a node with two arrows into it; conditioning on a collider induces correlation between its parents even when they are independent. Including outcomes-as-features (the *self-reported grades* error from §D.3) is the canonical way to introduce collider bias into an educational analysis.

### E.2 The three edge types from the Causal Graphs draft

The draft's most useful innovation, which the appendix should adopt:

- **Directed edge (→):** the literature converges on a mechanism, the direction is identifiable from existing evidence, and the edge is treated as the working hypothesis.
- **Contested edge (⇢):** two or more plausible mechanisms predict the effect but make distinguishable predictions about moderators, dose-response shape, or boundary conditions. *These are the appendix's primary scientific product*. Contested edges are not weaknesses of the graph; they are experiment specifications.
- **Reversed candidate (⟵?):** the variable may be downstream of the outcome rather than upstream of it; flagged for removal from the intervention set pending analysis.

The contested-edge convention is the appendix's epistemic discipline. It refuses the choice between asserting a mechanism the literature has not settled and averaging it away into a single point estimate. It says, in graph form: *here are the two ways this could work; here is the experiment that would distinguish them.*

### E.3 The mechanism-family taxonomy

The Causal Graphs draft §3.2 introduces a four-family taxonomy of mechanisms that should appear in the appendix:

- **Cognitive load mechanisms** — effects operating through working memory capacity and management (Sweller's cognitive load theory; managing intrinsic, extraneous, and germane load).
- **Memory consolidation mechanisms** — effects operating through encoding, retrieval, and interference in long-term memory (spacing effects, testing effects, retrieval-induced forgetting).
- **Metacognitive mechanisms** — effects operating through self-monitoring, calibration, and goal-setting (self-assessment accuracy, judgments of learning, goal difficulty calibration).
- **Motivational mechanisms** — effects operating through expectancy-value, attribution, and self-efficacy (competence beliefs, growth mindset, autonomy-supportive instruction).

The point of the taxonomy is not classification for its own sake — it is that mechanisms in different families predict different experimental signatures. Two interventions that both improve achievement through different mechanisms will have different dose-response shapes, different moderators, and different interaction patterns. Conflating them into a single effect-size cell is the analytical error a mechanism-family-tagged DAG prevents.

### E.4 The proposed graph — illustrative skeleton

The Causal Graphs draft sketches a starting structure that the appendix should reproduce and then formalize:

```
[Context layer — exogenous, conditioned on, never intervened on]
  Prior Knowledge ──┐
  SES ──────────────┤──→ [Self-Efficacy] ──→ [Achievement]
                    │             ↑
[Intervention layer — manipulable by platform]
  Teacher Credibility ──→ Teacher Clarity ──→ Feedback Quality
                                              ↓
                                  [Self-Assessment Accuracy]
                                              ↓
                                        [Achievement]
```

This is one slice. A full appendix-grade graph for a medical-education deployment would include nodes for retrieval practice, worked examples, scaffolded ill-structured problems (cf. Glimmer in Ch 6 and `glimmer-research.md`), case-based reasoning (Ch 6 and `case-study-research.md`), error trajectory coherence (Y2 in the GLP framework, Ch 5), and the seven-day retrieval probe (the bandit's primary reward signal, Ch 7).

The appendix should not attempt to be the complete graph. The complete graph is the Causal Graphs paper's empirical program. The appendix should:

1. Show the skeleton.
2. Run one edge through the full annotation (directed/contested/reversed; mechanism family; falsification criterion).
3. Point forward: the deployed graph lives in the platform; the published graph lives in the Causal Graphs paper; the appendix is the bridge.

### E.5 A worked edge — the "feedback specificity → seven-day retention" example

The appendix's worked-example move. Walk through this edge in full:

- **Source node:** *Feedback specificity* (an intervention; defined as the proportion of corrective-feedback events that explicitly name the success criterion violated and provide one example of the correct approach).
- **Target node:** *Seven-day retention probe accuracy* (a proximal outcome; defined in Ch 5 and `quiz-me-research.md`).
- **Mechanism hypothesis:** *Specificity reduces misconception persistence by replacing the erroneous retrieval cue before it consolidates in long-term memory* (memory consolidation family). The mechanism predicts a dose-response with diminishing returns past a specificity threshold (because beyond a certain level the criterion-mention becomes redundant with the example).
- **Edge type:** *Contested.* Competing mechanism: *Specificity improves feedback comprehensibility, which improves engagement, which improves time-on-task, which improves retention* (motivational mechanism, with engagement as the mediator). The two mechanisms make different predictions: the memory-consolidation account predicts a sharp inflection at the specificity threshold; the motivational account predicts a linear or curvilinear relationship across the full specificity range. The appendix should name the experimental design that distinguishes them (vary specificity in three bands; measure retention at 7 days and engagement-during-session; the predicted pattern of moderation by prior knowledge differs between mechanisms).
- **Falsification criterion:** A null effect of specificity on seven-day retention *with* a positive effect of specificity on within-session engagement disconfirms the memory-consolidation mechanism while leaving the motivational mechanism intact.

This worked example is what the appendix earns. It is the proof-of-concept that converts a flat-ranked Hattie variable (Feedback, d ≈ 0.72) into a structured experimental question Medhavy can run.

---

## F. The Adherence Classifier — the architectural addition `[verify-urgent]`

### F.1 The problem the classifier solves

Two related problems, both critical to the appendix:

**Problem 1: Treatment fidelity.** In a classical educational RCT, the experimental treatment is delivered by humans (teachers, tutors) whose execution of the protocol drifts. The standard solution is *implementation fidelity coding*: trained observers review video or transcripts and rate each session along the dimensions of the protocol. Fidelity is the proportion of sessions delivered as specified ([Iowa Reading Research Center: How Does Fidelity of Implementation Relate to Student Reading Outcomes?](https://irrc.education.uiowa.edu/blog/2024/11/how-does-fidelity-implementation-relate-student-reading-outcomes); [Michigan Education Corps: Fidelity in Education](https://mieducationcorps.org/2023/10/27/fidelity-in-education/)). Fidelity is consequential: studies that estimate treatment effects without measuring fidelity routinely under-estimate the effect of the intended treatment because they average over high-fidelity and low-fidelity deliveries.

In LLM-mediated tutoring, the same problem appears in a sharper form. The chatbot delivers an instructional policy (e.g., "deliver high-specificity corrective feedback") through stochastic natural-language generation. Two students assigned to the same policy receive different realizations — different wording, different examples, different lengths. Without fidelity measurement, the platform cannot tell whether a null result means *the policy didn't work* or *the policy wasn't delivered*.

**Problem 2: Reward signal contamination.** The Chapter 7 engagement trap (see `07-the-adaptive-engine_notes.md` §E.2) requires that the bandit's reward signal not be gameable by within-session shortcuts. But if the bandit's policy executor sometimes substitutes engagement-shaped responses for the specified policy — softening corrective feedback to maintain rapport, lengthening explanations when the student seems bored — then the bandit's updates are computed on a treatment that is *actually different* from the one the experimental design assigned. The reward weights drift toward the substituted policy, not the assigned policy.

The Adherence Classifier is the architecture that addresses both problems: a post-hoc treatment characterization layer that runs on every logged interaction and produces a structured score along the dimensions the causal model identifies as active ingredients.

### F.2 What the classifier does, operationally

Based on the Causal Graphs draft §4.3 (treatment characterization from logs) and the field of implementation-fidelity measurement in adaptive systems ([Visscher et al. 2024 systematic review of AI-driven ITS in K-12](https://pmc.ncbi.nlm.nih.gov/articles/PMC12078640/); [Yang et al. 2024 dual-layer ITS with validation layer](https://pmc.ncbi.nlm.nih.gov/articles/PMC11415727/)), the classifier's specification is reconstructable even though the Medhavy-internal implementation is not public:

- **Input.** A single interaction event: (student utterance, chatbot utterance, treatment specification, prior interaction context, learner-state vector).
- **Output.** A vector of scores, one per dimension of the treatment specification:
  - *Specificity score* (0–1): did the chatbot's output reference the specific success criterion the treatment specification names?
  - *Timing score* (0–1): was the chatbot's output delivered within the latency window the treatment specification names?
  - *Elaboration type* (corrective / confirmatory / elaborative — categorical): does the output match the treatment specification's elaboration type?
  - *Worked-example inclusion* (binary): if the treatment specification calls for a worked example, was one included?
  - *Cross-dimension contamination flags*: did the chatbot's output express a *different* dimension that the treatment specification is supposed to be holding constant (e.g., warmth when warmth was supposed to be at baseline)?
- **Architecture.** Almost certainly an LLM-based judge using a calibrated rubric — the standard approach in modern LLM evaluation pipelines. The judge model is prompted with the treatment specification, the interaction transcript, and the rubric; it returns structured scores. A second pass calibrates the judge against human raters on a held-out validation set ([Visscher et al. 2024](https://pmc.ncbi.nlm.nih.gov/articles/PMC12078640/) discusses validation approaches for AI-mediated educational interventions; [Yang et al. 2024](https://pmc.ncbi.nlm.nih.gov/articles/PMC11415727/) on dual-layer validation in proof-of-concept ITS).

### F.3 What the classifier produces for the engine

Three downstream uses:

- **Dose-response analysis.** Instead of testing the edge *assigned-treatment → outcome*, the engine can test the more informative edge *delivered-treatment → outcome*. The classifier converts the assignment-level analysis into a dose-response analysis at the active-ingredient level. This is the move the Causal Graphs draft §4.3 names as the partial recovery of SUTVA in the face of stochastic LLM output.
- **Drift detection.** If the classifier's scores drift over time (e.g., specificity scores fall while assignments remain constant), the platform team can detect a regression in the policy executor before it shows up as a confusing reward-update pattern. This is one of the engineering disciplines Chapter 7 §E.2 names as essential.
- **Edge confirmation/falsification.** A null result becomes interpretable only when the classifier confirms that the specified policy was delivered. A null *with* high adherence implicates the mechanism. A null *with* low adherence implicates the operationalization — the right mechanism may have been targeted with the wrong execution.

### F.4 The Adherence Classifier as the SUTVA bridge

This is the appendix's key technical move. SUTVA (Rubin 1980; see `[Rubin, D.B. 1980. Randomization analysis of experimental data: The Fisher randomization test comment. Journal of the American Statistical Association 75: 591-593]`) requires (a) no interference between units and (b) no multiple versions of treatment. Medhavy's one-on-one architecture handles (a) by construction. The Adherence Classifier handles (b) by *measuring* the version of treatment each student received, then using the measured version (not the assigned version) as the causal variable in the analysis. The remaining variation is within-treatment noise — analogous to the natural variance in how a human pharmacist explains a medication, not a SUTVA violation ([Rubin causal model on Wikipedia](https://en.wikipedia.org/wiki/Rubin_causal_model); [Cornell SUTVA reference](https://community.lawschool.cornell.edu/wp-content/uploads/2020/12/Green-presentation-on-SUTVA-for-CELS.pdf); [PMC: Extending the sufficient component cause model to describe SUTVA](https://pmc.ncbi.nlm.nih.gov/articles/PMC3351730/)).

This is the cleanest way to state the classifier's role: *the Adherence Classifier is what makes SUTVA-by-design tractable for stochastic LLM-mediated treatments*.

### F.5 What the appendix cannot say yet `[verify-urgent]`

The Adherence Classifier as a specific Medhavy artifact attributed to Satwik Reddy Sripathi (per the TIKTOC line in the appendix scope) is **not currently public**. My web searches return generic results about adherence/fidelity in AI tutoring but no Medhavy-specific or Sripathi-authored paper or repository describing the classifier's architecture. The Causal Graphs draft refers to "treatment characterization from logs" as the appendix-of-appendix it leaves as future work (its own Appendix B). The most likely state of affairs is:

- The classifier is a working Medhavy-internal component, possibly attached to a student project under Bear Brown at Northeastern.
- The architecture above (LLM-judge with calibrated rubric) is the standard contemporary approach to this problem; the Medhavy-specific implementation may differ in details.
- Citation discipline: the appendix should describe the *architecture* in the form it takes in the Causal Graphs draft's plan, *flag* that the Medhavy implementation is in progress, and credit Sripathi as the project lead with a footnote naming the unpublished status.

**Hard-rule discipline.** §F.2's architecture description is reconstructed from the Causal Graphs draft and the contemporary AI-judge literature. The appendix should make clear that it is describing the *design* the project is implementing rather than reporting on a deployed component with published validation. The phrasing the appendix should use: *the Adherence Classifier, as currently being developed by the Medhavy team, is intended to ...* — not *the Adherence Classifier does ...*.

---

## G. Open question — causal discovery vs. expert elicitation

### G.1 The two strategies

The appendix's closing intellectual move. There are two ways to construct a causal DAG, and the educational-research literature has not converged on which one is appropriate for educational interventions:

**Expert elicitation.** Domain experts (educational researchers, learning scientists, teachers) specify the graph based on theory and prior literature. This is what the Causal Graphs draft proposes — Hattie's variables, augmented by mechanism specifications from cognitive psychology, with directed and contested edges annotated by expert reading. Strengths: interpretable; respects mechanism; admits prior knowledge; the graph is structured to be tested. Weaknesses: experts disagree; experts have systematic blind spots; the graph is constrained by what experts already think.

**Causal discovery.** Algorithms that infer the graph structure directly from data. The canonical reference is the Carnegie Mellon Tetrad project, which implements PC, FGES, GFCI, and a suite of related algorithms ([CMU Tetrad documentation](https://www.cmu.edu/dietrich/philosophy/tetrad/educational-materials/faq.html); [Tetrad single-html manual](https://cmu-phil.github.io/tetrad/manual/); [University of Pittsburgh Center for Causal Discovery](https://www.ccd.pitt.edu/tools/); [Ramsey et al. 2020 *J. Machine Learning Research* on algorithm comparison](https://www.jmlr.org/papers/volume21/19-773/19-773.pdf)). PC is a constraint-based algorithm that uses conditional-independence tests to identify the equivalence class of DAGs consistent with the observed data. FGES is a score-based algorithm that searches the DAG space for the structure that best explains the data. FCI and its variants handle latent confounders. Strengths: data-driven; can surface structure the experts missed; scales to many variables. Weaknesses: requires strong assumptions about the data-generating process; the equivalence-class problem means observational data alone often cannot distinguish causally distinct graphs; performance is sensitive to sample size and noise.

### G.2 The educational-data-mining literature

The application of causal discovery to educational data is still early. The most recent activity:

- **Educational Data Mining 2025 conference** ([EDM 2025 accepted papers](https://educationaldatamining.org/edm2025/accepted-papers/)) includes a paper on *A Multi-View Predictive Student Modeling Framework with Interpretable Causal Graph Discovery for Collaborative Learning Analytics* (Acosta, Lee et al.) — [conference proceedings link](https://educationaldatamining.org/EDM2025/proceedings/2025.EDM.long-papers.135/index.html). This is one of the first applications of structured causal discovery to student modeling.
- **EDM 2023** included a relevant conceptual paper: *A Conceptual Model for End-to-End Causal Discovery in Knowledge Tracing* ([EDM 2023 proceedings](https://educationaldatamining.org/EDM2023/proceedings/2023.EDM-posters.42/index.html)) — argues for finding causal relationships among skills from response data, which would enable better curriculum design via prerequisite-structure inference.
- **Koedinger et al.'s machine-generated cognitive models** ([Koedinger, McLaughlin & Stamper 2012 EDM working paper](http://pact.cs.cmu.edu/pubs/Reformatted-Koedinger-EDM-for-WIRES-cogsci.pdf)) — applies ML to infer skill structure from log data; the resulting models are more predictive of student learning than expert-constructed cognitive models. This is the closest existing result to a causal-discovery-beats-expert-elicitation finding for educational structure, though the work is on cognitive-model structure rather than on intervention DAGs.
- **A practical guide to causal discovery with cohort data** ([Aragam et al. 2023 arXiv](https://arxiv.org/html/2108.13395v3)) — methodological reference that argues for hybrid strategies (expert priors with data-driven refinement) for moderate-sized cohort datasets, which is roughly the regime Medhavy will be in for several years.

### G.3 The honest position for the appendix

Pure causal discovery from educational data is not yet a solved problem. The signal-to-noise ratio in student log data is low; the relevant causal structures involve latent variables (cognitive state, motivation) that are not directly observed; the equivalence-class problem means the same data are consistent with multiple graphs. Pure expert elicitation reproduces the experts' blind spots and the literature's confusions.

The appendix's recommended position, consistent with the Causal Graphs draft's stance: **hybrid**. Use the Hattie corpus and the cognitive-psychology literature to elicit the *skeleton* of the graph (the variables, the high-confidence directed edges, the obvious context-vs-intervention distinctions). Use Medhavy's experimental log data to *refine* the graph (test contested edges via randomized assignment; use causal-discovery algorithms on the within-learner timeseries to surface unexpected structure; revise the prior). Use the Adherence Classifier as the layer that lets the experimental data be trusted at the active-ingredient level.

This is what makes the appendix the bridge it is meant to be: the corpus supplies the *prior* on the graph; the platform supplies the *posterior*; the classifier supplies the *fidelity check* that makes both trustworthy.

The open question — the one the appendix should leave the reader with — is *how much* causal-discovery refinement the platform actually achieves in deployment. If the experimental program runs as designed for five years, does the graph the platform converges to look substantially different from the expert-elicited skeleton? If yes, the educational-research community has been wrong about specific edges. If no, expert elicitation is doing its job and causal discovery is adding modest refinement. Either outcome is informative.

---

## H. Connections to existing chapter notes

Sub-appendix B sits between several main chapters and should cite by filename rather than re-research:

- `Causal Graphs_ A Testable Architecture for Pedagogical Research Using AI-Mediated Instruction.txt` — the primary source. The appendix is essentially a textbook-grade rendering of the architecture described in this draft. Sections 1.1–1.4 (motivation), 3.1–3.3 (graph construction methodology), 4.1–4.4 (Medhavy experimental architecture), and the SUTVA discussion are the load-bearing material.
- `_lib_applied-causal-inference-powered-by-ml-and-ai.md` — the canonical DAG/SEM textbook for the appendix. §6.2 on causal diagrams, §7.2 on DAGs as Markovian models and SEMs, §7.3 on the backdoor criterion and d-separation. Cite by section number rather than name-dropping.
- `07-the-adaptive-engine_notes.md` — the bandit reward function priors. Specifically §E.1 (where the engine's prior comes from — *the appendix is the answer*) and §E.2 (the engagement trap, which the Adherence Classifier guards against at the policy-executor level). The appendix closes the loop the engine chapter opens.
- `11-what-the-platform-does-not-know-yet_notes.md` — §2.6 (open question 6: priority-weighted vs. recall-only scheduling) and §2.1–2.5 (the eight open bets, each of which is an edge-test specification in the appendix's framework). The appendix should cross-reference these as the worked examples of the contested-edge convention.
- `concept-sequencing-research.md` — BKT/DKT/prerequisite graphs (§2). The prerequisite structure is one of the context-layer inputs to the appendix's DAG; the BKT/DKT mastery estimates feed into the diagnostic-node measurements.
- `03-the-evidence-base_notes.md` — §A.2–A.3 on Hattie's 0.40 hinge and the Horvath critique. The appendix should cite §A.3 specifically when discussing the hinge as cost-effectiveness guideline rather than absolute threshold.
- `05-the-measurement-layer_notes.md` — the GLP seven-Y-component framework. The classifier's output feeds into the same measurement stack; the appendix should clarify that adherence is a *seventh discipline* (alongside the seven Y-components, not a replacement for them).

---

## I. Citation block — primary sources for the appendix

The appendix's reference list. Every contestable factual claim in §C–G must be traceable to one of these:

**The Hattie corpus.**
- Hattie, J. (2009). *Visible learning: A synthesis of over 800 meta-analyses relating to achievement*. Routledge. [ISBN 9780415476188](https://www.routledge.com/Visible-Learning-A-Synthesis-of-Over-800-Meta-Analyses-Relating-to-Achievement/Hattie/p/book/9780415476188).
- Hattie, J. (2023). *Visible learning: The sequel: A synthesis of over 2,100 meta-analyses relating to achievement*. Routledge. [Taylor & Francis page](https://www.taylorfrancis.com/books/mono/10.4324/9781003380542/visible-learning-sequel-john-hattie).
- Visible Learning MetaX platform, [visiblelearningmetax.com](https://www.visiblelearningmetax.com/) (accessed 2026-05-17).
- Visible Learning Plus 252-influence ranking, [visible-learning.org Hattie ranking](https://visible-learning.org/hattie-ranking-influences-effect-sizes-learning-achievement/).
- Hattie 2023 announcement, [visible-learning.org/2023/01/visible-learning-the-sequel-2023/](https://visible-learning.org/2023/01/visible-learning-the-sequel-2023/).

**Critiques of Visible Learning.**
- Bergeron, P.-J., & Rivard, L. (2017). How to engage in pseudoscience with real data: A criticism of John Hattie's arguments in Visible Learning. *McGill Journal of Education* 52(1), 237–246. [ResearchGate](https://www.researchgate.net/publication/325983161_A_critique_of_John_Hattie's_theory_of_Visible_Learning).
- Snook, I., O'Neill, J., Clark, J., O'Neill, A.-M., & Openshaw, R. (2009). Invisible learnings? A commentary on John Hattie's book — *Visible Learning*. *New Zealand Journal of Educational Studies* 44(1), 93–106. `[verify pagination]`
- Simpson, A. (2017). The misdirection of public policy: Comparing and combining standardised effect sizes. *Journal of Education Policy* 32(4), 450–466. `[verify DOI]`
- Wecker, C., Vogel, F., & Hetmanek, A. (2017). `[verify exact citation — appears to be Zeitschrift für Erziehungswissenschaft on the year's-progress translation critique]`
- Eacott, S. (2021). Blind spots in visible learning: A critique of John Hattie as an educational theorist. *Nordic Psychology* 73(3). [Taylor & Francis link](https://www.tandfonline.com/doi/abs/10.1080/19012276.2021.1962731).
- David Didau, "Visible Learning, hidden error," substack overview compilation: [daviddidau.substack.com/p/visible-learning-invisible-errors](https://daviddidau.substack.com/p/visible-learning-invisible-errors).
- Andrew Gelman commentary: [statmodeling.stat.columbia.edu/2018/09/01/john-hatties-visible-learning-much-trust-influential-review-education-research/](https://statmodeling.stat.columbia.edu/2018/09/01/john-hatties-visible-learning-much-trust-influential-review-education-research/).
- De Bruyckere, P. (2025). Did the effect of collective teaching efficacy just drop (or did John Hattie's team make a mistake?) [theeconomyofmeaning.com](https://theeconomyofmeaning.com/2025/02/08/did-the-effect-of-collective-teaching-efficacy-just-dropped-or-did-john-hatties-team-made-a-mistake/).

**The DAG and causal-inference machinery.**
- Pearl, J. (2009). *Causality: Models, reasoning, and inference* (2nd ed.). Cambridge University Press. [Cambridge link](https://www.cambridge.org/core/books/causality/B0046844FAE10CBF274D4ACBDAEB5F5B).
- Pearl, J., & Mackenzie, D. (2018). *The book of why: The new science of cause and effect*. Penguin / Basic Books.
- Pearl, J. (1995). Causal diagrams for empirical research. *Biometrika* 82(4), 669–688. `[verify pagination]`
- Greenland, S., Pearl, J., & Robins, J. M. (1999). Causal diagrams for epidemiologic research. *Epidemiology* 10(1), 37–48.
- Bareinboim, E., Correa, J. D., Ibeling, D., & Icard, T. (2022). On Pearl's hierarchy and the foundations of causal inference. In *Probabilistic and causal inference: The works of Judea Pearl* (pp. 507–556). ACM. [causalai.net/r60.pdf](https://causalai.net/r60.pdf).
- Chernozhukov, V., Hansen, C., Kallus, N., Spindler, M., & Syrgkanis, V. (2026). *Applied causal inference powered by ML and AI*. Online version 0.1.2. [causalml-book.org](https://causalml-book.org/). §6.2 on DAGs, §7.2 on Markovian models, §7.3 on the backdoor criterion.
- Smitha Milli's plain-language causal-ladder explainer: [smithamilli.com/blog/causal-ladder/](http://smithamilli.com/blog/causal-ladder/).

**SUTVA and the Rubin model.**
- Rubin, D. B. (1980). Randomization analysis of experimental data: The Fisher randomization test comment. *Journal of the American Statistical Association* 75(371), 591–593. `[verify pagination — canonical citation for SUTVA]`
- VanderWeele, T. J., & Hernán, M. A. (2013). Causal inference under multiple versions of treatment. *Journal of Causal Inference* 1(1), 1–20. [PMC link](https://pmc.ncbi.nlm.nih.gov/articles/PMC4219328/).
- VanderWeele, T. J., & Robins, J. M. (2012). Extending the sufficient component cause model to describe the stable unit treatment value assumption (SUTVA). *Epidemiologic Perspectives & Innovations*. [PMC link](https://pmc.ncbi.nlm.nih.gov/articles/PMC3351730/).
- Rubin Causal Model overview: [Wikipedia: Rubin causal model](https://en.wikipedia.org/wiki/Rubin_causal_model).

**Causal discovery and educational data mining.**
- Carnegie Mellon Tetrad project: [cmu.edu/dietrich/philosophy/tetrad/](https://www.cmu.edu/dietrich/philosophy/tetrad/educational-materials/faq.html); [single-HTML manual](https://cmu-phil.github.io/tetrad/manual/).
- Ramsey, J., Spirtes, P., Glymour, C., et al. (2020). algcomparison: Comparing the performance of graphical structure learning algorithms with TETRAD. *Journal of Machine Learning Research* 21. [PDF](https://www.jmlr.org/papers/volume21/19-773/19-773.pdf).
- University of Pittsburgh Center for Causal Discovery: [ccd.pitt.edu/tools/](https://www.ccd.pitt.edu/tools/).
- Acosta, H., Lee, S., et al. (2025). A multi-view predictive student modeling framework with interpretable causal graph discovery for collaborative learning analytics. *Proceedings of EDM 2025*. [educationaldatamining.org/EDM2025/proceedings/2025.EDM.long-papers.135/](https://educationaldatamining.org/EDM2025/proceedings/2025.EDM.long-papers.135/index.html).
- *A conceptual model for end-to-end causal discovery in knowledge tracing.* (2023). *Proceedings of EDM 2023*. [educationaldatamining.org/EDM2023/proceedings/2023.EDM-posters.42/](https://educationaldatamining.org/EDM2023/proceedings/2023.EDM-posters.42/index.html).
- Koedinger, K. R., McLaughlin, E. A., & Stamper, J. C. (2012). Automated student model improvement. *Proceedings of EDM 2012*. [WIREs cogsci PDF](http://pact.cs.cmu.edu/pubs/Reformatted-Koedinger-EDM-for-WIRES-cogsci.pdf).
- Aragam, B., et al. (2023). A practical guide to causal discovery with cohort data. [arXiv:2108.13395](https://arxiv.org/html/2108.13395v3).

**Implementation fidelity / Adherence in adaptive systems.**
- Iowa Reading Research Center. (2024). How does fidelity of implementation relate to student reading outcomes? [irrc.education.uiowa.edu blog post](https://irrc.education.uiowa.edu/blog/2024/11/how-does-fidelity-implementation-relate-student-reading-outcomes).
- Michigan Education Corps. (2023). Fidelity in education: Doing the right thing the right way. [mieducationcorps.org](https://mieducationcorps.org/2023/10/27/fidelity-in-education/).
- Visscher, A., et al. (2024). A systematic review of AI-driven intelligent tutoring systems (ITS) in K-12 education. *npj Science of Learning*. [PMC link](https://pmc.ncbi.nlm.nih.gov/articles/PMC12078640/); [Nature link](https://www.nature.com/articles/s41539-025-00320-7).
- Yang, J., et al. (2024). Intelligent tutoring systems, generative artificial intelligence, and healthcare agents: A proof of concept and dual-layer approach. *PMC* [link](https://pmc.ncbi.nlm.nih.gov/articles/PMC11415727/).

**The Adherence Classifier itself.**
- *Internal Medhavy artifact, attributed in TIKTOC to Satwik Reddy Sripathi under the supervision of Nik Bear Brown. No public-facing paper, repository, or technical documentation identifiable at the time of compilation (2026-05-17).* **`[verify-urgent with Nik]`** Status: described in this appendix as the architecture-in-progress described by the Causal Graphs draft §4.3 (treatment characterization from logs). Citation deferred pending publication or internal documentation Nik can release.

---

## J. What the appendix should leave the reader with

The reader leaves Appendix B able to answer four questions:

1. **What is the relationship between the Hattie corpus and the Medhavy adaptive engine?** Answer: the corpus supplies the prior, sorted into intervention/diagnostic/context buckets, and the graph supplies the structural assumptions about which features condition on which others. The engine is calibrated to the corpus at deployment time and updates from there.
2. **Why is a flat ranked list not enough?** Answer: it implies independence between variables that are actually causally linked, and it conflates outcomes with causes. A graph makes both moves explicit and testable.
3. **What is the Adherence Classifier doing in the architecture?** Answer: it converts assignment-level analysis (the engine assigned policy X) into delivery-level analysis (policy X was actually executed with specificity score 0.78 and worked-example inclusion = 1), which is the move that recovers SUTVA-by-design for stochastic LLM-mediated treatments. Without it, the engine updates its policy on what it intended to do, not on what it did.
4. **What is the open question?** Answer: whether causal discovery from log data will substantially refine the expert-elicited graph, or whether the expert structure is approximately right and only the parameters need refinement. The platform's five-year experimental program is the bet that finds out.

---

## K. What would change the appendix's reading

Three specific evidentiary moves that would force a revision:

- **A within-learner causal-discovery study on Medhavy log data showing that the inferred DAG diverges substantially from the expert-elicited DAG on >30% of edges.** That would argue that expert elicitation is too constrained by the existing literature's confusions, and the appendix's recommendation should tilt toward heavier reliance on data-driven structure learning.
- **A meta-analysis demonstrating that the Adherence Classifier's scores fail to predict the experimental treatment-effect attenuation it is designed to capture.** That would argue that the active-ingredient framing is wrong — that LLM-mediated treatments are not decomposable into the dimensions the classifier scores, and that some other form of treatment characterization is needed.
- **A successful replication of the Causal Graphs draft's contested-edge methodology in a separate AI-tutoring platform (Khanmigo's research arm, Carnegie Learning, an academic ITS group).** That would argue the methodology generalizes and is not Medhavy-specific.

---

## L. Still puzzling — open questions the appendix raises but does not resolve

1. **How to handle latent variables.** Self-efficacy, metacognitive monitoring, and cognitive load are all causally important and not directly observable. The DAG handles them through proxy measures (confidence ratings, time-on-task, re-attempt behavior). Whether the proxies measure the constructs they claim to measure is a long-standing open question in educational psychology, and the appendix inherits it.
2. **The graph-update governance question.** When the experimental program produces results that revise an edge, who updates the graph, when, and with what oversight? This is a platform-governance question that the appendix raises but the book does not resolve. Likely a future chapter or future book.
3. **The cross-deployment generalization question.** Edges confirmed in the medical-education deployment may not transfer to undergraduate physics, or to K-12 mathematics, or to professional-certification contexts. The appendix's graph is currently specified at a level of generality that may be wrong — too general (the same edge has different parameters in different domains) or too specific (the same edge exists in different domains but the appendix's framing doesn't reveal it). The right level of graph-portability is not yet known.
4. **The classifier-as-introduced-confounder problem.** If the Adherence Classifier is itself an LLM-judge, and the policy executor is an LLM, and the judge model and the executor model share training data — does the classifier introduce systematic bias in its measurement of treatment fidelity? This is a subtle but real risk; the appendix should name it as a verify-down-the-road concern.

---

## M. Word-count target and appendix shape

The TIKTOC implies an appendix of medium-to-long length (4,000–6,000 words is reasonable for an appendix that does the work of bridging Hattie's corpus, Pearl's framework, and a Medhavy-specific architecture). Recommended internal allocation:

- §B Specification — ~600 words. Pull apart the title's vague terms.
- §C The Hattie corpus — ~1,100 words. Current state, the hinge, the critiques, the independence implication.
- §D The taxonomy — ~900 words. Intervention/Diagnostic/Context; example variables; reversed candidates; the engine's prior.
- §E The DAG framework — ~1,200 words. Pearl basics; the three edge types; mechanism families; the worked edge.
- §F The Adherence Classifier — ~900 words. Problem; operation; outputs; SUTVA bridge; verify-flag.
- §G Open question on causal discovery vs. elicitation — ~600 words.
- §H Reader takeaway and what-would-change — ~300 words.

Total: ~5,600 words. The research notes themselves are deliberately longer (≈4,900 words in §A–M); the appendix should compress, not expand.

---

## N. The flag list for Nik — verify items the writer must surface

1. **`[VERIFY URGENT]` The Adherence Classifier's public-facing status.** The TIKTOC attributes the project to Satwik Reddy Sripathi. The web search returns no public paper, repository, or even a project-page result for "Adherence Classifier" in connection with Medhavy or Nik Bear Brown. The appendix should either (a) cite Sripathi's work with a specific reference Nik can provide, or (b) describe the architecture as "in development" without naming Sripathi if the project is not yet attributable. The current draft assumes (b) and notes the issue here.
2. **`[VERIFY URGENT]` Specific effect-size figures from MetaX.** The notes cite ~2,100 meta-analyses, ~132,000 studies, ~300 million students from the public MetaX research-methodology page. *The Sequel* (2023) is cited as the version of record. Effect-size figures for specific variables (Feedback d ≈ 0.72, Teacher clarity d ≈ 0.75, Collective teacher efficacy d ≈ 1.34) are drawn from the public ranked list. If MetaX has been re-issued since 2026-05-17 and any of these figures have moved, the appendix should cite the most recent.
3. **`[verify]` Specific critique citations.** Bergeron & Rivard 2017 (*McGill Journal of Education*) — citation as given. Simpson 2017 (*Journal of Education Policy*) — need to verify DOI and pagination. Wecker, Vogel & Hetmanek 2017 — need to verify exact citation; my best reconstruction is *Zeitschrift für Erziehungswissenschaft* but this needs confirmation. Snook et al. 2009 — *New Zealand Journal of Educational Studies* 44(1) — pagination needs verification. Topphol 2012 on common-language effect-size errors — need to verify the exact citation in *Nordic Studies in Education*.
4. **`[verify]` Pearl 1995 *Biometrika* pagination.** Cited as 82(4), 669–688. Verify with primary source.
5. **`[verify]` Rubin 1980 pagination.** Cited as *JASA* 75(371), 591–593. Verify with primary source.

---

*End of research notes for Appendix B. Estimated appendix word count from these notes: 4,000–6,000. Load-bearing flag: this appendix is the *bridge* between Chapter 7 (the engine's reward function priors come from where?) and the Causal Graphs paper (the experimental program that tests the DAG's edges). The appendix is partially constrained by the public/unpublished status of the Adherence Classifier project — that constraint should be made visible to the reader rather than hidden. Voice: explanatory, with one strong throughline — Hattie's ranking is a prior, the graph is a hypothesis, and the classifier is what makes the hypothesis testable.*
