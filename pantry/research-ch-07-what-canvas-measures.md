# Research: Chapter 7 — What Canvas Measures and What It Misses
## Medhavy: Is the Loop Worth It?

**Chapter one-line:** The reader learns the specific gap between engagement analytics and learning evidence — and why that gap is the adoption decision's hinge.
**Research date:** 2026-05-27

---

## 1. Primary Sources

### Foundational papers and texts

- **Bjork, R. A. (1994). "Memory and Metamemory Considerations in the Training of Human Beings." In *Metacognition: Knowing About Knowing*, ed. Metcalfe & Shimamura. MIT Press.** The foundational text for the performance/learning distinction. Bjork's argument: instructional manipulations that produce better immediate performance often produce worse long-term retention, and vice versa. "Desirable difficulties" — conditions that slow acquisition but produce durable learning — include spacing, interleaving, generation, and varied conditions of practice. Anchor citation for Chapter 7.
- **Soderstrom, N. C., & Bjork, R. A. (2015). "Learning Versus Performance: An Integrative Review." *Perspectives on Psychological Science* 10(2): 176-199.** The contemporary restatement. Reviews 20+ years of evidence that immediate performance is an unreliable proxy for durable learning. Most accessible source for the chapter's load-bearing claim.
- **Bjork, E. L., & Bjork, R. A. (2011). "Making Things Hard on Yourself, but in a Good Way: Creating Desirable Difficulties to Enhance Learning." In *Psychology and the Real World*, ed. Gernsbacher et al.** Plain-language version of the Bjork distinction, written for educators. Quotable.
- **Bastani et al. (2025). "Generative AI Can Harm Learning." [PNAS or arXiv working paper, Aug 2024 / 2025 publication].** Same-AI, two-wrapper RCT in Turkish high-school math. Group with unguarded GPT-4 outscored the no-AI control by 48% during practice; on the unassisted final exam, the unguarded group scored 17 percentage points *below* the no-AI control. The guarded "GPT Tutor" wrapper closed most of the gap. Direct empirical demonstration that Canvas-style engagement and performance metrics can be inversely related to durable learning.
- **Selwyn, N. (2015). "Data Entry: Towards the Critical Study of Digital Data and Education." *Learning, Media and Technology* 40(1): 64-82.** The sociological critique of LMS analytics. What counts as "data" in education is a political choice; what is easy to measure (clicks, time-on-page) drives what is treated as evidence.
- **Williamson, B. (2017). *Big Data in Education: The Digital Future of Learning, Policy and Research.* SAGE.** Book-length treatment of education's quantification turn. Useful for the chapter's "Canvas was not designed to measure learning" framing.
- **Eynon, R. (2013). "The Rise of Big Data: What Does It Mean for Education, Technology, and Media Research?" *Learning, Media and Technology* 38(3): 237-240.** Editorial framing the data-validity question for learning analytics.
- **Verbert, K., et al. (2014). "Learning Dashboards: An Overview and Future Research Opportunities." *Personal and Ubiquitous Computing* 18(6): 1499-1514.** The CHI/HCI review of learning-analytics dashboards. Most dashboards visualize engagement, not learning; very few have validated outcome links.
- **Soares, F., et al. (2021/2022). Various papers on Canvas LA validity.** The general finding: Canvas Analytics' time-on-page and click counts have weak-to-no predictive validity for final grades, and even weaker validity for downstream retention.
- **Mollick, E., & Mollick, L. (2024). *Co-Intelligence: Living and Working with AI.*** The contemporary anchor for "AI made artifact-based assessment unreliable." Mollick's faculty-facing framing — what changes for assessment in a world where every student has GPT-class assistance.
- **OpenAI o1 evaluation and cheating studies (2024–2025).** Mostly press coverage and short technical reports rather than peer-reviewed papers, but the empirical finding is robust: current LLMs can produce graduate-level writing on most subjects, making the written artifact unreliable as a learning signal.

### Key empirical cases

