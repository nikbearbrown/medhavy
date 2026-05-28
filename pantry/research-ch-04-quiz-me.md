# Research: Chapter 04 — Quiz Me: Making Knowledge Stick
## Medhavy: Is the Loop Worth It?

**Chapter one-line:** The reader learns what spaced retrieval practice is, why it works, and when Quiz Me adds something that Anki or Canvas quizzes do not.
**Research date:** 2026-05-27

---

## 1. Primary Sources

### Foundational papers and texts

- **Roediger, H. L., & Karpicke, J. D. (2006).** "Test-Enhanced Learning: Taking Memory Tests Improves Long-Term Retention." *Psychological Science*, 17(3), 249–255. The single most cited demonstration of the testing effect. Compares re-reading vs. testing on delayed retention; testing wins, especially at longer delays. The chapter's central empirical anchor. This is *settled* science — the chapter can lean on it without hedging.

- **Karpicke, J. D., & Blunt, J. R. (2011).** "Retrieval Practice Produces More Learning than Elaborative Studying with Concept Mapping." *Science*, 331(6018), 772–775. Stronger result: retrieval beat even *elaborative* study techniques (concept maps) that students *believed* were more productive. Crucial for the chapter because curriculum directors often advocate for concept maps and study guides; the chapter has to honor that without endorsing it as the strongest available technique.

- **Cepeda, N. J., Pashler, H., Vul, E., Wixted, J. T., & Rohrer, D. (2006).** "Distributed practice in verbal recall tasks: A review and quantitative synthesis." *Psychological Bulletin*, 132(3), 354–380. Meta-analysis of the spacing effect. Distributed practice beats massed practice across 184 studies. With Roediger & Karpicke, defines the two pillars Quiz Me is built on: retrieval + spacing.

- **Dunlosky, J., Rawson, K. A., Marsh, E. J., Nathan, M. J., & Willingham, D. T. (2013).** "Improving Students' Learning With Effective Learning Techniques: Promising Directions From Cognitive and Educational Psychology." *Psychological Science in the Public Interest*, 14(1), 4–58. The Dunlosky review ranks 10 study techniques by evidence; **practice testing and distributed practice are the only two rated "high utility."** This is the *summary* citation a curriculum director needs — one paper, two top-rated techniques, both built into Quiz Me.

- **Bjork, R. A. (1994).** "Memory and metamemory considerations in the training of human beings." In Metcalfe & Shimamura (Eds.), *Metacognition: Knowing About Knowing*. The "desirable difficulties" framing — that interventions which slow practice performance often improve retention. Explains why Quiz Me feels harder than re-reading and produces better outcomes. Also explains why students will dislike Quiz Me initially and the chapter must pre-arm the reader for this.

- **Ye, J., et al. (Open Spaced Repetition project, 2022–present).** FSRS (Free Spaced Repetition Scheduler). The current state-of-the-art scheduling algorithm; adopted as Anki's default in version 23.10 (November 2023). Models memory with three parameters: difficulty, stability, retrievability. Claims roughly 20–30% fewer reviews than SM-2 at equivalent retention. Citation should reference the GitHub project at github.com/open-spaced-repetition/fsrs4anki and the Anki documentation rather than a peer-reviewed paper — the algorithm is open-source community work, not academic publication.

- **Woźniak, P. (1990).** SM-2 algorithm, SuperMemo. The historical ancestor: the original spaced-repetition algorithm, developed for the SuperMemo software, dominated flashcard scheduling for 30 years until FSRS displaced it. The chapter should mention SM-2 by name because many curriculum directors will have heard of Anki without knowing what algorithm runs under it.

- **FAA Aviation Instructor's Handbook (FAA-H-8083-9, current revision).** Government publication. Safety-critical concept review requirements — pilots review certain procedures *regardless* of recent demonstrated competency. This is the institutional precedent for Quiz Me's safety-critical override (high-stakes concepts reviewed even when retrieval is strong). Particularly useful for health-sciences readers because the parallel — drug dosing, sterile technique, code procedures — is immediate.

