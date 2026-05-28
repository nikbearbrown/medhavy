# Research: Chapter 01 — The Failure That Looks Like Success
## Medhavy: Is the Loop Worth It?

**Chapter one-line:** The reader learns why AI in education can look like it's working while actively harming learning — and why that failure is architectural, not incidental.
**Research date:** 2026-05-27

---

## 1. Primary Sources

### Foundational papers and texts

- **Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., & Mariman, R. (2025).** "Generative AI without guardrails can harm learning: Evidence from high school mathematics." *Proceedings of the National Academy of Sciences*, 122(26), e2422633122. DOI: 10.1073/pnas.2422633122. *Citation confirmed.* The single load-bearing study for this chapter — nearly 1,000 Turkish high school students across roughly 50 9th–11th grade math classes, four 90-minute sessions, randomized to GPT Base (unguarded), GPT Tutor (prompts engineered as guardrails), or no-AI control. Both AI groups outperformed control during practice; on the unassisted final exam, GPT Base scored *below* control by a wide margin while GPT Tutor matched control. A correction (PNAS 10.1073/pnas.2518204122) was issued; the core finding holds.

- **Kosmyna, N., et al. (2025).** "Your Brain on ChatGPT: Accumulation of Cognitive Debt when Using an AI Assistant for Essay Writing Task." *arXiv preprint* 2506.08872 (MIT Media Lab). EEG study of 54 Boston-area university students writing essays under three conditions (brain-only, search-engine, LLM). LLM users showed the weakest neural connectivity; participants who began with ChatGPT struggled to recover independence when later restricted to brain-only. Useful as a second, mechanism-level data point — but it is a 54-person preprint, not peer-reviewed, and should be presented as such.

- **Bjork, R. A., & Bjork, E. L. (1992).** "A new theory of disuse and an old theory of stimulus fluctuation." In Healy, Kosslyn, & Shiffrin (Eds.), *From learning processes to cognitive processes*. The original technical statement of the performance-learning distinction. The disposable distinction the reader needs: *current performance* (what you can do right now, with the AI in front of you) and *learning* (what you can do later, without it). Bastani is the operational demonstration of what the Bjorks named.

- **Bender, E. M., Gebru, T., McMillan-Major, A., & Shmitchell, S. (2021).** "On the Dangers of Stochastic Parrots: Can Language Models Be Too Big?" *FAccT '21.* Source for the "fluency trap" — the observation that an LLM's surface-level coherence is not a reliable signal of comprehension on either side of the conversation. Useful here because it pre-dates the deployment hype: an early statement of *why* AI-generated text reads as understanding without producing it.

- **Caulfield, M., & Wineburg, S. (2023).** *Verified: How to Think Straight, Get Duped Less, and Make Better Decisions about What to Believe Online.* University of Chicago Press. The SIFT framework (Stop, Investigate the source, Find better coverage, Trace claims) — relevant here as the antidote to fluency-as-credibility, and a precedent for "the wrapper around the information matters more than the information."

### Key empirical cases

- **Bastani GPT Base vs GPT Tutor (2025) — the worked example for this chapter.** Same model (GPT-4), same students, same content, two different system prompts. The 17-percentage-point gap on the post-test is the entire architectural argument compressed into one chart.

- **Heffernan et al. ASSISTments randomized trials (Roschelle et al. 2016, IES report; later replications).** Counter-case: a tutoring tool with proper feedback architecture (immediate, scaffolded, with teacher report-back) produced a roughly three-quarters-of-a-year math gain in Maine middle schools. The wrapper made the difference — same content, different architecture, opposite outcome from Bastani's GPT Base. Labeled documented, not illustrative.

- **Kosmyna 2025 EEG protocol** — illustrative of the mechanism (offloading produces measurable reductions in neural engagement) but small N and preprint status mean it is not a load-bearing citation. Flag as preliminary.

---

## 2. The Core Concept — State of the Field

### What is settled

