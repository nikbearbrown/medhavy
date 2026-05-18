# Glimmer — Creative Cumulative Assignments, AI Pre-Grading, and the Four Constructs Medhavy Must Not Confuse

*Research note for Medhavy's "Glimmer" mode design and the corresponding book chapter. Compiled 2026-05-17. Author: research subagent for Nik Bear Brown. Citation-dense; organized for direct quarrying into prose.*

> **Reader's compass.** This note refuses to collapse four constructs that are routinely conflated in EdTech writing about "creative" or "open-ended" assignments: **Generative Learning Activities (GLA)**, **Elaborative Interrogation (EI)**, **Ill-Structured Problems (ISP)**, and **Project-Based Learning (PBL)**. Each has a different mechanism, different evidence base, and different design requirement. Glimmer's actual design (Medhavy 1.5, chapter 4) inherits from one of these most cleanly and borrows from the others; this note names which is which.

---

## 0. The four constructs — get this right before anything else

The single most common error in vendor writing about "creative" assignments is to treat them as one thing. They are at least four, and the effect sizes do not transfer.

**Generative Learning Activities (GLA).** Wittrock 1974, formalized by Fiorella & Mayer 2016 as the eight "ways to promote generative learning": summarizing, mapping, drawing, imagining, self-explaining, teaching, enacting, self-testing. The theoretical engine is the SOI framework — *select* relevant information, *organize* it into a coherent representation, *integrate* it with prior knowledge. The activity is brief (a study session, not a term). The product is internal (a representation the learner now holds). The effect-size claims are about comprehension and retention measured days to weeks later.

**Elaborative Interrogation (EI).** Pressley et al. 1987; Pressley, Wood, Woloshyn, Martin, King & Menke 1992. A narrower technique: when studying a fact or claim, the learner asks *why is this true?* and generates an explanation linking it to prior knowledge. EI is one technique inside GLA; it is also a domain in itself with its own meta-analyses. Dunlosky et al. 2013 rated it "moderate utility" — useful, well-evidenced, narrower than self-explanation.

**Ill-Structured Problems (ISP).** Jonassen 1997, 2000; Sinnott 1989 on adult cognition. An ISP has multiple valid solutions, no agreed evaluation criteria, contested goals, and requires the solver to specify the problem before solving it. ISP-solving is a *capacity*, not an activity — the literature is about how to teach a student to navigate ambiguity, not how to teach a specific fact. Belland 2014 is the canonical scaffolding-for-ISP synthesis.

**Project-Based Learning (PBL).** Krajcik & Blumenfeld 2006; Thomas 2000; Chen & Yang 2019 meta-analysis. A cumulative inquiry sustained over weeks, producing an artifact the learner shows others. The "driving question" is announced at the start. PBL is what most K–12 educators mean by "project work." It is *not* GLA, *not* EI, and ISP is one component of PBL but not its defining feature.

**Why the distinction matters for Medhavy.** A Fiorella & Mayer effect-size for self-explanation cannot underwrite a claim about Glimmer's cumulative term project. A PBL meta-analysis effect cannot underwrite a claim about a single Glimmer session. The Glimmer's actual design (see §7) is a **hybrid that most closely inherits from GLA at the session level and from emergent-portfolio writing pedagogy at the term level** — and the evidence base for the term-level claim is genuinely thin. Throughout this note every effect-size citation is tagged with the construct class it actually applies to:

- `[generative-learning]` — GLA / SOI framework / Fiorella & Mayer canon.
- `[elaborative-interrogation]` — Pressley canon / "why" questions during study.
- `[ill-structured-problems]` — Jonassen / Belland / scaffolding for ambiguity.
- `[PBL]` — Project-based learning / cumulative artifact production.
- `[feedback]` — Hattie & Timperley / formative assessment / AI feedback.
- `[emergent-portfolio]` — Murray / Elbow / Flower & Hayes / writing-process pedagogy.
- `[clinical]` — Medical education applications.
- `[foundational-theory]` — Wittrock, Bandura, Deci & Ryan, Pekrun, etc.
- `[failure-mode]` — Anxiety, expertise reversal, cognitive offloading.

---

## 1. Effectiveness evidence

### 1.1 The canonical GLA synthesis — Fiorella & Mayer 2016 `[generative-learning]`

