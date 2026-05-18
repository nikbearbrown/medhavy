# Chapter 9: The Curriculum Design Layer

---

## Learning Objectives

By the end of this chapter, you will be able to:

1. **(Understand)** Explain why an adaptive engine is useless without a curriculum design layer — and name what specifically the engine cannot learn from an underspecified concept map.
2. **(Understand)** Describe backward design (Wiggins & McTighe) in two paragraphs: what its three stages are, what changes when you start from outcomes rather than topics, and why most curriculum is not built this way.
3. **(Apply)** Specify the contents of a concept map detailed enough to drive an adaptive engine — concept nodes, prerequisite edges, Bloom-level assignments, mode-appropriateness flags, outcome statements, and assessment evidence specifications.
4. **(Analyze)** Identify the three curriculum design failure modes — topic coverage masquerading as capability, author-sequence overriding learner-sequence, prerequisite gaps appearing as learner failure — and diagnose which one a deployed platform is exhibiting.
5. **(Create)** Produce a chapter specification, in backward design form, detailed enough that a developer could configure the adaptive engine without a meeting.

**Prerequisites:** Chapter 7 (the adaptive engine), because this chapter is its mirror image. Chapter 7 explained what the engine does with the concept map; this chapter explains what the concept map has to be. Also helpful: Chapter 5 on the measurement layer, because some of what the curriculum specifies is what the measurement layer probes.

**Where this fits:** The Medhavy architecture is a loop: measurement specifies what the engine can learn, modes give the engine its arms, curriculum design tells the engine what counts as good outcomes for each concept at each Bloom level, and content fills in what the curriculum specifies. This chapter sits between the engine and the content. It is the layer that, when done well, is invisible — and when done poorly, makes every other layer look broken.

---

## Where this fits the conductor frame

This chapter primarily serves the instructor — the second of the three questions, in order. The learner is downstream; the organization is further downstream still. But the curriculum specification is the work the instructor has to do before the platform can serve either of them. A curriculum that is topic-coverage masquerading as capability cannot be conducted against; the conductor will measure engagement because there is nothing else to measure.

What this chapter specifies for the conductor is the score she reads. Backward design produces the outcome statements, prerequisite edges, Bloom-level assignments, and mode-appropriateness flags that the adaptive engine of Chapter 8 needs to know what counts as a good outcome. Without this score, the conductor's decisions are arbitrary — sessions happen, modes get picked, dashboards register engagement, but no learning target was specified, so no learning can be tested for. The curriculum design layer is what makes the conductor's work legible at all.

The chapter runs the experiment by making the curriculum specification itself the contestable claim. Each outcome statement, each prerequisite edge, is a falsifiable bet about what learners need and in what order. When the deployment data shows that students fail Concept 7 because of an unspecified upstream gap, the conductor revises the prerequisite graph. The curriculum is not handed down from authority; it is held openly, tested against learner trajectories, and updated as the evidence accumulates.

---

## Suggest 15 Chapters

An author opens a design tool. She is a domain expert — a practicing pharmacologist, twenty years of teaching, a book contract with a respectable academic press, an idea about how to teach pharmacology better than the textbook she had to use as a student.

She types into the prompt: *"Suggest 15 chapters for a medical school pharmacology textbook."*

The model produces fifteen plausible-sounding chapter titles. *Drug Absorption. Distribution and Protein Binding. Drug Metabolism. Drug Elimination. Pharmacodynamics. Receptor Theory. Dose-Response Relationships. Drug-Drug Interactions. Adverse Drug Reactions. Special Populations. Antimicrobials. Cardiovascular Drugs. CNS Drugs. Oncology Drugs. Endocrine Drugs.*

They are plausible. They are the standard topics. They are wrong — not in their content, but in their shape. The author accepts. The tool offers to scaffold each chapter; she accepts that too. Two hours later she has an outline that looks like a book.

What she does not have, and the platform does not have, is a *concept map the adaptive engine can use*.

The chapter titles are topics, not concepts. There are no outcome statements. There are no prerequisite dependencies — *Drug Metabolism* depends on something, but the outline does not say what. There are no Bloom-level assignments — does the student need to *Remember* the major CYP450 isoforms or to *Apply* their knowledge of CYP450 substrate specificity to predict a clinically significant interaction? Those are different learning goals that require different modes; the outline collapses them. There are no mode-appropriateness flags telling the engine which modes are sensible for which concepts. The phase gates — when a Glimmer becomes available, when a Case Study unlocks — are nowhere in the document because the document has no specification of cognitive state.

The engine reads the chapter titles. It tries to schedule modes against them. The Quiz Me retrieval probe has no specific items to draw from. The Case Study has no scenario; the model invents one, possibly hallucinating. The Glimmer has no rubric; whatever the student produces, the system has no basis to score. The student gets sessions that feel adaptive — modes are being chosen, content is being generated — but the sessions are not aligned to a capability target *because no capability target was specified*. The student passes the Quiz Me items. She cannot answer a clinical question about warfarin metabolism. The system logs her as engaged.

