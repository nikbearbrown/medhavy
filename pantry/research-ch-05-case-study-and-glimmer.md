# Research: Chapter 05 — Case Study and Glimmer: The Two Modes Nobody Explains
## Medhavy: Is the Loop Worth It?

**Chapter one-line:** The reader learns what Case Study and Glimmer are, why they exist as separate modes, and what cognitive operation each one serves that Ask AI and Quiz Me cannot.
**Research date:** 2026-05-27

---

## 1. Primary Sources

### Foundational papers and texts

- **Cooke, Irby, O'Brien (2010). *Educating Physicians: A Call for Reform of Medical School and Residency.* Carnegie Foundation / Jossey-Bass.** Named directly in TIKTOC's Chapter 5 opening. The Carnegie report's central finding: medical schools train students for well-structured-problem performance (multiple-choice boards) but practice requires ill-structured-problem judgment. Four recommendations: standardize learning outcomes/individualize process; integrate formal and clinical knowledge; cultivate habits of inquiry and improvement; emphasize professional identity formation.
- **Sheppard, Macatangay, Colby, Sullivan (2008). *Educating Engineers: Designing for the Future of the Field.* Carnegie Foundation / Jossey-Bass.** Sister volume. Parallel finding for engineering: curricula privilege analytical problem-sets where the right answer exists; practice requires synthesis, design judgment, and accountability under uncertainty. The "professional formation" gap.
- **Jonassen, D. (1997). "Instructional Design Models for Well-Structured and Ill-Structured Problem-Solving Learning Outcomes." *Educational Technology Research and Development* 45(1): 65-94.** The foundational taxonomy. Well-structured problems have a single correct path and a single correct answer; ill-structured problems have multiple acceptable paths, competing constraints, and no clean stopping rule. The instructional design implications are different.
- **Spiro, Feltovich, Jacobson, Coulson (1988+). Cognitive Flexibility Theory.** The argument that ill-structured domains (medicine, history, literary interpretation) require multiple "crisscrossings" of the same conceptual terrain. Single-case examples produce brittle knowledge; multiple-case learning produces transferable knowledge.
- **Barrows, H., & Tamblyn, R. (1980). *Problem-Based Learning: An Approach to Medical Education.* Springer.** The founding text. McMaster's medical school as the live case. The pedagogical claim: students who acquire knowledge in the context of a problem retrieve it better when a similar problem arises in practice.
- **Williams, S. (1992). "Putting Case-Based Instruction Into Context: Examples From Legal and Medical Education." *Journal of the Learning Sciences* 2(4): 367-427.** Case-based learning's mechanism: the case is the retrieval cue. Without a case context, knowledge stays inert.
- **Koedinger, K. R., & Aleven, V. (2007). "Exploring the Assistance Dilemma in Experiments with Cognitive Tutors." *Educational Psychology Review* 19: 239-264.** Names the load-bearing concept for Case Study's graduated assistance ladder. Too much help produces offloading; too little produces shutdown. The optimal hint-density is non-obvious and context-dependent.
- **Sweller, J., & Cooper, G. (1985). "The Use of Worked Examples as a Substitute for Problem Solving in Learning Algebra." *Cognition and Instruction* 2(1): 59-89.** The worked-example effect — novices learn more from studying solutions than from solving novel problems. Important boundary condition for Case Study: deploy AFTER acquisition, not as acquisition.

### Key empirical cases

- **Hmelo-Silver, C. E. (2004). "Problem-Based Learning: What and How Do Students Learn?" *Educational Psychology Review* 16(3): 235-266.** Best meta-review of PBL outcomes. PBL underperforms direct instruction on immediate factual recall, outperforms it on delayed transfer and application. Aligns with the Bjork performance/learning distinction (relevant to Chapter 6 crossover).
- **Harvard Medical School "Pathways" curriculum (2015 onward).** Replaced the traditional two-year preclinical lecture sequence with case-based small-group learning. Publicly documented redesign.
- **USMLE Step 2 CK and Step 3 clinical vignettes.** The gold-standard "ill-structured problem in a four-paragraph case" format. Every US medical student encounters these. Useful reference frame for what a faculty-reviewed clinical case looks like.
- **Norman, G., & Schmidt, H. (1992). "The Psychological Basis of Problem-Based Learning: A Review of the Evidence." *Academic Medicine* 67(9): 557-565.** The mechanism: activation of prior knowledge by a case stem improves encoding of new material.

---

## 2. The Core Concept — State of the Field

### What is settled

The well-structured/ill-structured distinction is uncontested. The argument that professional practice in medicine, nursing, and pharmacy requires ill-structured judgment is uncontested. The worked-example effect is uncontested for novices. The assistance dilemma — that there is no universal correct hint density — is uncontested.

