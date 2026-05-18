# Research Notes — Chapter 12: The Design Conversation

*Research note for the Medhavy book project. Companion to `PEDAGOGY ARCHITECTURE.txt`, `MVAL.txt`, `Lexicon.txt`, the Medhavi Hub `ARCHITECTURE.md` / `API.md`, the existing pantry chapter drafts (`01-what-is-medhavy.md`, `02-why-does-solving-it-require-a-platform.md`, `06-medhavy-conducting-ai.md`), and `_lib_co-intelligence__living_and_working_with_ai.md`. Compiled 2026-05-17 for the Chapter Writer pipeline. Author: research subagent for Nik Bear Brown.*

> **Reader's compass.** Chapter 12 has the hardest pedagogical move in the book. It has to (a) deliver the design-conversation methodology as something the reader can actually run, (b) make the meta-move that the book itself has been the methodology in action since Chapter 1, and (c) name the relationship between Medhavy the platform and Medhavy the instrument without confusion. The chapter's worked example may need to be labeled explicitly as a design specification of what a Medhavy session produces rather than a product demo, depending on what the tool can actually do at draft time. The TIKTOC's open question #1 is: how much of Chapter 12 can be written if the tool is not yet built? Answer in this note: a great deal, because the methodology is well-specified through PEDAGOGY ARCHITECTURE.txt, MVAL.txt, and the existing book.md/architecture.md pattern from the workshop's other books — even if the tool itself is in development, the *conversation* the tool conducts is documented. The Gru section needs the source citation verified — the "senior dev is 80% thinking, 20% coding" framing is now established in the agentic-coding discourse (Osmani; Dasika; Vance) but the original phrasing may need attribution to a specific source.

---

## §1. The meta-move — the book as a Tic TOC session

### 1.1 Why this opening works

The chapter's hook (per TIKTOC): this book *is* a Tic TOC session. The reader has been experiencing the design conversation methodology since Chapter 1 — question by question, intake before architecture, evidence before specification, honest inventory before the map.

The move is reflexive, in the same sense Chapter 11's Montaigne register is reflexive. The architecture of the book *enacts* the methodology it teaches. Chapter 1 opens with a failure (IDK-IDK) before any framework. Chapter 2 imposes the honest check (complexity threshold) before the architecture. Chapter 3 delivers evidence before any design decision. Chapters 4–10 deliver the four-layer architecture with evidence at every decision point. Chapter 11 names the gaps. Chapter 12 makes visible that this sequence *was* the design conversation — the reader has been the participant.