### Key empirical cases

- **Roediger & Karpicke 2006 testing-effect experiments.** Documented. The original prose-passage / immediate-vs-delayed-test paradigm.

- **Dunlosky 2013 high-utility ranking.** Documented. Practice testing + distributed practice top the list.

- **Karpicke 2011 vs concept-mapping.** Documented. Important counterexample to popular study advice.

- **Bahrick 1984 "Fifty Years of Spanish."** Bahrick, H. P. (1984). "Semantic memory content in permastore: Fifty years of memory for Spanish learned in school." *Journal of Experimental Psychology: General*, 113(1), 1–29. 733 participants, 50-year retention curves, demonstrated the existence of *permastore* — long-term retention that resists decay. Cited as the long-arc evidence that practice-tested material can last decades; Quiz Me's value proposition compounds over time.

- **Pharmacology board-exam two-student example (TIKTOC).** Illustrative composite drawn from realistic study patterns. Label as illustrative.

---

## 2. The Core Concept — State of the Field

### What is settled

- **The testing effect is real and large.** Retrieval practice produces more durable retention than equivalent time spent re-reading. Replicated across hundreds of studies, multiple domains, multiple age groups. Among the most settled findings in cognitive psychology.
- **The spacing effect is real and large.** Distributed practice beats massed practice. Cepeda et al. (2006); replicated thousands of times.
- **Practice testing + spacing are the two highest-utility study techniques.** Dunlosky et al. (2013). Not in dispute.
- **Performance during practice does not predict retention.** Students who struggle more during practice retain more at delay. This is the *desirable difficulties* principle (Bjork) and is the cognitive-science backing for why Quiz Me should feel harder than re-reading.

### What is disputed

- **The optimal spacing interval.** Cepeda's "spacing ratio" findings give a range; FSRS personalizes per card; SM-2 uses fixed intervals. The exact algorithm matters less than the principle (space it out).
- **Whether FSRS outperforms SM-2 on *learning outcomes* (vs. *scheduling efficiency*).** FSRS is demonstrably more efficient at maintaining target retention with fewer reviews. Whether the freed time produces meaningfully better *outcomes* (vs. just less student work for the same outcome) is not a peer-reviewed claim. Treat as a scheduling-efficiency claim, not a learning-outcome claim. (This matters — the TIKTOC contested-claims table flags this.)
- **Transfer.** Whether retrieval practice on factual material produces flexible application is open. Probably yes for near transfer; less clear for far transfer. This is exactly why Quiz Me is *not* the only mode — Case Study and Glimmer pick up where retrieval practice taps out.
- **The "habit gap."** Why does student adoption of spaced-repetition tools stall around 20% in most deployments? Not well understood. Some interaction-design literature; not a settled question.

### What has changed recently (last 5 years)

- FSRS replaced SM-2 as the default algorithm in Anki in 2023. Most current literature on Anki effectiveness pre-dates the switch.
- AI-generated flashcards (ChatGPT, Quizlet AI) flooded the market 2023–2025. The category line between "Quiz Me" and "AI-generated flashcards" is something the chapter has to draw cleanly: the algorithm + curriculum integration + safety-critical override are what differentiate Quiz Me, not the flashcard format itself.
- Aviation pedagogy has continued to insist on safety-critical concept review regardless of recall score — this institutional pattern is *not* widespread in higher ed, and is one of Quiz Me's most distinctive design choices.

---

## 3. Application Domain Examples

1. **Drug name + mechanism + side effects (pharmacology).** Classic Quiz Me terrain. Hundreds of drugs to remember; spaced retrieval is the only practice that produces durable recall at NCLEX or board-exam scale. Two students prepping for a pharmacology board: re-reading vs. Quiz Me, divergent outcomes (the TIKTOC worked example).