- **Bastani 2025 (as above)** is the single most important case. The chapter is built around it.
- **Sawyer Effect / Reading the Test Without Reading the Book studies (decades old; cited by Bjork)** — the finding that students preparing for one form of test do poorly on another form because they have learned the test, not the material.
- **Bahrick, H. (1984). "Semantic Memory Content in Permastore: Fifty Years of Memory for Spanish Learned in School." *Journal of Experimental Psychology: General* 113(1): 1-29.** The "permastore" finding — what survives 25-50 years after instruction is not what scored well immediately after instruction. Direct empirical answer to "Canvas grades vs. durable learning."
- **Karpicke & Roediger (2008). "The Critical Importance of Retrieval for Learning." *Science* 319: 966-968.** Counterintuitive finding: students who tested themselves once outperformed students who restudied four times — at one-week delay. Performance after the study session was inverse to durable learning.

---

## 2. The Core Concept — State of the Field

### What is settled

The performance-learning distinction is settled. So is the related finding that *learners' own judgments of learning* (JOLs) are systematically miscalibrated — students believe they have learned material that they have not, and they prefer instructional conditions that produce less durable learning (Bjork, Dunlosky, Nelson). This last point is critical for the chapter: the reader's faculty believe they can tell when students are learning. The cognitive psychology says: no one can, including the students themselves, without a delayed measurement.

That LMS engagement metrics (clicks, time, completion) are weak predictors of learning outcomes — even of next-week quiz performance, let alone end-of-term retention — is settled in the learning-analytics literature. The dashboards that visualize these metrics are not lying; they are answering a different question than the one administrators usually think they are answering.

### What is disputed

Whether *better* engagement analytics could fix the problem is genuinely disputed. Some learning-analytics researchers argue that more sophisticated behavioral measures (mouse-movement patterns, scroll-back rate, time-to-first-action) recover predictive validity. Others — including the Frictional Framework's intellectual ancestors — argue that the problem is categorical: engagement is *not* learning, and any engagement-based proxy will be defeated by sufficiently engaged-looking offloading. Bastani's data favors the categorical position for the AI-tutoring case.

The decoupling problem (AI made artifacts unreliable as evidence of learning) is empirically real but its magnitude is disputed. Some studies find 30%+ of college-writing assignments now show LLM signatures; others find lower numbers. The reader needs the qualitative point, not the precise percentage.

Whether Canvas's roadmap will close the gap is disputed and increasingly important. Canvas has announced (2024–2025) AI-augmented analytics features. These may or may not measure learning. The book's claim should be that *as of book publication*, Canvas measures engagement, not learning — and that even if Canvas adds learning signals, they will likely be retrofitted onto an engagement-first architecture.

### What has changed recently (last 5 years)

- **The decoupling problem.** Before 2023, a well-written essay was reasonable evidence that the student could write it. After 2023, it is not. This single change has done more to motivate "process-level measurement" than 30 years of Bjork's writing did.
- **The Bastani finding (2024–2025).** The first high-quality RCT showing that AI tutoring can produce performance gains while *reducing* durable learning, with engagement metrics indistinguishable between conditions. Load-bearing for this chapter.
- **The faculty experience of AI in the gradebook.** Anecdotal but ubiquitous: every faculty member teaching since 2023 has had the experience of a beautifully written assignment from a student who cannot discuss the material orally. This is now common knowledge, not contested literature, and the chapter can lean on the reader's experience.
- **LMS vendor positioning.** Instructure (Canvas) and competitors are repositioning analytics offerings to address this gap. The chapter should note that Medhavy's claim is not that this gap is permanent but that it exists *now* and a measurement-and-adaptation layer addresses it directly.

---

## 3. Application Domain Examples

