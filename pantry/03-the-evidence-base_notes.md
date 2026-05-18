# Research Notes — Chapter 3: The Evidence Base

*Working pantry document for the Medhavy book project. Research underpinning the load-bearing Chapter 3 — the evidence base every architecture chapter will cite. Citation-dense. Pulls heavily on `ask-ai-research.md`, `quiz-me-research.md`, `case-study-research.md`, `glimmer-research.md`, and Bear's published Horvath review on the Computational Skepticism Substack.*

*Compiled 2026-05-17 for the chapter-writer subagent. Maintained for revision.*

---

## Chapter summary

Chapter 3 is the book's load-bearing evidence chapter. It is the place where every later chapter's "the evidence shows" sentence either earns its weight or fails to. The chapter opens with the *Butter Knife Fallacy* — judging the scalpel's potential by observing its average misuse — and then walks through the four bodies of evidence that the architecture chapters will draw on: (1) what Horvath proves beyond reasonable doubt and where Horvath overreaches, (2) the Bastani PNAS 2025 finding as the single most consequential generative-AI-in-education result published to date, (3) the ITS canon (VanLehn 2011, Kulik & Fletcher 2016, AutoTutor, ASSISTments), (4) the spaced-repetition canon (Roediger & Karpicke 2006, Cepeda 2006, Pan & Rickard 2018), the CBL literature (Thistlethwaite 2012 BEME), and the generative-assignment literature (Fiorella & Mayer 2016, Jonassen 1997). The chapter's worked example is Bear's own published Horvath review, which is the chapter's meta-lesson: *this is how you read an EdTech evidence claim*. The chapter's central discipline: every effect size carries the context that makes it meaningful — the comparison condition, the population, the outcome measure, the retention interval, the cherry-pick risk. The chapter teaches Hattie's 0.40 hinge correctly — as a cost-effectiveness guideline, not an absolute binary — and disposes of the "nearly every context" overreach in Horvath by simply naming a context (ITS-style step-grain tutoring; well-designed retrieval practice) where the evidence runs strongly in the other direction. By the end of the chapter, the reader has the evidence base to read every later architecture chapter as a *deployment of evidence at the right grain*, not as a sequence of design opinions wearing evidence-clothing. The reader also has the diagnostic for spotting cherry-picked EdTech evidence claims when they encounter them — which they will, often, from vendors and from the literature.

---

## A. Conceptual foundations

### A.1 The Butter Knife Fallacy

The chapter's opening. The metaphor: a researcher publishes a paper concluding *kitchen knives cause finger lacerations*, based on a survey of 10,000 households reporting cuts. The data are real. The correlation is robust. The recommendation — *eliminate kitchen knives from households* — does not follow, because the data describe the average outcome of *all knife use, including untrained use, intoxicated use, child use, and use on inappropriate surfaces*. The data are silent on the question of what a trained chef using a properly sharpened chef's knife on a cutting board produces, because the survey did not separate those cases.

