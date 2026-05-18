# Research Notes — Chapter 8: The Curriculum Design Layer

*TIKTOC filename `09-the-curriculum-design-layer.md`. Bloom's level: Create. Not flagged load-bearing, but supplies the structured input the Ch 7 engine consumes — a poorly written Ch 8 silently breaks Ch 7. Compiled 2026-05-17.*

---

## A. Concept under examination — what the chapter teaches

The reader learns:

1. **Why an adaptive engine needs a curriculum design layer at all.** The bandit can only pick the best arm if it knows what *best* means for the current concept. "Best" is a function of (a) the desired learning outcome, (b) the prerequisite state required to attempt the concept, (c) the Bloom's level the concept demands, and (d) the modes appropriate for that level. None of these are inferable from a list of chapter titles. They have to be specified.
2. **Backward design as the discipline that produces the specification.** Wiggins & McTighe's *Understanding by Design* gives the operational move: start with the outcome the student should be able to demonstrate, then design the assessment that would evidence the outcome, then build the content and the practice. The shape is not "topics → tests → grades"; it is "outcomes → evidence → activities."
3. **The concept map as the deliverable.** What the Ch 7 engine consumes is not a chapter outline; it is a concept map with prerequisite dependencies, Bloom-level assignments, mode-appropriateness flags, and outcome statements. Producing this is the curriculum designer's job. Skipping it produces the "suggest 15 chapters" failure.
4. **Three curriculum design failure modes** and how each shows up in deployment.
5. **Tic TOC as the curriculum design instrument** — and the meta-move that *this very book was produced through a Tic TOC session*.

The Bloom's level is Create. The reader should leave able to produce a chapter specification a developer can build from without a translation meeting — and able to recognize a curriculum specification that the engine cannot consume.

---

## B. Specification move — pulling apart vague terms

The terms that are doing too many jobs in conventional curriculum talk:

- **Curriculum.** In K–12 speak this is a state-mandated list of standards. In higher-ed speak it is a syllabus, possibly a degree map. In ed-tech speak it is a content library. The chapter should use *curriculum* in the strictest sense: a structured specification of (concepts, prerequisite dependencies, outcomes, assessment evidence, mode appropriateness) sufficient to drive an adaptive engine.
- **Concept.** A concept is *not* a chapter title. "Drug Metabolism" is a topic — a content header. The concept inside that topic might be "the rate-limiting role of CYP3A4 in clinical drug interactions" or "first-pass effect as a determinant of oral bioavailability." The granularity needs to be at the level the bandit can adapt over: small enough that mastery is meaningfully distinct between concepts, large enough that a single Quiz Me item or Case Study can probe it.
- **Outcome.** An outcome is what the student will be able to *do*. "Understand drug metabolism" is not an outcome; it is a wish. "Predict the qualitative change in steady-state plasma concentration of warfarin when a strong CYP3A4 inhibitor is added" is an outcome. The change in verb is the whole game.
- **Prerequisite.** A prerequisite is *not* "the previous chapter." It is the concept whose mastery is *necessary* for the focal concept's mastery to be possible. Some prerequisites cross chapters; some are within-chapter. Some are within-discipline; some are cross-discipline (the warfarin example requires biochemistry, physiology, and clinical reasoning together). The prerequisite graph is multi-edge, not a chain.
- **Bloom's level.** Bloom's revised taxonomy (Anderson & Krathwohl 2001 — see §C.3) is the canonical hierarchy: Remember, Understand, Apply, Analyze, Evaluate, Create. Each level is a distinct kind of cognitive operation; different modes serve different levels. Quiz Me serves Remember and Understand best; Case Study serves Apply and Analyze; Glimmer serves Create. The bandit cannot select a mode without knowing the level. *That is why mode-appropriateness flags exist in the concept map.*
- **Suggest 15 chapters.** The chapter writer should treat this phrase as a technical term meaning "the failure mode where a curriculum designer asks an LLM to produce structure without first producing the outcomes and the prerequisite logic." The phrase deserves a paragraph of its own at the chapter's opening.

---

## C. The deep dive — backward design and what it actually requires

### C.1 Wiggins & McTighe — verify the citation precisely

