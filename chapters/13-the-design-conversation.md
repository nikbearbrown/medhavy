# Chapter 13 — The Design Conversation

---

## Learning Objectives

By the end of this chapter, you will be able to:

1. **(Understand)** Explain why a "suggest 15 chapters" prompt produces unusable output — and what the tool requires from the human before it can produce a specification worth building from.
2. **(Apply)** Conduct the design conversation — the question-by-question process this book has modeled — that produces the inputs Medhavy needs.
3. **(Create)** Use Medhavy the instrument to produce a design map — complete specification of layers, modes, phase gates, measurement signals, and curriculum architecture — that can be handed to a developer without a translation meeting.
4. **(Evaluate)** Assess a Medhavy-generated specification for completeness: which layers are underspecified, which phase gates are missing, which measurement commitments are absent.

**Prerequisites:** Chapters 1–11. Everything before this.

**Skippable?** No. This is the chapter that converts everything you have read into something you can hand to a developer.

---

## Where this fits the conductor frame

This chapter primarily serves the instructor — the second of the three questions, in order — because the design conversation is what the instructor conducts with the tool to produce a specification a developer can build from. The learner is the eventual beneficiary; the organization is the eventual funder. But the chapter's load is on the instructor as the human who has to do the thinking the tool cannot do.

What this chapter specifies for the conductor is how the human conducts the conducting. Medhavy-the-instrument — the AI-and-domain-expert conversation — produces the specification that Medhavy-the-platform — the AI-and-student conversation — will then conduct against. Same shape of conversation, different domain. The instructor is conducting the design conversation in the way the conductor will later conduct the modes. The methodology compounds.

The chapter runs the experiment by making the design conversation itself the deliverable. The book has been operating with the methodology since Chapter 1; this chapter names it. The transparency move is structural: the same intake-before-architecture, evidence-before-specification, honest-inventory-before-the-map discipline that produced the four-layer architecture is the discipline the reader is now equipped to run on their own learning problem. A specification produced this way is a falsifiable commitment — phase gates, prerequisite chains, mode assignments — that the deployment will test. The instrument hands off to the platform, and the experiment continues in production.

---

## §1. The Meta-Move Named

This book is a Tic TOC session.

The reader has been experiencing the design conversation methodology since Chapter 1. Question by question. Intake before architecture. Evidence before specification. Honest inventory before the map. The only thing this chapter does is name it.

Chapter 1 opened with a failure — the IDK-IDK incident at Khanmigo — before any framework was introduced. Chapter 2 imposed the honest check — the complexity threshold test — before the architecture was delivered. Chapter 3 walked the evidence base before any architecture chapter could cite it. Chapters 4 through 10 delivered the four-layer architecture with evidence at every decision point, in the sequence that makes each layer comprehensible given what precedes it. Chapter 11 named the gaps in the language of the Montaigne *essai* — *que sais-je?* about the platform's own claims.

That sequence is the design conversation. The methodology is not a new instrument introduced in this chapter. It is the instrument the book has been operating with throughout. You have already done it. The architecture you now hold was produced by it. **The chapter is the naming of what you have been doing.**

Why this matters: a reader who learns the methodology by reading about it has acquired vocabulary. A reader who has *experienced* the methodology has acquired a capability. The latter is what the book has been building. This chapter is the moment the capability becomes nameable.

There is a second move embedded in the meta-move, and it dissolves a confusion I have been letting sit since Chapter 1. **Medhavy the platform and Medhavy the instrument are the same conversation in different domains.** The platform is the AI-and-student conversation about a concept. The instrument is the AI-and-domain-expert conversation about a curriculum. The shape of the question-by-question intake is the same. The output differs — student understanding in one case, buildable specification in the other.

That is why the book uses one name for two things. The two things share a structure. The structure is the conversation that produces a learning trajectory. The platform's trajectory ends with a student who can do something they could not do before. The instrument's trajectory ends with a specification a developer can build from.

---

## §2. Why the Tool Requires the Thinking

The failure mode this chapter teaches around is the one that opens Chapter 8. An author opens a design tool. They type:

> *"Suggest 15 chapters for a medical school pharmacology textbook."*

