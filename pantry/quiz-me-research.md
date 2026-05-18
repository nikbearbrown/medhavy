# Research Note — Quiz Me, FSRS, and the Two Literatures Medhavy Must Not Confuse

*Working pantry document for the Medhavy book project. Substantive research underpinning the "Quiz Me" chapter / sections, organized for direct quarrying into prose. Citation-dense.*

*Compiled 2026-05-17. Maintained for revision.*

---

## Preliminary: the distinction this note refuses to collapse

The single most common mistake in the practitioner literature on "spaced repetition" is treating it as one thing. It is at least three things, and conflating them produces effect-size claims that are technically true under one frame and false under the next.

- **Retrieval practice** (also "test-enhanced learning" or "the testing effect") is a **learning mechanism**. The act of trying to pull information out of memory changes the memory. The canonical demonstrations are Roediger & Karpicke 2006 and Karpicke & Blunt 2011. Effect-size magnitudes here describe what happens when you compare *testing* to *re-reading* — schedule held constant.
- **Spaced repetition** (also "distributed practice," "spacing effect") is a **scheduling principle**. The same total practice produces more durable memory if it is distributed across time rather than massed. Canonical demonstrations: Ebbinghaus 1885 forgetting curve; Cepeda, Pashler, Vul, Wixted & Rohrer 2006 meta-analysis; Bjork & Bjork's storage-strength / retrieval-strength theory. Effect-size magnitudes here describe what happens when you compare *distributed* to *massed* — review modality held constant.
- **FSRS, SM-2, Anki, SuperMemo** are **scheduling algorithms**. They are implementations of the scheduling principle; they are not learning theories and they do not, by themselves, generate retrieval practice — they decide *when* the practice is offered to a student who has already committed to doing it. An algorithm's "20% reduction in review burden" is a scheduling claim, not a learning claim.

These three categories interact, but they make different claims and rest on different evidence. The Quiz Me chapter in medhavy needs them named separately. Throughout this note every effect-size citation is tagged with the class it actually applies to:

- `[retrieval-practice]` — the learning mechanism (testing effect).
- `[spaced-repetition]` — the scheduling principle.
- `[scheduling-algorithm]` — a specific implementation (FSRS, SM-2, etc.).
- `[prerequisite-chaining]` — knowledge-component / knowledge-tracing / prerequisite literature.
- `[medical-application]` — clinical or medical-education evidence.
- `[foundational-theory]` — Bjork, Ebbinghaus, ACT-R, BKT, etc.

When the chapter says "Quiz Me uses FSRS, an evidence-based algorithm for scheduling review at intervals that maximize durable retention," it is claiming three things at once: that retrieval practice works (mechanism), that spacing matters (principle), and that FSRS is the right implementation of the principle (algorithm). Each is supported by different evidence with different strength. The chapter needs to honor that.

---

## 1. Effectiveness evidence

### 1.1 The retrieval-practice canon