- The **testing effect** (retrieval improves durable learning) and **spacing effect** (distributed practice beats massed) are among the most replicated findings in cognitive psychology. Roediger & Karpicke (2006), Dunlosky et al. (2013) — these are not in dispute.
- **Performance ≠ learning.** Bjork & Bjork's distinction is uncontroversial in the field; current performance is an unreliable predictor of retention at delay. This is the conceptual bedrock under the Bastani finding.
- **Engagement metrics (time on page, clicks, completion) do not predict learning outcomes** when measured rigorously. Multiple meta-analyses on LMS analytics; the engagement-completion gap is settled, though it is a habit of *interpretation* in institutional practice that has not caught up to the literature.

### What is disputed

- **Whether the Bastani finding generalizes** beyond Turkish high school mathematics, beyond GPT-4-class models, beyond four-session interventions, beyond the specific guardrails tested. It is a single RCT. Replication is in progress (multiple groups, none yet published in peer-reviewed venues as of May 2026).
- **Whether "cognitive offloading" is a stable construct** or an umbrella term covering several distinct effects (Kosmyna preprint vs. critique by arXiv:2601.00856). Treat as live debate.
- **Whether prompt-level guardrails are sufficient** or whether system-level constraints (RAG grounding, refusal policies, retrieval architecture) are required. Bastani tested the prompt-level case and found it sufficient *in that study*. Open question.

### What has changed recently (last 5 years)

- Generative AI in education moved from novelty to default between 2022 and 2025. Pre-Bastani, the dominant narrative was "AI tutors help." Bastani is the first large-scale RCT to flip that narrative for unguarded deployments.
- LMS vendors began marketing "AI assistants" (Canvas Cody, Khanmigo, etc.) without published outcome data. The institutional decision-maker now faces an evidence asymmetry — marketing volume far exceeds outcome evidence.
- The Kosmyna preprint (June 2025) catalyzed press coverage that has reached curriculum directors. Many will have heard "ChatGPT makes you dumber" before they encounter this chapter. The chapter has to be careful not to confirm the cartoon version.

---

## 3. Application Domain Examples

1. **Pharmacology drug-mechanism questions.** A nursing student asks GPT-4 "what's the difference between a beta-1 selective and non-selective beta blocker?" An unguarded chatbot delivers a fluent, complete, accurate paragraph. The student feels they understand. Two weeks later, on a paper exam without the AI, they cannot reconstruct the answer because they never built the schema — they consumed the AI's schema. This is the Bastani failure mode in a clinical context.

2. **Clinical reasoning case prep.** A medical resident uses an unguarded AI to work through cases before rounds. Performance during simulated cases is high. On the unannounced bedside oral exam, performance collapses — the resident learned to elicit answers from the model, not to reason through patients. (Illustrative; the parallel literature is the Heffernan-side finding inverted.)

3. **Dosage calculations in a med-math course.** A pharmacy student uses ChatGPT to check calculations. Mid-term scores rise. Final, without AI access, scores drop. The instructor sees the same shape Bastani saw — practice up, performance down. Domain-specific demonstration of the engagement-learning gap.

4. **NCLEX prep.** Students using unguarded AI question explanations score higher on practice questions, lower on the licensure exam itself. (Illustrative — direct NCLEX evidence is anecdotal; Bastani-shaped result expected and worth flagging as a hypothesis institutional decision-makers might want to investigate.)

5. **Anatomy identification.** A student uses an AI image companion to identify structures on cadaver photographs. In-app accuracy: 92%. Lab practical without AI: 64%. The 28-point gap is what an engagement dashboard cannot see.

---

## 4. The Book's Thesis Connection

This chapter is the pebble — the single concrete failure that the rest of the book justifies a response to. The thesis hinges here: Medhavy earns its cost when three conditions hold, and the *first* condition (present differently at scale) is meaningless if the institution cannot distinguish *engagement* from *learning*.

The Bastani finding installs that distinction by force. Once the reader sees that *the same AI*, in *the same students*, produced *opposite learning outcomes* depending only on the architectural commitments around it, they cannot un-see that "the AI is working" is not the question. The question is: *which AI architecture is working, for whom, on which signal*?

