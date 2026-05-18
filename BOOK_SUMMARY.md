# How to Build an Intelligent Textbook

## Detailed summary of chapters, research, and what the manuscript currently is

**Author:** Nik Bear Brown
**Project:** Medhavy — AI-native intelligent textbook platform
**Status:** Six body chapters drafted (~22,400 words); nine pantry research notes (~84,000 words); front matter and chapter 3 are placeholders; planning docs (book.md, outline.md, vision.md, architecture.md, chapters-spec.md, risks.md) are empty Tic TOC scaffolds.

---

## The book in one sentence

Most of what has been built under the banner of EdTech is solving the wrong problem, because content was never the product education was selling — and this book is the design specification for what is.

## The central argument

There are two failure modes the field manages to commit simultaneously and in opposite directions. **No AI at all** — the traditional model where the professor absorbs the automatable work (answering "what does the Warburg effect mean" for the fourteenth time this week) and the irreducibly human work (mentorship, the moment a student believes they can do something) gets crowded out by accident. **All AI** — the EdTech tradition where the AI replaces the teacher, the chatbot becomes the relationship, and the measurement system reports IDK-IDK as "engaged." Both produce worse outcomes than their proponents and critics typically acknowledge. The book argues for a third position with a name (the intelligent textbook), an architecture (four integrated layers), and a measurement framework (the GLP, not engagement) that does not collapse to either failure mode.

The book is about the platform. Each chapter is about a specific architectural commitment and the evidence that supports it.

---

## What the book already is — chapter-by-chapter summary

### Front Matter (`chapters/00-frontmatter.md`)
**Status:** Placeholder template. Title-page / copyright / dedication / preface skeleton with no substantive content yet.
**What needs to land here:** The preface. The author's voice — why this book exists, why now, what's at stake, the author's professional arc that grounds the credibility to write it.

### Introduction (`chapters/00-introduction.md`)
**Status:** Stub. Section 11 (*A note about AI*) is substantive and written; sections 1–10 and 12–13 are placeholders.
**The one substantive paragraph:** The platform thesis is opinionated; the model has no opinions of its own. The model can stress-test the thesis, surface alternatives, and pressure-test the differentiation. It cannot author the platform's identity.
**What needs to land here:** The cold open (probably the Swedish triage case used in *Computational Skepticism for AI*), the central claim, the audience location (engineers and education professionals building intelligent textbooks, not researchers measuring them after the fact), the chapter map, the running narrative thread.

### Chapter 1 — What Is Medhavy? (`chapters/01-what-is-medhavy.md`)
**Word count:** 6,567
**The argument:** Content was never the product. MIT put lectures online in 2001; Harvard followed; Khan Academy launched 2006; Coursera and edX in 2012. The world's most credentialed institutions have been giving away their content for two decades. Enrollment did not collapse — it increased. When MIT put lectures on the internet, what got more valuable was the experience of being at MIT.
**The two failure modes named:**
- *No AI at all.* Professors absorb the automatable work and the irreducibly human work gets crowded out.
- *All AI.* The Khanmigo example. Sal Khan in 2023: AI is "probably the biggest positive transformation that education has ever seen." Three years later, Kristen DiCerbo describes what the data actually showed: students typing "IDK IDK" into the Socratic prompts and moving on. The system logged them as engaged. They were not learning.
**Medhavy's four-layer architecture introduced:** Book Library (the content layer); Tic TOC (the curriculum-design layer, the instrument); the Adaptive Engine (the bandit + scheduling layer); the Measurement Layer (GLP, not engagement metrics).
**The book's key distinction:** engagement metrics vs. learning evidence. Conflating them produces systems that look effective while failing students.
**Epistemic honesty as a design decision:** the chapter ends by stating what Medhavy currently *does not* know — the chapter closes a loop by introducing the territory Chapter 5 will inhabit.

