# Chapter 9 — The Curriculum Design Layer

*The engine cannot learn from a specification that was never made.*

---

An author opens a design tool. She is a practicing pharmacologist with twenty years of teaching and a book contract. She types into the prompt: *"Suggest 15 chapters for a medical school pharmacology textbook."*

The model produces fifteen plausible-sounding titles. *Drug Absorption. Distribution and Protein Binding. Drug Metabolism. Drug Elimination. Pharmacodynamics. Receptor Theory. Dose-Response Relationships. Drug-Drug Interactions. Adverse Drug Reactions. Special Populations.* And so on. They are plausible. They are the standard topics. The author accepts. The tool offers to scaffold each chapter; she accepts that too. Two hours later she has an outline that looks like a book.

What she does not have, and the platform does not have, is a concept map the adaptive engine can use.

The chapter titles are topics, not concepts. There are no outcome statements. There are no prerequisite dependencies — *Drug Metabolism* depends on something, but the outline does not say what. There are no Bloom-level assignments: does the student need to *remember* the major CYP450 isoforms, or to *apply* her knowledge of CYP3A4 substrate specificity to predict a clinically significant interaction? Those are different learning goals requiring different modes. There are no mode-appropriateness flags telling the engine which modes are sensible for which concepts. The phase gates — when a Glimmer becomes available, when a Case Study unlocks — are nowhere in the document because the document contains no specification of cognitive state.

The engine reads the chapter titles. It tries to schedule modes. The Quiz Me retrieval probe has no specific items to draw from. The Case Study has no scenario. The Glimmer has no rubric; whatever the student produces, the system has no basis to score it. The student gets sessions that feel adaptive — modes are being chosen, content is being generated — but the sessions are not aligned to a capability target because no capability target was specified. She passes the Quiz Me items. She cannot answer a clinical question about warfarin metabolism. The system logs her as engaged.

This is the IDK-IDK failure from Chapter 1 at a different layer. There, the failure was at the mode level — the Socratic prompt did not enforce the discipline the mode required. Here, the failure is at the curriculum level — the concept map did not specify the capability the engine was supposed to help the student build. The failure mode is recursive. Every layer can produce the same shape of failure, and the architecture has to specify the discipline at every layer.

The discipline at this layer has a name: backward design.

---

## What the Engine Cannot Learn from a Bad Map

Before getting to the methodology, I want to be precise about what specifically goes wrong downstream when the curriculum layer is underspecified. Chapter 8 established that the engine is a contextual bandit whose arms are modes and whose reward is a learning signal. Take each of those words and ask: what does the curriculum layer have to supply for the engine to do its work?

**Arms.** The four modes are not equally appropriate for every concept. Quiz Me retrieval practice produces durable storage on Remember and Understand-level material. Case Study produces transfer on Apply and Analyze-level concepts. Glimmer produces generative integration on Evaluate and Create-level material. If the curriculum does not tell the engine which modes are sensible for the concept, the engine has to *learn it* from outcome data — which means the early sessions are wasted on confirming what the curriculum designer could have specified up front. Bandit budget spent on rediscovering pedagogy is bandit budget not spent on learning per-learner adaptation.

**Reward.** The reward signal is partly composed of a delayed retrieval probe — a Quiz Me item offered seven days after the mode-decision session. The probe items have to exist. Someone has to write them, calibrated to the outcome the concept is supposed to produce. If the curriculum says "Understand Drug Metabolism" — a verb so soft it does not specify what the student should be able to do — there is no clean way to write the probe. A probe drawn from the substrate table tests Remember. A probe asking the student to predict an interaction tests Apply. The curriculum's outcome verb decides which is appropriate. With a soft verb, the probe-writer guesses, and the engine's reward signal is now an artifact of that guess.

**Context.** The engine's context vector includes prerequisite mastery — the mean retrievability across all upstream concepts in the prerequisite graph. If the prerequisite graph is incomplete, the context vector is wrong. A student failing the focal concept because of a missing upstream concept looks, to the engine, like a student failing the focal concept. The engine doubles down on remediation in the focal concept. The real problem is a missing prerequisite no one encoded.