The canonical reference, drawn from the TIKTOC and the pantry note on `_lib_teaching-for-deeper-learning_-tools-to-engage-students-in-meaning-making.md`:

- Wiggins, Grant, and Jay McTighe. **2005**. *Understanding by Design*. **Expanded 2nd edition**. ASCD (Association for Supervision and Curriculum Development), Alexandria VA. First edition: 1998 (ASCD).
- The 2005 expanded edition is the conventional reference; it is the edition most U.S. teacher-prep programs use as the textbook for backward-design methodology. ([ASCD landing page](https://www.ascd.org/books/understanding-by-design-expanded-2nd-edition?variant=103055)) `[verify ISBN and exact publication year if quoting page-level]`
- The companion *Understanding by Design Professional Development Workbook* (McTighe & Wiggins 2004, ASCD) is sometimes cited interchangeably; check what edition the chapter writer wants to anchor on. The 2005 expanded edition is the one with the full three-stage framework most cleanly presented.

The chapter should be careful: *Understanding by Design* is sometimes referred to as "UbD." Some readers know it well; some know it not at all. A two-sentence definition is appropriate at first use:

> *Understanding by Design* is Wiggins and McTighe's framework for curriculum planning. Its central move is *backward*: start with the long-term capability the student should hold, then design the evidence that would demonstrate the capability, then choose the activities that build it. Most curriculum design is forward — topics chosen, activities ordered, assessment grafted on at the end — and the framework's argument is that forward design systematically produces "engagement" without the underlying capability.

### C.2 The three stages — operationalized for Medhavy

Wiggins & McTighe's three stages, translated into what the Ch 7 engine needs:

1. **Identify desired results.** For each concept, name the *enduring understanding* (the persistent capability) and the *essential question* the concept resolves. Output: outcome statements at a specified Bloom level. The engine consumes the Bloom level as a mode-appropriateness flag.
2. **Determine acceptable evidence.** What artifact, performance, or pattern of responses would convince a hostile reviewer that the student has the capability? Output: assessment specifications. The engine consumes these as Quiz Me item templates, Case Study scenarios, and Glimmer rubrics.
3. **Plan learning experiences and instruction.** What sequence of activities builds the capability? Output: the activity sequence — but in Medhavy this is *not* a fixed sequence. The activity sequence is what the bandit produces dynamically. What the curriculum designer specifies is the *mode-appropriateness flags* and the *prerequisite constraints*; the bandit decides the order.

The translation matters because it shifts the locus of design. In conventional UbD the curriculum designer specifies the activity sequence; in Medhavy the curriculum designer specifies the *constraints under which the engine can sequence*. That is a smaller but more disciplined deliverable. The chapter should make this shift visible.

### C.3 Bloom's revised taxonomy — verify the reference

The chapter should use the **revised** Bloom's taxonomy, not the 1956 original. The revised version is:

- Anderson, Lorin W., and David R. Krathwohl (eds.). 2001. *A Taxonomy for Learning, Teaching, and Assessing: A Revision of Bloom's Taxonomy of Educational Objectives*. Allyn & Bacon / Pearson. ([Library of Congress](https://lccn.loc.gov/00045446)) `[verify ISBN if quoting page]`
- The revision changed the verbs from nouns to gerunds (Remember rather than Knowledge), shuffled Synthesis and Evaluation (Create is now the top, not Evaluate), and split the taxonomy into a two-dimensional structure (cognitive process × knowledge type).
- The original 1956 reference is Bloom, Benjamin S. et al. *Taxonomy of Educational Objectives: The Classification of Educational Goals. Handbook I: Cognitive Domain*. David McKay. The 1956 version is what most older textbooks cite.

For Medhavy: the mode-appropriateness flags map onto the revised hierarchy:

- Remember / Understand → Quiz Me (retrieval practice produces durable recall).
- Apply / Analyze → Case Study (scenarios force application under ambiguity).
- Evaluate → Case Study with comparative cases; Glimmer with critique rubrics.
- Create → Glimmer (generative work surfaces gaps that comprehension questions miss).

### C.4 The concept map — what the engine consumes

The concept map (the deliverable the curriculum design layer produces) must contain, at minimum:

- **Concept nodes.** Each node is one concept at the bandit-appropriate granularity. Concept granularity is a curriculum-design choice; the chapter should give guidance (typically: a concept is granular enough that a single Quiz Me item can probe it and a single Glimmer prompt can extend it; typically 5–20 concepts per chapter).
- **Prerequisite dependencies.** Directed edges between concept nodes. The graph may be a DAG (cleanest case) or contain cycles (when concepts mutually inform each other — e.g., in iterative skill development). The Ch 7 bandit's "concept prerequisites" context feature reads off this graph.
- **Bloom's level assignment.** One revised-Bloom level per node, possibly per outcome-statement (some concepts have multiple outcomes at different levels).
- **Mode-appropriateness flags.** A 4-bit (or 5-bit, if Direct Instruction is a separate arm) vector per node: which modes the curriculum designer has approved for this concept. The bandit's exploration is bounded by these flags.
- **Outcome statements.** One or more per concept, at the right Bloom level, framed as student-demonstrable performances. These become the test items the seven-day delayed retrieval probe (Ch 7 reward signal) draws from.
- **Assessment evidence specifications.** What a passing performance looks like — for the bandit, this is the rubric the GLP signal-scoring infrastructure (Ch 5) needs.

The chapter should treat the concept map as a *deliverable specification*, not a soft suggestion. A concept map missing prerequisite edges is *unusable* by the engine. A concept map without mode flags forces the engine to assume all modes are equally appropriate everywhere — which the Ch 6 mode-evidence base shows is false.

---

## D. The "suggest 15 chapters" failure — opening case in detail

The TIKTOC names the hook: *an author opens a design tool, types "suggest 15 chapters for a medical school pharmacology textbook," accepts the output, and now the engine has a concept map with no prerequisite dependencies, no outcome statements, no phase gate logic, no mode assignments. It is flying blind.*

The chapter writer should walk through what specifically goes wrong:

1. **The titles are plausible.** "Drug Absorption," "Pharmacokinetics," "Drug Metabolism," "Drug Elimination" — these are real pharmacology topics. The LLM is not hallucinating in the obvious sense. But "Drug Metabolism" is not a concept; it is a topic header. There is no outcome attached. No prerequisite. No Bloom level. No mode flag.
2. **The author accepts.** The acceptance is the consequential moment. The author has the *content expertise* to convert "Drug Metabolism" into a precise concept map, but the tool's affordance is to accept the list and move on. The friction has been removed; the discipline that produced curriculum quality in the pre-AI era has been removed with it.
3. **The engine receives.** The bandit reads the chapter titles. It tries to schedule modes against them. The Quiz Me retrieval probe has no specific items to draw from — the items are themselves AI-generated against the vague topic. The Case Study has no scenario; the LLM invents one, possibly hallucinating. The Glimmer has no rubric; whatever the student produces, the system has no basis to score.
4. **The student experiences.** The student gets sessions that feel adaptive — the engine is choosing modes, the modes are producing content — but the sessions are not aligned to a capability target because no capability target was specified. The student passes the Quiz Me items but cannot answer a clinical question on warfarin metabolism. The system logs them as engaged. They are not learning the right thing.

This is the same shape as the Khanmigo IDK-IDK failure (Ch 1) — but at the curriculum layer rather than at the mode layer. The chapter should land this connection explicitly: *the failure mode is recursive; every layer can produce the same shape of failure, and the architecture has to specify the discipline at every layer.*

The corollary the chapter should also land: **the curriculum design layer cannot be AI-generated end-to-end and produce a usable specification**. The LLM can scaffold; it can suggest; it can produce drafts that the curriculum designer revises. But the *judgment* — what counts as a concept, what counts as mastery, which mode the concept admits — has to be supplied by a human who understands the domain. This is bet #7 in the eight open bets (TIKTOC; Ch 11), and the curriculum layer is where it is most visible.

---

## E. The three curriculum design failure modes

The TIKTOC enumerates three. Expanded:

### E.1 Topic coverage masquerading as capability

The most common failure. The curriculum designer has *listed* the content but has not *specified the capability*. Symptoms:

- Chapter titles read like a table of contents in an academic textbook.
- Outcomes (if stated) are at Remember or Understand level — "Know the major CYP450 isoforms" — never Apply or above.
- Assessment evidence is multiple-choice on factual recall.
- The Ch 7 engine's bandit converges to Quiz Me on everything because Quiz Me is the only mode the curriculum supports.

Diagnostic: read the outcomes. If the verbs are *know, understand, be familiar with, learn about*, the curriculum is topic-coverage. If the verbs are *predict, design, critique, justify, construct, troubleshoot*, the curriculum is capability-targeted.

Connection: this is the failure mode the Wiggins & McTighe framework explicitly diagnoses; it is also what Hattie's *Visible Learning* identifies as the modal failure in classroom curriculum design (`_lib_edtech-.md` and the trust-the-teacher pantry; cross-reference for adjacent evidence).

### E.2 Author-sequence vs. learner-sequence

The curriculum is ordered by *author logic* rather than *learner progression*. Symptoms:

- The sequence reflects the disciplinary structure of the field — historically, philosophically, taxonomically — rather than the sequence a novice can climb.
- Prerequisites are implicit in author headcanon; the curriculum designer "of course" knows that biochemistry comes before pharmacology, but the prerequisite graph does not encode the cross-discipline edges.
- The sequence is linear when the prerequisite graph is a DAG; concepts that could be learned in parallel are forced sequential by chapter order.

Diagnostic: ask the curriculum designer to draw the prerequisite graph from memory, then compare to the chapter sequence. If the graph is a chain (each concept has exactly one prerequisite, the previous concept), the curriculum is author-sequenced. Real concept maps in any rich discipline are DAGs with branching and convergence.

Cross-reference: `concept-sequencing-research.md` §2 on knowledge-component sequencing and §6 on combining prerequisite and frequency signals. The ALEKS production system (§2.2 in that note) is the closest deployed analog of explicit prerequisite-graph traversal; ALEKS computes ready-to-learn states from the graph rather than from the chapter order.

### E.3 Prerequisite gaps appearing as learner failure

The most diagnostically dangerous failure. The curriculum *has* a prerequisite graph, but the graph is missing edges. The student fails a downstream concept; the platform attributes the failure to the downstream concept; the engine doubles down on remediation in the downstream concept; the *real* problem is the missing prerequisite the student never mastered.

Symptoms:

- A student fails Chapter 7. Platform logs show high session count, high engagement, low GLP scores.
- Remediation in Chapter 7 does not move the GLP score.
- Diagnostic deep-dive reveals: the student is missing a prerequisite from Chapter 3 that the concept map did not encode as a prerequisite for Chapter 7.

Concrete pharmacology example (illustrative; flag as such): a student is failing warfarin dosing case studies. The Chapter 7 prerequisites listed are "drug absorption" and "drug metabolism." The student has both. The missing prerequisite is "Vitamin K cycle biochemistry," which sits in the biochemistry chapter and was never encoded as a pharmacology prerequisite. The engine cannot adapt to a prerequisite gap that the curriculum did not name.

Cross-reference: `concept-sequencing-research.md` §2.6 on Schneider & Stern 2010 and Booth & Newton 2012 — prior conceptual knowledge as predictor of subsequent learning, with prerequisite gaps compounding when not remediated.

### E.4 The diagnostic the chapter should hand to the reader

The TIKTOC exercise #2 names this diagnostic: *A student is failing Chapter 7 of a deployed intelligent textbook. Platform logs show high engagement and low GLP scores. Diagnose: curriculum design failure, measurement failure, or content failure?*

The answer the reader should be able to produce:

- If the GLP signals are noisy or absent → measurement failure (Ch 5).
- If the GLP signals are clean and the engine has converged on a single mode that is not producing learning → mode-fit failure (Ch 6).
- If the GLP signals are clean and the engine has explored modes but no mode produces learning gain → either curriculum design failure (prerequisite gap; topic coverage; author sequence) or content failure (Ch 9 — the content itself is wrong, missing, or AI-hallucinated). Distinguish by inspecting the concept map and the prerequisite trace for this learner.

The diagnostic is the practical capability the chapter should leave the reader holding.

---

## F. Tic TOC as the curriculum design instrument — and the meta-move

### F.1 What Tic TOC is

Tic TOC is the platform's name for the *design conversation* — the structured intake process that produces a chapter specification (and, by extension, a book specification). It is named for the time-honored Table of Contents discipline of writing, with the *Tic* prefix marking that it is iterative and timed — a structured tic of the design clock.

The chapter writer should specify Tic TOC at three levels:

1. **As a structured intake.** A sequence of questions: who is the learner? what is the complexity threshold? what is the four-layer specification? what is the economic envelope? what are the open bets? Each question is small; each answer constrains the next.
2. **As an instrument.** Tic TOC is what Medhavy the *instrument* (as distinct from Medhavy the *platform*) does. The instrument is the conversation; the platform is what gets built.
3. **As a forcing function.** Tic TOC's discipline is to refuse to produce structure before the specification is complete. A Tic TOC session that ends at "suggest 15 chapters" without the outcome statements, prerequisite graph, Bloom levels, and mode flags is an *incomplete* session. The discipline is the instrument's value.

### F.2 The meta-move — this book is a Tic TOC session

The TIKTOC names this directly: *the meta-move: this book was produced through a Tic TOC session; the reader has been experiencing the methodology since Chapter 1.*

The chapter writer should land this carefully. Done well, it is the chapter's most memorable moment. Done poorly, it is gimmicky. The successful landing requires:

- *Naming the moves the reader has already lived through.* The intake questions (Ch 1 — who is the failure mode for; Ch 2 — what is the complexity threshold; Ch 3 — what is the evidence base). The four-layer specification (Ch 4–9). The economics check (Ch 10). The open bets (Ch 11). Each chapter is a Tic TOC question.
- *Not claiming more than this.* The book is *a* Tic TOC session, not *the* canonical Tic TOC session. Other domains will produce different question sequences. The discipline is what generalizes, not the specific sequence.
- *Reframing the reading retrospectively.* The reader has been doing the work without knowing it. Naming the work at this point makes the work visible and gives the reader the capability to do it again, on their own domain.

This is the chapter's emotional center. The chapter writer should give it space; ~600 words of the chapter should sit here.

### F.3 Tic TOC in the platform — what gets built

The instrument-to-platform translation:

- *Tic TOC the instrument:* the design conversation. Produces a specification.
- *Tic TOC the platform feature:* the UI in Medhavy where a curriculum designer runs the design conversation. Reads the answers, structures them into the concept-map data format, exports to the engine as configuration.
- *Tic TOC the deliverable:* the concept map, the outcome statements, the prerequisite graph, the mode flags — the configuration the bandit consumes.

Ch 12 returns to Tic TOC the instrument as the chapter's main subject. Ch 8 introduces it as the discipline behind the curriculum design layer.

---

## G. Connection to existing pantry

Cite by filename:

- `PEDAGOGY ARCHITECTURE.txt` — §3 on the five pedagogical approaches and §4 on the bandit's content requirements ("the bandit can only deliver what it has to work with"). The chapter's argument that curriculum-layer specification is prerequisite to engine adaptation is anchored here.
- `concept-sequencing-research.md` — §2 on knowledge-component sequencing, BKT, ALEKS prerequisite-graph traversal; §6 on combining prerequisite and frequency signals for curriculum order. Chapter cites for the technical underpinning of the prerequisite-graph requirement.
- `domain-specific-instruction-research.md` — §2 on PCK (Shulman 1986; Hill, Rowan & Ball 2005); §3 on situated learning. Anchor for the argument that the curriculum designer's domain expertise is irreducible to LLM scaffolding. Chapter cites for the "AI cannot replace the curriculum designer" claim.
- `Lexicon.txt` — the platform's vocabulary for the curriculum design layer. Use as the source for terminology (concept node, prerequisite edge, mode flag, outcome statement) when introducing the technical terms.
- `_lib_teaching-for-deeper-learning_-tools-to-engage-students-in-meaning-making.md` — Wiggins & McTighe-adjacent synthesis on backward design and meaning-making pedagogy. Use for the two-paragraph introduction to backward design at first reference.
- `Sequencing and Prioritizing Learning Concepts.txt` — supplementary on the priority-weighting question the curriculum designer faces.

Cross-reference Ch 7 notes for the engine-side argument. Ch 8 supplies the *input*; Ch 7 explains what the input is *for*. The two chapters should read as a coupled pair.

---

## H. Open questions, gaps, and verify flags

### H.1 Wiggins & McTighe edition

`[verify]` — the 2005 expanded second edition is the conventional reference. The chapter writer should confirm ISBN 978-1-4166-0035-3 (paperback) before citing page-level. If the chapter quotes specific passages, page numbers must be verified against a physical or electronic copy of the 2005 ASCD edition.

### H.2 Anderson & Krathwohl 2001 Bloom's revision

`[verify]` — the 2001 revision is the canonical update. ISBN 978-0-321-08405-7 (Pearson). If the chapter uses the original 1956 Bloom verbs (Knowledge, Comprehension, Application, Analysis, Synthesis, Evaluation), it should explicitly note that it is using the original; otherwise the revised (Remember, Understand, Apply, Analyze, Evaluate, Create) is the standard.

### H.3 The "this book is a Tic TOC session" claim

This is a structural claim about how the book was produced. The chapter writer should verify with Nik that the production process matches: was there an actual Tic TOC session for this book? When? What were the inputs? If the answer is "yes, here are the inputs," the claim has the load-bearing specificity the chapter needs. If the answer is "the book describes the methodology but the methodology itself is being built as the book is being written," the chapter should say *that* — which is fine, and consistent with the book's epistemic honesty commitment.

Open question: how much of Chapter 8's Tic TOC presentation depends on Chapter 12's Tic TOC presentation? The chapter writer should coordinate with the Ch 12 author to avoid duplication. Ch 8 introduces Tic TOC; Ch 12 demonstrates it in full. The two presentations should be additive, not redundant.

### H.4 The prerequisite-graph audit

The chapter promises a discipline — *every concept has its prerequisite edges encoded, no broken chains* — but the discipline requires a tool. What tool? The chapter writer should specify (briefly) what *prerequisite-graph audit* looks like in practice:

- Static check: every concept node has at least one incoming prerequisite edge (except foundational nodes flagged as foundational).
- Reachability check: every concept node is reachable from the curriculum's entry point through prerequisite edges.
- Cycle check: cycles either explicitly tagged (iterative skill development) or broken into directed phases.
- Cross-discipline check: concepts that pull from multiple disciplines have edges to prerequisites in each discipline.

This may be the only place in the chapter where the writer needs to specify a technical procedure. Keep it short — ~150 words — and don't gold-plate; the full audit specification belongs in Appendix B (the Causal Knowledge Graph appendix) or Appendix D (Contextual Bandits implementation).

### H.5 The "Drug Metabolism" worked example

The TIKTOC names the worked example: *a pharmacology chapter specified incorrectly (topic-coverage model) versus specified correctly (backward design model)*. The chapter writer should choose **one specific concept** within drug metabolism — recommended: *CYP3A4 inhibition and the warfarin / statin clinical interaction class* — and run both specifications side by side:

- Topic-coverage version: "Understanding Drug Metabolism," outcome "Know the major CYP450 isoforms and their substrates," assessment "Quiz Me on the substrate table." This is what the engine receives.
- Backward design version: "Predicting CYP3A4-Mediated Clinical Interactions," outcome "Given a patient on warfarin and a list of co-prescribed drugs, predict which co-prescription is most likely to produce a clinically significant INR change and explain the mechanism," prerequisites listed (CYP3A4 substrate specificity, vitamin K cycle, INR pharmacodynamics), Bloom level Apply with Analyze-tagged extension exercises, mode flags (Quiz Me for the substrate facts; Case Study for the application; Glimmer for novel patient-design scenarios), assessment "scenario-based clinical question with the rubric specified."

The contrast should be sharp. The reader should see what the engine receives in each case and *why* one is consumable and one is not.

### H.6 The "Tic TOC vs. LLM brainstorm" boundary

The chapter should be honest that *Tic TOC uses LLM assistance*. The discipline is not "no LLM"; it is "LLM scaffolds, human judges, output is a specification not a list." The boundary needs naming:

- LLM scaffolds: produces candidate concepts, candidate outcomes, candidate prerequisite edges.
- Human judges: accepts, rejects, refines each candidate.
- Output: the specification, which contains only human-judged elements.

This is the same boundary the book argues for at the content layer (Ch 9). Naming it consistently across chapters strengthens the book's overall position.

### H.7 The mode-appropriateness flags — who sets them?

The chapter says *the curriculum designer sets the mode-appropriateness flags*. But on what basis? The flags are a judgment about which modes can produce learning gain at this concept-Bloom-level pair. The judgment depends on (a) the evidence base from Ch 3 / Ch 6 and (b) the curriculum designer's domain knowledge.

The chapter should give a default mapping the curriculum designer can start from:

| Bloom level | Default mode flags (1 = allowed, 0 = blocked) |
|---|---|
| Remember | Quiz Me 1, Ask AI 1, Case Study 0, Glimmer 0 |
| Understand | Quiz Me 1, Ask AI 1, Case Study 1*, Glimmer 0 |
| Apply | Quiz Me 0, Ask AI 1, Case Study 1, Glimmer 0 |
| Analyze | Quiz Me 0, Ask AI 1, Case Study 1, Glimmer 1* |
| Evaluate | Quiz Me 0, Ask AI 1, Case Study 1, Glimmer 1 |
| Create | Quiz Me 0, Ask AI 1, Case Study 0, Glimmer 1 |

*Asterisks mark debated calls.* The curriculum designer overrides defaults based on the concept-specific call. The chapter should present this table as a starting point, not a rigid rule.

### H.8 Phase gates — the cross-chapter coordination

The TIKTOC names phase gates as the curriculum-design output ("phase gate logic for each mode"). Phase gates are introduced in Ch 6 (mode design) — the gate is the rule that says "Quiz Me is locked on this concept until the section has been read; Glimmer is locked until Quiz Me retrieval at threshold; Case Study is locked until representation sufficient." Ch 8 specifies the gates per concept; Ch 6 explains what the gates do.

The chapter writer should make this coordination explicit: *phase gates live in the curriculum spec because they encode the curriculum designer's judgment about prerequisite cognitive state; the mode-implementation reads the gate but does not set it*. This keeps the curriculum layer and the mode layer cleanly separated.

---

## I. Worked example detail — beyond TIKTOC

In addition to the warfarin / CYP3A4 example above, the chapter could use:

- **A statistics concept (illustrative).** "The Central Limit Theorem." Topic-coverage version: "Students will understand the CLT." Backward-design version: "Given a sample mean and population variance, students will compute the 95% CI for the population mean and justify the CLT's applicability." The contrast is the same.
- **An engineering concept (cross-discipline).** "Beam deflection under load." Topic version: "Students will know how beams deflect." Backward version: "Given a simply supported beam and a load distribution, students will compute the maximum deflection and identify two failure modes the deflection calculation does not predict." Useful because it illustrates the across-disciplines applicability of the framework.

Recommend the chapter pick one example (warfarin/CYP3A4 from the pharmacology hook) and run it fully, with a one-sentence reference to the engineering analog at the close to show generalization. Picking two distracts from depth.

---

## J. Assessable exercises

The TIKTOC specifies three:

1. (Create) Produce a chapter specification (outcomes, phase gates, mode assignments, prerequisite dependencies) that passes backward design audit.
2. (Analyze) Diagnose the failing student (Chapter 7, high engagement, low GLP) as curriculum vs. measurement vs. content failure.
3. (Apply) Convert a topic-coverage chapter outline into a backward-design specification, naming every change.

The exercises are well-targeted for a Create-level chapter. Worked-answer sketches for the chapter writer's reference:

- *Exercise 1 sketch.* Provide a topic ("Acid-Base Balance in Critical Care"). The student must produce: 3–5 outcome statements at Apply or above; a prerequisite dependency map with at least 5 nodes and no broken chains; mode flags justified per Bloom level; phase gate logic for each mode. This is the chapter's capstone exercise — it tests the chapter's central capability.
- *Exercise 2 sketch.* (See §E.4 above for the diagnostic procedure.)
- *Exercise 3 sketch.* Provide a sample chapter outline as it might appear in a conventional textbook table of contents. Student converts to backward-design specification, line by line, naming each change. Tests their facility with the framework rather than producing original content.

---

## K. Bridge to Chapter 9

The TIKTOC bridge: *the curriculum design layer produces the specification. The content layer produces what the specification describes. Chapter 9 answers: given what the curriculum layer requires from the content layer, what content production decisions are justified by the evidence?*

The bridge is right. The chapter writer should land it by making the dependency explicit: *the concept map specifies what the content has to do; Ch 9 asks what content production process can do it, at what cost, with what evidence*. The two chapters are coupled: curriculum-without-content is a specification of nothing; content-without-curriculum is the failure mode at the content layer that Ch 9 is exactly about preventing.

---

## L. Word-count target and chapter shape

The TIKTOC implies 5,000–7,000 words for a non-load-bearing chapter at Create level. Recommended internal allocation:

- §1 Opening ("suggest 15 chapters") — ~600 words.
- §2 Why the engine needs the curriculum layer — ~700 words.
- §3 Backward design as the instrument — ~900 words. The chapter's central methodology section; needs space for the Wiggins & McTighe introduction.
- §4 The concept map — what it must contain — ~800 words. The deliverable specification.
- §5 The three curriculum design failure modes — ~900 words.
- §6 Tic TOC as the curriculum design instrument — ~700 words. The meta-move lands here.
- §7 Worked example (warfarin / CYP3A4) — ~700 words.
- §8 Exercises, what-would-change-my-mind, still-puzzling, bridge — ~600 words.

Total: ~5,900 words.

---

## M. What would change the chapter's reading

- A documented case of a Medhavy deployment where the curriculum design layer was *omitted* (the engine ran on author-suggested chapter titles only) and the platform still produced measurable learning gains comparable to a curriculum-specified deployment. *That* would argue that the curriculum layer is over-engineered — the engine is robust to underspecification. (I expect this won't happen; the bet is that it can't. But naming the falsifier is the discipline.)
- A documented case showing that LLM-generated curriculum specifications (with the prerequisite graph, outcome statements, and mode flags) match expert-designed specifications on engine downstream performance. *That* would change the boundary between Tic TOC instrument and Tic TOC LLM-scaffolding.
- A randomized comparison of backward-design vs. topic-coverage curricula on a Medhavy deployment showing no significant difference in 6-month GLP scores. *That* would force re-examination of the Wiggins & McTighe claim that backward design produces durably different outcomes.

---

## N. Still puzzling

Two to four open questions:

1. **The concept-granularity problem.** What is the right granularity for a concept node? Too coarse, the bandit cannot adapt; too fine, the curriculum designer is producing 200 nodes per chapter. The literature does not specify the right answer. Production systems (ASSISTments, ALEKS) operate at different granularities. The Medhavy default is unsettled.
2. **The cross-discipline prerequisite problem.** The pharmacology example needs biochemistry prerequisites; the biochemistry curriculum is in a different book. How does the prerequisite graph extend across books in the platform? The Medhavi Hub architecture (Appendix E) addresses this technically; the curriculum-design discipline for cross-book prerequisite encoding is not yet specified.
3. **The LLM-as-curriculum-scaffold problem.** Where exactly is the boundary between LLM-scaffolded curriculum design (helpful) and LLM-generated curriculum design (the "suggest 15 chapters" failure)? The chapter draws a line; the line will move as LLM capability improves. What is the test that distinguishes them?
4. **The phase-gate calibration problem.** The phase gates (introduced Ch 6, specified Ch 8) require thresholds — "Quiz Me retrieval at 80% accuracy unlocks Glimmer." Where does the 80% come from? It is an empirical question the platform has not yet answered. Bet #5 in the open-bets list addresses scaffolding fading; the phase-gate threshold is the same family of empirical question.

---

*End of research notes for Ch 8. Estimated chapter word count from these notes: 5,500–6,500. Coupled-pair flag: this chapter's output is Ch 7's input; co-review the two chapters before editorial.*
