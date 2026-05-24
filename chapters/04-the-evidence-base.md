# Chapter 4 — The Evidence Base

*Same model underneath. Opposite outcomes. The wrapper is the variable.*

---

Here is a mistake I have watched the EdTech field make in both directions with remarkable consistency.

A researcher publishes a paper concluding that kitchen knives cause finger lacerations. The data are real — 10,000 households, cuts reported in the last year, confidence intervals, the works. The recommendation: eliminate kitchen knives from households. The reasoning error is obvious the moment you name it. The data describe the average outcome of *all* knife use — untrained use, intoxicated use, child use, use on inappropriate surfaces. The data say nothing about what a trained chef using a properly sharpened knife on a cutting board produces, because the survey never separated those cases. The researcher judged the scalpel's potential by observing the butter knife's average misuse.

Call this the **Butter Knife Fallacy**. The skeptics commit it when they cite indiscriminate-deployment outcome data and extrapolate to a verdict on all educational technology. The optimists commit it when they cite carefully-designed-deployment outcome data and extrapolate to a verdict on what platforms will produce at scale in the wild. Neither extrapolation is licensed by the underlying study. Both get made anyway.

This chapter is about refusing the extrapolation in either direction.

The evidence base is dense. I am going to walk you through what is actually in the literature — the ITS results, the spaced-repetition canon, the case-based learning work, the generative-learning studies — and then show you how to read a specific claim against it. By the end you will be able to walk into a vendor pitch or a research seminar and audit what is in front of you. That is the whole point of the chapter. The citations earn their density.

---

## What Horvath gets right

I want to start with the side of the debate that is correct, because the chapter will not be credible if it leads with the critique. Jared Horvath's *The Digital Delusion* (2025) marshals a substantial body of evidence that makes three claims worth granting before we go anywhere else.

**First:** classroom technology, deployed indiscriminately at high dosages, is on average associated with worse learning outcomes. The OECD PISA 2022 data are real. Students who spend up to one hour per day on digital devices for leisure score approximately 49 points higher in mathematics than students who spend five to seven hours per day, even after adjusting for socioeconomic profile.[^1] I want to be precise about this figure because a working version of this book's outline carried "6+ hours / 66 points," which does not appear in the OECD primary sources. The verified figure is 49 points at the 5–7 hours versus up to 1 hour comparison. I am citing the corrected figure throughout. The distraction effect from *peer* phone use is also real — students whose classmates use phones during class score about 15 points lower on PISA's mathematics scale, even after adjusting for socioeconomic status.[^1] These are large effects. They should trouble anyone building platforms for classrooms.

**Second:** the meta-analytic effect of EdTech, averaged across studies, is approximately +0.29 standard deviations.[^2] That is below the Hattie 0.40 hinge, which I will explain in a moment. Horvath is not wrong about the average.

**Third:** most claims of EdTech effectiveness in the practitioner literature do not survive methodological scrutiny. Self-report bias. Satisfaction-as-proxy-for-learning. Single-cohort studies without controls. Vendor-funded evaluations. These are real patterns, pervasive ones.

Grant all three. The average EdTech deployment in the average context is not producing learning, and the average vendor claim cannot be trusted at face value. That is a defensible reading of the existing literature, and any architecture chapter that ignores it is doing the wrong work.

| Item | Meaning |
| --- | --- |
| Two-column reference card | "What Horvath's evidence licenses" vs. "What it does not license." Left: indiscriminate high-dosage deployment harm |
| +0.29 meta-analytic average | A concrete checkpoint for applying the chapter concept. |
| methodological critique of vendor literature. Right: a verdict on step-based ITS | A concrete checkpoint for applying the chapter concept. |
| a verdict on well-designed retrieval-practice apps | A concrete checkpoint for applying the chapter concept. |
| a verdict on safeguarded AI tutoring. Reader should use this as calibration before the ITS counter-context section. | Use the chapter example as the concrete test case. |

---

## Where Horvath overreaches

The overreach has a specific form: universal quantification. Horvath argues that EdTech fails in *nearly every context*. Nearly every is a universal quantifier. One counter-context is sufficient to disprove it, and the field has several.