Generative open-ended assignments (essays, design projects, clinical write-ups) have been a mainstay of professional education for a century. The cognitive operation they target — synthesis under uncertainty — is a recognized educational outcome at Bloom's "Create" level.

### What is disputed

Whether PBL outperforms traditional curricula on long-term outcomes is genuinely contested. Some meta-analyses (Hmelo-Silver) find moderate gains on transfer; others (Colliver 2000) find no compelling evidence at the residency-performance level. The honest framing for a curriculum director: PBL costs more faculty time and produces students who score similarly on boards but report better preparation for clinical reasoning.

Whether AI can write acceptable clinical cases is *not* genuinely contested in the safety-critical literature — every major review (Topol, AAMC guidance documents through 2025) recommends faculty review of any AI-generated clinical scenario before student exposure. The "plausible-sounding wrong" failure mode in medicine has direct patient-safety implications.

Whether generative AI grading of generative assignments is valid is heavily contested (2024–2026 literature). Most current consensus: AI feedback on writing/reasoning is useful as a first pass but cannot replace expert judgment on professional-level work.

### What has changed recently (last 5 years)

- Mollick & Mollick (2023, 2024) on LLM use in higher education made case-based and project-based learning *more* important by making rote essays *less* reliable as evidence of learning.
- Faculty surveys (Chronicle of Higher Ed, 2024–2025) show majority concern that AI has compromised written assignments. This drives interest in oral exams, in-class case discussions, and project-based defense — i.e., toward the Glimmer model.
- The "process-feedback vs. task-feedback" distinction from Hattie & Timperley (2007) has gained new currency: when AI can produce the task output, the only remaining signal of learning is the student's reasoning process.

---

## 3. Application Domain Examples

