# Research: Chapter 10 — When Kindle Is Enough
## Medhavy: Is the Loop Worth It?

**Chapter one-line:** The reader gets the complexity threshold test — three questions that determine whether their deployment warrants Medhavy or whether AI+1 on Kindle is the complete answer.
**Research date:** 2026-05-27

---

## 1. Primary Sources

### Foundational papers and texts
- **Kirkwood, A. & Price, L. (2014).** "Technology-enhanced learning and teaching in higher education: what is enhanced and how do we know?" *Learning, Media and Technology*, 39(1), 6–36. Meta-review of ~150 studies. The dominant finding: most technology adoptions in HE produce no measurable learning improvement when controlled for instructor effort and time-on-task. The "enhancement" is usually administrative or experiential, not learning-outcome based. Load-bearing for the Ch 9 argument because it documents — across a decade and many domains — that adding technology by default does not help learning.
- **Cuban, L. (2001).** *Oversold and Underused: Computers in the Classroom.* Harvard University Press. The "high access, low use" pattern: institutions buy computers; teachers use them for word processing. The book's hardest finding: even when technology is genuinely available, the curricular gravitational field pulls usage back toward administrative tasks. Predicts Medhavy's worst-case failure: bought, deployed, used as a fancy PDF reader.
- **Selwyn, N. (2014).** *Distrusting Educational Technology: Critical Questions for Changing Times.* Routledge. The "critical lens" book. Argues that edtech rhetoric routinely confuses adoption with improvement. Most useful for Ch 9's tone: skeptical without being reactionary.
- **Morozov, E. (2013).** *To Save Everything, Click Here: The Folly of Technological Solutionism.* PublicAffairs. The solutionism critique in its sharpest form. "Solutionism" = treating every situation as a problem to be solved by technology, even when the situation does not need solving. Directly relevant when a curriculum director with a working stack is being pitched a new layer.
- **Reeves, T. C. & Reeves, P. M. (2008).** "Implementing online learning: The frontiers of issues to resolve." *Distance Education*, 29(3). Names the recurring adoption failure modes — overestimated faculty readiness, underestimated implementation cost, mismatch between tool and pedagogical need. The taxonomy is what Ch 9 should help the reader avoid.
- **Watters, A. (2021).** *Teaching Machines: The History of Personalized Learning.* MIT Press. Traces the century-long arc from Pressey's testing machines through Skinner's teaching machines to today's adaptive platforms. The pattern: each generation oversells personalization; each generation discovers the rate-limiting step is curricular labor, not the algorithm. Critical for naming the genre Medhavy belongs to and what historically goes wrong inside it.
- **Bainbridge, L. (1983).** "Ironies of Automation." *Automatica*, 19(6), 775–779. The foundational paper on when not to automate. Two ironies: (1) automating the easy parts leaves humans with the hard, residual parts they are less rehearsed at; (2) automated systems still need human oversight, but the operator's skill atrophies. Both apply to Medhavy: if the loop "decides," what does the instructor still know?
- **Cohen, D. K. & Ball, D. L. (1999).** "Instruction, capacity, and improvement." CPRE Research Report. The "capacity" argument: institutions can only absorb improvements they have the capacity to implement. Capacity is faculty time, instructional design expertise, and willingness to change practice — not budget. A program with budget but no capacity buys overhead.

### Key empirical cases
- **LAUSD iPad rollout (2013–2015).** ~$1.3 billion total program (often cited as "$19B" in error — the $1.3B figure is well-documented in LA Times reporting and the FBI investigation). One iPad per student plus Pearson curriculum bundled. Collapsed within two years: incomplete curriculum, broken devices, students bypassing security, no instructional design layer. The canonical example of "infrastructure without capacity."
- **inBloom collapse (2014).** Gates-funded student data infrastructure project. Shut down 15 months after launch — not because the technology failed, but because the institutional change management failed. Parents, teachers, and state legislatures revolted over the data-sharing model. Showed that even a well-engineered platform can collapse if the institution is not ready for what it asks of them.
- **Reich, J. & Ruipérez-Valiente, J. A. (2019).** "The MOOC pivot." *Science*, 363(6423), 130–131. Showed median completion rates around 3% across the major MOOC platforms; most users do not return after the first week. The implication for Medhavy: deployment ≠ engagement; engagement ≠ learning. Each layer of the pipeline drops the population, often by an order of magnitude.
- **Holland & Tirthali (2014, Columbia CBCSE) MOOC cost study.** Estimated $39,000–$325,000 per MOOC to produce. Demonstrated that "scale" rhetoric masked the up-front curricular cost — the same hidden cost Medhavy will impose through its concept map and Case Study review burden.

---

## 2. The Core Concept — State of the Field