**Exploration constraints.** Bandit exploration is bounded by the mode-appropriateness flags. Without flags, every mode is in every arm, all the time, and the engine explores into modes that are obviously wrong for the concept — Glimmer on a foundational Remember-level concept, Quiz Me as the only tool for an Apply-level interaction-prediction outcome. The flags are the curriculum designer's judgment that some modes are not worth trying here. When the engine has to relearn that judgment from scratch, it costs sessions.

In each case, the missing curriculum-layer specification does not crash the engine. It silently degrades the engine's learning. The platform looks adaptive. What it is doing is rediscovering, slowly and noisily, what the curriculum designer could have stated cleanly up front.

| component name | what the curriculum layer must supply | what happens when it's missing | cost of the omission — reader should see the four silent degradation paths side by side | understand that none of them crash the engine |
| --- | --- | --- | --- | --- |
| row per bandit component (Arms, Reward, Context, Exploration constraints | Use the chapter example as the concrete test case. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |

---

## Backward Design — Two Paragraphs

*Understanding by Design* is the framework Grant Wiggins and Jay McTighe published in 1998 and expanded in 2005. It is the standard curriculum-planning text in most US teacher-preparation programs. The central move is backward: start with the long-term capability the student should hold, then design the evidence that would demonstrate the capability, then choose the activities that build it. Three stages. Identify desired results. Determine acceptable evidence. Plan learning experiences.

Most curriculum design is forward, not backward. Topics chosen, activities ordered, assessment grafted on at the end. The Wiggins and McTighe argument — and this is the part that matters for the platform — is that forward design systematically produces engagement without underlying capability. The student spends weeks on activities that feel substantive. At the end there is an assessment. The assessment tests what the activities covered, not what the student should be able to *do*. Pass rates are high because the assessment was built from the activities. Capability is invisible because the assessment was not built from the capability.

That second paragraph is what most engineers are inclined to dismiss as soft talk. It is not soft talk. It is exactly the shape of the IDK-IDK problem one layer up. Khanmigo's Socratic prompt was activity-shaped. The assessment was engagement-shaped. The capability was never the design target, so it was not measured, so it did not happen at scale. Backward design is the discipline that prevents this at the curriculum layer.

Two pieces of vocabulary the chapter will use.

*Bloom's revised taxonomy* — the 2001 revision by Anderson and Krathwohl of Bloom's 1956 hierarchy — orders cognitive operations as: Remember, Understand, Apply, Analyze, Evaluate, Create. The revision changed the nouns to gerunds, swapped the top two levels (Create now caps the hierarchy), and added a two-dimensional structure of cognitive process crossed with knowledge type. The 2001 verbs are what current curriculum work uses; the original 1956 nouns are a different document.

![The revised Bloom's taxonomy as a two-column comparison](images/09-the-curriculum-design-layer-fig-01.png)
*Figure 9.1 — The revised Bloom's taxonomy as a two-column comparison*

*Mode-appropriateness flags* are the bits of the concept map that tell the engine which modes can sensibly be offered for a given concept at a given Bloom level. Quiz Me is approved for substrate-table recall at Remember level. Glimmer is not approved for that same level. Case Study is approved for the Apply-level outcome where the student predicts an interaction. The flags are the curriculum designer's judgment about pedagogical fit. The engine does not have that judgment. The curriculum designer does.

---

## The Concept Map — What the Engine Consumes

A concept map is not a chapter outline. A chapter outline is a list of headings. A concept map is a structured specification of what the platform is supposed to teach, formatted as data the engine can read.

What it must contain, at minimum:

**Concept nodes.** Each node is one concept at the bandit-appropriate granularity. The working heuristic: a concept is granular enough that a single Quiz Me item can probe it and a single Glimmer prompt can extend it — typically five to twenty concepts per chapter. *Drug Metabolism* is not a concept node; it is a topic header. *The rate-limiting role of CYP3A4 in clinical drug interactions* is a concept node. *First-pass effect as a determinant of oral bioavailability* is a concept node.

**Prerequisite dependencies.** Directed edges between concept nodes. The graph will be a DAG — directed acyclic graph — not a chain. Some disciplines contain genuine iterative cycles where concepts mutually inform each other; those should be tagged explicitly rather than ignored. The engine's prerequisite mastery context feature reads off this graph. A graph with missing edges gives the engine a wrong context vector, and the engine's adaptation is wrong downstream of that.

**Bloom's level assignment.** One revised-Bloom level per concept node, sometimes per outcome statement — a single concept may have multiple outcomes at different levels.

**Mode-appropriateness flags.** A four-bit vector per concept node: Ask AI yes/no, Quiz Me yes/no, Case Study yes/no, Glimmer yes/no. The defaults follow the Bloom level. The curriculum designer can override on concept-specific grounds. Without flags, the engine assumes all modes are equally appropriate everywhere — which the Chapter 7 evidence base shows is false.

**Outcome statements.** One or more per concept, framed as student-demonstrable performances at the right Bloom level. *Predict the qualitative change in steady-state plasma concentration of warfarin when a strong CYP3A4 inhibitor is added* is an outcome statement. *Understand drug metabolism* is a wish. The change in verb is the whole game. The seven-day delayed retrieval probe draws its items from the outcome statements.

**Assessment evidence specifications.** What a passing performance looks like — for Quiz Me, an item template with answer key and distractor logic; for Case Study, a scenario with rubric; for Glimmer, a rubric across the dimensions the platform scores. The GLP-component scoring infrastructure needs these specifications to produce non-arbitrary scores.

Here is the default Bloom-to-mode mapping. Treat it as a starting point, not a rigid rule:

| Bloom level | Ask AI | Quiz Me | Case Study | Glimmer |
|---|---|---|---|---|
| Remember | yes | yes | no | no |
| Understand | yes | yes | yes* | no |
| Apply | yes | no | yes | no |
| Analyze | yes | no | yes | yes* |
| Evaluate | yes | no | yes | yes |
| Create | yes | no | no | yes |

*Asterisks mark debated calls where concept-specific context often drives the override.*

![The concept map node as a data structure](images/09-the-curriculum-design-layer-fig-02.png)
*Figure 9.2 — The concept map node as a data structure*

One more element: phase gates. The gate is the rule that says "Quiz Me is locked on this concept until the section has been read; Glimmer is locked until Quiz Me retrievability is above threshold; Case Study is locked until prerequisites are mastered." The gate's mechanism lives in the mode layer. The gate's threshold lives in the curriculum layer — because the threshold is a judgment about prerequisite cognitive state, and prerequisite cognitive state is what the curriculum designer is supposed to be expert in.

The concept map is a deliverable specification, not a soft suggestion. A concept map missing prerequisite edges is unusable by the engine. A concept map without mode flags forces the engine to assume all modes are equally appropriate everywhere. Treating the concept map as a starting point the platform will figure out the rest of — is exactly the *suggest 15 chapters* failure rebranded as competence.

---

## The Three Failure Modes

**Topic coverage masquerading as capability.** The most common failure. The curriculum designer has listed the content but not specified the capability. The verbs in the outcomes are *know, understand, be familiar with, learn about*. The assessment is multiple-choice on factual recall. The bandit converges to Quiz Me on every concept because Quiz Me is the only mode the curriculum supports.

The diagnostic is the verbs. *Know the major CYP450 isoforms* is topic coverage. *Predict the qualitative effect on warfarin INR when a CYP3A4 inhibitor is added* is capability. The change is not cosmetic. It shifts the probe item, the Bloom level, the mode flags, and the phase gates. Wiggins and McTighe identify this as the modal failure of classroom curriculum design. Hattie identifies the same failure in *Visible Learning*. AI platforms make it more dangerous because, when the curriculum is topic-coverage, the engine still appears to do something — and the appearance is what gets sold to the next institution.

**Author-sequence overriding learner-sequence.** The curriculum is ordered by author logic rather than learner progression. The sequence reflects the disciplinary structure of the field — historically, philosophically, taxonomically — rather than the sequence a novice can climb. Prerequisites are implicit in the author's headcanon but the prerequisite graph in the concept map does not encode the cross-discipline edges. The sequence is linear when the real prerequisite graph is a DAG.

The diagnostic: ask the curriculum designer to draw the prerequisite graph from memory, then compare it to the chapter sequence. If the graph is a chain — each concept has exactly one prerequisite, the previous concept — the curriculum is author-sequenced. Real concept maps in any rich discipline are DAGs with branching and convergence. Pharmacokinetics has prerequisites in biochemistry, physics, and clinical reasoning; structuring the curriculum as a chain forces the student to encounter each prerequisite at the moment the author decided to mention it, rather than at the moment she needs it.

**Prerequisite gaps appearing as learner failure.** The most diagnostically dangerous failure. The curriculum has a prerequisite graph, but the graph is missing edges. The student fails a downstream concept. The platform attributes the failure to the downstream concept. The engine doubles down on remediation there. The real problem is the missing prerequisite no one encoded.

A specific example: a student fails warfarin-dosing case studies. The chapter on warfarin lists *drug absorption* and *drug metabolism* as prerequisites; the student has both. The missing prerequisite is vitamin K cycle biochemistry, which sits in the biochemistry textbook and was never encoded as a pharmacology prerequisite. The engine cannot adapt to a prerequisite gap it cannot see. The student looks like a learner who is failing warfarin. She is a learner who is missing vitamin K. The remediation she needs is upstream by two chapters and across a discipline boundary the concept map did not encode.

The diagnostic procedure: if GLP signals are noisy or absent, suspect the measurement layer first. If the signals are clean and the engine has converged on a single mode that is not producing gain, suspect mode-fit. If signals are clean, modes have been explored, and no mode produces learning gain, suspect curriculum design or content. Distinguish those last two by inspecting the prerequisite trace. If the student is failing only downstream of a specific concept that no upstream node points to, there is a prerequisite gap. If the student is failing across multiple concepts that share content provenance, there is a content problem.

![Failure-mode diagnostic flowchart ](images/09-the-curriculum-design-layer-fig-03.png)
*Figure 9.3 — Failure-mode diagnostic flowchart *

---

## Tic TOC — The Curriculum Design Instrument

Backward design is a methodology. It is not a tool. A methodology without a tool tends to slip back into forward design under deadline pressure. Tic TOC is the tool the platform names.

The name is operational. *TOC* — the Table of Contents discipline every author produces and every editor reviews. *Tic* — iterative and timed. A structured tic of the design clock that refuses to advance until each stage has produced its deliverable. Together they name something the field needs: a Table of Contents discipline that is iterative, structured, and refuses to skip stages.

Tic TOC operates at three levels.

As a *structured intake*: a sequence of design conversations that produces a chapter specification and, by extension, a book specification. The questions are small; the answers constrain the next questions. Who is this learner? What is the complexity threshold — does this learning problem actually warrant the full architecture, or is the answer simpler (Chapter 3)? What is the four-layer specification — what does the measurement layer need to capture, what modes are the engine's arms, what does the curriculum look like, what content does it require? What are the open bets — which decisions are evidence-based and which are bets the platform will learn from deployment?

As an *instrument*: Tic TOC is what Medhavy the instrument does, as distinct from Medhavy the platform. The instrument is the design conversation. The platform is what gets built from it. The curriculum designer who works with the instrument well does not need to be the same person who works on the platform. The instrument is the shared language; the platform consumes the instrument's outputs.

As a *forcing function*: Tic TOC's discipline is to refuse to produce structure before the specification is complete. A Tic TOC session that ends at *suggest 15 chapters* without outcome statements, prerequisite graph, Bloom levels, and mode flags is an incomplete session. Without the forcing function, the instrument becomes a brainstorm tool — useful, but no different from existing LLM-assisted outlining. With it, the instrument produces a buildable specification that a developer can configure from without a translation meeting.

Now the meta-move. I want to be careful about it because it is the kind of move that is either the chapter's best paragraph or its gimmickiest.

*This book was produced through a Tic TOC session.*

The reading you have been doing since Chapter 1 is the methodology operating on itself. The intake questions: Chapter 1 — who is the failure mode for. Chapter 3 — what is the complexity threshold. Chapter 4 — what is the evidence base. The four-layer specification: Chapters 5 through 10, one layer per chapter, each specified before the next is introduced. The economics check: Chapter 11. The open bets: Chapter 12. The design conversation as a deliverable: Chapter 13. Each chapter is a Tic TOC question. The book is a Tic TOC session that produced a specification for an intelligent textbook.

The claim is not that this is *the* canonical Tic TOC session. Other domains will produce different question sequences. The discipline is what generalizes — do not advance to structure before the specification is complete — not the specific sequence for this domain. The reader has been doing the work without knowing it. Naming it at this point makes the work visible and gives the reader the capability to run a Tic TOC session on their own domain. That is the only reason for the meta-move to exist. If you cannot run the session yourself after reading this book, the book has failed.

One more thing about Tic TOC: it uses LLM assistance. The discipline is not "no LLM." It is "LLM scaffolds, human judges, output is a specification not a list." The LLM produces candidate concepts, candidate outcomes, candidate prerequisite edges. The curriculum designer accepts, rejects, refines each candidate. The output contains only human-judged elements. This is the same boundary the book argues for at the content layer in Chapter 10. The boundary is stated consistently across chapters because the argument is the same.

![Tic TOC session flow as a loop ](images/09-the-curriculum-design-layer-fig-04.png)
*Figure 9.4 — Tic TOC session flow as a loop *

---

## Warfarin, Done Wrong and Done Right

The same chapter specification, two ways. The case is a pharmacology chapter on CYP3A4 inhibition and the warfarin-statin clinical-interaction class.

**Version A — topic coverage.**

Chapter title: Drug Metabolism. Outcome statement: "Students will understand the major CYP450 isoforms and their substrates." Assessment evidence: multiple-choice questions on the substrate table. Prerequisite dependencies: "Drug Absorption" (the previous chapter). Bloom level: not specified. Mode flags: not specified — defaults to all four enabled. Phase gates: not specified.

What the engine receives: a chapter title, a list of substrates, quiz items mapping drugs to isoforms. The engine can run Quiz Me. It cannot meaningfully run Case Study — no scenario, no rubric. It cannot meaningfully run Glimmer — no rubric. The bandit, exploring all four modes, converges quickly on Quiz Me because that is the only mode the curriculum supports. What it reinforces is substrate-table recall, not the capability the chapter was supposed to produce.

What the student learns: the substrate table. She passes the chapter. Three weeks later, she fails the warfarin case study in the clinical reasoning chapter. The system logs the failure as a downstream-concept failure. The engine starts remediating the warfarin chapter. The real problem is upstream by two chapters and one outcome verb.

**Version B — backward design.**

Chapter title: Predicting CYP3A4-Mediated Clinical Interactions. Outcome statements: *(Apply)* Given a patient on warfarin and a list of co-prescribed drugs, predict which co-prescription is most likely to produce a clinically significant change in INR and explain the mechanism in terms of CYP3A4 substrate specificity and vitamin K cycle pharmacodynamics. *(Analyze)* Given the same scenario plus a measured INR change, distinguish a CYP3A4-mediated mechanism from a competing mechanism using the time course and the magnitude of the INR change.

Prerequisite dependencies: within pharmacology, CYP3A4 substrate specificity (Apply-level) and therapeutic index of warfarin (Understand-level). Cross-discipline: vitamin K cycle biochemistry (Apply-level, biochemistry textbook) and albumin binding and free-drug pharmacology (Understand-level, physiology). The cross-discipline edges are encoded. The graph is not a chain.

![The Version B prerequisite DAG ](images/09-the-curriculum-design-layer-fig-05.png)
*Figure 9.5 — The Version B prerequisite DAG *

Mode flags: Quiz Me yes for substrate facts and INR-direction recall. Ask AI yes for prerequisite rescue — the student who has forgotten the vitamin K cycle can request a clarification. Case Study yes for application of the mechanism to clinical scenarios. Glimmer yes at the Analyze extension for novel patient-design scenarios where the student constructs the scenario.

Phase gates: Quiz Me gated until the section has been read. Case Study gated until Quiz Me retrievability on substrate facts is above threshold *and* prerequisite mastery on vitamin K cycle is above threshold. Glimmer gated until at least two Case Study scenarios have been completed at proficiency.

What the engine receives: a concept map node with five prerequisite edges, two outcome statements at two Bloom levels, mode flags justified by those levels, phase gates specified per mode, and an assessment evidence specification rich enough to drive both the GLP-component scoring and the seven-day retrieval probe.

What the engine can do: run Quiz Me for substrate recall while the section is being read; once retrievability is up, unlock Case Study; Case Study produces Y3 (cross-context transfer) and Y6 (retrieval strength decay) data that the bandit reads back into its reward signal; once two Case Studies are at proficiency, unlock the Glimmer extension that probes the Analyze-level distinction between mechanisms. The bandit's adaptation is bounded by the curriculum's judgment — which is exactly what makes the adaptation cheap and the early sessions productive rather than exploratory.

What the student learns: not the substrate table in isolation. The substrate table is still there — the Quiz Me items haven't gone anywhere — but it is connected to a clinical capability the student is now producing repeatedly under scaffolded variation. Three weeks later, when the warfarin scenario shows up in the clinical reasoning chapter, the student has done it a dozen times. The downstream chapter does not look downstream anymore. It looks like the chapter where the capability gets exercised in a new context, which is what an integrated curriculum is supposed to feel like.

The same content. Two specifications. Two different engines. Two different student outcomes. The bandit is running the same algorithm in both cases. What changed is what the bandit was told the algorithm was for.

The structural argument generalizes. A statistics chapter on the Central Limit Theorem: *understand the CLT* is topic coverage; *given a sample mean and population variance, compute the 95% confidence interval for the population mean and justify the CLT's applicability* is backward design. An engineering chapter on beam deflection: *know how beams deflect* is topic coverage; *given a simply supported beam and a load distribution, compute the maximum deflection and identify two failure modes the deflection calculation does not predict* is backward design. The pharmacology case is the worked example. The structural move is portable.

---

## What the Conductor Reads

The conductor's score is the concept map. Without a score, a conductor can still wave her baton — sessions happen, modes get picked, dashboards register engagement — but there is no learning target specified, so no learning can be tested for. The curriculum design layer is what makes the conductor's work legible at all.

Three things the platform learns from this chapter that it does not learn from any other.

*The failure mode is recursive.* The IDK-IDK pattern is not specific to Khanmigo's Socratic prompt. It is the general shape of what happens when a layer in the architecture fails to specify its discipline. The mode layer can produce it; the curriculum layer can produce it; the content layer can produce it. The architecture has to be specified at every layer, and the discipline at this layer is backward design.

*The prerequisite graph is the most dangerous place to be incomplete.* A missing mode flag degrades adaptation efficiency. A missing outcome verb degrades probe quality. A missing prerequisite edge silently misdirects remediation onto the wrong concept for weeks. Of the things that can go wrong, missing prerequisite edges have the longest tail.

*The concept map is a bet, not a document.* Every prerequisite edge, every outcome statement, is a falsifiable prediction about what learners need and in what order. When the deployment data shows that students are failing Concept 7 because of an unspecified upstream gap, the conductor revises the prerequisite graph. The curriculum is not handed down from authority; it is held openly, tested against learner trajectories, and updated as the evidence accumulates.

That is the experiment-as-product posture from Chapter 1, applied one layer deeper. The concept map is the platform's working theory of the subject. The deployment is the test of the theory. The revisions are the science.