The tool produces 15 plausible-sounding chapter titles. The author accepts them. The adaptive engine now has a concept map with:

- No prerequisite dependencies — chapter 7 may require chapter 12 for any given concept.
- No learning-outcome statements — the chapters are *topics*, not *capabilities*.
- No phase-gate logic — the modes have nothing to gate on.
- No mode-appropriateness flags — Quiz Me vs. Glimmer vs. Case Study has no answer.

The engine is flying blind. The bandit can run, but it cannot learn — it has no structure to update against. The failure mode is silent: students engage, sessions log, dashboards look fine, and nothing has been learned.

**This is the IDK-IDK problem at the curriculum design layer.** A platform produced from "suggest 15 chapters" is a platform that will measure engagement as learning because there is nothing else for it to measure against.

### What the tool contributes

The tool's contribution is amplification of specification work that a domain expert is *already capable of producing* but would take days to write out. It reads the intake answers, infers the concept map structure, names the phase gates that would be coherent given the learning outcomes, flags the prerequisite chains, proposes the mode assignments, surfaces the measurement signals each phase gate would require, and produces the specification document in the format the developer needs.

### What the tool cannot do

The tool cannot generate the domain expert's understanding of what students get wrong. Sadler 2013 (Chapter 10, §2) is the empirical anchor. The most valuable input the domain expert brings is the *misconception map* — what students typically believe before instruction, what wrong answers they reach for, where the bottlenecks live in transfer. The LLM has training-data inferences about common misconceptions in well-documented subjects: Newtonian mechanics, Bayesian probability, photosynthesis. It does not have the domain expert's tacit knowledge of *this* population, *this* curriculum, *this* program's specific bottlenecks. That is the input the tool requires from the human — and the input it cannot produce on its own.

The cleanest framing: **the tool can produce the architecture but not the misconception map. The domain expert produces the misconception map and uses the tool to amplify it into the architecture.** That is the labor separation the chapter teaches.

### What "the thinking" consists of

The thinking the book provides — the input the tool requires — is the structured intake the design conversation conducts. Six moves:

1. **Learner profile.** One specific person, not a category.
2. **Complexity threshold check.** Does this learning problem warrant the full architecture, or is the right answer a simpler tool?
3. **Evidence audit.** What does the evidence say about how the target capability is built? Which design choices are evidence-supported and which are bets?
4. **Four-layer specification.** Content, curriculum design, adaptive engine, measurement — with the data each layer produces and receives.
5. **Economics check.** What audience size justifies the architecture at the available production budget?
6. **Honest inventory.** Adjacent evidence, direct evidence, design bet — per design decision.

These six moves are the design conversation. The Medhavy instrument conducts them as a question-by-question intake. The human (Charles Fadel type) provides the answers. The instrument produces the specification document the developer builds from. **The book has been training the reader to *do* these six moves since Chapter 1.**

---

## §3. Platform vs. Instrument — the Distinction That Makes Both Buildable

The distinction the chapter has to land:

- **Medhavy the platform** is what the developer builds. The four-layer architecture deployed at cancer.medhavy.com or physics.medhavy.com — the production system serving medical students or physics undergraduates with Ask AI + Quiz Me + Case Study + Glimmer + Video and Animation, instrumented by GLP measurement, optimized by the within-learner bandit.
- **Medhavy the instrument** is what the domain expert uses to produce the specification the developer builds from. The design conversation tool — the intake-driven session that walks the Charles Fadel type through learner profile, complexity threshold, evidence audit, four-layer specification, economics check, and honest inventory.

They share a name because they share a structure. **Both are conversations that produce learning trajectories.** The platform's conversation is between AI and student about a concept. The instrument's conversation is between AI and domain expert about a curriculum. The shape of the question-by-question intake is the same. The output differs.

### Why the distinction matters

A Charles Fadel type who confuses the platform with the instrument will commission the wrong thing. He will ask the developer to build "Medhavy" without specifying *which* Medhavy or what the specification is. The developer will build the platform without the specification, which produces the "suggest 15 chapters" output writ large — a platform with a concept map that no one designed for the learners actually being served.