This is the Khanmigo IDK-IDK failure (Chapter 1) at a different layer. There, the failure was at the mode level — the Socratic prompt did not enforce the discipline the mode required. Here, the failure is at the curriculum level — the concept map did not specify the capability the engine was supposed to help the student build. **The failure mode is recursive. Every layer can produce the same shape of failure, and the architecture has to specify the discipline at every layer.**

The discipline at this layer is what the rest of this chapter is about. It has a name that ought to be more famous than it is: backward design.

---

## What the Engine Cannot Learn from a Bad Map

Before we get to the methodology, I want to be precise about *what specifically goes wrong* downstream when the curriculum layer is underspecified. Chapter 7 established that the engine is a contextual bandit whose arms are modes and whose reward is a learning signal. Take each of those words and ask: what does the curriculum layer have to supply for the engine to do its work?

**Arms.** The four modes are not equally appropriate for every concept. Quiz Me retrieval practice produces durable storage on Remember and Understand-level concepts. Case Study produces transfer on Apply and Analyze-level concepts. Glimmer produces generative integration on Evaluate and Create-level concepts. Ask AI is useful across all of them but in different roles — initial clarification, prerequisite rescue, between-mode bridging. If the curriculum does not tell the engine which modes are sensible for the concept, the engine has to *learn it* from outcome data — which means the early sessions are wasted on confirming what the curriculum designer could have specified up front. Bandit budget spent on rediscovering pedagogy is bandit budget not spent on learning per-learner adaptation.

**Reward.** The reward signal is partly composed of a delayed retrieval probe — a Quiz Me item offered seven days after the mode-decision session. The probe items have to *exist*. Someone has to write them, calibrated to the outcome the concept is supposed to produce. If the curriculum says "Understand Drug Metabolism" — a verb so soft it does not specify what the student should be able to do — there is no clean way to write the probe item. A probe drawn from the substrate table tests Remember. A probe asking the student to predict an interaction tests Apply. The curriculum's outcome verb decides which is appropriate; with a soft verb, the writer picks one and the engine's reward signal is now partly an artifact of the probe-writer's guess about what the curriculum designer meant.

**Context.** The engine's context vector (Chapter 7) includes prerequisite mastery — the mean retrievability across all upstream concepts in the prerequisite graph. If the prerequisite graph is incomplete, the context vector is wrong. A student who is failing the focal concept *because of a missing upstream concept* looks, to the engine, like a student who is failing the focal concept. The engine doubles down on remediation in the focal concept. The real problem is the missing prerequisite no one encoded.

**Exploration constraints.** Bandit exploration is bounded by the mode-appropriateness flags. Without flags, every mode is in every arm, all the time, and the engine explores into modes that are obviously wrong for the concept (Glimmer on a foundational Remember-level concept; Quiz Me as the only tool for an Apply-level interaction-prediction outcome). The flags are the curriculum designer's *judgment that some modes are not worth trying here* — judgment that, when the engine has to relearn it from scratch, costs sessions.

In each case, the missing curriculum-layer specification does not crash the engine. It silently degrades the engine's learning. The engine appears to be doing something, the modes are being chosen, the data is accumulating. The platform looks adaptive. What it is doing is rediscovering, slowly and noisily, what the curriculum designer could have stated cleanly up front.

Garbage in, garbage out. The phrase is a cliché. It happens to be exactly right.

---

## Backward Design — Two Paragraphs for the Skeptic

Some readers know this framework already. Some have never heard of it. The chapter cannot proceed without making sure everyone has the same two paragraphs in their head.