VanLehn 2011 is the canonical meta-analysis of intelligent tutoring systems.[^3] Step-based ITS — systems that give feedback at each reasoning step, not just on the final answer — produce *d* = 0.76 against conventional instruction. That is statistically indistinguishable from human tutoring (*d* = 0.79). Answer-based computer-assisted instruction produces *d* = 0.31. The structural finding is worth holding: step-grain interactivity matters more than whether the tutor is human or machine. The machine that intervenes at each step is nearly as effective as the human who does the same thing.

Kulik and Fletcher 2016 confirmed the pattern across fifty controlled evaluations of ITS: median effect *g* = 0.66.[^4] Graesser et al.'s AutoTutor, a dialog-based natural-language tutoring system for Newtonian physics, produced *d* = 0.75 to 1.22.[^5] These are not vendor claims. They are peer-reviewed effect sizes from thirty years of controlled evaluation.

The ITS literature is the counter-context. It is not cherry-picking to cite a counter-context in response to a claim of *nearly every*. It is the appropriate response to the form of the argument.

I should name the Steenbergen-Hu and Cooper cold-water finding alongside the positive results, because the chapter's discipline requires it.[^6] ITS produced *g* = 0.01 to 0.09 for K–12 mathematics overall, and *g* = –0.18 for low-achieving K–12 students. The college sample showed *g* ≈ 0.37 to 0.43. The structural warning: ITS that works in college often fails in K–12, where motivation and prior knowledge differ substantially. Any platform claiming K–12 outcomes from college-validated ITS evidence is committing the same category error the chapter is trying to prevent.

The full picture: ITS works, under conditions. Those conditions include step-grain interactivity, appropriate age and prior-knowledge range, and careful pedagogical design. The same system failing in one context and succeeding in another is precisely the variance the Butter Knife Fallacy erases when it averages.

![Horizontal bar chart of ITS effect sizes from](images/04-the-evidence-base-fig-01.png)
*Figure 4.1 — Horizontal bar chart of ITS effect sizes from*

---

## The hinge

A word on Hattie's 0.40, because it is the most mis-used number in EdTech debate.

John Hattie's *Visible Learning* (2009) synthesized over 800 meta-analyses and reported that the average effect across all the educational interventions he reviewed was approximately *d* = 0.40.[^7] He called this the *hinge point* — the threshold above which an intervention is plausibly producing real value at reasonable cost. The number is widely used in EdTech as a binary classifier: above 0.40 is good, below is bad. Horvath uses it this way. Most vendors use it this way.

The honest reading is different. The 0.40 is not a threshold of effectiveness. It is the *average* across Hattie's database. Using it as a cutoff is roughly equivalent to concluding that any student who scores below class average on an exam has failed the class.

The Hattie critique literature is substantial — Simpson 2020 on the meta-meta-analysis problem, Kraft 2020 on pre-post designs inflating effect sizes, Eacott on the philosophical problems with reducing education to a single quantifiable metric.[^8] These are real methodological critiques. The chapter does not erase the figure; it uses it correctly. The correct use is as a **cost-effectiveness guideline**: interventions producing small effects at large cost are bad buys. Below-0.40 effects can still matter — small effects on equity-relevant outcomes for marginalized populations, small effects that compound over years, small effects in domains where any positive shift is hard-won. The guideline is useful. The binary classification is not.

When you see a vendor claim citing "above Hattie's hinge" without context, you are looking at the binary mis-use. When you see a skeptic dismissing an intervention because *d* = 0.32, you are looking at the same mis-use in reverse.

---

## What Khan gets right, and where he overreaches

The symmetric move. Salman Khan's *Brave New Words* (2024) is the optimistic case for AI in education. The optimism is selective, but the underlying structural claim deserves a fair hearing before it gets audited.

The promise is real. Bloom's 1984 two-sigma finding — that one-on-one human tutoring produces *d* = 2 against conventional instruction — has been revised down substantially by VanLehn 2011 to *d* = 0.79. Still very large. The finding that AI tutoring can approach that range, in well-designed deployments, is supported by evidence — not by broad evidence, but by the strongest single result currently published, which I am about to walk through in detail. The promise that *well-designed AI tutoring can approach the human-tutoring effect size* is supported. What is not supported is the inference that the average AI tutoring deployment will do so.