**Roediger & Karpicke 2006** `[retrieval-practice]` is the canonical demonstration of the testing effect with educationally meaningful prose. Students studied science passages and were assigned to one of three conditions: SSSS (four study periods), SSST (three study, one test), or STTT (one study, three tests). Final retention was measured at 5 minutes, 2 days, or 1 week. At 5 minutes, additional studying beat testing — performance favored SSSS (83% recall) over STTT (71%). At 1 week, the order *reversed*: STTT students recalled about 61% of the material, SSST about 56%, and SSSS only about 40%. ([Roediger & Karpicke 2006, *Psychological Science* 17(3), 249–255](https://journals.sagepub.com/doi/10.1111/j.1467-9280.2006.01693.x); [PDF](http://psychnet.wustl.edu/memory/wp-content/uploads/2018/04/Roediger-Karpicke-2006_PPS.pdf))

Two things to note for medhavy. First, the immediate-vs.-delayed reversal is the empirical face of what Soderstrom & Bjork 2015 will later formalize as the learning-vs.-performance distinction (see §4 on gating): the condition that produced the *best in-session performance* (SSSS) produced the *worst durable learning*. Second, the comparison condition is **re-reading**, not nothing. Testing beats one of the most common student study behaviors, not absence of practice.

**Karpicke & Blunt 2011** `[retrieval-practice]` is the most-cited single-experiment effect size in the testing-effect literature. Undergraduates studied a science text under four conditions: study-once, repeated study, elaborative concept-mapping, or retrieval practice (free recall, no feedback). On a one-week delayed short-answer test that included inference questions, retrieval practice outperformed elaborative concept-mapping by approximately **d = 1.50**. Critically, the advantage held even when the criterion test *required producing concept maps* — the form the concept-mapping group had practiced. The interpretation: retrieval practice is the mechanism; the surface form of the activity doesn't substitute for it. ([Karpicke & Blunt 2011, *Science* 331(6018), 772–775](https://www.science.org/doi/10.1126/science.1199327); [PDF](https://learninglab.psych.purdue.edu/downloads/2011/2011_Karpicke_Blunt_Science.pdf))

The 1.50 figure is the number most likely to appear in vendor marketing for any flashcard tool. The honest reading: this is a single laboratory study comparing free recall against concept mapping in a one-week window. It is the largest, cleanest demonstration of the mechanism. It is not a forecast of platform effect sizes in classroom deployment.

**Adesope, Trevisan & Sundararajan 2017** `[retrieval-practice]` is the major meta-analysis. 188 experiments, 272 independent effect sizes, K–university and adult learners. Headline numbers: practice tests vs. re-studying, **g = 0.51** (moderate, statistically significant). Practice tests vs. filler or no activity, **g = 0.93** (large). In classroom settings specifically, **g ≈ 0.67**. Multiple-choice practice tests produced larger effects (g = 0.70) than short-answer (g = 0.48), though the latter favors transfer (consistent with Pan & Rickard, below). ([Adesope, Trevisan & Sundararajan 2017, *Review of Educational Research* 87(3), 659–701](https://journals.sagepub.com/doi/abs/10.3102/0034654316689306))

The g = 0.51 vs.-restudy number is the cleanest "Quiz Me beats re-reading" claim in the literature. The chapter should use this rather than the d = 1.50 figure, which is a single-experiment outlier under specific comparison conditions.

**Pan & Rickard 2018** `[retrieval-practice]` is the meta-analysis on the **transfer** of test-enhanced learning — does the testing effect carry over to material that wasn't tested, or to a different form of question? 192 transfer effect sizes from 122 experiments (N = 10,382). Pooled transfer effect: **d = 0.40**, 95% CI [0.31, 0.50]. Crucial moderator: when there is no "response congruency" between initial and final test (i.e., the answers are fully different), d = 0.28; when there is overlap, d = 0.58. Transfer is largest across test formats, to application/inference questions, and — notably for medhavy — to problems involving **medical diagnoses**. ([Pan & Rickard 2018, *Psychological Bulletin* 144(7), 710–756](https://pubmed.ncbi.nlm.nih.gov/29733621/))

This is the single most important number for the medhavy design conversation, because it tells you what to expect when Quiz Me items don't perfectly match the test or clinical situation the student eventually faces. The answer: a real positive transfer of roughly half a standard deviation, larger when there is content overlap, larger still in medical contexts. It's not "free transfer to anything," and it's not "nothing transfers."

**Roediger, Putnam & Smith 2011** `[retrieval-practice]` is the standard pedagogical synthesis. They name ten benefits of testing — including a finding the Quiz Me design should sit with: testing *during* learning improves the learning of *un-tested related material*, by indirectly forcing the student to organize the studied material. ([Roediger, Putnam & Smith 2011, *Psychology of Learning and Motivation* 55, 1–36](https://psycnet.apa.org/record/2011-22030-001) `[verify edition/pages]`)

**McDaniel, Agarwal, Huelser, McDermott & Roediger 2011** `[retrieval-practice]` and **Roediger, Agarwal, McDaniel & McDermott 2011** are the classroom replications. The first study placed quizzes in middle-school science classrooms and observed unit-exam gains of **13–25 percentage points** for quizzed vs. unquizzed material. The second showed long-term improvements from quizzing in a sixth-grade social studies course on within-subject comparisons. These are the most ecologically valid demonstrations of the testing effect — actual K–12 classrooms, actual graded exams, not lab paragraphs. ([McDaniel et al. 2011, *Journal of Educational Psychology* 103, 399–414](https://psycnet.apa.org/record/2011-03466-001); [Roediger et al. 2011, *JEP: Applied* 17, 382–395](https://pdf.retrievalpractice.org/guide/Roediger_Agarwal_etal_2011_JEPA.pdf))

### 1.2 The spaced-repetition canon

**Cepeda, Pashler, Vul, Wixted & Rohrer 2006** `[spaced-repetition]` is the meta-analysis of distributed practice. 839 assessments in 317 experiments across 184 articles. Spaced practice consistently outperforms massed practice for verbal recall, and — the key finding — **the optimal inter-study interval (ISI) is a function of the retention interval (RI)**, not a fixed value. ([Cepeda et al. 2006, *Psychological Bulletin* 132(3), 354–380](https://pubmed.ncbi.nlm.nih.gov/16719566/); [PDF](https://augmentingcognition.com/assets/Cepeda2006.pdf))

This is the most important single empirical result for any scheduling algorithm: there is no universally optimal spacing. The right interval depends on how long you need to retain. A scheduling algorithm that ignores this — that uses fixed intervals like the original Leitner system — is leaving learning on the table.

**Cepeda, Vul, Rohrer, Wixted & Pashler 2008** `[spaced-repetition]` is the empirical specification of the curve. N = 1,354. People learned trivia facts, returned for a single review session at a gap of up to 3.5 months, then took a final test at a delay of up to one year. The optimal ratio of ISI to RI ("optimal gap as a percentage of test delay") **shrinks as the retention interval lengthens**: about 20–40% of a 1-week delay, about 10–20% of a 1-month delay, about **5–10% of a 1-year delay**. ([Cepeda et al. 2008, *Psychological Science* 19(11), 1095–1102](https://pubmed.ncbi.nlm.nih.gov/19076480/); [PDF](https://laplab.ucsd.edu/articles/Cepeda%20et%20al%202008_psychsci.pdf))

For medhavy, this is the spec for what "review timing" should mean. If a student needs to retain a concept for an end-of-semester exam fourteen weeks out, the optimal first re-review is roughly two to three weeks later, not a fixed seven days. FSRS in principle reproduces this kind of expanding interval from data; SM-2 approximates it but uses heuristics rather than fitting a memory model.

**Bjork & Bjork 1992** `[foundational-theory]` is the theoretical scaffold under everything else in this section. The "new theory of disuse" proposes that memory has two independent strengths: **storage strength** (how well-learned the item is, monotonically increases with practice, never decays) and **retrieval strength** (how accessible the item is right now, fluctuates with context and recency). The implication that drives spaced-repetition scheduling: storage strength gains *more* when you retrieve at low retrieval strength than when you retrieve at high retrieval strength. Massed practice keeps retrieval strength high, so each retrieval contributes little. Distributed practice lets retrieval strength fall, so each retrieval forces the work that builds storage strength. ([Bjork & Bjork 1992, in Healy, Kosslyn & Shiffrin (eds.), *From Learning Processes to Cognitive Processes*](https://bjorklab.psych.ucla.edu/wp-content/uploads/sites/13/2016/07/RBjork_EBjork_1992.pdf))

The Quiz Me chapter should treat this as the *theory*. FSRS is one parametric realization of it.

**Kang 2016** `[spaced-repetition]` is the educator-facing synthesis. Spacing produces gains across "diverse content areas (vocabulary, mathematics, science) and age groups" and ought to be a structural feature of curriculum design, not a study-skill tip. ([Kang 2016, *Policy Insights from the Behavioral and Brain Sciences* 3(1), 12–19](https://journals.sagepub.com/doi/10.1177/2372732215624708))

### 1.3 Conceptual vs. factual learning — does the testing effect transfer to understanding?

This is the question Quiz Me has to face directly. Flashcards are good at vocabulary. The medhavy claim is that a quiz mode, scheduled with FSRS, also drives **understanding**. The literature is supportive but cautious.

**Karpicke & Roediger 2008** `[retrieval-practice]` "The critical importance of retrieval for learning" — repeated retrieval, not repeated study, drives long-term retention. ([Karpicke & Roediger 2008, *Science* 319(5865), 966–968](https://www.science.org/doi/10.1126/science.1152408))

**McDaniel, Anderson, Derbish & Morrisette 2007** `[retrieval-practice]` extended the testing effect to a college course on web design. Both fact-based and concept-based questions showed retention benefits — though the gains for transfer items were smaller than for facts directly studied. ([McDaniel et al. 2007, *European Journal of Cognitive Psychology* 19(4–5), 494–513](https://www.tandfonline.com/doi/abs/10.1080/09541440701326154))

**Pan & Rickard 2018** (above) is the meta-analytic answer: transfer happens, d ≈ 0.40, larger with response overlap and in medical-diagnosis contexts. The honest reading for the chapter: retrieval practice does produce conceptual learning beyond rote recall, but the transfer effect is smaller than the within-set retention effect. Quiz Me will need both: well-formed items that test recall *and* items that test application (Pan & Rickard's "application and inference" category, where transfer is largest).

A caution worth flagging for the chapter: the Carpenter line (Carpenter, Pashler, Wixted & Vul 2008; Carpenter 2009) has produced cases where retrieval practice *fails* to transfer to surface-different test conditions — e.g., when the practiced cue and the criterion cue share no overlap. `[verify exact citations and findings]` This is one of the meaningful limits of the mechanism, and a chapter that claims "Quiz Me drives understanding" without naming it is overclaiming.

---

## 2. FSRS specifically — the scheduling algorithm

### 2.1 What FSRS is

FSRS (**Free Spaced Repetition Scheduler**) is an open-source spaced-repetition scheduling algorithm developed since 2022 by Jarrett Ye (research engineer at MaiMemo Inc.) and the open-spaced-repetition community on GitHub. It is the default scheduler in Anki as of version 23.10 (November 2023). ([Open Spaced Repetition project](https://open-spaced-repetition.github.io/); [fsrs4anki repository](https://github.com/open-spaced-repetition/fsrs4anki); [ABC of FSRS wiki](https://github.com/open-spaced-repetition/fsrs4anki/wiki/abc-of-fsrs))

The model represents each card with three latent variables — **D** (Difficulty), **S** (Stability, the number of days at which retrievability is predicted to fall to a target retention level, e.g., 90%), and **R** (Retrievability, the current predicted probability of recall). After each review, the user gives a 1–4 rating (Again / Hard / Good / Easy) and the model updates D and S as a function of the rating, the current R, and the prior values. The next review is scheduled at the time when R is predicted to hit the target retention rate (default 90%). ([fsrs PyPI package documentation](https://pypi.org/project/fsrs/))

The parameters of the update functions are not fixed. They are **trained** on review-log data — initially from the open-spaced-repetition benchmark corpus (350M+ reviews across hundreds of thousands of Anki users), with further personalization once a user has enough reviews of their own.

Underlying theory: FSRS is a parametric reconstruction of the Bjork retrieval-strength / storage-strength duality. Retrievability ≈ retrieval strength (the moment-to-moment access probability). Stability ≈ storage strength (the durable memory trace, expressed in days-to-decay). Difficulty is a per-card calibration that captures how much harder this item is than average for this user.

### 2.2 How FSRS differs from SM-2

**SM-2** (Wozniak, SuperMemo, late 1980s; carried into Anki for the next two decades) is heuristic. Each card has an "ease factor" (default 2.5) and an "interval." On each review the user rates the card 0–5; the rating modifies the ease factor and the next interval is computed as previous_interval × ease_factor, with a piecewise rule for the first two reviews. The model is not trained on data. It has no notion of retrievability — only of "time since last review."

**FSRS** differs structurally on three counts.

1. **Memory model, not heuristic.** FSRS represents a predicted recall probability at any given time; SM-2 represents only "when to show next."
2. **Trained from review logs.** FSRS-5 default parameters were fit on hundreds of millions of user reviews. SM-2 parameters are hand-designed.
3. **Personalization.** FSRS can be re-fit on an individual user's review history once they have ~1,000+ reviews, producing per-user parameters. SM-2's only personalization is the per-card ease factor, which compounds errors when initial ratings are noisy.

### 2.3 FSRS-4 → FSRS-5 → FSRS-6 evolution

Versioning summary from the project documentation `[verify version-by-version specifics with FSRS wiki]`:

- **FSRS-3 / FSRS-4** introduced the trainable Difficulty / Stability / Retrievability model.
- **FSRS-5** (the version Anki shipped as default) added improvements in handling of short-term intervals, "Hard" / "Good" / "Easy" rating differentials, and the cold-start problem (cards with few reviews).
- **FSRS-6** is in the research community as of 2025 with proposed improvements to handling of relearning intervals and to long-term stability decay.

The Anki team's adoption rationale, in summary form: in their internal benchmark against SM-2 on 500M+ review logs, FSRS produces approximately **20–30% fewer reviews** for the same target retention rate; FSRS-5 hits the user's target retention with ±5.3% error vs. SM-2's ±16.2%. ([Expertium FSRS benchmark](https://expertium.github.io/Benchmark.html); [Anki forums on benchmark methodology](https://forums.ankiweb.net/t/fsrs-vs-sm2-in-2-seperate-profiles/52171))

Important caveats the chapter should not skip:

- The benchmark is a **simulation against logged data**, not a controlled experiment comparing learning outcomes under FSRS vs. SM-2. The claim "FSRS produces better scheduling" is established. The claim "FSRS produces better learning" is **not yet demonstrated by RCT**.
- The "20–30% fewer reviews" figure is review-burden, not retention. The retention is held constant at the target.
- The benchmark population is overwhelmingly Anki users — i.e., medical students, language learners, and others using flashcards for factual recall.

### 2.4 Limitations of FSRS

**Cold-start problem.** A card with no review history forces FSRS to fall back on prior distributions from the training corpus. This is more conservative than SM-2's hard-coded short initial intervals, and produces slightly less efficient early scheduling for atypical users.

**Domain shift.** FSRS was trained primarily on Anki review logs — the user population over-represents medical and language flashcard study. Whether FSRS scheduling generalizes to **conceptual material** (mathematics derivations, multi-step physics problems, clinical-reasoning items) where the unit of review is not "atomic fact" is an open empirical question. ([Expertium 2024 benchmark notes](https://expertium.github.io/Benchmark.html))

**Conceptual-material gap.** The Bjork mechanism applies to memory traces generally, and the testing-effect transfer literature (Pan & Rickard 2018, §1.3) extends to inference items. But FSRS's *training data* is dominated by short-text Q&A cards. Whether the same D/S/R parameterization correctly predicts retrievability of an "explain why the Warburg Effect matters in tumor metabolism" item — where partial recall is the norm and binary scoring is approximate — is unresolved.

**The granularity question.** FSRS schedules per item. If a medhavy concept node has ten Quiz Me items, FSRS schedules each one independently. Whether the right unit is the item or the concept node is a design question; the literature does not yet answer it.

### 2.5 Adjacent models from the academic community

FSRS is the implementation that won deployment scale. It is not the only academic model.

**Pavlik & Anderson 2008** `[scheduling-algorithm]` `[foundational-theory]` "Using a model to compute the optimal schedule of practice." An ACT-R-based memory model (the Memory Chain Model / activation-based model of the spacing effect). Each practice repetition adds an activation increment that decays as a power function of time; decay rate depends on the activation at the time of repetition. An optimized practice schedule derived from this model produced **significant gains in recall with large effect sizes** vs. baseline schedules. ([Pavlik & Anderson 2008, *Journal of Experimental Psychology: Applied* 14(2), 101–117](http://act-r.psy.cmu.edu/?post_type=publications&p=14444))

**Mozer et al. Three-Component Model** `[scheduling-algorithm]` (Mozer, Pashler, Cepeda, Lindsey & Vul ≈ 2009; Lindsey, Shroyer, Pashler & Mozer 2014) — augments Pavlik's activation model with a context-dependent component and a study-context-fluctuation component. Lindsey et al. 2014 deployed it in a Spanish vocabulary course and showed improvements over generic spacing. `[verify exact citations]` ([Lindsey, Shroyer, Pashler & Mozer 2014, *Psychological Science* 25(3), 639–647](https://journals.sagepub.com/doi/abs/10.1177/0956797613504302))

**Duolingo half-life regression** (Settles & Meeder 2016, ACL) `[scheduling-algorithm]` — Duolingo's production model. Fits a regression to predict the "half-life" of each item per user, using features of the user, the item, and the prior practice history. Reported a 9.5% reduction in error rate over a Leitner baseline at production scale. ([Settles & Meeder 2016, ACL Proceedings](https://aclanthology.org/P16-1174/))

For the medhavy chapter, the takeaway is that **FSRS sits inside a small research community of memory-model schedulers**. The choice to use FSRS over Pavlik's MCM or Mozer's 3-component model is a design choice grounded in deployment maturity and open-source availability, not a claim that FSRS is theoretically optimal. The chapter should name this rather than imply that FSRS is the unique best answer.

---

## 3. Prerequisite chaining

The medhavy-specific question: when Quiz Me draws an item set for "current concept C," should the set also include items from prerequisite concepts P₁, P₂, …?

The chapter should treat this as two coupled questions: (a) is mixing across concepts beneficial in principle? (b) when a student fails a prerequisite item, what is the right policy — remediate the prerequisite, continue, or both?

### 3.1 Knowledge components and knowledge tracing

**Corbett & Anderson 1995** `[prerequisite-chaining]` `[foundational-theory]` — **Bayesian Knowledge Tracing (BKT)**. The foundational model: each "knowledge component" (KC) is a latent variable representing the probability the student has mastered it. Each practice opportunity updates the probability via a four-parameter HMM (initial knowledge, learn rate, slip, guess). The system continues to drill until P(mastery) exceeds a threshold (commonly 0.95). BKT underlies Cognitive Tutor / Carnegie Learning's Mathia. ([Corbett & Anderson 1995, *User Modeling and User-Adapted Interaction* 4, 253–278](https://link.springer.com/article/10.1007/BF01099821); [PDF](https://act-r.psy.cmu.edu/wordpress/wp-content/uploads/2012/12/893CorbettAnderson1995.pdf))

For medhavy: BKT is the natural model for "should Quiz Me include this prerequisite item?" The answer is yes if and only if P(mastery of the prerequisite KC) is below threshold. Medhavy's concept node map gives the KC granularity; Quiz Me logs give the evidence to update P(mastery); BKT or a successor model produces the per-item inclusion policy.

**Yudelson, Koedinger & Gordon 2013** `[prerequisite-chaining]` — Individualized BKT. Per-student initial-knowledge and learn-rate parameters substantially improve prediction over the standard BKT with population parameters. The chapter should treat this as the empirical evidence that BKT-style scheduling needs per-learner personalization, not population averages. ([Yudelson, Koedinger & Gordon 2013, AIED 2013](https://link.springer.com/chapter/10.1007/978-3-642-39112-5_18))

**Piech, Bassen, Huang, Ganguli, Sahami, Guibas & Sohl-Dickstein 2015** `[prerequisite-chaining]` — **Deep Knowledge Tracing (DKT)**. A recurrent neural network replaces BKT's hand-coded structure. DKT learns the KC relationships implicitly from data. Reported gains over BKT on standard datasets (ASSISTments, Khan Academy) ranged from 5% to 25% AUC improvement, though follow-up work (Khajah, Lindsey & Mozer 2016) showed BKT with a few extensions could match much of the gain. ([Piech et al. 2015, NeurIPS 2015](https://papers.nips.cc/paper/2015/hash/bac9162b47c56fc8a4d2a519803d51b3-Abstract.html); [Khajah, Lindsey & Mozer 2016](https://arxiv.org/abs/1604.02416))

For medhavy: DKT-style models matter because they don't require the concept map to be hand-tagged with prerequisite relationships. Given enough usage data, the model learns them. Medhavy's Tic TOC produces an explicit concept map (advantage: interpretable, ready on day one; cost: depends on the professor getting prerequisites right). A DKT-style backend could be deployed *over* Tic TOC's hand-coded map to validate or revise it from logged performance.

### 3.2 Prior-knowledge gaps as predictor of learning failure

**Schneider, Rittle-Johnson & Star 2011** `[prerequisite-chaining]` and the broader Schneider line — prior conceptual knowledge is a strong predictor of subsequent learning, with effects that compound when prerequisite gaps are not remediated. ([Schneider et al. 2011, *Journal of Educational Psychology* 103(2), 357–367](https://psycnet.apa.org/record/2011-04898-002) `[verify]`)

**Booth, Newton et al.** on fraction misconceptions `[prerequisite-chaining]` `[verify exact citations]` — students who enter an algebra course with unaddressed fraction misconceptions show systematic algebra failure. The mechanism is structural: the new content recruits the prerequisite, so the prerequisite gap surfaces as a current-concept failure that looks like a content problem but is actually a prerequisite problem. ([Booth & Newton 2012, *Contemporary Educational Psychology* 37, 247–253](https://www.sciencedirect.com/science/article/abs/pii/S0361476X12000343))

This is the empirical answer to "why bother chaining prerequisites in Quiz Me?" Because failure on the current concept will, in a sizable fraction of cases, be misdiagnosed as misunderstanding the current concept when it is actually a stale prerequisite. The signal is in the items, not in the chapter title.

### 3.3 Interleaving vs. blocked practice

This is the literature on whether quizzing across multiple concepts produces better learning than quizzing one concept at a time.

**Rohrer & Taylor 2007** `[spaced-repetition]` `[prerequisite-chaining]` is the foundational result. College students learned to compute the volumes of four geometric solids. Half practiced each solid type in a blocked schedule; half practiced the four interleaved. On a delayed test, interleaved practice produced **74% accuracy vs. 49%** for blocked — an enormous effect, despite the interleaved group performing *worse* during practice. ([Rohrer & Taylor 2007, *Instructional Science* 35, 481–498](http://uweb.cas.usf.edu/~drohrer/pdfs/Rohrer&Taylor2007IS.pdf))

The performance-vs.-learning inversion is Soderstrom & Bjork's distinction (§4) in concrete form. Interleaved practice felt harder during the session; it produced more durable learning.

**Rohrer 2012** `[spaced-repetition]` is the *Educational Psychology Review* synthesis. Interleaving works because it forces students to **discriminate** between problem types — to identify *which* tool the problem calls for, not just to apply a tool that's been pre-named at the top of the practice block. ([Rohrer 2012, *Educational Psychology Review* 24, 355–367](https://files.eric.ed.gov/fulltext/ED536926.pdf))

**Rohrer, Dedrick & Stershic 2015** `[spaced-repetition]` `[verify exact citation]` — a randomized field trial in middle-school math. Interleaved practice produced **roughly double** the test scores of blocked practice on a delayed unit test. ([Rohrer, Dedrick & Stershic 2015, *Journal of Educational Psychology* 107, 900–908](https://psycnet.apa.org/record/2014-56685-001))

**Brunmair & Richter 2019** `[spaced-repetition]` meta-analysis of interleaving — the effect is robust for category-learning tasks (where discriminating between categories is the point) but smaller or null for tasks where category discrimination is not the bottleneck. ([Brunmair & Richter 2019, *Psychological Bulletin* 145(11), 1029–1052](https://psycnet.apa.org/record/2019-44922-001))

For medhavy: **interleaving across concept nodes is the empirical default in the literature for category-learning tasks** (clinical diagnosis, math problem-type identification, language discrimination). For pure factual recall, the benefit is smaller. Quiz Me's design choice to mix current-concept and prerequisite items is supported by the discrimination-learning evidence. The cautious version of the claim for the chapter: interleaving helps when the cognitive challenge is "which tool / concept / diagnosis applies?", which is most of the time in medicine and clinical reasoning.

### 3.4 Remediation policy — inner loop vs. outer loop

When a student fails a prerequisite item inside Quiz Me, should the system (a) continue with the current concept items, (b) interrupt with a prerequisite re-explanation, or (c) silently drop the failed prerequisite into the future review queue?

**VanLehn 2006** `[prerequisite-chaining]` `[foundational-theory]` "The behavior of tutoring systems" introduced the distinction the field has used since: the **inner loop** is feedback and hint generation within a single problem step; the **outer loop** is the selection of which problem to give next. Most ITS work has been on the inner loop. The outer loop — which often *is* the prerequisite-remediation decision — has been studied less. ([VanLehn 2006, *International Journal of AI in Education* 16(3), 227–265](https://dl.acm.org/doi/10.5555/1435351.1435353))

For medhavy's Quiz Me: the policy choice ("remediate first vs. continue") is an **outer-loop** choice. Inner-loop work (per-question hints, explanations after wrong answers) is mostly handled by the Ask AI mode. The outer loop is the bandit's job.

**Aleven, McLaren, Roll & Koedinger 2016** `[prerequisite-chaining]` — combined inner+outer loop tutoring outperforms inner-loop-only feedback. The combination matters because inner-loop feedback fixes the local error; outer-loop feedback (re-scheduling the missed prerequisite for re-practice) fixes the underlying gap. ([Aleven, McLaren, Roll & Koedinger 2016, *International Journal of AI in Education* 26, 205–223](http://www.cs.cmu.edu/~aleven/Papers/2016/Aleven_etal_ITS2016_Tutors_in_MOOCs.pdf))

**Practical synthesis for the chapter.** The defensible Quiz Me policy is *not* to interrupt the current quiz with a forced remediation tangent. The defensible policy is:

1. **Inside the quiz session**: tag the failed prerequisite item, schedule it for high-priority re-review at the next FSRS retrievability dip (typically same day or next day), and continue the current-concept items.
2. **Across sessions**: when prerequisite-failure pattern crosses a threshold (e.g., the student is below mastery on the prerequisite KC), surface a recommendation — *"Looks like fractions are getting in the way of factoring. Want a 10-minute refresher?"* — that hands the student agency rather than forcing the interrupt.
3. **In the bandit**: the prerequisite-failure rate is a strong signal that the *Ask AI* mode (re-explanation) or a re-read of the prerequisite section may be the right next move, not another quiz session.

This is consistent with the Aleven combined-loop finding *and* with the Bjork desirable-difficulty principle (§4). The system uses the failure data for spaced re-quizzing rather than for synchronous tangent-remediation.

---

## 4. Availability gating

Medhavy gates Quiz Me until after the section is read. This is not a default in the spaced-repetition literature — most Anki / SuperMemo workflows start the user on the cards immediately. The gating decision is medhavy-specific and rests on a particular reading of when retrieval practice becomes effective.

### 4.1 Why gate at all — the prerequisite for retrieval

Retrieval practice requires *something to retrieve*. The Bastani et al. 2025 finding (cited in `ask-ai-research.md`) — that students who used unguarded GPT-4 during practice scored 17 percentage points lower on the no-AI exam — generalizes to a broader principle: practice without prior encoding produces performance during the practice and no learning afterward.

Quiz Me before the section is read would produce Bastani's failure mode in a different costume. The student would either (a) guess and get random feedback, which produces noise rather than learning, or (b) succeed on items by elimination and surface heuristics, which the FSRS algorithm will read as "they know this" and downschedule, leaving the gap unrecognized.

### 4.2 Soderstrom & Bjork 2015 — performance vs. learning

**Soderstrom & Bjork 2015** `[foundational-theory]` `[retrieval-practice]` is the integrative review. Performance during an instructional session is an unreliable measure of durable learning. The two can be **inversely related**: conditions that produce the best performance often produce the worst learning, and vice versa. ([Soderstrom & Bjork 2015, *Perspectives on Psychological Science* 10(2), 176–199](https://pubmed.ncbi.nlm.nih.gov/25910388/))

For medhavy: this is the canonical citation for the gate. If Quiz Me is offered before the section is read, the system collects performance data (the student answered the question, possibly correctly), but no learning has occurred. The metric goes up. The learning does not. This is the IDK IDK failure mode rediscovered: the engagement signal is real and the cognitive event isn't.

### 4.3 Desirable difficulties — the gate as a design choice

**Bjork & Bjork 2011** `[foundational-theory]` introduced **"desirable difficulties"** — practice conditions that feel harder during the session but produce better long-term retention. Spacing, interleaving, and retrieval practice are all canonical desirable difficulties. ([Bjork & Bjork 2011, in Gernsbacher, Pew, Hough & Pomerantz (eds.), *Psychology and the Real World*](https://bjorklab.psych.ucla.edu/wp-content/uploads/sites/13/2016/04/EBjork_RBjork_2011.pdf))

The gate is a desirable-difficulty boundary in two directions:

- **Too-early gate (no gate)**: the student has nothing to retrieve, so retrieval practice produces only guessing. The Bastani failure mode.
- **Too-late gate (excessive reading requirement)**: the student has forgotten what they read, so retrieval practice has to start at near-zero retrievability, which is inefficient. Bjork's "forgetting has run too far" condition.

The optimal gate is somewhere in between. The empirical literature does not yet specify exactly where, but the structural shape is clear: *enough exposure to encode, soon enough that retrieval is productive, far enough out that retrieval is non-trivial*.

### 4.4 Quiz timing — immediate vs. delayed

**Roediger, Agarwal, McDaniel & McDermott 2011** `[retrieval-practice]` (cited above) — in the middle-school classroom replication, quizzes administered the day of the lesson and quizzes administered later both produced gains, with both spacing and quizzing contributing independently. ([Roediger et al. 2011, *JEP: Applied* 17, 382–395](https://pdf.retrievalpractice.org/guide/Roediger_Agarwal_etal_2011_JEPA.pdf))

**Karpicke 2009** `[retrieval-practice]` — meta-cognitive evidence that students systematically under-use retrieval practice because they misjudge what produces learning. Students prefer to re-read (which feels productive) over self-test (which feels uncomfortable). The gate is partly a paternalism-vs.-agency choice: medhavy gates because students left to their own devices will skip the quizzing entirely, not because reading-then-quizzing is empirically better than quizzing-then-reading. ([Karpicke 2009, *Journal of Experimental Psychology: General* 138(4), 469–486](https://psycnet.apa.org/record/2009-23492-001))

A point the chapter should sit with: "**read first, quiz second**" is the medhavy design, *not* a finding from the literature. The literature supports the broader claim that quizzing-without-prior-encoding is unproductive. Whether the optimal gate is "section read once" or "section read once and reviewed" or "section read and one practice problem worked" is unresolved. Medhavy's choice is defensible; it is not the only defensible choice.

### 4.5 Retrieval-induced forgetting — a counter-finding the chapter should name

**Anderson, Bjork & Bjork 1994** `[foundational-theory]` introduced **retrieval-induced forgetting**: practicing retrieval of some items from a category produces *worsened* recall of un-practiced items from the same category. ([Anderson, Bjork & Bjork 1994, *Journal of Experimental Psychology: Learning, Memory, and Cognition* 20(5), 1063–1087](https://psycnet.apa.org/record/1995-08438-001) `[verify]`)

This is the most important boundary condition on the testing effect that the practitioner literature routinely ignores. If Quiz Me drills items A, B, C from a node and skips D, E, F from the same node, D, E, F may end up *less* recalled than they would have been with no practice at all. The medhavy chapter should name this and explain how the item-selection policy handles it (full coverage, or explicit acknowledgment that uncovered items are at risk).

---

## 5. Medical and clinical applications

This is the cleanest application domain for medhavy's claims. Two things make it special: high-stakes durable knowledge (boards, clinical practice years later), and a mature flashcard ecosystem (Anki, AnKing) that has produced informal natural-experiment evidence at scale.

### 5.1 The Augustin synthesis

**Augustin 2014** `[medical-application]` `[retrieval-practice]` `[spaced-repetition]` "How to learn effectively in medical school: test yourself, learn actively, and repeat in intervals." A *Yale Journal of Biology and Medicine* review pulling three converging mechanisms — testing effect, active recall, spaced repetition — into a single set of practical recommendations for medical students. ([Augustin 2014, *Yale J Biol Med* 87(2), 207–212](https://pmc.ncbi.nlm.nih.gov/articles/PMC4031794/))

For medhavy: this is the entry-level citation for "yes, this matters in medical education." The next several citations are the harder evidence.

### 5.2 Kerfoot's spaced-education RCTs

**Kerfoot, Baker, Connelly et al.** `[medical-application]` `[spaced-repetition]` `[retrieval-practice]` ran a series of randomized trials of "spaced education" — short clinical scenarios with multiple-choice questions delivered by email at scheduled intervals — across urology, surgery, and CME contexts in the late 2000s.

- **Kerfoot 2008 / 2009 *Annals of Surgery*** `[medical-application]` — 480 urology residents and attendings randomized. Spaced education vs. control on clinical-practice-guideline knowledge. Cohort A scores increased from 44.9% to 75.7% across three cycles; Cohort B scores increased from 45.2% to 69.5%. Effects persisted to delayed testing. ([Kerfoot et al. 2009, *Annals of Surgery*](https://journals.lww.com/annalsofsurgery/Abstract/2009/05000/Interactive_Spaced_Education_to_Assess_and_Improve.11.aspx))
- **Kerfoot 2007 *Medical Education*** `[medical-application]` — RCT in medical students of spaced education to retain clinical knowledge. Significantly improved retention vs. control. ([Kerfoot et al. 2007, *Medical Education* 41, 23–31](https://pubmed.ncbi.nlm.nih.gov/17209889/))
- **Kerfoot 2008 *Journal of Urology*** `[medical-application]` — multi-institutional RCT, online spaced education for urology to medical students. ([Kerfoot et al. 2008, *J Urology*](https://pubmed.ncbi.nlm.nih.gov/18614145/))
- **Kerfoot, Fu, Baker, Gonella, Brotchie, Hoyer & Lukes 2010 *Annals of Surgery*** `[medical-application]` — online spaced education generates **transfer** and improves long-term retention of diagnostic skills. ([Kerfoot et al. 2010, *Annals of Surgery* 252(2), 350–359](https://pubmed.ncbi.nlm.nih.gov/20800189/))

The Kerfoot line is the best body of medical-education evidence for spaced retrieval practice in real clinical contexts. Effect sizes are not always reported in standardized form, but the relative gains (50%+ improvements over baseline within cohort; significant advantages over control) are large and consistent across studies.

### 5.3 Anki and AnKing in medical training

**Lu, Farhat & Beck Dallaghan 2021** `[medical-application]` and adjacent cohort studies — the AnKing deck and its predecessors (Zanki, Brosencephalon) are the de facto standard medical-school spaced-repetition resource. A cohort study found that the percentage of "mature" Anki cards predicted course exam performance, with one model finding it the single statistically significant predictor of score, explaining over a third of variance. ([Lu et al. 2021, *Medical Science Educator*](https://pubmed.ncbi.nlm.nih.gov/37546209/) `[verify exact authors/journal/date]`)

This is the closest the literature gets to an effect-size claim for Anki specifically in medical training. The honest reading: it's a correlational, single-cohort study. Selection effects are non-trivial — students who use Anki extensively are likely also students with stronger study habits generally. The causal estimate is unclear.

**The AnKing phenomenon** more broadly: AnKing v12 contains ~30,000 cards mapped to First Aid, Boards & Beyond, Pathoma, Sketchy, UWorld, etc. It is reported to be used by 100,000+ medical students. There is no peer-reviewed RCT comparing AnKing-users vs. non-AnKing-users on board scores `[verify]`.

For medhavy: this is the natural-experiment evidence that medical students *believe* spaced repetition matters and that the practice has scaled to a substantial fraction of the U.S. medical-school population. It is not RCT evidence. The chapter should treat AnKing as a real phenomenon worth explaining, not as proof of effect size.

### 5.4 Spaced repetition in residency

**Versteeg, Pol, van Loon & Pijls 2022** `[medical-application]` — RCT of spaced learning vs. massed learning for clinical reasoning in radiology residents. Spaced learning improved retention at 3 months. ([Versteeg et al. 2022, *Medical Education* `[verify exact citation]`])

**Goyal, Singh & Sharma** `[medical-application]` `[verify]` — additional resident-level studies of spaced education across specialties.

### 5.5 Durability — what the evidence shows at 6 and 12 months

Across the Kerfoot studies and the broader medical-education spaced-repetition literature: retention advantages of spaced over massed practice **persist to 6 months and beyond** in the majority of studies. The Kerfoot 2010 *Annals of Surgery* transfer study showed durable effects on diagnostic skills at long-term follow-up.

A note for the chapter: the durability finding is the most important specific claim for medical education, because clinical knowledge is supposed to last beyond the exam. A textbook that gets students through Step 1 and produces no durable clinical knowledge fails. Spaced retrieval is the literature's best answer to that durability problem.

---

## 6. The medhavy planning docs — what Quiz Me actually is

The planning files (`book.md`, `outline.md`, `vision.md`, `architecture.md`, `chapters-spec.md`, `risks.md`) are mostly Tic TOC scaffolding templates with `[NEEDS HUMAN INPUT]` placeholders. The chapter prose in `chapters/01-what-is-medhavy.md` and `chapters/04-what-makes-this-different.md` is the working specification of Quiz Me, alongside what is implied by Tic TOC and the four-layer architecture.

### 6.1 What Quiz Me actually is, per the chapters

From `chapters/01-what-is-medhavy.md` §"The Four Layers" / Layer 3:

> **Quiz Me** — Spaced retrieval practice using FSRS (Free Spaced Repetition Scheduler), an evidence-based algorithm for scheduling review at the intervals that maximize durable retention. The questions are generated from the concept map, calibrated to what this student got wrong or uncertain on last time. Not random. Not the same quiz for every student.

From `chapters/04-what-makes-this-different.md` §"Intelligence Is Not One Thing":

> Quiz Me activates retrieval pathways and consolidates storage — appropriate when the representation needs to become durable.

The implied design contract:

1. Items are generated from the **concept node map** (the Tic TOC output).
2. Items are **calibrated to the individual student's prior errors** — i.e., per-learner item selection.
3. Scheduling is **FSRS** — interval determined by D/S/R prediction.
4. Quiz Me is one of four modes — the **contextual bandit** in 2.0 will decide when to offer Quiz Me vs. Ask AI vs. Case Study vs. Glimmer.
5. Quiz Me is gated until **after the section is read** (the brief states this; the chapter does not yet state it explicitly).

### 6.2 Evidence-base mapping

| Quiz Me claim | Evidence class | Strongest support | Weakest/most disputed |
|---|---|---|---|
| Retrieval practice produces durable learning | `[retrieval-practice]` | Adesope et al. 2017 g = 0.51; Roediger & Karpicke 2006 | Pan & Rickard 2018: transfer d = 0.40, smaller than within-set |
| Spaced scheduling beats massed | `[spaced-repetition]` | Cepeda et al. 2006 meta-analysis | Boundary: when items are independent — not when concepts cohere into structures |
| Optimal interval scales with retention horizon | `[spaced-repetition]` | Cepeda et al. 2008 (5–40% of RI) | Practical estimate, not point parameter |
| FSRS is better than SM-2 | `[scheduling-algorithm]` | Anki team benchmark, 20–30% fewer reviews | No RCT comparing FSRS vs. SM-2 on learning outcomes |
| Prerequisite chaining helps | `[prerequisite-chaining]` | Rohrer interleaving studies; BKT-based ITS results | Effect concentrated in category-discrimination tasks |
| Quiz Me drives understanding, not just recall | `[retrieval-practice]` (transfer) | Pan & Rickard 2018 d = 0.40 to inference items | Carpenter line on transfer failures |
| Gating before retrieval is correct | `[foundational-theory]` | Soderstrom & Bjork 2015; Bastani et al. 2025 generalization | No direct comparison study of "gate at section read" vs. alternatives |

### 6.3 Design choices to flag

**Three design points where medhavy's stated choices diverge from canonical evidence — none fatal, all worth naming in the chapter:**

1. **FSRS is named as the scheduler without comparison to MCM / Pavlik or 3-component / Mozer.** This is a defensible deployment choice (FSRS is the open-source standard, well-maintained, runs at scale). It is not a theoretical claim that FSRS is uniquely optimal. The chapter should be honest about the choice.
2. **The within-learner bandit will treat each mode as an arm.** This is consistent with the literature on adaptive instructional policies, but the literature does *not* yet have an RCT-validated multi-arm bandit on Quiz Me / Ask AI / Case Study / Glimmer as competing arms. Medhavy's 2.0 will be running the experiment, not citing it.
3. **The "questions calibrated to what the student got wrong" claim implies per-learner item generation.** If item generation is template-based with student-specific parameters, that is well-supported by the ITS literature (Cognitive Tutor, ASSISTments). If item generation is LLM-based from the concept map with prior-error context, that is unvalidated — the LLM-generated assessment literature is too thin for confident claims about item quality. The chapter should be specific about which one is happening.

### 6.4 The single sharpest finding for the Quiz Me design

**Cepeda et al. 2008's "optimal gap as a fraction of retention interval" is the single most operationally relevant finding for Quiz Me.** It says: the right scheduling interval is not a constant; it is a function of how long you need to retain. FSRS's target-retention parameter is the implementation handle. The default of 90% retention is a deployment choice with substantial scheduling consequences. The chapter should explain that this parameter is what the algorithm is actually optimizing — and what target the medhavy deployment uses.

---

## 7. Key citations consolidated

*Chicago author-date style. Tagged by evidence class.*

Adesope, Olusola O., Dominic A. Trevisan, and Narayankripa Sundararajan. 2017. "Rethinking the Use of Tests: A Meta-Analysis of Practice Testing." *Review of Educational Research* 87 (3): 659–701. https://doi.org/10.3102/0034654316689306. `[retrieval-practice]`

Aleven, Vincent, Bruce M. McLaren, Ido Roll, and Kenneth R. Koedinger. 2016. "Help Helps, But Only So Much: Research on Help Seeking with Intelligent Tutoring Systems." *International Journal of Artificial Intelligence in Education* 26 (1): 205–223. `[prerequisite-chaining]`

Anderson, Michael C., Robert A. Bjork, and Elizabeth L. Bjork. 1994. "Remembering Can Cause Forgetting: Retrieval Dynamics in Long-Term Memory." *Journal of Experimental Psychology: Learning, Memory, and Cognition* 20 (5): 1063–1087. `[foundational-theory]` `[verify]`

Augustin, Marc. 2014. "How to Learn Effectively in Medical School: Test Yourself, Learn Actively, and Repeat in Intervals." *Yale Journal of Biology and Medicine* 87 (2): 207–212. https://pmc.ncbi.nlm.nih.gov/articles/PMC4031794/. `[medical-application]`

Bastani, Hamsa, Osbert Bastani, Alp Sungu, Haosen Ge, Özge Kabakcı, and Rei Mariman. 2025. "Generative AI Can Harm Learning." *PNAS* 122 (26): e2422633122. https://doi.org/10.1073/pnas.2422633122. `[retrieval-practice]` (generalization to LLM-mediated practice)

Bjork, Robert A., and Elizabeth L. Bjork. 1992. "A New Theory of Disuse and an Old Theory of Stimulus Fluctuation." In *From Learning Processes to Cognitive Processes: Essays in Honor of William K. Estes*, edited by Alice F. Healy, Stephen M. Kosslyn, and Richard M. Shiffrin, Vol. 2, 35–67. Hillsdale, NJ: Erlbaum. `[foundational-theory]`

Bjork, Elizabeth L., and Robert A. Bjork. 2011. "Making Things Hard on Yourself, But in a Good Way: Creating Desirable Difficulties to Enhance Learning." In *Psychology and the Real World: Essays Illustrating Fundamental Contributions to Society*, edited by Morton A. Gernsbacher, Richard W. Pew, Leaetta M. Hough, and James R. Pomerantz, 56–64. New York: Worth. `[foundational-theory]`

Booth, Julie L., and Kristie J. Newton. 2012. "Fractions: Could They Really Be the Gatekeeper's Doorman?" *Contemporary Educational Psychology* 37 (4): 247–253. `[prerequisite-chaining]`

Brunmair, Matthias, and Tobias Richter. 2019. "Similarity Matters: A Meta-Analysis of Interleaved Learning and Its Moderators." *Psychological Bulletin* 145 (11): 1029–1052. `[spaced-repetition]`

Cepeda, Nicholas J., Harold Pashler, Edward Vul, John T. Wixted, and Doug Rohrer. 2006. "Distributed Practice in Verbal Recall Tasks: A Review and Quantitative Synthesis." *Psychological Bulletin* 132 (3): 354–380. https://doi.org/10.1037/0033-2909.132.3.354. `[spaced-repetition]`

Cepeda, Nicholas J., Edward Vul, Doug Rohrer, John T. Wixted, and Harold Pashler. 2008. "Spacing Effects in Learning: A Temporal Ridgeline of Optimal Retention." *Psychological Science* 19 (11): 1095–1102. https://doi.org/10.1111/j.1467-9280.2008.02209.x. `[spaced-repetition]`

Corbett, Albert T., and John R. Anderson. 1995. "Knowledge Tracing: Modeling the Acquisition of Procedural Knowledge." *User Modeling and User-Adapted Interaction* 4 (4): 253–278. `[prerequisite-chaining]` `[foundational-theory]`

Kang, Sean H. K. 2016. "Spaced Repetition Promotes Efficient and Effective Learning: Policy Implications for Instruction." *Policy Insights from the Behavioral and Brain Sciences* 3 (1): 12–19. https://doi.org/10.1177/2372732215624708. `[spaced-repetition]`

Karpicke, Jeffrey D. 2009. "Metacognitive Control and Strategy Selection: Deciding to Practice Retrieval During Learning." *Journal of Experimental Psychology: General* 138 (4): 469–486. `[retrieval-practice]`

Karpicke, Jeffrey D., and Janell R. Blunt. 2011. "Retrieval Practice Produces More Learning than Elaborative Studying with Concept Mapping." *Science* 331 (6018): 772–775. https://doi.org/10.1126/science.1199327. `[retrieval-practice]`

Karpicke, Jeffrey D., and Henry L. Roediger III. 2008. "The Critical Importance of Retrieval for Learning." *Science* 319 (5865): 966–968. `[retrieval-practice]`

Kerfoot, B. Price, William C. DeWolf, Barbara A. Masser, Paul A. Church, and Daniel D. Federman. 2007. "Spaced Education Improves the Retention of Clinical Knowledge by Medical Students: A Randomised Controlled Trial." *Medical Education* 41 (1): 23–31. `[medical-application]`

Kerfoot, B. Price, Yulei Fu, Harley Baker, Joseph Gonella, Anne Brotchie, Charlotte Hoyer, and Anthony C. Lukes. 2010. "Online Spaced Education Generates Transfer and Improves Long-Term Retention of Diagnostic Skills: A Randomized Controlled Trial." *Annals of Surgery* 252 (2): 350–359. `[medical-application]`

Kerfoot, B. Price, Harley Baker, Mary O. Koch, Daniel Connelly, David B. Joseph, and Martin L. Ritchey. 2007. "Randomized, Controlled Trial of Spaced Education to Urology Residents in the United States and Canada." *Journal of Urology* 177 (4): 1481–1487. `[medical-application]`

Khajah, Mohammad, Robert V. Lindsey, and Michael C. Mozer. 2016. "How Deep Is Knowledge Tracing?" In *Proceedings of the 9th International Conference on Educational Data Mining (EDM 2016)*. https://arxiv.org/abs/1604.02416. `[prerequisite-chaining]`

Lindsey, Robert V., Jeffery D. Shroyer, Harold Pashler, and Michael C. Mozer. 2014. "Improving Students' Long-Term Knowledge Retention through Personalized Review." *Psychological Science* 25 (3): 639–647. https://doi.org/10.1177/0956797613504302. `[scheduling-algorithm]` `[spaced-repetition]`

McDaniel, Mark A., Janis L. Anderson, Mary H. Derbish, and Nova Morrisette. 2007. "Testing the Testing Effect in the Classroom." *European Journal of Cognitive Psychology* 19 (4–5): 494–513. `[retrieval-practice]`

McDaniel, Mark A., Pooja K. Agarwal, Barbie J. Huelser, Kathleen B. McDermott, and Henry L. Roediger III. 2011. "Test-Enhanced Learning in a Middle School Science Classroom: The Effects of Quiz Frequency and Placement." *Journal of Educational Psychology* 103 (2): 399–414. `[retrieval-practice]`

Pan, Steven C., and Timothy C. Rickard. 2018. "Transfer of Test-Enhanced Learning: Meta-Analytic Review and Synthesis." *Psychological Bulletin* 144 (7): 710–756. https://doi.org/10.1037/bul0000151. `[retrieval-practice]`

Pavlik, Philip I., and John R. Anderson. 2008. "Using a Model to Compute the Optimal Schedule of Practice." *Journal of Experimental Psychology: Applied* 14 (2): 101–117. `[scheduling-algorithm]` `[foundational-theory]`

Piech, Chris, Jonathan Bassen, Jonathan Huang, Surya Ganguli, Mehran Sahami, Leonidas J. Guibas, and Jascha Sohl-Dickstein. 2015. "Deep Knowledge Tracing." In *Advances in Neural Information Processing Systems 28 (NeurIPS 2015)*, 505–513. `[prerequisite-chaining]`

Roediger, Henry L., III, Pooja K. Agarwal, Mark A. McDaniel, and Kathleen B. McDermott. 2011. "Test-Enhanced Learning in the Classroom: Long-Term Improvements from Quizzing." *Journal of Experimental Psychology: Applied* 17 (4): 382–395. `[retrieval-practice]`

Roediger, Henry L., III, and Jeffrey D. Karpicke. 2006. "Test-Enhanced Learning: Taking Memory Tests Improves Long-Term Retention." *Psychological Science* 17 (3): 249–255. https://doi.org/10.1111/j.1467-9280.2006.01693.x. `[retrieval-practice]`

Roediger, Henry L., III, Adam L. Putnam, and Megan A. Smith. 2011. "Ten Benefits of Testing and Their Applications to Educational Practice." *Psychology of Learning and Motivation* 55: 1–36. `[retrieval-practice]`

Rohrer, Doug. 2012. "Interleaving Helps Students Distinguish among Similar Concepts." *Educational Psychology Review* 24 (3): 355–367. `[spaced-repetition]`

Rohrer, Doug, Robert F. Dedrick, and Sandra Stershic. 2015. "Interleaved Practice Improves Mathematics Learning." *Journal of Educational Psychology* 107 (3): 900–908. `[spaced-repetition]`

Rohrer, Doug, and Kelli Taylor. 2007. "The Shuffling of Mathematics Problems Improves Learning." *Instructional Science* 35 (6): 481–498. `[spaced-repetition]` `[prerequisite-chaining]`

Settles, Burr, and Brendan Meeder. 2016. "A Trainable Spaced Repetition Model for Language Learning." In *Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics (ACL 2016)*, 1848–1858. `[scheduling-algorithm]`

Schneider, Michael, Bethany Rittle-Johnson, and Jon R. Star. 2011. "Relations among Conceptual Knowledge, Procedural Knowledge, and Procedural Flexibility in Two Samples Differing in Prior Knowledge." *Developmental Psychology* 47 (6): 1525–1538. `[prerequisite-chaining]` `[verify]`

Soderstrom, Nicholas C., and Robert A. Bjork. 2015. "Learning Versus Performance: An Integrative Review." *Perspectives on Psychological Science* 10 (2): 176–199. https://doi.org/10.1177/1745691615569000. `[foundational-theory]`

VanLehn, Kurt. 2006. "The Behavior of Tutoring Systems." *International Journal of Artificial Intelligence in Education* 16 (3): 227–265. `[prerequisite-chaining]` `[foundational-theory]`

Wozniak, Piotr A., and Edward J. Gorzelanczyk. 1994. "Optimization of Repetition Spacing in the Practice of Learning." *Acta Neurobiologiae Experimentalis* 54: 59–62. (Original SM-2 algorithm specification.) `[scheduling-algorithm]`

Ye, Jarrett, and the Open Spaced Repetition community. 2022–2025. *Free Spaced Repetition Scheduler (FSRS) algorithm and documentation.* https://github.com/open-spaced-repetition/fsrs4anki; https://open-spaced-repetition.github.io/. (Algorithm specification, FSRS-4 / FSRS-5 / FSRS-6.) `[scheduling-algorithm]`

Yudelson, Michael V., Kenneth R. Koedinger, and Geoffrey J. Gordon. 2013. "Individualized Bayesian Knowledge Tracing Models." In *Artificial Intelligence in Education (AIED 2013)*, 171–180. `[prerequisite-chaining]`

---

## 8. Boundary cases and common mis-citations the chapter must avoid

The practitioner literature on "spaced repetition" routinely conflates the three classes of evidence catalogued above. The chapter should treat each of the following confusions as a tripwire — name and refuse.

**Mis-citation 1.** "Anki improves learning by 1.5 standard deviations." This is the Karpicke & Blunt 2011 effect size, which compared free recall to concept mapping in a one-week lab study. It is **retrieval-practice mechanism** evidence in a controlled comparison. It is *not* an effect size for Anki, FSRS, or any other product. Vendor pages routinely re-attribute it. The chapter should not.

**Mis-citation 2.** "FSRS is the most evidence-based spaced repetition algorithm." FSRS has the largest benchmark corpus (Anki review logs at 500M+ scale) and the most active open-source maintenance. It has *not* been compared against alternatives (MCM, Mozer 3-component, half-life regression) in a head-to-head learning-outcome RCT. The chapter should use "production-mature implementation of spaced repetition theory" rather than "most evidence-based algorithm."

**Mis-citation 3.** "Spaced repetition produces a 200% improvement in retention." This appears in Anki / SuperMemo marketing and traces back to Wozniak's own non-peer-reviewed analyses of SM-2 from the 1990s. The peer-reviewed effect sizes (Cepeda et al. 2006 spacing meta-analysis; Adesope et al. 2017 testing meta-analysis) are g ≈ 0.5–0.7 — substantial but not 200%.

**Mis-citation 4.** "The testing effect proves Anki works." Conflates mechanism with implementation. The testing effect proves *that retrieval practice* produces durable learning. Anki, FSRS, and other tools are *implementations of scheduling for retrieval practice*. The link is real but not identity; a poorly scheduled retrieval-practice tool will under-deliver on the mechanism, and a well-designed non-flashcard retrieval activity will deliver on it without using any scheduling algorithm at all.

---

## 9. The open questions the literature does not yet resolve

Listed for the chapter's "What we don't yet know" / "Still puzzling" sections.

1. **Does FSRS-style scheduling generalize beyond atomic factual flashcards to conceptual material?** The benchmark corpus is Anki-dominated, which over-samples vocabulary, medical facts, and discrete Q&A. Whether the same D/S/R parameterization correctly handles "explain the Warburg Effect" or "derive Bayes' rule from first principles" is unstudied.
2. **What is the right granularity for retrievability tracking — item or concept node?** FSRS schedules per item. Medhavy thinks in concept nodes. The mapping is unspecified in the literature.
3. **Is mixing current-concept and prerequisite items in a single Quiz Me session better than separating them?** The interleaving literature suggests yes; the cognitive-load literature suggests "depends on prerequisite gap depth." No clean experiment for this in adaptive-platform contexts.
4. **When a prerequisite is failed inside Quiz Me, is forced remediation better than queued re-review?** The Aleven combined-loop work is the closest evidence; it does not specify whether the outer-loop re-scheduling should be synchronous (interrupt the session) or asynchronous (next session).
5. **What is the optimal "gate" before Quiz Me opens?** Section read once, section read with one worked example, section read after a delay? The literature supports "something must be encoded first" but does not specify the threshold.
6. **Does Quiz Me cause retrieval-induced forgetting of items it doesn't cover?** Anderson, Bjork & Bjork 1994 predicts it can. No study of this in a deployed adaptive-tutor context.
7. **Does FSRS scheduling improve learning outcomes (not just review burden) in a controlled head-to-head against SM-2 or fixed-interval scheduling?** The Anki benchmark is simulation, not RCT. No published RCT comparing FSRS vs. SM-2 on learning outcomes exists at this writing `[verify]`.

The Quiz Me chapter is in good shape to be honest about each of these — every one is testable in the bandit data medhavy 1.5 is generating, and the chapter can promise the empirical answer rather than pretend the question is closed.

---

## 10. What this note is and isn't

This is a working pantry document. It is dense by intent — designed for quarrying into chapter prose, not for end-user reading. Effect sizes are reported with the comparisons they actually came from. Vendor claims are flagged as vendor claims. The retrieval-practice / spaced-repetition / scheduling-algorithm distinction is enforced throughout.

Two things to verify before any of this lands in published prose:

- The `[verify]` tags scattered through the citation list — specific edition / journal / page numbers I couldn't confirm in the time available.
- The version-specific claims about FSRS-4 / FSRS-5 / FSRS-6 — the algorithm is evolving and the chapter should cite the version that is current at the time of publication.

The chapter on Quiz Me will need to make one move this note has not made: it will need to choose, from the catalog above, the **one mechanism** to deep-dive on in Feynman style. The strong candidate is Bjork's storage-strength / retrieval-strength duality, because it is the conceptual scaffold that ties testing, spacing, FSRS, and gating into a single coherent picture. The supporting candidate is Cepeda et al. 2008's "optimal gap as a function of retention interval," which is the cleanest single quantitative result and the one a student can use to *think with* about scheduling. The chapter will be better if it picks one rather than gesturing at both.