*Understanding by Design* is the framework Grant Wiggins and Jay McTighe published in 1998 and expanded in [Wiggins and McTighe (2005), *Understanding by Design*, Expanded 2nd ed., ASCD](https://www.ascd.org/books/understanding-by-design-expanded-2nd-edition). It is the standard curriculum-planning text in most U.S. teacher-preparation programs. The central move is *backward*: start with the long-term capability the student should hold, then design the evidence that would demonstrate the capability, then choose the activities that build it. Three stages. *Identify desired results. Determine acceptable evidence. Plan learning experiences.*

Most curriculum design is forward, not backward. Topics chosen, activities ordered, assessment grafted on at the end. The Wiggins & McTighe argument — and this is the part that matters for the platform — is that forward design *systematically produces engagement without underlying capability*. The student spends weeks on activities that feel substantive. At the end there is an assessment. The assessment tests what the activities covered, not what the student should be able to *do*. Pass rates are high because the assessment was built from the activities. Capability is invisible because the assessment was not built from the capability.

That second paragraph is the part most engineers are inclined to dismiss as soft talk. It is not soft talk. It is exactly the shape of the IDK-IDK problem one layer up. Khanmigo's Socratic prompt was activity-shaped: get the student to interact with the prompt. The assessment was engagement-shaped: did the student interact. The capability — *can the student now reason about this concept* — was never the design target, so it was not measured, so it did not happen at scale. Backward design is the discipline that prevents this at the curriculum layer.

Two more pieces of vocabulary, because the chapter cannot use these words without first specifying them.

*Bloom's revised taxonomy* is the canonical hierarchy of cognitive operations: Remember, Understand, Apply, Analyze, Evaluate, Create. The 2001 revision ([Anderson & Krathwohl 2001](https://lccn.loc.gov/00045446), Pearson) updated the 1956 original — Bloom's earlier *Knowledge, Comprehension, Application, Analysis, Synthesis, Evaluation* — by changing the verbs from nouns to gerunds, swapping the top two levels (Create now caps the hierarchy, not Evaluate), and splitting the taxonomy into a two-dimensional structure of cognitive process × knowledge type. The 2001 revision is what most current curriculum work uses; if you cite the original 1956 verbs, mark that you are doing so.

*Mode-appropriateness flags* are a Medhavy-specific term. They are the bits of the concept map that tell the engine which modes can sensibly be offered for this concept at this Bloom level. Quiz Me is approved for the substrate-table recall items at Remember level. Glimmer is *not* approved for that same Bloom level. Case Study is approved for the Apply-level outcome where the student predicts an interaction. The flags are the curriculum designer's judgment about pedagogical fit. The engine does not have that judgment; the curriculum designer has it.

---

## The Concept Map — What the Engine Consumes

A concept map is not a chapter outline. A chapter outline is a list of headings. A concept map is a *structured specification* of what the platform is supposed to teach, formatted as data the engine can read.

What it must contain, at minimum:

**Concept nodes.** Each node is one concept at the bandit-appropriate granularity. Concept granularity is a curriculum-design choice. The working heuristic: a concept is granular enough that a single Quiz Me item can probe it and a single Glimmer prompt can extend it; typically five to twenty concepts per chapter. *"Drug Metabolism"* is not a concept node; it is a topic header. *"The rate-limiting role of CYP3A4 in clinical drug interactions"* is a concept node. *"First-pass effect as a determinant of oral bioavailability"* is a concept node. The granularity question is real and the platform's default is unsettled; one of the *still puzzling* questions at the end of the chapter.

**Prerequisite dependencies.** Directed edges between concept nodes. The graph may be a clean directed acyclic graph (DAG) — every node has at most one upstream chain — or it may contain branching and convergence (the DAG case for any real discipline). Some disciplines contain genuine cycles where concepts mutually inform each other in iterative skill development; those should be tagged explicitly rather than ignored. The Chapter 7 bandit's *prerequisite mastery* context feature reads off this graph. A graph with missing edges is a graph whose context feature is wrong, and the engine's adaptation is wrong downstream of that.

**Bloom's level assignment.** One revised-Bloom level per concept node, sometimes per outcome statement — a single concept may have multiple outcomes at different levels (a Remember-level outcome about the substrate table and an Apply-level outcome about predicting interactions for a given patient).

**Mode-appropriateness flags.** A four-bit vector per concept node: Ask AI yes/no, Quiz Me yes/no, Case Study yes/no, Glimmer yes/no. The defaults follow the Bloom level (see the table below), but the curriculum designer can override on concept-specific grounds. The engine's exploration is bounded by these flags. Without them, the engine will explore into modes that are obviously inappropriate, which costs sessions.

**Outcome statements.** One or more per concept, framed as student-demonstrable performances at the right Bloom level. *"Predict the qualitative change in steady-state plasma concentration of warfarin when a strong CYP3A4 inhibitor is added"* is an outcome statement. *"Understand drug metabolism"* is a wish. The change in verb is the whole game. The seven-day delayed retrieval probe (Chapter 7) draws its items from the outcome statements.

**Assessment evidence specifications.** What a passing performance looks like — for Quiz Me, an item template with answer key and distractor logic; for Case Study, a scenario with rubric; for Glimmer, a rubric across the dimensions the platform scores (mechanism, specificity, integration, precision). The GLP-component scoring infrastructure (Chapter 5) needs these specifications to produce non-arbitrary scores.

Here is the default Bloom-to-mode mapping. **Treat it as a starting point, not a rigid rule.** Asterisks mark debated calls.

| Bloom level | Ask AI | Quiz Me | Case Study | Glimmer |
|---|---|---|---|---|
| Remember | yes | yes | no | no |
| Understand | yes | yes | yes* | no |
| Apply | yes | no | yes | no |
| Analyze | yes | no | yes | yes* |
| Evaluate | yes | no | yes | yes |
| Create | yes | no | no | yes |

The override pattern is concept-specific. A Remember-level concept whose factual answer is *clinically important enough to require scenario-anchored retrieval* — for example, the specific drugs that are absolute contraindications during pregnancy — may benefit from a Case Study override despite the Bloom level. An Apply-level concept whose foundation is fragile across the cohort may benefit from a Quiz Me override to reinforce the substrate first. The default table is the answer when there is nothing concept-specific to override it. The override is the curriculum designer's job, and writing the override down is part of the concept map.

One more thing the concept map must do, and it is the place the curriculum layer hands off to the mode layer. *Phase gates.* The gate is the rule that says "Quiz Me is locked on this concept until the section has been read; Glimmer is locked until Quiz Me retrievability is above threshold; Case Study is locked until prerequisites are mastered." Chapter 6 introduced phase gates as a feature of the mode layer. The curriculum layer is where the thresholds are specified per concept — because the threshold is a judgment about prerequisite cognitive state, and prerequisite cognitive state is what the curriculum designer is supposed to be expert in. **The gate's mechanism lives in the mode layer; the gate's threshold lives in the curriculum layer.** Keeping this separation clean is what keeps the two layers from leaking into each other.

The concept map is a *deliverable specification*, not a soft suggestion. A concept map missing prerequisite edges is *unusable* by the engine. A concept map without mode flags forces the engine to assume all modes are equally appropriate everywhere, which the Chapter 6 evidence base shows is false. Treating the concept map as a soft document — a starting point the platform will figure out the rest of — is exactly the *suggest 15 chapters* failure rebranded as competence.

---

## The Three Curriculum Design Failure Modes

The chapter has been circling them. Let me state them plainly and walk through the diagnostic for each.

### Topic coverage masquerading as capability

The most common failure. The curriculum designer has *listed* the content but has not *specified the capability*. The chapter titles read like a table of contents in an academic textbook. If outcomes are stated, the verbs are *know, understand, be familiar with, learn about*. The assessment evidence is multiple-choice on factual recall. The bandit converges to Quiz Me on every concept because Quiz Me is the only mode the curriculum supports.

The diagnostic is the verbs in the outcomes. *Know the major CYP450 isoforms* is topic coverage. *Predict the qualitative effect on warfarin INR when a CYP3A4 inhibitor is added* is capability. The change is not cosmetic; it shifts the entire downstream chain. The probe item the second outcome admits is qualitatively different from the multiple-choice substrate question the first one admits. The Bloom level is different. The mode flags shift. The phase gates change.

This is the failure mode Wiggins & McTighe diagnose at the head of *Understanding by Design*. It is the same failure mode John Hattie identifies in *Visible Learning* as the modal failure of classroom curriculum design. It is not new and it is not specific to AI platforms. AI platforms make it more dangerous because, when the curriculum is topic-coverage, the engine still appears to do something — and the appearance is what gets sold to the next district.

### Author-sequence overriding learner-sequence

The curriculum is ordered by *author logic* rather than *learner progression*. The sequence reflects the disciplinary structure of the field — historically, philosophically, taxonomically — rather than the sequence a novice can climb. Prerequisites are implicit in author headcanon (the curriculum designer "of course" knows biochemistry comes before pharmacology), but the prerequisite graph in the concept map does not encode the cross-discipline edges. The sequence is linear when the real prerequisite graph is a DAG; concepts that could be learned in parallel are forced sequential because chapters can only be ordered one way.

The diagnostic is to ask the curriculum designer to draw the prerequisite graph from memory, then compare it to the chapter sequence. If the graph is a chain — each concept has exactly one prerequisite, the previous concept — the curriculum is author-sequenced. Real concept maps in any rich discipline are DAGs with branching and convergence. Pharmacokinetics has prerequisites in biochemistry, physics, and clinical reasoning; structuring the curriculum as a chain forces the student to learn each prerequisite at the moment the author decided to mention it rather than at the moment they need it. The ALEKS system has worked from explicit prerequisite-graph traversal for two decades; the platform's adaptive engine reads ready-to-learn states from the graph rather than from the chapter order, and the [evidence base for ALEKS-style sequencing](https://www.aleks.com/k12/research) is consistent enough that the platform should not be re-inventing a chain when a DAG is available.

### Prerequisite gaps appearing as learner failure

The most diagnostically dangerous failure. The curriculum *has* a prerequisite graph, but the graph is missing edges. The student fails a downstream concept. The platform attributes the failure to the downstream concept. The engine doubles down on remediation in the downstream concept. The *real* problem is the missing prerequisite the student never mastered.

A specific pharmacology example: a student is failing warfarin-dosing case studies. The chapter on warfarin lists *drug absorption* and *drug metabolism* as prerequisites; the student has both. The missing prerequisite is *vitamin K cycle biochemistry*, which sits in the biochemistry textbook and was never encoded as a pharmacology prerequisite. The engine cannot adapt to a prerequisite gap it cannot see. The student looks like a learner who is failing warfarin. She is a learner who is missing vitamin K. The remediation she needs is upstream by two chapters and across a discipline boundary the concept map did not encode. The engine spends weeks doing the wrong thing because the curriculum's prerequisite graph was wrong by one edge.

The exercises at the end of the chapter ask the reader to *diagnose* this case — given platform logs, separate curriculum design failure from measurement failure from mode-fit failure from content failure. The diagnostic procedure: if the GLP signals are noisy or absent, suspect the measurement layer first. If the signals are clean and the engine has converged on a single mode that is not producing learning, suspect mode-fit. If the signals are clean, the engine has explored modes, and no mode produces learning gain, suspect either curriculum design (prerequisite gap, topic coverage, author sequence) or content (Chapter 9). Distinguish those last two by inspecting the concept map and the prerequisite trace for the learner. If the trace shows the student is failing only downstream of a specific concept that no upstream node points to, you have a prerequisite gap. If the trace shows the student is failing across multiple concepts that share content provenance — same author, same textbook section, same case study source — you have a content problem.

---

## Tic TOC — the Curriculum Design Instrument

Backward design is a methodology. It is not a tool. A methodology without a tool tends to slip back into forward design under deadline pressure. Tic TOC is the tool the platform names.

The name is a small joke that also turns out to be operational. *TOC* — the time-honored Table of Contents discipline of writing, the document every author produces and every editor reviews. *Tic* — iterative and timed. A structured tic of the design clock that refuses to advance until each stage has produced its deliverable. The two together name something the field needs more of: *a Table of Contents discipline that is iterative, structured, and refuses to skip stages*.

Tic TOC operates at three levels.

As a *structured intake*: a sequence of design conversations that produces a chapter specification (and, by extension, a book specification). The questions are small; the answers constrain the next questions. Who is this learner? What is the complexity threshold (Chapter 2 — does this learning problem actually warrant the full architecture, or is the answer simpler)? What is the four-layer specification — what does the measurement layer need to capture, what modes are the engine's arms, what does the curriculum look like, what content does it require? What is the economic envelope? What are the open bets — which decisions are evidence-based and which are bets the platform is going to learn from deployment?

As an *instrument*: Tic TOC is what *Medhavy the instrument* does, as distinct from *Medhavy the platform*. The instrument is the design conversation. The platform is what gets built from it. Chapter 12 returns to Tic TOC the instrument as its main subject; this chapter introduces it as the discipline behind the curriculum design layer. The instrument-platform distinction matters because the curriculum designer who works with the instrument well does not need to be the same person who works on the platform. The instrument is the shared language; the platform consumes the instrument's outputs.

As a *forcing function*: Tic TOC's discipline is to refuse to produce structure before the specification is complete. A Tic TOC session that ends at *suggest 15 chapters* without the outcome statements, prerequisite graph, Bloom levels, and mode flags is an *incomplete* session. The discipline is the instrument's value. Without the forcing function, the instrument becomes a brainstorm tool — useful, but no different from the existing genre of LLM-assisted outlining. With the forcing function, the instrument produces a buildable specification that a developer can configure from without a translation meeting.

Now the meta-move, and I want to be careful about it because it is the kind of move that is either the chapter's best paragraph or its gimmickiest.

*This book was produced through a Tic TOC session.*

The reading you have been doing since Chapter 1 is the methodology operating on itself. The intake questions: Chapter 1 — who is the failure mode for; Chapter 2 — what is the complexity threshold; Chapter 3 — what is the evidence base. The four-layer specification: Chapters 4 through 9, one layer per chapter, each one specified before the next is introduced. The economics check: Chapter 10. The open bets: Chapter 11. The design conversation as a deliverable: Chapter 12. Each chapter is a Tic TOC question. The book is a Tic TOC session that produced this specification for an intelligent textbook.

The claim is not that this is *the* canonical Tic TOC session. Other domains will produce different question sequences. The discipline is what generalizes — *do not advance to structure before the specification is complete* — not the specific sequence for this domain. The reader has been doing the work without knowing it. Naming the work at this point makes the work visible and gives the reader the capability to do it again on their own domain, which is the only reason for the meta-move to exist. If you cannot run a Tic TOC session on your own domain after reading this book, the book has failed. If you can, the meta-move has earned its place.

One more thing about Tic TOC, and it is the place where this chapter has to be honest about what the instrument is *not*. Tic TOC uses LLM assistance. The discipline is not "no LLM"; it is "*LLM scaffolds, human judges, output is a specification not a list*." The LLM produces candidate concepts, candidate outcomes, candidate prerequisite edges. The curriculum designer accepts, rejects, refines each candidate. The output of the session contains only human-judged elements. This is the same boundary the book argues for at the content layer (Chapter 9). Naming it consistently across chapters is part of why the book is built the way it is.

---

## Worked Example — Warfarin, Done Wrong and Done Right

The case that runs through this chapter: a chapter in a pharmacology textbook on *CYP3A4 inhibition and the warfarin / statin clinical-interaction class*. I will run the chapter specification two ways. The first is what the *suggest 15 chapters* tool produces, lightly accepted. The second is what backward design produces when the curriculum designer does the work.

### Version A — topic coverage

**Chapter title:** Drug Metabolism

**Outcome statement:** "Students will understand the major CYP450 isoforms and their substrates."

**Assessment evidence:** Multiple-choice questions on the substrate table — which drugs are metabolized by which isoforms.

**Prerequisite dependencies:** "Drug Absorption" (the previous chapter).

**Bloom level:** Not specified.

**Mode flags:** Not specified — defaults to all four enabled.

**Phase gates:** Not specified.

What the engine receives: a chapter title, a list of substrates, a quiz that maps drugs to isoforms. The engine can run Quiz Me — there are items to draw from. It cannot meaningfully run Case Study (no scenario specification, no rubric). It cannot meaningfully run Glimmer (no rubric). Ask AI will work for any clarification request the student makes, but with no outcome target, the Ask AI session has no quality signal. The bandit, exploring all four modes, will quickly converge on Quiz Me because that is the only mode the curriculum supports — and even so, what it is reinforcing is substrate-table recall, not the capability the chapter is supposed to produce.

What the student learns: the substrate table. The student passes the chapter. The student fails the warfarin case study in the clinical reasoning chapter three weeks later, because passing the substrate table did not produce the capability to *predict an interaction*. The system logs the warfarin failure as a downstream-concept failure. The engine starts remediating the warfarin chapter. The real problem is upstream by two chapters and one outcome verb.

### Version B — backward design

**Chapter title:** Predicting CYP3A4-Mediated Clinical Interactions

**Outcome statements:**
- *(Apply.)* "Given a patient on warfarin and a list of co-prescribed drugs, the student will predict which co-prescription is most likely to produce a clinically significant change in INR and explain the mechanism in terms of CYP3A4 substrate specificity and vitamin K cycle pharmacodynamics."
- *(Analyze.)* "Given the same scenario plus a measured INR change after a co-prescription, the student will distinguish a CYP3A4-mediated mechanism from a competing mechanism (e.g., displacement from albumin binding) using the time course and the magnitude of the INR change."

**Assessment evidence:**
- For the Apply outcome: a scenario-based clinical question, with rubric: identification of the interacting drug pair (binary), explanation of the mechanism (3-point: substrate specificity, INR direction, vitamin K cycle linkage), and clinical-significance prediction (3-point: magnitude, time course, monitoring recommendation).
- For the Analyze outcome: a paired scenario where the differential is between two mechanism candidates, rubric weighted toward time-course reasoning.

**Prerequisite dependencies:**
- *Within pharmacology:* CYP3A4 substrate specificity (Apply-level concept node in the chapter on drug metabolism). Therapeutic index of warfarin (Understand-level node in the chapter on dose-response).
- *Cross-discipline:* Vitamin K cycle biochemistry (Apply-level node in the biochemistry book). Albumin binding and free-drug pharmacology (Understand-level node in physiology).

The cross-discipline edges are encoded. The graph is not a chain.

**Bloom level:** Apply, with Analyze-tagged extension exercises.

**Mode flags:**
- Quiz Me: yes — for substrate facts and INR-direction recall.
- Ask AI: yes — for prerequisite rescue (the student who has forgotten the vitamin K cycle can request a clarification).
- Case Study: yes — for application of the mechanism to clinical scenarios.
- Glimmer: yes (Analyze extension) — for novel patient-design scenarios where the student constructs the scenario.

**Phase gates:**
- Quiz Me: gated until the section has been read (Y1 temporal engagement threshold).
- Case Study: gated until Quiz Me retrievability on substrate facts is above threshold (~0.8) *and* prerequisite mastery on vitamin K cycle is above threshold.
- Glimmer (Analyze extension): gated until at least two Case Study scenarios have been completed at proficiency level.

What the engine receives: a concept map node with five prerequisite edges (two within-pharmacology, three cross-discipline), two outcome statements at two Bloom levels, mode flags justified by the Bloom levels, phase gates specified per mode, and an assessment evidence specification rich enough to drive both the GLP-component scoring and the seven-day retrieval probe.

What the engine can do: run Quiz Me for the substrate recall while the section is being read; once retrievability is up, unlock Case Study; Case Study produces Y3 (cross-context transfer) and Y6 (retrieval strength decay) data that the bandit reads back into its reward signal; once two Case Studies are at proficiency, unlock the Glimmer extension that probes the Analyze-level distinction between mechanisms. The bandit's adaptation is bounded by the curriculum's judgment, which is exactly what makes the adaptation cheap and the early sessions productive rather than exploratory.

What the student learns: not the substrate table in isolation. The substrate table is still there — the Quiz Me items haven't gone anywhere — but it is connected to a clinical capability the student is now producing repeatedly under scaffolded variation. Three weeks later, when the warfarin scenario shows up in the clinical reasoning chapter, the student has done it a dozen times. The downstream chapter does not look downstream anymore. It looks like the chapter where the capability gets exercised in a new context — which is what an integrated curriculum is supposed to feel like.

The same content, two specifications, two different engines, two different student outcomes. The data the platform collects looks completely different from one version to the other. **The bandit is doing the same algorithm. What changed is what the bandit was told the algorithm was for.**

A note on the example: the structural argument generalizes. A statistics chapter on the Central Limit Theorem has the same shape — *understand the CLT* is topic coverage; *given a sample mean and population variance, compute the 95% confidence interval for the population mean and justify the CLT's applicability* is backward design. An engineering chapter on beam deflection: *know how beams deflect* is topic coverage; *given a simply supported beam and a load distribution, compute the maximum deflection and identify two failure modes the deflection calculation does not predict* is backward design. The pharmacology case is the worked example in this chapter; the structural move is portable.

---

## Common Misconceptions

**"Backward design just means writing outcomes first."**

Writing outcomes first is the *easy* part. The hard part is making the outcomes specific enough to determine the assessment evidence, and making the assessment evidence specific enough to determine the activity choice. *Students will understand the Central Limit Theorem* is an outcome written first; it does not determine an assessment or an activity. *Students will compute a 95% confidence interval given a sample mean and justify the CLT's applicability* determines the assessment (give them a sample mean, ask for the CI and a justification) and the activity (the practice problems that build the capability). Writing outcomes first without the discipline of *then asking what evidence would demonstrate the outcome* slides back into topic coverage with new vocabulary.

**"The concept map is just an index."**

An index lists topics. A concept map encodes prerequisites, Bloom levels, mode flags, outcomes, and assessment specifications. An index lets a reader find a topic. A concept map lets an engine adapt. They are different documents that share some surface vocabulary; treating them as interchangeable is the conceptual error behind the *suggest 15 chapters* failure.

**"The LLM can produce the concept map."**

The LLM can produce a draft, and a curriculum designer with strong domain expertise and explicit specifications can use that draft as a starting point. The LLM cannot produce the *judgment* — what counts as a concept at this granularity, what counts as mastery for this concept, which mode this concept admits, which prerequisite edges cross disciplines. The judgment is what makes the concept map *usable by the engine*; the draft without the judgment is exactly the failure the chapter opens with. This is bet #7 in the open-bets list. The boundary will move as LLM capability improves; the test for whether the boundary has moved is whether LLM-produced concept maps deliver equivalent engine downstream performance to expert-produced maps. That test has not yet been run at scale.

**"Phase gates are pedagogical paternalism."**

Phase gates are a measurement decision before they are a pedagogical decision. The reason Quiz Me is gated until the section has been read is not that the platform wants to control the student's reading order. It is that a Quiz Me attempt before reading produces no meaningful Y1 (temporal engagement) signal — the student has not had the chance to engage with the content, so the engagement pattern is not measurable. The gate exists so that the measurement layer's reward signal is interpretable. The pedagogy follows from the measurement.

**"Author expertise is enough."**

A practicing pharmacologist with twenty years of teaching is genuinely expert at pharmacology. She is not, typically, expert at curriculum design — the explicit specification of outcomes, prerequisite graphs, Bloom-level mapping, mode-appropriateness flags. That is a different skill, and most academic training does not teach it. Tic TOC is a tool to extract the curriculum specification from the domain expert by asking the questions the domain expert may not have explicit answers to until they are asked. The expertise is the input. The discipline of converting expertise into specification is the work the instrument exists to do.

---

## Exercises

### Warm-up

**1.** Take the outcome statement *"Students will understand exponential growth."* Identify three different Bloom-level outcomes this sentence could be expanded into. For each, name what the assessment evidence would look like.

**2.** Distinguish between a *topic*, a *concept*, and an *outcome*, in your own words. Give one example of each, drawn from a domain you know.

### Application

**3.** *(Apply.)* The chapter argues that the concept map needs prerequisite edges that cross disciplines. Pick a topic from your own field that depends on a prerequisite in a different discipline. Specify the cross-discipline edge (where the prerequisite lives, what its Bloom level is, what mastery threshold the focal concept requires). Explain what the engine would do wrong if the cross-discipline edge were not encoded.

**4.** *(Analyze; producing.)* You are handed the platform logs for a student who is failing a deployed intelligent textbook's Chapter 7. The logs show: high engagement (Y1 strong), low cross-context transfer (Y3 weak), normal retrieval decay (Y6 normal for the chapter's content), and the engine has explored all four modes without finding one that produces gain. Diagnose the failure. Specify your reasoning path: which of the failure modes (curriculum design, measurement, mode-fit, content) you have ruled out, and which one remains. What is the next diagnostic action you would take?

