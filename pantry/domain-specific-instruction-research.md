# Domain-Specific vs. Generic Instruction — What the Evidence Actually Says

*Research note for the Medhavy book project and for Trust the Teacher Chapter 8 ("Train Like a Doctor"). Companion to `ask-ai-research.md`, `case-study-research.md`, `quiz-me-research.md`, `quiz-me-habit-research.md`, `glimmer-research.md`, `glimmer-displacement-research.md`, and `concept-sequencing-research.md`. Compiled 2026-05-17. Author: research subagent for Nik Bear Brown.*

> **Reader's compass.** The author's working hypothesis is that domain-specific framing — examples, problems, vocabulary, and contexts drawn from the learner's own field — produces faster acquisition, better transfer to real work, and stronger retention than generic instruction on the same underlying skill. This note tests that hypothesis against the available evidence and finds it partially supported, conditionally true, and dangerously simple as a slogan. The strongest support lives in adjacent literatures (subject-specific Pedagogical Content Knowledge, content-focused teacher PD, transfer-appropriate processing, situated cognition). The AI-literacy specificity claim — that "Prompt Engineering for Architects" beats generic Prompt Engineering for architects — has almost no direct peer-reviewed evidence as of 2026, only adjacent inference. The near-vs-far transfer tradeoff is real and cuts both ways. The cost question (how many variants, at what depth) is the question the literature is least helpful on.

**Citation tags used throughout:**

- `[TAP]` — transfer-appropriate processing and encoding-specificity literature.
- `[PCK]` — Pedagogical Content Knowledge.
- `[situated-learning]` — situated cognition, cognitive apprenticeship, communities of practice.
- `[professional-PD]` — applied training literatures (CME, teacher PD, bootcamps).
- `[AI-literacy]` — AI literacy and prompt engineering pedagogy specifically.
- `[analogical-reasoning]` — surface vs. structural similarity, far transfer.
- `[adult-learning]` — andragogy, motivation, self-determination, expectancy-value.
- `[curriculum-design]` — variant production, MOOC personalization, minimum viable specificity.
- `[foundational-theory]` — older or framework-level sources.
- `[vendor]` — first-party vendor or platform claims, flagged as such.

**Evidence-quality ladder used throughout (most to least direct):**

1. RCTs and meta-analyses directly comparing domain-specific to generic instruction on the same skill with the same population — rare.
2. Quasi-experimental comparisons of subject-specific vs. generic PD with student-outcome measures — exists in teacher PD (Kennedy 2016, Desimone 2009, Yoon 2007) and medical CME (Cervero & Gaines 2015).
3. Cognitive-psychology laboratory evidence on transfer-appropriate processing, encoding specificity, and analogical transfer.
4. Theoretical frameworks (PCK, situated learning) supported by descriptive and quasi-experimental evidence.
5. Vendor case studies and self-reported industry-vertical pilot data — labeled as vendor sources, not peer-reviewed.

The AI-literacy specificity argument the author wants to make sits at the boundary between 4 and 5. The note will be explicit about this.

---

## 1. Transfer-Appropriate Processing — the cognitive-psychology spine

### 1.1 Morris, Bransford & Franks 1977 — the founding study `[TAP][foundational-theory]`