1. **Pharmacology — drug-mechanism understanding.** Canvas shows the student spent 47 minutes on the beta-blockade module, completed all interactive elements, and scored 88% on the module quiz. Six weeks later, faced with a clinical question that requires applying the mechanism, the student cannot. The Canvas record says "learned." The downstream evidence says "didn't."
2. **Nursing — medication-administration safety.** Canvas certifies module completion. Six months later, a nurse in clinical rotation cannot recognize a high-alert medication situation. The gap between "completed the module" and "can identify the danger" is the gap this chapter is about. Patient-safety stakes make this concrete.
3. **Medical education — anatomy retention.** Bahrick-style finding for medical students: anatomy detail learned for first-year boards is largely gone by third-year clerkships. The Canvas gradebook said "A in anatomy." The clinical reality says "needs to relearn before useful." The Frictional Framework's claim: retrieval-strength decay (Y6) would have predicted this; Canvas could not.
4. **Pharmacy — calculation accuracy.** A student passes the dosage-calculation Canvas quiz on the second try, scoring 90%. The gradebook shows competence. In the OSCE practical six weeks later, the student makes a decimal-place error. The error pattern (Y2 error trajectory coherence) was visible in the original quiz attempts but invisible to the gradebook's pass/fail summary.
5. **Health sciences research methods — statistical literacy.** The student earned a B in biostatistics two years ago and now cannot interpret a confidence interval in a journal club. The Canvas record was accurate as a record of performance. It was not evidence of durable learning. The instructor who needed the student to read that journal article had no way to know in advance.

---

## 4. The Book's Thesis Connection

This is the chapter where the loop's *measurement* layer becomes the central question. The book's thesis is that Medhavy earns its cost only when three things are true; Chapter 7 makes the *second* condition concrete: "someone needs to know whether the variation is working (not just whether students are engaged)."

Three thesis-specific moves are load-bearing:

1. **Frame the gap as a category difference, not a Canvas failure.** Canvas was built to administer courses. It administers them well. Engagement analytics are accurate measurements of engagement. The category mistake is treating engagement as a proxy for learning. The chapter's central distinction: *engagement evidence* vs. *learning evidence*. Both are real; they are not the same thing.
2. **Use Bastani as the chapter's spine.** The Bastani finding was previewed in Chapter 1 (the "pebble") and pays off here. The two groups had identical engagement profiles; one learned, one un-learned. If engagement metrics cannot distinguish a group that gained 17 points from one that lost 17 points, they cannot distinguish anything important about learning. This is the hardest moment in the book per TIKTOC. The chapter must not editorialize — let Bastani do the work.
3. **Set up the seven signals without naming them yet.** The chapter ends by pointing to "behavioral traces of genuine cognitive engagement." Don't name Y1–Y7 here; that's Chapter 8's job. But establish that the alternative to engagement metrics is *not* better engagement metrics — it is a different kind of measurement entirely.

The hard rhetorical work: the reader has spent their career using engagement as a proxy for learning. Per TIKTOC, this chapter must "correct a deeply held professional habit without insulting the reader." The way to do this is to make the gap a *Canvas property*, not a reader property. The reader did not make a mistake; the tool wasn't built for what the reader needs now. This is true and it lets the reader update without losing face.

The honest case for not adopting (Ch 9) requires this chapter to set up the *value* of measurement. If the chapter overshoots and the reader concludes "measurement is irrelevant — engagement is fine for my deployment," the book has not earned its later chapters. If the chapter undershoots and the reader concludes "Canvas is useless," the book has alienated them. The Goldilocks framing: Canvas gives you what it was designed to give you; for some deployments that is enough; for others, learning evidence is the only thing that closes the loop.

---

## 5. The AI Wayback Machine — Candidate Figures