1. **Pharmacology — beta-blockade decision (TIKTOC's running example).** Quiz Me makes the mechanism durable. Case Study presents a 64-year-old with COPD, heart failure with reduced ejection fraction, and recent bradycardia. The question is not "what does beta-blockade do?" — it is "should this patient receive a beta-blocker, which one, at what dose, and what would you monitor?" No clean answer; trade-offs are the point.
2. **Nursing — sepsis recognition.** Early sepsis presents ambiguously. Vital sign trends and qSOFA scores are useful but not deterministic. Case Study scenario: 78-year-old post-op patient with subtle changes in respiratory rate, mental status, and urine output. The well-structured version ("what is sepsis?") is Quiz Me material. The ill-structured version ("is this patient septic, and what do you do in the next ten minutes?") is Case Study material.
3. **Medical education — chest pain triage.** Differential diagnosis under time pressure. The 22-year-old with sharp pleuritic chest pain has a different prior than the 67-year-old with diaphoresis and crushing substernal pain. The reasoning, not the recall, is the learning objective.
4. **Pharmacy — polypharmacy in geriatric care.** A patient on 14 medications presents with a new symptom. Is it a side effect, an interaction, or a new condition? Glimmer scenario: design a deprescribing plan with explicit reasoning at each step. No single right answer; the defense of the reasoning is the work.
5. **Public health / health sciences — outbreak investigation.** Glimmer-appropriate: design the surveillance plan for a suspected foodborne outbreak in a long-term care facility. The student must specify what to measure, why, and what would change their conclusion. Cognitive operation is generative and accountable.

---

## 4. The Book's Thesis Connection

Chapter 5 is the chapter that closes the four-mode sequence — Ask AI for acquisition, Quiz Me for retention, Case Study for application under ambiguity, Glimmer for generative capability. The thesis connection is sharp because Case Study and Glimmer are the two modes that *cannot* be replaced by Canvas + Anki + an unguarded chatbot. Canvas can administer a case study assignment, but it cannot facilitate the case as a Socratic conversation; it cannot enforce the graduated-assistance ladder; it cannot detect whether the student is reasoning or pattern-matching from prior cases.

This is also the chapter that sharpens the "three conditions" test for the reader. A program where students never face ill-structured problems on the job does not need Case Study or Glimmer. A program where they do — every health sciences program — has a real question about whether the four-mode sequence delivers what direct case-based instruction with faculty does. The honest framing: Medhavy's Case Study and Glimmer modes operate at scale where individual faculty case-tutoring cannot. The trade-off is the AI's pattern-matching versus the human's clinical judgment as facilitator.

The chapter must also do work for Act Two: it sets up *why* measurement matters. A case discussion produces no Canvas-visible artifact other than the final write-up. The reasoning happens in the dialogue. Without measurement of the dialogue, the institution cannot tell whether the case discussion produced reasoning or just an AI-fluent final paragraph. This points forward to the seven signals (Ch 7) — specifically Y3 (cross-context transfer), Y7 (scaffolding response curve), and Y5 (social knowledge texture).

The Glimmer-specific thesis hook: the five proprietary dimensions (WHY, Usefulness, Mechanism, Defensibility, Specificity) are framed in TIKTOC as "designed to resist AI offloading." Each dimension targets a cognitive operation that current LLMs do poorly without explicit human reasoning: domain-specific problem framing, real-world utility judgment, mechanistic causal explanation, defense against counter-argument, and concrete commitment to specifics. The chapter should name this as the design intent.

---

## 5. The AI Wayback Machine — Candidate Figures

1. **Cindy Hmelo-Silver (preferred — woman, lesser-known outside ed-psych).** Indiana University and Rutgers. PBL research, computer-supported collaborative learning, scaffolding research. Less famous than Barrows but more rigorous on mechanism. Satisfies: woman, contemporary, less-known outside ed-psych. Example prompt: "You're Cindy Hmelo-Silver. A curriculum director asks: my faculty say PBL is too expensive and the boards still test factual recall. How do I justify case-based instruction to a skeptical dean?"
2. **Yrjö Engeström (non-Anglo — Finnish).** University of Helsinki. Activity theory, "expansive learning." The framework that ill-structured problems are learning opportunities precisely because they expose the contradictions in current practice. Less famous in the US than Vygotsky but central in European ed research. Satisfies: non-Anglo, lesser-known in US health sciences context. Example prompt: "You're Yrjö Engeström. Explain to a US curriculum director why a Case Study in nursing is not just 'realistic practice' but an expansion of what students can do."
3. **Patricia Alexander (woman, less-known).** University of Maryland. Model of Domain Learning — how novices acquire knowledge in a specific domain through three stages (acclimation, competence, proficiency). Directly relevant to when Glimmer is appropriate (proficiency stage) vs. when it produces anxiety (acclimation stage). Example prompt: "You're Patricia Alexander. A curriculum director wants to assign generative open-ended projects in week 3 of a pharmacology course. What do you tell her?"

**Diversity assessment:** Two women, one non-Western figure (Engeström, Finnish). All three are accessible to a non-research reader if their work is translated. Hmelo-Silver is the strongest candidate for this chapter — her name will be unfamiliar to most curriculum directors but her work most directly addresses their question.

---

## 6. Pedagogical Delivery Research

Chapter 5 is positioned at the end of Act One, where the reader has just learned about Ask AI (Ch 3) and Quiz Me (Ch 4). The pedagogical challenge: the reader is now primed to think of "modes" as cognitive tools, but Case Study and Glimmer are categorically different — they are assignments, not interactions.

Two pedagogical moves are load-bearing:

- **The cognitive-sequence frame.** Ask AI → Quiz Me → Case Study → Glimmer maps to acquire → retain → apply → generate. This sequence echoes Bloom's revised taxonomy but is more granular. Use the running beta-blockade example to walk the student through all four stages, as the TIKTOC worked example does. The sequence is the chapter's spine.
- **The "two-mode chapter" structure.** Two distinct modes in one chapter is structurally risky. The reader can confuse them. Mitigation: clear visual/structural separation. First half is Case Study (application under ambiguity). Second half is Glimmer (generative production). The bridge between halves is the cognitive-sequence frame above.

The chapter should resist the temptation to defend PBL/case-based learning against its critics. The reader is a curriculum director in health sciences — they already use cases. The chapter's job is to explain what Case Study (the Medhavy mode) does *as a system* that an instructor-led case discussion does not: scale, consistency of facilitation, measurement of the dialogue, and the prerequisite gate (Quiz Me threshold met before Case Study unlocks).

For Glimmer specifically: the reader has likely never used a "generative open-ended assignment with AI pre-grading." The chapter must make this concrete with one extended example, not a list of features. The TIKTOC worked example (the student progressing through all four modes on beta-blockade) is the right vehicle.

---

## 7. Representation and Display Research

Per TIKTOC anatomy, every chapter needs a worked example. Chapter 5's worked example is sequential, not tabular — the same student moving through Ask AI → Quiz Me → Case Study → Glimmer on the beta-blockade concept. This is a narrative table, not a comparison table.

**Recommended Section 7 table — the four-mode capability comparison:**

| Mode | Cognitive operation | Right when student... | Wrong when student... | Canvas can do this? |
|---|---|---|---|---|
| Ask AI | Acquire | Has no schema for the concept yet | Has the schema and is patronized by hints | No (chatbot bolt-on does the wrong version) |
| Quiz Me | Retain | Has the schema and needs durability | Needs to learn application under ambiguity | Partially (Canvas quizzes lack FSRS scheduling) |
| Case Study | Apply | Can retrieve but can't deploy under uncertainty | Lacks underlying mechanism (will guess) | No (can administer the assignment, cannot facilitate) |
| Glimmer | Generate | Can apply and needs to create and defend | Lacks proficiency in domain (will produce anxiety) | No (Canvas grades the artifact, cannot grade the reasoning) |

**Recommended supplementary representation — the five Glimmer dimensions:** A short five-row mini-table naming WHY / Usefulness / Mechanism / Defensibility / Specificity in plain language, with one example of what each dimension looks like in a pharmacology Glimmer assignment. Flag heavily as proprietary.

The faculty-review process for Case Study scenarios warrants a process diagram or simple list: scenario draft → faculty content review → faculty Socratic-laddering review → student pilot → revision. The reader needs to see what they're committing to in faculty time (Ch 10 makes this concrete; Ch 5 should preview it).

---

## 8. Open Questions and Research Gaps

- **The five Glimmer dimensions are proprietary to Humanitarians AI / Medhavy.** WHY, Usefulness, Mechanism, Defensibility, Specificity are not in any external rubric literature in this exact form. They resemble Toulmin argumentation (claim, ground, warrant, backing, qualifier, rebuttal) and Hattie's process-feedback dimensions but are not equivalent. The chapter should present the five dimensions clearly while flagging that the specific framework is Medhavy's. Adjacent legit literature: Toulmin (1958) *The Uses of Argument*; Kuhn (1991) *The Skills of Argument*; Hattie & Timperley (2007) "The Power of Feedback."
- **"Faculty-reviewed" as a gate is a process claim, not an empirical claim.** No published RCT compares AI-generated clinical cases (faculty-reviewed vs. not) on student learning outcomes. The patient-safety argument is normative and prudent — and the AAMC, ABIM, and joint medical-education AI guidance documents all support faculty review — but the strict empirical evidence is thin. The book should frame this as a safety-engineering principle, not as a finding.
- **The "emergent term project" feature** (students don't know they're building a portfolio until week 10) is a design choice with no direct empirical support. The closest literature is hidden-purpose research on intrinsic motivation (Deci & Ryan, self-determination theory) but the specific design is Medhavy's invention. The book can present it as a hypothesis with theoretical support rather than as evidence-based.
- **The backwards-faded scaffolding solution** that TIKTOC mentions for Glimmer phase gates does have a real research base — Renkl & Atkinson (2003) on faded worked examples — but adapting that paradigm from algebra to clinical reasoning is itself a research-grade extrapolation. Worth naming.
- **Highest-priority gap:** A single end-to-end case showing one health sciences student completing all four modes on one concept with measured learning outcomes. This does not exist in the public literature; it would need to be an internal Medhavy deployment study. The chapter should be honest that the four-mode sequence is theoretically motivated but not yet empirically validated as a sequence (the individual components are evidence-based; the integration is the bet).

---

## 9. Sourcing Notes

The Carnegie Foundation reports (Cooke 2010; Sheppard 2008) are the highest-quality anchor sources and are named in TIKTOC. They are accessible to a non-research reader through their executive summaries — the chapter should cite them by their plain-language conclusions, not by methodology. Both have been continuously cited in medical-education reform literature for 15+ years; aging risk is low.

Jonassen (1997) and Spiro (1988) are the canonical theoretical anchors for the well-structured/ill-structured distinction. Jonassen is more accessible; lead with him.

The Hmelo-Silver review (2004) is the right citation for PBL outcomes — recent enough to matter, old enough to be settled. The Colliver (2000) critique is the right counter-citation if the book wants to acknowledge the dispute honestly.

For the assistance dilemma: cite Koedinger & Aleven (2007) directly. The phrase "assistance dilemma" is theirs and is precise.

For worked-example research: Sweller & Cooper (1985) is the founding paper. Renkl is the contemporary anchor (Renkl 2014 review).

Cross-chapter overlap: Bjork's performance/learning distinction (Ch 6's anchor) is implicitly relevant here through Hmelo-Silver's finding that PBL underperforms on immediate recall and outperforms on delayed transfer. Cross-reference but do not duplicate.

The proprietary Medhavy concepts (Glimmer's five dimensions, the four-mode sequence, the phase gate, the emergent term project) should be presented with the Humanitarians AI / Medhavy attribution clearly marked. Outside-of-Medhavy primary sources do not exist for these in their specific form; adjacent legitimate literature exists for each component and should be cited for that mechanism, not for the integration.
