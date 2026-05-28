# Research: Chapter 03 — Ask AI: When the Student Needs to Think, Not Receive
## Medhavy: Is the Loop Worth It?

**Chapter one-line:** The reader learns what Ask AI is, why it is deliberately constrained, and when that constraint is the point.
**Research date:** 2026-05-27

---

## 1. Primary Sources

### Foundational papers and texts

- **Lewis, P., Perez, E., Piktus, A., et al. (2020).** "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks." *NeurIPS 2020.* arXiv:2005.11401. The foundational RAG paper. Combines a parametric language model (BART) with a non-parametric retrieval index (Dense Passage Retrieval over Wikipedia). Produces output that is *grounded* in retrieved passages rather than generated from model parameters alone. Relevant here because Ask AI is architecturally a RAG system — the retrieval corpus is the textbook itself, so Ask AI cannot hallucinate "off-textbook" content if the architecture is enforced.

- **Slamecka, N. J., & Graf, P. (1978).** "The generation effect: Delineation of a phenomenon." *Journal of Experimental Psychology: Human Learning and Memory*, 4(6), 592–604. The original demonstration that words *generated* by the learner are remembered better than words *received*. The single most relevant cognitive-psychology finding for Ask AI's design — answering Socratically forces generation; answering directly does not.

- **Koedinger, K. R., & Aleven, V. (2007).** "Exploring the Assistance Dilemma in Experiments with Cognitive Tutors." *Educational Psychology Review*, 19(3), 239–264. The canonical statement of the assistance dilemma: *too much help* produces offloading; *too little help* produces shutdown. Ask AI's hints-not-answers design is a direct response to this dilemma — calibrated assistance is the design goal, not absence of assistance.

- **Sweller, J. (1988).** "Cognitive load during problem solving: Effects on learning." *Cognitive Science*, 12(2), 257–285. Founding cognitive-load-theory paper. Relevant because the unguarded chatbot collapses the *germane* load (the productive struggle that builds schemas) while leaving the *intrinsic* load unchanged — student feels the same surface effort, learns less.

- **Paul, R., & Elder, L. (2006).** *The Thinker's Guide to Socratic Questioning.* Foundation for Critical Thinking Press. The most accessible plain-language treatment of Socratic technique for educators. Six question categories — clarification, probing assumptions, probing reasons, viewpoint, implication, the question itself. Ask AI's prompt design is a software implementation of this taxonomy.

- **Mazur, E. (1997).** *Peer Instruction: A User's Manual.* Prentice Hall. The peer-instruction model (ConcepTest, vote, discuss, re-vote) is the canonical example of structured *not-telling* producing better learning than direct instruction. Worth citing as evidence that withholding the answer is not a Medhavy invention — it is a 30-year-old pedagogical move with replicated outcomes.

- **Bastani et al. (2025) PNAS** — re-applied here. The unguarded GPT condition in Bastani is precisely the failure mode Ask AI's design prevents. The guarded GPT condition in Bastani is a closer cousin of Ask AI than the unguarded condition. The chapter's argument: Bastani's GPT Tutor is Ask AI in primitive form; Ask AI is Bastani's GPT Tutor productionized with RAG grounding to a specific textbook.

### Key empirical cases

- **Bastani 2025 GPT Tutor vs GPT Base** (already cited Ch 1). The on-the-record comparison of guarded vs. unguarded AI conversation. Documented.

- **ASSISTments hint sequences (Heffernan et al.).** Documented. The graduated-hint model — first hint a Socratic prompt, last hint near-but-not-quite-the-answer — is well-studied in ASSISTments randomized trials. Closest existing empirical precedent for Ask AI's hint ladder.