### Synthesis — producing exercise

**5.** *(Create.)* Produce a chapter specification for a single chapter in a discipline you know well. Include: chapter title, three to five outcome statements at Apply level or above with their Bloom-level tags, a prerequisite dependency map with at least five concept nodes and no broken chains, mode-appropriateness flags justified by Bloom level, and phase-gate logic for each mode. Length: 600–900 words. The deliverable should be detailed enough that another reader could read it and configure an adaptive engine without asking you questions.

### Challenge

**6.** *(Evaluate.)* The chapter draws a boundary between LLM-scaffolded curriculum design (helpful) and LLM-generated curriculum design (the *suggest 15 chapters* failure). Propose a test that would distinguish them empirically. The test should describe a specific deployment comparison: what would be measured, on which learners, over what time period, and what result would count as the LLM-produced specification matching the expert-produced specification on engine downstream performance. Be honest about what the test would *not* settle — the failure modes the test would not catch even if the LLM-produced specification appeared equivalent on the test's metrics.

---

## What Would Change My Mind

A documented case of a Medhavy deployment where the curriculum design layer was *omitted* — the engine ran on author-suggested chapter titles only, no concept map, no Bloom levels, no mode flags — and the platform still produced measurable learning gains comparable to a curriculum-specified deployment. That would argue the curriculum layer is over-engineered, that the engine is robust to underspecification, and that the discipline this chapter argues for is a discipline only the deploying team should care about. The bet is that this won't happen; the bet is also testable.