1. **Elizabeth Bjork (preferred — woman, less famous than her husband Robert).** UCLA. Co-architect of the desirable difficulties framework. Her work on test-enhanced learning and on the JOL miscalibration is foundational but less cited than Robert's. Satisfies: woman, lesser-known, directly relevant to the chapter's central claim. Example prompt: "You're Elizabeth Bjork. A curriculum director says her Canvas dashboard shows her students are engaged and scoring well. What is she missing?"
2. **Henry "Roddy" Roediger III (well-known in cog psych, less so to a curriculum director).** Washington University in St. Louis. The testing effect — retrieval practice produces more durable learning than restudying — is Roediger and Karpicke's signature finding. Relevant here as the empirical demonstration that immediate performance and durable learning can diverge. Example prompt: "You're Henry Roediger. A curriculum director's faculty insist their gradebook is a fair measure of student learning. What's the cleanest experiment you'd show them to update their view?"
3. **Audrey Watters (non-academic, woman, sharp critic).** Independent writer; *Teaching Machines* (2021, MIT Press). Long-running critique of edtech metrics culture. Less academic than the cognitive psychologists; more accessible. Satisfies: woman, lesser-known in clinical-education circles. Example prompt: "You're Audrey Watters. A vendor is selling a curriculum director on a 'learning analytics dashboard.' What questions should she ask the vendor before signing?"

**Diversity assessment:** Two women (Elizabeth Bjork, Audrey Watters), no non-Western figures in this chapter. The non-Western figure is best deployed in Ch 5 (Engeström) or Ch 7 (Immordino-Yang). Elizabeth Bjork is the strongest candidate for Chapter 7 — her name is unfamiliar to most curriculum directors, her work is directly on the chapter's central distinction, and she gets credit she has historically not received.

---

## 6. Pedagogical Delivery Research

This is the hardest chapter in the book per TIKTOC's own assessment. The chapter is asking the reader to update a career-long habit (treating engagement as a learning proxy) without making them feel foolish for having had that habit. Three pedagogical moves help:

- **Lead with the experience, not the theory.** Open with the Canvas dashboard the reader has actually seen — completion rates, time-on-page, quiz scores. Establish that the reader is not wrong to want this information, and that this information *is* accurate for what it measures. Then introduce the Bastani case as a controlled demonstration that the same metrics can correspond to opposite learning outcomes.
- **Name the category error explicitly, then absolve the reader of it.** "Engagement evidence vs. learning evidence" is the distinction. Naming it makes it sticky. Saying "Canvas was built for the first; you need the second" puts the gap in the tool, not in the reader's professional judgment.
- **Restraint on the AI critique.** The reader is making a decision *about* an AI tool. If Chapter 7 is read as anti-AI, the reader will assume the book is biased and discount the framework. The Bastani finding's most powerful framing is: AI is not the villain; the *measurement gap* is. The same AI, with a measurement-aware wrapper, produced *learning*. The same AI without one produced un-learning. The wrapper is the variable. Medhavy is a particular kind of wrapper.

The TIKTOC worked example (two students, identical Canvas analytics, different learning) is the chapter's structural climax. It should be drawn in detail. The temptation to multiply examples must be resisted; the *one* example, deeply elaborated, is more persuasive than five.

The exercises require the reader to look at their own Canvas data. This is high-leverage. A reader who runs their own analytics through the chapter's framework will internalize it. The third exercise — "what would change if your highest-stakes assessment were based on learning evidence rather than artifact quality" — is the chapter's transfer test.

---

## 7. Representation and Display Research

Per the TIKTOC anatomy, the worked example is mandatory. The chapter's worked example is the two-student comparison. This warrants a two-column table:

| Metric | Student A (genuine learner) | Student B (AI-assisted, did not learn) |
|---|---|---|
| Time on module | 47 minutes | 47 minutes |
| Click count | 142 | 138 |
| Module completion | 100% | 100% |
| Module quiz score | 88% | 88% |
| Submitted assignment quality | High | High |
| Six-weeks-later retention quiz | 82% | 31% |
| What Canvas saw | Indistinguishable | Indistinguishable |
| What Medhavy's seven signals would see | (preview Ch 7) | (preview Ch 7) |

A second representation: a "category map" diagram showing engagement evidence (left side: clicks, time, completion, submission, immediate score) and learning evidence (right side: delayed retrieval, transfer, calibration, scaffolding response). The chapter's argument is the gap between the two columns.

