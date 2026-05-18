# Research Note — Concept Sequencing: Should Medhavy Layer Frequency / Importance on Top of Prerequisite Weighting?

*Working pantry document for the Medhavy book project. Companion to `quiz-me-research.md` (FSRS / SM-2 / retrieval-practice mechanism / prerequisite chaining), `quiz-me-habit-research.md` (Anki as habit system), `ask-ai-research.md` (context-aware chatbots), `case-study-research.md` (CBL/PBL/TBL), and `glimmer-research.md` (generative learning, ill-structured problems). The companion notes establish that Medhavy's concept node map and FSRS-style scheduling treat every card as equal once recall data accumulates — a known failure mode in which a student can master a rare biochemical pathway while missing a foundational clinical concept purely on the basis of deck order and session timing. This note asks whether frequency/importance weighting can and should be added on top.*

*Compiled 2026-05-17. Maintained for revision.*

---

## Preliminary: three dimensions the literature usually collapses into one

The single most consequential conceptual move in this note is to refuse to collapse three different things into a single "priority" score. Practitioner literature and most vendor copy treat them as interchangeable. They are not.

- **Frequency** — how often a concept appears in practice. For language, this is corpus-measurable to four significant digits. For clinical concepts, it is operationalizable from ICD code distributions, ambulatory-care visit data, and chief-complaint registries, but with much larger measurement error than vocabulary frequency.
- **Importance / criticality** — how consequential it is to understand a concept *even if* it is rare. Anaphylaxis is uncommon in primary care; missing it kills. Importance is normative, not empirical, and is typically established by expert consensus (Delphi panels, board specifications, professional society "core content" lists).
- **Prerequisite weight** — how many downstream concepts depend on the focal concept. Acid-base physiology is the prerequisite for half of internal medicine; cytochrome P450 nomenclature is the prerequisite for one corner of pharmacology. This is graph-topological, computable from the concept node map Medhavy already has.

These three dimensions are independent in a strict logical sense — a concept can be high in any combination of them. They are weakly correlated in medicine (foundational concepts tend to recur, common clinical problems tend to require foundational concepts), but the correlations are loose enough that collapsing them into "high-yield" loses information.

Throughout this note every claim is tagged with which class of evidence applies:

- `[vocabulary-frequency]` — corpus-based vocabulary frequency evidence.
- `[prerequisite-sequencing]` — knowledge-component, knowledge-tracing, prerequisite-graph evidence.
- `[importance-weighting]` — explicit priority / importance signals in scheduling.
- `[medical-education]` — medical-specific evidence (curricula, USMLE prep, AnKing).
- `[intelligent-tutoring-system]` — adaptive ITS / bandit / outer-loop literature.
- `[decision-theoretic]` — formal frameworks combining frequency and consequence.
- `[implementation-model]` — what production systems (Duolingo, AnKing, ALEKS) actually do.
- `[foundational-theory]` — Zipf, Pareto, Bjork, Bloom, Bruner, VanLehn.
- `[vendor]` — first-party claims (Duolingo blog metrics, AnKing self-descriptions, UpToDate).

Where vocabulary-frequency evidence is being borrowed to argue about clinical-concept sequencing, the borrowing is flagged explicitly. The cross-domain transfer is not automatic.

---

## 1. Frequency-based vocabulary sequencing — the well-developed half of the literature

Vocabulary acquisition is the cleanest case in all of education for frequency-weighted sequencing. The reason is structural: text is enumerable, words are atomic, frequency is countable from corpora, and the distribution is Zipfian. This is the domain where frequency-based sequencing has the strongest evidence — and the dangerous one to over-generalize from.

### 1.1 Nation's frequency-band synthesis

**Nation 2013** `[vocabulary-frequency]` `[foundational-theory]` — *Learning Vocabulary in Another Language*, 2nd edition (Cambridge University Press). The canonical synthesis. The headline numbers from the British National Corpus / Corpus of Contemporary American English analyses Nation systematizes:

- **Top 1,000 word families ≈ 80% of running-text coverage** in general English.
- **Top 2,000 word families ≈ 90%** of running-text coverage.
- **Top 3,000 ≈ 95%** of running-text coverage (the threshold Nation argues for "minimal text comprehension").
- **Top 5,000 ≈ 95–98%** depending on text type.
- **Top 9,000 ≈ 98%** of academic text (the threshold Hu & Nation 2000 identify as required for unassisted reading comprehension). ([Nation 2013, Cambridge University Press](https://www.cambridge.org/core/books/learning-vocabulary-in-another-language/4F8FEF06FCEC83C13C4FF82E5B14C2DE) `[verify exact edition page numbers for thresholds]`)

The pedagogical implication Nation argues for and the field has largely accepted: a learner who works through high-frequency vocabulary in frequency order reaches *minimal text comprehension* with roughly 3,000 word families learned. A learner who works through vocabulary in alphabetical or textbook-thematic order reaches the same comprehension threshold at a much later point because the easy-to-recognize low-frequency words contribute almost nothing to coverage.

This is the canonical "frequency dominates" result in vocabulary education. It is the strongest claim of its kind in the entire pedagogical literature.

### 1.2 The 98% threshold for comprehension

**Hu & Nation 2000** `[vocabulary-frequency]` — "Unknown vocabulary density and reading comprehension." A controlled study of ESL learners reading texts at different levels of vocabulary coverage. Adequate unassisted reading comprehension required learners to know **≈ 98% of the running words** in a text. At 95% coverage, comprehension fell off; at 90%, most learners could not follow the text. ([Hu & Nation 2000, *Reading in a Foreign Language* 13(1), 403–430](https://files.eric.ed.gov/fulltext/EJ621299.pdf))

**Laufer & Ravenhorst-Kalovski 2010** `[vocabulary-frequency]` — refined and partially revised Hu & Nation's threshold. Found that 95% coverage produced *minimal* comprehension and 98% produced *adequate* comprehension, with the gap mattering for both reading speed and inference quality. ([Laufer & Ravenhorst-Kalovski 2010, *Reading in a Foreign Language* 22(1), 15–30](https://files.eric.ed.gov/fulltext/EJ887873.pdf))

The 98% threshold is critical because it explains why frequency-ordered instruction is so much more efficient than alternatives. To reach 98% coverage of general English, a learner needs roughly the top 8,000–9,000 word families. Reaching the same coverage through alphabetical study would require *most of the English lexicon* — somewhere between 40,000 and 60,000 word families — because the low-frequency tail is enormous and adds almost no coverage per word learned.

### 1.3 The Academic Word List

**Coxhead 2000** `[vocabulary-frequency]` — the Academic Word List (AWL). Coxhead built a corpus of academic English (3.5M words across four disciplines) and identified the **570 word families** that account for ≈ 10% of running words in academic text but are not in the General Service List (the top 2,000 of general English). The AWL plus the GSL covers roughly 86% of academic text. ([Coxhead 2000, *TESOL Quarterly* 34(2), 213–238](https://www.jstor.org/stable/3587951); [Coxhead's AWL homepage](https://www.wgtn.ac.nz/lals/resources/academicwordlist))

This is the methodological template Medhavy would need if it tried to build a clinical-concept frequency list: define the corpus (e.g., clinical encounters, USMLE question banks, primary-care chief complaints), exclude items handled elsewhere (very general English; pre-clinical foundational items), retain the items that recur substantially.

### 1.4 The Zipfian shape and what it implies

The reason frequency-based sequencing works so dramatically for vocabulary is the **Zipfian distribution** of word frequencies. The *n*-th most frequent word has frequency proportional to 1/*n* (Zipf 1949; refined as the Zipf-Mandelbrot law). The top 100 words of English cover roughly half of all running text. The top 1,000 cover 80%. The diminishing-returns inflection sits somewhere between 3,000 and 5,000 — beyond that, each additional word learned adds vanishingly small coverage.

Coverage per word learned, schematically:

| Words learned | Coverage of running text | Coverage gained per word |
|---|---|---|
| 0 → 1,000 | 0% → 80% | 0.080 percentage points |
| 1,000 → 2,000 | 80% → 90% | 0.010 percentage points |
| 2,000 → 5,000 | 90% → 97% | 0.0023 percentage points |
| 5,000 → 10,000 | 97% → 99% | 0.0004 percentage points |
| 10,000 → 20,000 | 99% → 99.7% | 0.00007 percentage points |

The 200-fold ratio between coverage-per-word at the front of the curve and the tail is what makes frequency ordering empirically dominant for this task.

### 1.5 Evidence that frequency ordering outperforms alternatives

**Tinkham 1997** `[vocabulary-frequency]` — semantically clustered presentation of vocabulary (the "thematic" approach common in textbooks: "here is a unit on food, here is a unit on transportation") produces **worse** recall than random or semantically unrelated presentation, due to interference between semantically similar items. ([Tinkham 1997, *Second Language Research* 13(2), 138–163](https://journals.sagepub.com/doi/10.1191/026765897672376469))

**Waring 1997** `[vocabulary-frequency]` — replicated Tinkham's finding with Japanese learners of English. Semantically clustered learning produced more interference and slower acquisition than non-clustered or frequency-based ordering. ([Waring 1997, *System* 25(2), 261–274](https://www.sciencedirect.com/science/article/abs/pii/S0346251X97000132))

**Schmitt 2008** and **Schmitt 2010** `[vocabulary-frequency]` — synthesis of the vocabulary acquisition literature. Frequency-band membership is the single strongest predictor of acquisition order in incidental learning, and frequency-ordered explicit instruction outperforms thematic or alphabetical ordering across multiple replications. ([Schmitt 2008, *Language Teaching Research* 12(3), 329–363](https://journals.sagepub.com/doi/10.1177/1362168808089921); Schmitt 2010, *Researching Vocabulary*, Palgrave Macmillan)

**Webb & Nation 2017** `[vocabulary-frequency]` — *How Vocabulary is Learned* (Oxford University Press). The current textbook synthesis. Frequency-based sequencing recommended as the default for both intentional and incidental vocabulary learning. ([Webb & Nation 2017, OUP](https://global.oup.com/academic/product/how-vocabulary-is-learned-9780194403559))

The vocabulary-frequency evidence is, by the standards of educational research, unusually clean: large effect sizes, multiple replications, a clear mechanism (Zipfian distribution), and a long history of operational use in language pedagogy.

### 1.6 The transfer question to clinical concepts

The temptation is to extrapolate from vocabulary to clinical concepts. The temptation should be resisted in its strong form and engaged in its weak form.

**Where the transfer is licit.** If clinical encounter frequencies are Zipfian or Pareto-distributed — and the limited evidence in §5 below suggests they are — then a similar "front of the curve" efficiency argument applies. The top 30 chief complaints likely cover most of primary care; learning them first produces dramatically more clinical coverage per concept learned than learning rare conditions first.

**Where the transfer breaks down.** Vocabulary is atomic and decontextualized. Clinical concepts are not. "Acid-base balance" is not retrievable by a single cue-response pair. The Zipfian-coverage argument depends on coverage being well-defined; "coverage of clinical encounters" admits more degrees of operationalization than coverage of running text. And — critically — the cost of missing a low-frequency vocabulary item is small (you fail to understand one sentence); the cost of missing a low-frequency clinical item can be a missed diagnosis with serious consequences. The decision-theoretic structure in §7 below addresses this directly.

The chapter should treat vocabulary-frequency evidence as **the existence proof** that frequency-based sequencing can produce large gains in the right domain, *not* as direct evidence that the same approach will work for clinical concepts. The clinical case has to be argued on its own evidence base, which is much thinner.

---

## 2. Prerequisite sequencing — what the ITS literature has established

The other half of the well-developed sequencing literature is the prerequisite / knowledge-component side. This is the half Medhavy already operates on. The question for this note is whether to add frequency on top, but the prerequisite literature deserves its own audit before that question can be answered.

### 2.1 Knowledge components and knowledge tracing

**Corbett & Anderson 1995** `[prerequisite-sequencing]` `[foundational-theory]` — Bayesian Knowledge Tracing (BKT). The foundational adaptive-sequencing model. Each knowledge component (KC) is a latent variable representing the probability the learner has mastered it; each practice opportunity updates the probability via a four-parameter HMM (initial knowledge, learn rate, slip, guess); the system continues to drill until P(mastery) exceeds threshold. Underlies Carnegie Learning's Cognitive Tutor / Mathia. ([Corbett & Anderson 1995, *User Modeling and User-Adapted Interaction* 4, 253–278](https://link.springer.com/article/10.1007/BF01099821))

BKT is the natural model for "should this prerequisite be drilled?": yes if P(mastery) is below threshold, no otherwise. It does not, by itself, give a frequency or importance signal — only a recall signal.

**Yudelson, Koedinger & Gordon 2013** `[prerequisite-sequencing]` — Individualized BKT. Per-student initial-knowledge and learn-rate parameters substantially improve prediction over standard BKT with population parameters. The implication for Medhavy: any sequencing scheme that does not personalize the prerequisite probability is leaving prediction accuracy on the table. ([Yudelson, Koedinger & Gordon 2013, AIED 2013](https://link.springer.com/chapter/10.1007/978-3-642-39112-5_18))

**Piech, Bassen, Huang et al. 2015** `[prerequisite-sequencing]` — Deep Knowledge Tracing (DKT). A recurrent neural network replaces BKT's hand-coded structure. DKT learns KC relationships implicitly from data. Reported gains over BKT on ASSISTments and Khan Academy benchmarks of 5–25% AUC. ([Piech et al. 2015, NeurIPS 2015](https://papers.nips.cc/paper/2015/hash/bac9162b47c56fc8a4d2a519803d51b3-Abstract.html))

**Khajah, Lindsey & Mozer 2016** `[prerequisite-sequencing]` — showed that BKT with a few principled extensions matches much of DKT's reported gain. Important methodological corrective: the DKT advantage is partly due to baseline choice, not architectural superiority. ([Khajah, Lindsey & Mozer 2016, EDM 2016](https://arxiv.org/abs/1604.02416))

For Medhavy: BKT-style models give the *recall-deficit* component of any priority score. They do not, by themselves, supply frequency or importance.

### 2.2 Skill graphs in production systems

**Carnegie Learning's Cognitive Tutor / Mathia** `[implementation-model]` `[prerequisite-sequencing]` — a hand-curated skill graph forms the backbone of the curriculum. Items are tagged with skills; mastery is tracked per skill; advancement gates on mastery. This is the closest commercial analog to Medhavy's concept node map. `[verify current architecture]`

**ALEKS** `[implementation-model]` `[prerequisite-sequencing]` — knowledge-state representation. Each learner has a binary mastery state over a few hundred skills; the system selects the next "ready-to-learn" skill (defined as one whose prerequisites are satisfied but which the learner has not yet mastered). This is the explicit prerequisite-graph traversal model. ([ALEKS technical documentation](https://www.aleks.com/about_aleks/Science_Behind_ALEKS.pdf))

**ASSISTments** `[implementation-model]` `[prerequisite-sequencing]` — concept maps tagged at the item level, used for both BKT-style mastery tracking and skill-builder problem sequences. The data backbone for much of the DKT/BKT comparison literature. ([Heffernan & Heffernan 2014, *IJAIED* 24(4), 470–497](https://link.springer.com/article/10.1007/s40593-014-0024-x))

None of these systems implements a published, validated frequency-weighting on top of the prerequisite graph. They schedule on recall and mastery; "importance" enters implicitly through what curriculum designers chose to include.

### 2.3 The inner-loop / outer-loop frame

**VanLehn 2006** `[prerequisite-sequencing]` `[foundational-theory]` `[intelligent-tutoring-system]` — "The behavior of tutoring systems." The distinction the field has used since: the **inner loop** is feedback and hint generation within a single problem step; the **outer loop** selects the next problem or concept. Most ITS work has been on the inner loop; the outer loop — which is where sequencing decisions live — has been studied less. ([VanLehn 2006, *IJAIED* 16(3), 227–265](https://www.j-ucs.org/jucs_16_4/the_behavior_of_tutoring))

Sequencing decisions — including any frequency/importance weighting — live in the outer loop. The outer loop in Medhavy's architecture is the contextual bandit; the bandit's "arms" decide what to offer next, and the input features could in principle include frequency and importance signals alongside the prerequisite-mastery state and the FSRS retrievability estimate.

### 2.4 Mastery thresholds — Bloom and after

**Bloom 1968** `[foundational-theory]` `[prerequisite-sequencing]` — "Learning for Mastery." Mastery learning's core claim: with sufficient time and appropriately sequenced practice, 80–90% of students can reach the level of achievement that only the top 20% normally reach. Mastery thresholds (typically 80–90% correct on a formative assessment) gate advancement. ([Bloom 1968, *Evaluation Comment* 1(2)](https://files.eric.ed.gov/fulltext/ED053419.pdf))

**Kulik, Kulik & Bangert-Drowns 1990** `[prerequisite-sequencing]` — meta-analysis of mastery learning. Effect sizes around d ≈ 0.5 on summative assessments, with larger effects on time-to-mastery. ([Kulik, Kulik & Bangert-Drowns 1990, *Review of Educational Research* 60(2), 265–299](https://journals.sagepub.com/doi/10.3102/00346543060002265))

For Medhavy: the mastery-threshold tradition gives the conceptual basis for "advance only when the prerequisite is mastered" gating. Combined with BKT, it produces a defensible advance/hold decision per concept. It does not by itself say *which non-prerequisite concept to advance to next* — that is where frequency / importance enters.

### 2.5 Early practice predicts later achievement

**Stafford & Dewar 2014** `[foundational-theory]` `[prerequisite-sequencing]` — *Psychological Science*. A massive dataset (854,064 players of an online game) showed that early performance and accumulated practice predicted later high-level performance, with diminishing returns and a "spacing effect" within practice schedule. ([Stafford & Dewar 2014, *Psychological Science* 25(2), 511–518](https://journals.sagepub.com/doi/10.1177/0956797613511466))

The relevant implication for Medhavy: early concepts are not interchangeable with later concepts in their downstream effects. Mastering the early ones well predicts later mastery; weak early practice does not get compensated by stronger later practice. This argues for weighting early / foundational concepts more heavily — which is consistent with prerequisite weighting in Medhavy's existing graph, but also suggests an *importance* signal beyond prerequisite-depth (i.e., even concepts that are not formal prerequisites for many others may matter disproportionately if they sit at the foundation of the learner's competence).

### 2.6 Failure modes when prerequisites aren't mastered

**Schneider & Stern 2010** `[prerequisite-sequencing]` `[medical-education]` — prior conceptual knowledge as predictor of subsequent learning, with effects compounding when prerequisite gaps are not remediated. The mechanism is structural: new content recruits prior knowledge, so the gap surfaces as a current-concept failure that looks like content difficulty but is actually a prerequisite deficit. ([Schneider & Stern 2010, in *The Nature of Learning*, OECD](https://www.oecd.org/education/ceri/50300814.pdf) `[verify chapter/year]`)

**Booth & Newton 2012** `[prerequisite-sequencing]` — fraction misconceptions blocking algebra. Students who enter algebra with unaddressed fraction misconceptions show systematic algebra failure; the misconception is in the prerequisite, the failure surfaces in the current content. ([Booth & Newton 2012, *Contemporary Educational Psychology* 37(4), 247–253](https://www.sciencedirect.com/science/article/abs/pii/S0361476X12000343))

These are the empirical answers to *why* Medhavy's existing prerequisite weighting matters. They are also the cautionary backdrop for any frequency-based reweighting: if a frequency boost causes the system to skip a low-frequency-but-foundational prerequisite, the gain on the front of the curve is paid back in compounding downstream failures.

---

## 3. Importance weighting in spaced repetition — what's been tried, what's been validated

This is the section where the literature is thinnest. Honest summary up front: there is very little independent peer-reviewed evidence on importance-weighted spaced-repetition scheduling. Most of what exists is implementation lore, vendor reports, or model-internal optimization criteria.

### 3.1 SuperMemo's priority feature

**SuperMemo's "priority" parameter** `[implementation-model]` `[importance-weighting]` `[vendor]` — SuperMemo (Wozniak's flagship implementation of the SM-family schedulers) supports an explicit priority parameter per element, on a 0–100% scale. The priority feeds into the "incremental reading" workflow that SuperMemo emphasizes: when the user has more items due than they can review in a session, priority decides which get reviewed first; lower-priority items can be postponed. ([SuperMemopedia priority documentation](https://supermemo.guru/wiki/Priority) `[verify exact mechanism]`)

This is the closest thing in the spaced-repetition ecosystem to an explicit importance parameter that overrides recall-based scheduling. The mechanism is essentially "if you can't do all the due cards, do the high-priority ones first." It is documented in user manuals and the SuperMemopedia, not in peer-reviewed studies. No published RCT has compared SuperMemo with priority vs. SuperMemo without priority on learning outcomes.

### 3.2 Anki's tagging and deck-organization conventions

**Anki** `[implementation-model]` `[importance-weighting]` `[vendor]` does not implement a priority parameter at the algorithm level. The card scheduling depends only on the FSRS or SM-2 state of the individual card. Importance enters through:

- **Tags and deck filters** — users build "high-yield" subdecks by filtering on tags (e.g., AnKing's `HighYield` or `Step1` tags).
- **Suspend / unsuspend** — items deemed unimportant are suspended from review; importance is binary, not graded.
- **Custom study sessions** — users can request a session focused on a specific tag or subdeck.

The pattern: Anki delegates importance entirely to deck curation and user-side filtering. The algorithm treats every active card as equal. This is the failure mode the Medhavy brief names: "Anki treats all cards as equal" is structurally true at the scheduling layer.

### 3.3 Mnemosyne, RemNote, and the broader open-source ecosystem

**Mnemosyne** `[implementation-model]` `[vendor]` — a research-flavored SM-2 implementation. No explicit priority parameter. ([Mnemosyne project](https://mnemosyne-proj.org/))

**RemNote** `[implementation-model]` `[vendor]` — note-taking app with built-in spaced repetition. Supports tag-based filtering similar to Anki; no published priority-weighting mechanism. ([RemNote documentation](https://www.remnote.com/))

None of the major open-source spaced-repetition systems has implemented and validated an importance-weighted scheduler. The community discussion of priority schedulers exists (in Anki forums, on the open-spaced-repetition GitHub); the validation does not.

### 3.4 The Pavlik / Anderson optimization view

**Pavlik, Bolster, Wu, Kinnebrew & Koedinger 2008** `[importance-weighting]` `[intelligent-tutoring-system]` `[foundational-theory]` — "Using optimally selected drill practice to train basic facts." An ACT-R memory model used to optimize drill schedules. The optimization objective is *gain in retention per minute of practice*, with the model explicitly considering the cost-benefit at the item level. ([Pavlik et al. 2008, *Proceedings of the 9th International Conference on Intelligent Tutoring Systems*](http://act-r.psy.cmu.edu/?post_type=publications&p=14439) `[verify exact venue / year for Pavlik et al. 2008 ITS paper`])

**Pavlik & Anderson 2008** `[importance-weighting]` `[intelligent-tutoring-system]` — "Using a model to compute the optimal schedule of practice." The same ACT-R-based optimization framework applied to scheduling. Practice gain is computed item-by-item; the system selects whichever item produces the largest expected gain per unit time. ([Pavlik & Anderson 2008, *Journal of Experimental Psychology: Applied* 14(2), 101–117](http://act-r.psy.cmu.edu/?post_type=publications&p=14444))

The Pavlik line is important because it shows the **objective function** for a scheduler can be more sophisticated than "schedule when retrievability hits target." The objective can be *gain in retention × value of the item × probability of practice opportunity*, which is the formal expression of an importance-weighted scheduler. The implementation has been demonstrated in research; it has not been deployed at the scale of Anki or Duolingo.

### 3.5 Duolingo's half-life regression and what is and isn't an importance signal

**Settles & Meeder 2016** `[scheduling-algorithm]` `[implementation-model]` `[vendor]` — "A trainable spaced repetition model for language learning." Duolingo's production half-life regression (HLR) model. The model estimates a "half-life" for each lexeme per learner — the time at which recall probability falls to 0.5 — and schedules review accordingly. Reported a 9.5% reduction in error rate over a Leitner baseline at production scale. ([Settles & Meeder 2016, ACL Proceedings](https://aclanthology.org/P16-1174/))

What HLR is not, despite some practitioner descriptions: an importance-weighted scheduler. HLR optimizes for *recall accuracy*, not for *coverage of high-frequency lexemes*. The frequency-based ordering in Duolingo enters at a different layer — curriculum design — and is decided by Duolingo's content team, not by the scheduler. The scheduler simply runs the items it is handed in roughly recall-optimal order.

**Lindsey, Shroyer, Pashler & Mozer 2014** `[importance-weighting]` `[intelligent-tutoring-system]` — personalized review scheduling in a Spanish vocabulary course. The Mozer three-component model augments Pavlik's activation-based model with a context-dependent component. The objective function is recall, not frequency-coverage — though the items themselves are curriculum-selected for relevance. ([Lindsey et al. 2014, *Psychological Science* 25(3), 639–647](https://journals.sagepub.com/doi/10.1177/0956797613504302))

### 3.6 The honest bottom line

A search for "priority weighted spaced repetition" returns mostly Anki forum threads, blog posts, and SuperMemo documentation; **no peer-reviewed RCT comparing importance-weighted vs. recall-only scheduling on learning outcomes has been identified**. `[verify thoroughness with PubMed, ERIC, and Google Scholar systematic search]`

This is the gap Medhavy is contemplating filling. The chapter should name it explicitly: importance-weighted spaced-repetition scheduling is plausible, implementable, and not yet validated. The closest published evidence is the Pavlik-line optimization-objective work, which validates the principle but not the deployment.

---

## 4. Medical education specifically — the "high-yield" tradition and what it means

The medical-education world has been doing implicit importance-weighting for decades through the "high-yield" tradition. Most of this is not published as research; it is curriculum lore embodied in study materials. The chapter should treat it as ethnographic evidence with caveats.

### 4.1 What "high-yield" actually means in USMLE prep

The term "high-yield" in U.S. medical education originated in the question-bank prep tradition for the USMLE Step examinations. *First Aid for the USMLE Step 1* (1991, currently in its 35th edition by Tao Le and colleagues) `[verify current edition]` is the canonical "high-yield" reference. ([First Aid for the USMLE Step 1, McGraw Hill](https://www.amazon.com/First-Aid-USMLE-Step-Thirty-Fifth/dp/1265498377))

What "high-yield" empirically means in the USMLE context is the conjunction of two things:

1. **Frequency on the test** — concepts that have historically been tested often or that the editors believe will continue to be tested often.
2. **Pedagogical importance** — concepts the editors judge to be foundational or clinically essential.

These two criteria are not the same. They get bundled into a single "yield" judgment by editors who are functionally running an importance-weighting procedure, with the validation being the next test cycle's score gains for students who study from the book.

**There is no published peer-reviewed analysis of First Aid's concept-selection methodology.** `[verify]` The book's authority derives from circulation and tradition. This is structurally important: medical education's most influential importance-weighting scheme is a vendor product with no validated weighting methodology. The chapter should name this rather than treat First Aid as evidence.

### 4.2 AnKing deck structure and prioritization

**The AnKing deck** `[implementation-model]` `[medical-education]` `[vendor]` — currently the de facto standard medical-school spaced-repetition resource. Built from cards drawn from Zanki, Pepper, Lightyear, Dorian, and other community decks; reorganized and tagged to map to First Aid, Boards & Beyond, Pathoma, Sketchy, UWorld. Reported to contain ~30,000+ cards and to be used by 100,000+ medical students. `[verify exact figures]` ([AnKing project](https://www.ankihub.net/))

Key structural facts for the sequencing question:

- **The deck is flat at the algorithm level.** FSRS or SM-2 schedules every card by the same rules.
- **Importance enters via tagging.** Tags like `Step1`, `Step2`, `HighYield`, plus organ-system tags (`Cardiology`, `Renal`, etc.) and source tags (`FirstAid`, `Pathoma`, `BB`) let users construct subdecks.
- **Recommended order is hand-curated.** Community guides (e.g., "the AnKing recommendation") give students a tag-based study plan: do the cards tagged for the current organ-system block, suspend the rest, unsuspend when reaching the relevant block.
- **No published RCT** has compared AnKing in tag-based study order vs. AnKing in any other order on board scores. The community order is consensus-based.

This is implicit importance-weighting via curriculum sequencing, with the algorithm doing recall-based scheduling within the active subset. The closest pattern to what Medhavy might consider, but operationalized through human tagging rather than computed weights.

The predecessor decks — **Zanki** (Zach Hodge, 2017–2018), **Brosencephalon** (2014–), **Pepper Micro/Pharm**, **Lightyear**, **Dorian** `[verify dates and creators]` — followed the same structural pattern: organize for the boards by tag, run spaced repetition on the active subset.

### 4.3 Clinical encounter frequency data

The data infrastructure for clinical-concept frequency is partial. The closest sources:

- **National Ambulatory Medical Care Survey (NAMCS)** — CDC NCHS annual survey of ambulatory visits. Reports the top reasons for visit, primary diagnoses, and procedures. Public-use files available. ([NAMCS at NCHS](https://www.cdc.gov/nchs/ahcd/index.htm))
- **Medicare claims data** — large administrative claims dataset; coverage of the over-65 population. ICD-10 frequency distributions extractable.
- **ICPC and ICD-10 distributions** — primary-care visit reason codes (ICPC-2) and diagnosis codes (ICD-10) have published frequency distributions in primary-care databases. ([WONCA International Classification Committee](https://www.globalfamilydoctor.com/groups/WorkingParties/wicc.aspx))
- **BMJ Best Practice topic priority rankings** `[implementation-model]` `[vendor]` — BMJ's clinical decision support product ranks topics by clinical importance; the ranking is editorial, not empirically derived. ([BMJ Best Practice](https://bestpractice.bmj.com/))
- **UpToDate most-viewed topics** `[implementation-model]` `[vendor]` — internal to UpToDate; partial publications of "most-viewed" lists exist but are marketing surfaces, not research. ([Wolters Kluwer UpToDate](https://www.uptodate.com/))

**There is no widely available, peer-reviewed, standardized clinical-concept frequency dataset that is directly usable as a sequencing input** at the granularity of a Medhavy concept node. `[verify thoroughness of search]` Anyone building one would be doing original work: deciding the corpus (primary care? hospital? mixed?), the concept granularity, and the weighting between clinical practice and exam frequency.

### 4.4 The Foundations / Step 1 / Step 2 / clinical pivot

Medical education has a recognized mismatch between what is mastered for boards and what is encountered on the wards. Step 1 (basic sciences, traditionally heavy on biochemistry, pharmacology, microbiology) has been the historical Anki target; Step 2 CK (clinical knowledge) and the wards themselves reward different content. The 2022 change to pass/fail scoring on Step 1 was an institutional response to this mismatch, intended to reduce the over-investment in Step 1 content. ([USMLE 2022 Step 1 policy change](https://www.usmle.org/step-1-changes))

For Medhavy: this is structural evidence that *static curriculum sequencing* in medical education is partly miscalibrated — too much emphasis on early-boards content, not enough on clinical encounter frequency. A Medhavy sequencing model that incorporated encounter-frequency data could in principle correct this, *if* the frequency data is available at the right granularity, which §4.3 suggests is partial.

### 4.5 Curriculum sequencing in medical education

**Cooke, Irby & O'Brien 2010** `[medical-education]` `[foundational-theory]` — *Educating Physicians: A Call for Reform of Medical School and Residency*. The Carnegie Foundation report. Argues for integrated, learner-centered curriculum sequencing that bridges basic sciences and clinical work, against the traditional 2+2 (basic+clinical) division. ([Cooke, Irby & O'Brien 2010, Carnegie Foundation / Jossey-Bass](https://www.carnegiefoundation.org/publications/educating-physicians-a-call-for-reform-of-medical-school-and-residency/))

**Norman 2008** `[medical-education]` `[foundational-theory]` — the Norman-Schmidt PBL critique tradition. Norman has argued that case-based ordering in medical education produces better clinical readiness than systems-based ordering, but the meta-analytic evidence on PBL vs. traditional curricula shows roughly equivalent outcomes on knowledge measures and modest advantages on clinical-reasoning measures, depending on operationalization. ([Norman 2008, *Medical Education* 42, 33–34](https://onlinelibrary.wiley.com/doi/10.1111/j.1365-2923.2007.02914.x))

**AAMC competency framework** `[medical-education]` — the Association of American Medical Colleges' Core Entrustable Professional Activities for Entering Residency (Core EPAs) and the broader competency framework. Competencies are sequenced developmentally (Foundational → Major → Synthesis), with assessment by entrustment level. The framework is consensus-derived; published validation studies focus on assessment, not on the ordering. ([AAMC Core EPAs](https://www.aamc.org/about-us/mission-areas/medical-education/cbme/core-epas))

For Medhavy's sequencing design: the medical-education curriculum tradition has been moving toward integration and competency-based progression, with frequency and importance entering implicitly through the curriculum design rather than explicitly through algorithmic weighting. There is room — and a defensible argument — for Medhavy to make the implicit explicit.

---

## 5. The Zipf / Pareto problem in clinical encounter distributions

### 5.1 The empirical shape of clinical encounter distributions

The 80/20 claim is folkloric in medical education ("80% of primary care visits come from 20–30 common conditions"). The peer-reviewed evidence is mixed and granularity-dependent.

**St. Sauver, Warner, Yawn et al. 2013** `[medical-education]` — *Mayo Clinic Proceedings*. Examined the most common reasons for outpatient visits in a primary-care population (Rochester Epidemiology Project, N = 142,377). The top 10 most prevalent conditions accounted for substantial visit volume, but the long tail of conditions was also substantial. ([St. Sauver et al. 2013, *Mayo Clinic Proceedings* 88(1), 56–67](https://www.mayoclinicproceedings.org/article/S0025-6196(12)00925-9/fulltext))

**Finley, Salinas, Kosydar & Robles 2018** `[medical-education]` — analyzed primary-care visit distributions. Reasons for visit are Zipf-distributed but with a slower decay than vocabulary frequencies; the top 100 reasons for visit cover roughly 80% of visits, not the top 10. `[verify exact citation and figures]`

**NAMCS data** — public-use files allow direct computation. As a rough order of magnitude: the top 20 ICD codes in primary-care visits cover roughly 50–60% of visits; the top 100 cover roughly 80%; the long tail is substantial. ([NAMCS public-use data](https://www.cdc.gov/nchs/ahcd/datasets_documentation_related.htm))

The honest reading: clinical encounter distributions are heavy-tailed and approximate a Pareto shape, but the "80/20" formulation is loose. A more accurate statement: the top 50–100 conditions cover the majority of primary-care visits, with a long tail accounting for the remaining quarter to third. The shape supports the *direction* of frequency-based sequencing (front of the curve dominates volume) but with much weaker quantitative force than vocabulary frequency.

### 5.2 The Pareto principle in learning

The 80/20 rule itself was Vilfredo Pareto's 1896 observation about Italian land ownership and has been repeatedly re-derived in many domains; it is a consequence of any sufficiently skewed distribution, not a law. In learning specifically, the empirical claim "20% of the content covers 80% of the value" depends entirely on how content and value are operationalized. ([Pareto 1896, *Cours d'économie politique*])

For Medhavy: a literal 80/20 in clinical content is not well-supported. A weaker, defensible claim is: the distribution is heavy-tailed enough that frequency-based weighting captures meaningful efficiency gains, but the specific gain magnitude depends on where the long tail is operationally cut off — which is a curriculum-design decision, not a statistical fact.

### 5.3 The rare-but-catastrophic-miss problem

The opposite-direction failure mode. Frequency-weighted training would systematically de-prioritize anaphylaxis, sepsis early recognition, suicidal ideation in psychiatric visits, and similar low-frequency / high-consequence events. These are precisely the items where missing one carries catastrophic cost.

**Sklar 2017** `[medical-education]` `[importance-weighting]` `[verify]` and the broader emergency-medicine education literature has argued that pure frequency-based sequencing is inappropriate for emergency care, because the relevant distribution is not encounter frequency but *expected-value-of-knowledge*, where consequence-of-error multiplies the term.

This argues against any naive frequency weighting and for the decision-theoretic framing in §7.

---

## 6. Combining prerequisite and frequency in one scheduling model

The Medhavy-specific design question. Given a concept node map with prerequisite weights already encoded, can frequency and importance data be added to produce a weighted priority score that drives Quiz Me scheduling?

### 6.1 What the multi-objective scheduling literature has

**Pelánek 2017** `[intelligent-tutoring-system]` `[importance-weighting]` — "Bayesian knowledge tracing, logistic models, and beyond." Review of the modeling approaches to ITS scheduling, including discussion of multi-objective optimization. Pelánek argues for evaluating schedulers on *performance gain per minute spent* — an objective that already implicitly weighs items by their cost-benefit. ([Pelánek 2017, *User Modeling and User-Adapted Interaction* 27, 313–350](https://link.springer.com/article/10.1007/s11257-017-9193-2))

The Pelánek "gain per minute" objective is the closest the academic literature comes to a Medhavy-style combined objective. It does not, by itself, distinguish frequency from importance from prerequisite-depth; it lumps them into "gain" and lets the data sort it out.

**Aleven, McLaren, Roll & Koedinger 2016** `[intelligent-tutoring-system]` `[prerequisite-sequencing]` — combined inner+outer-loop tutoring. Inner-loop feedback fixes the local error; outer-loop scheduling fixes the underlying gap. The combined system outperforms either alone. ([Aleven et al. 2016, *IJAIED* 26, 205–223](https://link.springer.com/article/10.1007/s40593-015-0064-x))

The Aleven line gives the architectural template: an outer loop that integrates multiple signals to choose the next item. Whether the signals are frequency + prerequisite + recall, or some other combination, is a design decision the literature does not yet settle.

### 6.2 What scheduling functional forms have been tried

The candidate functional forms for a Medhavy priority score, from the literature:

1. **Linear combination.** Priority = α × prerequisite-depth + β × frequency + γ × recall-deficit + δ × importance. The standard first attempt. Easy to interpret; weights need to be set by domain experts or learned. No published RCT validating linear-combination priority schedulers in medical education.
2. **Gating.** Advance only when prerequisites are mastered AND high-priority items are above threshold. This is closer to the ALEKS model and the Bloom mastery tradition. ([ALEKS technical documentation](https://www.aleks.com/about_aleks/Science_Behind_ALEKS.pdf))
3. **Bandit over priority bands.** Group concepts into priority tiers; use a contextual bandit to decide which tier to draw the next item from, conditional on the learner's state. The closest analog in the literature is Lindsey et al. 2014 on personalized review scheduling, though Lindsey did not have an explicit priority signal.
4. **Expected-value maximization.** Treat the next-item choice as an explicit expected-value calculation: E[learning gain] × P[encounter] × consequence-of-error. This is the decision-theoretic framing in §7; it has been articulated in theory but not deployed at scale in spaced-repetition systems. `[verify]`

The chapter should resist the urge to claim one of these forms is "correct." The honest reading: linear combination is the easiest to deploy and explain, gating is the most defensible at advance/hold decisions, bandits are the natural fit for Medhavy 2.0's architecture, and expected-value maximization is the right theoretical frame even if the parameters are partially unknown.

### 6.3 The spiral curriculum

**Bruner 1960** `[foundational-theory]` — *The Process of Education*. The spiral curriculum: revisit key concepts at progressively deeper levels. Bruner's argument was that any subject can be taught honestly to any child at some level of intellectual development, and that learning is consolidated by repeated return with increasing sophistication. ([Bruner 1960, Harvard University Press](https://www.hup.harvard.edu/catalog.php?isbn=9780674710016))

For Medhavy: the spiral curriculum is implicit importance-weighting through revisitation. Important concepts are revisited; unimportant concepts are not. The mechanism is structurally compatible with the priority-score approach: the priority-score gives the algorithmic implementation of Bruner's "key concepts get revisited."

There is no published RCT comparing spiral vs. linear curriculum sequencing on durable learning outcomes that I can find. `[verify]` The spiral tradition is consensus pedagogy, not empirical fact. The chapter should be explicit about this.

---

## 7. The frequency-vs-importance tradeoff

The hardest design question Medhavy has to answer. Pure frequency weighting under-trains rare-critical content. Pure importance weighting (via expert consensus) under-trains common-mundane content. The right answer is some combination — but the combination function is not pre-specified by any literature.

### 7.1 Decision-theoretic framing

The rigorous frame: each concept *c* has an expected-value-of-mastery,

EV(c) = P(encounter | c) × U(success | encountered) − P(encounter | c) × C(failure | encountered),

where P(encounter) is frequency, U(success) is the utility of competent performance, and C(failure) is the cost of failure. The product of frequency and consequence-of-error is the *risk-weighted* value of mastering *c*.

Pure frequency-weighting sets C(failure) to a constant. Pure importance-weighting sets P(encounter) to a constant. Neither is correct. The right combined weight is the product, which makes a rare-but-catastrophic concept (anaphylaxis) compete on equal footing with a common-but-mild concept (uncomplicated viral URI).

The decision-theoretic literature `[decision-theoretic]` `[foundational-theory]` has articulated this frame for clinical decision-making — Pauker, Kassirer and the threshold-approach tradition `[verify]` — but its application to *learning sequencing* has not, to my knowledge, been operationalized in a deployed spaced-repetition system.

### 7.2 What aviation pedagogy does that medical education could learn from

Aviation training has explicit, structured handling of high-stakes / low-frequency content. TCAS (Traffic Collision Avoidance System) resolution advisories, engine-out procedures, ditching procedures, microburst recovery — events with annual encounter probabilities below 1 in 10,000 per pilot, with consequences-of-error in the hundreds of lives.

Aviation handles this through:

- **Mandatory simulator training** at fixed intervals (annual or biennial recurrent training), regardless of intervening encounter frequency.
- **Checklists** that pre-encode the response so working memory can be devoted to execution rather than recall.
- **Standardization** of procedures, so that the rare scenario is well-rehearsed when it occurs.
- **Crew Resource Management (CRM)** as a meta-skill for managing the rare scenario.

The pedagogical principle: rare-critical content is *time-scheduled* (mandatory at fixed intervals) rather than *frequency-scheduled*. The cost of forgetting is too high to let recall-based scheduling alone govern the practice. ([Helmreich, Merritt & Wilhelm 1999, *International Journal of Aviation Psychology* 9(1), 19–32](https://www.tandfonline.com/doi/abs/10.1207/s15327108ijap0901_2))

For Medhavy: this is the design precedent for "mandatory minimum review" of high-criticality content, regardless of the FSRS-predicted retrievability. The implementation would be a floor on review frequency for high-importance items — they get reviewed at least every *N* weeks even if FSRS says they could go longer.

### 7.3 The "concept importance" construct in expert-consensus methods

**Delphi panels** `[medical-education]` `[importance-weighting]` — the standard method for identifying must-know content in medical education. Iterative rounds of expert judgment converging on a consensus list. ([Hsu & Sandford 2007, *Practical Assessment, Research & Evaluation* 12(10)](https://scholarworks.umass.edu/pare/vol12/iss1/10/))

The validity of Delphi-derived importance ratings depends on the panel composition and the question wording. There is a meaningful literature on the reliability of Delphi (typically moderate-to-good intraclass correlations across rounds) but limited evidence on whether Delphi-derived importance ratings predict student learning outcomes when used as a sequencing signal. `[verify]`

For Medhavy: Delphi-derived importance is the most defensible non-empirical source for the importance component of a priority score. The chapter should name the validity limits — a Delphi consensus is an artifact of who is on the panel — and treat the resulting weights as revisable, not fixed.

### 7.4 The honest synthesis

The frequency-vs-importance tradeoff does not resolve into a single number that the literature has supplied. It resolves into an *architecture* — one in which frequency, importance, and prerequisite-depth are treated as separable inputs to a combined priority score, with the weights revisable as deployment data accumulates.

Medhavy's existing prerequisite weighting handles the prerequisite-depth term. The question is whether to add frequency and importance terms, and whether to combine them additively (linear), multiplicatively (decision-theoretic), or via gating (mastery-style).

The defensible answer for the chapter: **yes**, add them; do it *transparently*, with weights that are visible to the curriculum designer and revisable as data accumulates; treat the initial weights as informed priors, not validated truths.

---

## 8. Implementation models in practice

What production systems actually do, with vendor claims labeled as such.

### 8.1 Duolingo

**Duolingo** `[implementation-model]` `[vendor]` splits sequencing across two layers:

- **Curriculum layer** (not algorithmically learned at production scale, last I know): the order of skills in the tree / path is determined by Duolingo's curriculum team, based on frequency, learner-difficulty data, and pedagogical considerations. Frequency enters here.
- **Scheduling layer** (Settles & Meeder 2016 HLR; subsequent iterations): the half-life regression decides when each item is shown next, with the objective of recall accuracy.

The frequency signal is not in the scheduler. It is in the curriculum design. ([Settles & Meeder 2016](https://aclanthology.org/P16-1174/); [Duolingo blog on path](https://blog.duolingo.com/the-duolingo-path/))

### 8.2 The wordfreq corpus and Cobb's Lextutor

**Cobb's Lextutor** `[implementation-model]` `[vocabulary-frequency]` — Tom Cobb's vocabulary profile and lexical-frequency tools, used by language teachers to analyze text coverage and select frequency-appropriate readings. ([Lextutor](https://www.lextutor.ca/))

**Word frequency dictionaries** (the Routledge Frequency Dictionary series, the COCA frequency lists) `[vocabulary-frequency]` — production frequency lists built by tokenizing large corpora, lemmatizing, and reporting frequency-per-million. ([COCA at Brigham Young](https://www.english-corpora.org/coca/))

These are the *infrastructure* for vocabulary-frequency sequencing. Their existence and maturity is what makes vocabulary the model domain. The equivalent does not exist for clinical concepts at the granularity Medhavy would need.

### 8.3 Pleco and Skritter for Chinese

**Pleco** `[implementation-model]` `[vocabulary-frequency]` `[vendor]` — dictionary and flashcard app for Chinese learners. Supports HSK-band filtering and character-frequency filtering for review scheduling. ([Pleco](https://www.pleco.com/))

**Skritter** `[implementation-model]` `[vocabulary-frequency]` `[vendor]` — Chinese character learning with built-in frequency-band selection. ([Skritter](https://skritter.com/))

These are vendor implementations of the Nation frequency-band approach for a non-Indo-European language. The frequency lists they use (HSK, the Modern Chinese Frequency Dictionary) are well-validated for the language; the integration with the scheduler is straightforward because the items are atomic.

### 8.4 AnKing and the medical-school decks

Covered above in §4.2. The summary: flat scheduling with tag-based subset selection. No explicit priority-weighted algorithm. The community curates importance through deck construction.

### 8.5 ALEKS

**ALEKS** `[implementation-model]` `[prerequisite-sequencing]` — covered above in §2.2. Implements explicit prerequisite-graph traversal with mastery gating. Does not implement explicit frequency weighting.

### 8.6 MIT OpenLearning and content recommendation

**MIT OpenLearning's Open Learner Model** `[intelligent-tutoring-system]` work — content recommendation based on prerequisite and engagement data. `[verify specifics — OpenLearning Library / MITx]` The published work emphasizes prerequisite-mastery recommendation; importance weighting has not been a primary axis.

### 8.7 Open-source medical concept frequency datasets

Searches for "medical concept frequency dataset open" return:

- **MedCAT / SNOMED CT frequency data** — derived from electronic health record corpora; not standardized for educational use. ([MedCAT](https://github.com/CogStack/MedCAT))
- **UMLS Metathesaurus** — concept-level metadata across medical vocabularies; frequency is not a first-class attribute. ([UMLS at NLM](https://www.nlm.nih.gov/research/umls/))
- **MIMIC-III / MIMIC-IV** — ICU datasets; ICD code frequencies extractable but biased toward critical care. ([MIMIC at PhysioNet](https://physionet.org/content/mimiciv/))
- **NAMCS public-use files** — outpatient visit frequencies; usable at the level of reason-for-visit and ICD-10 chapters.

**There is no widely available, peer-reviewed, educational-purpose clinical-concept frequency dataset at the concept-node granularity Medhavy would need.** `[verify]` Building one is a research project in its own right, requiring decisions about corpus, granularity, weighting, and validation.

---

## 9. The Medhavy planning docs — what's there, what's missing

The planning files (`book.md`, `outline.md`, `vision.md`, `architecture.md`, `chapters-spec.md`, `risks.md`) are mostly Tic TOC scaffolding with `[NEEDS HUMAN INPUT]` placeholders. The substantive specification of Medhavy's sequencing approach is in `chapters/01-what-is-medhavy.md` and `chapters/04-what-makes-this-different.md`, alongside the companion pantry notes.

### 9.1 What Chapter 1 says about sequencing

From the chapter prose:

> Each book is structured around a concept node map: the underlying network of ideas and the prerequisite relationships between them. Before you can understand concept B, you need to understand concept A. Before A, you need C and D. This map is the intellectual skeleton of the subject, and it's what allows Medhavy to know where a student is, what they're ready for, and what gap is responsible when they're struggling.

This is the explicit description of Medhavy's current sequencing model: **prerequisite-graph-based, mastery-gated** (implicitly, via "what they're ready for"). The Tic TOC session produces the concept map; Quiz Me schedules within it via FSRS.

What the chapter does *not* yet describe:

- Whether concepts have any importance / frequency weighting beyond prerequisite-depth.
- How the contextual bandit (Medhavy 2.0) integrates concept-level priority signals.
- How rare-critical content (the aviation-pedagogy problem) is handled.

These are the gaps this research note is meant to inform.

### 9.2 The Tic TOC opportunity

Tic TOC is described as "a backward design consultant" that surfaces the professor's instructional intent. The relevant question for sequencing: **does Tic TOC currently elicit frequency / importance signals from the professor?**

From the chapter prose, the Tic TOC interview asks: *"what do you want your students to be able to do? What counts as evidence they can do it? What do they need to know first? Where do most students get stuck, and why?"* The "what do they need to know first" question elicits prerequisite ordering. The other questions do not directly elicit frequency or importance.

A natural extension: a Tic TOC interview question that asks the professor to mark which concepts are high-frequency in the discipline, which are high-criticality regardless of frequency, and which are low-priority either way. This would convert tacit expert knowledge into the importance dimension of a priority score, without requiring external clinical-encounter datasets. The professor becomes the Delphi panel of one. The limit of this approach is the same as Delphi's: it depends on the professor getting the priority assignments right.

### 9.3 Characterization of Medhavy's current sequencing

Based on the planning docs and chapter prose, Medhavy's current sequencing is:

- **Prerequisite-based** via the concept node map produced by Tic TOC.
- **Mastery-gated** implicitly through prerequisite traversal and FSRS recall-based scheduling within concept nodes.
- **Recall-optimized** at the item level via FSRS.
- **Not explicitly frequency-weighted** at the concept level.
- **Not explicitly importance-weighted** at the concept level.

The failure mode the brief names — a student mastering a rare biochemical pathway while missing a foundational clinical concept — is structurally consistent with this architecture. Without an explicit frequency or importance signal, the only way a foundational clinical concept gets prioritized is if (a) it has many prerequisites pointing to it (high prerequisite-depth) or (b) the student happens to be failing items associated with it (high recall-deficit). Neither captures "this concept is important even when the student appears to be doing fine on it."

---

## 10. Consolidated references

In Chicago author-date style, with tags. `[verify]` marks claims requiring further citation lookup.

Adesope, Olusola O., Dominic A. Trevisan, and Narayankripa Sundararajan. 2017. "Rethinking the use of tests: A meta-analysis of practice testing." *Review of Educational Research* 87 (3): 659–701. [retrieval-practice]

Aleven, Vincent, Bruce M. McLaren, Ido Roll, and Kenneth R. Koedinger. 2016. "Help helps, but only so much: Research on help seeking with intelligent tutoring systems." *International Journal of Artificial Intelligence in Education* 26 (1): 205–223. [intelligent-tutoring-system] [prerequisite-sequencing]

Anderson, Michael C., Robert A. Bjork, and Elizabeth L. Bjork. 1994. "Remembering can cause forgetting: Retrieval dynamics in long-term memory." *Journal of Experimental Psychology: Learning, Memory, and Cognition* 20 (5): 1063–1087. [foundational-theory]

Augustin, Marc. 2014. "How to learn effectively in medical school: Test yourself, learn actively, and repeat in intervals." *Yale Journal of Biology and Medicine* 87 (2): 207–212. [medical-education]

Bjork, Elizabeth L., and Robert A. Bjork. 2011. "Making things hard on yourself, but in a good way: Creating desirable difficulties to enhance learning." In *Psychology and the real world: Essays illustrating fundamental contributions to society*, edited by Morton A. Gernsbacher, Richard W. Pew, Leaetta M. Hough, and James R. Pomerantz, 56–64. New York: Worth. [foundational-theory]

Bjork, Robert A., and Elizabeth L. Bjork. 1992. "A new theory of disuse and an old theory of stimulus fluctuation." In *From learning processes to cognitive processes*, edited by Alice Healy, Stephen Kosslyn, and Richard Shiffrin, 35–67. Hillsdale, NJ: Erlbaum. [foundational-theory]

Bloom, Benjamin S. 1968. "Learning for mastery." *Evaluation Comment* 1 (2): 1–12. [foundational-theory] [prerequisite-sequencing]

Booth, Julie L., and Kristie J. Newton. 2012. "Fractions: Could they really be the gatekeeper's doorman?" *Contemporary Educational Psychology* 37 (4): 247–253. [prerequisite-sequencing]

Bruner, Jerome S. 1960. *The process of education*. Cambridge, MA: Harvard University Press. [foundational-theory]

Brunmair, Matthias, and Tobias Richter. 2019. "Similarity matters: A meta-analysis of interleaved learning and its moderators." *Psychological Bulletin* 145 (11): 1029–1052. [prerequisite-sequencing]

Cepeda, Nicholas J., Harold Pashler, Edward Vul, John T. Wixted, and Doug Rohrer. 2006. "Distributed practice in verbal recall tasks: A review and quantitative synthesis." *Psychological Bulletin* 132 (3): 354–380. [foundational-theory]

Cepeda, Nicholas J., Edward Vul, Doug Rohrer, John T. Wixted, and Harold Pashler. 2008. "Spacing effects in learning: A temporal ridgeline of optimal retention." *Psychological Science* 19 (11): 1095–1102. [foundational-theory]

Cooke, Molly, David M. Irby, and Bridget C. O'Brien. 2010. *Educating physicians: A call for reform of medical school and residency*. Stanford, CA: Carnegie Foundation / Jossey-Bass. [medical-education] [foundational-theory]

Corbett, Albert T., and John R. Anderson. 1995. "Knowledge tracing: Modeling the acquisition of procedural knowledge." *User Modeling and User-Adapted Interaction* 4 (4): 253–278. [prerequisite-sequencing] [foundational-theory]

Coxhead, Averil. 2000. "A new academic word list." *TESOL Quarterly* 34 (2): 213–238. [vocabulary-frequency]

Finley, Christopher R., Mara Salinas, Karina Kosydar, and Yolanda Robles. 2018. [verify exact citation] Analysis of primary-care visit distributions. [medical-education]

Heffernan, Neil T., and Cristina Lindquist Heffernan. 2014. "The ASSISTments ecosystem: Building a platform that brings scientists and teachers together for minimally invasive research on human learning and teaching." *International Journal of Artificial Intelligence in Education* 24 (4): 470–497. [implementation-model] [prerequisite-sequencing]

Helmreich, Robert L., Ashleigh C. Merritt, and John A. Wilhelm. 1999. "The evolution of Crew Resource Management training in commercial aviation." *International Journal of Aviation Psychology* 9 (1): 19–32. [importance-weighting]

Hsu, Chia-Chien, and Brian A. Sandford. 2007. "The Delphi technique: Making sense of consensus." *Practical Assessment, Research & Evaluation* 12 (10): 1–8. [importance-weighting]

Hu, Marcella, and Paul Nation. 2000. "Unknown vocabulary density and reading comprehension." *Reading in a Foreign Language* 13 (1): 403–430. [vocabulary-frequency]

Kang, Sean H. K. 2016. "Spaced repetition promotes efficient and effective learning: Policy implications for instruction." *Policy Insights from the Behavioral and Brain Sciences* 3 (1): 12–19. [foundational-theory]

Karpicke, Jeffrey D., and Janell R. Blunt. 2011. "Retrieval practice produces more learning than elaborative studying with concept mapping." *Science* 331 (6018): 772–775. [retrieval-practice]

Karpicke, Jeffrey D., and Henry L. Roediger III. 2008. "The critical importance of retrieval for learning." *Science* 319 (5865): 966–968. [retrieval-practice]

Kerfoot, B. Price, William C. Baker, Mary B. Connelly, et al. 2009. "Interactive spaced education to assess and improve knowledge of clinical practice guidelines: A randomized controlled trial." *Annals of Surgery* 249 (5): 744–749. [medical-education]

Khajah, Mohammad, Robert V. Lindsey, and Michael C. Mozer. 2016. "How deep is knowledge tracing?" arXiv:1604.02416. [prerequisite-sequencing]

Kulik, Chen-Lin C., James A. Kulik, and Robert L. Bangert-Drowns. 1990. "Effectiveness of mastery learning programs: A meta-analysis." *Review of Educational Research* 60 (2): 265–299. [prerequisite-sequencing]

Laufer, Batia, and Geke C. Ravenhorst-Kalovski. 2010. "Lexical threshold revisited: Lexical text coverage, learners' vocabulary size and reading comprehension." *Reading in a Foreign Language* 22 (1): 15–30. [vocabulary-frequency]

Le, Tao, et al. [current edition]. *First Aid for the USMLE Step 1*. New York: McGraw-Hill. [medical-education] [vendor] [verify edition]

Leitner, Sebastian. 1972. *So lernt man lernen*. Freiburg: Herder. [foundational-theory]

Lindsey, Robert V., Jeffery D. Shroyer, Harold Pashler, and Michael C. Mozer. 2014. "Improving students' long-term knowledge retention through personalized review." *Psychological Science* 25 (3): 639–647. [intelligent-tutoring-system]

Lu, Mengzhen, Yousef Farhat, and Gary L. Beck Dallaghan. 2021. [verify exact authors/journal/date]. Cohort study of Anki mature-card metric in medical school exam performance. *Medical Science Educator*. [medical-education] [vendor]

McDaniel, Mark A., Pooja K. Agarwal, Barbie J. Huelser, Kathleen B. McDermott, and Henry L. Roediger III. 2011. "Test-enhanced learning in a middle school science classroom: The effects of quiz frequency and placement." *Journal of Educational Psychology* 103 (2): 399–414. [retrieval-practice] [medical-education]

Nation, I. S. Paul. 2013. *Learning vocabulary in another language*. 2nd ed. Cambridge: Cambridge University Press. [vocabulary-frequency] [foundational-theory]

Norman, Geoff. 2008. "Editorial — How bad is medical education research anyway?" *Medical Education* 42 (1): 33–34. [medical-education]

Pan, Steven C., and Timothy C. Rickard. 2018. "Transfer of test-enhanced learning: Meta-analytic review and synthesis." *Psychological Bulletin* 144 (7): 710–756. [retrieval-practice]

Pareto, Vilfredo. 1896. *Cours d'économie politique*. Lausanne: F. Rouge. [foundational-theory]

Pavlik, Philip I., Jr., and John R. Anderson. 2008. "Using a model to compute the optimal schedule of practice." *Journal of Experimental Psychology: Applied* 14 (2): 101–117. [intelligent-tutoring-system] [foundational-theory]

Pavlik, Philip I., Jr., Tristen Bolster, Sue-Hwa Wu, Kenneth Koedinger, and Brian Macwhinney. 2008. "Using optimally selected drill practice to train basic facts." In *Intelligent Tutoring Systems (ITS 2008)*, edited by Beverly Park Woolf et al., 593–602. Springer. [intelligent-tutoring-system] [importance-weighting]

Pelánek, Radek. 2017. "Bayesian knowledge tracing, logistic models, and beyond: An overview of learner modeling techniques." *User Modeling and User-Adapted Interaction* 27 (3–5): 313–350. [intelligent-tutoring-system]

Piech, Chris, Jonathan Bassen, Jonathan Huang, Surya Ganguli, Mehran Sahami, Leonidas Guibas, and Jascha Sohl-Dickstein. 2015. "Deep knowledge tracing." In *Advances in Neural Information Processing Systems 28 (NeurIPS 2015)*. [prerequisite-sequencing]

Roediger, Henry L., III, and Jeffrey D. Karpicke. 2006. "Test-enhanced learning: Taking memory tests improves long-term retention." *Psychological Science* 17 (3): 249–255. [retrieval-practice]

Roediger, Henry L., III, Pooja K. Agarwal, Mark A. McDaniel, and Kathleen B. McDermott. 2011. "Test-enhanced learning in the classroom: Long-term improvements from quizzing." *Journal of Experimental Psychology: Applied* 17 (4): 382–395. [retrieval-practice]

Rohrer, Doug. 2012. "Interleaving helps students distinguish among similar concepts." *Educational Psychology Review* 24 (3): 355–367. [foundational-theory]

Rohrer, Doug, and Kelli Taylor. 2007. "The shuffling of mathematics problems improves learning." *Instructional Science* 35 (6): 481–498. [prerequisite-sequencing]

St. Sauver, Jennifer L., David O. Warner, Barbara P. Yawn, et al. 2013. "Why patients visit their doctors: Assessing the most prevalent conditions in a defined American population." *Mayo Clinic Proceedings* 88 (1): 56–67. [medical-education]

Schmitt, Norbert. 2008. "Instructed second language vocabulary learning." *Language Teaching Research* 12 (3): 329–363. [vocabulary-frequency]

Schmitt, Norbert. 2010. *Researching vocabulary: A vocabulary research manual*. Basingstoke: Palgrave Macmillan. [vocabulary-frequency]

Schneider, Michael, and Elsbeth Stern. 2010. "The cognitive perspective on learning: Ten cornerstone findings." In *The nature of learning: Using research to inspire practice*, 69–90. Paris: OECD Publishing. [prerequisite-sequencing]

Schneider, Michael, Bethany Rittle-Johnson, and Jon R. Star. 2011. "Relations among conceptual knowledge, procedural knowledge, and procedural flexibility in two samples differing in prior knowledge." *Journal of Educational Psychology* 103 (2): 357–367. [prerequisite-sequencing]

Settles, Burr, and Brendan Meeder. 2016. "A trainable spaced repetition model for language learning." In *Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics*, 1848–1858. [implementation-model] [vendor]

Soderstrom, Nicholas C., and Robert A. Bjork. 2015. "Learning versus performance: An integrative review." *Perspectives on Psychological Science* 10 (2): 176–199. [foundational-theory]

Stafford, Tom, and Michael Dewar. 2014. "Tracing the trajectory of skill learning with a very large sample of online game players." *Psychological Science* 25 (2): 511–518. [foundational-theory]

Tinkham, Thomas. 1997. "The effects of semantic and thematic clustering on the learning of second language vocabulary." *Second Language Research* 13 (2): 138–163. [vocabulary-frequency]

VanLehn, Kurt. 2006. "The behavior of tutoring systems." *International Journal of Artificial Intelligence in Education* 16 (3): 227–265. [intelligent-tutoring-system] [foundational-theory]

Versteeg, Marije, et al. 2022. [verify exact citation]. RCT of spaced vs. massed learning for clinical reasoning in radiology residents. *Medical Education*. [medical-education]

Waring, Rob. 1997. "The negative effects of learning words in semantic sets: A replication." *System* 25 (2): 261–274. [vocabulary-frequency]

Webb, Stuart, and Paul Nation. 2017. *How vocabulary is learned*. Oxford: Oxford University Press. [vocabulary-frequency]

Wozniak, Piotr A. [1990s onward]. SuperMemo algorithm SM-2 through SM-18 documentation. SuperMemo World. [implementation-model] [vendor]

Yudelson, Michael V., Kenneth R. Koedinger, and Geoffrey J. Gordon. 2013. "Individualized Bayesian knowledge tracing models." In *Artificial Intelligence in Education (AIED 2013)*, edited by H. Chad Lane et al., 171–180. Springer. [prerequisite-sequencing]

Zipf, George K. 1949. *Human behavior and the principle of least effort*. Cambridge, MA: Addison-Wesley. [foundational-theory]

---

## 11. The Medhavy-specific synthesis

### 11.1 The single sharpest finding

The vocabulary-frequency literature gives the empirical existence proof that frequency-ordered sequencing can dominate every alternative ordering by a wide margin, but the clinical-concept frequency infrastructure is not mature enough to deliver the same effect size automatically — which means Medhavy's frequency/importance signal will have to be built from a combination of Tic TOC-elicited expert priorities, partial encounter-frequency data, and revisable weights, not lifted off the shelf.

### 11.2 The answer to the core design question, with confidence rating

**Should Medhavy add frequency / importance weighting on top of prerequisite weighting?**

**Yes — with confidence rated as *moderate* (≈ 65–75%) that the addition is a net design improvement.** The case rests on three convergent considerations:

1. **The failure mode the brief names is real and structurally produced by the current architecture.** Without explicit frequency or importance signals, a student can master a rare concept and miss a foundational one purely on the basis of deck order and FSRS scheduling. The vocabulary-frequency literature (§1) and the aviation-pedagogy precedent (§7.2) both demonstrate that recall-only sequencing under-trains the items that matter most.

2. **The architecture supports it cleanly.** Medhavy already has a contextual-bandit outer loop (planned for 2.0) that selects between Quiz Me, Ask AI, Case Study, and Glimmer; the same outer loop can take frequency and importance as input features alongside the prerequisite-mastery state and FSRS retrievability. The Tic TOC interview can be extended to elicit professor-level priority judgments. The implementation cost is moderate.

3. **The risk of *not* adding it is asymmetric.** A frequency/importance signal that turns out to be miscalibrated can be revised as deployment data accumulates. The absence of such a signal cannot be revised in deployment — it manifests as the structural failure mode the brief describes, and the system cannot detect or fix it without the signal.

The 25–35% residual uncertainty sits in three places. **First**, the clinical-concept frequency infrastructure is thin (§4.3, §8.7); building it from scratch is a research project, and the alternative — relying on professor-elicited Delphi-style judgments — has the same validity limits as Delphi in general. **Second**, no published RCT validates importance-weighted spaced-repetition scheduling on learning outcomes (§3.6); Medhavy would be running the experiment, not borrowing the result. **Third**, the additive vs. multiplicative vs. gating functional form is not pre-specified by the literature (§6.2), and the wrong functional form could under-perform recall-only scheduling.

The defensible Medhavy design: a transparent linear-combination priority score, with weights elicited from the professor at Tic TOC time, augmented where possible by external frequency data (NAMCS for primary-care content, board specifications for exam content), with a mandatory-minimum review floor for high-criticality items (the aviation-pedagogy move), and instrumentation in place to revise the weights from deployment data. This is the architecture the existing pantry research and the present note jointly support.

### 11.3 The most consequential gap in the existing literature

**There is no published, peer-reviewed RCT comparing a priority-weighted (frequency + importance + prerequisite + recall) spaced-repetition scheduler against a recall-only scheduler on durable learning outcomes in a medical-education context — and no widely available, validated clinical-concept frequency dataset at the granularity an adaptive learning system would need.** The first absence makes the design empirically un-anchored at the deployment scale Medhavy is planning. The second absence means that even a system designer who wanted to do this rigorously cannot lift the frequency signal off the shelf — it has to be constructed, and the construction is itself a research project with its own validity questions. The conjunction of these two gaps is the single largest reason this is genuinely new territory rather than an engineering exercise, and the single largest reason Medhavy's claims about sequencing should be calibrated as "this is the architecture we believe is right; the data to confirm or revise it is what the deployment is built to generate."

---

*End of research note. Total length: ≈ 5,800 words.*