- **Peer Instruction in introductory physics (Crouch & Mazur 2001, *Am. J. Phys.*).** Documented. Multi-year data from Harvard introductory physics; pre-post conceptual gains substantially higher in Peer Instruction sections than traditional lecture. The structural move (don't tell — make them generate) generalizes.

---

## 2. The Core Concept — State of the Field

### What is settled

- **Generation outperforms reception for retention.** Slamecka & Graf (1978) and 40+ years of replications. Not in dispute.
- **Socratic questioning, applied competently, produces better critical-thinking outcomes than direct instruction in domains where reasoning is the target.** Multiple meta-analyses; the effect is moderate but robust.
- **The assistance dilemma is real.** Too much help and too little help both impair learning. The shape of the curve (inverted U) is settled; where the optimum sits varies with student, domain, task.

### What is disputed

- **Whether AI can deliver Socratic instruction competently at scale.** Open. Bastani's GPT Tutor condition is encouraging; the question of whether prompt-engineered guardrails are sufficient or whether system-level constraints are required is unresolved.
- **The optimal hint ladder.** ASSISTments has empirical results for math; the equivalent ladder for pharmacology, clinical reasoning, or anatomy is not as well characterized.
- **Whether students adapt around guardrails.** Some evidence that students who recognize a Socratic tutor pattern will switch tools to an unguarded chatbot. Mitigation strategies (institutional commitment, integration into graded work) are not well studied.

### What has changed recently (last 5 years)

- RAG became a default architectural pattern in 2023–2024. By 2025, "grounded to a corpus" is the assumed minimum for educational AI; ungrounded chatbots are increasingly seen as inadequate even outside the AI-in-education literature.
- The Bastani finding (2025) put a number on the cost of *not* having guardrails. Before Bastani, the assistance dilemma was a theoretical concern; after Bastani, it is an outcome-evidence concern.
- The "Socratic tutor" framing has been re-popularized by Khanmigo (Khan Academy, 2023) and similar products. The reader may have encountered the term as a marketing label without understanding the cognitive-science underpinnings.

---

## 3. Application Domain Examples

1. **A nursing student asks: "What is beta blockade?"** Ask AI's response: "What did you observe about heart rate when sympathetic activity dropped in the prerequisite section? What would happen if we blocked the receptors that drive that effect?" The student has to retrieve the prerequisite and reason forward — generation effect engaged.

2. **A pharmacy student asks: "Why is this patient hypotensive on her ACE inhibitor?"** Ask AI declines to diagnose the patient. It returns: "Walk me through the mechanism of ACE inhibition step by step — what does that mechanism predict about blood pressure? Where on that chain might this patient be especially sensitive?"

3. **A medical student asks: "Can you just explain the citric acid cycle to me?"** This is the Ask AI patronizing-failure-case. Asking the student to generate when she genuinely lacks the schema produces frustration, not learning. The Ask AI response in this case should *offer* a brief explanation and then *immediately* convert into Socratic mode for the next step. Worth showing as the "Ask AI is not always right" case.

4. **A nursing student stuck on a clinical-reasoning case** (e.g., differential for chest pain in an older patient). Ask AI is the wrong mode — Case Study is the right mode. The chapter must show this so the reader understands the four modes form a sequence, not a menu.

5. **A pharmacology TA prep session.** TA uses Ask AI as a personal reasoning partner: "How would you explain the difference between competitive and non-competitive inhibition to a confused student?" — Ask AI prompts the TA to articulate her own thinking, which is exactly how a Socratic tool should function with an advanced user.

---

## 4. The Book's Thesis Connection

Ask AI is the *first* mode in the four-mode sequence and the most architecturally distinctive — because it is the mode most easily confused with a chatbot. The chapter's job is to install the architectural distinction:

- **Chatbot** = ungrounded, answer-giving, optimized for fluent response.
- **Ask AI** = grounded (RAG over the textbook), hints-not-answers, optimized for retrieval and articulation by the student.

If the reader cannot tell these apart by the end of the chapter, the rest of the book does not work — because she will keep conflating Medhavy with "a chatbot bolted onto a PDF" (TIKTOC misconception #1).

The connection to the loop: Ask AI is the *intervention* at the acquisition stage — "presenting differently" means presenting via Socratic question rather than via explanation. Whether this *helps* a particular student on a particular concept is the question Medhavy's measurement layer answers in Chapter 7. The bandit's decision in Chapter 8 is whether to deploy Ask AI again for this student on this concept, or move to Quiz Me, or escalate to Case Study.

For the three-condition test: Ask AI's value is highest where the *first* condition is most active — where different learners need to encounter the same concept from different entry points. A class of 30 with one instructor can run informal Ask AI manually. A program of 300 across five sections cannot.

---

## 5. The AI Wayback Machine — Candidate Figures

**Figure 1: Lauren Resnick (1936–2021).** Wikipedia page title: "Lauren Resnick." Pittsburgh-based educational psychologist; founder of the Learning Research and Development Center. Pioneered *situated cognition* and the institutional treatment of learning as embedded in practice rather than in heads. Her work on classroom discourse (the "accountable talk" framework) is a structured version of what Ask AI tries to do conversationally. Female, lesser-known to non-specialists than Vygotsky or Bruner.
**Example prompt:** "Lauren Resnick developed the 'accountable talk' framework — students articulate, justify, and respond to evidence in classroom discussion. Apply that framework to a one-on-one AI tutor designed to ask questions, not answer them. What does Resnick's framework predict about which question-types produce learning?"

**Figure 2: Tetsuro Matsuzawa (b. 1950).** Wikipedia page title: "Tetsuro Matsuzawa." Japanese primatologist, Kyoto University. Documented "Education by Master-Apprenticeship" in chimpanzee nut-cracking — adults do not teach; juveniles observe and try, fail, and try again, with the master available but not intervening. The structural parallel to Ask AI's hints-not-answers design is striking, and the cross-cultural / cross-species framing helps a reader see *not-telling* as a deep pedagogical pattern, not a software trick. Non-Anglo. Male.
**Example prompt:** "Tetsuro Matsuzawa documented 'Education by Master-Apprenticeship' in chimpanzee tool use — the master is present but does not intervene; the apprentice learns by failure and observation. Explain the pattern, then tell me how Ask AI's hints-not-answers design implements the same teaching strategy in software."

**Figure 3: Eric Mazur (b. 1954).** Wikipedia page title: "Eric Mazur." Harvard physicist; developed Peer Instruction. Famous within physics-education circles, less famous outside. Useful Wayback because Peer Instruction is a deeply-replicated example of "structured not-telling beats telling." Male, Anglo — flag.
**Example prompt:** "Eric Mazur's Peer Instruction reverses the lecture: instructor poses a ConcepTest, students vote, discuss with neighbors, vote again. Explain why this works, then tell me how Ask AI implements the same structural move — students generate before they receive — in one-on-one software."

**Diversity assessment for this chapter:** One woman (Resnick), one non-Anglo (Matsuzawa), one Anglo male (Mazur). Across Ch 1–3 the running tally is: 4 women OR non-Anglo, 4 Anglo men. Acceptable; Chapter 4 should keep this trajectory.

---

## 6. Pedagogical Delivery Research

**Prior knowledge required:** Reader needs to know what RAG is at a one-sentence level (the chapter provides this). She needs the *intuition* that "asking" and "answering" are different cognitive operations.

**Common misconceptions in institutional decision-makers:**
1. *"Ask AI is a chatbot."* TIKTOC misconception #1. The chapter's primary lift.
2. *"Hints are softer answers."* No — hints redirect to material the student already has access to. They do not partially answer.
3. *"Socratic = harder."* Socratic done badly is patronizing or paralyzing. Done well, it is calibrated to where the student is, which is why the assistance dilemma matters.
4. *"If students hate it, it's wrong."* Some students will hate Ask AI initially because they came in expecting an answer-giving chatbot. The chapter should pre-arm the reader for this; student satisfaction in early weeks is not the metric.

**What teaching of this concept fails at:** The chapter has to resist the urge to *prove* Ask AI works by listing the generation effect, the assistance dilemma, the Bastani finding. The reader does not need a literature review. She needs to be able to *tell the difference between Ask AI and a chatbot* and to *predict when Ask AI would help her students.*

**What makes the difference between understanding and memorization:** The reader who can describe what Ask AI would do *given a specific student question in her own curriculum* — and who can name when Ask AI would be the wrong tool — has the concept.

---

## 7. Representation and Display Research

**Opening case:** Brief; the natural assumption ("an AI tool in a textbook answers questions") followed by the reframe ("Ask AI does not answer questions. This is not a limitation. It is the design.").

**Worked example:** The "What is beta blockade?" two-response comparison from the TIKTOC. Recommend a **two-column side-by-side comparison block**:

| Unguarded chatbot response | Ask AI response |
|---|---|
| "Beta blockade refers to the pharmacologic antagonism of beta-adrenergic receptors. Beta-1 receptors, predominantly in cardiac tissue, mediate increased heart rate and contractility..." (continues for 400 words) | "What did you observe about heart rate when sympathetic activity dropped in the prerequisite chapter? What do you think would happen if we blocked the receptors that drive that effect?" |
| What the student does: reads, nods, moves on. | What the student does: retrieves, articulates, sometimes wrong, learns. |
| Dashboard metric: high time-on-page. | Dashboard metric: low time-on-page; high friction signal (Chapter 7). |

**Display required:** This two-column response comparison is load-bearing. Also recommend a small **mode-fit matrix** showing where Ask AI is appropriate (acquisition, articulation under uncertainty) and where it is not (recall of well-understood material, application under clinical ambiguity, generative work).

---

## 8. Open Questions and Research Gaps

- **Ask AI as a Humanitarians AI proprietary term.** Outside-of-Medhavy primary sources for "Ask AI" specifically will not exist. The chapter must cite the Medhavy manuscript as the primary source for the term and place the architecture (RAG + Socratic prompts + hints-not-answers guardrail) in the broader literature lineage.
- **Frictional Framework / GLP** — proprietary; Section 4 references the framework but the full detail is in Chapter 7.
- **Empirical evidence specific to Ask AI deployments at scale.** Limited. Chapter should present the design argument as well-grounded in *components* (RAG, Socratic, assistance dilemma) without overclaiming on aggregate outcome evidence.
- **Whether students develop "Ask AI literacy"** over a semester (learn to engage productively with Socratic questioning, rather than going around it). Open.
- **Cross-domain transfer.** Most evidence for Socratic-style tutoring is in math and physics. Health-sciences-specific evidence is thinner. Worth flagging.
- **Aging risk:** RAG architectures will change. Pin the chapter's argument on the *commitment* (grounded retrieval, hints not answers) rather than the *implementation* (Lewis-style RAG, BART, DPR). The commitment is stable; the implementation is not.

---

## 9. Sourcing Notes

- **Lewis et al. 2020:** arXiv 2005.11401; NeurIPS 2020 proceedings. Open access.
- **Slamecka & Graf 1978:** APA journal. Paywalled, but the finding is reported in every cognitive psychology textbook; secondary citation via Roediger & Karpicke (2006) or Dunlosky et al. (2013) is acceptable.
- **Koedinger & Aleven 2007:** *Educational Psychology Review*, Springer. ERIC accession EJ785065. Some institutional access required; author copies on ResearchGate.
- **Sweller 1988:** Open via Cognitive Science journal archives. Foundational.
- **Paul & Elder 2006:** Trade book, Foundation for Critical Thinking. Cite via the most recent edition the reader can buy.
- **Mazur 1997 + Crouch & Mazur 2001:** *American Journal of Physics* article is open via AAPT archive. Mazur's book is in print.
- **Bastani et al. 2025 PNAS:** Open access (same citation as Ch 1).
- **Resnick "accountable talk":** Resnick, L. B. (1999) and follow-ups. Open via University of Pittsburgh's Institute for Learning publications.
- **Matsuzawa:** Primary sources include *Cognitive Development in Chimpanzees* (Matsuzawa, Tomonaga, & Tanaka, eds., 2006, Springer) and CV at matsuzawa.kyoto. The "Education by Master-Apprenticeship" framing is widely attributed to him; specific citation may require consulting his summary chapter in the Springer volume.
- **Fact-checking priority:** the framing "Ask AI is RAG-grounded." Confirm against the Medhavy primary manuscript that RAG is the architectural pattern in use, not a related variant.