A developer who confuses the platform with the instrument will build the platform and assume the design conversation will happen later, somewhere else, by someone else. That is the bolt-on failure of Chapter 4. **The design conversation does not happen later. It happens before the build or it does not happen at all.** A platform configured against an unspecified curriculum is the platform that cannot learn.

The chapter's move: name the distinction explicitly so both readers can recognize when they are asking the wrong question, and use the shared structure — intake → architecture → specification → deployment — to make the right question askable.

### What the implementation book holds

This book ends with the map, not the build. The *implementation* book — the book about turning the specification into deployed code — is a follow-up that does not exist yet. Chapter 12 hands the specification. The implementation book is about turning the specification into deployed code, and that is a separate project with separate scope.

---

## §4. How to Conduct the Design Conversation

This is the operational core. The reader must finish able to run the conversation themselves.

### 4.1 Intake questions

The intake's job is to surface the inputs the rest of the conversation needs.

- *Who is the learner?* One specific person, not a category. Age. Prior knowledge. Prior misconceptions. Current capability gap. Motivation type (academic credential, professional qualification, intellectual project). Institutional context (credentialing, executive education, K-12, homeschool, microschool).
- *What capability are they being built toward?* Named in terms of what they will be able to *do*, not what they will *know about*. Bloom's level above Apply is required for the full architecture; below Apply, the complexity threshold may not warrant the full build.
- *Why does this matter?* The motivation layer. Academic credential, job qualification, intellectual project — the motivation type determines which inputs to the adaptive engine matter most.
- *What is the deployment context?* Phone, desktop, classroom, asynchronous, blended. Platform-bound assumptions of v1.5 vs. the ambient deployment the deployment may aspire to.

### 4.2 Learner profile

The learner profile is the artifact the intake produces. Specific. One person, not a category. **A reader who cannot be named is a reader the book cannot be written for.** This is the bear-textbooks workshop pattern adapted to platform commissioning.

### 4.3 Complexity threshold test

Three questions from Chapter 2:

- *Is adaptive sequencing required across concepts that cannot be pre-ordered?* If the curriculum is fixed and sequential, the bandit has nothing to learn.
- *Is live instrumentation required?* If the learning evidence is observable at the artifact level, the measurement layer is a different design.
- *Is a multi-layered capability build required?* If the capability is a single tight skill, one mode is enough and the architecture is over-engineered.

If all three answers are *yes*, the full architecture is warranted. If any is *no*, the chapter recommends the simpler tool. **The complexity threshold is not a gate against the architecture. It is the honest check that prevents the architecture from being commissioned for problems that do not need it.**

### 4.4 Evidence audit

Walk the evidence base relevant to the design choices the architecture will require. Distinguish what Khan uses, what Horvath uses, what both omit. Apply Hattie's 0.40 correctly — as a cost-effectiveness guideline, not an absolute binary. Identify which findings from ITS, spaced repetition, CBL, and generative-assignment literatures apply to this specific design decision. Assess any claimed effect for cherry-picking.

The audit produces the *evidence ladder* for this specific deployment: which design decisions are direct-evidence-supported, which are adjacent-evidence-supported, which are bets. **Chapter 11's epistemic ladder applied to this design conversation.**

### 4.5 Four-layer specification

Each layer specified to the depth the developer needs:

- **Layer 1 — Content.** Domain specificity level (Level 1/2/3 per Chapter 9), AI-generation policy, faculty review gate specifications, minimum viable content per chapter.
- **Layer 2 — Curriculum design.** Concept map with nodes, prerequisite dependencies, Bloom's level assignments, mode-appropriateness flags. Phase-gate logic per mode per concept.
- **Layer 3 — Adaptive engine.** Bandit configuration — context features, reward signal, exploration strategy, cold-start defaults.
- **Layer 4 — Measurement.** Which GLP components are instrumented, which require additional instrumentation, what threshold values trigger phase-gate transitions or engine updates, what the consent architecture commits to and does not.

The cross-layer data flow: what each layer produces and receives. **Chapter 4's architecture applied to this concrete deployment.**

### 4.6 Economics check