That is the loop. Present differently (Bastani: with or without guardrails) → measure whether it helped (Bastani: with a delayed, unassisted post-test, not in-session metrics) → adapt (Bastani's authors recommend the guarded variant; Medhavy generalizes this into a continuous, per-student, per-concept process).

For the curriculum director with a vendor proposal in hand: this chapter is what makes her ask the vendor "what does your platform commit the AI to *not* doing, and how would I know if it failed at that commitment?" That is the right question. The book exists to teach her to ask it.

---

## 5. The AI Wayback Machine — Candidate Figures

**Figure 1: Hubert Dreyfus (1929–2017).** Wikipedia page title: "Hubert Dreyfus." Phenomenologist, UC Berkeley philosopher. His 1972 *What Computers Can't Do* (revised 1992 as *What Computers Still Can't Do*) argued that disembodied symbol manipulation could not capture skilled human coping — that fluency in a symbol system is not the same as understanding the world the symbols are about. The Bastani finding is a quantitative footnote to Dreyfus's qualitative argument. Lesser-known to a curriculum director than Turing or Minsky. Undergraduate-accessible.
**Example prompt:** "I'm a curriculum director evaluating an AI tutor. Hubert Dreyfus argued in 1972 that AI could produce fluent symbol manipulation without understanding. Explain that argument to me in two paragraphs, then tell me how it shows up in the Bastani 2025 finding."

**Figure 2: Yrjö Engeström (b. 1948).** Wikipedia page title: "Yrjö Engeström." Finnish educational theorist; Cultural-Historical Activity Theory (CHAT); developed the concept of *expansive learning* and "the activity system" as the unit of analysis. His core insight: learning is shaped by the tool-mediated activity system, not by the individual learner alone. A different AI wrapper is a different activity system, which is a different learning event — that is Bastani's finding restated in Engeström's vocabulary. Non-Anglo (Finnish), lesser-known in US contexts. Diversity note: still male; flagged.
**Example prompt:** "Explain Yrjö Engeström's activity theory to me as if I were deciding whether to buy an AI textbook. What does the framework predict will happen when you change the 'tool' in a learning activity system without changing anything else?"

**Figure 3: Sherry Turkle (b. 1948).** Wikipedia page title: "Sherry Turkle." MIT sociologist; *Reclaiming Conversation* (2015), *Alone Together* (2011). Documented the difference between *interaction with* a system and *learning from* it — that fluent conversational interfaces produce a feeling of connection or competence that does not track with what is actually being acquired. Female, broadly accessible, less famous than Turing/Hawking.
**Example prompt:** "Sherry Turkle has written about how conversational technology produces feelings of connection that don't track underlying reality. Apply that to a student using ChatGPT for homework — what would Turkle say is happening, and how does it map onto the Bastani 2025 finding?"

**Diversity assessment for this chapter:** Two men, one woman. Engeström is non-Anglo. Will rebalance across the four-chapter set.

---

## 6. Pedagogical Delivery Research

**Prior knowledge required:** Familiarity with the phrase "engagement metrics," basic awareness that AI tools exist, and an intuition that exam scores measure something. No research literacy assumed.

**Common misconceptions in institutional decision-makers:**
1. *"If students use the tool and like it, they're learning."* This is the engagement-learning conflation. The Bastani finding is the most direct rebuttal available.
2. *"AI is bad for education."* The chapter must not confirm this. The point is architectural, not categorical — *guarded* AI matched control in Bastani; *unguarded* AI underperformed.
3. *"The vendor's dashboard reflects learning."* It reflects platform usage. Different category.
4. *"A higher score during the unit means a higher score at the end."* This is the performance-learning conflation. Bjork's distinction predicts the Bastani result.

**What teaching of this concept fails at:** Most explanations frame the engagement-learning gap as a measurement problem (we just need better dashboards). It is not. It is a *causal* problem — engagement is sometimes downstream of learning, sometimes downstream of offloading, and the dashboard cannot tell which. The chapter has to resist the dashboard-improvement framing.