Alternatively: a documented case showing that LLM-generated curriculum specifications — produced with explicit instructions, but without expert review — match expert-designed specifications on engine downstream performance. That would shift the boundary between LLM-as-scaffold and LLM-as-author, and would change the AI-generation policy the next chapter spells out for the content layer.

A third: a randomized comparison of backward-design and topic-coverage curricula on a Medhavy deployment showing no significant six-month GLP score difference. That would force re-examination of the Wiggins & McTighe claim — that backward design produces durably different outcomes — at least in the specific case of an intelligent-textbook deployment. The chapter would still hold that *specification* matters; only the claim about *which kind of specification* would change.

---

## Still Puzzling

The concept-granularity problem. What is the right granularity for a concept node? Too coarse, the bandit cannot adapt. Too fine, the curriculum designer is producing 200 nodes per chapter, and Tic TOC sessions take a week instead of an afternoon. The literature does not specify the right answer. Different production systems — ASSISTments, ALEKS, Carnegie Learning — operate at different granularities. The Medhavy default is unsettled.

The cross-discipline prerequisite problem. The pharmacology example needs biochemistry prerequisites. The biochemistry curriculum lives in a different book. How does the prerequisite graph extend across books in the platform? Technically the [Medhavi Hub architecture](#) supports cross-book prerequisite encoding, but the curriculum-design discipline for *deciding* the cross-book edges — who owns the decision, how the edges get audited when a downstream book is updated — is not yet specified. This is an organizational question the platform's first multi-book deployment will have to answer.

The LLM-as-scaffold boundary. Where exactly is the line between LLM-scaffolded curriculum design (helpful) and LLM-generated curriculum design (the *suggest 15 chapters* failure)? The chapter draws a line. The line will move as LLM capability improves. What is the test that distinguishes scaffold from author, deployment by deployment? The chapter offers heuristics; a sharper test is not yet specified.

The phase-gate calibration problem. The phase gates require thresholds — Quiz Me retrievability at 0.8 unlocks Glimmer, for instance. Where does 0.8 come from? It is an empirical question the platform has not yet answered at scale. Bet #5 in the open-bets list addresses scaffolding fading; the phase-gate threshold is the same family of empirical question. The first cohort's data will start to answer it.

---

## Chapter Closing / Bridge to Chapter 9

The curriculum design layer produces the specification. The engine consumes the specification. The measurement layer probes whatever the specification points to. The mode layer offers what the specification's flags allow. All four layers are now in place — except for one. The specification points to *content*: the substrate text, the worked examples, the case scenarios, the Quiz Me items, the Glimmer rubrics. The substrate has to exist before any of this loop produces learning.

The content layer is the one most authors want to start with. Content is what an author has. Content is what an author knows. Content is what an author's reputation rests on. The next chapter is the one that says: content is the *last* of the four layers in this book, and on purpose. The discipline that protects against the *suggest 15 chapters* failure at the curriculum layer has an analog at the content layer — and AI generation, at the moment, has changed what is economically possible without changing what is pedagogically sound.

That asymmetry is the next chapter's subject.

---

*Suggested next chapter: 9 — The Content Layer.*