What audience size justifies the architecture at the available production budget? Where does the cost-collapse argument apply? Where does it leave the burden of proof unchanged? Project A ($15K) / Project B ($150K) / Project C ($1.5M) — which budget tier is the deployment in, and what subset of the architecture is feasible at that tier?

The economics check is the gate against over-commitment. **A specification that requires Project C investment at Project A budget is the specification that does not get built.**

### 4.7 Honest inventory

Three categories per design decision:

- *Adjacent evidence* — what the literature on partial designs supports.
- *Direct evidence* — what evidence exists on the integrated claim under deployment conditions.
- *Bet* — what the design commits to without sufficient evidence and what the deployment will test.

The inventory is the honesty layer. **A specification without an inventory is a specification that has not yet acknowledged what it is committing to without evidence.** Which is the IDK-IDK problem at the design-conversation level.

---

## §5. What the Map Contains

The output the design conversation produces. The TIKTOC specifies: *complete specification, everything a developer needs to build without a translation meeting, everything Charles needs to evaluate whether what gets built is what he designed.*

Drawing from the MVAL pattern (Minimum Viable Analytical Log), the map contains six fields per design decision:

- **WHAT** — the specific design decision. ("Quiz Me phase-gate at section-read threshold of 3 minutes.")
- **WHY** — the reasoning anchored in evidence. Bastani 2025 for the guardrail-design decision. Cepeda 2006/2008 for the spacing-interval decision. Sadler 2013 for the priority-weighting decision. The WHY field is where the evidence audit lands per decision.
- **HOW** — the implementation specification. Exact field values, exact threshold numbers, exact mode-selection rules.
- **ENVIRONMENT** — the dependencies. Which Layer 4 measurement signals the Layer 3 engine requires. Which content elements the Layer 2 curriculum requires from Layer 1. The cross-layer interface specification.
- **RESULTS expected** — pre-registered prediction of what the design produces. What the engine should converge on after N sessions. What the GLP signal should look like after the phase-gate transition.
- **QUESTIONS** — the open bets per design decision. What this decision commits to without direct evidence. What the deployment will test.

The map is auditable per the same six-field discipline MVAL enforces. **A developer reading the map can implement. A Charles reading the map can evaluate.** A specification missing any of the six fields per design decision is incomplete in the same sense MVAL flags incomplete entries: it cannot pass review because the missing field cannot be reconstructed from the rest.

---

## §6. The Shared Language

The design conversation produces a *shared vocabulary* between Charles Fadel and the developer. Charles can say *"Socratic isn't right here because of retrieval interference"* — and mean the specific finding from Bastani-style guardrail design. The developer can say *"we already have something close — here's what Mixture-of-Experts routing does for the persona-classification problem"* — and mean the specific cancer biology textbook implementation. Both are talking about the same design decision in the same terms.

**The lexicon is not vocabulary for vocabulary's sake.** It is the precondition for the design conversation to scale beyond a single team. Without the lexicon, every new Charles-developer pair has to re-invent the vocabulary that the previous pair invented. With the lexicon, the conversation can happen across teams, across institutions, across years.

The thirteen terms the lexicon owns (Appendix A specifies these in full):

- The IDK-IDK problem
- The four layers — Book Library / Tic TOC / Adaptive Engine / Measurement Layer
- The four modes — Ask AI / Case Study / Quiz Me / Glimmer
- The seven signals (GLP)
- Phase gates
- The within-learner bandit
- The GLP reward signal
- Ambient infrastructure
- The conductor
- The fluency trap
- Cost-collapse asymmetry
- The due-today counter
- Genuine Learning Probability

Charles uses these terms to talk about the design with the developer. The developer uses them to talk about the implementation with Charles. **The chapter's claim is operational: both readers can say the same sentence about the same decision in the same vocabulary by the end of the book.** The lexicon is the test of whether the book delivered on its promise.

---

## §7. The Gru Connection

One section. The implementation book is the right home for the full Gru specification. This is the conceptual hand-off.