2. **NCLEX-RN test-prep.** Massive recall load; documented benefit of spaced practice. Quiz Me's prerequisite-interleaving (mixing cards from related concepts) forces discrimination learning — distinguishing between similar-presenting drugs or syndromes.

3. **Anatomy structure identification.** Nursing and pre-med anatomy require thousands of structures. Spaced retrieval is the only sustainable strategy; Quiz Me's image-card support plus FSRS scheduling is well-matched to the load.

4. **Clinical decision rules (e.g., Wells criteria, CHA₂DS₂-VASc).** Discrete, high-stakes, frequently needed. Quiz Me's *safety-critical override* (aviation principle) keeps these in rotation even after the algorithm would otherwise stop scheduling them.

5. **Where Quiz Me is NOT the right mode:** clinical reasoning about a complex case (Case Study territory); designing a novel patient education protocol (Glimmer territory); teaching a student who has never encountered the underlying concept (Ask AI territory). Quiz Me is *retention*, not *acquisition*, *application*, or *generation*.

---

## 4. The Book's Thesis Connection

Quiz Me is the most "obvious" of the four modes — many curriculum directors will have used Anki or assigned it to students. The chapter's job is therefore not to *justify* Quiz Me but to *distinguish* it from what the reader already knows.

What Quiz Me adds beyond Anki (per the TIKTOC):
1. **Integration with the concept node map** — cards are not orphans; they are pinned to curriculum concepts the bandit also operates on.
2. **Priority weighting for high-importance concepts** — institutional safety-critical knowledge gets weighted upward.
3. **The aviation pedagogy principle** — safety-critical concepts reviewed regardless of recall score.
4. **Prerequisite interleaving** — forces discrimination between related concepts.

These four together are the answer to "why pay for Quiz Me when Anki is free?" The curriculum director needs to be able to articulate them.

Connection to the loop:
- **Present differently**: Quiz Me is the *retention* intervention. The bandit decides when to schedule it.
- **Measure whether it helped**: Y6 (Retrieval Strength Decay) is the seven-signal diagnostic. Knowledge that holds at delay produced retention; performance that collapses at delay produced *current performance* without learning.
- **Adapt**: cards that show decay get more frequent scheduling; cards that hold get spaced out. FSRS does this at the card level; the bandit does this at the *mode* level.

The three conditions for Quiz Me specifically:
- *Different learners at scale?* Quiz Me's per-student FSRS schedule is exactly this — but a class of 30 with one instructor can use shared Anki decks without much loss.
- *Need to know whether variation helped?* If institutional outcomes (NCLEX pass, board pass) are externally measured, the variation answer is already coming. If not, Medhavy provides the diagnostic.
- *Willing to act?* If the answer is "we will require Quiz Me usage in graded work," yes. If "we'll make it optional and hope," no — Quiz Me without institutional commitment will collapse on the habit-gap problem.

---

## 5. The AI Wayback Machine — Candidate Figures

**Figure 1: Henry "Harry" Bahrick (1924–2020).** Wikipedia page title: "Harry P. Bahrick." Ohio Wesleyan psychologist. Documented *permastore* — the empirical existence of a memory state that resists decay for decades. His 50-year Spanish-vocabulary cohort (1984) is one of the longest-running retention studies in psychology. Far less famous than Ebbinghaus. Male, Anglo — flag, but his work is exactly the long-arc evidence the chapter needs.
**Example prompt:** "Harry Bahrick studied Spanish vocabulary retention 50 years after high school in 733 former students. Summarize his findings about 'permastore' and tell me what they imply for the long-term value of a daily Quiz Me habit during a 15-week pharmacology course."

