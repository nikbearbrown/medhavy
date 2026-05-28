# Research: Chapter 8 — The Seven Signals: What Genuine Learning Looks Like
## Medhavy: Is the Loop Worth It?

**Chapter one-line:** The reader learns the Frictional Framework's seven signals in plain language — what each one is, what it measures, and which mode produces it.
**Research date:** 2026-05-27

---

## 1. Primary Sources

### Foundational papers and texts

The seven signals (Y1–Y7), the Frictional Framework, and the GLP score are **proprietary inventions of Humanitarians AI / Medhavy**. No outside-of-Medhavy primary sources will use these terms in this exact form. The chapter's intellectual honesty requires citing the *mechanistic* literature each signal draws on, not pretending the integration is settled science. Section 8 flags this heavily.

**For the neurobiological foundation (the chapter's opening argument that learning leaves traces):**

- **Schultz, W., Dayan, P., & Montague, P. R. (1997). "A Neural Substrate of Prediction and Reward." *Science* 275: 1593-1599.** The dopamine temporal-difference learning paper. The mechanistic claim: dopamine neurons signal *prediction error*, not reward itself. Surprise is the encoding driver. When students bypass the cognitive work (AI offload), they bypass the prediction error and therefore the encoding signal. This is the chapter's central neuroscience argument in one citation.
- **Tulving, E. (1985). "Memory and Consciousness." *Canadian Psychology* 26(1): 1-12.** Tulving's distinction between episodic, semantic, and procedural memory systems. Useful for explaining why durable learning leaves traces in multiple systems — recognition, recall under cue, transfer.
- **Squire, L. R. (2004). "Memory Systems of the Brain: A Brief History and Current Perspective." *Neurobiology of Learning and Memory* 82: 171-177.** Consolidation as a multi-stage process; the role of sleep and time in stabilizing learned material. Anchor for Y6 (Retrieval Strength Decay).
- **McClelland, J. L., McNaughton, B. L., & O'Reilly, R. C. (1995). "Why There Are Complementary Learning Systems in the Hippocampus and Neocortex." *Psychological Review* 102: 419-457.** Complementary learning systems theory — fast hippocampal encoding, slow neocortical consolidation. The mechanistic basis for why learning takes time and shows up later, not immediately.

**For metacognitive calibration (Y4 — uncertainty calibration):**

- **Dunlosky, J., & Metcalfe, J. (2008). *Metacognition.* SAGE.** Textbook treatment of judgments of learning (JOLs), feelings of knowing, and calibration accuracy. Established finding: borrowed certainty (using an external resource) inflates JOLs without improving recall.
- **Nelson, T. O., & Narens, L. (1990). "Metamemory: A Theoretical Framework and New Findings." *Psychology of Learning and Motivation* 26: 125-173.** Foundational model of metacognitive monitoring and control.

**For transfer of learning (Y3 — cross-context transfer):**

- **Thorndike, E. L. (1901). "The Influence of Improvement in One Mental Function upon the Efficiency of Other Functions." *Psychological Review* 8: 247-261.** The founding paper. Identical-elements theory of transfer.
- **Bransford, J. D., & Schwartz, D. L. (1999). "Rethinking Transfer: A Simple Proposal with Multiple Implications." *Review of Research in Education* 24: 61-100.** The contemporary reframing — "preparation for future learning" rather than direct application. Most cited modern transfer paper.
- **Barnett, S. M., & Ceci, S. J. (2002). "When and Where Do We Apply What We Learn? A Taxonomy for Far Transfer." *Psychological Bulletin* 128(4): 612-637.** The taxonomy of near/far transfer dimensions.

**For error analysis (Y2 — error trajectory coherence):**

- **Brown, J. S., & Burton, R. R. (1978). "Diagnostic Models for Procedural Bugs in Basic Mathematical Skills." *Cognitive Science* 2(2): 155-192.** The foundational "buggy" model: student errors are not random; they reveal systematic procedural misconceptions that update lawfully under correct instruction. This is exactly the empirical pattern Y2 claims to detect.
- **VanLehn, K. (1990). *Mind Bugs: The Origins of Procedural Misconceptions.* MIT Press.** Book-length development.

**For retrieval strength and decay (Y6 — retrieval strength decay):**

- **Bjork, R. A., & Bjork, E. L. (1992). "A New Theory of Disuse and an Old Theory of Stimulus Fluctuation." In *From Learning Processes to Cognitive Processes.*** The distinction between storage strength and retrieval strength. Retrieval strength decays with disuse; storage strength does not. Y6 measures the decay curve.
- **Karpicke, J. D., & Roediger, H. L. (2008). "The Critical Importance of Retrieval for Learning." *Science* 319: 966-968.** Retrieval practice produces durable learning; restudying produces immediate performance.

**For deliberate practice and graduated assistance (Y7 — scaffolding response curve):**

- **Ericsson, K. A., Krampe, R. T., & Tesch-Römer, C. (1993). "The Role of Deliberate Practice in the Acquisition of Expert Performance." *Psychological Review* 100(3): 363-406.** Effortful, scaffolded practice at the edge of current capability is what produces expertise. Y7 detects the response shape.
- **Vygotsky, L. (1978). *Mind in Society.*** Zone of proximal development — the conceptual ancestor of "scaffolding response curve." A learner in the zone responds to a small hint; outside the zone, even big hints don't help.

**For temporal engagement (Y1) and social knowledge texture (Y5):**

- **Sweller, J. (1988). "Cognitive Load During Problem Solving: Effects on Learning." *Cognitive Science* 12(2): 257-285.** Cognitive load theory — genuine processing takes time proportional to difficulty; offloaded "processing" does not. Anchor for Y1.
- **Hadwin, A. F., & Järvelä, S. (2011). "Socially Shared Regulation of Learning: A New Frontier for Self-Regulated Learning Research." *Teachers College Record*.** Group learning research; the texture of authentic disagreement and confusion vs. surface agreement. Anchor for Y5.

### Key empirical cases

- **Bastani 2025 (carried from Ch 6) — the cleanest demonstration that the seven-signal-equivalent traces would have differed where Canvas analytics did not.**
- **AlphaTutor / Khanmigo deployment studies (2024–2025).** Various pilot reports. Most are not peer-reviewed.
- **Norman, G. (2005). "Research in Clinical Reasoning: Past History and Current Trends." *Medical Education* 39: 418-427.** The mechanism by which clinical reasoning's behavioral traces (think-aloud patterns, error coherence) are diagnostic of genuine vs. rote understanding. Health-sciences-specific anchor.

---

## 2. The Core Concept — State of the Field

### What is settled

The neurobiological argument that learning produces durable, measurable changes in the brain — and that those changes have behavioral signatures — is uncontroversial. The specific signatures (consolidation, retrieval-strength decay, transfer) are well-mapped in cognitive psychology. The argument that *engagement* is not the same as *learning* is the inverse of Chapter 7's claim and is settled.

That genuine learners show different patterns from cheating or offloading learners is established for specific behaviors: timing patterns (Sweller), error coherence (Brown & Burton), calibration accuracy (Dunlosky), and retrieval at delay (Bjork, Roediger). These are not new findings.

### What is disputed

Whether a *seven-signal composite* — operationalized at scale, in software, in real classroom deployment — can reliably distinguish genuine learning from offloading is not settled. Each signal individually has empirical support; the integration is Medhavy's bet. The book must be honest: this is theoretically motivated but not yet empirically validated as a deployed composite.

Whether the GLP score is interpretable to faculty is open. Faculty trust in numerical learning-process scores is a separate question from the validity of the underlying signals.

The exact operationalization of each signal (e.g., what counts as "coherent error trajectory" in software; what threshold for "calibration accuracy" matters) is an engineering choice with no public specification. The reader cannot evaluate the specific implementation; they can only evaluate whether the *concept* is sound.

### What has changed recently (last 5 years)

- **The decoupling problem (Ch 6) has made process-level measurement urgent.** Before LLMs, the artifact carried evidence of process. Now it does not. The seven-signal approach is a response to this loss.
- **Affective neuroscience of learning (Immordino-Yang) has reframed engagement.** "Productive struggle" — the felt experience of working at the edge of capability — has neural correlates that mere engagement does not. Y1 (temporal engagement) and Y7 (scaffolding response curve) lean on this.
- **Process mining and learning analytics at fine granularity** have matured enough that signals like Y2 (error trajectory) and Y4 (calibration) can be computed in real time from interaction logs. The seven-signal framework is technically feasible in 2026 in a way it was not in 2010.

---

## 3. Application Domain Examples

1. **Pharmacology — anticoagulation reasoning.** Y4 (calibration) is diagnostic: the genuine learner who has studied anticoagulation correctly hesitates on the borderline case (mild hepatic dysfunction; low body weight) and says "I'm not sure — I'd want to check the most recent guideline." The AI-assisted student who absorbed a textbook answer states the answer with confidence the situation does not warrant. The hesitation is the signal.
2. **Nursing — vital-signs interpretation.** Y2 (error trajectory coherence): a student who has not yet learned to integrate vital-signs trends makes coherent errors — consistently misreading subtle deterioration as stable, with a learnable pattern. A student guessing makes incoherent errors that do not update with correction. The chapter can use this as a vivid health sciences case.
3. **Medical education — clinical reasoning at delay.** Y6 (retrieval strength decay): the student who genuinely learned the differential for chest pain in the cardiology block can still produce it three months later in the emergency medicine block. The student who memorized for the block exam cannot. Y6 measures the curve.
4. **Pharmacy — medication-error analysis case studies.** Y3 (cross-context transfer): the student who learned the mechanism of QT prolongation on one drug class can recognize the risk in a new drug class. The student who memorized the warning labels cannot.
5. **Health sciences — group case discussions.** Y5 (social knowledge texture): a real case-discussion transcript contains specific confusions, partial agreements, and real-time position changes ("wait — I was wrong about the loop diuretic dosing"). An AI-assisted discussion produces smooth, generic claims. The texture of the dialogue is diagnostic.

---

## 4. The Book's Thesis Connection

This is the chapter where the loop's second step — "measure whether it helped" — gets its concrete content. The reader has been told in Ch 6 that engagement evidence is not learning evidence. Chapter 8 says: here is what learning evidence looks like, in seven specific forms, each connected to a mode.

The thesis-specific work:

1. **Each signal must connect to a mode.** Ask AI primarily produces Y1, Y4, Y7. Quiz Me primarily produces Y2, Y6. Case Study primarily produces Y3, Y4, Y7. Glimmer primarily produces Y3, Y5. The mode-to-signal mapping table (Section 7) is the chapter's structural backbone. Without it, the seven signals feel like a marketing list. With it, they feel like a coherent measurement architecture.
2. **The GLP score must be framed as adding evidence, not replacing judgment.** TIKTOC is explicit: the instructor is the meta-model. The GLP score is one input the instructor weighs against artifact quality and direct observation. The chapter must not promise the GLP score replaces faculty judgment; it promises it adds a signal faculty currently cannot see.
3. **The framework's honest status: theoretically motivated, integration-level unvalidated.** The chapter cannot oversell. Each signal has a real mechanistic basis. The composite is Medhavy's bet. The reader is buying the bet, with eyes open, when they adopt.

The reader needs to leave this chapter with three things: (1) the names of the seven signals in plain language, (2) at least one example of each in their own domain (the chapter should drive this through exercises), and (3) the mode-to-signal mapping that makes the loop coherent. The next chapter (Ch 8) will then show how the bandit uses these signals as a reward signal.

---

## 5. The AI Wayback Machine — Candidate Figures

1. **Mary Helen Immordino-Yang (preferred — woman, non-Western heritage, contemporary, accessible).** USC. Affective neuroscience of learning. Her work — *Emotions, Learning, and the Brain* (2015) — argues that the felt experience of cognitive engagement (productive struggle, surprise, social emotion) is mechanistically distinct from disengaged compliance. Directly relevant to the chapter's central argument that genuine learning leaves traces. Satisfies: woman, less famous outside ed-neuroscience, non-Western heritage. Example prompt: "You're Mary Helen Immordino-Yang. A curriculum director asks: my students look engaged, but I can't tell if they're learning. What should I look for?"
2. **Anders Ericsson (well-known in expertise research; lesser-known to general curriculum directors).** Florida State. Deliberate practice research; *Peak* (2016). Most relevant to Y7 (scaffolding response curve). His central finding: expertise is built by sustained effort at the edge of current ability, and the *behavior* of that effort is observably different from rote repetition. Example prompt: "You're Anders Ericsson. Explain to a curriculum director the difference between a student who is genuinely practicing and one who is going through motions — by what they do, not what they say."
3. **Diana Laurillard (UK; less famous in US health sciences).** UCL Institute of Education. *Teaching as a Design Science* (2012); the "Conversational Framework" for teaching and learning. Useful for Y5 (social knowledge texture) and for framing the GLP score as instructor-supporting rather than instructor-replacing. Example prompt: "You're Diana Laurillard. A curriculum director worries that adding a learning-measurement system will displace faculty judgment. What is the right framing?"

**Diversity assessment:** Two strong candidates (Immordino-Yang and Laurillard) are women; Immordino-Yang has non-Western heritage and works in affective neuroscience explicitly bridging Western and non-Western framings of learning. This is the strongest single Wayback Machine candidate across the four chapters. Use Immordino-Yang here.

---

## 6. Pedagogical Delivery Research

Chapter 8 introduces seven new concepts at once. The pedagogical risk is that the seven signals become a list to memorize rather than a coherent framework. Three moves help:

- **One signal at a time, with an example in each paragraph.** TIKTOC calls for one paragraph per signal. Each paragraph should follow the structure: name (plain-language) → mechanism (one sentence) → behavioral example (concrete, health-sciences-grounded) → which mode produces it. Repeat seven times. The structure is the pedagogy.
- **Cluster the signals into functional groups for retention.** Y1 (Temporal Engagement) and Y4 (Uncertainty Calibration) cluster as "in-the-moment" signals. Y2 (Error Trajectory) and Y7 (Scaffolding Response) cluster as "developmental" signals. Y3 (Cross-Context Transfer) and Y6 (Retrieval Strength Decay) cluster as "durability" signals. Y5 (Social Knowledge Texture) is the "dialogue" signal. Grouping aids retention. Not every reader will remember all seven; every reader can remember three clusters.
- **The two-student worked example carries the cognitive load.** The TIKTOC chapter spec calls for revisiting Ch 6's two-student scenario through all seven signals. This is the right move: a single concrete case, walked through seven times, builds the framework experientially.

The chapter must resist proprietary jargon overload. "Y1 Temporal Engagement" is fine; "GLP score" is fine if introduced clearly; further jargon (e.g., the Frictional Framework's internal subdivisions, if any exist) should be flagged as out-of-scope for this book.

The exercises do most of the transfer work. Exercise 1 asks the reader to find one behavior in their own teaching experience that corresponds to each signal. This is the chapter's transfer test and should be set up to succeed — the reader has years of relevant observations; the chapter just needs to give them the framework to name them.

---

## 7. Representation and Display Research

Per TIKTOC, this chapter MUST include a mode-to-signal mapping table. Here is the draft source:

**Mode-to-Signal Mapping (Draft):**

| Signal | Plain-language name | Ask AI | Quiz Me | Case Study | Glimmer |
|---|---|---|---|---|---|
| Y1 | Temporal Engagement | Primary | Secondary | Primary | Primary |
| Y2 | Error Trajectory Coherence | Secondary | Primary | Primary | Secondary |
| Y3 | Cross-Context Transfer | — | Secondary | Primary | Primary |
| Y4 | Uncertainty Calibration | Primary | Secondary | Primary | Primary |
| Y5 | Social Knowledge Texture | Secondary | — | Primary | Primary |
| Y6 | Retrieval Strength Decay | — | Primary | Secondary | Secondary |
| Y7 | Scaffolding Response Curve | Primary | Secondary | Primary | Secondary |

Reading: "Primary" means the mode is designed to produce this signal as its main measurement output. "Secondary" means the signal is observable as a side effect but is not the mode's primary measurement target. "—" means the signal is not meaningfully produced by this mode.

**Second representation — the seven-signal at-a-glance card:**

| # | Signal | What it asks | What genuine learning shows | What offloading shows |
|---|---|---|---|---|
| Y1 | Temporal Engagement | Does time spent scale with difficulty? | Yes (harder = longer) | No (decoupled) |
| Y2 | Error Trajectory Coherence | Do errors form a pattern that updates? | Yes (coherent, learnable) | No (random) |
| Y3 | Cross-Context Transfer | Does it work in a new context? | Yes | No (only in the trained context) |
| Y4 | Uncertainty Calibration | Does confidence match knowledge? | Yes (knows what they don't know) | No (borrowed certainty) |
| Y5 | Social Knowledge Texture | Specific confusions, real position changes? | Yes | No (smooth, generic) |
| Y6 | Retrieval Strength Decay | Does it hold at delay? | Yes | No (collapses) |
| Y7 | Scaffolding Response Curve | Does a small hint unlock? | Yes (partial → unlock) | No (needs full answer) |

**Third representation — the GLP score conceptual sketch (per TIKTOC Open Question #5).** The reader should see a stylized dashboard mock-up: per-student, per-concept, the seven signals shown as small sparklines or heat-strips, with the composite GLP score above. Critical visual point: the instructor sees both the composite and the constituent signals. Hiding the constituents would make the score opaque; showing only the composite would make it untrustworthy. Both are necessary.

---

## 8. Open Questions and Research Gaps

**Flag heavily: all of the following are proprietary to Medhavy / Humanitarians AI.**

- **The Frictional Framework as a *framework*.** The name, the integration, and the framing as seven specific signals are Medhavy's. Outside literature uses adjacent terms (cognitive load, retrieval strength, calibration, transfer) but does not bundle them this way.
- **GLP (Genuine Learning Process? Genuine Learning Profile? — the acronym is internal to Humanitarians AI).** The composite score is proprietary. No external validation literature exists on the specific composite. The book must say this.
- **The exact operationalization of each Yn.** What computational threshold turns "error trajectory" into a numerical score; what time window defines "retrieval strength decay"; what threshold on "calibration accuracy" matters — all are engineering choices undisclosed in the book. The book should commit to the *concept*, not the implementation.
- **The mode-to-signal mapping (Section 7's table) is itself a Medhavy design choice.** The mappings have face validity given each mode's design intent, but no published study validates the mapping in deployment.
- **Whether seven is the right number.** Could be six; could be nine. Medhavy committed to seven. The book should not defend the number; it should acknowledge the number is an architectural choice and explain why each of the seven is in the set.
- **Highest-priority gap (cross-chapter):** A single empirical demonstration that a Medhavy-style multi-signal score predicts downstream learning outcomes better than Canvas-style engagement metrics. This is the most important missing study. The book's honest framing: the components have evidence; the composite is the bet. A curriculum director adopting Medhavy is buying the integration on theoretical grounds. This is not a flaw of the book; it is the honest state of the evidence in 2026.
- **Faculty interpretability research.** No data on whether a typical health sciences faculty member can correctly read a GLP dashboard. The chapter cannot promise interpretability without that evidence.
- **Cross-cultural validity.** The mechanistic literature is largely from Anglophone and European traditions. Whether the seven signals look the same in international or culturally diverse cohorts is an open question.

---

## 9. Sourcing Notes

The mechanistic citations (Schultz, Squire, Tulving, Bjork, Brown & Burton, Sweller, Bransford & Schwartz) are all classic. They are the right ones, they are stable, and they translate well into plain language. Lead with one or two per signal; do not bury the chapter in citations.

The Frictional Framework and GLP score must be cited as Humanitarians AI's framework with a footnote pointing at the Medhavy manuscript (Book Two in the series). The chapter should not pretend this is third-party validated.

**Cross-chapter overlap:**
- **Ch 1:** The Bastani finding ("same AI, opposite outcomes") sets up the question this chapter answers.
- **Ch 4 (Quiz Me):** The testing effect and FSRS are mechanistically connected to Y6 (retrieval strength decay). Cross-reference.
- **Ch 5 (Case Study):** The assistance dilemma (Koedinger & Aleven) is mechanistically connected to Y7 (scaffolding response curve). Cross-reference.
- **Ch 6:** The performance/learning distinction (Bjork) is the conceptual ancestor of the seven-signal framework. Cross-reference.
- **Ch 8:** The seven signals are the reward signal for the contextual bandit. Direct setup.

**Most accessible source for the reader to follow up:** Bjork & Bjork (2011) chapter in *Psychology and the Real World*. Free PDF online; written for educators; covers Y1, Y2, Y6, Y7 implicitly.

**Aging risk:** The mechanistic literature is decade-stable. The Medhavy-specific framework may evolve. The book should commit to the seven-signal architecture as named in TIKTOC v1.0; future Medhavy versions may iterate, but the book stays anchored to the version it describes.

**Tone reminder per TIKTOC:** This is not an academic paper. The reader is making a decision, not preparing a literature review. Cite enough to be credible; translate everything; never use jargon before the concept is felt.