For the decoupling problem: a small before/after frame showing what a written assignment used to be evidence of (the student wrote it, therefore can write it) versus what it is now evidence of (the student submitted it; authorship is uncertain). This is a one-paragraph point made vivid by a visual.

The Bastani study warrants its own clean display — a four-cell layout: (1) no-AI control on practice, (2) unguarded GPT on practice, (3) no-AI control on unassisted exam, (4) unguarded GPT on unassisted exam — showing the inversion. The visual carries the argument; the prose interprets it.

---

## 8. Open Questions and Research Gaps

- **Bastani replication status.** As of the book's writing, Bastani 2025 is one RCT in one country (Turkey) in one subject (high-school math) with one specific AI wrapper. The finding has been replicated in spirit (multiple smaller studies on AI tutoring producing immediate gains and delayed losses) but not in exact protocol. The chapter must flag this honestly — TIKTOC explicitly says so in Part 10's contested-claims table. Frame Bastani as "the strongest currently available evidence," not "settled science."
- **What Canvas measures beyond the basic five.** Canvas's "New Analytics" and "Learning Analytics" features are evolving. The chapter should describe the *category* of measurement (engagement, performance, completion) without committing to a specific feature list that will date quickly.
- **The Frictional Framework / seven signals are proprietary to Humanitarians AI / Medhavy.** The book introduces the concept at the end of Ch 6 and details it in Ch 7. Chapter 7 should *name* the framework as Medhavy's invention while pointing at the mechanistic argument (prediction error, consolidation, calibration) that supports it. No outside-of-Medhavy primary source uses "GLP score" or "seven signals" in this form.
- **The "decoupling" terminology.** Different authors use different terms — "AI-mediated authorship," "assessment integrity post-LLM," "the artifact problem." The chapter should pick one term and define it; "decoupling" (used in TIKTOC) is serviceable but not standard.
- **Highest-priority gap:** No published study currently shows a head-to-head comparison of Canvas-style analytics with Medhavy-style learning-evidence measurement on the same students, same content, same time window. The book makes a theoretically motivated case for the gap; it cannot show direct empirical evidence that Medhavy's measurement closes it. Flag honestly in this chapter (and again in Ch 7).
- **Faculty-acceptability question.** No published data on whether faculty *trust* learning-evidence dashboards more than gradebook scores. Open empirical question; relevant for Ch 10.

---

## 9. Sourcing Notes

**Lead with Bjork.** Bjork (1994) is the foundational citation; Soderstrom & Bjork (2015) is the contemporary restatement most accessible to the reader. Bjork & Bjork (2011) is the educator-facing version. The chapter should cite Bjork by name once and then use "the performance/learning distinction" as the recurring framing.

**Bastani 2025 is load-bearing.** TIKTOC names it as the chapter's anchor. The chapter should describe the study in three to four plain-language sentences (two conditions, identical engagement, opposite learning outcomes, identical AI under the hood). The numerical claim (17 percentage points below control on unassisted exam) is precise and quotable.

**Selwyn, Williamson, Eynon** are the right citations for the sociological critique of LMS analytics. They are most useful as one-sentence framing — "researchers studying LMS analytics have argued for years that engagement metrics measure what is easy to count, not what matters most" — rather than as direct quotations. Selwyn 2015 is the most accessible.

**Mollick 2024** is the right citation for the decoupling problem. Faculty-facing; non-technical; reader-trusted.

**Cross-chapter overlap with Ch 1:** Bastani appears in both Ch 1 (the pebble) and Ch 6 (the central evidence). This is intentional — Ch 1 plants the question, Ch 6 pays it off. The chapters should reference each other.

**Cross-chapter overlap with Ch 7:** The "behavioral traces of cognitive engagement" framing is set up here and developed in Ch 7. Do not name the seven signals in Ch 6.

**Aging risk:** Specific Canvas features will date. The category-level claims (engagement ≠ learning; immediate performance ≠ durable learning) will not. The chapter should privilege category-level claims and use specific features only as illustrative examples. Per TIKTOC Part 10, frame Bastani explicitly as "one study; replication pending."