This is the same architectural move bear-textbooks itself takes (the CLAUDE.md is an *essai*; the workshop's method applies to itself; "the method applies to the method" is §4 of the workshop CLAUDE.md). The Medhavy book inherits the reflexive commitment as a design feature, not a stylistic flourish. The chapter's first paragraph names this explicitly: *the methodology has been visible since the IDK-IDK opening; the only thing this chapter does is name it.*

### 1.2 What this opening accomplishes

Three things, simultaneously:

- **It earns the methodology.** A reader who has just spent ten chapters being walked through the four-layer architecture has *experienced* the question-by-question intake. The methodology is not a new instrument introduced in Chapter 12 — it is the instrument the book has been operating with throughout.
- **It dissolves the platform/instrument confusion.** The reader has been thinking of Medhavy as a platform (what gets built). The chapter pivots: Medhavy is also an instrument (what produces the specification for what gets built). The platform and the instrument share a name because they share a structure — the conversation that produces a specification is the same conversation that produces a learning trajectory.
- **It legitimizes the audacious claim of Chapter 12.** That claim: a Medhavy session produces a specification a developer can build from without a translation meeting. This is a strong claim. The legitimization is that the reader has *already seen* the design conversation produce coherent architecture. The chapter doesn't have to argue this from scratch; it has to name what the reader already experienced.

---

## §2. Why the tool requires the thinking

### 2.1 The "suggest 15 chapters" failure mode

The failure mode the chapter has to name precisely. An author opens a design tool and types *"suggest 15 chapters for a medical school pharmacology textbook."* The tool produces 15 plausible-sounding chapter titles. The author accepts them. The adaptive engine now has a concept map with:

- No prerequisite dependencies (chapter 7 may require chapter 12 for any given concept)
- No learning-outcome statements (the chapters are *topics*, not *capabilities*)
- No phase-gate logic (the modes have nothing to gate on)
- No mode-appropriateness flags (Quiz Me vs. Glimmer vs. Case Study has no answer)

The engine is flying blind. Garbage curriculum in, garbage adaptation out. The bandit can run, but it cannot learn — it has no structure to update against. The failure mode is silent: students engage, sessions log, dashboards look fine, and nothing has been learned.

This is the failure mode Chapter 8 ("The Curriculum Design Layer") opens with. Chapter 12's job is to name *why* the tool produces this failure mode when used without the thinking, and what the thinking has to deliver before the tool can produce a buildable specification.

### 2.2 The tool's contribution and its limit

The tool's contribution: amplification of specification work that a domain expert is *already capable of producing* but would take days to write out. The tool reads the intake answers, infers the concept map structure, names the phase gates that would be coherent given the learning outcomes, flags the prerequisite chains, proposes the mode assignments, surfaces the measurement signals each phase gate would require, and produces the specification document in the format the developer needs.

The tool's limit: it cannot generate the domain expert's understanding of what students get wrong. Sadler 2013 (Chapter 10) is the empirical anchor. The most valuable input the domain expert brings is the *misconception map* — what students typically believe before instruction, what wrong answers they reach for, where the bottlenecks live in transfer. The LLM has training-data inferences about common misconceptions in well-documented subjects (Newtonian mechanics, Bayesian probability, photosynthesis). It does not have the domain expert's tacit knowledge of *this* population, *this* curriculum, *this* program's specific bottlenecks. That is the input the tool requires from the human — and the input it cannot produce on its own.

The cleanest framing: **the tool can produce the architecture but not the misconception map; the domain expert produces the misconception map and uses the tool to amplify it into the architecture.** This is the labor separation the chapter teaches.

### 2.3 What "the thinking" actually consists of

The thinking the book provides — the input the tool requires — is the structured intake the design conversation conducts. From PEDAGOGY ARCHITECTURE.txt and the Tic TOC scaffolding pattern used across bear-textbooks:

- **Learner profile.** One specific person, not a category. What they know, what they don't, what they typically get wrong, what they need to be able to do after.
- **Complexity threshold check.** Does this learning problem warrant the full architecture, or is the right answer a simpler tool? (Chapter 2's frame.) If Anki + a volunteer + a Kindle book gets the job done, the architecture is over-engineered for the case.
- **Evidence audit.** What does the evidence say about how the target capability is built? What does it not say? Which design choices are evidence-supported and which are bets?
- **Four-layer specification.** Content (Layer 1), curriculum design (Layer 2), adaptive engine (Layer 3), measurement (Layer 4) — with the data each layer produces and receives, the phase gates that connect them, and the binding constraints at each layer.
- **Economics check.** What audience size justifies the architecture at the available production budget? (Chapter 10's frame.) Where does the cost-collapse argument apply and where does it leave the burden of proof unchanged?
- **Honest inventory.** What is supported by direct evidence? What by adjacent evidence? What is a design bet that the deployment will test? (Chapter 11's frame.)

These six moves are the design conversation. The Medhavy instrument conducts them as a question-by-question intake; the human (Charles Fadel type) provides the answers; the instrument produces the specification document the developer builds from. The book has been training the reader to *do* these six moves since Chapter 1.

---

## §3. Platform vs. instrument — the distinction

### 3.1 Two things, same name, same structure

The distinction the chapter has to land:

- **Medhavy the platform** is what the developer builds. It is the four-layer architecture deployed at, e.g., cancer.medhavy.com or physics.medhavy.com — the production system serving medical students or physics undergraduates with Ask AI + Quiz Me + Case Study + Glimmer + Video and Animation, instrumented by the GLP measurement layer, optimized by the within-learner bandit.
- **Medhavy the instrument** is what the domain expert uses to produce the specification the developer builds from. It is the design conversation tool — the intake-driven session that walks the Charles Fadel type through learner profile, complexity threshold, evidence audit, four-layer specification, economics check, and honest inventory, and that produces the chapter specifications a developer can configure the platform from without a translation meeting.

They share a name because they share a structure: both are *conversations* that produce *learning trajectories*. The platform's conversation is between AI and student about a concept. The instrument's conversation is between AI and domain expert about a curriculum. The shape of the question-by-question intake is the same. The output differs — student understanding in one case, buildable specification in the other.

### 3.2 Why the distinction matters for the reader

A Charles Fadel type who confuses the platform with the instrument will commission the wrong thing. He will ask the developer to build "Medhavy" without specifying *which* Medhavy and what the specification is. The developer will build the platform without the specification, which produces the "suggest 15 chapters" output writ large — a platform with a concept map that no one designed for the learners actually being served.

A developer who confuses them will build the platform and assume the design conversation will happen later, somewhere else, by someone else. That is the bolt-on failure (Chapter 4): the design conversation does not happen later. It happens before the build or it does not happen at all. A platform configured against an unspecified curriculum is the platform that cannot learn.

The chapter's move: name the distinction explicitly so both readers can recognize when they are asking the wrong question, and use the shared structure (intake → architecture → specification → deployment) to make the right question askable.

### 3.3 What the implementation book holds

The TIKTOC notes (Chapter 12 closing): "The Gru connection is deliberately brief — one section, not a full technical treatment. The implementation book is the right home for the full Gru specification." This is the chapter author's signal that the *implementation* book — the book about building the platform — is a follow-up. Chapter 12 hands the specification; the implementation book is about turning the specification into deployed code. The chapter should be transparent about this scope: the book ends with the map, not with the build.

---

## §4. How to conduct the design conversation — the six moves

This is the chapter's operational core. The reader must finish able to run the conversation themselves.

### 4.1 Intake questions

The intake's job is to surface the inputs the rest of the conversation needs. From the bear-textbooks workshop pattern (Tic TOC `/i1`–`/i4`) and from PEDAGOGY ARCHITECTURE.txt's institutional-context inputs:

- *Who is the learner?* One specific person, not a category. Age, prior knowledge, prior misconceptions, current capability gap, motivation type (academic/professional/intellectual), institutional context (credentialing, executive education, K-12, homeschool).
- *What capability are they being built toward?* Named in terms of what they will be able to *do*, not what they will *know about*. Bloom's level above Apply is required for the full architecture; below Apply, the complexity threshold may not warrant the full build.
- *Why does this matter?* The motivation layer — academic credential, job qualification, intellectual project. The motivation type determines which inputs to the adaptive engine matter most.
- *What is the deployment context?* Phone, desktop, classroom, asynchronous, blended. The platform-bound assumptions of v1.5 vs. the ambient deployment (Chapter 5) the deployment may aspire to.

### 4.2 Learner profile

The learner profile is the artifact the intake produces. Specific. One person, not a category. The bear-textbooks workshop pattern requires this — a reader who cannot be named is a reader the book cannot be written for.

Per `PEDAGOGY ARCHITECTURE.txt`'s explicit-instruction signature: "early in a topic, when prior knowledge assessment suggests foundational gaps, and when interaction patterns show confusion rather than engagement — repeated short questions, requests for clarification of the AI's previous response, low dwell time on content sections." This is the *signal-level* description of a learner profile. The instrument's intake produces the *content-level* description that the platform's instrumentation then maps signal-level patterns against.

### 4.3 Complexity threshold test

Three questions from Chapter 2:

- *Is adaptive sequencing required across concepts that cannot be pre-ordered?* If the curriculum is fixed and sequential (Anki for vocabulary; a phonics primer), the bandit has nothing to learn.
- *Is live instrumentation required?* If the learning evidence is observable at the artifact level (a typed exam answer, a finished essay graded by a human), the measurement layer is a different design.
- *Is a multi-layered capability build required?* If the capability is a single tight skill (typing speed, vocabulary recall), one mode is enough and the architecture is over-engineered.

If all three answers are *yes*, the full architecture is warranted. If any is *no*, the chapter recommends the simpler tool. The complexity threshold is not a gate against the architecture; it is the honest check that prevents the architecture from being commissioned for problems that do not need it.

### 4.4 Evidence audit

Walk the evidence base relevant to the design choices the architecture will require. From Chapter 3's frame: distinguish what Khan uses, what Horvath uses, what both omit. Apply Hattie's 0.40 correctly (cost-effectiveness guideline, not absolute binary). Identify which findings from ITS, spaced repetition, CBL, and generative-assignment literatures apply to this specific design decision. Assess any claimed effect for cherry-picking.

The audit produces the *evidence ladder* for this specific deployment: which design decisions are direct-evidence-supported, which are adjacent-evidence-supported, which are bets. Chapter 11 is the methodology; the audit is the methodology applied to this design conversation.

### 4.5 Four-layer specification

The deliverable. Each layer specified to the depth the developer needs:

- **Layer 1 — Content.** Domain specificity level (Level 1/2/3 per Chapter 9), AI-generation policy (which elements can be AI-generated with light review, which require domain expert authorship), faculty review gate specifications, minimum viable content layer per chapter.
- **Layer 2 — Curriculum design.** Concept map with concept nodes, prerequisite dependencies, Bloom's level assignments, mode-appropriateness flags. Phase-gate logic per mode per concept. The deliverable the bear-textbooks `outline.md` produces, extended with mode and phase-gate annotation.
- **Layer 3 — Adaptive engine.** Bandit configuration — context features (FSRS retrievability, prerequisite mastery, concept importance tier, recency, prior mode performance), reward signal (which GLP components contribute, initial weights), exploration strategy (epsilon-greedy / UCB1 / Thompson sampling for this use case), cold-start defaults.
- **Layer 4 — Measurement.** Which GLP components are instrumented from existing data streams, which require additional instrumentation, what threshold values trigger phase-gate transitions or engine updates, what the consent architecture commits to and does not.

The cross-layer data flow: what each layer produces and receives. Chapter 4 (The Four Layers) is the architecture; the specification is the architecture applied to this concrete deployment.

### 4.6 Economics check

Per Chapter 10. What audience size justifies the architecture at the available production budget? Where does the cost-collapse argument apply? Where does it leave the burden of proof unchanged? Project A ($15K) / Project B ($150K) / Project C ($1.5M) — which budget tier is the deployment in, and what subset of the architecture is feasible at that tier?

The economics check is the gate against over-commitment. A specification that requires Project C investment at Project A budget is the specification that does not get built; the chapter teaches the reader to scope the architecture to the budget honestly rather than commit to a build that cannot complete.

### 4.7 Honest inventory

Per Chapter 11. Three categories per design decision:

- *Adjacent evidence* — what the literature on partial designs supports.
- *Direct evidence* — what evidence exists on the integrated claim under deployment conditions.
- *Bet* — what the design commits to without sufficient evidence and what the deployment will test.

The inventory is the honesty layer. A specification without an inventory is a specification that has not yet acknowledged what it is committing to without evidence — which is the IDK-IDK problem at the design-conversation level.

---

## §5. What the map contains

The output the design conversation produces. The TIKTOC specifies: complete specification, everything a developer needs to build without a translation meeting, everything Charles needs to evaluate whether what gets built is what he designed.

Drawing from `MVAL.txt`'s structured-intake pattern, the map contains six fields per design decision (analogous to MVAL's WHAT/WHY/HOW/ENVIRONMENT/RESULTS/QUESTIONS):

- **WHAT** — the specific design decision (e.g., "Quiz Me phase-gate at section-read threshold of 3 minutes").
- **WHY** — the reasoning anchored in evidence. Bastani 2025 for the guardrail-design decision. Cepeda 2006/2008 for the spacing-interval decision. Sadler 2013 for the priority-weighting decision. The WHY field is where the evidence audit lands per decision.
- **HOW** — the implementation specification. Exact field values, exact threshold numbers, exact mode-selection rules. Per `PEDAGOGY ARCHITECTURE.txt`: "Content requirement: Textbook must include definition blocks, worked examples, numbered step sequences..." This level of specificity per layer.
- **ENVIRONMENT** — the dependencies. Which Layer 4 measurement signals the Layer 3 engine requires. Which content elements the Layer 2 curriculum requires from Layer 1. The cross-layer interface specification.
- **RESULTS expected** — pre-registered prediction of what the design produces. What the engine should converge on after N sessions. What the GLP signal should look like after the phase-gate transition. What the failure mode looks like if the design does not work.
- **QUESTIONS** — the open bets per design decision. What this decision commits to without direct evidence. What the deployment will test.

The map is auditable per the same six-field discipline MVAL enforces on research logs. A developer reading the map can implement; a Charles reading the map can evaluate. A specification missing any of the six fields per design decision is incomplete in the same sense MVAL flags incomplete entries: it cannot pass review because the missing field cannot be reconstructed from the rest.

---

## §6. The shared language

### 6.1 What the lexicon does

From `Lexicon.txt` and `PEDAGOGY ARCHITECTURE.txt`: the design conversation produces a *shared vocabulary* between Charles Fadel and the developer. Charles can say "Socratic isn't right here because of retrieval interference" — and mean the specific finding from Bastani-style guardrail design. The developer can say "we already have something close — here's what Mixture-of-Experts routing does for the persona-classification problem" — and mean the specific Cancer Biology textbook implementation. Both are talking about the same design decision in the same terms.

The lexicon is not vocabulary for vocabulary's sake. It is the precondition for the design conversation to scale beyond a single team. Without the lexicon, every new Charles–developer pair has to re-invent the vocabulary that the previous pair invented; with the lexicon, the conversation can happen across teams, across institutions, across years.

This is the same reflexive move the workshop's Lexicon.txt makes: the NanoLex pipeline (Pipeline B in Lexicon.txt) is the production version of *the lexicon layer itself becoming an AI-generated artifact* — fine-tuned to extend the human-curated vocabulary into domains it has not yet covered. The lexicon-as-instrument move parallels the platform-as-instrument move. Both are cases of the conversation producing the conversation's vocabulary as a byproduct.

### 6.2 The thirteen terms the lexicon owns

From the TIKTOC's Appendix A specification:

- The IDK-IDK problem (Chapter 1)
- The four layers — Book Library / Tic TOC / Adaptive Engine / Measurement Layer (Chapter 4)
- The four modes — Ask AI / Case Study / Quiz Me / Glimmer (Chapter 6)
- The seven signals (Chapter 5 GLP)
- Phase gates (Chapter 6)
- The within-learner bandit (Chapter 7)
- The GLP reward signal (Chapter 5, 7)
- Ambient infrastructure (Chapter 5, 11)
- The conductor (the human conducting Medhavy as the orchestra — `06-medhavy-conducting-ai.md`)
- The fluency trap (Chapter 5)
- Cost-collapse asymmetry (Chapter 10)
- The due-today counter (Chapter 6 Quiz Me, Chapter 11 open question 4)
- Genuine Learning Probability (Chapter 5)

Charles uses these terms to talk about the design with the developer. The developer uses them to talk about the implementation with Charles. The chapter's claim is operational: *both readers can say the same sentence about the same decision in the same vocabulary by the end of the book.* The lexicon is the test of whether the book delivered on its promise.

---

## §7. The Gru connection — 80% thinking / 20% coding

### 7.1 The framing, sourced

The current state of the "senior developer is 80% thinking, 20% coding" framing in agentic-coding discourse, as of 2025–2026:

- **Addy Osmani, "The 80% Problem in Agentic Coding"** ([Elevate Substack 2024–2025](https://addyo.substack.com/p/the-80-problem-in-agentic-coding)). Argues the inversion is the central shift: in traditional engineering, developers spend ~80% of time on implementation and ~20% on thinking. In agentic coding, the ratio inverts — developers spend ~80% on thinking and ~20% on implementation.
- **Koushik Dasika, "Coding Was Never the Hard Part"** ([blog](https://koushikdasika.com/blog/coding-was-never-the-hard-part/)). Makes the explicit "for a senior engineer, actual coding is roughly 20%, while the other 80% consists of research, planning, designing the right solution, and collecting and interpreting results" claim.
- **Ari Vance, "Stop Coding. Start Orchestrating. The New Survival Guide for 2026"** ([Medium 2026](https://medium.com/@AgenticAri/stop-coding-start-orchestrating-the-new-survival-guide-for-2026-83a02d6be859)). Frames the shift as a reconceptualization of role from implementer to orchestrator.
- **OpenAI / Greg Brockman, 2025.** "AI Went From Writing 20% To 80% Of Code In A Single Month" — the inverse framing from the production-side rather than the developer-side. The same ratio appears in both directions.

**Verification flag.** The original canonical phrasing of "senior dev is 80% thinking, 20% coding" cannot be cleanly attributed to a single source as of 2026 — the framing is now distributed across the agentic-coding discourse with multiple near-simultaneous formulations. The chapter should treat it as **a shared framing of the field circa 2025–2026** rather than a quote from a single source, with Osmani's "80% Problem in Agentic Coding" essay as the most-cited explicit articulation. `[verify with the author whether a specific source is intended; Osmani is the safest single citation if one is required]`.

### 7.2 What the framing does for Chapter 12

The connection the chapter makes: **the map Medhavy produces is the 80%. The Gru-assisted build is the 20%.** This is the right framing for the chapter's hand-off to the implementation book. The design conversation produces the specification — that is the thinking work. The Gru-assisted (or Claude-Code-assisted, or any agentic-coding-assisted) build executes the specification — that is the implementation work.

The chapter's move: name that the *specification* is the load-bearing artifact, and that the production-cost collapse for coding (which mirrors the production-cost collapse for content from Chapter 10) means the *binding constraint on building intelligent textbooks has shifted from coding capacity to specification quality*. The Charles Fadel type can now commission an intelligent textbook and have it built at production-grade quality, provided he can produce the specification. The instrument's job is to help him produce the specification.

This is the structural parallel between Chapter 10 (cost-collapse on content) and Chapter 12 (cost-collapse on code): when production is cheap, the binding constraint shifts to specification and judgment. The Sadler-2013 move at the content layer (the misconception map) has its mirror at the implementation layer (the design specification). In both cases, what becomes valuable when production gets cheap is the human's contextual knowledge of *what to produce*.

### 7.3 The deliberate brevity

The TIKTOC's instruction: the Gru section is deliberately brief — one section, not a full technical treatment. The implementation book is the right home for the full Gru specification. The chapter should respect this — one section, the conceptual frame, the hand-off to the implementation book. Do not over-specify here; the over-specification is precisely the move the next book is for.

---

## §8. Verification flags and open questions

### 8.1 Things to verify at draft time `[verify]`

- **The Gru / 80-20 framing source.** The Osmani essay is the safest single citation; the framing as such is distributed. Confirm with the author whether a specific source is intended.
- **Montaigne *Essais* opening (cross-reference Ch 11).** Confirm 1580 first publication date and the *"Que sais-je?"* motto attribution. Both are well-attested.
- **The Medhavy instrument's actual capabilities at draft time.** Per TIKTOC: if the tool is not built when the chapter is drafted, the worked example must be labeled explicitly as a design specification of what the session will produce — not a product demo. Verify against the actual deployment state at draft time and label accordingly.

### 8.2 Open questions the chapter raises but does not resolve

- *Does the instrument produce specifications a developer can actually build from without a translation meeting?* This is testable: hand a Medhavy-generated specification to a developer who was not in the session; can they build from it without asking a question? The TIKTOC names this as the only test that matters.
- *Does the shared language hold across institutions, or does each new deployment re-invent the vocabulary?* The book's circulation strategy (Learning Engineering community, course assignment, colleague-to-colleague handoff) is the empirical test of this.
- *Does the design conversation methodology scale beyond Medhavy?* The methodology is general — it applies to any intelligent-textbook design conversation, not just Medhavy-platform commissions. Whether the chapter's worked example reads as generalizable or Medhavy-specific is itself a design choice.

### 8.3 What would change the chapter's reading

A deployment story where a developer outside the original team built a specified Medhavy textbook without a translation meeting, with the specification surviving the audit afterwards, would convert the chapter's claim from *current best reading* to *demonstrated capability*. The chapter should treat this as the empirical test waiting to be run.

---

## §9. Consolidated citations and pantry cross-reference

### 9.1 Existing pantry sources (cite by filename)

- `PEDAGOGY ARCHITECTURE.txt` — heavy use throughout for §2 (why the tool requires the thinking), §4 (the design conversation moves), §6 (shared language). The five approaches' content requirements per approach (definition blocks for direct instruction, decision points for case-based, etc.) are the specification template the design conversation produces.
- `MVAL.txt` — heavy use for §5 (what the map contains). The six-field structure (WHAT/WHY/HOW/ENVIRONMENT/RESULTS/QUESTIONS) is the model for what each design decision in the map must contain. The MVAL discipline ("an entry with five fields is not a partial entry — it is an incomplete entry") is the model for the specification audit.
- `Lexicon.txt` — heavy use for §6 (shared language). The NanoLex two-pipeline architecture is the production version of the lexicon-as-instrument move. The structured lexical entry schema (Classification, Synonymy, Hypernymy, etc.) is the model for the rigor the design-conversation lexicon enforces.
- `_lib_co-intelligence__living_and_working_with_ai.md` (Mollick) — supporting reference for the human+AI labor-separation argument. Mollick's framing of AI as a tool that amplifies human judgment rather than replacing it is consonant with the platform-vs-instrument distinction the chapter makes.
- `01-what-is-medhavy.md`, `02-why-does-solving-it-require-a-platform.md`, `06-medhavy-conducting-ai.md` — Medhavi-internal chapter drafts establishing the conductor metaphor, the platform argument, and the four-layer architecture as currently articulated. The chapter should reconcile its design-conversation framing with these existing articulations.
- `medhavy-1.5-feature-roadmap-complete.md` — the current platform state. Determines what the worked-example Medhavy session can actually demonstrate vs. what must be labeled as design specification.

### 9.2 New citations introduced in this note (Chicago author-date, link-bearing)

Dasika, Koushik. 2025. "Coding Was Never the Hard Part." Personal blog. [https://koushikdasika.com/blog/coding-was-never-the-hard-part/](https://koushikdasika.com/blog/coding-was-never-the-hard-part/)

Mollick, Ethan. 2024. *Co-Intelligence: Living and Working with AI.* Portfolio.

Osmani, Addy. 2025. "The 80% Problem in Agentic Coding." *Elevate* (Substack). [https://addyo.substack.com/p/the-80-problem-in-agentic-coding](https://addyo.substack.com/p/the-80-problem-in-agentic-coding)

Vance, Ari. 2026. "Stop Coding. Start Orchestrating. The New Survival Guide for 2026." Medium. [https://medium.com/@AgenticAri/stop-coding-start-orchestrating-the-new-survival-guide-for-2026-83a02d6be859](https://medium.com/@AgenticAri/stop-coding-start-orchestrating-the-new-survival-guide-for-2026-83a02d6be859)

Brockman, Greg. 2025. Quoted in "OpenAI's Greg Brockman Says AI Went From Writing 20% To 80% Of Code In A Single Month." Tech.Yahoo. [https://tech.yahoo.com/ai/chatgpt/articles/openais-greg-brockman-says-ai-143153552.html](https://tech.yahoo.com/ai/chatgpt/articles/openais-greg-brockman-says-ai-143153552.html)

Sadler, Philip M., Gerhard Sonnert, Harold P. Coyle, Nancy Cook-Smith, and Jaimie L. Miller. 2013. "The Influence of Teachers' Knowledge on Student Learning in Middle School Physical Science Classrooms." *American Educational Research Journal* 50(5): 1020–1049. (Cross-reference to Ch 10 notes.)

Shulman, Lee S. 1986. "Those Who Understand: Knowledge Growth in Teaching." *Educational Researcher* 15(2): 4–14. (PCK as the theoretical anchor for the misconception-map argument.)

Bastani, Hamsa, et al. 2025. "Generative AI without guardrails can harm learning: Evidence from high school mathematics." *PNAS* 122(26): e2422633122. (Cross-reference to Ch 11 notes; relevant here for the WHY field on the guardrail-design decision.)

---

## §10. Note on the worked example labeling

The TIKTOC instruction is load-bearing: *if the tool is not built when the chapter is drafted, the worked example must be labeled explicitly as a design specification of what the session will produce — not a product demo. The book's epistemic honesty commitment requires this label.*

This is the same Montaigne-register move Chapter 11 makes. A worked example labeled as design-specification-rather-than-demo is honest about the deployment state. A worked example presented as demo when the tool is not yet built is the IDK-IDK problem at the chapter level — claiming capability that has not been delivered.

The chapter author's call at draft time: check the actual instrument state, label accordingly. *"What follows is the design specification of the Medhavy intake conversation as currently architected; the live instrument is in development as of [date]"* is the honest framing if the tool is not yet usable. A book describing a tool it is building is more interesting than a book describing a tool that already exists, *and* is the only framing consistent with the book's epistemic commitments.

---

*End of research note for Chapter 12. ~4,800 words.*