**Figure 2: Piotr Woźniak (b. 1962).** Wikipedia page title: "Piotr Woźniak (researcher)." Polish researcher; built SuperMemo and the SM-2 algorithm in the late 1980s. Non-Anglo. Pre-dates the academic spaced-repetition literature in important ways — Woźniak was a *user* studying his own retention before the cognitive psychology mainstream caught up. Lesser-known than Ebbinghaus; far lesser-known to curriculum directors than Ebbinghaus.
**Example prompt:** "Piotr Woźniak built SuperMemo and the SM-2 algorithm in the 1980s, before spaced repetition was mainstream in cognitive psychology. Explain what he discovered by self-experimentation, and how the modern FSRS algorithm extends his work."

**Figure 3: Elizabeth Ligon Bjork (b. 1944).** Wikipedia page title: "Elizabeth Bjork" (or "Elizabeth Ligon Bjork"). UCLA psychologist; co-developer of the New Theory of Disuse with Robert Bjork. Female; co-author rather than singular figure on most major papers, so often overlooked despite shared authorship of the core conceptual framework underlying Quiz Me. The chapter can use her to introduce *desirable difficulties* — and to make clear that the "Bjork" most readers vaguely remember is sometimes Robert, sometimes Elizabeth, often both.
**Example prompt:** "Elizabeth Bjork co-developed the concept of 'desirable difficulties' — interventions that slow current performance but improve durable retention. Explain the concept and tell me what it predicts about a student's experience using Quiz Me for the first three weeks of a course."

**Diversity assessment for this chapter:** One non-Anglo (Woźniak), one woman (Elizabeth Bjork), one Anglo male (Bahrick). Across the four-chapter set (Ch 1–4): Dreyfus, Engeström, Turkle, Woolf, Licklider, Alexander, Resnick, Matsuzawa, Mazur, Bahrick, Woźniak, Elizabeth Bjork. **Final tally: 5 women, 2 non-Anglo, 5 Anglo men. Meets the per-task requirement of at least one woman and one non-Anglo. Diversity is acceptable but Anglo-male-heavy; the back half of the book should look for more non-Anglo figures.**

---

## 6. Pedagogical Delivery Research

**Prior knowledge required:** Some awareness that Anki exists or that spaced repetition is a phrase. No knowledge of the underlying cognitive psychology assumed.

**Common misconceptions in institutional decision-makers:**
1. *"Quiz Me is just Anki with the Medhavy logo."* The chapter has to install the four-thing differentiator (concept-map integration, priority weighting, aviation override, prerequisite interleaving).
2. *"If students like a study technique, it's working."* Bjork's finding: students systematically prefer re-reading and dislike practice testing, and practice testing produces better retention. Quiz Me will feel harder; the chapter must warn the reader.
3. *"Retrieval practice = quiz-taking = assessment."* No. Quiz Me is *practice*, not assessment. Confusion between these is a category error that often makes faculty think Quiz Me will replace exams. It will not.
4. *"FSRS is just a better SM-2."* True but boring. The chapter should treat the algorithm switch as a footnote and focus on the curriculum-integration features that actually differentiate Quiz Me from a free flashcard app.

**What teaching of this concept fails at:** Most explanations of the testing effect deliver the evidence and stop. The reader closes the chapter agreeing that testing helps and not knowing whether *Quiz Me, specifically*, is worth the line-item. The chapter has to keep returning to the four differentiators, the institutional commitment requirement, and the three conditions.

**What makes the difference between understanding and memorization:** The reader who can describe what Quiz Me looks like in her own curriculum on a particular concept — and who can name the concepts in her curriculum that are *not* good Quiz Me targets — has the concept.

---

## 7. Representation and Display Research

**Opening case:** The testing-effect finding stated as plainly as the TIKTOC opens it — "There is a finding in cognitive psychology so well-replicated that it functions as a law." Then immediately to the counterintuitive consequence: students who study by testing perform worse immediately and better at every subsequent measurement.

**Worked example:** The two-pharmacology-students board-exam scenario. Recommend a **forgetting-curve comparison plot**:
- X-axis: days from initial learning.
- Y-axis: retention.
- Curve A: re-reading group — high at day 1, declines steeply.
- Curve B: spaced-retrieval group — lower at day 1, much higher at day 30, day 60, day 90.
- Vertical line marking "exam day" on day 60 or 90.