Fiorella, L., & Mayer, R. E. (2016). "Eight Ways to Promote Generative Learning." *Educational Psychology Review* 28(4): 717–741. ([DOI: 10.1007/s10648-015-9348-9](https://link.springer.com/article/10.1007/s10648-015-9348-9))

- **The frame:** Generative learning is the active construction of meaning, operationalized by Wittrock 1974 and elaborated through the SOI model — *select, organize, integrate*. The 2016 paper synthesizes evidence across eight activities.
- **The eight activities and their evidence (Fiorella & Mayer's verbatim summary, paraphrased for brevity; full effect-size table in the paper):**
  - **Summarizing:** Median effect ~ d = 0.50 on retention; smaller and more variable on transfer. Best for older learners with summarization training. Without training, learners often produce summaries that are functionally re-reading.
  - **Mapping (concept/graphic organizer):** d = 0.43 on retention, d = 0.53 on transfer. Larger when learners construct the map themselves rather than complete a partial one.
  - **Drawing:** d ≈ 0.40 on retention, larger on transfer for spatial/causal material. Quality of drawing matters more than quantity.
  - **Imagining:** Small but consistent effects, d ≈ 0.20–0.30. Works best for material with concrete imageable referents.
  - **Self-explaining:** d ≈ 0.55 on both retention and transfer — the largest and most reliable of the eight. Effects scale with prompt quality.
  - **Teaching (learning-by-teaching, expecting to teach):** d ≈ 0.40 on retention; even *expectation* of teaching (without actually teaching) produces gains.
  - **Enacting (gesture, role-play, physical movement):** d ≈ 0.50, larger for STEM concepts with spatial/temporal structure.
  - **Self-testing:** This is the testing-effect literature subsumed; see Adesope et al. 2017 (g = 0.51 vs. re-study; see quiz-me-research.md).
- **The conditions for all eight:** Fiorella & Mayer name three: the learner must have **prerequisite knowledge** sufficient to generate, must be **motivated** to engage in generation, and must have **scaffolding** that constrains what gets generated. Without all three, generative activities produce illusion-of-fluency without learning — the "desirable difficulties" become merely undesirable.
- **For Glimmer:** The "creative non-trivial assignment" at the *session* level is most plausibly a generative activity. Which of the eight depends on the assignment specifics. A Glimmer that asks "design a protocol for X" is closest to **drawing + self-explaining + teaching** in combination. A Glimmer that asks "explain why this clinical decision was made" is closer to **self-explaining + elaborative interrogation**. The chapter should pick the closest match and report that activity's effect size — *not* claim "generative learning effect" generically.

### 1.2 The ranking of study techniques — Dunlosky, Rawson, Marsh, Nathan & Willingham 2013 `[generative-learning]` `[elaborative-interrogation]`

Dunlosky, J., Rawson, K. A., Marsh, E. J., Nathan, M. J., & Willingham, D. T. (2013). "Improving Students' Learning With Effective Learning Techniques: Promising Directions From Cognitive and Educational Psychology." *Psychological Science in the Public Interest* 14(1): 4–58. ([DOI: 10.1177/1529100612453266](https://journals.sagepub.com/doi/10.1177/1529100612453266))

- **The ranking (of ten common techniques):**
  - **High utility:** Practice testing, distributed practice.
  - **Moderate utility:** Elaborative interrogation, self-explanation, interleaved practice.
  - **Low utility:** Summarization, highlighting/underlining, keyword mnemonic, imagery for text, re-reading.
- **For Glimmer:** The two GLA techniques most relevant to a Glimmer assignment — **self-explanation** and **elaborative interrogation** — sit in the *moderate utility* tier, not the high-utility tier. Dunlosky and colleagues' caveat is important: moderate utility means the technique works under specific conditions, with prepared learners, on tasks of appropriate complexity, with prompts of sufficient quality. It is not a guarantee that a "creative assignment" produces learning.
- **The honest read for the Medhavy chapter:** The literature does not say "creative cumulative assignments are the highest-utility study activity." It says: practice testing and spacing are the most reliably effective study activities; self-explanation and elaborative interrogation are moderately effective generative add-ons; project-based and ill-structured work have *different* effect sizes that depend on facilitation, scaffolding, and time.

### 1.3 The original generative-learning theory — Wittrock 1974 `[foundational-theory]`

Wittrock, M. C. (1974). "Learning as a Generative Process." *Educational Psychologist* 11(2): 87–95. (Reprinted with annotation in *Educational Psychologist* 45(1), 2010.)

- **The original claim:** Learning is not the reception of information but the construction of relations — between new material and existing knowledge, between new material and itself, between new material and the learner's own experience. The verb "generate" was a deliberate move against the dominant transmission metaphor of the early 1970s.
- **For Glimmer:** Wittrock's 1974 frame names the operational distinction Fiorella & Mayer formalize in 2016. The test of whether a Glimmer is "genuinely generative" rather than "disguised summary" is: does the learner produce a relation that did not exist on the page? A protocol design that recombines content into a new structure is generative. A "creative assignment" that asks the learner to restate the chapter in their own words is summarization wearing a generative costume.

### 1.4 The elaborative-interrogation canon — Pressley et al. 1987, 1992 `[elaborative-interrogation]`

- Pressley, M., McDaniel, M. A., Turnure, J. E., Wood, E., & Ahmad, M. (1987). "Generation and Precision of Elaboration: Effects on Intentional and Incidental Learning." *Journal of Experimental Psychology: Learning, Memory, and Cognition* 13(2): 291–300.
- Pressley, M., Wood, E., Woloshyn, V. E., Martin, V., King, A., & Menke, D. (1992). "Encouraging Mindful Use of Prior Knowledge: Attempting to Construct Explanatory Answers Facilitates Learning." *Educational Psychologist* 27(1): 91–109.
- **The mechanism:** Asking *why is this true?* during study activates a search through prior knowledge for explanatory connections. The act of attempting the explanation — even when the explanation is partial or wrong — produces an elaboration trace that retrieval can use later.
- **Effect-size pattern (from the 1992 review and subsequent meta-analytic work):** Most demonstrations are in the **d = 0.40 to 0.75** range on delayed retention of factual material. Effects are larger when:
  - The learner has prior knowledge to elaborate from (novices produce thinner traces).
  - The "why" question targets material that has an actual causal structure (true for biology, history, mechanics; weaker for arbitrary lists).
  - Feedback or peer interaction confirms whether the generated explanation was on-track.
- **For Glimmer's AI pre-grading move:** This is where the EI literature directly informs Medhavy's design. The AI reviewer asking "What is your strongest reason for this design choice? What is your weakest?" is a structured elaborative interrogation prompt — the system is forcing the learner to generate the "why" trace they would skip if left alone. See §3.

### 1.5 The ill-structured-problems literature — Jonassen 1997, 2000 `[ill-structured-problems]`

- Jonassen, D. H. (1997). "Instructional Design Models for Well-Structured and Ill-Structured Problem-Solving Learning Outcomes." *Educational Technology Research and Development* 45(1): 65–94.
- Jonassen, D. H. (2000). "Toward a Design Theory of Problem Solving." *ETR&D* 48(4): 63–85.
- **The frame:** Well-structured problems have a single correct answer, agreed evaluation criteria, and a known solution path. Ill-structured problems have *none of the three*. Jonassen 2000 identifies eleven problem types, ranging from "logic problems" (most well-structured) to "dilemmas" (most ill-structured). Design problems, policy problems, and clinical diagnosis problems sit toward the ill-structured end.
- **Design implications Jonassen names:**
  - ISP-solving requires learners to *specify* the problem before solving it. Instruction must scaffold the specification move, not just the solution move.
  - Evaluation cannot be by correctness; it must be by **defensibility** of reasoning — the learner names tradeoffs, justifies choices, identifies what would change the choice.
  - **Multiple cases** are required; a single ISP teaches one solution, not the capacity to navigate the class.
  - **Cognitive flexibility** (Spiro et al. 1988) — exposure to the same content from multiple angles — is necessary for transfer.
- **Sinnott 1989** (the foundational adult-cognition work Jonassen cites): *Everyday Problem Solving: Theory and Applications*. Plenum Press. Sinnott's argument is that adult cognition is *organized around* ill-structured problems; treating real-world expertise as application of well-structured-problem rules misses the actual cognitive work.
- **For Glimmer:** The Glimmer rubric (WHY / usefulness / mechanism / defensibility / specificity) maps almost exactly onto Jonassen's defensibility-of-reasoning criterion. **The rubric is an ISP rubric.** This is the cleanest construct match for the *session-level* Glimmer task.

### 1.6 Belland 2014 — scaffolding ill-structured problems `[ill-structured-problems]`

Belland, B. R. (2014). *Instructional Scaffolding in STEM Education: Strategies and Efficacy Evidence*. Springer. (Also Belland, Walker, Kim & Lefler 2017 meta-analysis in *Review of Educational Research* 87(2): 309–344 for the effect-size synthesis.)

- **Headline effect (Belland et al. 2017 meta-analysis of computer-based scaffolding for STEM cognitive outcomes):** g = 0.46 (95% CI 0.36–0.55), 144 studies. Scaffolding works.
- **The conditions:** Effects are larger when scaffolding is **contextualized** (specific to the problem), **fades** over time (less support as competence grows), and addresses **conceptual** rather than purely procedural support. Generic scaffolding ("here's a worksheet") produces smaller effects than scaffolding embedded in the work.
- **For Glimmer:** A Glimmer that asks "design a clinical protocol for X" without scaffolding is asking a novice to perform an ill-structured task without the supports the literature says are necessary. The AI reviewer (§3) is one form of contextualized scaffolding. The rubric is another. The chapter should be explicit: the *design* of the Glimmer is the scaffolding; without it, the assignment is a setup for novice underperformance.

### 1.7 Hmelo-Silver 2004 — PBL synthesis `[PBL]`

Hmelo-Silver, C. E. (2004). "Problem-Based Learning: What and How Do Students Learn?" *Educational Psychology Review* 16(3): 235–266. ([DOI: 10.1023/B:EDPR.0000034022.16470.f3](https://link.springer.com/article/10.1023/B:EDPR.0000034022.16470.f3))

- The canonical synthesis of PBL outcomes. Hmelo-Silver argues PBL produces gains in **flexible knowledge, effective problem-solving skills, self-directed learning, effective collaboration, and intrinsic motivation** — but knowledge breadth is often weaker than direct instruction.
- **Effect-size context:** Aligns with Dochy et al. 2003 (see case-study-research.md): −0.22 SD on knowledge, +0.46 SD on skills. Hmelo-Silver's contribution is the mechanism — *why* PBL produces this trade.
- **For Glimmer:** The cumulative term-project emergence in Glimmer is closer to a PBL effect than a GLA effect. But Glimmer differs from PBL in one critical way: in PBL, the driving question is **announced** at the start, and the project's purpose is visible from session one. In Glimmer, the project's structure is **hidden** until week 10–11. This is a meaningful design divergence (see §4).

### 1.8 Chen & Yang 2019 — PBL meta-analysis `[PBL]`

Chen, C.-H., & Yang, Y.-C. (2019). "Revisiting the Effects of Project-Based Learning on Students' Academic Achievement: A Meta-Analysis Investigating Moderators." *Educational Research Review* 26: 71–81. ([DOI: 10.1016/j.edurev.2018.11.001](https://www.sciencedirect.com/science/article/abs/pii/S1747938X18301027))

- **Design:** 46 studies, 30 effect sizes after de-duplication, K–university learners.
- **Headline effect:** PBL vs. traditional instruction on academic achievement: **g = 0.71** (medium-to-large). Moderators: effects larger in social science than STEM, larger in primary than secondary, larger when project duration is 4 weeks to one semester (not shorter, not longer), larger when technology support is present.
- **For Glimmer:** This is the cleanest positive effect-size for sustained project work. But the cited studies are predominantly *announced* PBL — the learner knew they were doing a project. The transfer of this effect to *emergent* projects (Glimmer's design) is **not directly supported by the meta-analysis**. The chapter should report the g = 0.71 as PBL's general effect and flag the divergence explicitly.

### 1.9 Lin & Mintzes 2010 — concept mapping vs. generative tasks `[generative-learning]`

Lin, H., & Mintzes, J. J. (2010). "Learning Argumentation Skills Through Instruction in Socioscientific Issues: The Effect of Ability Level." *International Journal of Science and Mathematics Education* 8(6): 993–1017. (Also see Nesbit & Adesope 2006 meta-analysis on concept mapping: *Review of Educational Research* 76(3): 413–448.)

- **Nesbit & Adesope 2006** (the major meta-analysis for concept mapping): 55 studies, effect sizes for concept-map construction vs. typical activities (reading, lecture, discussion): **d ≈ 0.74** on knowledge retention; d ≈ 0.81 on transfer. Concept-map construction beats outline construction by about d = 0.30.
- **For Glimmer:** If a Glimmer assignment is "build a concept map of how X connects to Y," the effect-size literature suggests this is a high-utility generative activity. If it is "produce a creative artifact that synthesizes X and Y," the literature is less clear — the closer the activity is to mapping/diagramming the structure, the more directly the evidence applies.

### 1.10 Roelle & Berthold — generative summarization vs. comprehension testing `[generative-learning]`

Roelle, J., & Berthold, K. (2017). "Effects of Incorporating Retrieval Into Learning Tasks: The Complexity of the Tasks Matters." *Learning and Instruction* 49: 142–156. (Also Roelle, Lehmkuhl, Beck & Berthold 2015 in *Journal of Educational Psychology* 107(2): 528–545.)

- **The finding:** When generative summarization tasks are pitted against retrieval-based comprehension tests, the comparison depends on task complexity. For simple material, retrieval wins on retention. For complex material requiring integration, generative summarization (when scaffolded) produces stronger transfer.
- **For Glimmer:** Glimmer assignments target complex integration. The Roelle & Berthold pattern suggests this is the domain where generative work has its strongest comparative advantage — but only with scaffolding. The AI reviewer is plausibly that scaffold.

### 1.11 Effect sizes consolidated by construct class

| Construct | Outcome | Effect | Source |
|---|---|---|---|
| GLA: self-explanation | Retention + transfer | d ≈ 0.55 | Fiorella & Mayer 2016 |
| GLA: summarization | Retention | d ≈ 0.50 | Fiorella & Mayer 2016 |
| GLA: concept mapping | Retention | d ≈ 0.74 | Nesbit & Adesope 2006 |
| Elaborative interrogation | Delayed retention | d ≈ 0.40–0.75 | Pressley et al. 1992; Dunlosky et al. 2013 |
| ISP scaffolding (STEM) | Cognitive outcomes | g = 0.46 | Belland et al. 2017 |
| PBL (announced) | Academic achievement | g = 0.71 | Chen & Yang 2019 |
| PBL (announced) | Knowledge breadth | d ≈ −0.22 | Dochy et al. 2003 |
| PBL (announced) | Skills application | d ≈ +0.46 | Dochy et al. 2003 |
| PBL (emergent) | Any outcome | **No direct evidence** | — |
| AI formative feedback on writing | Revision quality | d ≈ 0.30–0.50 `[verify]` | See §3 |

The bottom row is the honest gap. Glimmer's *session-level* design is best supported by the ISP and GLA literatures. Its *term-level emergent* design has no direct meta-analytic evidence base — the closest analogs are writing-process pedagogy (§4) and the implicit-curriculum literature in clinical education (§5).

---

## 2. Design principles — what makes a creative assignment *genuinely generative*

### 2.1 The Wittrock/Fiorella & Mayer distinction operationalized `[generative-learning]`

The Fiorella & Mayer 2016 review names three conditions for generative activities to produce learning gains:

1. **Prerequisite knowledge sufficient to generate.** A learner with no schema for "clinical protocol" cannot generate one; they can only restate prompts.
2. **Motivation to engage in genuine generation.** A learner who knows the assignment is graded on length will produce length, not generation.
3. **Scaffolding that constrains the generation space.** Open prompts produce wandering; constrained prompts force selection.

The **test of whether a Glimmer is genuinely generative** rather than a disguised literature review: ask whether the learner's output contains a *relation* that did not exist on the page. Not a restatement. Not a selection. A new connection.

### 2.2 Scaffolding and the expertise-reversal effect — Kalyuga et al. 2003 `[ill-structured-problems]` `[failure-mode]`

Kalyuga, S., Ayres, P., Chandler, P., & Sweller, J. (2003). "The Expertise Reversal Effect." *Educational Psychologist* 38(1): 23–31.

- **The effect:** Instructional supports that help novices *hurt* experts and vice versa. A worked example helps a learner who cannot yet generate a solution; the same worked example wastes the time of a learner who can. The reverse holds for open problems.
- **For Glimmer:** A heavily scaffolded Glimmer prompt (the AI reviewer asks specific structured questions) is what novices need and what experts will find redundant. A sparse prompt (the learner generates the entire structure) is what experts need and what novices will experience as the abyss. Medhavy's contextual bandit (chapter 4) is supposed to handle this — selecting Glimmer's level of structure based on the learner's current competence at the concept node. **Whether the bandit can actually calibrate this is the open empirical question chapter 4 names honestly.**

### 2.3 Specificity as a rubric dimension — Anderson & Krathwohl, Berliner `[foundational-theory]`

- Anderson, L. W., & Krathwohl, D. R. (Eds.) (2001). *A Taxonomy for Learning, Teaching, and Assessing: A Revision of Bloom's Taxonomy of Educational Objectives*. Longman. The revised Bloom's separates the *cognitive process* (Remember, Understand, Apply, Analyze, Evaluate, Create) from the *knowledge type* (Factual, Conceptual, Procedural, Metacognitive). Specificity is operationalized as the precision of the verb-noun pair in objectives: "explain the difference between X and Y" is specifiable; "understand X" is not.
- **Berliner 2001** ("Learning About and Learning From Expert Teachers," *International Journal of Educational Research* 35(5): 463–482): expert teachers describe their practice with more specific, more contextual, more conditional detail than novices. Specificity in description tracks expertise.
- **For Glimmer:** Specificity as a rubric dimension is well-grounded in the assessment literature. It is the operational signal that the learner has moved from "understand the concept" to "apply the concept to a particular case." A rubric that rewards specificity is rewarding the move from inert knowledge to usable knowledge.

### 2.4 The Glimmer rubric vs. AAC&U VALUE rubrics `[generative-learning]` `[ill-structured-problems]`

The Association of American Colleges and Universities VALUE rubrics (2009, ongoing revision) are the closest validated analog to Medhavy's Glimmer rubric. Three are directly relevant:

- **Critical Thinking VALUE rubric.** Dimensions: explanation of issues, evidence, influence of context and assumptions, student's position (perspective, thesis/hypothesis), conclusions and related outcomes. (Source: AAC&U, accessible at [aacu.org/value-rubrics](https://www.aacu.org/value-rubrics).)
- **Creative Thinking VALUE rubric.** Dimensions: acquiring competencies, taking risks, solving problems, embracing contradictions, innovative thinking, connecting/synthesizing/transforming.
- **Inquiry and Analysis VALUE rubric.** Dimensions: topic selection, existing knowledge/research/views, design process, analysis, conclusions, limitations and implications.

**Mapping Medhavy's rubric onto these:**

| Glimmer dimension | Closest VALUE dimension |
|---|---|
| WHY | Critical Thinking: "student's position" + Inquiry: "topic selection" |
| Usefulness | Inquiry: "conclusions" + Critical Thinking: "conclusions and related outcomes" |
| Mechanism | Critical Thinking: "evidence" + Inquiry: "analysis" |
| Defensibility | Critical Thinking: "student's position" + "evidence" |
| Specificity | (Implicit across all three; explicit in Inquiry: "design process") |

The mapping is good. Glimmer is essentially a Critical Thinking + Inquiry rubric with specificity pulled out as its own dimension. This is defensible — the specificity move is one of the things that distinguishes a useful Glimmer from a vague one, and the VALUE rubrics treat it as implicit when it should arguably be explicit.

- **Reeves & Newton on assessment of elaborated reasoning** (Reeves 2000, "Validity Issues for Performance-Related Rubrics," *Education Policy Analysis Archives* 8(31), and related work): rubrics that distinguish elaborated reasoning from summary require dimensions that *cannot be satisfied by quotation*. Defensibility and mechanism are both such dimensions — you cannot quote yourself into defending a position, and you cannot quote yourself into explaining a mechanism. The Glimmer rubric, on this read, is well-designed against the failure mode of "lengthy restatement scoring well."

### 2.5 The PBL design principles — Krajcik & Blumenfeld 2006 `[PBL]`

Krajcik, J. S., & Blumenfeld, P. C. (2006). "Project-Based Learning." In R. K. Sawyer (Ed.), *The Cambridge Handbook of the Learning Sciences* (pp. 317–333). Cambridge University Press.

- **Five features of well-designed PBL:** A **driving question** that frames the project, **situated inquiry** (real-world relevance), **collaboration** (peer/expert), **scaffolded learning technologies**, and **artifact creation** that allows public sharing.
- **For Glimmer:** Glimmer has artifact creation. Glimmer has scaffolded learning technologies (the AI reviewer). Glimmer has situated inquiry when the Glimmer is concretely anchored. Glimmer does *not* have collaboration (it is solo work). Glimmer does *not* have an announced driving question (the project emerges).
- **The honest read:** Glimmer is PBL minus the two features Krajcik & Blumenfeld treat as load-bearing. The Medhavy design is making a bet that the artifact + scaffolding pair carries enough of the effect for the design to work. **This bet is not directly supported by the PBL literature.**

---

## 3. AI as pre-grading reviewer

### 3.1 The Hattie & Timperley feedback framework `[feedback]`

Hattie, J., & Timperley, H. (2007). "The Power of Feedback." *Review of Educational Research* 77(1): 81–112. ([DOI: 10.3102/003465430298487](https://journals.sagepub.com/doi/10.3102/003465430298487))

- **The three levels:** Feed Up (where am I going? — clarifying goals), Feed Back (how am I doing? — current performance against goals), Feed Forward (where to next? — actions for improvement).
- **The four foci:** Task level (correctness), Process level (the strategy used), Self-regulation level (the metacognitive monitoring), and Self level (praise/blame about the person). Process and self-regulation feedback produce the largest effects; task feedback produces small-to-moderate effects; self-level feedback produces near-zero or negative effects.
- **For Glimmer's AI reviewer:** The Medhavy design — AI asks questions about the **weakest part of the learner's reasoning** — operates primarily at the **process level** ("why is your mechanism explanation thin here?") and the **self-regulation level** ("can you defend this choice against this counter-example?"). It is doing exactly the kind of feedback Hattie & Timperley identify as highest-effect. The deliberate avoidance of task-level "right answer" feedback aligns with the Khanmigo design stance (see §3.4) — though for a different reason.
- **What level is "Feed Forward"?** The AI reviewer's questions are simultaneously Feed Back (here's what's weak) and Feed Forward (here's what to address). They do not Feed Up — the learner does not see the term-project destination. This is a *deliberate* divergence (see §4) but one that breaks one leg of the Hattie & Timperley framework.

### 3.2 Iterative revision in writing — Graham, Hebert, Harris 2015 `[feedback]`

Graham, S., Hebert, M., & Harris, K. R. (2015). "Formative Assessment and Writing: A Meta-Analysis." *Elementary School Journal* 115(4): 523–547. (Also Graham, Harris & Hebert 2011 in *Carnegie Corporation report* on writing assessment.)

- **Headline:** Formative assessment of writing produces meta-analytic effects of **d ≈ 0.40–0.50** on writing quality, with larger effects when feedback addresses **process** (organization, argument) rather than **mechanics** (spelling, grammar).
- **The Graham 2015 specifics:** Feedback that *asks the writer questions* about their work outperforms feedback that *tells* the writer what is wrong. The questioning move forces the writer to do the diagnostic work themselves — converting feedback into elaborative interrogation.
- **For Glimmer:** This is the empirical foundation closest to what Medhavy's AI reviewer does. AI asking "what is your strongest reason here?" is structurally identical to the questioning-feedback moves in Graham 2015. The effect-size expectation is moderate (~d = 0.40) on revision quality, with the caveat that the Graham work is about *writing teachers* asking questions, not AI.

### 3.3 Peer-review-as-revision-prompt — Cho & MacArthur `[feedback]`

- Cho, K., & MacArthur, C. (2010). "Student Revision With Peer and Expert Reviewing." *Learning and Instruction* 20(4): 328–338.
- Cho, K., & MacArthur, C. (2011). "Learning by Reviewing." *Journal of Educational Psychology* 103(1): 73–84.
- **The findings:** Multiple peer reviews produce revision quality equal to or better than single expert reviews — *and* reviewing others' work improves the reviewer's own writing, an additional generative effect. The mechanism is that reviewing forces the reviewer to operationalize criteria they would otherwise leave implicit.
- **For Glimmer:** The translation to AI is non-trivial. AI as reviewer can produce the question-asking effect (Graham 2015) but cannot replicate the *reviewer-as-learner* effect Cho & MacArthur identify — the AI does not learn from reviewing. This is a real limit; the chapter should not claim Medhavy's AI pre-grading captures the full Cho & MacArthur benefit.

### 3.4 AI as Socratic interlocutor `[feedback]` `[failure-mode]`

- **Khanmigo's design stance** (Khan Academy 2023–2026): the tutor "won't give the answer." This is a deliberate constraint, designed to force learner generation. The 2026 admission (chapter 1 of this book) is that **the constraint produced compliance without learning** — students reported the tutor was annoying, learning outcomes did not move. The mechanism: avoiding answers is not the same as asking productive questions. A tutor that refuses to answer but does not redirect productively produces frustration, not generation.
- **Bastani et al. 2025** (preprint; "GPT-Tutor: Generative AI for Personalized Education at Scale" `[verify exact title and outlet]`): a GPT-based tutor designed to scaffold problem-solving in undergraduate mathematics. Reports learning gains over a control condition but with strong caveats about which question types the tutor handles well and which it confabulates on. The chapter should cite this carefully — the AI-tutor evidence base in 2025–2026 is shifting fast and many headline claims have not been replicated.
- **For Glimmer:** The AI reviewer is *not* a Socratic tutor in the answer-refusing sense. It is a questioner targeting weakness — closer to a thesis-advisor mode than a Socratic-dialogue mode. This is a real design choice and should be named. The reviewer's job is **diagnosis**, not pedagogy. The pedagogy is the learner's revision in response to the diagnosis.

### 3.5 AI feedback effect sizes — the thin literature `[feedback]`

The peer-reviewed literature on AI formative feedback specifically (as distinct from automated essay scoring or rule-based formative systems) is recent and thin.

- **Steiss et al. 2024** ("Comparing the Quality of Human and ChatGPT Feedback of Students' Writing." *Learning and Instruction* 91: 101894 `[verify volume]`): ChatGPT-generated feedback on student writing was rated by trained human raters as comparable in quality to human teacher feedback on most dimensions, weaker on emotional support, stronger on specificity. Sample of student writing in middle/high school.
- **Vendor claims about Grammarly, Turnitin's AI feedback, etc.:** Most cite proprietary studies with non-public methodology. Tagged here as `[vendor]` — do not use as primary evidence.
- **Cognitive offloading concerns** (Brown, Lin et al. 2025 `[verify]`; the broader cognitive-offloading literature originating in Sparrow, Liu & Wegner 2011 "The Memory Effects of Search Engines on Memory," *Science* 333(6043): 776–778): the worry is that AI feedback creates dependence — learners stop generating their own critique because the AI will. **For Glimmer**: this is a real risk. The design mitigation is that AI feedback is *pre-grading*, not the grade. The learner revises in response to AI questions; the instructor grades the revision. This preserves the learner-revises-themselves loop that Graham 2015 shows is the actual mechanism.

**The honest read:** AI as Socratic pre-grading reviewer is a *plausible* extension of well-established formative-feedback principles to a new mode of delivery. It is **not** an evidence-base; the empirical work is two to three years young, much of it preprint, much of it under sample sizes that would not survive peer review for an established intervention. The chapter should name this thinness rather than paper over it with vendor claims.

---

## 4. Term-project emergence — the hidden destination question

### 4.1 The closest practical analog: writing-process pedagogy `[emergent-portfolio]`

The Glimmer's term-level design — accumulated fragments that compose into a substantial project the learner doesn't know they're building until week 10–11 — has no direct PBL evidence base. The closest practical analog is the writing-process pedagogy tradition, where the final product emerges from accumulated drafts and the writer often does not know the destination at the start.

- **Murray, D. M. (1972).** "Teach Writing as a Process Not Product." *The Leaflet* 71(3): 11–14. The foundational article. "When students complete a draft, they think they are finished... Writing is rewriting." Murray argued the final form emerges from accumulating, cutting, reorganizing — the writer discovers what they think by writing what they don't yet think.
- **Elbow, P. (1973).** *Writing Without Teachers*. Oxford University Press. The "growing-and-cooking" metaphor: writing grows by accumulation (no judgment), then cooks (selection and revision). The destination is not known at the start; it is discovered in the cooking.
- **Flower, L. S., & Hayes, J. R. (1981).** "A Cognitive Process Theory of Writing." *College Composition and Communication* 32(4): 365–387. The cognitive-process model: planning, translating, reviewing — recursive, not linear. Writers revise their goals during the process; the destination *changes* as writing proceeds.
- **For Glimmer:** Writing-process pedagogy provides the deepest theoretical and empirical foundation for emergent-product design. The mechanism — that accumulation without a fixed destination produces genuine discovery rather than execution of a pre-formed plan — is the mechanism Glimmer is borrowing.
- **The empirical evidence for writing-process pedagogy:** Mixed and contested. Hillocks (1986) *Research on Written Composition* meta-analysis found process-oriented writing instruction produced moderate gains over traditional instruction, but the largest effects came from *environmental* (structured task) approaches rather than pure free-form process. The straight Murray/Elbow free-write approach produced gains over no-instruction but smaller gains than scaffolded approaches. **The translation for Glimmer:** scaffolding matters; pure emergence without structure does not reliably outperform structured project work.

### 4.2 Goal-setting theory — Locke & Latham `[foundational-theory]`

Locke, E. A., & Latham, G. P. (2002). "Building a Practically Useful Theory of Goal Setting and Task Motivation: A 35-Year Odyssey." *American Psychologist* 57(9): 705–717. Also Locke & Latham 1990 *A Theory of Goal Setting and Task Performance*.

- **The core findings:** Specific, difficult, accepted goals produce higher performance than vague or easy goals. Goal commitment is essential. Feedback during pursuit is essential.
- **The tension with Glimmer:** Locke & Latham's theory predicts that *hiding* the goal (the term project) reduces commitment to it, reduces specific goal-directed effort, and removes the feedback-against-goal signal. This is a real theoretical critique of Glimmer's emergent design.
- **The reconciliation Medhavy implicitly offers:** Each Glimmer *session* has a specific, difficult, immediate goal (the assignment for the week). The session-level goals satisfy Locke & Latham. The term-level emergence is layered on top — the cumulative effect is a byproduct of well-set session goals, not the focus of learner attention. Whether this layering preserves the goal-setting effect or undermines it is **an empirical question Medhavy is running**, not a settled finding.

### 4.3 Self-determination theory — Deci & Ryan `[foundational-theory]`

Deci, E. L., & Ryan, R. M. (2000). "The 'What' and 'Why' of Goal Pursuit: Human Needs and the Self-Determination of Behavior." *Psychological Inquiry* 11(4): 227–268.

- **Three needs:** autonomy, competence, relatedness. Intrinsic motivation is highest when all three are supported.
- **For Glimmer's emergent design:** Hiding the term-project structure could be read two ways under SDT:
  - **Pro-autonomy:** The learner experiences each session as a freely chosen creative task, not as compliance toward a pre-set destination. The autonomy support is high session-by-session.
  - **Anti-autonomy:** The learner cannot make informed choices about effort allocation because they cannot see the destination. Autonomy requires information.
  - **My reading:** SDT is genuinely ambiguous about emergent designs. The "autonomy support" research (Reeve & Jang 2006, etc.) is mostly about *moment-to-moment* choice and rationale, not about *strategic* goal visibility. The chapter should not claim SDT support either way without overreach.

### 4.4 Threshold effects and chunking — Bransford, Brown, Cocking; Chi 1981 `[foundational-theory]`

- **Bransford, J. D., Brown, A. L., & Cocking, R. R. (Eds.) (2000).** *How People Learn: Brain, Mind, Experience, and School*. National Academy Press.
- **Chi, M. T. H., Feltovich, P. J., & Glaser, R. (1981).** "Categorization and Representation of Physics Problems by Experts and Novices." *Cognitive Science* 5(2): 121–152.
- **The Chi 1981 finding:** Experts categorize physics problems by deep structure (conservation principle, type of force); novices categorize by surface features (inclined plane, pulley). Expertise is reorganization of knowledge, not addition of facts.
- **For Glimmer:** The cumulative emergent project, if it works, produces a knowledge-reorganization moment in week 10–11 — the learner sees the structural connections across what they have been doing. This is functionally a chunking moment in the Chi 1981 sense. **If** the moment lands, the gain is exactly the expertise-reorganization gain the cognitive-science literature predicts. If it does not land (the learner reaches week 11 and sees only a pile of unrelated fragments), the design fails.

### 4.5 The honest empirical read on emergent vs. announced project structures `[emergent-portfolio]` `[PBL]`

Direct comparison studies of *announced* vs. *emergent* project structures in formal education are essentially nonexistent in the peer-reviewed literature. The closest evidence is:

- **Hidden curriculum studies in medical education** (Hafferty 1998 in *Academic Medicine*; Hafler et al. 2011): show that students learn substantial structure from accumulated experience that was not made explicit — but the evidence is observational, not interventional, and the "hidden" content is typically *professional values*, not *project skills*.
- **Implicit learning literature** (Reber 1989 in *Journal of Experimental Psychology: General*; ongoing work): people can learn complex structural patterns without conscious awareness, sometimes more durably than with awareness. This supports the *plausibility* of Glimmer's design but does not validate it as superior to announced PBL.
- **The verdict:** Glimmer's emergent-portfolio design is theoretically defensible — writing-process pedagogy, expert chunking, SDT autonomy, implicit learning all provide *plausibility* — but is not directly evidenced as superior to announced project work. The chapter should claim plausibility and design rationale, not effect-size advantage.

---

## 5. Clinical and medical applications

### 5.1 Clinical reasoning assessment in open-ended formats `[clinical]`

- **Norman, G. (2005).** "Research in Clinical Reasoning: Past History and Current Trends." *Medical Education* 39(4): 418–427. The canonical synthesis. Norman's central finding: clinical reasoning is **case-specific**, not domain-general. The skilled diagnostician's competence is "encapsulated" patterns of disease presentation, accessed by pattern-match against current case, with deliberate analytic reasoning called in as backup.
- **Eva, K. W. (2005).** "What Every Teacher Needs to Know About Clinical Reasoning." *Medical Education* 39(1): 98–106. The companion teaching synthesis. Eva argues think-aloud protocols and structured reflection are the most defensible methods for *assessing* clinical reasoning, because reasoning quality is invisible from outcome alone (you can get the right diagnosis with wrong reasoning, or wrong with right).
- **For Glimmer:** A Glimmer that asks for clinical protocol design or differential-diagnosis reasoning maps onto exactly this assessment problem. The Glimmer rubric (especially mechanism + defensibility) is a structured way to capture what Eva 2005 says think-aloud protocols capture: not whether the answer is right, but whether the reasoning that produced it is defensible.

### 5.2 Competency-Based Medical Education (CBME) `[clinical]`

- **Frank, J. R., Snell, L. S., Cate, O. T., Holmboe, E. S., Carraccio, C., Swing, S. R., et al. (2010).** "Competency-Based Medical Education: Theory to Practice." *Medical Teacher* 32(8): 638–645.
- **AAMC and CanMEDS frameworks:** Define competencies (Patient Care, Medical Knowledge, Practice-Based Learning, etc.) and require assessment of authentic performance, not just knowledge recall. Entrustable Professional Activities (EPAs; ten Cate 2005) translate competencies into observable units of clinical work.
- **For Glimmer:** A Glimmer assignment in a clinical course is functionally an EPA-aligned authentic assessment. The five Glimmer dimensions (WHY / usefulness / mechanism / defensibility / specificity) are compatible with the entrustment-decision logic of CBME — "can this learner be trusted to perform this clinical activity unsupervised?" requires evidence of mechanism understanding and defensibility of choices, not just exam performance.

### 5.3 Protocol-design assignments in medical education `[clinical]`

Peer-reviewed literature on *clinical protocol design as a student assignment* is genuinely thin. The closest evidence base:

- **Quality Improvement (QI) curricula:** The Institute for Healthcare Improvement Open School (founded 2008) provides QI training, often culminating in a student-designed QI project. **Wong et al. 2010** ("Teaching Quality Improvement and Patient Safety to Trainees: A Systematic Review." *Academic Medicine* 85(9): 1425–1439) reviewed 41 studies of QI training and found moderate evidence of skill gains but limited evidence of patient-outcome effects.
- **Patient-safety projects:** The IHI Open School framework explicitly uses creative project design as a capstone. The pedagogical model is closer to PBL than to GLA. Effect sizes for QI/patient-safety project work on long-term professional behavior are largely unknown.
- **CanMEDS Scholar and Professional roles:** The Royal College of Physicians and Surgeons of Canada CanMEDS framework includes "Scholar" (engaging in scholarly inquiry) and "Professional" (commitment to ethical practice and quality improvement). Both are typically assessed via project work, but standardized rubrics are not widely validated.
- **For Glimmer in clinical education:** The evidence base for *creative cumulative assignments in medical education specifically* is much thinner than the GLA, ISP, or PBL literatures. Most clinical creative-assignment evidence is descriptive (curriculum case reports) rather than comparative. The chapter should be explicit: applying Glimmer to clinical content extends a pedagogical model that has stronger evidence in other domains.

### 5.4 Where the clinical evidence is thin — say so `[clinical]`

The honest accounting:

1. AI as pre-grading reviewer in clinical education — no peer-reviewed effect sizes I can find.
2. Emergent-portfolio cumulative assignments in medical education — descriptive case reports only.
3. AI-graded protocol-design rubrics for clinical learners — no validated rubrics in the published literature `[verify]`.
4. The five-dimension Glimmer rubric applied to clinical reasoning — novel; would need its own validation work.

The chapter should treat Glimmer in clinical content as **a design proposal informed by adjacent evidence**, not as an evidence-based clinical intervention. The instrumentation Medhavy is building is what would produce the validation; the validation is not in.

---

## 6. Failure modes — the anxiety question

### 6.1 The expertise-reversal effect applied to creative work `[failure-mode]` `[ill-structured-problems]`

Kalyuga et al. 2003 (introduced in §2.2) directly predicts a failure mode for Glimmer:

- **Novice with unscaffolded open assignment** = performance below scaffolded alternative.
- **Expert with heavily scaffolded assignment** = wasted time, boredom, possible disengagement.

A Glimmer that is appropriately scaffolded for a novice will under-challenge an expert. A Glimmer that challenges an expert will overwhelm a novice. The bandit (Medhavy 2.0) is supposed to calibrate. Until the bandit runs, calibration depends on the professor's design choices and the AI reviewer's adaptiveness.

**The risk:** A learner who experiences three Glimmers above their current scaffolding-need disengages from the mode entirely. The pattern Medhavy must avoid: students opting out of Glimmer (saying "this is too hard / too vague / not for me") and concentrating on Quiz Me, which feels more tractable. This would produce a population-level result where Glimmer is the under-used mode, *not because it is ineffective*, but because the scaffolding calibration failed at the start.

### 6.2 Self-efficacy and productive struggle — Bandura `[failure-mode]` `[foundational-theory]`

- **Bandura, A. (1997).** *Self-Efficacy: The Exercise of Control*. W.H. Freeman.
- **The mechanism:** Self-efficacy — belief in one's capacity to execute a task — predicts engagement, persistence under difficulty, and performance. Self-efficacy is built primarily by **mastery experiences** (succeeding at difficult tasks), reinforced by **vicarious experiences** (seeing similar others succeed), **verbal persuasion**, and **physiological state**.
- **The boundary:** Productive struggle (Sweller's "desirable difficulty," Bjork's "desirable difficulty," the Vygotskian zone of proximal development) requires difficulty *within reach*. Demoralizing struggle is difficulty *beyond reach*. The boundary is set by the learner's current self-efficacy, not by the task's objective difficulty.
- **For Glimmer:** A learner with low domain self-efficacy entering a Glimmer cold will experience the assignment's openness as evidence they cannot do it. A learner with calibrated self-efficacy will experience the same openness as space to operate. The AI reviewer must be designed not to *reduce* self-efficacy by emphasizing weakness without affirming progress — the Hattie & Timperley "self-level" feedback warning applies (§3.1).

### 6.3 The Hidi & Renninger four-phase interest model `[failure-mode]` `[foundational-theory]`

Hidi, S., & Renninger, K. A. (2006). "The Four-Phase Model of Interest Development." *Educational Psychologist* 41(2): 111–127.

- **Four phases:** Triggered situational interest → Maintained situational interest → Emerging individual interest → Well-developed individual interest.
- **The progression:** Early phases are externally triggered (a vivid example, an unexpected question). Later phases are internally maintained (the learner returns to the content of their own accord). Transitions require both *content* features (depth, complexity, structure) and *learner* features (knowledge, value).
- **For Glimmer:** Emergent project work likely operates well for learners in *emerging* or *well-developed individual interest* — they care about the content enough to invest in cumulative work whose payoff is uncertain. For learners in *triggered* or *maintained situational* phases, the emergent design may underperform announced design — they need the visible destination to maintain engagement. **The risk:** Glimmer's design assumes a level of intrinsic engagement that not all learners enter the course holding.

### 6.4 Pekrun's control-value theory of achievement emotions `[failure-mode]` `[foundational-theory]`

Pekrun, R. (2006). "The Control-Value Theory of Achievement Emotions: Assumptions, Corollaries, and Implications for Educational Research and Practice." *Educational Psychology Review* 18(4): 315–341.

- **The two appraisals:** Control (can I influence the outcome?) and value (do I care about the outcome?). Their combination produces specific emotions:
  - High control + high value + positive outcome = enjoyment.
  - Low control + high value = anxiety.
  - Low control + low value = boredom.
  - High control + low value = relief (or apathy).
- **For Glimmer:** The emergent-design risk maps directly onto control-value theory. A learner who cannot see the destination (low control over how their work composes) and cares about the grade (high value) is in the **anxiety quadrant**. This is the modal Pekrun prediction for the modal student given Glimmer's design. The mitigation: the AI reviewer's diagnostic questions need to give the learner traction — to convert "I don't know what they want" (low control) into "I know what the reviewer is asking and I can address it" (restored control). If the AI reviewer is good, control is restored. If it is generic or off-target, anxiety is the predicted emotion.

### 6.5 Open-ended assignment anxiety — the empirical picture `[failure-mode]`

The peer-reviewed literature on student anxiety specifically in response to *open-ended creative* assignments is patchy. Some signal:

- **Ill-structured-problem anxiety:** Jonassen 2011 (in *Learning to Solve Complex Scientific Problems*, Routledge) notes that ill-structured problems consistently produce higher self-reported anxiety than well-structured problems, with the gap larger for low-prior-knowledge learners.
- **Creative-assignment anxiety in design education:** Daly, Adams & Bodner 2012 ("What Does It Mean to Design? A Qualitative Investigation of Design Professionals' Experiences." *Journal of Engineering Education* 101(2): 187–219) document recurring "what do they want?" anxiety even among advanced design students. Design education has long known this; their answer is heavy critique-based feedback culture, which Glimmer is trying to replicate in AI form.
- **The translation:** Glimmer-style open creative work is *expected* to produce more anxiety than tractable retrieval practice. The design question is whether the anxiety is **productive** (motivates engagement with feedback) or **demoralizing** (motivates disengagement). The literature does not give a universal answer; it gives a moderator: learners with prior generative-work experience tolerate ambiguity; novices to generative work do not.

### 6.6 The single most consequential anxiety failure mode for Medhavy to address `[failure-mode]`

Across the failure-mode literatures, the consistent prediction is:

> **First-generation Glimmer users in early weeks of a course will experience the open assignment as evidence they cannot do the work, will under-engage with the AI reviewer's feedback (because feedback emphasizing weakness without restoring agency confirms their initial appraisal), and will optimize their effort toward Quiz Me as the mode that feels controllable. The effect will be a population where Glimmer is the under-used mode by design failure, not by content failure.**

This is the *modal* predicted failure. The design mitigation is in three places: scaffolding calibration (so early Glimmers are within reach), AI-reviewer feedback quality (so feedback restores rather than undermines control), and explicit teacher framing (so students know the cognitive purpose). All three need to work; none is provided in the Medhavy chapters I read as a fully solved problem.

---

## 7. The Medhavy Glimmer in its own documents — characterization and divergence map

### 7.1 What Medhavy's chapters actually say about Glimmer

From `chapters/01-what-is-medhavy.md`:
> "Glimmer — A creative, non-trivial assignment that scaffolds forward without the student knowing where it's going. Each Glimmer session builds a piece of work that, over the term, assembles into a substantial project. The student doesn't experience this as 'building a term project.' They experience it as an interesting assignment this week. The cumulative product is the evidence of genuine integration — the kind of work you can only produce if you actually understand the material."

From `chapters/04-what-makes-this-different.md`:
> "Glimmer is a creative non-trivial assignment that scaffolds forward without the student knowing where it's going — each session adds a piece that assembles, over the term, into substantial project work the student doesn't know they're building."

> "Glimmer activates creative integration and metacognitive reflection — appropriate when the components need to be assembled into something the learner couldn't produce from any single component alone."

From `chapters/06-medhavy-conducting-ai.md`:
> "The Glimmer assignment that builds into a term project the learner doesn't know they're building — because synthesis across concepts is the evidence of understanding that transfer requires."

From the task brief (the design specification for this research note):
- Each Glimmer is "a creative proposal or design task anchored to a specific concept."
- Rubric dimensions: WHY / usefulness / mechanism / defensibility / specificity.
- Multiple Glimmers compose into a term project; the learner does not know until week 10–11.
- Before instructor grading, an AI reviewer asks questions about the weakest part of the learner's reasoning.

### 7.2 Construct mapping — confidence rating: high

**The Glimmer is most closely an Ill-Structured Problem (Jonassen 1997, 2000) at the session level, layered into an emergent-portfolio design (writing-process pedagogy: Murray, Elbow, Flower & Hayes) at the term level, with AI-mediated formative interrogation (Graham 2015; Hattie & Timperley 2007) bridging the two.**

It is **not** primarily a Generative Learning Activity in the Fiorella & Mayer 2016 sense, though it contains generative elements (self-explanation, mapping). The Fiorella & Mayer effect sizes apply to *brief, internal-product* activities; Glimmer is sustained external-product creative work.

It is **not** primarily Elaborative Interrogation, though the AI reviewer step is structurally EI applied to the learner's own reasoning rather than to studied material.

It is **not** standard PBL, because PBL announces the driving question. Glimmer hides it.

The cleanest construct-fit ranking, with confidence:

1. **Ill-Structured Problem (session-level): high confidence.** The rubric is an ISP rubric. The task type (design, propose, anchor to a specific concept) is paradigmatic ISP. Belland's scaffolding evidence applies.
2. **Emergent-portfolio writing pedagogy (term-level): medium-high confidence.** The mechanism — cumulative fragments composing into a discovered final form — is exactly Murray/Elbow. The empirical evidence is contested but the theoretical fit is clean.
3. **PBL minus driving question, minus collaboration: medium confidence.** Useful for inheriting PBL effect-size ballpark (g ≈ 0.7 in Chen & Yang) but with two load-bearing PBL features missing.
4. **GLA: lower confidence.** Some session-level overlap with self-explanation and mapping. Not the dominant frame.

### 7.3 Divergences from the canonical evidence base for the matched construct

Where Glimmer diverges from canonical ISP / emergent-portfolio / PBL designs, and what each divergence costs or buys:

| Divergence | What it borrows from | What it costs | What it buys |
|---|---|---|---|
| Solo (not collaborative) | Writing-process pedagogy | PBL's peer-review-as-learning effect (Cho & MacArthur); collaboration evidence in Krajcik & Blumenfeld | Cleaner causal attribution; works in solo platform |
| Hidden destination | Writing-process pedagogy; implicit learning | Locke & Latham goal-setting clarity; Hattie & Timperley Feed-Up channel | Possible reduction in performance-trap behavior; preserves curiosity |
| AI as pre-grading reviewer | Graham 2015 questioning feedback; Hattie & Timperley process feedback | Cho & MacArthur reviewer-as-learner effect (cannot transfer to AI) | Scale; consistency; immediate availability |
| Five-dimension rubric (WHY/usefulness/mechanism/defensibility/specificity) | VALUE rubrics; Jonassen defensibility criterion | Familiarity; widely validated alternative rubrics | Operational alignment with Medhavy's other measurement (GLP) |
| Concept-anchored (not free-topic) | ISP scaffolding evidence | Some autonomy reduction | Tight coupling to curriculum design layer; assessability |

The divergence-cost-benefit table is the honest map. The hidden-destination divergence is the largest single bet — it is theoretically defensible from writing-process and implicit-learning evidence, but it is not directly supported by ISP or PBL effect-size work.

---

## 8. The sharpest finding for Glimmer design, in one sentence

> **The Glimmer is an ill-structured problem with an emergent-portfolio scaffold, and the failure mode the design must address most urgently is not whether students can produce the work — it is whether the AI pre-grading reviewer's questions restore the learner's sense of control over the assignment fast enough, in the early sessions, to prevent the Pekrun anxiety-quadrant collapse that the open-design literature consistently predicts for novice learners.**

---

## 9. Key citations consolidated (Chicago author-date)

### Foundational theory

- Bandura, Albert. 1997. *Self-Efficacy: The Exercise of Control*. New York: W. H. Freeman. `[foundational-theory]`
- Bransford, John D., Ann L. Brown, and Rodney R. Cocking, eds. 2000. *How People Learn: Brain, Mind, Experience, and School*. Washington, DC: National Academy Press. `[foundational-theory]`
- Chi, Michelene T. H., Paul J. Feltovich, and Robert Glaser. 1981. "Categorization and Representation of Physics Problems by Experts and Novices." *Cognitive Science* 5 (2): 121–152. `[foundational-theory]`
- Deci, Edward L., and Richard M. Ryan. 2000. "The 'What' and 'Why' of Goal Pursuit: Human Needs and the Self-Determination of Behavior." *Psychological Inquiry* 11 (4): 227–268. `[foundational-theory]`
- Hidi, Suzanne, and K. Ann Renninger. 2006. "The Four-Phase Model of Interest Development." *Educational Psychologist* 41 (2): 111–127. `[foundational-theory]` `[failure-mode]`
- Locke, Edwin A., and Gary P. Latham. 2002. "Building a Practically Useful Theory of Goal Setting and Task Motivation: A 35-Year Odyssey." *American Psychologist* 57 (9): 705–717. `[foundational-theory]`
- Pekrun, Reinhard. 2006. "The Control-Value Theory of Achievement Emotions: Assumptions, Corollaries, and Implications for Educational Research and Practice." *Educational Psychology Review* 18 (4): 315–341. `[foundational-theory]` `[failure-mode]`
- Wittrock, Merlin C. 1974. "Learning as a Generative Process." *Educational Psychologist* 11 (2): 87–95. `[foundational-theory]`

### Generative learning

- Adesope, Olusola O., Dominic A. Trevisan, and Narayankripa Sundararajan. 2017. "Rethinking the Use of Tests: A Meta-Analysis of Practice Testing." *Review of Educational Research* 87 (3): 659–701. `[generative-learning]`
- Dunlosky, John, Katherine A. Rawson, Elizabeth J. Marsh, Mitchell J. Nathan, and Daniel T. Willingham. 2013. "Improving Students' Learning With Effective Learning Techniques: Promising Directions From Cognitive and Educational Psychology." *Psychological Science in the Public Interest* 14 (1): 4–58. `[generative-learning]` `[elaborative-interrogation]`
- Fiorella, Logan, and Richard E. Mayer. 2016. "Eight Ways to Promote Generative Learning." *Educational Psychology Review* 28 (4): 717–741. `[generative-learning]`
- Nesbit, John C., and Olusola O. Adesope. 2006. "Learning With Concept and Knowledge Maps: A Meta-Analysis." *Review of Educational Research* 76 (3): 413–448. `[generative-learning]`
- Roelle, Julian, and Kirsten Berthold. 2017. "Effects of Incorporating Retrieval Into Learning Tasks: The Complexity of the Tasks Matters." *Learning and Instruction* 49: 142–156. `[generative-learning]`

### Elaborative interrogation

- Pressley, Michael, Mark A. McDaniel, James E. Turnure, Eileen Wood, and Mariam Ahmad. 1987. "Generation and Precision of Elaboration: Effects on Intentional and Incidental Learning." *Journal of Experimental Psychology: Learning, Memory, and Cognition* 13 (2): 291–300. `[elaborative-interrogation]`
- Pressley, Michael, Eileen Wood, Vera E. Woloshyn, Vicki Martin, Alison King, and Deborah Menke. 1992. "Encouraging Mindful Use of Prior Knowledge: Attempting to Construct Explanatory Answers Facilitates Learning." *Educational Psychologist* 27 (1): 91–109. `[elaborative-interrogation]`

### Ill-structured problems

- Belland, Brian R. 2014. *Instructional Scaffolding in STEM Education: Strategies and Efficacy Evidence*. Cham: Springer. `[ill-structured-problems]`
- Belland, Brian R., Andrew E. Walker, Nam Ju Kim, and Mason Lefler. 2017. "Synthesizing Results From Empirical Research on Computer-Based Scaffolding in STEM Education: A Meta-Analysis." *Review of Educational Research* 87 (2): 309–344. `[ill-structured-problems]`
- Jonassen, David H. 1997. "Instructional Design Models for Well-Structured and Ill-Structured Problem-Solving Learning Outcomes." *Educational Technology Research and Development* 45 (1): 65–94. `[ill-structured-problems]`
- Jonassen, David H. 2000. "Toward a Design Theory of Problem Solving." *Educational Technology Research and Development* 48 (4): 63–85. `[ill-structured-problems]`
- Jonassen, David H. 2011. *Learning to Solve Complex Scientific Problems*. New York: Routledge. `[ill-structured-problems]` `[failure-mode]`
- Kalyuga, Slava, Paul Ayres, Paul Chandler, and John Sweller. 2003. "The Expertise Reversal Effect." *Educational Psychologist* 38 (1): 23–31. `[ill-structured-problems]` `[failure-mode]`
- Sinnott, Jan D. 1989. *Everyday Problem Solving: Theory and Applications*. New York: Plenum. `[ill-structured-problems]` `[foundational-theory]`
- Spiro, Rand J., Walter P. Vispoel, John G. Schmitz, Ala Samarapungavan, and A. E. Boerger. 1988. "Knowledge Acquisition for Application: Cognitive Flexibility and Transfer in Complex Content Domains." Center for the Study of Reading Technical Report 441. `[ill-structured-problems]`

### Project-based learning

- Chen, Chih-Hung, and Yu-Chu Yang. 2019. "Revisiting the Effects of Project-Based Learning on Students' Academic Achievement: A Meta-Analysis Investigating Moderators." *Educational Research Review* 26: 71–81. `[PBL]`
- Dochy, Filip, Mien Segers, Piet Van den Bossche, and David Gijbels. 2003. "Effects of Problem-Based Learning: A Meta-Analysis." *Learning and Instruction* 13 (5): 533–568. `[PBL]`
- Hmelo-Silver, Cindy E. 2004. "Problem-Based Learning: What and How Do Students Learn?" *Educational Psychology Review* 16 (3): 235–266. `[PBL]`
- Krajcik, Joseph S., and Phyllis C. Blumenfeld. 2006. "Project-Based Learning." In *The Cambridge Handbook of the Learning Sciences*, edited by R. Keith Sawyer, 317–333. Cambridge: Cambridge University Press. `[PBL]`
- Thomas, John W. 2000. *A Review of Research on Project-Based Learning*. San Rafael, CA: Autodesk Foundation. `[PBL]`

### Feedback

- Cho, Kwangsu, and Charles MacArthur. 2010. "Student Revision With Peer and Expert Reviewing." *Learning and Instruction* 20 (4): 328–338. `[feedback]`
- Cho, Kwangsu, and Charles MacArthur. 2011. "Learning by Reviewing." *Journal of Educational Psychology* 103 (1): 73–84. `[feedback]`
- Graham, Steve, Michael Hebert, and Karen R. Harris. 2015. "Formative Assessment and Writing: A Meta-Analysis." *Elementary School Journal* 115 (4): 523–547. `[feedback]`
- Hattie, John, and Helen Timperley. 2007. "The Power of Feedback." *Review of Educational Research* 77 (1): 81–112. `[feedback]`
- Sparrow, Betsy, Jenny Liu, and Daniel M. Wegner. 2011. "Google Effects on Memory: Cognitive Consequences of Having Information at Our Fingertips." *Science* 333 (6043): 776–778. `[feedback]` `[failure-mode]`
- Steiss, Jacob, et al. 2024. "Comparing the Quality of Human and ChatGPT Feedback of Students' Writing." *Learning and Instruction* 91 `[verify volume and authors]`. `[feedback]`
- Reeve, Johnmarshall, and Hyungshim Jang. 2006. "What Teachers Say and Do to Support Students' Autonomy During a Learning Activity." *Journal of Educational Psychology* 98 (1): 209–218. `[feedback]` `[foundational-theory]`

### Emergent-portfolio / writing-process

- Elbow, Peter. 1973. *Writing Without Teachers*. New York: Oxford University Press. `[emergent-portfolio]`
- Flower, Linda S., and John R. Hayes. 1981. "A Cognitive Process Theory of Writing." *College Composition and Communication* 32 (4): 365–387. `[emergent-portfolio]`
- Hillocks, George Jr. 1986. *Research on Written Composition: New Directions for Teaching*. Urbana, IL: National Conference on Research in English. `[emergent-portfolio]`
- Murray, Donald M. 1972. "Teach Writing as a Process Not Product." *The Leaflet* 71 (3): 11–14. `[emergent-portfolio]`
- Reber, Arthur S. 1989. "Implicit Learning and Tacit Knowledge." *Journal of Experimental Psychology: General* 118 (3): 219–235. `[emergent-portfolio]` `[foundational-theory]`

### Rubrics and assessment

- Anderson, Lorin W., and David R. Krathwohl, eds. 2001. *A Taxonomy for Learning, Teaching, and Assessing: A Revision of Bloom's Taxonomy of Educational Objectives*. New York: Longman. `[foundational-theory]`
- Association of American Colleges and Universities (AAC&U). 2009. *Critical Thinking VALUE Rubric*; *Creative Thinking VALUE Rubric*; *Inquiry and Analysis VALUE Rubric*. Available at [https://www.aacu.org/value-rubrics](https://www.aacu.org/value-rubrics). `[generative-learning]` `[ill-structured-problems]`
- Berliner, David C. 2001. "Learning About and Learning From Expert Teachers." *International Journal of Educational Research* 35 (5): 463–482. `[foundational-theory]`
- Reeves, Douglas B. 2000. "Validity Issues for Performance-Related Rubrics." *Education Policy Analysis Archives* 8 (31). `[feedback]`

### Clinical / medical

- Daly, Shanna R., Robin S. Adams, and George M. Bodner. 2012. "What Does It Mean to Design? A Qualitative Investigation of Design Professionals' Experiences." *Journal of Engineering Education* 101 (2): 187–219. `[clinical]` `[failure-mode]`
- Eva, Kevin W. 2005. "What Every Teacher Needs to Know About Clinical Reasoning." *Medical Education* 39 (1): 98–106. `[clinical]`
- Frank, Jason R., Linda S. Snell, Olle Ten Cate, Eric S. Holmboe, Carol Carraccio, Susan R. Swing, Peter Harris, Nicholas J. Glasgow, et al. 2010. "Competency-Based Medical Education: Theory to Practice." *Medical Teacher* 32 (8): 638–645. `[clinical]`
- Hafferty, Frederic W. 1998. "Beyond Curriculum Reform: Confronting Medicine's Hidden Curriculum." *Academic Medicine* 73 (4): 403–407. `[clinical]` `[emergent-portfolio]`
- Norman, Geoffrey. 2005. "Research in Clinical Reasoning: Past History and Current Trends." *Medical Education* 39 (4): 418–427. `[clinical]`
- ten Cate, Olle. 2005. "Entrustability of Professional Activities and Competency-Based Training." *Medical Education* 39 (12): 1176–1177. `[clinical]`
- Wong, Brian M., Edward E. Etchells, Andrea Kuper, Wendy Levinson, and Kaveh G. Shojania. 2010. "Teaching Quality Improvement and Patient Safety to Trainees: A Systematic Review." *Academic Medicine* 85 (9): 1425–1439. `[clinical]`

### AI tutoring / vendor-adjacent

- Bastani, Hamsa, et al. 2025. "GPT-Tutor: Generative AI for Personalized Education at Scale" `[verify exact title, authors, outlet]`. `[feedback]`
- Khan Academy. 2023–2026. "Khanmigo" product documentation. (Vendor source; cited for design stance, not evidence.) `[vendor]` `[feedback]`

---

## 10. Items flagged `[verify]` before publication

1. Bastani 2025 GPT-Tutor — exact title, authors, and outlet (preprint vs. published) should be confirmed before citation.
2. Steiss et al. 2024 — volume number and full author list need verification; *Learning and Instruction* 91 is likely but should be checked.
3. Cognitive-offloading specific claim "Brown, Lin et al. 2025 on AI writing assistance and student development" — I cannot confirm this paper exists as named. The broader cognitive-offloading literature (Sparrow et al. 2011) is solid; the specific 2025 paper needs verification.
4. AAMC's CBME specific publication — Frank et al. 2010 is the canonical CBME paper but AAMC has its own competency frameworks (Core EPAs for Entering Residency, 2014); these should be cited specifically if the chapter discusses AAMC CBME.
5. IHI Open School effect-size evidence — Wong et al. 2010 is the canonical review; specific Open School outcome studies would need separate verification.

---

*End of research note. Tag distribution: foundational-theory: 8; generative-learning: 5; elaborative-interrogation: 2; ill-structured-problems: 7; PBL: 5; feedback: 8; emergent-portfolio: 5; clinical: 7; failure-mode: 6. Unique primary citations: 48 (plus VALUE rubrics, IHI Open School, AAMC frameworks as organizational sources).*