**What makes the difference between understanding and memorization:** The reader should be able to predict what would happen in a deployment she has never seen, given the architecture. If she can say "this vendor's design has no guardrail on answer-giving, so Bastani predicts harm" — she has the concept. If she can only repeat "engagement isn't learning" — she has a slogan.

---

## 7. Representation and Display Research

**Opening case:** The Bastani study as narrated in plain language. No statistics in the first paragraph. The visual is the gap between two dashboards (identical) and two exam-score distributions (very different).

**Worked example:** Same. Recommend a **two-panel comparison figure**:
- Left panel: in-session metrics (time on task, problems attempted, satisfaction rating, completion rate) — bars roughly identical between GPT Base and GPT Tutor.
- Right panel: unassisted post-test scores — GPT Base distribution shifted left of control; GPT Tutor distribution overlapping control.

**Source material for the figure:** Bastani et al. 2025 PNAS Figure 2 and Figure 3 contain the underlying data. Reproduce as a redrawn comparison with permission citation; the journal is open access (PNAS open access since 2022). The visual must not require statistical literacy to read.

**Table (optional):** A "what the dashboard saw vs. what the exam showed" two-column table running down the page, with one row per metric. Reinforces the engagement-learning distinction visually.

---

## 8. Open Questions and Research Gaps

- **Replication of Bastani.** As of May 2026, the published RCT count of "unguarded vs guarded AI tutor" interventions remains one. Flag explicitly in the chapter and in the contributor notes. The book's claim is "this is the strongest evidence currently available, and it needs replication," not "this is settled."
- **Cross-cultural and cross-subject generalization.** Bastani is Turkish high school math. We do not know whether the effect size holds in US health sciences, in adult learners, in conceptual rather than procedural domains.
- **"Stochastic Parrots" framing.** Useful but politically charged in some institutional contexts. Recommend using the *fluency trap* phrasing rather than citing the paper title in the chapter itself.
- **Kosmyna preprint.** Not peer-reviewed; small N. Use sparingly and flagged.
- **Heffernan ASSISTments parallel.** Used here as a positive-architecture contrast, but Heffernan is not strictly a generative-AI study — flag in any text that compares directly.
- **Aging:** Bastani will be replicated, contested, or extended within 12–24 months. Chapter must be written so a replication-failure or a replication-success would both leave the architectural argument intact. The architecture-matters claim is older than Bastani (Dreyfus, Engeström, Bjork) and would survive the loss of any single study.

---

## 9. Sourcing Notes

- **Bastani 2025 PNAS:** Open access. DOI 10.1073/pnas.2422633122. Also available at SSRN 4895486 and as preprint on the author's site (hamsabastani.github.io/education_llm.pdf). The PNAS correction is at 10.1073/pnas.2518204122 — the chapter should reference both or note "as corrected" if quoting figures.
- **Kosmyna 2025:** arXiv 2506.08872. Preprint only. Note non-peer-reviewed status.
- **Bjork & Bjork 1992:** Book chapter, hard to locate online; cite via APA secondary references (Soderstrom & Bjork 2015, *Perspectives on Psychological Science* — open access — restates the distinction with the same authorship).
- **Bender et al. 2021:** Open access in ACM Digital Library proceedings of FAccT.
- **Dreyfus 1972/1992:** MIT Press. PDF of 1972 edition available on monoskop.org; the 1992 edition is in print.
- **Engeström 1987:** *Learning by Expanding*, Cambridge University Press 2nd edition (2014) is the citable form; full text at lchc.ucsd.edu/mca/Paper/Engestrom/Learning-by-Expanding.pdf.
- **Heffernan / ASSISTments:** Roschelle, J., Feng, M., Murphy, R. F., & Mason, C. A. (2016). "Online Mathematics Homework Increases Student Achievement." *AERA Open*, 2(4). Open access. The press version at wpi.edu/news/study-shows-wpi-developed-math-homework-tool-closes-learning-gap is usable for the lay-reader story.
- **Fact-checking priority:** the "17 percentage points" number in the TIKTOC opening. Verify against the corrected PNAS figure tables before final draft. Current reading of the published abstract supports the qualitative claim of a substantial deficit; the precise number may shift in the corrected version.