### Chapter 2 — Why Does Solving It Require a Platform? (`chapters/02-why-does-solving-it-require-a-platform.md`)
**Word count:** 5,590
**The argument:** Reasonable people will object that the problems Chapter 1 names could be solved by buying off-the-shelf tools and connecting them. This chapter argues why that doesn't work. The chapter answers a reasonable objection from someone who has heard the Chapter 1 argument and is asking the next question: *why does this have to be its own platform?*
**The structural moves:**
- *What gets lost when you measure afterward* — post-hoc measurement misses the seven signals (engagement vs. learning, struggle vs. confusion, transfer vs. recall, etc.) that require live instrumentation.
- *The seven signals that require live instrumentation* — named one by one; the case for the platform builds from this list.
- *Why bolt-on doesn't work* — the deep technical argument about why composed tools cannot produce the integrated signal an intelligent textbook needs.
- *Platform as destination vs. platform as ambient infrastructure* — Medhavy is the second.
- *Phase gates as the design principle that separates learning from engagement* — Quiz Me gated until after the section is read; Glimmer gated until after the concept is built; Case Study gated until after representation is sufficient. The gate is the mechanism by which the platform refuses to be gamed.
- *The authentic context problem* — why simulated assignments don't produce learning the same way authentic ones do.
**The synthesis:** the seven signals, the four phase gates, and the ambient-infrastructure framing are the same argument in three registers.

