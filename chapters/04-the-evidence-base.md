# Chapter 4 — The Evidence Base

---

## Learning Objectives

By the end of this chapter, you will be able to:

1. **(Analyze)** Distinguish between the evidence Khan uses, the evidence Horvath uses, and the evidence both omit.
2. **(Evaluate)** Apply Hattie's 0.40 effect size threshold correctly: as a cost-effectiveness guideline, not an absolute binary.
3. **(Understand)** Explain the Bastani PNAS 2025 finding and identify the design variable that determined the difference between outcomes.
4. **(Analyze)** Identify which findings from the ITS, spaced repetition, CBL, and generative assignment literatures apply to a specific intelligent textbook design decision.
5. **(Evaluate)** Assess a claimed EdTech evidence base for cherry-picking.

**Prerequisites:** Chapters 1–2. You need the engagement-vs-learning distinction, the four-layer sketch, and the complexity threshold test. Chapter 3 supplies the evidence that the rest of the book will cite rather than re-argue. It is the longest chapter in the book. It earns its length.

---

## Where this fits the conductor frame

This chapter primarily serves the instructor — the second of the three questions, in order. The learner is the audience the evidence ultimately bears on, but the instructor is the one who has to read the literature, audit the cherry-picking, and decide what to build. The chapter trusts that an instructor who can audit evidence can build pedagogy that serves the learner; an instructor who cannot will misread the field and produce something that fails Question 1 by accident.

What this chapter specifies for the conductor is the evidence base she reads to decide which instrument plays. The conductor does not pick a position and defend it; she reads what each design produced and updates from that. The Butter Knife Fallacy is a conductor discipline: refusing the extrapolation in either direction from data that describe a different regime than the one the conductor is conducting. Hattie's *d* = 0.40, Bastani's GPT-Base/GPT-Tutor split, the PISA dosage curves — these are the calibration data the conductor consults before reaching for a mode.

The chapter runs the experiment by modeling the audit itself. The corrected PISA figure — 49 points, not the 66 from an earlier draft — is the transparency move on the page. The book is publicly correcting itself. That is what an experiment-as-product commits to: not certainty about every figure but the discipline of revising the figure when the primary source does not support it.

---

## The Butter Knife Fallacy

A researcher publishes a paper concluding that *kitchen knives cause finger lacerations*, based on a survey of 10,000 households reporting cuts in the last year. The data are real. The correlation is robust. The mean cut depth is reported with confidence intervals. The recommendation — *eliminate kitchen knives from households* — does not follow. The data describe the average outcome of *all knife use, including untrained use, intoxicated use, child use, and use on inappropriate surfaces*. The data are silent on the question of what a trained chef using a properly sharpened chef's knife on a cutting board produces, because the survey did not separate those cases.

Call this the **Butter Knife Fallacy**: judging the scalpel's potential by observing the butter knife's average misuse. It is, by my count, the single most common reasoning error in EdTech debate. It is committed by *both sides* of the field. The skeptics cite indiscriminate-deployment outcome data and extrapolate to a verdict on all educational technology. The optimists cite carefully-designed-deployment outcome data and extrapolate to a verdict on what platforms will produce at scale in the wild. Neither extrapolation is licensed by the underlying study. Both extrapolations get made anyway.