The PISA 2022 finding ([OECD 2023, *PISA 2022 Results Volume I*](https://www.oecd.org/en/publications/pisa-2022-results-volume-i_53f23881-en.html)) is the Butter Knife Fallacy in action. The OECD reports that **students who spent up to one hour per day for leisure on digital devices scored approximately 49 points higher in mathematics than students who spent five to seven hours per day, even after adjusting for students' and schools' socio-economic profile**. The finding is real, large, and important. It describes *leisure* digital-device use at saturating dosages. It does not describe what a constrained, evidence-anchored, measurement-equipped learning tool produces. The Horvath move — taking the 49-point finding as evidence that *classroom technology* harms learning — is the butter-knife move. The data describe one regime (high-dosage, leisure, indiscriminate); the conclusion is being applied to a different regime (purpose-built, instrumented, learning-targeted). The two are not the same.

[A note on the figure: the working TIKTOC referenced "6+ hours / 66-point drop" — that specific combination does not appear in the OECD reports. The closest verifiable OECD figure is 49 points at the 5–7 hours / >1 hour comparison; a related figure (PISA 2018) is the ~15-point distraction effect from other students' device use in class. Chapter 3 should use the 49-point figure with the correct threshold (5–7 hours vs. up to 1 hour). The 66 figure should not appear unless a primary source confirms it.]

The chapter's discipline: *the Butter Knife Fallacy is the most common reasoning error in EdTech debate*. Both Horvath and Khan commit it, in opposite directions. Horvath takes the average misuse data and extrapolates to a verdict on all technology. Khan takes the unusually positive deployment data (engagement growth, satisfaction surveys, the Kestin et al. Harvard physics outcome) and extrapolates to a verdict on all AI tutoring. The chapter's job is to teach the reader to refuse the extrapolation in either direction.

### A.2 What Horvath proves beyond reasonable doubt

Horvath's *The Digital Delusion* (2025) marshals a substantial body of correlational and meta-analytic evidence that, taken as a whole, makes three claims that are well-supported:

- **Classroom technology, deployed indiscriminately at high dosages, is on average associated with worse learning outcomes.** The PISA correlations are real. The TIMSS and PIRLS findings track. The Felisoni / Stroebe / Kuznekoff–Titsworth body of work on attention and academic performance is real. The smartphone-in-the-classroom distraction effect is large (~15 points on PISA's mathematics scale, even adjusting for SES).
- **The meta-analytic effect of EdTech, averaged across studies, is approximately +0.29 standard deviations.** Horvath cites this as the average across ~400 meta-analyses encompassing >21,000 studies ([Education Next book review](https://www.educationnext.org/latter-day-luddite-pulls-the-plug-on-edtech-book-review-digital-delusion-jared-cooney-horvath/)). The figure is consistent with the broader Hattie-tradition synthesis. A +0.29 effect size is *moderate* by Cohen's conventions and *below* Hattie's 0.40 hinge.
- **Most claims of EdTech effectiveness in the practitioner literature do not survive methodological scrutiny.** Self-report bias, satisfaction-as-proxy-for-learning, single-cohort studies, vendor-funded evaluations, and the missing-control problem are all real and pervasive.

The chapter should grant all three of these. Horvath is not wrong about what the average dose of EdTech, in the average context, produces. He is not wrong that the practitioner literature is methodologically thin. He is not wrong that PISA 2022 is telling us something we should take seriously about device-use dosages.

### A.3 Where Horvath overreaches

The overreach has three components:

- **The 0.40 hinge as absolute binary.** Hattie's *Visible Learning* (2009) reported an average effect of all the educational interventions Hattie reviewed of approximately *d* = 0.40, and labeled this the "hinge point" — the threshold above which an intervention is plausibly producing real value. ([Hattie ranking and effect sizes](https://visible-learning.org/hattie-ranking-influences-effect-sizes-learning-achievement/)). The hinge is widely used in EdTech debate as a cutoff: above 0.40 is "good," below is "bad." Horvath uses the 0.40 cutoff this way. The honest reading: the 0.40 figure is not a sharp threshold of effectiveness; it is the *average* effect across Hattie's database, and it has been substantially critiqued (Simpson 2020 on the meta-meta-analysis problem; Kraft 2020 on pre-post designs inflating effect sizes; Eacott on the philosophical problems with reducing education to a single quantifiable metric — see [Visible Learning critique compilation](https://daviddidau.substack.com/p/visible-learning-invisible-errors)). The 0.40 should be read as a cost-effectiveness guideline (interventions that produce small effects at large cost are not good buys), not as a binary classification rule. Below-0.40 effects can be very important in specific contexts (small effects on equity-relevant outcomes for marginalized populations; small effects on long-term outcomes; small effects that compound across years). The chapter's discipline: use 0.40 as guideline. Never as verdict.

- **The "nearly every context" claim.** Horvath argues that EdTech fails in nearly every context. The claim is provably false. ITS, when well-designed, produces effects substantially above 0.40 in well-defined contexts: VanLehn 2011 (*Educational Psychologist* 46(4), 197–221, [DOI 10.1080/00461520.2011.611369](https://www.tandfonline.com/doi/abs/10.1080/00461520.2011.611369)) finds step-based ITS producing *d* = 0.76, statistically indistinguishable from human tutoring (*d* = 0.79). Kulik & Fletcher 2016 (*Review of Educational Research* 86(1), 42–78, [DOI 10.3102/0034654315581420](https://journals.sagepub.com/doi/abs/10.3102/0034654315581420)) finds a median ITS effect of *g* = 0.66 across 50 controlled evaluations. AutoTutor on Newtonian physics produced *d* = 0.75–1.22 (Graesser et al. 2005, [Behavior Research Methods, Instruments, & Computers](https://link.springer.com/article/10.3758/BF03195563)). ASSISTments in the Maine RCT produced *g* ≈ 0.22 on a state math assessment ([Roschelle et al. 2016, *AERA Open*](https://files.eric.ed.gov/fulltext/ED631720.pdf)). The chapter only needs *one* counter-context to disprove "nearly every"; the ITS literature provides several.

- **The selection of meta-analyses.** Horvath's +0.29 is an average across a sample of meta-analyses. The averaging operation hides enormous variance. Some meta-analyses in the same database report effects above 0.50 (well-designed CAI, retrieval-practice deployments, computer-assisted reading programs); some report null effects (most ed-tech-in-K-12-math broadly defined). The chapter should name this: *averaging across a heterogeneous literature is not the same as showing the median context*. The averaging operation is precisely the move Horvath's own critique of EdTech vendors objects to when vendors do it.

### A.4 What Khan gets right (and what the chapter takes seriously)

Khan's *Brave New Words* is the optimistic case for AI in education. Strip the optimism and the structural claim is one Chapter 3 should grant:

- **The promise is real.** Bloom's 1984 "2-sigma" finding — that one-on-one human tutoring produces *d* = 2 against conventional instruction — has been substantially revised down by VanLehn 2011 to *d* = 0.79, still very large. The Kestin et al. 2025 ([*Scientific Reports* 15, June 2025](https://www.nature.com/articles/s41598-025-97652-6)) finding for a research-designed Harvard physics AI tutor — *d* ≈ 0.7–1.3 in a single course — is the strongest existing evidence that *some* AI tutoring deployments can produce gains in the upper range of human-tutoring effects, in a single carefully-designed context.
- **Engagement growth is real.** Khanmigo's growth from 40,000 to 700,000 students in the 2024–25 school year across 380+ district partners ([Khan Academy 2024 efficacy blog](https://blog.khanacademy.org/khan-academy-efficacy-results-november-2024/)) reflects substantial real demand for AI tutoring as a category. Common Sense Media's 4-star rating ([Common Sense Media](https://www.commonsensemedia.org/ai-ratings/khanmigo)) is a non-trivial third-party endorsement.
- **The problem is not the AI.** The chapter's pivot — and the chapter's central concession to the Khan reading — is that *the AI itself is not the source of the failure*. The Bastani PNAS 2025 finding makes this exact point: same GPT-4 underneath, two prompt wrappers, opposite outcomes. The model is not the variable. The variable is what the system around the model commits to. Khan, in his own deployment, has acknowledged via DiCerbo's "IDK IDK" remark that what the system was committed to was not producing the learning evidence the team had hoped for.

Where Khan overreaches: treating engagement-as-proxy-for-learning, treating growth-as-proof-of-effect, treating the optimistic case as if the evidence were settled. The chapter's discipline: take Khan's promise seriously without granting Khan's measurement choices.

### A.5 The Bastani PNAS 2025 finding — the chapter's central anchor

The single most consequential generative-AI-in-education result published to date. Citation: **Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., & Mariman, R. (2025). Generative AI without guardrails can harm learning: Evidence from high school mathematics. *Proceedings of the National Academy of Sciences*, 122(26), e2422633122.** [DOI 10.1073/pnas.2422633122](https://www.pnas.org/doi/10.1073/pnas.2422633122). [PubMed PMID 40560616](https://pubmed.ncbi.nlm.nih.gov/40560616/). Working paper / preprint: [SSRN 4895486](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4895486); author PDF: [hamsabastani.github.io/education_llm.pdf](https://hamsabastani.github.io/education_llm.pdf). Press summary: [Wharton Knowledge](https://knowledge.wharton.upenn.edu/article/without-guardrails-generative-ai-can-harm-education/).

Design: Field experiment in a Turkish high school. *N* ≈ 1,000 students, grades 9–11. Math practice sessions. Three conditions: (1) no AI control, (2) "GPT Base" — GPT-4 with a standard ChatGPT-style chat interface, (3) "GPT Tutor" — GPT-4 with a teacher-designed prompt wrapper that injected hints and refused to give complete answers.

Results during practice (with AI access):
- GPT Base: 48% higher math practice performance vs. no-AI control.
- GPT Tutor: 127% higher math practice performance vs. no-AI control.

Results on subsequent exam (without AI access):
- GPT Base: **17 percentage points lower** than no-AI control on the exam.
- GPT Tutor: statistically indistinguishable from no-AI control on the exam.

The structural reading. Three claims fall out:

- **In-session performance is not learning.** Bjork's distinction between performance and learning (Soderstrom & Bjork 2015, *Perspectives on Psychological Science* 10(2), 176–199) has now been demonstrated empirically for LLM-mediated practice. Students felt smarter, performed better, and learned less.
- **The wrapper, not the model, is the variable.** Same GPT-4 underneath two conditions. Different prompt design. Different outcomes by ~half a standard deviation. The model was not the source of either outcome.
- **The harm from naïve deployment is not subtle.** A 17-percentage-point exam decrement is roughly half a standard deviation of damage relative to no AI at all. This is not "AI is mildly suboptimal." It is "unguarded AI in this context made students substantially worse than they would have been without it."

The chapter's discipline: cite Bastani as the single most important data point for any responsible AI-tutor deployment. Every architecture chapter that touches Ask AI will reference back to this finding. Get the citation right.

### A.6 The ITS canon (Class A, ITS-distinct-from-GenAI)

Chapter 3 has to teach the reader to keep ITS and generative-AI evidence in separate buckets. From `ask-ai-research.md`:

- **VanLehn 2011** [ITS] — canonical meta-analysis. Step-based ITS *d* = 0.76, statistically indistinguishable from human tutoring (*d* = 0.79). Answer-based CAI *d* = 0.31. The structural finding: *step-grain interactivity matters more than whether the tutor is human or machine*. The chatbot equivalent — requiring the student to externalize a reasoning step before the system advances — is the design move that maps ITS into the AI-tutoring world.
- **Kulik & Fletcher 2016** [ITS] — 50 controlled evaluations, *g* = 0.66 median. Larger effects on locally-developed tests than on standardized tests — the "teach to the test" warning, which transfers to generative AI tutors that can be steered toward whatever assessment they will be graded against.
- **Steenbergen-Hu & Cooper 2013** [ITS] — the cold-water finding. K–12 mathematics, *g* = 0.01–0.09 overall, *g* = –0.18 for low-achieving K–12 students. The college sample (2014 companion) showed *g* ≈ 0.37–0.43. The structural warning: ITS that work in college often fail in K–12, where motivation and prior knowledge differ substantially.
- **AutoTutor** [ITS, dialog-based] — *d* = 0.7–0.8 average; Why/AutoTutor on Newtonian physics *d* = 0.75–1.22. The closest ITS analog to a chatbot: turn-based natural-language dialog, hints, questions. Provides the historical baseline against which generative chatbots should be benchmarked.
- **ASSISTments** [ITS, online homework] — *g* ≈ 0.22 in the Maine RCT (≈ three-quarters of a school year of additional learning), *g* ≈ 0.10 a year after in the North Carolina replication. The wild-deployment effect (*g* ≈ 0.1–0.2) is substantially smaller than the controlled-evaluation effect (*g* ≈ 0.66) — the chapter should name this gap, because it is the gap every EdTech evaluation has to negotiate.

The chapter's discipline: ITS results from 1995–2020 do *not* automatically transfer to a generative chatbot in 2026. Generative-chatbot results from 2024–2025 are early, methodologically uneven, and dominated by single-course trials. The two literatures share a name and almost nothing else.

### A.7 The spaced-repetition canon

From `quiz-me-research.md`:

- **Roediger & Karpicke 2006** [retrieval-practice] — *Psychological Science* 17(3), 249–255. The testing effect with educationally meaningful prose. Students who took practice tests recalled approximately 50% more than students who studied repeatedly on delayed (1-week) tests. Immediate (5-minute) testing favored re-studying; delayed testing reversed the pattern. The chapter's anchor for *why retrieval practice works*.
- **Karpicke & Blunt 2011** [retrieval-practice] — *Science* 331(6018), 772–775. The largest single-experiment effect size in the literature: retrieval practice outperformed elaborative concept mapping by *d* ≈ 1.50 on a one-week delayed test, including inference questions. The chapter should cite this but flag it as a single-experiment outlier — it is the laboratory ceiling, not the deployment expectation.
- **Adesope, Trevisan & Sundararajan 2017** [retrieval-practice] — *Review of Educational Research* 87(3), 659–701. The major meta-analysis: 188 experiments, 272 independent effect sizes. Practice tests vs. re-studying *g* = 0.51; vs. filler/no activity *g* = 0.93; in classrooms specifically *g* ≈ 0.67. This is the cleanest "Quiz Me beats re-reading" claim in the literature.
- **Cepeda, Pashler, Vul, Wixted & Rohrer 2006** [spaced-repetition] — *Psychological Bulletin* 132(3), 354–380, [DOI 10.1037/0033-2909.132.3.354](https://psycnet.apa.org/record/2006-06233-002). Meta-analysis of distributed practice. 839 assessments across 317 experiments and 184 articles. Spaced reviews produce more durable retention than massed reviews; optimal ISI scales with retention interval. The chapter's anchor for *why spacing matters*.
- **Cepeda et al. 2008** [spaced-repetition] — *Psychological Science*, follow-up showing spacing effects in learning with retention intervals up to 350 days. The chapter cites this for the *duration of the spacing benefit*.
- **Pan & Rickard 2018** [retrieval-practice, transfer] — *Psychological Bulletin* 144(7), 710–756, [PubMed 29733621](https://pubmed.ncbi.nlm.nih.gov/29733621/). Meta-analysis on transfer of test-enhanced learning. 192 effect sizes from 122 experiments. Pooled transfer effect *d* = 0.40, 95% CI [0.31, 0.50]. Larger transfer in medical contexts specifically. The chapter's anchor for *what retrieval practice transfers to*.

The chapter's discipline: distinguish retrieval-practice (mechanism), spacing (scheduling principle), and FSRS/SM-2 (implementation). Each has different evidence and different effect-size magnitudes. Conflating them is the most common error in vendor marketing for flashcard tools.

### A.8 The CBL literature

From `case-study-research.md` and verified directly:

- **Thistlethwaite, Davies, Ekeocha, Kidd, MacDougall, Matthews, Purkis & Clay 2012** [medical-CBL] — *Medical Teacher* 34(6), e421–e444. *The effectiveness of case-based learning in health professional education: A BEME systematic review: BEME Guide No. 23.* [Full text via Taylor & Francis](https://www.tandfonline.com/doi/full/10.3109/0142159X.2012.680939); [PubMed 22578051](https://pubmed.ncbi.nlm.nih.gov/22578051/). The systematic review reviewed 104 papers (after amalgamating duplicates) across medicine, dentistry, veterinary, nursing/midwifery, and allied health. The review's central finding: CBL is consistently rated highly by students and educators; the evidence base is heterogeneous in design but consistent in direction; *"CBL improves student engagement and learning outcomes."* The review notes that the literature has substantial methodological diversity (case definitions vary, comparison conditions vary, outcomes vary) but the directional finding is robust across the included studies.

The chapter's nuance: Thistlethwaite is the most-cited synthesis on CBL effectiveness. The chapter should grant the finding while naming the limitation: the review is on *human-facilitated* CBL — small-group discussion led by a clinical educator. The evidence does not directly license *solo asynchronous AI-facilitated CBL*, which is what Medhavy's Case Study mode is. The architecture has to make the bet that the *case structure* is doing real work and the *human facilitator* is not the irreplaceable component — but the bet is not directly evidenced in the Thistlethwaite review. The chapter must name this gap.

### A.9 The generative-assignment literature

From `glimmer-research.md`:

- **Fiorella & Mayer 2016** [generative-learning] — *Educational Psychology Review* 28(4), 717–741. [Springer Nature Link](https://link.springer.com/article/10.1007/s10648-015-9348-9); [Cambridge book](https://www.cambridge.org/core/books/learning-as-a-generative-activity/A7E1D7F80C8078AF9E4418ABFF459589). *Eight Ways to Promote Generative Learning*: summarizing, mapping, drawing, imagining, self-testing, self-explaining, teaching, enacting. Each strategy has a research base of varying maturity; self-testing and self-explaining have the strongest evidence; summarizing and teaching are well-established; drawing, imagining, mapping, and enacting are more domain-specific. The chapter's anchor for *what generative work means and why it matters*.
- **Jonassen 1997** [generative-learning, ill-structured] — *Educational Technology Research and Development* 45(1), 65–94. [Springer Nature Link](https://link.springer.com/article/10.1007/BF02299613). *Instructional design models for well-structured and ill-structured problem-solving learning outcomes*. The canonical distinction between well-structured problems (constrained, convergent, finite-rule) and ill-structured problems (multiple solutions, fewer manipulable parameters, uncertainty about which concepts are necessary). Information-processing theory grounds well-structured-problem instruction; constructivism and situated cognition ground ill-structured-problem instruction. The chapter's anchor for *why Glimmer is the right mode for ill-structured problems and Quiz Me is the right mode for well-structured problems*.

The chapter's discipline: name the conditions under which generative assignments produce gains (sufficient prior knowledge to generate; appropriate scaffolding; feedback on the generative artifact). Name the failure mode: novice learners asked to do unscaffolded generative work in ill-structured domains often experience the anxiety failure mode (`glimmer-displacement-research.md`) and produce nothing.

---

## B. Domain examples and cases

### B.1 The worked example — Bear's published Horvath review

The chapter's worked example, per the TIKTOC, is Bear's own published analysis of Horvath's *The Digital Delusion* on the Computational Skepticism Substack. (Verify the URL when drafting; the substack is Bear's and the post is published.) The walk-through is the chapter's meta-lesson: *this is how you read an EdTech evidence claim*.

The structure of the review (the chapter's worked example):

1. **Specify what Horvath actually claims.** Pull out the three claims of §A.2 above. State them in their strongest form.
2. **Specify what would have to be true for the claims to be supported.** PISA-style correlations would have to translate to causal effects (they don't, automatically). The meta-analytic average would have to be a representative summary of the underlying literature (it isn't, because the literature is heterogeneous). The "nearly every context" claim would have to survive a counter-example search (it doesn't, because the ITS literature is a counter-example).
3. **Apply the threshold test.** Does the evidence support a verdict on EdTech-in-general, or only on a specific subset of EdTech deployments? The evidence supports a verdict on indiscriminate high-dosage classroom technology. It does not support a verdict on well-designed retrieval-practice apps, well-designed ITS, well-designed safeguarded AI tutoring with Bastani-style prompt wrappers, or well-designed CBL.
4. **State the residual.** What does Horvath get right that the field should not ignore? The +0.29 average is real. The PISA correlations are real. The methodological critique of vendor literature is real. These survive the audit.
5. **State the implication.** The book's response to Horvath is not to dispute his evidence; it is to specify the architecture that the evidence licenses *when deployed with discipline*.

This is the chapter's pedagogical move. The reader sees the audit performed in front of them. They learn the form. They can then apply it to the next vendor claim or the next paper they encounter.

### B.2 The Khanmigo case as evidence-reading exercise

A second worked example the chapter can use: how to read Khan Academy's published efficacy claims for Khanmigo.

- **The claim.** Khanmigo grew from 40,000 to 700,000 students across 380+ district partners in the 2024–25 school year. Common Sense Media gave it 4 stars. Khan Academy publishes case studies of districts where teacher and student satisfaction is high.
- **What the claim supports.** Adoption is real. Demand is real. Satisfaction surveys directionally favor the product.
- **What the claim does not support.** A learning-outcomes claim. None of the cited evidence is a controlled comparison with a no-Khanmigo control measuring durable learning. The Common Sense Media rating is on educational quality and safety, not on durable learning outcomes; their own review notes that *"persistent prompting would lead to Khanmigo offering a more complete answer"* — i.e., the guardrail leaks.
- **What evidence would change the picture.** A multi-site RCT (*N* in the thousands, independent evaluators, no-Khanmigo control, durable-learning outcome measured on transfer-bearing assessments at delay of weeks). Such a study has not yet been published in peer-reviewed form. WestEd has been listed as a Khanmigo evaluation partner in press materials; the specific evaluation report has not surfaced in peer-reviewed publication at the time of this note (`ask-ai-research.md` flags this with a [verify] marker).

The exercise teaches the reader the same diagnostic Bear's Horvath review applies. Khan and Horvath are using the same kind of evidence in opposite directions; both deserve the same audit.

### B.3 A positive-case worked example — the Kestin Harvard physics RCT

The chapter should include one strong positive case to balance the negative emphasis. Citation: Kestin, G., Miller, K., Klales, A., Milbourne, T., & Ponti, G. (2025). [*Scientific Reports* 15, online 3 June 2025](https://www.nature.com/articles/s41598-025-97652-6). Harvard Physical Sciences 2, *N* = 233 (Fall 2023). A custom AI tutor designed with the same research-based pedagogical principles as the in-class active-learning sessions (segmented content, formative checks, deliberate misconception traps). Students learned roughly twice as much in less time on the AI tutor than in the active-learning class; reported effect sizes *d* ≈ 0.7–1.3. [Harvard Gazette coverage](https://news.harvard.edu/gazette/story/2024/09/professor-tailored-ai-tutor-to-physics-course-engagement-doubled/).

The chapter's read:

- **The result is large and credible *for what it measures*.** One institution. One course. One professor. One custom-built tutor with research-based design principles. Comparison to a single active-learning session rather than the full course.
- **The result does not support *"any AI tutor is twice as good as active learning."*** That is the inference the paper does not license.
- **The result does support *"with sufficient pedagogical design discipline, generative AI tutors can produce effect sizes in the human-tutoring range in well-defined contexts."*** This is the chapter's positive read.

Kestin and Bastani together specify the chapter's central claim: *the wrapper is the variable*. Bastani shows the negative case (unguarded wrapper, –17 pp). Kestin shows the positive case (research-designed wrapper, *d* = 0.7–1.3). Both used GPT-4 (or comparable). The difference is the design discipline applied to the wrapper.

### B.4 The third assessable exercise — Bastani applied to Ask AI

The chapter's third assessable exercise, per TIKTOC: *The Bastani finding — what does it imply for the Ask AI mode's guardrail design? What specific design decision does it justify?* The chapter's expected answer:

- The wrapper must force the student to externalize a reasoning step before the system advances (the step-grain interactivity move from VanLehn 2011, plus the Bastani Tutor-wrapper move).
- The wrapper must constrain the model from giving complete answers; teacher-designed hints with explicit phase-gating are the design pattern.
- The wrapper must include a measurement layer for whether the student is actually working through the reasoning or offloading; the Khanmigo IDK-IDK failure is the diagnostic signal the measurement layer must catch.
- The Bastani PNAS finding is the *evidence* that licenses the Ask AI mode's guardrail design. Without that finding, the architecture's commitment to guardrail discipline would be a design preference rather than an evidence-supported requirement.

The exercise teaches the reader to do what the architecture chapters will do throughout the book: *cite Bastani to license a specific design decision*.

---

## C. Connections and dependencies

### C.1 Within-book connections

- **Backward to Chapter 1 and Chapter 2.** Chapter 3 delivers the evidence base that the failure-mode claims in Chapter 1 and the complexity-threshold claims in Chapter 2 implicitly rely on. After Chapter 3, the reader can re-read Chapter 1 with the citations as scaffolding. They can re-read Chapter 2 with the retrieval-practice and CBL evidence specifying why the threshold test resolves where it does.
- **Forward to all of Act Two.** Chapter 3 is the *evidence base every architecture chapter will cite*. Specifically:
  - Chapter 4 (Four Layers) cites the seven-signals argument (`ask-ai-research.md`) and the ITS-vs-GenAI literature.
  - Chapter 5 (Measurement) cites the Bjork performance/learning distinction (Soderstrom & Bjork 2015), the Bastani PNAS finding for the decoupling problem, the GLP preprint.
  - Chapter 6 (Four Modes) cites Bastani for Ask AI guardrails, Roediger-Karpicke and Adesope for Quiz Me, Thistlethwaite for Case Study, Fiorella & Mayer and Jonassen for Glimmer.
  - Chapter 7 (Adaptive Engine) cites the ITS canon (VanLehn step-grain interactivity, Koedinger-Aleven assistance dilemma) and the contextual bandit literature.
  - Chapter 8 (Curriculum Design) cites Cepeda for spacing, the Tic TOC concept-sequencing literature (`concept-sequencing-research.md`).
  - Chapter 9 (Content) cites the Sadler 2013 Level-3 specificity argument and Mayer CTML.
  - Chapter 10 (Economics) cites the Sesame Street precedent and the cost-collapse asymmetry.
- **The discipline.** Every architecture chapter's "the evidence shows" sentence either traces back to a Chapter 3 citation or it is unevidenced and should be flagged. Chapter 3 is the book's evidentiary spine.

### C.2 Cross-pantry dependencies

This is the chapter that draws on *all* existing pantry research notes. The chapter's job is to render their evidence base accessible. The cross-references:

- **`ask-ai-research.md`** — primary source for the Bastani PNAS 2025 citation in full, the ITS canon (VanLehn 2011, Kulik & Fletcher 2016, Steenbergen-Hu & Cooper 2013, AutoTutor, ASSISTments), the Khanmigo qualitative evidence, the Kestin Harvard physics RCT, the Wang Tutor CoPilot RCT, the LearnLM UK RCT, the Lee et al. CHI 2025 cognitive-effort survey. **Chapter 3 cites approximately 12 of the ~30 sources in this note.** The chapter does not exhaust the note; later architecture chapters draw further from it.
- **`quiz-me-research.md`** — primary source for the retrieval-practice canon (Roediger & Karpicke 2006, Karpicke & Blunt 2011, Adesope et al. 2017, Pan & Rickard 2018), the spacing canon (Cepeda et al. 2006, Cepeda et al. 2008), the FSRS / SM-2 distinction, the medical-application evidence. **Chapter 3 cites approximately 5 of the ~20 sources in this note.**
- **`case-study-research.md`** — primary source for Thistlethwaite 2012, the CBL effectiveness evidence, the pre-written vs. on-demand cases distinction. **Chapter 3 cites the Thistlethwaite review with the noted limitation that the CBL literature is on human-facilitated CBL, not solo AI-facilitated CBL.**
- **`glimmer-research.md`** — primary source for Fiorella & Mayer 2016, Jonassen 1997, the generative-learning literature. **Chapter 3 cites both.**
- **`glimmer-displacement-research.md`** — secondary source for the displacement framing; Chapter 3 references the displacement-of-irreducibly-human-work argument once.
- **`concept-sequencing-research.md`** — primary source for BKT, DKT, prerequisite chaining; Chapter 3 references the *frequency-orderable curriculum* concept and the BKT literature lightly.
- **`domain-specific-instruction-research.md`** — primary source for Sadler 2013 Level-3 specificity, PCK. Chapter 3 references the Sadler framing once when discussing what makes a benchmark meaningful.
- **`educational-media-economics-research.md`** — primary source for Sesame Street evidence (Bogatz & Ball 1970–1971, Mares & Pan 2013, Kearney & Levine 2019) and Mayer CTML. Chapter 3 cites the Mares & Pan *d* = 0.29 as the benchmark for what high-quality educational media is capable of.
- **`_lib_co-intelligence__living_and_working_with_ai.md`** (Mollick) — Chapter 3 references the *Co-Intelligence* framing once for the human+AI vs. human-vs-AI distinction.
- **`_lib_the_art_of_statistics__how_to_learn_from_data.md`** (Spiegelhalter) — Chapter 3 uses Spiegelhalter's framing of evidence-reading discipline lightly; Spiegelhalter's "what would have to be true for this claim to be supported" move is the chapter's epistemological tool.
- **Bear's published Horvath review on Computational Skepticism Substack** — primary source for the worked example. (Verify URL when drafting.)

### C.3 Cross-book connections

- **Trust the Teacher.** TtT's Ch 10 ("Honest Measures") and Appendix B (Three-Measure Framework) are the methodological complements to Medhavy's Chapter 3. The evidence-reading discipline Bear deployed in TtT is the same discipline Medhavy's Ch 3 deploys.
- **Bear's Computational Skepticism Substack reviews** of various EdTech books are the worked-example tradition the chapter sits inside.

---

## D. Current state of the field

The EdTech evidence-reading field is fractured along three axes that the chapter has to name:

### D.1 The two-literatures problem

The first axis: ITS vs. generative-AI literatures are kept separate by their methodologies but conflated in popular discussion. ITS literature is 30+ years deep, methodologically mature, with consistent effect sizes in the *d* = 0.4–0.7 range for well-designed systems. Generative-AI literature is three years deep, with effect sizes ranging from –0.5 (Bastani GPT Base) to +1.3 (Kestin) depending on the wrapper. Vendor marketing routinely cites the ITS literature to support generative-AI deployments — this is a category error the chapter must name. The chapter's discipline: every effect-size citation is tagged with the class it applies to. ITS effects do not automatically transfer to generative-AI deployments.

### D.2 The measurement-mismatch problem

The second axis: most of the EdTech literature measures the *wrong outcome*. User satisfaction. Time on platform. Engagement. Self-reported usefulness. Quiz completion rate. None of these is durable learning. The Bastani PNAS finding is so important precisely because it measured the right outcome — a no-AI exam at delay — and found that the in-session metrics were diametrically opposed to the durable-learning outcome. The literature has not yet converged on a measurement framework that distinguishes engagement from learning at the instrumentation level. The GLP framework (TIKTOC §Ch 5) is the book's proposal. It is not yet validated in deployment.

### D.3 The vendor-publication asymmetry

The third axis: vendor-published evidence is dominant and is not subject to the same scrutiny as peer-reviewed evidence. Khanmigo's published evaluations are largely Khan Academy's own efficacy blog posts. The two-girl framing of an AI hallucination problem in HoH+1 is the kind of qualitative pattern that does not yet have peer-reviewed evidence. The honest position: where vendor evidence and peer-reviewed evidence agree (e.g., the satisfaction findings for Khanmigo, the Common Sense Media 4-star rating), the chapter can use both. Where they disagree (e.g., the implicit claim of learning gains in vendor materials vs. the lack of RCT confirmation), the chapter cites the peer-reviewed evidence and names the vendor evidence as a satisfaction/adoption claim rather than a learning claim.

### D.4 The Mollick / co-intelligence framing

Mollick's *Co-Intelligence* (2024) — present in pantry as `_lib_co-intelligence__living_and_working_with_ai.md` — is the field's most influential popular text on the *human + AI* framing. Mollick is broadly consistent with the chapter's read: the AI is a co-actor whose behavior depends substantially on how it is used; the value is created at the interface between the human and the AI, not by either alone. The chapter's discipline: take Mollick's framing as a useful lens, name its limitations (popular synthesis, not original empirical work), and use it as one of several supporting frames rather than as a primary citation.

### D.5 What the field is converging on

Across the heterogeneity, a few claims are broadly accepted across both Khan-side and Horvath-side observers:

- The model is not the variable. The wrapper, the deployment context, and the surrounding instructional system are the variables.
- Engagement is not learning. Both sides have now publicly acknowledged this (Khan via DiCerbo, Horvath throughout *The Digital Delusion*).
- Effect sizes in deployed (as opposed to laboratory) EdTech are typically smaller than in controlled-evaluation studies (the ASSISTments wild-vs-lab gap is the canonical demonstration; *g* ≈ 0.1–0.2 in wild deployment vs. *g* ≈ 0.66 in controlled evaluation).
- Methodological discipline (RCTs with no-treatment controls, durable-outcome measurement, independent evaluators) is rare in the AI-in-education literature.

These four claims are the field's current floor of consensus. The architecture chapters build on this floor.

---

## E. Teaching considerations

### E.1 The chapter's pedagogical move

The reader is being asked to acquire the *evidence-reading instrument*. This is an Analyze-level Bloom's task in the assessable exercises (apply the audit pattern to a new vendor claim) and Evaluate-level in the third exercise (assess a claimed evidence base for cherry-picking).

The pedagogical sequence:

1. **Open with the Butter Knife Fallacy.** Concrete metaphor. Apply it immediately to PISA 2022. The reader gets the diagnostic posture.
2. **Walk through what Horvath proves and where Horvath overreaches.** Show both moves on the same author. The reader learns that *correctly diagnosing one regime does not license a verdict on all regimes*.
3. **Walk through what Khan gets right.** Show the same structure on the optimistic side. Symmetry.
4. **Anchor on Bastani PNAS 2025.** The single most important finding. The chapter spends real length here.
5. **Walk through the four literatures.** ITS, retrieval practice + spacing, CBL, generative assignment. Each gets a tight summary with the canonical citations.
6. **Worked example.** Bear's Horvath review. Show the audit performed.
7. **Hand the instrument to the reader.** The three assessable exercises — vendor effect-size claim audit, Horvath "nearly every context" claim audit, Bastani-applied-to-Ask-AI-guardrail design.
8. **Close.** The reader holds the evidence base. The architecture chapters can now cite.

### E.2 What to avoid

- **Do not let the chapter become an effect-size catalog.** The temptation is to list every meta-analysis. The discipline is to name only the citations that the architecture chapters will use. Approximately 25 primary citations is the right density. More is performative.
- **Do not pretend the evidence is settled.** It isn't. The Bastani PNAS finding is one RCT. Kestin is one course. The Thistlethwaite review is on human-facilitated CBL. The chapter's authority comes from honesty about what the evidence supports, not from forcing more certainty than the data gives.
- **Do not deploy Hattie's 0.40 as a verdict.** Use it as a cost-effectiveness guideline. The 0.40 is widely critiqued (Simpson 2020, Kraft 2020, Eacott); the chapter should name the critique, not erase it.
- **Do not let Bear's Horvath review feel like score-settling.** The review is a worked example of the audit pattern. The chapter's tone is *here is how we read EdTech evidence*, not *here is why Horvath is wrong*. The chapter grants what Horvath gets right; that grant is what licenses the chapter to specify where Horvath overreaches.

### E.3 Voice and register

- The chapter has the highest citation density in the book. Citation density should feel like *competence*, not like *defense*. Each citation does work; no citation is decorative.
- The chapter should read as a teacher walking the student through how to read a hostile literature. The voice is *patient*, not *hectoring*.
- The Butter Knife metaphor is the chapter's spine. It can be referenced once at open, once at midpoint (when discussing Horvath's "nearly every context" claim), and once at close. Three uses; more is over-leveraging the metaphor.

### E.4 The Hattie problem specifically

A reader trained on Hattie will arrive expecting the chapter to argue for or against the 0.40 hinge. The chapter's move: neither. The 0.40 is a useful summary statistic, badly mis-used as a binary cutoff. The chapter teaches the right use (cost-effectiveness guideline) and disposes of the wrong use (verdict on whether an intervention "works") with one paragraph and a citation to the Simpson 2020 critique. The Hattie debate is not the chapter's center; the chapter walks past it with discipline.

---

## F. Library files — what existing pantry covers

This is the chapter where the cross-referencing is densest. Section-by-section:

- **`ask-ai-research.md`** is the primary source for:
  - Bastani et al. 2025 *PNAS* citation in full (Section 1.2 of the note carries the citation, study design, and results).
  - The ITS canon — VanLehn 2011, Kulik & Fletcher 2016, Steenbergen-Hu & Cooper 2013, AutoTutor, ASSISTments (Section 1.1).
  - Khanmigo evaluations and the DiCerbo IDK-IDK acknowledgment (Section 1.2).
  - Kestin et al. 2025 Harvard physics RCT (Section 1.2).
  - Wang et al. 2024 Tutor CoPilot (Section 1.2).
  - LearnLM UK RCT (Section 1.2).
  - Lee et al. 2025 CHI cognitive-effort survey (Section 1.2).
  - Socratic vs. direct prompting evidence (Section 2.1).
  - Aleven / Koedinger / McLaren ITS hint design (Section 2.2).
  - The "lost in the middle" and context-rot findings (Section 3.3).
  - Hallucination evidence in education (Section 4.2).
  - **Chapter 3 cites approximately 12 sources from this note.** Use this note as the primary reference for all AI-tutoring effect-size claims.
- **`quiz-me-research.md`** is the primary source for:
  - Retrieval-practice canon — Roediger & Karpicke 2006, Karpicke & Blunt 2011, Adesope 2017, Pan & Rickard 2018, Roediger Putnam & Smith 2011.
  - Spaced-repetition canon — Cepeda 2006, Cepeda 2008, Bjork & Bjork storage-strength / retrieval-strength.
  - FSRS / SM-2 / Anki scheduling-algorithm literature.
  - Bjork's performance/learning distinction (Soderstrom & Bjork 2015).
  - Medical-application evidence.
  - **Chapter 3 cites approximately 6 sources from this note.**
- **`case-study-research.md`** is the primary source for:
  - Thistlethwaite 2012 BEME Guide No. 23.
  - CBL effectiveness evidence broadly.
  - Pre-written vs. on-demand case design.
  - **Chapter 3 cites approximately 2 sources from this note.**
- **`glimmer-research.md`** is the primary source for:
  - Fiorella & Mayer 2016 Eight Ways to Promote Generative Learning.
  - Jonassen 1997 ill-structured problem solving.
  - Wittrock's generative model.
  - **Chapter 3 cites approximately 3 sources from this note.**
- **`glimmer-displacement-research.md`** — secondary source. Chapter 3 references displacement framing once.
- **`concept-sequencing-research.md`** — secondary source. Chapter 3 references BKT/DKT and prerequisite-chaining literature once each.
- **`domain-specific-instruction-research.md`** — secondary source. Chapter 3 references Sadler 2013 Level-3 specificity once for what makes benchmarks meaningful.
- **`educational-media-economics-research.md`** is the primary source for:
  - Sesame Street evidence (Bogatz & Ball 1970–1971, Mares & Pan 2013 *d* = 0.29, Kearney & Levine 2019).
  - Mayer CTML twelve principles.
  - Cost-collapse asymmetry framing.
  - **Chapter 3 cites approximately 3 sources from this note.**
- **`_lib_co-intelligence__living_and_working_with_ai.md`** (Mollick) — Chapter 3 references the human+AI framing once.
- **`_lib_the_art_of_statistics__how_to_learn_from_data.md`** (Spiegelhalter) — Chapter 3 references the evidence-reading discipline once.
- **Bear's published Horvath review on Computational Skepticism Substack** — Chapter 3's worked example. The chapter's spine.
- **Horvath, *The Digital Delusion* (2025)** — Chapter 3 engages the book directly. The chapter cites Horvath's own claims and qualifies them; it does not rely on second-hand summaries.

---

## G. Gaps and flags

### G.1 Verification flags

These are the citations that must be verified before draft is final:

- **The PISA 6+ hours / 66-point figure (from TIKTOC) does not appear in the OECD PISA 2022 reports verbatim.** The verified figure is 49 points at the 5–7 hours vs. up-to-1 hour comparison ([OECD PISA 2022 Volume I](https://www.oecd.org/en/publications/pisa-2022-results-volume-i_53f23881-en.html)). The 66 figure may be a transposition error. Chapter 3 should use 49 points with the correct threshold (5–7 hours vs. up to 1 hour). The TIKTOC needs updating; flag this for the orchestrator. This is the most important verification issue in the chapter — the wrong number undercuts the evidence-reading discipline the chapter is trying to teach.
- **The Bastani PNAS 2025 citation: full and verified.** Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., & Mariman, R. (2025). Generative AI without guardrails can harm learning: Evidence from high school mathematics. *Proceedings of the National Academy of Sciences*, 122(26), e2422633122. [DOI 10.1073/pnas.2422633122](https://www.pnas.org/doi/10.1073/pnas.2422633122). The note above (and `ask-ai-research.md`) carries this correctly. The figure to cite: the GPT Base group scored 17 percentage points lower on the post-practice exam than the no-AI control. Some popular summaries state this as "17% lower"; the precise figure is *17 percentage points*, not 17%. Be precise.
- **The Thistlethwaite 2012 citation: full and verified.** Thistlethwaite, J. E., Davies, D., Ekeocha, S., Kidd, J. M., MacDougall, C., Matthews, P., Purkis, J., & Clay, D. (2012). The effectiveness of case-based learning in health professional education. A BEME systematic review: BEME Guide No. 23. *Medical Teacher*, 34(6), e421–e444. [DOI 10.3109/0142159X.2012.680939](https://www.tandfonline.com/doi/full/10.3109/0142159X.2012.680939). 104 papers reviewed.
- **The Roediger & Karpicke 2006 citation: full and verified.** Roediger, H. L., III, & Karpicke, J. D. (2006). Test-enhanced learning: Taking memory tests improves long-term retention. *Psychological Science*, 17(3), 249–255. [PubMed 16507066](https://pubmed.ncbi.nlm.nih.gov/16507066/).
- **The Cepeda et al. 2006 citation: full and verified.** Cepeda, N. J., Pashler, H., Vul, E., Wixted, J. T., & Rohrer, D. (2006). Distributed practice in verbal recall tasks: A review and quantitative synthesis. *Psychological Bulletin*, 132(3), 354–380. [PubMed 16719566](https://pubmed.ncbi.nlm.nih.gov/16719566/).
- **The Fiorella & Mayer 2016 citation: full and verified.** Fiorella, L., & Mayer, R. E. (2016). Eight ways to promote generative learning. *Educational Psychology Review*, 28(4), 717–741. [DOI 10.1007/s10648-015-9348-9](https://link.springer.com/article/10.1007/s10648-015-9348-9).
- **The Jonassen 1997 citation: full and verified.** Jonassen, D. H. (1997). Instructional design models for well-structured and ill-structured problem-solving learning outcomes. *Educational Technology Research and Development*, 45(1), 65–94. [DOI 10.1007/BF02299613](https://link.springer.com/article/10.1007/BF02299613).
- **The Hattie 0.40 hinge: contextually used.** Hattie, J. (2009). *Visible Learning: A Synthesis of Over 800 Meta-Analyses Relating to Achievement*. Routledge. The 0.40 figure is real; the critique of its use as a binary cutoff is also real. Cite the figure with the critique attached, not without. The Simpson 2020 critique is the standard citation for the meta-meta-analysis problem.
- **Horvath's "nearly every context" claim — verify the exact wording.** The chapter should cite the exact page in *The Digital Delusion* where the claim is made. The book is dated 2025/2026 depending on edition; verify the printing.

### G.2 Conceptual flags

- **The chapter must not be read as score-settling against Horvath.** Horvath is a serious thinker with a serious argument; the chapter's job is to teach how to read EdTech evidence using Horvath's book as an example, not to dunk on Horvath. Voice discipline: grant what Horvath gets right *first*, then specify where the argument overreaches. The Horvath review is a *demonstration of the audit pattern*, not a verdict on Horvath.
- **The chapter must not be read as endorsement of Khan.** The chapter cites Khanmigo evidence — including DiCerbo's IDK-IDK acknowledgment — as honestly as it cites Horvath. The third position is neither Khan nor Horvath. The chapter's discipline: keep symmetry. If Horvath gets a "what he gets right" paragraph, Khan gets one too.
- **The Bastani finding is one study.** The chapter spends substantial real length on Bastani because it is the cleanest existing demonstration of the wrapper-as-variable claim. It is one RCT in one country. The chapter must say so. The "What would change my mind" at chapter close should name the replication question explicitly.

### G.3 Hostile-reader objections to anticipate

- *"You're cherry-picking the ITS literature to counter Horvath."* The chapter's response: the chapter named the counter-context explicitly. ITS is a counter-context. Horvath's claim was "nearly every context"; one counter-context is sufficient to disprove "nearly every." The move is not cherry-picking; it is responding to the universal quantifier.
- *"You're treating Bastani as definitive when it's one RCT."* The chapter's response: yes, the chapter treats Bastani as the *most important single result*, not as definitive. The replication question is named. Until the replications arrive, Bastani is the field's strongest evidence on the wrapper-as-variable claim.
- *"You're using effect sizes from different literatures interchangeably."* The chapter's response: every effect size carries a class tag. ITS, retrieval-practice, GenAI, CBL, generative-learning — each cited effect is tagged. The chapter teaches the discipline of not interchanging them.
- *"Hattie has been debunked. Why are you citing him at all?"* The chapter's response: Hattie's hinge is a useful cost-effectiveness guideline, and it has been widely critiqued as a binary verdict. The chapter cites Hattie correctly (as guideline) and names the critique. The 0.40 is a real summary statistic in a real database; the critique is of its mis-use, not of its existence.

### G.4 What would change my mind for this chapter

- A successful replication of the Bastani PNAS finding in a non-Turkish context with a different age group would substantially strengthen the chapter's central claim. A failed replication would substantially weaken it.
- A rigorous independent RCT of Khanmigo or LearnLM with no-treatment control and durable-learning outcomes at delay would update the chapter's read of vendor-published evidence. If such an RCT produces large positive durable-learning effects, the chapter's skepticism of vendor evidence would need to soften. If it produces null effects, the chapter's read sharpens.
- A direct comparison of well-designed solo asynchronous AI-facilitated CBL vs. human-facilitated CBL would address the gap the chapter names in the Thistlethwaite literature. If the AI-facilitated version produces equivalent outcomes, the chapter's caveat on CBL evidence can be removed.
- A meta-analytic update synthesizing the 2024–2026 generative-AI-in-education studies (which would by then number in the high tens or low hundreds) would let the chapter cite a meta-analytic effect size for AI tutoring rather than relying on Bastani plus Kestin as the two anchor studies.

### G.5 Still puzzling

- Why has the field not produced more RCTs of AI tutoring? The Bastani / Kestin pair are anomalously rigorous in a literature dominated by satisfaction surveys. The structural reasons (RCTs are expensive, vendors have no incentive to publish negative results, journals have not yet calibrated their expectations for the new class of study) are real but the gap remains striking. The chapter cannot resolve this; it can note it.
- What does the +0.29 EdTech meta-analytic average actually mean? It is the average across an enormously heterogeneous literature. The average masks variance that is itself the most informative finding. Horvath uses the average as a verdict; the chapter argues the variance is the actual signal. But specifying *which* contexts produce which effects requires meta-regression work that the field has not done at scale. The chapter notes this as an open methodological question.
- How does the wrapper-as-variable finding scale beyond Bastani? Bastani used a teacher-designed hint wrapper. What if the wrapper is engine-selected per learner, per concept, per moment (as Medhavy's architecture proposes)? Does the wrapper's value scale? Plateau? Become brittle? The chapter cannot answer this. The architecture chapters explore it. The chapter at least names the question as the bet the book is making.

---

*End of research notes. Approx. 6,200 words. For Chapter 3 author use.*