Khanmigo's growth from 40,000 to 700,000 students across 380 district partners in 2024–25 reflects real demand for AI tutoring as a category. Common Sense Media's 4-star rating is a non-trivial third-party endorsement of educational quality and safety.

The overreach is measurement: treating engagement as a proxy for learning, treating growth as proof of effect, treating the optimistic case as if the evidence were settled. The chapter takes Khan's promise seriously. It does not grant Khan's measurement choices. Until an independent evaluator publishes a controlled-comparison RCT with durable-learning outcomes at delay, the learning-outcomes inference from Khanmigo's adoption numbers is not licensed by the cited evidence. The people inside Khan Academy who have acknowledged the IDK-IDK pattern — students typing "I don't know" repeatedly until the Socratic system revealed the answer — are the people with access to the actual usage data, and their acknowledgment is consistent with this read.

---

## Bastani PNAS 2025 — the chapter's central anchor

The single most consequential generative-AI-in-education result published to date. It earns real length.

Bastani et al. conducted a field experiment in a Turkish high school, approximately 1,000 students in grades 9–11, math practice sessions across a multi-week curriculum.[^9] Three conditions, random assignment:

**No-AI control.** Standard practice, no LLM access.

**GPT Base.** GPT-4 wrapped in a standard ChatGPT-style interface. Students could ask whatever they wanted; the model helped in its default helpful-assistant mode.

**GPT Tutor.** GPT-4 wrapped in a teacher-designed system prompt. The wrapper injected pedagogical hints, refused to give complete answers, and structured the interaction around the student externalizing a reasoning step before the model advanced.

The underlying model was *the same* in both AI conditions. Same weights. Same training. The only thing that changed was the wrapper — a few hundred tokens of system prompt and some conversational scaffolding.

During practice, with AI access:

- GPT Base: 48% higher math practice performance versus the no-AI control.
- GPT Tutor: 127% higher math practice performance versus the no-AI control.

Both numbers look like wild success. If you were running either deployment's engagement dashboard, you would be writing a press release.

On the subsequent exam, without AI access:

- GPT Base: **17 percentage points lower** than no-AI control.
- GPT Tutor: statistically indistinguishable from no-AI control.