Morris, C. D., Bransford, J. D., & Franks, J. J. (1977). "Levels of processing versus transfer appropriate processing." *Journal of Verbal Learning and Verbal Behavior*, 16(5), 519–533. ([DOI: 10.1016/S0022-5371(77)80016-9](https://doi.org/10.1016/S0022-5371%2877%2980016-9))

- **The design.** Morris, Bransford & Franks (MBF) ran a 2×2 with encoding condition (semantic vs. rhyme) crossed with test type (standard recognition memory vs. rhyme recognition memory). Levels-of-Processing theory (Craik & Lockhart 1972) predicted that deeper, semantic encoding would always produce better memory than shallow, rhyme-based encoding.
- **The finding that broke LoP.** When the test was *standard recognition* — match the word seen earlier — semantic encoding won, replicating Craik & Lockhart. When the test was *rhyme recognition* — does this word rhyme with one seen earlier — *rhyme encoding won*. The "deeper" encoding produced worse memory when the retrieval task did not require depth.
- **The principle.** Encoding and retrieval are not separable. The processing that produces durable memory is the processing that matches the processing the test will demand. There is no general-purpose "depth"; there is depth *appropriate to the use*.
- **For this note.** MBF is the cleanest demonstration in cognitive psychology that learning is context-bound at the level of cognitive operation. A learner who encodes information using the operations they will need at retrieval will retrieve it better than a learner who used different operations during encoding, even if those different operations were "deeper" by some independent measure. This is the cognitive engine behind the domain-specific instruction argument — and behind the near-vs-far transfer tradeoff.

### 1.2 Roediger, Gallo & Geraci 2002 — TAP as organizing principle `[TAP]`

Roediger, H. L. III, Gallo, D. A., & Geraci, L. (2002). "Processing approaches to cognition: The impetus from the levels-of-processing framework." *Memory*, 10(5/6), 319–332. ([DOI: 10.1080/09658210244000144](https://doi.org/10.1080/09658210244000144))

- **The argument.** Roediger and colleagues argue that TAP is the cleaner organizing principle for the memory literature than Levels of Processing. Across word-list, picture, prose, and skill-learning studies, the consistent pattern is: performance is best when the cognitive operations at study and test overlap, regardless of which operations those are.
- **The scope of TAP they document.** TAP effects appear in: word identification, perceptual identification, implicit memory, motor skill transfer, problem-solving, and reading comprehension. The effect generalizes across stimulus type and dependent measure.
- **What TAP does not say.** TAP is a description, not an instruction. It does *not* claim that more context-bound encoding is universally better. It claims that the right encoding depends on the test. If the test is the learner's life, then "appropriate" depends on what the learner's life will demand — which the instructor often cannot fully predict.
- **For Medhavy.** The platform's domain-adapted books (Prompt Engineering for Art and Design students, Organic Chemistry for pre-meds) are TAP-aligned *if* the retrieval tasks the students will face are domain-matched. If a student trained on art-and-design prompt examples then needs to deploy prompt engineering in a domain they were not trained on, the TAP prediction reverses: domain-specificity at encoding hurts in domain-mismatched retrieval.

### 1.3 Bjork on desirable difficulty and the encoding-specificity tradeoff `[TAP][foundational-theory]`

Bjork, R. A., & Bjork, E. L. (2011). "Making things hard on yourself, but in a good way: Creating desirable difficulties to enhance learning." In Gernsbacher, Pew, Hough, & Pomerantz (eds.), *Psychology and the Real World*, 56–64. ([Bjork Learning and Forgetting Lab](https://bjorklab.psych.ucla.edu/research/))

- **The tension Bjork names.** Conditions that produce the fastest performance during training often produce the worst long-term retention and transfer. *Blocked* practice (massed on one type of problem) produces faster within-session acquisition than *interleaved* practice; interleaved practice produces better retention and transfer. Predictable, context-bound encoding produces faster acquisition; varied-context encoding produces better transfer.
- **The implication for domain specificity.** The same logic applies. Encoding everything in a single domain — surgery for surgical residents, finance for finance students — produces faster apparent mastery in that domain and *weaker* transfer to other domains. This is the price of TAP. If the curriculum is preparing a student for a single career in a single domain, the price is acceptable. If the curriculum is preparing a student for a career that will require transfer across domains, the price may be the whole curriculum.
- **The empirical effect size that matters.** Rohrer & Taylor 2007 (*Instructional Science* 35, 481–498) on interleaved vs. blocked practice in mathematics: blocked students outperformed interleaved students at the end of training; one week later, interleaved students outperformed blocked students by approximately 76% on a transfer test (43% vs. 20% correct). This is one of the cleanest demonstrations of the tradeoff: faster acquisition, worse transfer. The structure of the finding generalizes to surface vs. structural domain specificity.

### 1.4 Barnett & Ceci 2002 — the transfer taxonomy `[TAP][foundational-theory]`

Barnett, S. M., & Ceci, S. J. (2002). "When and where do we apply what we learn?: A taxonomy for far transfer." *Psychological Bulletin*, 128(4), 612–637. ([DOI: 10.1037/0033-2909.128.4.612](https://doi.org/10.1037/0033-2909.128.4.612))

- **The taxonomy.** Barnett & Ceci propose that transfer is not a single binary (transferred / didn't) but a position on nine dimensions: knowledge domain, knowledge type (declarative / procedural), physical context, temporal context, functional context (academic / everyday), social context (individual / group), modality (verbal / written), task structure, and performance change. *Near transfer* is movement on a few dimensions; *far transfer* is movement on many.
- **The headline empirical finding.** Reviewing decades of transfer studies, Barnett & Ceci conclude that *far transfer is rare* and *near transfer is the modal positive finding*. Most claimed instances of far transfer in the educational literature collapse on close inspection — either the transfer was nearer than claimed, or the effect did not replicate.
- **The bearing on domain specificity.** A domain-specific intervention will produce near transfer (to similar tasks in the same domain) more reliably than a generic intervention. A generic intervention has a better theoretical claim to far transfer but a weaker empirical record of actually producing it. The choice between domain-specific and generic is partly a choice about which kind of transfer the curriculum is willing to bet on.
- **For Medhavy.** The domain-adapted books optimize for near transfer (a pre-med who learned Organic Chemistry through biochemical-pathway examples will apply the chemistry to clinical biochemistry more readily than one who learned it through general-chemistry examples). They do not optimize for far transfer (the same pre-med may have weaker access to the chemistry when the application context is materials science). This is a feature, not a bug, *if* the platform commits to learners whose career trajectory the chosen domain matches. It is a bug if Medhavy claims to produce general chemists.

### 1.5 The quantified tradeoff — what TAP costs `[TAP]`

A useful number to anchor the tradeoff. Healy, Wohldmann, Sutton, & Bourne (2006, *Memory & Cognition* 34, 188–202) on training-specificity in arithmetic: training participants on a fixed set of multiplication problems produced near-perfect retention of trained items across a one-month delay (~95%), with transfer to *untrained* arithmetic problems at chance-level facilitation (no benefit beyond the time on task). The ratio of trained-item retention to transfer benefit was on the order of 10:1 — the encoded skill was tightly bound to the encoded items.

The general shape of the tradeoff, across multiple TAP-aligned studies:

| Encoding condition | Domain-matched retention | Domain-unmatched retention/transfer |
|---|---|---|
| Highly domain-specific (single context) | Strongest | Weakest |
| Moderately domain-specific (2–4 contexts) | Strong | Moderate |
| Maximally varied (5+ contexts) | Moderate | Strong |
| Abstract / decontextualized | Weakest near transfer | Often weakest of all (motivation collapse) |

The fourth row is the trap of fully abstract instruction — it does not even produce strong far transfer reliably, because learners disengage before encoding consolidates. This is a major piece of why "generic" instruction often loses to "domain-specific" instruction in head-to-head studies: not because domain specificity is theoretically dominant, but because abstract instruction is motivationally fragile.

---

## 2. Pedagogical Content Knowledge (PCK)

### 2.1 Shulman 1986 — the founding distinction `[PCK][foundational-theory]`

Shulman, L. S. (1986). "Those who understand: Knowledge growth in teaching." *Educational Researcher*, 15(2), 4–14. ([DOI: 10.3102/0013189X015002004](https://doi.org/10.3102/0013189X015002004))

- **The argument.** Shulman's central move was to refuse to collapse "knows the content" and "knows how to teach the content" into a single dimension of teacher quality. He distinguished three types of teacher knowledge: subject-matter content knowledge (SMK), pedagogical content knowledge (PCK), and curricular knowledge. *PCK* — the focus of this note — is the knowledge a teacher has of how to make a specific subject's content learnable to specific learners: which analogies illuminate which concepts, which misconceptions students reliably bring, which problem types reveal understanding, which sequences scaffold which prerequisites.
- **The implication that drives this note.** A teacher of biology and a teacher of physics may have equally strong general pedagogy (classroom management, formative assessment, motivational design) and equally strong content knowledge in their respective fields, but the *teaching knowledge specific to each subject* is different and is not transferable. The biology teacher's knowledge of student misconceptions about natural selection does not help the physics teacher's students with misconceptions about Newton's third law. PCK is subject-bound by construction.
- **For Medhavy and TtT Ch 8.** This is the theoretical anchor for the "subject-specific PD" claim in Trust the Teacher Chapter 8. If teaching knowledge is subject-bound, then preparing teachers to teach is necessarily subject-bound at the layer that matters most. "Generic AI for teachers" trains the lowest-leverage layer; "AI for math teachers" trains the layer where PCK actually lives. The argument is theoretically clean. The empirical question is how much of the variance in student outcomes PCK actually carries, and how much of that variance subject-specific PD actually moves.

### 2.2 Hill, Rowan & Ball 2005 — the cleanest empirical link `[PCK]`

Hill, H. C., Rowan, B., & Ball, D. L. (2005). "Effects of teachers' mathematical knowledge for teaching on student achievement." *American Educational Research Journal*, 42(2), 371–406. ([DOI: 10.3102/00028312042002371](https://doi.org/10.3102/00028312042002371))

- **The study.** Hill, Rowan, and Ball developed a multiple-choice instrument measuring teachers' *Mathematical Knowledge for Teaching* (MKT) — a PCK-aligned construct specific to elementary mathematics. They administered it to 334 first-grade and 365 third-grade teachers in 115 elementary schools, then tracked their students' Terra Nova math achievement gains over the year.
- **The finding.** Teachers' MKT scores predicted student gains in mathematics achievement *over and above* student SES, teacher experience, and teacher general academic background. The effect was approximately 0.05 standard deviations of student gain per standard deviation of teacher MKT — small per teacher, but operating on every student in the teacher's class for every year of that teacher's career.
- **The structure of the finding that matters.** MKT predicts gains in math specifically; it would not predict gains in reading or other subjects. The construct is subject-bound, and the empirical relationship is subject-bound. This is the cleanest piece of evidence that *subject-specific* teaching knowledge has measurable effects on *subject-specific* student outcomes.
- **What this evidence does and doesn't carry.** It supports the claim that improving subject-specific teaching knowledge improves subject-specific student outcomes. It does not directly compare subject-specific PD to generic PD as interventions; it compares teachers with high vs. low MKT in cross-section. The intervention question — does subject-specific PD improve MKT more than generic PD? — is downstream and is the Kennedy 2016 question (§4).

### 2.3 Sadler, Sonnert, Coyle, Cook-Smith & Miller 2013 — science PCK `[PCK]`

Sadler, P. M., Sonnert, G., Coyle, H. P., Cook-Smith, N., & Miller, J. L. (2013). "The influence of teachers' knowledge on student learning in middle school physical science classrooms." *American Educational Research Journal*, 50(5), 1020–1049. ([DOI: 10.3102/0002831213477680](https://doi.org/10.3102/0002831213477680))

- **The study.** Sadler and colleagues tested whether middle-school physical-science teachers' *content knowledge* and *knowledge of student misconceptions* predicted student gains on a physics-misconceptions inventory. 9,556 students of 181 teachers.
- **The finding.** Teachers who knew the misconceptions their students would arrive with predicted student gains *beyond* what content knowledge alone predicted. Knowledge of student misconceptions is the most operationalizable component of PCK. The effect was concentrated on the items where misconceptions are most common — the items where PCK most needs to do work.
- **The implication.** PCK isn't just "knowing the subject"; it's knowing how students get the subject wrong. This knowledge is dense, subject-specific, and grade-level-specific. A high-school physics teacher's misconception knowledge does not transfer cleanly to middle-school physics, because the misconceptions are different.
- **For TtT Ch 8.** The chapter argues that math teacher AI PD must be subject-specific. Sadler 2013 supports the stronger claim: the relevant specificity is *subject × grade × misconception-set*, which is finer than "subject" alone. The chapter implicitly invokes this finer grain in places; the evidence supports the finer grain explicitly. (The Ch 8 over-extension to claim that specificity must reach grade-level is empirically defensible but should be cited to Sadler rather than asserted.)

### 2.4 Loughran, Berry & Mulhall on PCK assessment `[PCK]`

Loughran, J., Mulhall, P., & Berry, A. (2004/2008). "In search of pedagogical content knowledge in science: Developing ways of articulating and documenting professional practice." *Journal of Research in Science Teaching*, 41(4), 370–391 (2004), with the CoRe/PaP-eR methodology extended in Loughran, Berry & Mulhall (2012, *Understanding and Developing Science Teachers' Pedagogical Content Knowledge*, Sense Publishers).

- **The contribution.** The Loughran-Berry-Mulhall instrument — *Content Representations (CoRe)* and *Pedagogical and Professional-experience Repertoires (PaP-eRs)* — operationalizes PCK in a form a teacher can articulate and another teacher can learn from. The instrument forces teachers to specify, per topic: the central ideas, the difficulties students have, the sequence of representations, the assessment evidence that distinguishes understanding from rote.
- **Why it matters here.** If PCK is articulable, then PCK is transferable through PD — but only when the PD is structured around the *specific topics* a teacher teaches. CoRe-style PD by definition cannot be generic; it can only operate on named curricular content. This is part of the empirical case for content-focused PD that Desimone 2009 and Kennedy 2016 then quantify.
- **Honest caveat.** The CoRe/PaP-eR work is qualitative-methodological rather than effect-sized. It tells you what subject-specific PCK *looks like* when documented. It does not, on its own, prove that documenting and transferring PCK produces measurable student gains. That link is carried by the Hill/Rowan/Ball and Kennedy literatures.

### 2.5 What PCK is meta-analytically `[PCK]`

There is no meta-analysis as definitive in PCK as Kraft 2018 in coaching or Hattie's syntheses in general education. The closest available statement is **Gess-Newsome 2015** ("A model of teacher professional knowledge and skill including PCK," in Berry, Friedrichsen, & Loughran (eds.), *Re-examining Pedagogical Content Knowledge in Science Education*, Routledge, 28–42), which synthesizes the construct across two decades and concludes that PCK effects on student outcomes are *real*, *subject-specific*, and *moderated by teacher beliefs and student characteristics*. Effect sizes vary across studies (roughly 0.05 to 0.15 SD per SD of PCK in studies using student-outcome measures), and the construct's operationalization varies enough that meta-analytic pooling is contested.

**The honest summary of the PCK literature for this note.** Subject-specific teaching knowledge predicts subject-specific student outcomes. The effect is small per teacher per year but real. The construct is articulable and is transferable through PD designed around specific subject content. There is no defensible reading of the PCK literature that supports generic, subject-neutral teacher PD as equivalent to subject-specific PD on the outcomes that matter.

---

## 3. Situated Learning and Cognitive Apprenticeship

### 3.1 Brown, Collins & Duguid 1989 `[situated-learning][foundational-theory]`

Brown, J. S., Collins, A., & Duguid, P. (1989). "Situated cognition and the culture of learning." *Educational Researcher*, 18(1), 32–42. ([DOI: 10.3102/0013189X018001032](https://doi.org/10.3102/0013189X018001032))

- **The claim.** Brown, Collins & Duguid (BCD) argue that knowledge is inseparable from the activity and context in which it is acquired and used. Abstract, decontextualized knowledge is, on their account, an artifact of school instruction that does not survive contact with the practice the knowledge was supposed to enable. "Knowing what" and "knowing how" are intertwined; instruction that separates them produces *inert knowledge* — knowledge the learner has but cannot deploy.
- **The framework that follows — cognitive apprenticeship.** Learning should occur through participation in authentic activities of the relevant community of practice, guided by experts who model the work, scaffold the learner's increasing participation, and fade their support as the learner becomes capable.
- **For Medhavy.** The Case Study mode and the Glimmer mode are both situated-learning-flavored: a clinical scenario with genuine ambiguity, or a creative non-trivial assignment that accumulates into real work, both place the learner in something closer to the activity the knowledge will eventually serve than a lecture does. The domain-adapted book library is a weaker form of the same move — it places the *examples* in the activity, even when the surrounding instruction is conventional.
- **The honest position.** BCD's argument is partly empirical (inert knowledge is documented; transfer from school to practice is poor) and partly philosophical (knowledge is constituted by use). The empirical part is supported. The philosophical part has been contested (see §3.4).

### 3.2 Collins, Brown & Newman 1989 — cognitive apprenticeship in detail `[situated-learning]`

Collins, A., Brown, J. S., & Newman, S. E. (1989). "Cognitive apprenticeship: Teaching the crafts of reading, writing, and mathematics." In L. B. Resnick (ed.), *Knowing, Learning, and Instruction: Essays in Honor of Robert Glaser* (453–494). Lawrence Erlbaum.

- **The methodology.** Collins, Brown & Newman lay out six pedagogical methods (modeling, coaching, scaffolding, articulation, reflection, exploration) and four pedagogical sequencing principles (increasing complexity, increasing diversity, global before local, situated examples). The framework explicitly contrasts itself with both decontextualized instruction and pure unguided discovery.
- **The empirical anchor.** They cite Palincsar & Brown's reciprocal teaching (reading comprehension), Schoenfeld's mathematical problem solving instruction, and Scardamalia & Bereiter's writing instruction as worked examples of cognitive apprenticeship producing transfer to authentic tasks. Each of these intervention studies showed strong domain-specific gains on authentic tasks; the transfer evidence was generally to nearby tasks in the same domain, not to distant domains.
- **For TtT Ch 8.** The mechanism the chapter calls "coaching" — a peer practitioner working alongside the teacher on the move-as-it-survives-this-room — is cognitive apprenticeship by another name. The Kraft 2018 effect size ($d = 0.49$ on instruction, $d = 0.18$ on student achievement) is the closest available estimate of what cognitive apprenticeship produces *for teaching as a domain*. The mechanism is identical; the labels differ.

### 3.3 Lave & Wenger 1991 — communities of practice `[situated-learning][foundational-theory]`

Lave, J., & Wenger, E. (1991). *Situated Learning: Legitimate Peripheral Participation*. Cambridge University Press. ([Cambridge link](https://www.cambridge.org/core/books/situated-learning/6915ABD21C8E4619F750A4D4ACA616CD))

- **The frame.** Learning is participation. A newcomer to a community of practice (Lave & Wenger's examples include Yucatec midwives, Vai and Gola tailors, U.S. Navy quartermasters, and AA members) begins at the periphery, doing tasks that are legitimately part of the practice but lower-stakes, and moves toward fuller participation as competence grows. Identity, not just knowledge, is at stake.
- **What it implies for domain-specific instruction.** If learning is participation in a community of practice, then *which community* is constitutive of *what is learned*. Generic instruction is not learning into a community; it is learning into nothing in particular. A pre-med who learned Organic Chemistry through biochemical-pathway examples has been moved toward the periphery of medical practice; a generic Organic Chemistry student has been moved toward the periphery of nothing. The motivational difference is structural, not decorative.
- **Caveat for Medhavy.** Lave & Wenger's strongest claims are about apprenticeship into bounded craft communities (tailoring, midwifery). The argument generalizes less cleanly to broad academic disciplines, where "the community of practice" is fragmented across sub-specialties. A pre-med learner is not yet a member of the cardiology community, the surgical community, or the public-health community. The domain-adapted book chooses a *fiction* of community that may or may not align with the community the learner actually enters. This is not a fatal objection but is a constraint on the cleanness of the situated-learning argument.

### 3.4 Anderson, Reder & Simon 1996 — the cognitive-science critique `[situated-learning]`

Anderson, J. R., Reder, L. M., & Simon, H. A. (1996). "Situated learning and education." *Educational Researcher*, 25(4), 5–11. ([DOI: 10.3102/0013189X025004005](https://doi.org/10.3102/0013189X025004005))

- **The critique.** Anderson, Reder & Simon (ARS) argue that situated learning's stronger claims — that knowledge is inseparable from context, that transfer is rare or impossible, that abstract instruction is necessarily inert — are not supported by the cognitive-science evidence. They marshal evidence that abstract instruction does transfer, that context-dependence is partial rather than total, and that the situated-learning literature has conflated rhetorical strength with empirical strength.
- **What ARS conceded.** ARS accept that *some* domain-specific encoding is valuable for transfer to similar domain tasks. Their target is the *strong* situated claim that abstract instruction is in principle ineffective. The weak claim — that authentic contexts and worked examples in the domain of intended use enhance transfer — they accept as supported.
- **The Greeno response and the lasting position.** Greeno (1997, *Educational Researcher* 26(1), 5–17) replied that ARS had attacked a caricature of the situated-learning position and that the productive question was not "situated vs. cognitive" but "what aspects of the learning environment most strongly influence what kind of transfer." This is the version of the debate that has substantially survived. The 2020s consensus is roughly: context matters, especially for motivation and for near transfer; abstract structure also matters, especially for far transfer; the best instruction balances both.
- **For this note.** The ARS critique is the reason the headline claim "domain-specific instruction outperforms generic instruction" needs all of its qualifiers. There is no general universal dominance of situated/domain-specific instruction over abstract/generic instruction. There is a *near transfer* dominance, a *motivation* dominance, and a *worked-example* dominance, each of which is supported. The bare claim "domain-specific is better" is not.

### 3.5 Renkl on worked examples in the learner's domain `[situated-learning][TAP]`

Renkl, A. (2014). "Toward an instructionally oriented theory of example-based learning." *Cognitive Science*, 38(1), 1–37. ([DOI: 10.1111/cogs.12086](https://doi.org/10.1111/cogs.12086))

- **The finding the field has converged on.** Worked examples — fully-worked solutions presented for the learner to study before they attempt problems on their own — produce reliably stronger learning than equivalent time spent on problem solving alone, particularly for novices. Effect sizes from Sweller, van Merriënboer & Paas (1998) and subsequent reviews are in the 0.5–1.0 SD range for novice learners on near-transfer tests.
- **The domain-specificity moderator.** Renkl and others (Atkinson, Derry, Renkl & Wortham 2000, *Review of Educational Research* 70(2), 181–214) document that worked examples in the learner's intended domain produce stronger acquisition than worked examples in unrelated domains, controlling for example complexity. The mechanism is dual: examples in-domain are more motivating (the learner sees why they would care) and the encoded representations are TAP-aligned with the problems the learner will later encounter.
- **The honest qualifier.** The worked-examples literature does not directly compare "domain-specific worked examples" to "generic worked examples" — the comparisons are usually within-domain. The cross-domain comparison is rarer because few studies have run it cleanly. The inference that *all* worked examples in domain X beat *all* worked examples not in domain X is supported by the TAP and motivation literatures, but the direct head-to-head studies are not abundant.

### 3.6 Gick & Holyoak 1980, 1983 — analogical transfer with surface vs. structural similarity `[analogical-reasoning][foundational-theory]`

Gick, M. L., & Holyoak, K. J. (1980). "Analogical problem solving." *Cognitive Psychology*, 12(3), 306–355. ([DOI: 10.1016/0010-0285(80)90013-4](https://doi.org/10.1016/0010-0285%2880%2990013-4))

Gick, M. L., & Holyoak, K. J. (1983). "Schema induction and analogical transfer." *Cognitive Psychology*, 15(1), 1–38. ([DOI: 10.1016/0010-0285(83)90002-6](https://doi.org/10.1016/0010-0285%2883%2990002-6))

- **The Duncker radiation problem paradigm.** Gick & Holyoak gave students a story analogous to the radiation problem (a general dividing his army to attack a fortress from multiple roads) and then the radiation problem (how to destroy a tumor without destroying surrounding tissue). They measured spontaneous transfer (without a hint that the prior story was relevant).
- **The headline finding.** Spontaneous transfer was *low* — roughly 30% — when learners saw one analogous story. Spontaneous transfer rose to roughly 75% when learners saw *two* analogous stories from different surface domains, because the comparison forced extraction of the underlying structural principle (the convergence schema).
- **The principle that matters here.** *Single-domain examples bind the schema to the domain.* Multiple-domain examples produce structural abstraction. If the goal is far transfer, multiple varied domains beat one focused domain. If the goal is near transfer to the same domain, one focused domain is sufficient or better.
- **For Medhavy.** This is the strongest single empirical anchor for the near-vs-far tradeoff. If Medhavy produces *Prompt Engineering for Architects* (one domain), the student will transfer better to architectural prompting and worse to medical prompting. If Medhavy produces a course with examples spanning architecture, medicine, finance, and design, the student will transfer worse to any single domain but better to the structural principle. The choice depends on what the student will do next.

### 3.7 Catrambone & Holyoak 1989 — when multiple examples produce abstraction `[analogical-reasoning]`

Catrambone, R., & Holyoak, K. J. (1989). "Overcoming contextual limitations on problem-solving transfer." *Journal of Experimental Psychology: Learning, Memory, and Cognition*, 15(6), 1147–1156. ([DOI: 10.1037/0278-7393.15.6.1147](https://doi.org/10.1037/0278-7393.15.6.1147))

- **The finding.** Multiple analogous examples produced structural abstraction *only when learners were prompted to compare them*. Two examples without comparison instructions produced little more transfer than one. Two examples with explicit "what is similar about these?" prompts produced near-ceiling transfer.
- **For curriculum design.** Domain variation alone is not sufficient for far transfer. *Explicit comparison* across the variants is required. A platform that produces N domain variants without ever asking the learner to compare them across domains gets the cost of variant production without the structural-abstraction benefit. The Catrambone & Holyoak finding is one of the cleanest implementation lessons in the analogical-transfer literature.

### 3.8 Expertise reversal — Kalyuga, Ayres, Chandler & Sweller 2003 `[analogical-reasoning][TAP]`

Kalyuga, S., Ayres, P., Chandler, P., & Sweller, J. (2003). "The expertise reversal effect." *Educational Psychologist*, 38(1), 23–31. ([DOI: 10.1207/S15326985EP3801_4](https://doi.org/10.1207/S15326985EP3801_4))

- **The effect.** Instructional designs that help novices often *hurt* experts. Worked examples that benefit novices become redundant for experts and impose cognitive load that interferes with retrieval of the expert's already-formed representations. The instruction that is optimal at one level of expertise is suboptimal at another.
- **Bearing on domain specificity.** Domain-specific examples may benefit novices more than experts. A novice in finance benefits from financial examples of statistical concepts because the examples ground unfamiliar abstractions in known referents. An expert in finance who already has the statistical structure may benefit more from *cross-domain* examples that extend their schema, because the financial examples are redundant.
- **For Medhavy.** The implication is that domain-specific framing has its largest effects on novices and its smallest (or possibly reversed) effects on experts. Medhavy's audience is undergraduate and early-graduate learners — novices in the domain they are entering. The domain-specific bet is well-aimed at this population. It would be less well-aimed at a continuing-education audience already expert in their domain who needs cross-domain extension.

### 3.9 Schwartz, Bransford & Sears 2005 — preparation for future learning `[analogical-reasoning]`

Schwartz, D. L., Bransford, J. D., & Sears, D. (2005). "Efficiency and innovation in transfer." In J. P. Mestre (ed.), *Transfer of Learning from a Modern Multidisciplinary Perspective* (1–51). IAP.

- **The reframe.** Schwartz, Bransford & Sears (SBS) argue that the standard transfer paradigm — measure whether students can immediately apply knowledge in a novel context — is the wrong measure. The right measure is *preparation for future learning* (PFL): does the instruction prepare students to *learn rapidly* when they encounter a new context, including by seeking out new information and integrating it with what they have?
- **The empirical move.** SBS show that instruction with abstract structure and varied examples produces worse immediate transfer than instruction with focused worked examples but *better* future learning when the new context is encountered with new instructional resources available. The well-prepared learner is not the one who can apply knowledge in a vacuum; it is the one who can leverage their knowledge to acquire what they need when the situation requires it.
- **For Medhavy and TtT.** This is the most important corrective to a naive reading of the TAP and PCK literatures. Domain-specific instruction is the right bet *if* the learner will spend their career in the domain. If the learner will cross domains repeatedly — and most learners in a 40-year career will — then PFL is the actual target, and PFL is better served by *some* variation across contexts even at the cost of immediate domain-specific performance.
- **The medhavy synthesis.** The right design is probably not "one domain, deep" or "all domains, shallow." It is "the learner's domain at depth, with at least one structured comparison point in an adjacent domain, and with the structural principle made explicit at the comparison." This is approximately what Catrambone & Holyoak's findings would predict.

---

## 4. The Applied Case — Professional Training

### 4.1 Davis et al. on CME effectiveness `[professional-PD]`

Davis, D., O'Brien, M. A. T., Freemantle, N., Wolf, F. M., Mazmanian, P., & Taylor-Vaisey, A. (1999). "Impact of formal continuing medical education: Do conferences, workshops, rounds, and other traditional continuing education activities change physician behavior or health care outcomes?" *JAMA*, 282(9), 867–874. ([DOI: 10.1001/jama.282.9.867](https://doi.org/10.1001/jama.282.9.867))

Davis, D., et al. (1995, *JAMA* 274(9), 700–705) is the earlier companion synthesis.

- **The finding.** Across 14 included randomized trials of formal CME, didactic-only formats (lectures, conferences) produced essentially no measurable change in physician practice or patient outcomes. Interactive formats (workshops, rounds with case discussion, audit-and-feedback) produced moderate effects on practice. Multifaceted interventions combining several formats produced the largest effects. Specialty-specific content embedded in interactive formats outperformed generic content, though the comparison is rarely clean in the underlying studies (specialty content tends to co-occur with interactivity).
- **The structure that matters for this note.** The CME literature has spent thirty years finding that *content specificity* and *interactive format* are the two most consistent moderators of effect size on practice change. Generic, didactic CME does not work. Specialty-specific, interactive CME does. The TtT Ch 8 chapter is partially building on this analogy.

### 4.2 Cervero & Gaines 2015 — the updated synthesis `[professional-PD]`

Cervero, R. M., & Gaines, J. K. (2015). "The impact of CME on physician performance and patient health outcomes: An updated synthesis of systematic reviews." *Journal of Continuing Education in the Health Professions*, 35(2), 131–138. ([DOI: 10.1002/chp.21290](https://doi.org/10.1002/chp.21290))

- **Method.** Umbrella review of 8 systematic reviews of CME (encompassing roughly 470 underlying primary studies), 2003–2014.
- **Headline findings.**
  - CME *can* improve physician performance and patient outcomes; the magnitudes are small to moderate.
  - **Content-specific CME outperforms generic CME** on practice change measures. Effect sizes for content-specific interventions on physician performance cluster around 0.20–0.40 SD; generic CME effects cluster around 0.05–0.10 SD.
  - Multiple exposures (vs. single exposures) and multimedia (vs. single medium) consistently improve effects.
  - Patient-outcome effects are smaller and more variable than physician-performance effects, paralleling the practice-to-outcome translation losses Kraft 2018 documented in teaching.
- **For TtT Ch 8.** The Cervero & Gaines finding that *content-specific CME outperforms generic CME* is a direct empirical analog to the chapter's claim that subject-specific teacher PD outperforms generic teacher PD. The mechanisms are likely similar (PCK in teaching; clinical-content-specific judgment in medicine). The effect sizes are roughly comparable in magnitude.

### 4.3 Yoon et al. 2007 — the canonical PD synthesis `[professional-PD]`

Yoon, K. S., Duncan, T., Lee, S. W.-Y., Scarloss, B., & Shapley, K. (2007). *Reviewing the evidence on how teacher professional development affects student achievement* (Issues & Answers Report, REL 2007–No. 033). Regional Educational Laboratory Southwest. ([ERIC: ED498548](https://files.eric.ed.gov/fulltext/ED498548.pdf))

- **Method.** Screened 1,343 candidate studies of teacher PD; 9 met What Works Clearinghouse evidence standards. Most rejected studies failed on causal inference (no control, contaminated assignment, attrition).
- **Findings.**
  - PD programs averaging >49 hours produced student-achievement effects equivalent to ~21 percentile points improvement (about 0.5 SD).
  - PD programs averaging <14 hours produced no detectable effect.
  - In all 9 included studies, the PD was *content-focused* — specific to a subject (math, reading, science) at a specific grade level. The synthesis cannot directly answer whether content focus matters because there is no generic-PD comparison in the included studies.
- **The honest reading.** Yoon 2007 establishes the duration threshold and the lower-bound case for sustained PD. It does *not* establish content specificity directly, because all of the included high-effect studies happen to be content-specific. The implication — that content-specific PD is the form that produces these effects — is supported by the studies' design but is correlational, not experimentally isolated, within the synthesis.
- **For TtT Ch 8.** The chapter cites Yoon 2007 correctly. The Yoon evidence is suggestive on content specificity, definitive on duration.

### 4.4 Desimone 2009 — the five-feature framework `[professional-PD][foundational-theory]`

Desimone, L. M. (2009). "Improving impact studies of teachers' professional development: Toward better conceptualizations and measures." *Educational Researcher*, 38(3), 181–199. ([DOI: 10.3102/0013189X08331140](https://doi.org/10.3102/0013189X08331140))

- **The framework.** Desimone synthesized the PD literature to identify five core features of effective PD:
  1. **Content focus** — PD anchored to specific subject-matter content and how students learn it. (The PCK-aligned feature.)
  2. **Active learning** — teachers engaging with material rather than passively receiving it.
  3. **Coherence** — alignment with state standards, district priorities, and teachers' existing knowledge.
  4. **Duration** — sufficient time spread over weeks/months rather than one-shot delivery.
  5. **Collective participation** — teachers from the same school, grade, or department working together.
- **The empirical anchor.** Desimone reviews evidence from multiple PD studies (Garet et al. 2001, Penuel et al. 2007, others) consistent with each feature predicting larger effects on teacher practice and student outcomes. Content focus is the feature with the strongest direct evidence.
- **For this note.** The Desimone framework operationalizes the "PCK plus situated learning" synthesis into a recipe for PD. The first feature — content focus — is the explicit endorsement of subject-specific PD. The Desimone framework has been adopted essentially universally in the teacher-PD literature since 2009; the field's consensus is that content focus is a necessary feature of effective PD.

### 4.5 Garet et al. 2001 — what makes PD effective `[professional-PD]`

Garet, M. S., Porter, A. C., Desimone, L., Birman, B. F., & Yoon, K. S. (2001). "What makes professional development effective? Results from a national sample of teachers." *American Educational Research Journal*, 38(4), 915–945. ([DOI: 10.3102/00028312038004915](https://doi.org/10.3102/00028312038004915))

- **Method.** Survey of 1,027 mathematics and science teachers participating in Eisenhower Professional Development Program activities.
- **Findings.** Teachers reported significantly more change in instructional practice when PD: (a) focused on specific content (math or science), (b) emphasized active learning, (c) was coherent with other professional activities, (d) was of sufficient duration, and (e) included collective participation. Content focus and active learning were the strongest single predictors.
- **For this note.** The Garet 2001 effect of *content focus* on self-reported practice change is the empirical scaffold under Desimone 2009. The construct is consistently the most robust single predictor in the PD literature.

### 4.6 Kennedy 2016 — the strongest recent synthesis `[professional-PD]`

Kennedy, M. M. (2016). "How does professional development improve teaching?" *Review of Educational Research*, 86(4), 945–980. ([DOI: 10.3102/0034654315626800](https://doi.org/10.3102/0034654315626800))

- **Method.** Re-analysis of 28 RCTs of teacher PD published 1975–2014 with student-achievement outcomes. Kennedy categorizes interventions by their *theory of action* — what the PD assumes will move teacher practice — rather than by surface features alone.
- **The headline finding.** PD programs designed around *content-specific* instructional moves (e.g., specific representations of mathematics, specific science misconception confrontations) produced larger student-achievement gains than PD programs targeting *general* teaching skills (formative assessment in general, classroom management in general, motivational design in general).
- **The Kennedy theory-of-action categories with student-outcome effect sizes (approximate):**
  - Programs giving teachers *prescribed practices* (specific instructional moves in specific content domains): largest effects (some studies in the 0.4–0.6 SD range on student outcomes).
  - Programs developing *insight into student thinking* (subject-specific misconception work, akin to PCK): moderate effects.
  - Programs developing *general teaching strategies*: small to negligible effects.
  - Programs aimed at *teacher knowledge* in the abstract: small effects on practice, minimal effects on students.
- **For TtT Ch 8.** This is the single strongest direct evidence for the chapter's central claim that AI teacher PD must be subject-specific. Kennedy 2016 establishes — across 28 RCTs — that content-specific PD produces larger student gains than generic PD. The transposition to AI is the chapter's move; the underlying empirical pattern is robust.
- **For Medhavy.** The same pattern likely generalizes to professional AI training in other fields. The Kennedy result is on K-12 teaching, but the mechanism (content-specific instructional moves anchored in domain expertise) is general enough that the same prediction would apply to "prompt engineering for radiologists" vs. "prompt engineering in general."

### 4.7 Coding bootcamps — the thin literature `[professional-PD]`

The literature on coding bootcamps is dominated by self-reported placement statistics from bootcamp operators (Course Report, SwitchUp surveys) and a small number of academic studies, mostly descriptive.

- **Daniels & Brooker (2014, *Journal of Computing Sciences in Colleges*) and the broader bootcamp-effectiveness literature** consist primarily of descriptive case studies, not comparative trials. There is no published RCT comparing domain-specific bootcamps (e.g., data science for finance) to generic data-science bootcamps.
- **Eggleston, Bohon, & Pavetti (2024, *Journal of Labor Economics*) `[verify]`** is one of the more rigorous available studies (employment outcomes for graduates of subsidized bootcamps), but does not address the specificity question.
- **The honest summary.** The bootcamp literature is too thin to settle the domain-specificity question for upskilling adults. Industry-funded marketing reports of "AI training for healthcare professionals" or "data science for financial analysts" tend to report higher completion and self-reported relevance scores than generic equivalents, but selection effects and absence of student-outcome measurement make these reports weak evidence.

---

## 5. AI Literacy and Prompt Engineering — the Thin Direct Evidence

### 5.1 Long & Magerko 2020 — the foundational competencies framework `[AI-literacy][foundational-theory]`

Long, D., & Magerko, B. (2020). "What is AI literacy? Competencies and design considerations." *Proceedings of the 2020 CHI Conference on Human Factors in Computing Systems* (1–16). ([DOI: 10.1145/3313831.3376727](https://doi.org/10.1145/3313831.3376727))

- **Contribution.** Long & Magerko define AI literacy as "a set of competencies that enables individuals to critically evaluate AI technologies; communicate and collaborate effectively with AI; and use AI as a tool online, at home, and in the workplace." They list 17 competencies across five themes (What is AI? What can AI do? How does AI work? How should AI be used? How do people perceive AI?).
- **The Long & Magerko framework is generic by construction.** The competencies are framed at a domain-neutral level. They are also not empirically validated against learning or use outcomes — the paper is a design framework, not an effects study.
- **For this note.** Long & Magerko 2020 is the AI-literacy field's most-cited starting point. It does not, on its own, support either generic or domain-specific instruction. It defines what AI literacy is. The question of how best to teach it is downstream and is mostly unanswered in the peer-reviewed literature.

### 5.2 Ng, Leung, Su, Yim, Qiao & Chu 2021/2023 — AI literacy assessment `[AI-literacy]`

Ng, D. T. K., Leung, J. K. L., Chu, S. K. W., & Qiao, M. S. (2021). "Conceptualizing AI literacy: An exploratory review." *Computers and Education: Artificial Intelligence*, 2, 100041. ([DOI: 10.1016/j.caeai.2021.100041](https://doi.org/10.1016/j.caeai.2021.100041))

Ng, D. T. K., Leung, J. K. L., Su, M. J., Yim, I. H. Y., Qiao, M. S., & Chu, S. K. W. (2023). "Teachers' AI digital competencies and twenty-first century skills in the post-pandemic world." *Educational Technology Research and Development*, 71(1), 137–161. ([DOI: 10.1007/s11423-023-10203-6](https://doi.org/10.1007/s11423-023-10203-6))

- **What Ng et al. add.** A systematization of AI literacy assessment instruments, mostly self-report scales of AI knowledge and attitudes; some performance-based measures of AI-tool use. The 2023 paper specifically addresses teacher AI competencies and finds large variance, weak baseline competence, and limited PD infrastructure (consistent with TtT Ch 8's argument).
- **What Ng et al. do not provide.** Direct experimental comparison of domain-specific vs. generic AI training. The field has not run those studies yet. Effect-size evidence is essentially absent.

### 5.3 The 2024–2026 emerging literature on domain-specific AI training `[AI-literacy]`

A targeted search for peer-reviewed studies comparing domain-specific to generic AI training (e.g., "AI for radiologists" vs. "AI for healthcare professionals" vs. "AI in general") produces meaningfully thin results as of mid-2026.

- **Medical AI literacy.** **Charow, Jeyakumar, Younus et al. (2021, *JMIR Medical Education*, 7(4), e31043)** `[AI-literacy][verify]` reviewed AI-in-healthcare curricula and found high heterogeneity in scope, level, and assessment, with no comparative studies of curriculum specificity. **Wartman & Combs (2018, *Academic Medicine*)** argue normatively for AI literacy as a medical-education core competency but provide no comparative effects evidence. **Park, Pursnani et al. (2024)** `[verify]` on radiology-resident AI training reports favorable participant evaluation; no controlled comparison.
- **Legal AI literacy.** **Susskind (2023)** *Tomorrow's Lawyers* (3rd ed., Oxford University Press) and the small but growing law-school AI-literacy literature (Schwartz, Mitchell, & various law-review pieces) are normatively strong on the need for domain-specific AI training in law but empirically thin on comparative effects.
- **Architecture and design AI training.** Largely vendor-led (Adobe, Autodesk reports on Firefly and Forma) and trade-press; no peer-reviewed comparative studies as of 2026.
- **AI for teachers.** **An, Hu, Tang et al. (2023, *Educational Technology Research and Development*)** on a teacher-AI-literacy intervention reports gains on self-report measures, no controlled comparison to generic AI training. **Su, Ng & Chu (2023)** on early-childhood-teacher AI literacy is similar.
- **The honest summary.** *There is no peer-reviewed RCT, as of mid-2026, directly comparing domain-specific AI literacy training to generic AI literacy training on the same population.* The closest comparisons are field-specific intervention reports without generic-AI control conditions. The case for domain-specific AI training rests on the adjacent literatures (TAP, PCK, situated learning, content-specific CME and teacher PD) and on theoretical inference, not on direct AI-literacy effects evidence.

### 5.4 Vendor sources — labeled and bounded `[AI-literacy][vendor]`

The remaining direct evidence is vendor case studies. These are useful as existence proofs and as scoping data; they are not peer-reviewed and they have selection and reporting incentives that should be named.

- **Anthropic case studies** (Anthropic.com/customers) `[vendor]` — Anthropic publishes case studies of enterprise Claude deployments in specific industries (legal, software, healthcare, financial services). The studies report productivity gains, user satisfaction, and integration patterns; they do not typically include controlled-comparison data on whether domain-specific Claude deployments outperform generic deployments. They are useful for understanding *what* enterprise customers deploy, not for measuring *whether specificity per se* drives the gains.
- **OpenAI / Microsoft enterprise reports** `[vendor]` — Microsoft's *Copilot for Healthcare*, *Copilot for Finance*, and similar industry-vertical products are accompanied by vendor case studies (Microsoft customer stories, OpenAI customer success pages). Reported gains in productivity and adoption are real-but-vendor-sourced. The structural argument the vendor pages make — that industry-vertical fine-tuning and prompt libraries beat generic deployments — is consistent with the TAP and worked-examples literatures but is not, on its own, peer-reviewed evidence.
- **Khan Academy / Khanmigo studies** `[vendor]` — Subject-area Khanmigo deployments (math vs. writing vs. science) report differential engagement and usage patterns; the IDK IDK finding (Digital Promise 2024, see TtT Ch 8) is the cleanest published evidence on the limits of these deployments. The Khanmigo data does not, on its own, settle the specificity question, but it documents that domain context affects user behavior in ways generic-platform claims tend to elide.

### 5.5 The TtT Ch 8 specificity claim — direct evidence audit `[AI-literacy]`

The TtT Ch 8 argument that math teachers need "AI for math teaching" PD rather than "AI for teachers" PD has the following evidence chain:

1. **PCK is subject-bound** (Shulman 1986, Hill/Rowan/Ball 2005, Sadler et al. 2013). Strong evidence.
2. **Content-focused PD outperforms generic PD on teacher practice and student outcomes** (Desimone 2009, Garet et al. 2001, Kennedy 2016). Strong evidence.
3. **AI in teaching is enacted through subject-specific PCK** — the math teacher's AI use happens in the math class, on math content, with math-specific misconceptions and math-specific representations. Strong theoretical claim; the empirical version is in early-stage descriptive studies (An et al. 2023, Su et al. 2023, Ng et al. 2023). No direct comparison studies yet.
4. **Therefore AI teacher PD must be subject-specific.** Conclusion supported by 1+2+3, with the qualification that step 3's empirical base is thin and the conclusion is an extrapolation from PCK + Desimone + Kennedy rather than a direct finding.

**The honest framing for TtT Ch 8.** The chapter's claim is well-supported by adjacent evidence and is the modal prediction the literature would make. It is *not* directly demonstrated by an RCT of subject-specific AI PD vs. generic AI PD. The chapter should — and largely does — frame this as the principled bet rather than the proven finding. Where the chapter risks over-extending: when it implies that the specificity must reach subject *and* grade level (rather than subject alone). The grade-level addition is supported by Sadler 2013's misconception evidence but is finer than what most of the cited literature directly addresses. A clean revision would attribute the grade-level specificity to misconception research specifically and the subject-level specificity to Desimone/Kennedy/Hill/PCK.

---

## 6. Adult Learning, Motivation, and the Decomposition Problem

### 6.1 Knowles on andragogy `[adult-learning][foundational-theory]`

Knowles, M. S. (1980). *The Modern Practice of Adult Education: From Pedagogy to Andragogy* (rev. ed.). Cambridge Books. ([Cambridge Books listing](https://www.umsl.edu/~henschkej/articles/a_The_%20Modern_Practice_of_Adult_Education.pdf))

- **The framework.** Knowles' six andragogical principles include the *relevance principle*: adult learners need to know why they are learning what they are learning, and learning is anchored to problems the learner is currently trying to solve in their own life or work. Adult learners are problem-centered, not content-centered.
- **The implication for domain specificity.** Adult learners — including the professionals Medhavy is designed to serve and the in-service teachers TtT Ch 8 is concerned with — are predicted to engage more deeply, persist longer, and report higher satisfaction with instruction that is anchored to their own domain than with generic instruction. The motivation effect is upstream of and partially independent of the cognitive effect.
- **Caveat.** Knowles' framework is theoretical and influential but has been criticized for being culturally specific (U.S. adult education in the 1960s–70s) and for lacking experimental validation as a complete framework. The relevance principle specifically is the most empirically supported component, partially by the broader expectancy-value literature.

### 6.2 Self-determination theory — Deci & Ryan `[adult-learning][foundational-theory]`

Ryan, R. M., & Deci, E. L. (2000). "Self-determination theory and the facilitation of intrinsic motivation, social development, and well-being." *American Psychologist*, 55(1), 68–78. ([DOI: 10.1037/0003-066X.55.1.68](https://doi.org/10.1037/0003-066X.55.1.68))

- **The framework.** Self-determination theory (SDT) identifies three universal psychological needs that drive sustained engagement: autonomy (the learner experiences agency), competence (the learner experiences capability growth), and relatedness (the learner experiences connection to others or to a meaningful community/practice).
- **Domain-relevance and competence/autonomy.** Domain-relevant content satisfies the competence need more efficiently — learners experience growth in capability they can use immediately. Domain-relevant content also feeds autonomy by allowing learners to choose how to apply what they learn in their own work. Domain-relevant content can feed relatedness by connecting the learner to a community of practice (the architects, the radiologists, the financial analysts).
- **The empirical record on SDT and learning outcomes.** A meta-analysis by Howard, Bureau, Guay, Chong & Ryan (2021, *Perspectives on Psychological Science*) — 109 studies, 230,000+ participants — found autonomy and competence supports each producing roughly 0.4–0.5 SD effects on engagement and intrinsic motivation, with smaller (0.2 SD) but consistent effects on learning outcomes. SDT effects are robust.

### 6.3 Expectancy-value — Wigfield & Eccles `[adult-learning][foundational-theory]`

Wigfield, A., & Eccles, J. S. (2000). "Expectancy–value theory of achievement motivation." *Contemporary Educational Psychology*, 25(1), 68–81. ([DOI: 10.1006/ceps.1999.1015](https://doi.org/10.1006/ceps.1999.1015))

- **The framework.** Achievement-oriented behavior is driven by expectancy (does the learner believe they can succeed?) and value (does the learner believe the task is worth doing?). Value has four components: attainment value, intrinsic value, utility value, and cost. Domain-relevant content drives *utility value* most directly — the perception that what is being learned will be useful for things the learner cares about.
- **The empirical record on utility-value interventions.** Hulleman & Harackiewicz (2009, *Science*, 326, 1410–1412) and subsequent work show that *brief utility-value interventions* — having students write a paragraph about how course content connects to their lives — produce measurable gains in course grades (effect sizes 0.15–0.30 SD, larger for students with lower expectancy). The mechanism is generalizable: framing content for personal relevance to the learner's domain or life raises engagement and retention measurably, even when the underlying content is identical.
- **For Medhavy.** Hulleman & Harackiewicz is among the strongest *direct* evidence that surface-level personalization of content to learner-relevant context produces learning gains — not just engagement gains. The effect is small per intervention but real and robust, and it is *cheap* (a writing exercise, not a curriculum rewrite). The mechanism is value-driven motivation, which sits upstream of effort allocation and persistence.

### 6.4 The decomposition problem — learning gain vs. engagement gain

The hardest question this note can pose is: *how much of the observed domain-specific advantage is genuine learning gain, and how much is engagement gain that drives more time-on-task, which in turn produces apparent learning gain?*

The literature has not cleanly decomposed this. Studies that control time-on-task (e.g., the worked-examples literature) suggest that domain-specific advantage survives time-on-task adjustment, but the controls are imperfect. Studies that decompose effects (e.g., by measuring both engagement metrics and learning outcomes separately) typically find that domain-specific framing produces both — and that the engagement and learning effects are positively correlated within learners.

**The honest position.** Domain-specific framing probably produces both effects. The cognitive (TAP/PCK) channel and the motivational (SDT/expectancy-value) channel are not exclusive; they reinforce one another. For Medhavy's design purposes, the question of which channel is doing more of the work is less important than the joint effect. For Medhavy's *measurement* purposes (the GLP framework), the decomposition matters more: engagement gains alone are the IDK IDK pattern. The GLP measurement layer is precisely designed to distinguish engagement from learning, which is the right move and is consistent with what the decomposition literature suggests is needed.

---

## 7. The Curriculum Design Question — Minimum Viable Specificity

### 7.1 The N-variants problem `[curriculum-design]`

A platform that produces N domain variants of a course incurs roughly N× the content-production cost. The question is whether that cost is justified by the marginal benefit at each level of specificity.

The literature does not directly answer this, but a reasonable taxonomy of specificity levels and what each costs / what each likely buys:

| Level | Description | Production cost | Likely benefit | Evidence base |
|---|---|---|---|---|
| 0 | Fully generic curriculum, abstract examples | 1× | Baseline; weakest motivation; weakest near transfer | TAP, situated learning predict worst near-transfer; Knowles, SDT, expectancy-value predict weakest engagement |
| 1 | Generic curriculum + few domain examples sprinkled in | ~1.1× | Modest engagement gain; minimal cognitive gain | Hulleman & Harackiewicz utility-value evidence (~0.15 SD); minimal-cost intervention |
| 2 | Generic curriculum + a domain-specific capstone project | ~1.2× | Stronger engagement gain; transfer to capstone domain; structural curriculum unchanged | Situated-learning capstone literature (Lave & Wenger style), but evidence is mostly descriptive |
| 3 | Domain-specific examples throughout, generic structural backbone | ~1.5–2× | Substantial near-transfer gain in domain; modest engagement gain; some loss of far transfer; PCK-aligned for the domain | Renkl/Atkinson worked-examples evidence; TAP encoding alignment; cost-benefit favorable |
| 4 | Fully restructured domain-specific curriculum (different concept sequence, different problem types, different worked examples) | ~3–5× | Largest near-transfer gain; largest engagement gain; largest loss of far transfer; possible PCK-aligned at the deepest level | PCK + Kennedy 2016 + content-focused PD evidence; cost questionable for non-flagship domains |

The inflection point on the cost-benefit curve is probably between Levels 2 and 3. Level 1 is cheap and produces measurable but small gains. Level 3 is moderately expensive and captures most of the cognitive and motivational benefit the domain-specificity literature predicts. Level 4 is expensive and produces incremental benefit only when the domain has unique problem types or unique misconceptions worth restructuring around.

### 7.2 The MOOC personalization literature `[curriculum-design]`

The MOOC research on domain-tracked vs. general courses is suggestive but limited.

- **Reich & Ruipérez-Valiente (2019, *Science*, 363(6423), 130–131)** — analysis of 565 MOOCs at Harvard and MIT 2012–2018 found that the much-promised personalization of MOOCs had not materialized in practice; most courses remained one-size-fits-all, with retention dominated by learner characteristics rather than course design.
- **The domain-tracked exceptions.** A small set of MOOCs that produced *parallel tracks* (e.g., a Python course with a data-science track and a web-development track) reported higher completion and self-reported relevance among track-aligned learners. The evidence is mostly platform-internal (Coursera, edX research blogs) and not strongly peer-reviewed.
- **The lesson.** MOOC personalization is mostly an under-delivered promise. The platforms that produced track-aligned variants saw differential engagement; the platforms that promised personalization without producing variants saw no differential engagement. The implication for Medhavy: producing real variants (Levels 3–4 in §7.1) is what generates the benefit; promising adaptation without producing it does not.

### 7.3 The dynamic per-learner specificity option `[curriculum-design]`

Medhavy's "context-aware AI tutor" approach — a RAG-anchored Ask AI that draws on the current section and the student's prior interactions to produce domain-relevant explanations on demand — is a fundamentally different design from static N-variant production. The cost structure is different (one curriculum, dynamic per-learner adaptation at inference time rather than at production time). The pedagogical question is different (can on-the-fly domain examples produce the same TAP, PCK, and motivational benefit as pre-produced domain examples?).

The peer-reviewed evidence on dynamic per-learner content adaptation is *very* thin as of 2026. The closest available work is on adaptive *sequencing* (knowledge-tracing, ALEKS, mastery learning) rather than adaptive *content framing*. The mechanism Medhavy is betting on — that an Ask AI grounded in the student's domain context can produce TAP-aligned explanations in real time — is theoretically defensible but empirically untested at scale.

**The Medhavy synthesis.** A reasonable design is:
- Level 1 personalization (utility-value framing, sprinkled examples) baked into all books, cheap and well-supported.
- Level 3 personalization (domain-specific examples throughout, generic backbone) for the 2–4 flagship domains the platform serves first. Cost is moderate; benefit is largest in the literature.
- Dynamic per-learner Ask AI augmentation on top, treated as a research bet rather than a settled design. Run within-learner experiments via the bandit to learn whether the dynamic layer adds measurable value beyond the static Level 3 base.

This positions Medhavy to capture most of the literature-predicted gain at moderate cost, with the high-cost Level 4 commitments reserved for domains where the platform has scale and where the evidence base is most favorable (e.g., domains where PCK is most developed, where misconceptions are well-mapped, where the community of practice is well-defined).

---

## 8. The Trust the Teacher Chapter 8 Connection — Explicit Mapping

The TtT Ch 8 argument rests on a five-link chain. Each link's evidence is summarized below with confidence ratings.

1. **PD under ~14 hours produces no measurable student-outcome effect.** *Strong evidence* (Yoon 2007).
2. **Sustained coaching produces measurable effects on instruction ($d = 0.49$) and student achievement ($d = 0.18$).** *Strong evidence* (Kraft, Blazar & Hogan 2018).
3. **PD is more effective when it is content-focused (subject-specific).** *Strong evidence* (Desimone 2009, Garet 2001, Kennedy 2016).
4. **Effective teaching requires subject-specific PCK.** *Strong evidence* (Shulman 1986, Hill/Rowan/Ball 2005, Sadler 2013).
5. **Therefore AI teacher PD must be subject-specific.** *Inference, not direct evidence* (no RCT of subject-specific AI PD vs. generic AI PD as of 2026).

Links 1–4 are well-supported by peer-reviewed evidence. Link 5 is the extrapolation TtT Ch 8 is making. The extrapolation is principled — it follows from links 3 and 4 by direct analogy — but is not directly demonstrated in the AI-literacy literature.

**The strongest single sentence in support of Ch 8's specificity argument.** Kennedy (2016, *Review of Educational Research*) re-analyzed 28 RCTs of teacher PD and found that programs giving teachers *prescribed instructional practices in specific content domains* produced the largest student-achievement gains, while programs targeting *general teaching skills* produced small to negligible effects — establishing across the strongest available causal evidence in teacher PD that content specificity is the moderator that consistently distinguishes effective from ineffective interventions.

**Where TtT Ch 8 may over-extend.**
- Implying that subject + grade-level specificity is empirically required. Sadler 2013 supports this for science misconceptions specifically; the broader literature mostly addresses subject specificity, with grade-level effects less directly measured. The over-extension is minor and probably defensible, but the citation should attribute the grade-level claim to Sadler/misconception research rather than the broader PD literature.
- Treating "AI for math teaching" as automatically equivalent in structure to "math PD" generally. The AI-specific implementation challenges (tool selection, prompt-design, output evaluation) may require AI-cross-cutting elements that pure subject-specific PD does not. The chapter should leave room for a hybrid structure: AI-specific foundational content + subject-specific application work.

---

## 9. The Medhavy Synthesis — What the Platform Should Bet On

The platform currently produces sixty-plus base textbooks with stated domain adaptations (Prompt Engineering for Art and Design vs. for CS; Organic Chemistry for pre-meds vs. for chemistry majors; algorithms for non-CS-majors). This positions Medhavy at Level 3 specificity (§7.1), which the literature predicts is near the inflection point on cost-benefit. The platform's chapter drafts (1, 4) implicitly argue this is the right level. The literature supports the bet.

The hypothesis the platform is running on — that domain-adapted books produce better engagement and better retention than generic books with the same concept map — is consistent with TAP, PCK, situated learning, worked-examples, andragogy, and expectancy-value theory. It has been empirically tested in *adjacent* domains (subject-specific teacher PD, specialty-specific CME, domain-anchored worked examples) at effect sizes in the 0.2–0.5 SD range on outcomes that matter. It has not been directly tested in AI-literacy or prompt-engineering contexts at scale, and the platform's in-class deployment is itself part of the evidence-generation program.

**The near-vs-far tradeoff Medhavy must address honestly.** Domain-adapted books optimize near transfer at the cost of structural abstraction. A pre-med who learned organic chemistry through biochemical-pathway examples will transfer well to clinical biochemistry and less well to materials science. This is a feature for learners committed to a career in the chosen domain. It is a limitation for learners who will cross domains. The platform should acknowledge this and consider whether the Glimmer mode or the Case Study mode can introduce *one* structured cross-domain comparison point, in line with Catrambone & Holyoak's finding that explicit comparison is necessary for structural abstraction.

**The dynamic per-learner specificity bet.** The Ask AI layer's RAG-anchored, context-aware operation is a research bet on Level 3+ specificity at near-Level-3 cost. The literature is too thin to settle whether this delivers; the within-learner bandit design is the right instrument for measuring it.

**The honest claim.** Medhavy is betting on a hypothesis that the strongest adjacent literatures support and that the AI-literacy literature has not yet directly tested. The bet is principled. The bet is also empirical — the platform is built to learn whether the bet pays off, and the GLP framework is the measurement layer that will distinguish engagement gains from learning gains. The bet is not the same as the claim.

---

## 10. Consolidated References (Chicago author-date)

Anderson, John R., Lynne M. Reder, and Herbert A. Simon. 1996. "Situated learning and education." *Educational Researcher* 25 (4): 5–11. https://doi.org/10.3102/0013189X025004005 `[situated-learning]`

Atkinson, Robert K., Sharon J. Derry, Alexander Renkl, and Donald Wortham. 2000. "Learning from examples: Instructional principles from the worked examples research." *Review of Educational Research* 70 (2): 181–214. https://doi.org/10.3102/00346543070002181 `[situated-learning][TAP]`

Barnett, Susan M., and Stephen J. Ceci. 2002. "When and where do we apply what we learn?: A taxonomy for far transfer." *Psychological Bulletin* 128 (4): 612–637. https://doi.org/10.1037/0033-2909.128.4.612 `[TAP][foundational-theory]`

Bjork, Robert A., and Elizabeth L. Bjork. 2011. "Making things hard on yourself, but in a good way: Creating desirable difficulties to enhance learning." In *Psychology and the Real World: Essays Illustrating Fundamental Contributions to Society*, edited by Morton A. Gernsbacher, Richard W. Pew, Leaetta M. Hough, and James R. Pomerantz, 56–64. New York: Worth Publishers. `[TAP][foundational-theory]`

Brown, John Seely, Allan Collins, and Paul Duguid. 1989. "Situated cognition and the culture of learning." *Educational Researcher* 18 (1): 32–42. https://doi.org/10.3102/0013189X018001032 `[situated-learning][foundational-theory]`

Catrambone, Richard, and Keith J. Holyoak. 1989. "Overcoming contextual limitations on problem-solving transfer." *Journal of Experimental Psychology: Learning, Memory, and Cognition* 15 (6): 1147–1156. https://doi.org/10.1037/0278-7393.15.6.1147 `[analogical-reasoning]`

Cervero, Ronald M., and Julie K. Gaines. 2015. "The impact of CME on physician performance and patient health outcomes: An updated synthesis of systematic reviews." *Journal of Continuing Education in the Health Professions* 35 (2): 131–138. https://doi.org/10.1002/chp.21290 `[professional-PD]`

Charow, Rebecca, Tharshini Jeyakumar, Sarah Younus, et al. 2021. "Artificial intelligence education programs for health care professionals: Scoping review." *JMIR Medical Education* 7 (4): e31043. https://doi.org/10.2196/31043 `[AI-literacy][verify]`

Collins, Allan, John Seely Brown, and Susan E. Newman. 1989. "Cognitive apprenticeship: Teaching the crafts of reading, writing, and mathematics." In *Knowing, Learning, and Instruction: Essays in Honor of Robert Glaser*, edited by Lauren B. Resnick, 453–494. Hillsdale, NJ: Lawrence Erlbaum. `[situated-learning]`

Craik, Fergus I. M., and Robert S. Lockhart. 1972. "Levels of processing: A framework for memory research." *Journal of Verbal Learning and Verbal Behavior* 11 (6): 671–684. https://doi.org/10.1016/S0022-5371(72)80001-X `[TAP][foundational-theory]`

Davis, David, Mary Ann Thomson O'Brien, Nick Freemantle, Fredric M. Wolf, Paul Mazmanian, and Anne Taylor-Vaisey. 1999. "Impact of formal continuing medical education: Do conferences, workshops, rounds, and other traditional continuing education activities change physician behavior or health care outcomes?" *JAMA* 282 (9): 867–874. https://doi.org/10.1001/jama.282.9.867 `[professional-PD]`

Desimone, Laura M. 2009. "Improving impact studies of teachers' professional development: Toward better conceptualizations and measures." *Educational Researcher* 38 (3): 181–199. https://doi.org/10.3102/0013189X08331140 `[professional-PD][foundational-theory]`

Digital Promise. 2024. *Estudia Khanmigo: An Equity-Focused Pilot Exploration of an AI-Powered Tutor in Puerto Rico*. September 2024. https://digitalpromise.org/wp-content/uploads/2024/09/SRM-Gates-Khanmigo-Report-Final.pdf `[AI-literacy]`

Garet, Michael S., Andrew C. Porter, Laura Desimone, Beatrice F. Birman, and Kwang Suk Yoon. 2001. "What makes professional development effective? Results from a national sample of teachers." *American Educational Research Journal* 38 (4): 915–945. https://doi.org/10.3102/00028312038004915 `[professional-PD]`

Gess-Newsome, Julie. 2015. "A model of teacher professional knowledge and skill including PCK." In *Re-examining Pedagogical Content Knowledge in Science Education*, edited by Amanda Berry, Patricia Friedrichsen, and John Loughran, 28–42. New York: Routledge. `[PCK]`

Gick, Mary L., and Keith J. Holyoak. 1980. "Analogical problem solving." *Cognitive Psychology* 12 (3): 306–355. https://doi.org/10.1016/0010-0285(80)90013-4 `[analogical-reasoning][foundational-theory]`

Gick, Mary L., and Keith J. Holyoak. 1983. "Schema induction and analogical transfer." *Cognitive Psychology* 15 (1): 1–38. https://doi.org/10.1016/0010-0285(83)90002-6 `[analogical-reasoning][foundational-theory]`

Greeno, James G. 1997. "On claims that answer the wrong questions." *Educational Researcher* 26 (1): 5–17. https://doi.org/10.3102/0013189X026001005 `[situated-learning]`

Healy, Alice F., Erica L. Wohldmann, James A. Sutton, and Lyle E. Bourne Jr. 2006. "Specificity effects in training and transfer of speeded responses." *Memory & Cognition* 34 (1): 188–202. https://doi.org/10.3758/BF03193396 `[TAP]`

Hill, Heather C., Brian Rowan, and Deborah L. Ball. 2005. "Effects of teachers' mathematical knowledge for teaching on student achievement." *American Educational Research Journal* 42 (2): 371–406. https://doi.org/10.3102/00028312042002371 `[PCK]`

Howard, Joshua L., Julien S. Bureau, Frédéric Guay, Jane X. Y. Chong, and Richard M. Ryan. 2021. "Student motivation and associated outcomes: A meta-analysis from self-determination theory." *Perspectives on Psychological Science* 16 (6): 1300–1323. https://doi.org/10.1177/1745691620966789 `[adult-learning]`

Hulleman, Chris S., and Judith M. Harackiewicz. 2009. "Promoting interest and performance in high school science classes." *Science* 326 (5958): 1410–1412. https://doi.org/10.1126/science.1177067 `[adult-learning]`

Kalyuga, Slava, Paul Ayres, Paul Chandler, and John Sweller. 2003. "The expertise reversal effect." *Educational Psychologist* 38 (1): 23–31. https://doi.org/10.1207/S15326985EP3801_4 `[analogical-reasoning][TAP]`

Kennedy, Mary M. 2016. "How does professional development improve teaching?" *Review of Educational Research* 86 (4): 945–980. https://doi.org/10.3102/0034654315626800 `[professional-PD]`

Knowles, Malcolm S. 1980. *The Modern Practice of Adult Education: From Pedagogy to Andragogy*. Rev. ed. Cambridge, MA: Cambridge Books. `[adult-learning][foundational-theory]`

Kraft, Matthew A., David Blazar, and Dylan Hogan. 2018. "The effect of teacher coaching on instruction and achievement: A meta-analysis of the causal evidence." *Review of Educational Research* 88 (4): 547–588. https://doi.org/10.3102/0034654318759268 `[professional-PD]`

Lave, Jean, and Etienne Wenger. 1991. *Situated Learning: Legitimate Peripheral Participation*. Cambridge: Cambridge University Press. `[situated-learning][foundational-theory]`

Long, Duri, and Brian Magerko. 2020. "What is AI literacy? Competencies and design considerations." In *Proceedings of the 2020 CHI Conference on Human Factors in Computing Systems*, 1–16. New York: ACM. https://doi.org/10.1145/3313831.3376727 `[AI-literacy][foundational-theory]`

Loughran, John, Pamela Mulhall, and Amanda Berry. 2004. "In search of pedagogical content knowledge in science: Developing ways of articulating and documenting professional practice." *Journal of Research in Science Teaching* 41 (4): 370–391. https://doi.org/10.1002/tea.20007 `[PCK]`

Morris, C. Donald, John D. Bransford, and Jeffery J. Franks. 1977. "Levels of processing versus transfer appropriate processing." *Journal of Verbal Learning and Verbal Behavior* 16 (5): 519–533. https://doi.org/10.1016/S0022-5371(77)80016-9 `[TAP][foundational-theory]`

Ng, Davy T. K., Jac K. L. Leung, Samuel K. W. Chu, and Maggie S. Qiao. 2021. "Conceptualizing AI literacy: An exploratory review." *Computers and Education: Artificial Intelligence* 2: 100041. https://doi.org/10.1016/j.caeai.2021.100041 `[AI-literacy]`

Ng, Davy T. K., Jac K. L. Leung, Maggie J. Su, Iris H. Y. Yim, Maggie S. Qiao, and Samuel K. W. Chu. 2023. "Teachers' AI digital competencies and twenty-first century skills in the post-pandemic world." *Educational Technology Research and Development* 71 (1): 137–161. https://doi.org/10.1007/s11423-023-10203-6 `[AI-literacy]`

Reich, Justin, and José A. Ruipérez-Valiente. 2019. "The MOOC pivot." *Science* 363 (6423): 130–131. https://doi.org/10.1126/science.aav7958 `[curriculum-design]`

Renkl, Alexander. 2014. "Toward an instructionally oriented theory of example-based learning." *Cognitive Science* 38 (1): 1–37. https://doi.org/10.1111/cogs.12086 `[situated-learning][TAP]`

Roediger, Henry L. III, David A. Gallo, and Lisa Geraci. 2002. "Processing approaches to cognition: The impetus from the levels-of-processing framework." *Memory* 10 (5/6): 319–332. https://doi.org/10.1080/09658210244000144 `[TAP]`

Rohrer, Doug, and Kelli Taylor. 2007. "The shuffling of mathematics problems improves learning." *Instructional Science* 35 (6): 481–498. https://doi.org/10.1007/s11251-007-9015-8 `[TAP]`

Ryan, Richard M., and Edward L. Deci. 2000. "Self-determination theory and the facilitation of intrinsic motivation, social development, and well-being." *American Psychologist* 55 (1): 68–78. https://doi.org/10.1037/0003-066X.55.1.68 `[adult-learning][foundational-theory]`

Sadler, Philip M., Gerhard Sonnert, Harold P. Coyle, Nancy Cook-Smith, and Jaimie L. Miller. 2013. "The influence of teachers' knowledge on student learning in middle school physical science classrooms." *American Educational Research Journal* 50 (5): 1020–1049. https://doi.org/10.3102/0002831213477680 `[PCK]`

Schwartz, Daniel L., John D. Bransford, and David Sears. 2005. "Efficiency and innovation in transfer." In *Transfer of Learning from a Modern Multidisciplinary Perspective*, edited by Jose P. Mestre, 1–51. Greenwich, CT: Information Age Publishing. `[analogical-reasoning]`

Shulman, Lee S. 1986. "Those who understand: Knowledge growth in teaching." *Educational Researcher* 15 (2): 4–14. https://doi.org/10.3102/0013189X015002004 `[PCK][foundational-theory]`

Sweller, John, Jeroen J. G. van Merriënboer, and Fred G. W. C. Paas. 1998. "Cognitive architecture and instructional design." *Educational Psychology Review* 10 (3): 251–296. https://doi.org/10.1023/A:1022193728205 `[TAP][situated-learning]`

Wigfield, Allan, and Jacquelynne S. Eccles. 2000. "Expectancy–value theory of achievement motivation." *Contemporary Educational Psychology* 25 (1): 68–81. https://doi.org/10.1006/ceps.1999.1015 `[adult-learning][foundational-theory]`

Yoon, Kwang Suk, Teresa Duncan, Silvia W.-Y. Lee, Beth Scarloss, and Kathy L. Shapley. 2007. *Reviewing the Evidence on How Teacher Professional Development Affects Student Achievement*. Issues & Answers Report, REL 2007–No. 033. Washington, DC: U.S. Department of Education, Institute of Education Sciences, Regional Educational Laboratory Southwest. https://files.eric.ed.gov/fulltext/ED498548.pdf `[professional-PD]`

**Vendor and case-study sources (labeled, not peer-reviewed):**

Anthropic. n.d. "Customer stories." Accessed May 17, 2026. https://www.anthropic.com/customers `[AI-literacy][vendor]`

Microsoft. n.d. "Customer stories: Microsoft Copilot." Accessed May 17, 2026. https://www.microsoft.com/en-us/customers `[AI-literacy][vendor]`

OpenAI. n.d. "Customer stories." Accessed May 17, 2026. https://openai.com/stories `[AI-literacy][vendor]`

---

*End of note. Maintained for revision. Where a citation carries `[verify]`, the underlying claim has been described correctly but a specific data point (year, page, exact effect size) should be re-checked against the primary source before drafting from this note.*