### What is settled
- Educational technology, on average, produces small to null learning gains when studies control for instructor time and curricular redesign (Means, Toyama, Murphy, Bakia, Jones 2010 meta-analysis; Tamim et al. 2011; Escueta et al. 2020 J-PAL review).
- The variation between deployments of the same technology is larger than the average effect — meaning context, not the tool, is the primary driver. (This is also Bastani 2025's finding in the AI-tutor case: same AI, different wrapper, opposite outcomes.)
- "Solutionism" is a documented institutional pathology, not a rhetorical accusation. Procurement processes routinely reward visible action over correct action.
- Faculty time is the binding constraint in HE technology adoption — not budget, not infrastructure (Educause faculty time studies 2019–2023).

### What is disputed
- Whether adaptive systems can produce population-level gains at all when deployed without intensive curricular design. The optimistic camp (Pane et al. 2014, RAND on Cognitive Tutor) shows modest gains under intensive support. The skeptical camp (Watters; Selwyn; Williamson) argues these gains do not survive deployment outside heavily-resourced pilots.
- Whether the right unit of analysis for "did it work" is the average student, the marginal student, or the variance of outcomes. Different conclusions follow from each choice.

### What has changed recently (last 5 years)
- Generative AI (post-ChatGPT, late 2022 onward) has destabilized many assessment assumptions. The artifact-based assessment is no longer a reliable proxy for learning. This actually strengthens the case for measurement-and-adaptation layers — but only where there is enough scale and stake to justify the measurement infrastructure.
- "Pilot fatigue" is a documented phenomenon in HE (Educause 2023 Top 10 issues): institutions that adopted many edtech tools during the pandemic now report that the marginal tool subtracts attention.
- LMS data dashboards have become more capable. Canvas New Analytics, D2L Brightspace Insights, and Anthology Reach all now offer some learning-evidence signals (delayed performance, prerequisite mastery curves) that did not exist five years ago. The "Canvas can't measure that" claim must be precise about what specifically Canvas can and cannot do as of 2025.

---

## 3. Application Domain Examples

1. **Nursing fundamentals class, N=28, one instructor.** Single section, one faculty member who knows every student's name by week two. AI+1 pharmacology Kindle, Anki for drug recall, Canvas for assignments. The instructor's office hours and weekly quiz review are the adaptation loop. Adding Medhavy here adds dashboards she already has in her head. **Recommendation: Kindle is enough.**

2. **Anatomy & physiology, two sections of 60, two instructors who don't coordinate.** Each instructor adapts independently. Variation between sections is high but neither instructor is willing to share or change practice based on the other's data. The middle-condition case: the data would exist, but the institution is not willing to act on it. **Recommendation: Kindle is enough — institutional capacity, not technology, is the binding constraint.**

3. **Pharmacology, 4 sections × 80 students, shared exam, accreditation pressure to reduce variance.** The board pass rate varies 12 points across sections. Faculty have agreed they will redesign whichever section underperforms. **Recommendation: this is the deployment where the loop earns its cost.**

4. **Pre-clinical clerkship, 240 students rotating through 8 clinical sites.** Different attending physicians, different patient mixes, no shared curriculum tracking. Performance gaps exist but cannot be attributed without measurement. The institution has a curriculum committee with budget authority. **Recommendation: loop earns its cost — but only if the curriculum committee precommits to the redesign step.**

5. **CE / professional update modules for licensed pharmacists.** Asynchronous, no live instructor, ~500 enrollees per quarter, completion is the regulator-relevant outcome (not durable learning). The institution is not willing to act on durable-learning data because the regulator does not ask for it. **Recommendation: Kindle is enough. The loop has no reward signal.**

---

## 4. The Book's Thesis Connection

Chapter 10 is the chapter that earns the book's credibility. The thesis claims Medhavy is overhead unless three conditions hold; the test of that claim is whether the book is willing to name — specifically, by deployment type — the cases where the simpler stack wins.

The connection works on three levels:

**First, it operationalizes the "three conditions" thesis** by turning it into a falsifiable test the reader applies to her actual deployment. The chapter's job is not to argue that the conditions are good or bad; it is to give the reader an honest way to check her own situation. A reader who runs the test and lands at "no" must trust the test enough to say so out loud at a budget meeting. That trust is built only if the test sometimes says no in named, specific cases.

**Second, it inoculates against the failure mode the book itself could cause.** A book about Medhavy, written by people associated with Medhavy, that always concludes "yes, adopt" would be vendor literature. The whole point of the decision-support frame is that the reader is making a real decision with real consequences, and the book has to be the kind of advisor who occasionally says "don't buy this." Chapter 10 is that advisor speaking aloud.

**Third, it positions Medhavy correctly in the edtech historical record.** Watters and Cuban document a century of teaching-machine rhetoric that oversold and underdelivered. Medhavy will only escape that pattern if its adopters are pre-filtered for the conditions where the loop can actually close. The book that helps that pre-filtering happen does Medhavy a favor — even when it tells some readers not to buy.

Section 4 of the chapter must say plainly: in named deployment types — small single-instructor courses, sections where faculty will not coordinate, CE modules without durable-learning stakes — the book recommends against Medhavy. Not as a hedge. As the correct answer.

---

## 5. The AI Wayback Machine — Candidate Figures

**Recommended: Audrey Watters.** Independent edtech critic, author of *Teaching Machines* (MIT Press 2021) and the long-running Hack Education blog (2010–2022). Not Anglo-male academic; not famous in the Kahneman sense; deeply qualified. Her central argument — that "personalized learning" is a recurring marketing frame for what is usually behaviorist content-delivery — is the precise frame a reader of Ch 9 needs to hold while evaluating Medhavy. Diversity scrutiny: woman, independent (not academic-credentialed), explicitly critical of the field. **Use her.**

**Strong alternative: Diana Laurillard.** Professor of Learning with Digital Technologies at UCL Institute of Education. Built the Conversational Framework — a six-step model for evaluating when a technology adds or subtracts from the dialogic exchange between teacher and learner. Author of *Teaching as a Design Science* (2012). British, woman, senior. Her framework is the analytical scaffolding behind exactly the question Ch 9 asks: does adding this layer enrich or substitute the human conversation? Diversity scrutiny: woman, UK-based, technical-pedagogical hybrid. **Strong second choice.**

**Honorable mention: Larry Cuban.** *Oversold and Underused* author, Stanford historian of education. Risks: white, male, American, very well-known in the field. Use only as quoted source, not as the wayback figure.

For Ch 9 final: Watters is the right pick. She is alive, accessible, less famous than Kahneman or Cuban, and her work is precisely about distinguishing genuine learning improvement from technological theater.

---

## 6. Pedagogical Delivery Research

The reader is a curriculum director under time pressure. The chapter must do three things mechanically:

1. **Present the three-question test before any case examples.** The test is the chapter's load-bearing artifact. Reader should be able to flip back to it.
2. **Run multiple deployments through the test in fast succession.** Five deployments in 600 words; each with a one-sentence verdict. The cumulative effect should feel like an experienced colleague rapid-firing through her clients.
3. **End with a "permission to say no" paragraph.** This is the chapter's emotional payload — the reader needs to feel that recommending against Medhavy is a defensible, professional answer, not a failure to keep up.

Pedagogical scaffolding: opening case should be a deployment that fails the test, not one that passes. The book has spent eight chapters building enthusiasm. The reader's natural state at Ch 9 is "I want to buy this." Opening with a failure case interrupts that.

Worked-example density: 5 deployments × ~120 words each. Standard textbook-case density.

---

## 7. Representation and Display Research

The chapter calls for a **three-question test display**. Three formats are candidates:

**Option A: Decision tree / flowchart.** Three diamond nodes (one per question), yes/no branches, terminal recommendation boxes. Pro: visually obvious. Con: implies more deterministic decision-making than the chapter wants. The three questions are weighted by context, not pure AND-gates.

**Option B: Checklist with verdict matrix.** Three rows (the questions), columns for each deployment. Empty cells get filled with the reader's honest answer. Pro: matches how a curriculum director would actually use the test (literal worksheet). Con: less visually arresting.

**Option C: 2x2x2 cube (eight cells).** All three questions binary, eight outcomes. Pro: shows the partial cases the chapter wants to name (one-yes, two-yes). Con: a 2x2x2 is hard to draw legibly on a Kindle screen.

**Recommendation: Option B (checklist with verdict matrix) as the primary artifact, plus a short prose ladder of the eight combinations.** The checklist is what the reader takes to the budget committee. The prose ladder is what helps her interpret partial answers.

For Kindle constraints: black-and-white reproducible, < 4 inches wide. Avoid color-coding; use shape (filled circle = yes, open circle = no) and a bold "VERDICT" column.

---

## 8. Open Questions and Research Gaps

1. **Threshold sharpness.** "Scale" in question 1 is fuzzy. Is 60 students enough? 100? 300? The chapter must give the reader a working number while admitting it is heuristic. Author decision needed.
2. **"Willing to act" measurement.** Open Question 3 in TIKTOC asks the same thing. We need at least one named example of an institution that had the measurement and did not act. Cuban's general findings are the next-best evidence; a specific case would be stronger.
3. **What counts as the "simpler stack."** Is it AI+1 Kindle + Canvas, or AI+1 Kindle + Anki + Canvas? The book has talked about both. Ch 9 should pick one and stay with it.
4. **The "yes-but-not-yet" case.** The chapter currently treats the test as binary per question. A more honest treatment might say: "All three are no right now, but the deployment is growing." This is real for a program scaling from 30 to 300 students over three years. Worth one paragraph.

---

## 9. Sourcing Notes

- Bastani 2025 (referenced through Ch 1, 6) is the most current evidence; use it once in Ch 9 to remind the reader that "looks engaged ≠ is learning" is not just an abstract concern.
- LAUSD figures are commonly mis-cited as $19B; the correct figure is approximately $1.3 billion (LA Times 2014–2015 coverage; FBI/SEC investigation documents). Use $1.3B and note that the program was eventually wound down with substantial losses.
- Watters' *Teaching Machines* is the strongest single source for the historical-pattern argument; quote sparingly to keep the chapter the curriculum director's voice, not the historian's.
- Cohen & Ball "capacity" argument is the deepest theoretical anchor for the "willing to act" condition. Worth one direct invocation.
- Kirkwood & Price 2014 is the meta-review that lets the chapter say "this is a documented pattern, not a single skeptic's view."