This is the canonical figure. Source data shape from Roediger & Karpicke 2006 + Cepeda et al. 2006 + Bahrick 1984 (for the very-long-tail). The figure must be honest — not exaggerated; the testing-effect effect size is meaningful but not gigantic in the first weeks.

**Display required:**
- The forgetting-curve comparison (load-bearing).
- A small **Quiz Me vs. Anki feature comparison table** so the four differentiators are explicit and visible.

| Feature | Anki (free) | Quiz Me |
|---|---|---|
| FSRS algorithm | Yes (since 2023) | Yes |
| Cards from student/community | Yes | Faculty-curated, concept-mapped |
| Concept-map integration | No | Yes |
| Priority weighting (safety-critical) | No | Yes |
| Aviation override | No | Yes |
| Prerequisite interleaving | Manual | Algorithmic |
| Instructor dashboard | No | Yes |

---

## 8. Open Questions and Research Gaps

- **The four Quiz Me differentiators (concept-map integration, priority weighting, aviation override, prerequisite interleaving)** are described in the Medhavy primary manuscript but not separately validated by published RCTs. Frame as design choices grounded in supporting literature (concept-map theory; FAA pedagogy; interleaved practice research) rather than as separately-tested effects.
- **Habit formation evidence.** Why some institutions achieve 80%+ Quiz Me adoption and others 20% is not well characterized. Likely a function of curriculum design (graded vs. optional) and instructor messaging; not a Medhavy software question. Flag.
- **FSRS as a learning-outcome improvement vs. an efficiency improvement.** Per TIKTOC contested-claims table, presented as efficiency. Be careful not to overclaim.
- **Quiz Me and AI-generated cards.** As of 2026, students can ask any LLM to generate cards from a textbook chapter. Whether Quiz Me's faculty-curated cards meaningfully outperform student-generated cards at scale is an open empirical question.
- **Transfer beyond recall.** Most testing-effect research is on near transfer. The chapter should be careful not to claim Quiz Me builds clinical reasoning — it builds the recall foundation on which clinical reasoning depends.
- **Aging risk:** FSRS will be superseded. Pin the chapter's argument on the *commitment to algorithmic per-card scheduling*, not on FSRS specifically.

---

## 9. Sourcing Notes

- **Roediger & Karpicke 2006:** *Psychological Science*. Often paywalled; author copies on Karpicke's Purdue site.
- **Karpicke & Blunt 2011:** *Science*. AAAS. Paywalled; widely summarized in higher-ed press.
- **Cepeda et al. 2006:** *Psychological Bulletin*. APA. Author copies on Pashler's UCSD site.
- **Dunlosky et al. 2013:** *Psychological Science in the Public Interest*. **Open access** — this is the single most useful citation for a non-research-reader because PSPI articles are written for policymakers. The chapter should foreground this paper.
- **Bjork 1994:** Book chapter. Hard to obtain online. Cite via Soderstrom & Bjork (2015) which restates the framework with citation.
- **Bahrick 1984:** *JEP: General*. APA. Hard to access; the 1984 paper is the definitive citation but the SuperMemo wiki has summaries.
- **Ye / FSRS:** No peer-reviewed citation. Cite the GitHub project (github.com/open-spaced-repetition/fsrs4anki) and Anki documentation. Stable URLs; the chapter should flag that the FSRS literature is community-engineering rather than academic.
- **Woźniak SM-2:** Original SuperMemo documentation. Citable via supermemo.com or supermemo.guru.
- **FAA Aviation Instructor's Handbook (FAA-H-8083-9):** Government document. Free PDF at faa.gov. Use the most current revision.
- **Fact-checking priority:** the four Quiz Me differentiators against the Medhavy primary manuscript — confirm that "aviation override" and "prerequisite interleaving" are the correct names and that the chapter's description matches the implementation.