The framing — *senior dev is 80% thinking, 20% coding* — is now distributed across the agentic-coding discourse of 2025–2026. The clearest single articulation is Addy Osmani's ["The 80% Problem in Agentic Coding"](https://addyo.substack.com/p/the-80-problem-in-agentic-coding) on Elevate Substack. Koushik Dasika makes the explicit *"for a senior engineer, actual coding is roughly 20%, while the other 80% consists of research, planning, designing the right solution, and collecting and interpreting results"* claim in ["Coding Was Never the Hard Part"](https://koushikdasika.com/blog/coding-was-never-the-hard-part/). Ari Vance frames the shift as a role reconceptualization in ["Stop Coding. Start Orchestrating"](https://medium.com/@AgenticAri/stop-coding-start-orchestrating-the-new-survival-guide-for-2026-83a02d6be859). Greg Brockman at OpenAI 2025 frames it from the production side: AI went from writing 20% to 80% of code in a single month.

I treat the framing as a shared field formulation rather than a quote from a single source. Osmani is the safest single citation if one is required `[verify whether a specific source is intended]`.

### What the framing does for the chapter

**The map Medhavy produces is the 80%. The Gru-assisted build is the 20%.**

The design conversation produces the specification — that is the thinking work. The Gru-assisted (or Claude-Code-assisted, or any agentic-coding-assisted) build executes the specification — that is the implementation work.

The structural parallel to Chapter 10 is the chapter's deepest claim. Cost-collapse on content shifted the binding constraint to knowledge of the individual learner (Sadler 2013). **Cost-collapse on code shifts the binding constraint to specification quality.** The Charles Fadel type can now commission an intelligent textbook and have it built at production-grade quality, *provided he can produce the specification*. The instrument's job is to help him produce the specification.

What becomes valuable when production gets cheap — at both the content layer and the implementation layer — is the human's contextual knowledge of *what to produce*. The Sadler-2013 move at the content layer has its mirror at the implementation layer. The instrument is the same kind of thing in both cases: a conversation that converts human judgment into structured input the cheap-production layer can act on.

The deliberate brevity here is the right scope. The implementation book is the right home for the full Gru spec. This chapter ends with the map. The next book begins with the build.

---

## §8. Worked Example — A Medhavy Session as Design Specification

**Label.** What follows is a *design specification* of the Medhavy intake conversation as currently architected. The live instrument is in development as of 2026-05-17 `[verify deployment state at draft time]`. This is not a product demo. It is the specification of what the session will produce when it is complete. A book describing a tool it is building is more interesting than a book describing a tool that already exists — and is the only framing consistent with the epistemic commitments this book has held since Chapter 1.

The case: Charles Fadel has content on 21st-century skills and curriculum redesign. He wants to commission an intelligent textbook deployment for graduate students in education policy. Here is what the design conversation looks like.

### 8.1 Intake — the first three questions

**Q1: Who is the learner?**

Charles: "Graduate students in education policy programs. Mid-career. They have classroom experience or administrative experience. They are working toward a credential — usually a master's, sometimes a doctoral cognate. They are skeptical of jargon. They have read either too much Hattie or too little."

The instrument captures: motivation = professional credential + intellectual project; prior knowledge = uneven, weighted toward practitioner; misconception risk = treating Hattie's 0.40 as a binary threshold; institutional context = credentialed graduate program.

**Q2: What capability are they being built toward?**

Charles: "They have to be able to evaluate a proposed curriculum reform — looking at the evidence base, the audience, the cost, the institutional fit — and decide whether to support it. Apply level at minimum. Evaluate level is the real target."

The instrument captures: Bloom's primary level = Evaluate; target capability = evidence-base assessment + audience-fit assessment + cost-benefit reasoning + institutional-fit assessment.

**Q3: What is the deployment context?**

Charles: "Asynchronous. Most are part-time. They study at night on a laptop. The course already exists as a Canvas shell with PDFs and discussion forums."

The instrument captures: deployment = LMS-embedded (Canvas LTI); platform-bound; asynchronous; existing course structure.

### 8.2 Learner profile (the artifact)

> *The learner is a 38-year-old assistant principal at a Title I middle school in a state with active legislation on AI in classrooms. She enrolled in the master's program because she keeps being asked to evaluate vendor proposals and she does not trust her own evidence-evaluation. She has read Hattie's first book and an old copy of Robert Marzano. She has not read Horvath. She reads at night on a laptop after her kids are asleep. She has 90 minutes per session, three sessions a week. She is skeptical of academic jargon and very tolerant of practitioner anecdote. Her current evidence-evaluation move is "trust the colleague who recommended it."*