### Chapter 3 — placeholder (`chapters/03-chapter-02.md`)
**Status:** 269-word stub with no body content. Filename suggests it was once a renumbered draft of an earlier Chapter 2.
**Conjecture about what belongs here:** Given the existing chapter sequence (Ch 1 names the problem and the architecture; Ch 2 defends the platform; Ch 4 distinguishes from other adaptive platforms; Ch 5 names what's unknown; Ch 6 is the conductor brief) — Chapter 3 should land between *why a platform* and *what makes this platform different.* The natural slot is **the empirical evidence base** — the chapter that lays out what the research actually shows about chatbots, case-based learning, spaced repetition, generative assignments, sequencing, specificity, and educational-media economics. That's exactly what the nine pantry research notes were assembled to support. The chapter writes itself out of the pantry.

### Chapter 4 — What Makes This Different From Every Other Adaptive Platform? (`chapters/04-what-makes-this-different.md`)
**Word count:** 5,641
**The argument:** Adaptive platforms exist. There are dozens. Why is this different?
**The pattern first:** the chapter starts by describing the existing-platform pattern (recommend-next-item, optimize-engagement, A/B-test-features) and naming what that pattern produces.
**The technical difference: integration.** The four layers are explained:
- *Layer 1: Curriculum Design.* Tic TOC as the design instrument; the chapters-spec / outline / vision discipline.
- *Layer 2: The Book Library.* Domain-specific books built on a generic structural backbone — the Level-3 specificity tier validated by the domain-specific-instruction research note.
- *Layer 3: The Adaptive Engine.* The within-learner bandit that does not depend on cross-learner generalization; FSRS / SM-2 family scheduling for Quiz Me; mode selection for the four modes (Ask AI / Case Study / Quiz Me / Glimmer).
- *Layer 4: The Measurement Layer.* GLP as the reward signal, not engagement. Live instrumentation that captures the seven signals Chapter 2 named.
- *The integration.* The layers are not independent; the integration is the architecture.
**The philosophical difference:** intelligence is not one thing. The chapter argues against single-metric adaptation (predict-next-correct, engagement maximization) and for multi-objective adaptation under explicit weight tradeoffs.

### Chapter 5 — What Doesn't It Know Yet? (`chapters/05_what_doesnt_it_know_yet.md`)
**Word count:** 2,281
**The argument:** The deliberate Montaigne register chapter. What Medhavy currently knows; what it does not know; why the not-knowing is itself an instrumented research bet.
**What Medhavy knows:** the design principles, the architecture, the evidence base for each mode (chatbot effectiveness, CBL, spaced repetition, generative assignments, sequencing, specificity, economics) — drawn from the pantry.
**What Medhavy does not yet know:**
1. The right weights for the GLP reward signal.
2. Which bandit arms work for which learners on which concepts.
3. Whether content adaptation produces durable learning gains or just engagement.
4. Whether the gaming-resistance claim holds at scale.
5. What the ambient context evidence reveals.
**Two design moves the chapter introduces:**
- *Student consent architecture* — the data-collection commitments the platform makes explicit.
- *Switching behavior as signal* — when learners switch modes (from Quiz Me to Glimmer mid-session), the switch itself is information.
**Filename irregularity:** uses underscores instead of hyphens; should be renamed `05-what-doesnt-it-know-yet.md` for build-pipeline consistency.

### Chapter 6 — Medhavy: Conducting AI (`chapters/06-medhavy-conducting-ai.md`)
**Word count:** 2,316
**Status:** Currently formatted as a **chapter brief**, not a chapter draft. The opening line reads *"Feed this to Feynman × MKBHD using /write"* — it is the briefing document the chapter will be written from, not the chapter itself.
**The arguments the brief contains:**
- *The recommendation engine failure.* Netflix-style recommenders optimize for engagement-as-revealed-preference. Education's recommendation engines have inherited this objective and are wrong about it.
- *Preferences are signal, not constraint.* A learner's expressed preference to use Quiz Me instead of Glimmer is data. It is not the policy. The bandit chooses; the learner's preference informs.
- *Nobody knows what works.* The honest framing — there is no settled answer to which mode-sequence produces the most durable learning for a given learner on a given concept. The platform's bet is that within-learner bandits over instrumented modes will produce the answer.
- *The within-learner bandit: what it is learning.* Personalized contextual bandit, learning per-learner reward functions across (mode × concept × time) cells.
- *Medhavy's structural advantages as experimental substrate.* Authenticated learners, persistent identity, ground-truth assessment, phase gates that allow clean comparisons.
- *The conductor is accountable for the outcome.* The conductor (the bandit, supervised by the human author) does not pretend to be neutral. It is making bets. It owns the bets. It revises them when the evidence comes in.

### Back Matter (`chapters/99-back-matter.md`)
**Status:** Placeholder template. Acknowledgments / About the Author / Notes / References / No-Index-note / Glossary skeleton with no substantive content yet.

---

## What the research notes contribute — nine notes, ~84,000 words

The pantry is the empirical foundation that supports the chapters. Each note is organized for direct quarrying into chapter prose, with citations tagged by evidence class so the writer can pull what fits without re-deriving the evidence chain.

### 1. `ask-ai-research.md` — 5,541 words, 23 primary sources
**What it covers:** ITS and generative-AI chatbot effectiveness. Distinguishes Intelligent Tutoring Systems (mature literature, d ≈ 0.4–0.7) from generative-AI chatbots (2022–2026 literature still settling).
**Sharpest finding:** Bastani PNAS 2025 — same GPT-4 underneath, two prompt wrappers, opposite outcomes. Unguarded produced +48% practice / −17% exam; teacher-designed hint-only wrapper produced no harm. **The guardrail design is the variable, not the model.**
**The open question for medhavy:** whether context-anchoring alone (RAG to section + prerequisites) converts GPT-Base failure into GPT-Tutor success, or whether the answer-refusing guardrail must be a separate, additional design move. No published RCT has decomposed the two; medhavy's design bundles them, and its deployment could be the first decomposition.

### 2. `case-study-research.md` — 7,600 words, 32 primary sources
**What it covers:** Case-Based Learning (CBL) for the Case Study mode. Distinguishes PBL (McMaster, week-long, group, self-directed), CBL (guided, faculty-curated, shorter cycle), and TBL (Michaelsen, team-based, application exercises).
**Sharpest finding:** Medhavy's Case Study mode is solo-asynchronous AI-facilitated CBL on faculty-curated cases used at the application stage — Thistlethwaite 2012 BEME synthesis is the applicable evidence base, and it supports satisfaction and modest skill gains, does not support knowledge-superiority claims, and assumes faculty curation. **The design choices "professor-approved scenarios" and "one of four modes after representation is built" are exactly what the evidence licenses.**
**The pre-written vs. on-demand AI-generated cases call:** the existing-evidence path is pre-written + faculty review. On-demand AI generation sits outside the evidence base; it would need to demonstrate, before deployment, that it doesn't propagate clinical errors as student misconceptions.

### 3. `quiz-me-research.md` — 8,756 words, 33 primary sources
**What it covers:** The algorithm-and-mechanism side of Quiz Me. Distinguishes *retrieval practice* (learning mechanism — Roediger & Karpicke 2006), *spaced repetition* (scheduling principle — Cepeda 2006, Bjork & Bjork 1992), and *scheduling algorithms* (FSRS, SM-2, MCM, HLR — implementations).
**Sharpest finding:** Cepeda et al. 2008's temporal ridgeline of optimal retention — the optimal gap between sessions falls from ~20–40% of a one-week retention horizon to ~5–10% of a one-year horizon. The right scheduling target is not a fixed interval but a function of the retention horizon. **FSRS's "target retention" knob exposes exactly this parameter.**
**The prerequisite-chaining answer:** when a student fails on a prerequisite item, tag it, continue the current-concept session, schedule the prerequisite for high-priority re-review at the next FSRS retrievability dip, and surface an *Ask AI* re-explanation across sessions if mastery probability stays below threshold.

### 4. `quiz-me-habit-research.md` — 9,015 words, 31 primary sources + 4 vendor
**What it covers:** Anki as a habit system, not just an algorithm. B.J. Fogg / Nir Eyal / Wendy Wood on habit loops; Zeigarnik on closure; the SuperMemo-vs-Anki natural experiment.
**Sharpest finding:** The "due today" counter is the load-bearing UI element — a Zeigarnik closure variable that converts a study tool into a daily-use product. **Hiding or de-emphasizing it breaks the habit loop more reliably than any algorithm change could compensate for.**
**The algorithm-vs-habit-loop decomposition:** retrieval practice alone (no spacing) produces *g* ≈ 0.51 over re-reading. The marginal value of sophisticated scheduling is bounded by Settles & Meeder's 9.5% Duolingo result and Anki team's 20–30% review-burden reduction (an efficiency metric, not a learning metric). **The honest reading: algorithm sophistication is a small-to-moderate contributor for users who already use the tool daily, and near-zero for whether users adopt the tool at all.**
**The Quiz-Me design implication:** Quiz Me should be designed in the **flashcard register, not the quiz register**. Daily-due-count instead of session scores. A visible closure event instead of a percentage grade.

### 5. `glimmer-research.md` — 10,053 words, 48 primary sources
**What it covers:** The construct-mapping side of Glimmer. Distinguishes *generative learning activities* (Fiorella & Mayer 2016), *elaborative interrogation* (Pressley 1992), *ill-structured problems* (Jonassen 1997, 2000), and *project-based learning* (Krajcik & Blumenfeld 2006).
**Construct mapping for Glimmer (with confidence):** ill-structured problem at the session level (high confidence); emergent-portfolio writing pedagogy at the term level (medium-high); PBL minus the driving question (medium); not primarily GLA (low confidence — the chapter should not lean on GLA effect sizes).
**The anxiety failure mode:** first-generation Glimmer users in early weeks may experience the open assignment as evidence they cannot do the work, under-engage with AI-reviewer feedback, and optimize their effort toward Quiz Me as the mode that feels controllable — producing a population-level pattern where Glimmer is the under-used mode by **design failure, not content failure.**

### 6. `glimmer-displacement-research.md` — 12,912 words, 41 new + 9 cross-referenced
**What it covers:** Three new angles complementing the previous Glimmer note — the AI-displacement argument, the art-school vs. engineering field divide, the pseudocode / scaffolding-fading problem.
**Strongest finding on displacement:** Acemoglu & Restrepo 2022, Eloundou et al. 2023, Brynjolfsson/Li/Raymond 2023 support that AI is displacing specifiable cognitive tasks and compressing the skill distribution. The *educational translation* — that practicing fully-specifiable tasks therefore loses educational value while judgment-under-ambiguity practice retains it — is a **theoretically defensible 2024+ working hypothesis with adjacent empirical support and no direct empirical support in education research yet.** The book has to be honest about that.
**Strongest finding on the field divide:** Carnegie Foundation studies (Sheppard 2008 on engineering, Cooke 2010 on medicine) reached the same diagnosis a generation apart — curriculum trains for well-structured problems, profession requires ill-structured judgment. Studio-critique pedagogy that closes the gap in art and design schools has been adopted only in isolated engineering programs (Olin, d.school, MIT 2.009) at high institutional cost. **The Glimmer is the studio-critique pattern retrofitted at the assignment level so individual courses can do what the institution has not.**
**The actionable scaffolding-fading recommendation for the first three weeks:** week 1 supplies framing/mechanism/defensibility; student fills only specificity; reviewer comments only on specificity. Week 2 fades to leave defensibility blank. Week 3 first full Glimmer with all four rubric dimensions student-supplied and reviewer-commented. Operationalizes Renkl's backwards-faded worked-example sequence inside van Merriënboer's 4C/ID.

### 7. `concept-sequencing-research.md` — 9,757 words, 47 primary sources
**What it covers:** Frequency-based vocabulary sequencing (Nation, Schmitt, Coxhead AWL); prerequisite sequencing (BKT, DKT, VanLehn outer-loop); importance weighting in spaced repetition; medical-education high-yield content; the Zipf distribution problem; combining prerequisite + frequency in one scheduling model.
**Sharpest finding:** The vocabulary-frequency literature gives the empirical existence proof that frequency-ordered sequencing can dominate every alternative ordering by a wide margin — but the clinical-concept frequency infrastructure is not mature enough to deliver the same effect size automatically. **Medhavy's frequency/importance signal will have to be built from Tic TOC-elicited expert priorities, partial encounter-frequency data, and revisable weights — not lifted off the shelf.**
**The design answer:** Yes, Medhavy should add frequency/importance weighting on top of prerequisite weighting. Confidence moderate (~65–75%). Implementation: transparent linear-combination priority score (priority = α × frequency + β × importance + γ × prerequisite-depth + δ × recall-deficit), mandatory-minimum review floor for high-criticality items (the aviation-pedagogy move), and instrumentation to revise weights from deployment data.

### 8. `domain-specific-instruction-research.md` — 11,588 words, 40+ primary sources
**What it covers:** Transfer-appropriate processing (Morris/Bransford/Franks 1977); Pedagogical Content Knowledge (Shulman 1986, Hill/Rowan/Ball 2005); situated learning (Brown/Collins/Duguid 1989); subject-specific PD evidence (Kennedy 2016, Desimone 2009); AI-literacy specificity evidence (thin, 2022+).
**Sharpest finding:** Domain-specific instruction produces reliably larger near-transfer, motivational, and PCK-aligned effects than generic instruction on matched outcomes — **but at a measurable cost to far transfer and structural abstraction.** The headline claim is true with substantial qualification.
**The minimum-viable-specificity answer for Medhavy:** the inflection point sits between Level 2 (generic + domain-specific capstone) and Level 3 (domain-specific examples throughout, generic structural backbone). Level 3 for 2–4 flagship domains at ~1.5–2× production cost captures the bulk of TAP/PCK/motivation-driven benefit. **The critical design constraint:** include at least one explicit cross-domain comparison point — otherwise the deep-specificity bet trades far transfer away without recovering structural abstraction. The Glimmer or Case Study is the natural place to host this.

### 9. `educational-media-economics-research.md` — 8,737 words, ~35 primary sources
**What it covers:** Sesame Street evidence base (Mares & Pan 2013, Kearney & Levine 2019); Mayer's CTML (12 principles, effect-size support); personalization in educational media (Walkington 2013, Hulleman & Harackiewicz 2009); minimum-viable-audience economics; AI-generated content quality evidence; uncontrolled-experiment problem; homeschool / micro-audience markets; burden-of-proof inversion (Sunstein).
**Sharpest finding:** Cost collapse changes the burden of proof **asymmetrically** — lowers the deployment threshold for low-risk content (interest-matching, drill, retrieval) while leaving it unchanged for high-risk content (initial concept acquisition, expertise-level adaptation, unfamiliar domains) because the cost of being wrong scales with harm done, not with cost saved.
**The Trust the Teacher connection:** When production cost collapses, the binding constraint shifts from production-capability to **knowledge of the individual learner**. Sadler/Sonnert/Coyle/Cook-Smith/Miller 2013 (AERJ, 9,556 students) — teachers who could identify student misconceptions produced substantially larger gains than teachers who only knew the right answers. **Cheap content does not displace the teacher's pedagogical-content knowledge; it makes that knowledge more valuable by removing the cost of acting on it.** This sentence is the direct bridge between Medhavy and the trust-the-teacher argument.

---

## The vocabulary the book is teaching

The intelligent-textbook book builds and uses a specific lexicon. Some terms are inherited (Hattie's hinge point; Bastani's GPT Base / GPT Tutor; Bjork's desirable difficulties; Anki's due-count). Some are book-original or sharpened here:

- **The IDK-IDK problem** — when engagement metrics report "engaged" because students typed "I don't know, I don't know" into the Socratic prompts and moved on.
- **The four layers** — Book Library / Tic TOC / Adaptive Engine / Measurement Layer.
- **The four modes** — Ask AI / Case Study / Quiz Me / Glimmer.
- **The seven signals** — what live instrumentation captures that post-hoc measurement misses.
- **Phase gates** — Quiz Me is gated until after the section is read; Glimmer until after the concept is built; Case Study until after representation is sufficient. The gate is the mechanism by which the platform refuses to be gamed.
- **The within-learner bandit** — personalized contextual bandit over (mode × concept × time) cells, not the cross-learner generalization the existing-platform pattern uses.
- **The GLP reward signal** — the multi-objective learning measurement that replaces engagement.
- **Ambient infrastructure** — the platform is not a destination ("come spend an hour in Medhavy") but an ambient layer that runs underneath the reading experience.
- **The conductor** — the bandit + the human author together, accountable for the outcome.
- **The fluency trap** (cross-referenced from trust-the-teacher) — smooth AI output processed as understanding when it isn't.
- **Cost-collapse asymmetry** — the burden-of-proof inversion for low-risk vs. high-risk content.
- **The due-today counter** (from the Anki habit-system research) — the Zeigarnik closure variable.

---

## The central concept that runs throughout

The platform is opinionated. The model has no opinions of its own.

That sentence is the through-line. Every chapter is an instance of it. Chapter 1 says: the platform's opinion is that content is not the product. Chapter 2 says: the platform's opinion is that measurement must be live, not post-hoc. Chapter 4 says: the platform's opinion is that integration produces signals composition cannot. Chapter 5 says: the platform's opinion is to be honest about what it does not yet know. Chapter 6 says: the conductor is accountable for the bets it is making. Every chapter is an opinion the platform is willing to defend.

The book is the case for opinionated platforms in a field that has overwhelmingly tried to be neutral.

---

## What the manuscript is missing — gap analysis

### Chapters that need to be written

1. **The Preface** — the author's voice; why this book; why now. The "I have been running into this fact for years" framing from Chapter 1's opening, written at the book level.
2. **The Introduction** — sections 1–10 and 12–13 of the existing template. The cold open is probably the Swedish triage case; the central claim is "content was never the product"; the chapter map names the six existing chapters and the gaps.
3. **Chapter 3** — currently a placeholder. The natural slot is **the empirical evidence base** — the chapter that lays out what the nine pantry research notes establish. It would summarize: Bastani PNAS 2025 (chatbot scaffolding), Thistlethwaite 2012 (case-based learning), the retrieval-practice + spacing canon (Quiz Me), the ill-structured-problems literature (Glimmer), the sequencing evidence (frequency + prerequisite + importance), the domain-specificity evidence (PCK + situated learning), and the cost-collapse economics (Sesame Street + Mayer + AI-generated content). That chapter writes itself out of the pantry.
4. **The chapter that operationalizes Chapter 6** — Chapter 6 is currently a brief, not a chapter. The Feynman × MKBHD voice has to render the brief into prose. The substance is there; the writing is not.
5. **The Back Matter** — acknowledgments, about-the-author, references, glossary. The glossary in particular matters because the book is teaching vocabulary.

### Planning documents to fill

- `book.md` — currently a Tic TOC scaffold with [NEEDS HUMAN INPUT] placeholders.
- `outline.md` — same.
- `vision.md` — same.
- `architecture.md` — same.
- `chapters-spec.md` — same.
- `risks.md` — same.

The chapter drafts and pantry are now substantively ahead of the planning documents. The next sensible step is filling in the planning docs from the chapters + pantry, not the other way around.

### Structural gaps the pantry implies but the chapters haven't named yet

- **The Tic TOC system itself.** Chapter 1 names Tic TOC as the curriculum-design layer. Chapter 4 names it as Layer 1. But no chapter currently *describes* Tic TOC — what it is, how it works, what makes it different from existing curriculum-design tools. The book the reader is reading is itself a Tic TOC artifact. That meta-move is unspecified.
- **The four-mode rationale as a single chapter.** The pantry has separate research notes for each mode (Ask AI, Case Study, Quiz Me, Glimmer) plus a habit-loop note specifically for Quiz Me. The book has no chapter that explains *why these four modes and not others* — the typological argument. That belongs somewhere between Chapter 4 (the architecture) and the chapter that hasn't been written yet about the empirical base.
- **The cost-collapse argument as a chapter.** The `educational-media-economics-research.md` note is dense and good. None of the existing chapters surfaces it. This is probably its own chapter — the economic case for the intelligent textbook, separate from the architectural case.
- **The trust-the-teacher bridge.** The Sadler 2013 finding combined with the cost-collapse asymmetry argument is the cleanest possible bridge between this book and the author's other book *Trust the Teacher*. There's no chapter that does that bridge work. It could be a short chapter or an epilogue.

---

## Open questions the deployment is designed to answer

The book's most interesting structural commitment is that the platform is itself the experimental apparatus. Each open question listed below corresponds to a research bet medhavy is making, and the deployment is instrumented to produce evidence on each.

1. **Does context-anchoring alone (RAG-to-current-section + prerequisites) convert a Bastani GPT-Base failure into a GPT-Tutor success, or is the answer-refusing guardrail a separate, additional requirement?** *(From `ask-ai-research.md`.)*
2. **Does pre-written + faculty-reviewed case-based learning produce reasoning gains comparable to group human-facilitated CBL when delivered solo and asynchronous?** *(From `case-study-research.md`.)*
3. **Does FSRS-style scheduling, trained on Anki review logs (vocabulary, atomic facts), generalize to conceptual material where the unit of review is multi-step reasoning?** *(From `quiz-me-research.md`.)*
4. **Is the Quiz Me habit loop driven primarily by the due-count closure mechanic, the streak, the shared-deck community effect, or the algorithm quality? Can a Medhavy-style platform reproduce the Anki adoption pattern in a domain where no shared community decks exist?** *(From `quiz-me-habit-research.md`.)*
5. **Does the Glimmer's backwards-faded scaffolding in weeks 1–3 prevent the predicted anxiety-quadrant collapse for novice learners with no prior open-assignment experience?** *(From `glimmer-research.md` + `glimmer-displacement-research.md`.)*
6. **Does priority-weighted (frequency + importance + prerequisite + recall) scheduling produce durable learning gains over recall-only scheduling in a medical-education context?** *(From `concept-sequencing-research.md`. The note observes that no published RCT has compared these.)*
7. **Does Level-3 domain specificity (Medhavy's current bet) outperform Level-1 generic instruction on near-transfer measures by enough to justify the ~1.5–2× production cost?** *(From `domain-specific-instruction-research.md`.)*
8. **Does AI-generated educational content at $5/unit produce durable learning outcomes comparable to professionally produced Sesame-Street-quality content at $5/child/year? At what audience size does the cost-collapse argument break down?** *(From `educational-media-economics-research.md`.)*

These eight questions are the chapter the book hasn't written yet — *What Medhavy Is Trying to Find Out*, which is the empirical-bet inventory.

---

## Honest framing the book should adopt

The Medhavy book is making a forward-looking architectural argument. The peer-reviewed evidence directly testing the integrated platform claim does not yet exist. The adjacent evidence (Sesame Street, Mayer's CTML, PCK, situated learning, retrieval practice, spaced repetition, ill-structured problems, Bastani's GPT-Tutor design) is strong. The direct evidence (AI-generated curriculum content RCT data, context-aware chatbot vs. general chatbot RCT data, Glimmer-style rubrics in clinical reasoning) is genuinely thin. The book should be calibrated accordingly — making the architectural bet, naming the adjacent evidence that supports it, naming the direct evidence that doesn't yet exist, and framing the deployment as the apparatus that will produce the missing direct evidence.

This framing is the book's honesty contract with the reader, and it is the chapter Medhavy is best positioned to write that nobody else in the field is currently writing.

---

## The book in one paragraph (for the back cover)

EdTech has had two decades to disrupt education. It did not. MIT put its lectures online in 2001; Coursera and edX in 2012; Khan Academy launched in 2006; Khanmigo arrived in 2023 with the most ambitious Socratic-tutor claims any vendor had ever made. Three years later, students were typing "IDK IDK" into the Socratic prompts and moving on. The system logged them as engaged. They were not learning. *How to Build an Intelligent Textbook* is the design specification for what the field has been failing to build — an opinionated platform with a measurement layer that captures learning rather than engagement, an adaptive engine that uses within-learner bandits rather than cross-learner generalization, a curriculum-design instrument (Tic TOC) that treats the textbook as a research apparatus rather than a static artifact, and four pedagogical modes (Ask AI, Case Study, Quiz Me, Glimmer) each anchored to a specific empirical evidence base and each gated to prevent the failure modes the field has spent sixty years repeating. The book is the case for opinionated platforms in a field that has overwhelmingly tried to be neutral.

---

*End of summary. Manuscript word count: ~22,400 (chapter drafts) + ~84,000 (pantry research notes) = ~106,400 words of book-relevant material. The book has its empirical foundation. The next sensible move is filling in the planning documents from the chapters + pantry and writing the four missing chapters (preface, introduction, the empirical-evidence-base chapter, and the Feynman × MKBHD rendering of Chapter 6).*