| Dimension | Contrast |
| --- | --- |
| No-AI Control, GPT Base, GPT Tutor | A concrete checkpoint for applying the chapter concept. |
| columns: In-practice performance (vs. control | A concrete checkpoint for applying the chapter concept. |
| Exam performance (vs. control | A concrete checkpoint for applying the chapter concept. |
| Durable learning verdict. Values: Control baseline | baseline |
| GPT Base +48% | –17 percentage points |
| GPT Tutor +127% | ~0 |

Read those numbers again. Popular summaries sometimes report the harm as "17% lower"; the precise figure is 17 percentage points, which on the underlying scale is approximately half a standard deviation of durable-learning damage relative to no AI at all. That is not noise. That is the systematic destruction of a half-standard-deviation of learning by a system that, during practice, appeared to be producing a 48% performance gain.

Three things fall out of this.

**In-session performance is not learning.** Bjork's distinction between *performance* and *learning* — the idea that ease of acquisition during practice does not predict retention at delay — has been empirically demonstrated for LLM-mediated practice. Students felt smarter, performed better in-session, and learned less. The performance metric and the learning metric pointed in opposite directions.[^10]

**The wrapper, not the model, is the variable.** Same GPT-4 underneath both conditions. Different prompt design. Outcomes diverge by roughly half a standard deviation on the durable measure. The model was not the source of either outcome. The model was a willing actor. The wrapper made the pedagogical decisions.

**The harm from naïve deployment is not subtle.** A 17-percentage-point exam decrement is not "AI is mildly suboptimal." In this context, an unguarded AI deployment made students substantially worse than they would have been without any AI at all.

I want to be honest about what Bastani is and is not. It is one RCT, in one country, in one subject domain, at one age range. The replication question is open. The chapter does not treat Bastani as definitive. It treats Bastani as the strongest single result currently published. The specific finding that should update every architect's priors: *two deployments of the same model, at the same institution, in the same subject, for the same students, produced opposite outcomes, and the only variable was the wrapper.* That is not a finding you can explain away.

---

## Kestin Harvard 2025 — the positive case

Bastani shows the negative case. Kestin et al. show the positive one, and together the two studies specify the chapter's central claim with more precision than either could alone.

Kestin et al. ran an RCT at Harvard, Physical Sciences 2, 233 students, Fall 2023.[^11] A custom AI tutor was built with research-based pedagogical principles: segmented content, formative checks, deliberate misconception traps — the same design discipline as the in-class active-learning sessions. Students learned roughly twice as much in less time on the AI tutor than in the active-learning class. Reported effect sizes *d* ≈ 0.7 to 1.3.

The audit: one institution, one course, one professor, one custom-built tutor. The comparison is to a single active-learning session, not a full course. The result does not support "any AI tutor is twice as good as active learning." That inference is not licensed. What the result does support: with sufficient pedagogical design discipline, generative AI tutors can produce effect sizes in the human-tutoring range in well-defined contexts.

Now put Bastani and Kestin side by side. Both used current-generation frontier LLMs. Both were rigorous by the standards of the literature. The outcomes diverged dramatically. The difference is the design discipline applied to the wrapper. Bastani's unguarded wrapper destroyed half a standard deviation of durable learning. Kestin's research-designed wrapper produced effect sizes in the human-tutoring range.

The architecture this book describes is the systematic specification of that design discipline — what the wrapper must do, and why, at every interaction point. Chapter 6's Ask AI mode is where Bastani's GPT Tutor wrapper becomes a four-mode integrated system. Chapters 5 and 7 specify how the measurement layer knows whether the wrapper is working.

---

## The retrieval-practice canon

The Quiz Me mode rests on the most methodologically mature subfield in instructional research. The effect sizes are large, the mechanisms are well-understood, and the canonical citations have stood up to thirty years of replication.

Roediger and Karpicke 2006 established the testing effect with educationally meaningful prose.[^12] At five minutes after study, repeated study beats testing: 83% versus 71%. At one week, the order reverses: 40% after study-only, 61% after three test trials. The act of pulling information out of memory changes the memory. Everything built on Anki, everything built on flashcard-style retrieval, is built on this paper.

Karpicke and Blunt 2011 produced the largest single-experiment effect size in the literature: retrieval practice outperformed elaborative concept mapping by *d* ≈ 1.50 on a one-week delayed test, including inference questions.[^13] Treat that as a laboratory ceiling. The population effect at scale will not match it. The direction is what matters.

Adesope, Trevisan, and Sundararajan 2017 gave the meta-analytic picture: 188 experiments, 272 independent effect sizes, practice tests versus re-studying *g* = 0.51, versus no activity *g* = 0.93, in classrooms specifically *g* ≈ 0.67.[^14] The cleanest summary of "Quiz Me beats re-reading" in the literature.

Cepeda et al. 2006 established the spacing benefit across 839 assessments.[^15] Spaced reviews produce more durable retention than massed reviews; the optimal inter-study interval scales with the retention horizon. This is the paper Anki's algorithm implements. Cepeda et al. 2008 showed the benefit persists over retention intervals up to 350 days — the spacing advantage does not decay over a year.[^16] That is the empirical license for scheduling reviews over multi-month horizons rather than cramming over weeks.

Pan and Rickard 2018 addressed the transfer question: not just "does retrieval practice improve recall of the practiced items" but "does it improve performance on related items the student has not directly practiced."[^17] The pooled transfer effect was *d* = 0.40, 95% CI [0.31, 0.50], and larger in medical contexts specifically. That is the citation that licenses Quiz Me's role in clinical-reasoning curricula — the benefit is not narrow memorization, it generalizes.

The discipline the chapter requires: distinguish *retrieval practice* as mechanism, *spacing* as scheduling principle, and the specific algorithms (SM-2, FSRS) as implementation. Each has different evidence and different effect-size magnitudes. Conflating them is the most common error in vendor marketing for flashcard tools.

![Three-tier stack distinguishing the retrieval-practice evidence hierarchy ](images/04-the-evidence-base-fig-02.png)
*Figure 4.2 — Three-tier stack distinguishing the retrieval-practice evidence hierarchy *

---

## Case-based learning and the gap I am naming on purpose

The Case Study mode rests primarily on Thistlethwaite et al. 2012, a systematic review covering 104 papers across medicine, dentistry, veterinary, nursing, midwifery, and allied health.[^18] The central finding: CBL is consistently rated highly by students and educators; the evidence is heterogeneous but consistent in direction; CBL improves student engagement and learning outcomes.

Here is the gap I want to name on purpose, because the chapter's discipline requires it. The Thistlethwaite review is on *human-facilitated* CBL — small-group discussion led by a clinical educator. The evidence does not directly license *solo asynchronous AI-facilitated CBL*, which is what Medhavy's Case Study mode is. The architecture has to make the bet that the case structure itself is doing the real work, and that the human facilitator is not the entirely irreplaceable component. That bet is reasonable. It is not directly tested by the Thistlethwaite review. Chapter 6 will return to this when it specifies the Case Study mode. I am naming the gap here so it cannot be papered over later.

---

## Generative learning and the anxiety failure mode

The Glimmer mode rests on Fiorella and Mayer 2016, which catalogued eight ways to promote generative learning: summarizing, mapping, drawing, imagining, self-testing, self-explaining, teaching, enacting.[^19] Self-testing and self-explaining have the strongest evidence. Teaching — Feynman's own discipline — is well-established. The evidence for drawing, imagining, and enacting is more domain-specific.

The distinction between well-structured and ill-structured problems is the design logic that determines *which mode to use when*. Jonassen 1997 established the canonical framework: well-structured problems have constrained, convergent, finite-rule solutions; ill-structured problems have multiple solutions, uncertainty about which concepts are necessary, and no clean stopping criterion.[^20] Information-processing theory grounds well-structured-problem instruction. Constructivism and situated cognition ground ill-structured-problem instruction.

The practical implication: Quiz Me is the right mode for well-structured problems — recall of a pharmacological mechanism, calculation of a drug dosage, interpretation of a known ECG pattern. Glimmer is the right mode for ill-structured problems — diagnosing an ambiguous presentation, designing a treatment plan under uncertainty, explaining a concept to a patient. Using Quiz Me on ill-structured problems produces brittle knowledge that does not transfer. Using Glimmer on problems the student does not yet have the prior knowledge to generate anything about produces the anxiety failure mode: students freeze and produce nothing. The architecture has to know which regime it is operating in. Chapter 6 specifies how.

The failure mode is worth naming separately because it is the most common complaint about "active learning" approaches in practice. The instructor who assigns generative work to students who lack the prerequisite knowledge is not experiencing a failure of the generative-learning framework; they are experiencing the framework correctly applied to the wrong regime. The distinction matters because the remedy is different: the solution is not to abandon generative work, it is to ensure sufficient prior knowledge before assigning it.

![Two-branch decision tree for mode selection ](images/04-the-evidence-base-fig-03.png)
*Figure 4.3 — Two-branch decision tree for mode selection *

---

## How to read an evidence claim — the audit in five moves

The chapter teaches a form. Five moves. You will use them again.

**Move 1: Specify what the claim actually is.** State it in its strongest form, not its weakest. You cannot critique a position you have not first stated charitably. Horvath's strongest claim: indiscriminate-deployment harm is real, the meta-analytic average is +0.29, and the practitioner literature is methodologically thin. Khan's strongest claim: AI tutoring can approach the human-tutoring effect size, and the demand for AI tutoring is real.

**Move 2: Specify what would have to be true for the claim to be supported.** PISA correlations would have to translate to causal effects — they do not, automatically; PISA is observational. The meta-analytic average would have to be a representative summary — it is not, because the underlying literature is heterogeneous and averaging across meta-analyses hides the variance that is the most interesting finding. The "nearly every context" claim would have to survive a counter-example search — it does not, because the ITS literature is a counter-example.

This is the Spiegelhalter move: *what would have to be true for this claim to be supported, and is that thing true?*[^21] It is the most useful epistemic instrument I know. The move separates evidence-reading from evidence-citing.

**Move 3: Apply the threshold test.** Does the evidence support a verdict on EdTech-in-general, or only on a specific subset of deployments? Horvath's evidence supports a verdict on indiscriminate high-dosage classroom technology. It does not support a verdict on well-designed retrieval-practice apps, well-designed ITS, or well-designed safeguarded AI tutoring with Bastani-style wrappers. The over-generalization is the universal-quantifier move.

**Move 4: State the residual.** What does the claim get right that should not be dismissed? Horvath's +0.29 is real. The PISA correlations are real. The methodological critique of vendor literature is real. Khan's adoption numbers are real. Khan's demand signal is real. The audit is not a dismissal. It is a clarification of what the evidence actually licenses.

**Move 5: State the implication.** What architecture does the evidence license, given the residual? The book's response to Horvath is not to dispute his evidence — it is to specify the design discipline that produces outcomes above the butter-knife average. The Bastani finding is the bridge: take Horvath's correctly-diagnosed indiscriminate-deployment harm, ask what wrapper produces the opposite outcome, build the architecture around the wrapper.

---

## What would change my mind

The chapter's central claim is that the wrapper is the variable, that Bastani and Kestin together license an architecture built around pedagogically-designed prompt structure, and that the field's two dominant readings of the evidence both commit the Butter Knife Fallacy by extrapolating from one regime to another.

Four things would force a revision.

A successful Bastani replication in a non-Turkish context, different age group, different subject domain, would substantially strengthen the wrapper-as-variable claim. A failed replication would substantially weaken it. If Bastani does not replicate, the chapter's central anchor moves to Kestin alone, which is a narrower base — one course, one institution, one professor.

A rigorous independent RCT of Khanmigo or LearnLM with a no-treatment control and durable-learning outcomes at delay would update my read of vendor-published evidence in both directions: large positive durable-learning effects would soften the chapter's skepticism; null effects would sharpen it.

A direct comparison of well-designed solo asynchronous AI-facilitated CBL versus human-facilitated CBL would address the gap I named in the Thistlethwaite literature. If AI-facilitated produces equivalent outcomes, the Case Study mode's evidence base is stronger than the chapter claims.

A meta-analytic update synthesizing the 2024–2026 generative-AI-in-education studies — which would by then number in the high tens or low hundreds — would let the chapter cite a meta-analytic effect size for AI tutoring rather than relying on two anchor studies. Two studies is honest but thin. The architecture's evidence base improves as the literature accumulates.

---

## Exercises

The following exercises are for practice with large language models in an educational context. Use an LLM of your choice for each.

1. **(Audit — LLM exercise)** A vendor presents the following claim: *"Our adaptive math platform produces an effect size of g = 0.45, based on a meta-analysis of 12 implementation studies across 47 schools."* Walk an LLM through the five-move audit. Ask it to apply each move in sequence — specification, what-would-have-to-be-true, threshold test, residual, implication. Then ask the LLM to identify which moves it found hardest to apply and why. Where did the LLM reach for a verdict before completing the audit?

2. **(Counter-context — LLM exercise)** Ask an LLM to argue that EdTech fails in nearly every context, using the strongest evidence it can find. Then ask it to identify one counter-context where the evidence runs in the opposite direction — one class of EdTech deployment with positive controlled-evaluation results. Ask it to name the design variable that distinguishes the successful deployment from the average deployment. Evaluate whether the LLM correctly separates the ITS evidence from the generative-AI evidence, or conflates them.

3. **(Wrapper design — LLM exercise)** Present the Bastani PNAS finding to an LLM and ask it to design a wrapper specification for an AI tutoring deployment in a subject of your choice. The specification should name three guardrail decisions the Bastani finding justifies, one decision the finding does not directly justify but you would still recommend, and the measurement signal that would tell you whether the wrapper is working. Evaluate the output: does the LLM treat the wrapper as the variable, or does it default to model-selection as the primary design lever?

4. **(Symmetry — LLM exercise)** The chapter audits both Horvath's skepticism and Khan's optimism. Ask an LLM to apply the five-move audit to a piece of EdTech evidence you find persuasive — something you are inclined to agree with. Ask it to steelman the counter-position. The goal is to practice the discipline on evidence you like rather than evidence you distrust. Where did the audit change your view?

---

## References

[^1]: OECD. (2023). *PISA 2022 Results (Volume I): The State of Learning and Equity in Education*. OECD Publishing. https://www.oecd.org/en/publications/pisa-2022-results-volume-i_53f23881-en.html

[^2]: Horvath, J. C. (2025). *The Digital Delusion: How EdTech Has Failed Our Schools — and How to Fix It.* The +0.29 figure is cited in the book and supporting essays; consistent with broader Hattie-tradition synthesis.

[^3]: VanLehn, K. (2011). The relative effectiveness of human tutoring, intelligent tutoring systems, and other tutoring systems. *Educational Psychologist*, 46(4), 197–221. https://doi.org/10.1080/00461520.2011.611369

[^4]: Kulik, J. A., & Fletcher, J. D. (2016). Effectiveness of intelligent tutoring systems: A meta-analytic review. *Review of Educational Research*, 86(1), 42–78. https://doi.org/10.3102/0034654315581420

[^5]: Graesser, A. C., et al. (2005). AutoTutor: A tutor with dialogue in natural language. *Behavior Research Methods, Instruments, & Computers*, 36(2), 180–192. https://link.springer.com/article/10.3758/BF03195563

[^6]: Steenbergen-Hu, S., & Cooper, H. (2013). A meta-analysis of the effectiveness of intelligent tutoring systems on K–12 students' mathematical learning. *Journal of Educational Psychology*, 105(4), 970–987.

[^7]: Hattie, J. (2009). *Visible Learning: A Synthesis of Over 800 Meta-Analyses Relating to Achievement*. Routledge.

[^8]: Simpson, A. (2020). The misdirection of public policy: Comparing and combining standardised effect sizes. Kraft, M. A. (2020). Interpreting effect sizes of education interventions. *Educational Researcher* 49(4), 241–253.

[^9]: Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., & Mariman, R. (2025). Generative AI without guardrails can harm learning: Evidence from high school mathematics. *Proceedings of the National Academy of Sciences*, 122(26), e2422633122. https://doi.org/10.1073/pnas.2422633122

[^10]: Soderstrom, N. C., & Bjork, R. A. (2015). Learning versus performance: An integrative review. *Perspectives on Psychological Science*, 10(2), 176–199.

[^11]: Kestin, G., Miller, K., Klales, A., Milbourne, T., & Ponti, G. (2025). AI tutoring outperforms in-class active learning: An RCT introducing a smart learning companion. *Scientific Reports*, 15. https://www.nature.com/articles/s41598-025-97652-6

[^12]: Roediger, H. L., III, & Karpicke, J. D. (2006). Test-enhanced learning: Taking memory tests improves long-term retention. *Psychological Science*, 17(3), 249–255. https://pubmed.ncbi.nlm.nih.gov/16507066/

[^13]: Karpicke, J. D., & Blunt, J. R. (2011). Retrieval practice produces more learning than elaborative studying with concept mapping. *Science*, 331(6018), 772–775.

[^14]: Adesope, O. O., Trevisan, D. A., & Sundararajan, N. (2017). Rethinking the use of tests: A meta-analysis of practice testing. *Review of Educational Research*, 87(3), 659–701.

[^15]: Cepeda, N. J., Pashler, H., Vul, E., Wixted, J. T., & Rohrer, D. (2006). Distributed practice in verbal recall tasks: A review and quantitative synthesis. *Psychological Bulletin*, 132(3), 354–380. https://pubmed.ncbi.nlm.nih.gov/16719566/

[^16]: Cepeda, N. J., et al. (2008). Spacing effects in learning: A temporal ridgeline of optimal retention. *Psychological Science*, 19(11), 1095–1102.

[^17]: Pan, S. C., & Rickard, T. C. (2018). Transfer of test-enhanced learning: Meta-analytic review and synthesis. *Psychological Bulletin*, 144(7), 710–756. https://pubmed.ncbi.nlm.nih.gov/29733621/

[^18]: Thistlethwaite, J. E., et al. (2012). The effectiveness of case-based learning in health professional education. A BEME systematic review: BEME Guide No. 23. *Medical Teacher*, 34(6), e421–e444. https://doi.org/10.3109/0142159X.2012.680939

[^19]: Fiorella, L., & Mayer, R. E. (2016). Eight ways to promote generative learning. *Educational Psychology Review*, 28(4), 717–741. https://doi.org/10.1007/s10648-015-9348-9

[^20]: Jonassen, D. H. (1997). Instructional design models for well-structured and ill-structured problem-solving learning outcomes. *Educational Technology Research and Development*, 45(1), 65–94. https://doi.org/10.1007/BF02299613

[^21]: Spiegelhalter, D. (2019). *The Art of Statistics: How to Learn from Data*. Basic Books.

## Prompts

Use these prompts with Claude to generate interactive D3 v7 versions of the
figures in this chapter. Each produces a standalone HTML file you can open
in a browser and modify freely.

**Prerequisites:** Load `brutalist/CLAUDE.md` and `brutalist/DESIGN.md` into
your Claude project context before using these prompts. They define the stack,
naming conventions, color system, and typography the figures use.

---

### Figure 4.1 — Horizontal bar chart of ITS effect sizes from

Create a standalone D3 v7 HTML file for Figure Horizontal bar chart of ITS effect sizes from. Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: Horizontal bar chart of ITS effect sizes from the canonical studies — bars: VanLehn step-based ITS d=0.76, VanLehn human tutoring d=0.79, Kulik & Fletcher ITS median g=0.66, AutoTutor d=0.75–1.22, Steenbergen-Hu K–12 overall g=0.01–0.09, Steenbergen-Hu low-achieving K–12 g=–0.18, VanLehn answer-based CAI d=0.31. Color-code positive vs. negative. Hattie 0.40 hinge shown as a vertical reference line. Reader should immediately see the variance: same category of technology, wildly different outcomes depending on context and design discipline.. Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relationships in the brief. Use a zero baseline for bars or areas, direct labels where possible, and annotations named in the brief. Use only DESIGN.md color variables and the required serif/mono font split.

> Reference implementation: `d3/04-the-evidence-base-fig-01.html`

---

### Figure 4.2 — Three-tier stack distinguishing the retrieval-practice evidence hierarchy 

Create a standalone D3 v7 HTML file for Figure Three-tier stack distinguishing the retrieval-practice evidence hierarchy . Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: Three-tier stack distinguishing the retrieval-practice evidence hierarchy — top tier: Mechanism (retrieval practice itself; Roediger & Karpicke 2006, Karpicke & Blunt 2011, Adesope et al. 2017 meta-analysis, Pan & Rickard 2018 transfer); middle tier: Scheduling principle (spacing; Cepeda et al. 2006, Cepeda et al. 2008); bottom tier: Implementations (SM-2 algorithm, FSRS algorithm — note: implementation benchmarks only, no peer-reviewed learning-outcome RCTs). Effect sizes annotated at each tier. Reader should see immediately that the evidence is strongest at the mechanism level and thins out toward implementation — and that a vendor citing FSRS internal benchmarks is not citing the same level of evidence as Roediger & Karpicke.. Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relatio

> Reference implementation: `d3/04-the-evidence-base-fig-02.html`

---

### Figure 4.3 — Two-branch decision tree for mode selection 

Create a standalone D3 v7 HTML file for Figure Two-branch decision tree for mode selection . Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: Two-branch decision tree for mode selection — root node: "Does the student have sufficient prior knowledge to generate?" → No branch leads to: "Build prior knowledge first (Ask AI / Quiz Me)" → then return to root. Yes branch splits on: "Is the problem well-structured or ill-structured?" → Well-structured leads to "Quiz Me" with example problems listed; Ill-structured leads to "Glimmer / Case Study" with example problems listed. Anxiety failure mode annotated on the "Glimmer without prior knowledge" path. Reader should be able to use this as a practical reference for instructional design decisions.. Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relationships in the brief. Use a zero baseline for bars or areas, direct labels where possible, and annotations named in the brief. Use only DESIGN.md color variables an

> Reference implementation: `d3/04-the-evidence-base-fig-03.html`