This is the artifact the intake produces. Specific. One person. Named.

### 8.3 Complexity threshold check

The instrument applies the three questions from Chapter 2.

- *Adaptive sequencing required?* Yes — evidence-evaluation builds across cases the learner has not encountered, and the prerequisite chain (effect-size literacy → audience-fit reasoning → cost-effectiveness comparison → institutional fit) cannot be pre-ordered without losing learners who arrive at different starting points.
- *Live instrumentation required?* Yes — the target capability is evaluative reasoning, which is observable in the *process* of working through cases, not in a single final answer. Engagement metrics are not enough; the GLP signal is required.
- *Multi-layered capability build required?* Yes — the capability is a composite of evidence reading, audience reasoning, cost-effectiveness comparison, and institutional fit. Each requires a different mode at different points in the build.

**All three answers are yes. Full architecture warranted.** The instrument records the threshold result.

### 8.4 Evidence audit

The instrument walks the literature relevant to the design choices the architecture will require for this deployment. Excerpts:

- *Hattie 0.40.* Use as cost-effectiveness guideline, not threshold. Cite Bergeron 2017, Wecker et al. 2017 as the criticism layer. Reference the MetaX 2023+ update for current values. Direct-evidence supported as a heuristic; *adjacent* evidence for any specific threshold claim.
- *Bastani 2025 on guardrails.* Direct evidence that AI tutor design matters for durable learning. Adjacent for the specific context-anchoring claim in Medhavy. Use as the load-bearing citation for Ask AI design decisions.
- *Sadler 2013.* Direct evidence for pedagogical content knowledge effect. Adjacent for the misconception-map specification claim. Use for the priority-weighting rationale.
- *Cornelius-White 2007.* Direct evidence for relationship effect on learning. Use as the rationale for protecting human-mediated time when the platform handles automatable work.

The audit produces the *evidence ladder* per design decision. The instrument records each ladder position.

### 8.5 Four-layer specification (partial — Layer 2 expanded)

The output for Layer 2, as a worked excerpt:

**Concept Map for Module 1 — "Effect Sizes and What They Don't Tell You"**

- Node 1.1 — Effect size definition (Bloom: Understand; mode: Ask AI with context-anchoring; prerequisite: none)
- Node 1.2 — Effect size magnitude interpretation (Bloom: Understand; mode: Quiz Me with priority weighting; prerequisite: 1.1)
- Node 1.3 — Effect size *vs.* practical significance (Bloom: Analyze; mode: Case Study with pre-written faculty-reviewed case; prerequisite: 1.1, 1.2)
- Node 1.4 — Cherry-picking the literature (Bloom: Evaluate; mode: Glimmer with backwards-faded scaffolding; prerequisite: 1.1, 1.2, 1.3)

**Phase gates:** Quiz Me on 1.2 gates on Y1 (Temporal Engagement) showing the learner has actually read 1.1. Case Study on 1.3 gates on Y6 (Retrieval Strength Decay) showing 1.1 and 1.2 have stuck through a 7-day spacing interval. Glimmer on 1.4 gates on Y3 (Cross-Context Transfer) showing the learner can apply 1.3 to a case different from the one used in the Case Study mode.

This is what *one* node of the specification looks like. The full specification covers ~80 nodes for an 8-week module, with the same level of detail per node. The instrument generates the specification document. The reviewer (Charles) audits it. The developer builds from it.

### 8.6 Economics check

The instrument records: target audience ≈ 1,200 graduate students per cohort across partner programs; production budget = $120K. Project tier: between A and B. Subset feasible: all four layers at minimum viable scope; ~80 concept nodes (not 200); GLP at Y1 + Y6 + Y2 (three components, not seven); Case Study with pre-written content (no AI-generated cases); Glimmer with rubric review only (no AI pre-grading); no Video and Animation layer.

The economics check is the gate. The instrument flags Glimmer at the rubric-review level rather than the pre-grading level as a constraint imposed by the budget, not by the pedagogy.