Here is the canonical example. The OECD PISA 2022 report finds that **students who spend up to one hour per day on digital devices for leisure score approximately 49 points higher in mathematics than students who spend five to seven hours per day, even after adjusting for socioeconomic profile**.[^1] (A working version of this book's outline carried a "6+ hours / 66 points" figure; that specific combination does not appear in the OECD primary sources. The verified figure is 49 points at the 5–7 hours vs. up to 1 hour comparison. I am citing the corrected figure throughout; the original 66 was either a transposition error or a figure pulled from a secondary source that did not survive checking. The discipline this chapter teaches starts with this kind of correction.)

The 49-point finding is real, large, and important. It describes *leisure* digital-device use at saturating dosages. It does not describe what a constrained, evidence-anchored, measurement-equipped learning tool produces. The Horvath move — taking the 49-point finding as evidence that *classroom technology* harms learning — is the butter-knife move. The data describe one regime (high-dosage, leisure, indiscriminate). The conclusion is being applied to a different regime (purpose-built, instrumented, learning-targeted). They are not the same.

This chapter has one job: to teach you the discipline of refusing the extrapolation in either direction, and to give you the evidence base that the rest of the book will cite. By the end you will be able to walk into a vendor pitch or a research seminar and audit the evidence claim in front of you. The chapter is long because the discipline takes practice and because the citations earn their density. Each citation does work. None is decorative.

---

## What Horvath proves beyond reasonable doubt

I want to start with what Horvath gets right, for two reasons. The first is voice discipline: a chapter that opens by listing where the critique fails reads as score-settling, and the chapter is not score-settling. The second is structural: the move the chapter is teaching is *grant what is supported, then specify where the argument overreaches*. The move has to be modeled before it can be taught.

Horvath's *The Digital Delusion* (2025)[^2] marshals a substantial body of correlational and meta-analytic evidence that, taken as a whole, makes three claims that are well-supported.

**Claim 1: Classroom technology, deployed indiscriminately at high dosages, is on average associated with worse learning outcomes.** The PISA correlations are real. The TIMSS and PIRLS findings track. The Felisoni / Stroebe / Kuznekoff–Titsworth body of work on attention and academic performance is real. The smartphone-in-the-classroom distraction effect — students whose peers use phones during class score about 15 points lower on PISA's mathematics scale, even after adjusting for SES[^1] — is large enough to matter and replicated across countries.

**Claim 2: The meta-analytic effect of EdTech, averaged across studies, is approximately +0.29 standard deviations.** Horvath cites this as the average across approximately 400 meta-analyses encompassing more than 21,000 studies.[^3] The figure is consistent with the broader Hattie-tradition synthesis. *d* = 0.29 is moderate by Cohen's conventions and below Hattie's 0.40 hinge.

**Claim 3: Most claims of EdTech effectiveness in the practitioner literature do not survive methodological scrutiny.** Self-report bias. Satisfaction-as-proxy-for-learning. Single-cohort studies. Vendor-funded evaluations. The missing-control problem. All real, all pervasive.

The chapter grants all three. Horvath is not wrong about what the average dose of EdTech, in the average context, produces. He is not wrong that the practitioner literature is methodologically thin. He is not wrong that PISA 2022 is telling us something we should take seriously about device-use dosages. If you take away nothing else from the next thirty pages, take this: **the average EdTech deployment in the average context is not producing learning, and the average vendor claim cannot be trusted at face value.** That is a defensible reading of the existing literature, and any architecture chapter that ignores it is doing the wrong work.

The Computational Skepticism Substack review I published on Horvath grants these three claims explicitly.[^4] The review is the worked example I am going to walk through in the middle of this chapter. The move starts with the grant.

---

## Where Horvath overreaches

The overreach has three components. Each will appear again in the architecture chapters; the move is worth getting right here.

### Overreach 1: The 0.40 hinge as absolute binary

Hattie's *Visible Learning* (2009) reported an average effect of all the educational interventions Hattie reviewed of approximately *d* = 0.40, and labeled this the *"hinge point"* — the threshold above which an intervention is plausibly producing real value at reasonable cost.[^5] The hinge is widely used in EdTech debate as a cutoff: above 0.40 is "good," below is "bad." Horvath uses the 0.40 this way.

The honest reading is sharper. The 0.40 figure is not a threshold of effectiveness; it is the *average* effect across Hattie's database. The figure has been substantially critiqued — Simpson 2020 on the meta-meta-analysis problem (averaging averages-of-averages without sample-size correction inflates the variance into noise);[^6] Kraft 2020 on pre-post designs systematically inflating effect sizes; Eacott on the philosophical problems with reducing education to a single quantifiable metric. The 0.40 should be read as a **cost-effectiveness guideline** — interventions producing small effects at large cost are bad buys — not as a binary classification rule. Below-0.40 effects can be very important in specific contexts: small effects on equity-relevant outcomes for marginalized populations; small effects on long-term outcomes that compound across years; small effects in domains where any positive shift is hard-won.

The chapter's discipline, which I'll deploy repeatedly: **use 0.40 as guideline. Never as verdict.** When you see a vendor claim citing "above Hattie's hinge" without context, you are looking at the binary mis-use. When you see a skeptic dismissing an intervention because *d* = 0.32, you are looking at the same mis-use in reverse.

### Overreach 2: The "nearly every context" claim

Horvath argues, in the book and in supporting essays, that EdTech fails in *nearly every context*. The claim is provably false. The chapter only needs *one* counter-context to disprove "nearly every"; the ITS literature provides several.

- **VanLehn 2011** — step-based ITS produces *d* = 0.76, statistically indistinguishable from human tutoring (*d* = 0.79). Answer-based CAI produces *d* = 0.31.[^7] The structural finding: *step-grain interactivity matters more than whether the tutor is human or machine*.
- **Kulik & Fletcher 2016** — 50 controlled evaluations of ITS, median effect *g* = 0.66.[^8]
- **Graesser et al. 2005, AutoTutor on Newtonian physics** — *d* = 0.75–1.22.[^9]
- **Roschelle et al. 2016, ASSISTments Maine RCT** — *g* ≈ 0.22 on a state math assessment.[^10]

These are not vendor claims. They are peer-reviewed effect sizes from controlled evaluations across thirty years. The ITS literature is the counter-context. *Nearly every* is a universal quantifier. One counter-context is sufficient to disprove it.

### Overreach 3: The selection of meta-analyses

Horvath's +0.29 is an average across a sample of meta-analyses. The averaging operation hides enormous variance. Some meta-analyses in the same database report effects above 0.50 (well-designed CAI, retrieval-practice deployments, computer-assisted reading programs). Some report null effects (most ed-tech-in-K-12-math broadly defined). The chapter should name this: *averaging across a heterogeneous literature is not the same as showing the median context.* The averaging operation is precisely the move Horvath's own critique of EdTech vendors objects to when vendors do it. You cannot reasonably criticize vendor cherry-picking by performing the inverse cherry-pick.

---

## What Khan gets right

Symmetry. If Horvath gets a "what he gets right" paragraph, Khan gets one too. The chapter's tone is patient, not partisan.

Khan's *Brave New Words* (2024) is the optimistic case for AI in education. Strip the optimism and the structural claim is one I want to grant.

**The promise is real.** Bloom's 1984 "2-sigma" finding — that one-on-one human tutoring produces *d* = 2 against conventional instruction — has been substantially revised down by VanLehn 2011 to *d* = 0.79. Still very large. The Kestin et al. 2025 finding for a research-designed Harvard physics AI tutor — *d* ≈ 0.7–1.3 in a single course (PS2, *N* = 233, Fall 2023) — is the strongest existing evidence that *some* AI tutoring deployments can produce gains in the upper range of human-tutoring effects, in a single carefully-designed context.[^11] The promise that AI tutoring *can* approach the human-tutoring effect size is supported by evidence. It is supported by *some* evidence, in *some* contexts, with *very specific* design discipline. But it is supported.

**Engagement growth is real.** Khanmigo's growth from 40,000 to 700,000 students in the 2024–25 school year across 380+ district partners reflects substantial real demand for AI tutoring as a category. Common Sense Media's 4-star rating is a non-trivial third-party endorsement of educational quality and safety.

**The problem is not the AI.** This is the chapter's central concession to the Khan reading, and it is also Khan's own most recent reading: *the AI itself is not the source of the failure*. The Bastani PNAS 2025 finding makes this point empirically. Same GPT-4 underneath, two prompt wrappers, opposite outcomes. The model is not the variable. The wrapper is.

Where Khan overreaches: treating engagement-as-proxy-for-learning, treating growth-as-proof-of-effect, treating the optimistic case as if the evidence were settled. The chapter takes Khan's promise seriously without granting Khan's measurement choices.

---

## Bastani PNAS 2025 — the chapter's central anchor

The single most consequential generative-AI-in-education result published to date. I want to spend real length on this study because every architecture chapter that touches Ask AI will reference back to it.

**Citation, in full:** Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., & Mariman, R. (2025). Generative AI without guardrails can harm learning: Evidence from high school mathematics. *Proceedings of the National Academy of Sciences*, 122(26), e2422633122. DOI: 10.1073/pnas.2422633122.[^12]

**Design.** Field experiment in a Turkish high school. *N* ≈ 1,000 students, grades 9–11. Math practice sessions across a multi-week curriculum. Three conditions, random assignment:

1. **No-AI control.** Standard practice, no LLM access.
2. **GPT Base.** GPT-4 wrapped in a standard ChatGPT-style chat interface. Students could ask whatever they wanted; the model would help in its default helpful-assistant mode.
3. **GPT Tutor.** GPT-4 wrapped in a teacher-designed system prompt. The wrapper injected pedagogical hints, refused to give complete answers, structured the interaction around the student externalizing a reasoning step before the model advanced.

The underlying model was *the same* in both AI conditions. Same weights. Same temperature. Same training. The only thing that changed was the wrapper — roughly a few hundred tokens of system prompt and a small amount of conversational scaffolding.

**Results during practice (with AI access).**

- GPT Base: **48% higher** math practice performance vs. no-AI control.
- GPT Tutor: **127% higher** math practice performance vs. no-AI control.

Both numbers look like wild success. If you were running the engagement dashboard for either deployment, you would be writing a press release.

**Results on the subsequent exam (without AI access).**

- GPT Base: **17 percentage points lower** than no-AI control on the post-practice exam.
- GPT Tutor: statistically indistinguishable from no-AI control on the post-practice exam.

Read those numbers again. Note the precise figure: **17 percentage points**, not 17%. Popular summaries sometimes report this as "17% lower"; the precise figure is 17 percentage points, which on the underlying scale is approximately half a standard deviation of durable-learning damage relative to no AI at all. The Khan growth numbers and the Horvath PISA numbers both work in absolute terms; the Bastani exam decrement is in the same currency. *Bastani is not in the noise.* It is large.

**Three claims fall out.**

**Claim A: In-session performance is not learning.** Bjork's distinction between *performance* and *learning* (Soderstrom & Bjork 2015)[^13] has now been demonstrated empirically for LLM-mediated practice. Students felt smarter, performed better in-session, and learned less. The performance metric and the learning metric pointed in opposite directions for the GPT Base condition.

**Claim B: The wrapper, not the model, is the variable.** Same GPT-4 underneath both conditions. Different prompt design. Outcomes diverge by roughly half a standard deviation on the durable measure. The model was not the source of either outcome. The model was a willing actor. The wrapper made the pedagogical decisions.

**Claim C: The harm from naïve deployment is not subtle.** A 17-percentage-point exam decrement is not "AI is mildly suboptimal." It is *unguarded AI in this context made students substantially worse than they would have been without it*. This is the empirical anchor for the Chapter 1 claim that **a platform without opinions is a platform that will reliably reproduce the GPT Base outcome.**

I want to be honest about what Bastani is and is not. It is *one RCT*, in *one country*, in *one subject domain*, at *one age range*. The replication question is open. The chapter does not treat Bastani as definitive — it treats Bastani as *the strongest single result currently published*. The "What would change my mind" section at the bottom of this chapter names the replication question explicitly. Until the replications arrive, Bastani is what the field has.

---

## The ITS literature — what works, and what does not transfer

Chapter 3 has to teach you to keep ITS and generative-AI evidence in *separate buckets*. ITS results from 1995–2020 do not automatically transfer to a generative chatbot in 2026. Vendor marketing routinely cites the ITS literature to support generative-AI deployments. That is a category error. The two literatures share a name and almost nothing else.

The ITS canon worth holding in mind:

**VanLehn 2011** [step-based ITS]. The canonical meta-analysis. Step-based ITS produces *d* = 0.76 — statistically indistinguishable from human tutoring (*d* = 0.79). Answer-based CAI produces *d* = 0.31. **The structural finding: step-grain interactivity matters more than whether the tutor is human or machine.** This is the finding the architecture's Ask AI mode operationalizes in Chapter 6 — the design discipline of *requiring the student to externalize a reasoning step before the system advances* is the step-grain interactivity move from VanLehn, transposed into the generative-AI context.

**Kulik & Fletcher 2016** [ITS]. 50 controlled evaluations. Median effect *g* = 0.66. Importantly: larger effects on locally-developed tests than on standardized tests. The "teach to the test" warning, which transfers to generative-AI tutors that can be steered toward whatever assessment they will be graded against.

**Steenbergen-Hu & Cooper 2013** [ITS]. The cold-water finding. K–12 mathematics, *g* = 0.01–0.09 overall, *g* = –0.18 for low-achieving K–12 students.[^14] The college sample (2014 companion) showed *g* ≈ 0.37–0.43. The structural warning: ITS that work in college often fail in K–12, where motivation and prior knowledge differ substantially. Any platform claiming K–12 outcomes from college-validated ITS evidence is committing a category error.

**AutoTutor** [ITS, dialog-based]. *d* = 0.7–0.8 average; Why/AutoTutor on Newtonian physics *d* = 0.75–1.22 (Graesser et al. 2005). The closest ITS analog to a chatbot: turn-based natural-language dialog, hints, questions. The historical baseline against which generative chatbots should be benchmarked.

**ASSISTments** [ITS, online homework]. *g* ≈ 0.22 in the Maine RCT (≈ three-quarters of a school year of additional learning), *g* ≈ 0.10 a year after in the North Carolina replication. The wild-deployment effect (*g* ≈ 0.1–0.2) is substantially smaller than the controlled-evaluation effect (*g* ≈ 0.66) — the gap every EdTech evaluation has to negotiate. **In real classrooms, the same intervention produces about a third of the effect it produces in the lab.**

The chapter's discipline: every effect-size citation in this section is tagged *[ITS]*. None of these effect sizes automatically transfer to a generative chatbot in 2026. They are the field's historical baseline. Generative-chatbot results from 2024–2025 are early, methodologically uneven, and dominated by single-course trials. The two literatures share a name and almost nothing else.

---

## The spaced-repetition canon

The retrieval-practice and spacing literature is the most methodologically mature subfield in instructional research. The effect sizes are large, the mechanisms are well-understood, and the canonical citations have stood up to thirty years of replication. The architecture's Quiz Me mode is built directly on this literature.

**Roediger & Karpicke 2006** [retrieval-practice]. The testing effect with educationally meaningful prose. At 5-minute retention, repeated study beats testing (83% vs. 71%). At 1-week retention, the order reverses: 40% after study-only, 61% after three test trials.[^15] The mechanism is retrieval practice — the act of pulling information out of memory changes the memory. Anki, the AnKing deck, every retrieval-practice tool you have ever used: this is the paper they are built on.

**Karpicke & Blunt 2011** [retrieval-practice]. *Science* 331(6018), 772–775. The largest single-experiment effect size in the literature: retrieval practice outperformed elaborative concept mapping by **d ≈ 1.50** on a one-week delayed test, including inference questions.[^16] Treat this as a *laboratory ceiling*, not a deployment expectation. The single-experiment number is real; the population effect at scale will not match it.

**Adesope, Trevisan & Sundararajan 2017** [retrieval-practice]. The major meta-analysis: 188 experiments, 272 independent effect sizes. Practice tests vs. re-studying *g* = 0.51; vs. filler/no activity *g* = 0.93; in classrooms specifically *g* ≈ 0.67. **The cleanest "Quiz Me beats re-reading" claim in the literature.**[^17]

**Cepeda, Pashler, Vul, Wixted & Rohrer 2006** [spaced-repetition]. *Psychological Bulletin*. 839 assessments across 317 experiments and 184 articles. Spaced reviews produce more durable retention than massed reviews; the optimal inter-study interval scales with the retention horizon.[^18] This is the paper Anki's algorithm implements. The pattern is robust.

**Cepeda et al. 2008** [spaced-repetition]. Follow-up showing spacing effects in learning with retention intervals up to 350 days. **The spacing benefit does not decay over a year.** This is the empirical license for the architecture's commitment to scheduling reviews over multi-month horizons rather than cramming over weeks.

**Pan & Rickard 2018** [retrieval-practice, transfer]. *Psychological Bulletin* 144(7), 710–756. Meta-analysis on transfer of test-enhanced learning. 192 effect sizes from 122 experiments. **Pooled transfer effect d = 0.40, 95% CI [0.31, 0.50].** Larger transfer in medical contexts specifically.[^19] This is the citation that licenses Quiz Me's role in clinical-reasoning curricula — retrieval practice transfers beyond the items it was practiced on, more reliably in medical training than in laboratory tasks.

The discipline: distinguish *retrieval-practice* (mechanism), *spacing* (scheduling principle), and *FSRS/SM-2* (implementation). Each has different evidence and different effect-size magnitudes. Conflating them is the most common error in vendor marketing for flashcard tools. The Anki community's revealed-preference outcomes in medical-school Step 1 preparation — which I described in Chapter 2 — sit on the retrieval-practice + spacing canon; they do not sit on the FSRS-specifically literature, which is current but lacks peer-reviewed academic citation for the learning-outcome claim.[^20]

---

## The CBL literature

The architecture's Case Study mode rests on the case-based learning evidence base. The primary citation:

**Thistlethwaite, Davies, Ekeocha, Kidd, MacDougall, Matthews, Purkis & Clay 2012** [medical-CBL]. *Medical Teacher* 34(6), e421–e444. *The effectiveness of case-based learning in health professional education: A BEME systematic review: BEME Guide No. 23.*[^21] The systematic review covered 104 papers across medicine, dentistry, veterinary, nursing/midwifery, and allied health. The central finding: CBL is consistently rated highly by students and educators; the evidence base is heterogeneous in design but consistent in direction; CBL improves student engagement and learning outcomes.

The chapter's nuance, which the architecture inherits. Thistlethwaite is the most-cited synthesis on CBL effectiveness. **The review is on *human-facilitated* CBL** — small-group discussion led by a clinical educator. The evidence does not directly license *solo asynchronous AI-facilitated CBL*, which is what Medhavy's Case Study mode is. The architecture has to make the bet that the *case structure* is doing real work and the *human facilitator* is not the entirely irreplaceable component — but the bet is not directly evidenced by the Thistlethwaite review.

I am naming the gap here so it cannot be papered over later. Chapter 6, where the four modes are specified, will return to this. The Case Study mode is licensed by Thistlethwaite *under the assumption* that pre-written, faculty-reviewed cases delivered with AI-facilitated structured prompts capture most of what the human-facilitated small-group setting was doing. That assumption is reasonable. It is not directly tested.

---

## The generative-assignment literature

The architecture's Glimmer mode rests on the generative-learning evidence base.

**Fiorella & Mayer 2016** [generative-learning]. *Educational Psychology Review* 28(4), 717–741. *Eight Ways to Promote Generative Learning*: summarizing, mapping, drawing, imagining, self-testing, self-explaining, teaching, enacting.[^22] Each strategy has its own research base. Self-testing and self-explaining have the strongest evidence. Summarizing and teaching are well-established. Drawing, imagining, mapping, and enacting are more domain-specific. The chapter's anchor for *what generative work means and why it matters*.

**Jonassen 1997** [generative-learning, ill-structured]. *Educational Technology Research and Development* 45(1), 65–94.[^23] The canonical distinction between **well-structured problems** (constrained, convergent, finite-rule) and **ill-structured problems** (multiple solutions, fewer manipulable parameters, uncertainty about which concepts are necessary). Information-processing theory grounds well-structured-problem instruction; constructivism and situated cognition ground ill-structured-problem instruction. The chapter's anchor for *why Glimmer is the right mode for ill-structured problems and Quiz Me is the right mode for well-structured problems*.

The discipline: generative assignments produce gains *under conditions*. Sufficient prior knowledge to generate. Appropriate scaffolding. Feedback on the generative artifact. The failure mode — novice learners asked to do unscaffolded generative work in ill-structured domains — is the *anxiety failure mode*: students freeze and produce nothing. Chapter 6 will specify the scaffolding discipline that prevents this. Chapter 3 names the literature.

---

## Worked example: walking through my published Horvath review

Now the chapter's worked example, per the TIKTOC. I want to walk through the audit pattern I applied to Horvath's *The Digital Delusion* in the review I published on the Computational Skepticism Substack.[^4] The audit is the chapter's meta-lesson: *this is how you read an EdTech evidence claim.* You will run this pattern again, on a vendor pitch or a paper, the next time you need to. The point of the chapter is to give you the form.

The audit had five moves.

**Move 1: Specify what Horvath actually claims.** I pulled out the three claims I named earlier in this chapter: indiscriminate-deployment harm, +0.29 meta-analytic average, methodological thinness of the practitioner literature. I stated them in their strongest form, not their weakest. The reviewer's first move is to make the argument as strong as the author would. **You cannot critique a position you have not first stated charitably.**

**Move 2: Specify what would have to be true for the claims to be supported.** PISA-style correlations would have to translate to causal effects (they don't, automatically — PISA is observational, not experimental). The meta-analytic average would have to be a representative summary of the underlying literature (it isn't, because the literature is heterogeneous and the averaging is across-meta-analyses, not within them). The "nearly every context" claim would have to survive a counter-example search (it doesn't, because the ITS literature is a counter-example).

This is the Spiegelhalter move from *The Art of Statistics*[^24] — *what would have to be true for this claim to be supported, and is that thing true?* It is the most useful epistemic instrument I know. It is the move that separates evidence-reading from evidence-citing.

**Move 3: Apply the threshold test.** Does the evidence support a verdict on *EdTech-in-general*, or only on *a specific subset of EdTech deployments*? The evidence supports a verdict on indiscriminate high-dosage classroom technology. It does not support a verdict on well-designed retrieval-practice apps, well-designed ITS, well-designed safeguarded AI tutoring with Bastani-style prompt wrappers, or well-designed CBL. The over-generalization is exactly the universal-quantifier move I described under "nearly every context."

**Move 4: State the residual.** What does Horvath get right that the field should not ignore? The +0.29 average is real. The PISA correlations are real. The methodological critique of vendor literature is real. These survive the audit. *The audit is not a dismissal.* The audit is a clarification of what the evidence actually licenses.

**Move 5: State the implication.** The book's response to Horvath is not to dispute his evidence. It is to specify the architecture that the evidence licenses *when deployed with discipline*. The Bastani PNAS finding makes this exact move: take Horvath's correctly-diagnosed indiscriminate-deployment harm, ask what wrapper produces the opposite outcome, build the architecture around the wrapper.

This is the pattern. Five moves. Specify, audit, threshold, residual, implication. You will run it again. The chapter teaches the form, not the verdict.

---

## A second worked example: how to read Khan Academy's efficacy claims

I want to deploy the same audit on the optimistic side, because the chapter's discipline requires symmetry. The target: Khan Academy's published efficacy claims for Khanmigo.

**Move 1: Specify the claim.** Khanmigo grew from 40,000 to 700,000 students across 380+ district partners in the 2024–25 school year. Common Sense Media gave it 4 stars. Khan Academy publishes case studies of districts where teacher and student satisfaction is high.

**Move 2: What would have to be true for the claim to support a learning-outcomes inference?** A controlled comparison with a no-Khanmigo condition. Durable-learning outcomes measured on transfer-bearing assessments at delay. Independent evaluation. None of these is present in the cited evidence. The Common Sense Media rating is on educational quality and safety, not durable learning outcomes; their own review notes *"persistent prompting would lead to Khanmigo offering a more complete answer"* — the guardrail leaks.[^25]

**Move 3: Threshold test.** What does the evidence support? Adoption is real. Demand is real. Satisfaction surveys directionally favor the product. What does the evidence not support? A learning-outcomes claim.

**Move 4: Residual.** Adoption and satisfaction are not nothing. A platform 700,000 students are using is a platform with substantial usability and educational-design competence. That residual is real.

**Move 5: Implication.** The Khan claim is *a satisfaction-and-adoption claim, not a learning-outcomes claim*. Until WestEd or an equivalent independent evaluator publishes a controlled-comparison RCT with durable-learning outcomes at delay, the learning-outcomes inference is not licensed by the cited evidence. The DiCerbo "IDK IDK" acknowledgment is consistent with this read: the people inside Khan Academy with access to the actual usage data are seeing what the published metrics could not.

Same audit. Same five moves. The point: **Khan and Horvath are using the same kind of evidence in opposite directions; both deserve the same audit.** A chapter that disciplines one side without the other is doing the wrong work.

---

## A third worked example: the Kestin Harvard physics RCT

One positive case, to keep the chapter from feeling like it consists entirely of negative reads.

**Citation.** Kestin, G., Miller, K., Klales, A., Milbourne, T., & Ponti, G. (2025). *Scientific Reports* 15. Harvard Physical Sciences 2, *N* = 233 (Fall 2023). A custom AI tutor designed with the same research-based pedagogical principles as the in-class active-learning sessions — segmented content, formative checks, deliberate misconception traps. Students learned roughly twice as much in less time on the AI tutor than in the active-learning class; reported effect sizes *d* ≈ 0.7–1.3.[^11]

**The audit.**

The result is large and credible *for what it measures*. One institution. One course. One professor. One custom-built tutor with research-based design principles. Comparison to a single active-learning session rather than a full course.

The result does *not* support *"any AI tutor is twice as good as active learning."* That is the inference the paper does not license. A vendor citing Kestin to support a generic AI-tutor product is committing the inference error.

The result *does* support *"with sufficient pedagogical design discipline, generative AI tutors can produce effect sizes in the human-tutoring range in well-defined contexts."* This is the chapter's positive read.

**Kestin and Bastani together specify the chapter's central claim: the wrapper is the variable.** Bastani shows the negative case (unguarded wrapper, –17 percentage points). Kestin shows the positive case (research-designed wrapper, *d* = 0.7–1.3). Both used current-generation frontier LLMs. The difference is the design discipline applied to the wrapper. The architecture this book describes is the systematic specification of that design discipline. Chapter 6's Ask AI mode is the place where Bastani's "GPT Tutor" wrapper becomes a four-mode integrated system.

---

## Common misconceptions

**Misconception 1: "Hattie has been debunked. Why are you citing him at all?"**

Plausible. The Hattie critique literature is substantial — Simpson, Kraft, Eacott, and many others. The honest reading: the 0.40 hinge is a real summary statistic in a real database, *and* its mis-use as a binary verdict is widely criticized. The chapter cites Hattie correctly — as a cost-effectiveness guideline — and names the critique. The figure is not the problem. The binary application is the problem. The chapter teaches the right use; it does not erase the figure.

**Misconception 2: "You're cherry-picking the ITS literature to counter Horvath."**

Plausible. The response: the chapter named the counter-context explicitly. ITS is a counter-context. Horvath's claim was *nearly every*. *Nearly every* is a universal quantifier. One counter-context is sufficient to disprove a universal quantifier. The move is not cherry-picking; it is responding to the form of the claim. If Horvath's claim were "the average effect of indiscriminately-deployed EdTech is small," the chapter would grant it. The chapter is responding to the over-generalization, not to the underlying observation.

**Misconception 3: "You're treating Bastani as definitive when it's one RCT."**

Plausible and important. The response: the chapter treats Bastani as *the strongest single result currently published*, not as definitive. The replication question is named in the "What would change my mind" section. Until the replications arrive, Bastani is what the field has. If the field had three independent replications, the chapter would lean on the replications rather than on the single PNAS paper. It does not. The chapter's discipline is *cite the strongest result available, name its limits, return to it if replications arrive or fail to arrive*.

**Misconception 4: "You're using effect sizes from different literatures interchangeably."**

Plausible. The response: every effect size in this chapter carries a class tag. *[ITS]*. *[retrieval-practice]*. *[generative-AI]*. *[CBL]*. *[generative-learning]*. The discipline of not interchanging them is the discipline the chapter is teaching. A vendor citing VanLehn 2011 to support a generative-AI deployment is making the category-error mistake. A vendor citing Bastani 2025 to support an ITS deployment is making the inverse mistake.

---

## Exercises

### Exercise 3.1 — Audit a vendor effect-size claim (Evaluate)

A vendor presents the following claim at a district procurement meeting: *"Our adaptive math platform produces an effect size of g = 0.45, based on a meta-analysis of 12 implementation studies across 47 schools."*

Identify three specific questions you must ask before accepting this claim. For each question, name (a) the audit move from this chapter that produces the question (specification, what-would-have-to-be-true, threshold test, residual, implication), (b) the specific reasoning error the question is designed to catch, and (c) the answer the vendor would have to give for the claim to be supported.

Produce a one-page memo for the district's procurement committee summarizing the three questions and the audit framework.

### Exercise 3.2 — Stress-test the "nearly every context" claim (Analyze)

Horvath argues that EdTech fails *in nearly every context*. The chapter argues this is provably false using the ITS literature as a counter-context.

Pick one of the four literatures the chapter walks through — ITS, retrieval-practice + spacing, CBL, or generative-learning — and write a 600-word analysis that does three things: (1) names *one specific class of EdTech deployment* in that literature where the evidence runs strongly in favor of the deployment, with effect-size citations; (2) names *one specific class of EdTech deployment* in the same literature where the evidence is null or negative; (3) specifies the design variable that distinguishes the two classes.

The exercise is meant to give you the experience of arguing from inside a literature rather than from above it.

### Exercise 3.3 — Apply Bastani to Ask AI guardrail design (Apply)

The chapter's third TIKTOC-mandated exercise. The Bastani PNAS finding shows that the same GPT-4 underneath a teacher-designed wrapper preserved learning while underneath an unguarded wrapper destroyed it.

What does the Bastani finding imply for the Ask AI mode's guardrail design in the four-layer architecture? Write a 500-word design specification for the Ask AI guardrail that does the following: (1) names three specific design decisions the Bastani finding justifies; (2) names one design decision the Bastani finding does *not* justify but that you would still recommend (and why); (3) identifies the measurement-layer signal that would tell you whether the guardrail is working as intended.

This is the kind of citation-from-evidence-base move the rest of the book does at every architecture decision. The exercise is the rehearsal.

---

## What would change my mind

The chapter's central claim is that the field's two dominant readings of the EdTech evidence — Khan's optimism and Horvath's pessimism — both commit the Butter Knife Fallacy by extrapolating from data describing one regime to verdicts about a different regime; the wrapper-as-variable claim, anchored on Bastani PNAS 2025 plus Kestin et al. 2025, is the strongest current empirical finding; and the architecture this book describes is the systematic specification of the wrapper discipline that the evidence licenses. Four findings would force me to revise.

A successful Bastani replication in a non-Turkish context, with a different age group and subject domain, would substantially strengthen the central claim. A failed replication would substantially weaken it. The PNAS finding is currently the single strongest result in the literature; if it does not replicate, the wrapper-as-variable claim weakens significantly and the chapter's central anchor moves to Kestin alone, which is a narrower base. A rigorous independent RCT of Khanmigo or LearnLM with no-treatment control and durable-learning outcomes at delay would update my read of vendor-published evidence — if such an RCT produces large positive durable-learning effects, the chapter's skepticism of vendor evidence softens; if it produces null effects, the skepticism sharpens. A direct comparison of well-designed solo asynchronous AI-facilitated CBL vs. human-facilitated CBL would address the gap I named in the Thistlethwaite literature; if the AI-facilitated version produces equivalent outcomes, the Case Study mode's evidence base is more robust than the chapter currently claims. A meta-analytic update synthesizing the 2024–2026 generative-AI-in-education studies — which would by then number in the high tens or low hundreds — would let the chapter cite a meta-analytic effect size for AI tutoring rather than relying on Bastani plus Kestin as the two anchor studies. The current reliance on two studies is honest but thin; the architecture's evidence base improves substantially as the literature accumulates.

---

## Still puzzling

1. Why has the field not produced more RCTs of AI tutoring? Bastani and Kestin are anomalously rigorous in a literature dominated by satisfaction surveys. The structural reasons are real — RCTs are expensive, vendors have no incentive to publish negative results, journals have not yet calibrated their expectations for the new class of study — but the gap remains striking. Three years into the most heavily-funded edtech moment in history, the peer-reviewed durable-learning evidence base for generative-AI tutoring fits on a single notecard.

2. What does the +0.29 EdTech meta-analytic average actually mean? It is the average across an enormously heterogeneous literature. The average masks variance that is itself the most informative finding. Horvath uses the average as a verdict; the chapter argues the variance is the actual signal. But specifying *which* contexts produce *which* effects requires meta-regression work that the field has not done at scale. The averaging operation hides the field's most interesting question.

3. How does the wrapper-as-variable finding scale beyond Bastani? Bastani used a teacher-designed hint wrapper. What if the wrapper is engine-selected per learner, per concept, per moment, as the four-layer architecture proposes? Does the wrapper's value scale? Plateau? Become brittle? The chapter cannot answer this. Chapters 6 and 7 explore it. The chapter names the question as the bet the book is making.

4. The IDK-IDK pattern: is it a Khan Academy implementation problem, a deeper property of how students *adapt* to any unsafeguarded chatbot, or both? The architecture commits to phase-gated externalization as the prevention; whether that commitment is strong enough is itself an empirical question Chapter 11 will address honestly.

---

## Bridge to Chapter 4

You now hold the evidence base. Every architecture chapter from here on will *cite* rather than *argue*. Chapter 4 delivers the blueprint: why bolt-on tools cannot produce the integrated signal an intelligent textbook requires, and what each of the four layers must do for the integration to function.

The reader will arrive at Chapter 4 with a reasonable objection. *I could buy an LMS, a chatbot, a spaced repetition tool, and a case study library and connect them. Why do I need a platform?* The bolt-on failure answers before the question finishes. Chapter 4 names the seven signals that require live instrumentation across layers, walks through one student session in Medhavy's cancer textbook deployment to show what data flows between layers at each step, and identifies the specific signal lost at each seam when the tools are assembled rather than integrated.

The architecture is the answer. The evidence base — Bastani, Kestin, VanLehn, Roediger-Karpicke, Cepeda, Pan & Rickard, Adesope, Thistlethwaite, Fiorella & Mayer, Jonassen, plus Hattie used correctly and Horvath audited rather than dismissed — is the warrant. The chapters that follow are the elaboration.

The discipline goes on the page. **The platform is opinionated; the model has no opinions of its own.** That sentence is the entire book. The evidence base licenses every opinion the platform will commit to. Chapter 4 begins the commitments.

---

## References

[^1]: OECD. (2023). *PISA 2022 Results (Volume I): The State of Learning and Equity in Education*. OECD Publishing. https://www.oecd.org/en/publications/pisa-2022-results-volume-i_53f23881-en.html [49-point math gap at 5–7 hours/day vs. up to 1 hour leisure digital-device use, adjusted for SES; ~15-point distraction effect from peer phone use in class]

[^2]: Horvath, J. C. (2025). *The Digital Delusion: How EdTech Has Failed Our Schools — and How to Fix It*. [Publisher and exact pagination [verify] before final draft.]

[^3]: Horvath cites the +0.29 average in the book and supporting essays. The figure is consistent with the broader Hattie-tradition synthesis. See also the *Education Next* review of Horvath's *Digital Delusion*: https://www.educationnext.org/latter-day-luddite-pulls-the-plug-on-edtech-book-review-digital-delusion-jared-cooney-horvath/

[^4]: Brown, N. B. *Review: The Digital Delusion*. Computational Skepticism Substack. [verify exact URL before final draft]

[^5]: Hattie, J. (2009). *Visible Learning: A Synthesis of Over 800 Meta-Analyses Relating to Achievement*. Routledge. See also https://visible-learning.org/hattie-ranking-influences-effect-sizes-learning-achievement/

[^6]: Simpson, A. (2020). The Misdirection of Public Policy: Comparing and Combining Standardised Effect Sizes. Plus Kraft, M. A. (2020). Interpreting Effect Sizes of Education Interventions. *Educational Researcher* 49(4), 241–253. See also the David Didau critique compilation: https://daviddidau.substack.com/p/visible-learning-invisible-errors

[^7]: VanLehn, K. (2011). The relative effectiveness of human tutoring, intelligent tutoring systems, and other tutoring systems. *Educational Psychologist*, 46(4), 197–221. https://doi.org/10.1080/00461520.2011.611369

[^8]: Kulik, J. A., & Fletcher, J. D. (2016). Effectiveness of intelligent tutoring systems: A meta-analytic review. *Review of Educational Research*, 86(1), 42–78. https://doi.org/10.3102/0034654315581420

[^9]: Graesser, A. C., et al. (2005). AutoTutor: A tutor with dialogue in natural language. *Behavior Research Methods, Instruments, & Computers*, 36(2), 180–192. https://link.springer.com/article/10.3758/BF03195563

[^10]: Roschelle, J., et al. (2016). Online mathematics homework increases student achievement. *AERA Open*. https://files.eric.ed.gov/fulltext/ED631720.pdf

[^11]: Kestin, G., Miller, K., Klales, A., Milbourne, T., & Ponti, G. (2025). AI tutoring outperforms in-class active learning: An RCT introducing a smart learning companion. *Scientific Reports*, 15 (online 3 June 2025). https://www.nature.com/articles/s41598-025-97652-6. See also Harvard Gazette coverage: https://news.harvard.edu/gazette/story/2024/09/professor-tailored-ai-tutor-to-physics-course-engagement-doubled/

[^12]: Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., & Mariman, R. (2025). Generative AI without guardrails can harm learning: Evidence from high school mathematics. *Proceedings of the National Academy of Sciences*, 122(26), e2422633122. https://doi.org/10.1073/pnas.2422633122. PubMed PMID 40560616. Preprint: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4895486

[^13]: Soderstrom, N. C., & Bjork, R. A. (2015). Learning versus performance: An integrative review. *Perspectives on Psychological Science*, 10(2), 176–199.

[^14]: Steenbergen-Hu, S., & Cooper, H. (2013). A meta-analysis of the effectiveness of intelligent tutoring systems on K–12 students' mathematical learning. *Journal of Educational Psychology*, 105(4), 970–987.

[^15]: Roediger, H. L., III, & Karpicke, J. D. (2006). Test-enhanced learning: Taking memory tests improves long-term retention. *Psychological Science*, 17(3), 249–255. https://pubmed.ncbi.nlm.nih.gov/16507066/

[^16]: Karpicke, J. D., & Blunt, J. R. (2011). Retrieval practice produces more learning than elaborative studying with concept mapping. *Science*, 331(6018), 772–775.

[^17]: Adesope, O. O., Trevisan, D. A., & Sundararajan, N. (2017). Rethinking the use of tests: A meta-analysis of practice testing. *Review of Educational Research*, 87(3), 659–701.

[^18]: Cepeda, N. J., Pashler, H., Vul, E., Wixted, J. T., & Rohrer, D. (2006). Distributed practice in verbal recall tasks: A review and quantitative synthesis. *Psychological Bulletin*, 132(3), 354–380. https://pubmed.ncbi.nlm.nih.gov/16719566/

[^19]: Pan, S. C., & Rickard, T. C. (2018). Transfer of test-enhanced learning: Meta-analytic review and synthesis. *Psychological Bulletin*, 144(7), 710–756. https://pubmed.ncbi.nlm.nih.gov/29733621/

[^20]: FSRS (Free Spaced Repetition Scheduler) — open-source spaced-repetition algorithm used in Anki and several other tools. Internal benchmark data reports ~20–30% fewer reviews at equivalent retention vs. SM-2, with ±5.3% retention error. Peer-reviewed academic citation for learning-outcome comparison [pending]; the algorithm's documentation is the current primary source.

[^21]: Thistlethwaite, J. E., Davies, D., Ekeocha, S., Kidd, J. M., MacDougall, C., Matthews, P., Purkis, J., & Clay, D. (2012). The effectiveness of case-based learning in health professional education. A BEME systematic review: BEME Guide No. 23. *Medical Teacher*, 34(6), e421–e444. https://doi.org/10.3109/0142159X.2012.680939. PubMed PMID 22578051.

[^22]: Fiorella, L., & Mayer, R. E. (2016). Eight ways to promote generative learning. *Educational Psychology Review*, 28(4), 717–741. https://doi.org/10.1007/s10648-015-9348-9

[^23]: Jonassen, D. H. (1997). Instructional design models for well-structured and ill-structured problem-solving learning outcomes. *Educational Technology Research and Development*, 45(1), 65–94. https://doi.org/10.1007/BF02299613

[^24]: Spiegelhalter, D. (2019). *The Art of Statistics: How to Learn from Data*. Basic Books.

[^25]: Common Sense Media. *Khanmigo AI Rating*. https://www.commonsensemedia.org/ai-ratings/khanmigo

---

*Chapter 4: The Four Layers →*