### 8.7 Honest inventory

For each major design decision, the instrument records the evidence ladder position. Excerpts:

- *Ask AI with RAG-grounded context-anchoring.* Adjacent (Bastani 2025 + VanLehn 2011). Bet — Open Question 1 from Chapter 11.
- *Quiz Me with priority weighting.* Adjacent (Sadler 2013 + spaced retrieval canon). Bet — Open Question 6.
- *Glimmer with backwards-faded scaffolding for novice users.* Adjacent (Belland et al. 2017 + Pekrun 2006). Bet — Open Question 5.
- *Solo asynchronous AI-facilitated Case Study on pre-written faculty-reviewed cases.* Adjacent (Thistlethwaite 2012 + Dochy 2003). Bet — Open Question 2.

The inventory is honest. The deployment commits to bets that adjacent evidence supports. The bets will be tested by the deployment. The chapter's commitment to Chapter 11's epistemic ladder is enforced operationally in this layer.

### 8.8 The map handed off

The output the conversation produces is a document. The structure: each design decision in WHAT / WHY / HOW / ENVIRONMENT / RESULTS / QUESTIONS form, organized by layer, with cross-layer dependencies mapped.

A developer who was not in the session reads the map. The test the TIKTOC names: **can they build from it without asking a question?** If yes, the design conversation succeeded. If no, the specification is incomplete in a way the chapter teaches the reader to identify.

This is the deliverable. This is what Medhavy the instrument produces. This is what the book has been building toward since the IDK-IDK opening of Chapter 1.

---

## §9. Common Misconceptions

### "The tool can produce the specification without the thinking"

The plausible claim: with enough prompt engineering, the tool can take "suggest 15 chapters" inputs and produce a buildable specification.

**Why it fails.** The misconception map is the input the tool cannot generate. The domain expert's tacit knowledge of *this* curriculum's specific bottlenecks is the thing the LLM does not have. Without it, the architecture has no signal to update against, and the platform reduces to the engagement-as-learning failure mode. The tool amplifies the thinking. It does not replace it.

### "The methodology applies only to Medhavy commissions"

The plausible claim: the design conversation is specific to Medhavy platform deployments and does not generalize.

**Why it fails.** The six moves — intake, complexity threshold, evidence audit, four-layer specification, economics check, honest inventory — are general. They apply to any intelligent textbook design conversation, not just Medhavy. The chapter's worked example is Medhavy-specific because the platform vocabulary is Medhavy's. The methodology under the vocabulary is general. A team commissioning a non-Medhavy intelligent textbook can run the same six moves and produce the same kind of map.

### "The shared language requires institutional adoption"

The plausible claim: the thirteen lexicon terms only work if Medhavy becomes an institutional standard. Otherwise the vocabulary fragments and the cross-team conversation breaks down.

**Why it fails.** This is testable, and the book's circulation strategy is the test. If the Learning Engineering community adopts the lexicon, the conversation scales across teams. If it does not, the lexicon needs to be re-invented per team. **The shared language is itself an open question** that the book's deployment will help answer. The fact that it is open does not make it a weak claim — it makes it a falsifiable one.

---

## §10. Exercises

### Exercise 12.1 — Run a Medhavy session (Create)

Pick a real learning problem you would commission an intelligent textbook for. Run the design conversation:

(a) Conduct the intake. Specify the learner profile in one paragraph naming a specific person.
(b) Apply the complexity threshold test. Record the three answers.
(c) Walk the evidence audit. Identify three load-bearing citations.
(d) Specify the four-layer architecture for the deployment. Use the §8 worked example as the format.
(e) Run the economics check. Specify the budget tier and what subset of the architecture is feasible.
(f) Produce the honest inventory. Categorize each major design decision as adjacent-supported, direct-supported, or bet.

Hand the specification to a developer who was not in the session. **Can they build from it without asking a question?** This is the only test that matters. If they ask a question, identify which of the six moves failed to produce sufficient detail. Revise.

### Exercise 12.2 — Audit a Medhavy-generated specification (Evaluate)

Given a partial Medhavy-generated specification (use the §8 worked example or a specification you produce in Exercise 12.1), identify:

(a) Which layer is underspecified. Name the specific missing element.
(b) Which phase gates are missing. Specify what each missing gate should look like.
(c) Which measurement commitments are absent. Identify what GLP components are required to instrument the phase gates and which are not yet specified.
(d) What questions would the developer ask? List the questions and the specific spec gap each one indicates.

The exercise is the test of whether you can read the specification critically. A reviewer who cannot identify gaps cannot enforce the map's discipline.

### Exercise 12.3 — Conduct the first three intake questions (Apply)

Charles Fadel has content on 21st-century skills and curriculum redesign. Run the first three intake questions of a Medhavy session for his intelligent textbook. For each question:

(a) Specify the question precisely. Use §4.1 as the structure.
(b) Specify what answer Charles would give. Be concrete — name the audience, the capability, the deployment context.
(c) Specify what the instrument captures from the answer.
(d) Identify what the specification needs that the first three questions did not yet surface — and what the next intake question should ask to surface it.

The exercise is the discipline of intake. A reader who can run the first three questions has demonstrated the methodology at the most fundamental level.

### Exercise 12.4 — Test the shared language (Apply)

Pick a design decision from any chapter of this book. Write two sentences:

(a) A sentence Charles Fadel would say about the decision, using the lexicon (§6).
(b) A sentence the developer would say in response, using the same lexicon.

Then test the sentences. Hand them to a Charles Fadel type and a developer who were not part of the book's construction. Can both parse the sentences using only the lexicon? If yes, the language scales. If no, the chapter (or Appendix A) needs to expand the term that broke.

### Exercise 12.5 — Specify a bet (Apply)

From the eight open questions in Chapter 11, pick the one most relevant to a deployment you would commission. Write:

(a) The bet as it appears in the §7 honest inventory. WHAT / WHY / HOW / ENVIRONMENT / RESULTS / QUESTIONS form.
(b) The specific instrumentation the deployment will use to test the bet.
(c) The pre-registered prediction. What result would confirm the bet? What result would falsify it?

The exercise is the discipline of Chapter 11 applied operationally. A specification that names bets but does not specify how the deployment will test them is a specification that has not yet committed to learning.

---

## What Would Change My Mind

A deployment in which a developer outside the original team built a specified Medhavy textbook from the map alone — without a translation meeting with the design conversation participants — and the build survived audit afterward against the specification, would convert the chapter's claim from *current best reading* to *demonstrated capability*. If the developer could build only with translation meetings, the specification format is missing something the chapter has not yet identified, and the six-move methodology has to be revised to surface what is missing.

If the developer could build from the map but the build failed audit — if what got built was not what the specification described — the failure points to the map's underspecification or to the developer's reading discipline. Either way the chapter's claim would have to be revised. I am betting the map is sufficient. The deployment is the test.

## Still Puzzling

Does the shared language hold across institutions, or does each new deployment re-invent the vocabulary? The book's circulation strategy — Learning Engineering community, course assignment, colleague-to-colleague handoff — is the empirical test. The answer is not yet in. The lexicon's portability is itself an open question.

Does the design conversation methodology scale beyond Medhavy? The six moves are general. The lexicon is Medhavy-specific. Whether a team commissioning a non-Medhavy intelligent textbook can run the same six moves with their own vocabulary and produce the same kind of map is testable but not yet tested. I think yes. I have not proven it.

At what point does the design conversation become a single-vendor methodology rather than a field practice? If only Medhavy deployments use the six moves, the methodology is captured. If multiple platforms adopt the structure, the methodology becomes part of how the field designs. The latter outcome is what the book is for. The former outcome would mean the book did not do its work.

---

## Chapter Closing — The Book's Last Paragraph

The reader holds the map. The developer has a specification they can build from. Charles has the language to evaluate whether what gets built is what he designed. The platform is opinionated. The model has no opinions of its own. The conversation is what makes the platform worth building — and the conversation is what this book has been, from the first IDK-IDK incident to this page.

---

**Tags:** design-conversation, Tic-TOC, platform-vs-instrument, shared-language, Gru-80-20, intelligent-textbook-specification, reflexive-methodology
