# Chapter 4 — Quiz Me: Making Knowledge Stick

**The reader learns what spaced retrieval practice is, why it works, and when Quiz Me adds something that Anki or Canvas quizzes do not.**

---

## Opening case

There is a finding in cognitive psychology so well-replicated that it functions as a law: **testing yourself on material produces more durable learning than re-reading it, even when re-reading feels more productive.** Students who study by testing themselves perform worse on a quiz given immediately after the study session and better on every subsequent quiz at longer delays. The crossover is reliable, the size is meaningful, and the effect runs in the opposite direction of student intuition.

This is the testing effect. It was first cleanly demonstrated by Henry Roediger and Jeffrey Karpicke in a 2006 *Psychological Science* paper that has been replicated hundreds of times. It is the cognitive-science mechanism Quiz Me [Humanitarians AI internal framework] is built on. The first job of the chapter is to install the finding cleanly, because if the reader leaves with "testing helps learning" she has heard a slogan; the chapter needs her to leave with the counterintuitive consequence — that the practice technique that *feels* most productive is not the one that *produces* the best retention, and that the gap between feeling and outcome is the variable her students are navigating every time they study.

The second job: distinguish Quiz Me from Anki, from Canvas quizzes, and from AI-generated flashcard apps. All four use the word "quiz" or "retrieval"; none of them are the same product. Quiz Me adds four things that matter to a health-sciences curriculum, and the reader needs to be able to articulate them in a budget meeting.

---

## The testing effect in plain language

The mechanism is not complicated. Memory is not a recording you replay; it is a structure you rebuild every time you retrieve. The rebuilding is what consolidates the memory — each retrieval is a reinforcement of the pattern that lets you retrieve it next time. Re-reading skips the rebuilding step. You recognize the material on the page; recognition is much easier than recall; recognition does not consolidate the trace the way recall does. Two students who spend the same hour studying the same material — one re-reading, one self-testing — leave the hour with different memory structures. The self-tester has the structure that survives; the re-reader has the structure that decays.

Roediger and Karpicke's 2006 paradigm was elegant. Students read short prose passages. Some students re-read the passages multiple times. Other students read once and then tested themselves with free recall. Immediately after, the re-readers scored higher — they could reproduce more from the passage. Then the delays: two days, one week. The re-readers' performance collapsed. The self-testers' performance held. By the one-week measurement, the testing group was outperforming the re-reading group by a margin large enough to overturn 50 years of intuitive study advice.

The students' own predictions, before the delay, were exactly backwards. The re-readers predicted they would do better at delay; they had felt productive during practice. The self-testers predicted they would do worse; they had felt unproductive — making errors, struggling to retrieve, leaving items blank. The feeling-of-productivity and the actual learning were *anti-correlated* in this paradigm. This is the most important thing the chapter has to install in the reader's head, because it explains why students universally prefer re-reading and why student preference is not a reliable signal of pedagogical effectiveness.

The 2011 follow-up was stronger. Karpicke and Blunt, in *Science*, ran retrieval practice against *elaborative study with concept maps* — a technique many curriculum directors actively recommend. Retrieval practice won, again, on delayed retention. The concept-map students predicted they would do better; they did worse. The chapter is not asking the reader to abandon concept maps — they have other uses — but the reader needs to know that retrieval practice outperforms even the techniques her faculty are most likely to endorse.

The summary citation a curriculum director can take to a colleague is Dunlosky and colleagues' 2013 *Psychological Science in the Public Interest* review. The PSPI is open-access, written for policy audiences, and ranks ten common study techniques by evidence strength. Two techniques receive "high utility" ratings: practice testing and distributed practice. The other eight (highlighting, summarizing, rereading, keyword mnemonics, imagery, etc.) range from "moderate utility" to "low utility." Quiz Me is built on the two techniques the most rigorous review in the literature places at the top. This is not a marginal evidence base; this is the strongest evidence base in the entire study-skills literature.

A reader's note from Robert Bjork's "desirable difficulties" framework, codeveloped with Elizabeth Bjork: the same Bjorks who drew the performance-learning distinction in Chapter 1 also drew the related principle that *interventions which slow current performance often improve durable retention.* Quiz Me feels harder than re-reading. Students will report it as harder. That is the predicted experience of a technique tuned to produce desirable difficulty. The chapter's recommendation, repeated here and in Chapter 9, is that the student satisfaction signal in the first three weeks of Quiz Me deployment is not the right signal to act on. Wait for the retention measurement.

---

## Spaced repetition — the second pillar

Retrieval is the first mechanism. Spacing is the second. Together they account for most of the documented gain.

The spacing effect: if you have an hour to study something, you produce more durable retention by distributing the hour across multiple sessions over days than by spending the hour in one block. Cepeda and colleagues' 2006 meta-analysis in *Psychological Bulletin* synthesized 184 studies of verbal recall and found the effect was large, consistent, and held across age groups and domains. Distributed practice is the technique that paired with practice testing earned a "high utility" rating in the Dunlosky review. Together they are the two pillars Quiz Me runs on.

The mechanism, again, is not complicated. Each retrieval reinforces the trace; the next retrieval is slightly harder because some forgetting has occurred between retrievals; the harder retrieval, when successful, reinforces the trace more strongly than an easy retrieval would. This is the desirable-difficulties principle applied to scheduling. The longer the gap (without crossing into total forgetting), the more the retrieval costs and the more it pays. An algorithm that schedules retrievals at the right intervals — long enough to produce desirable difficulty, short enough to avoid forgetting — is implementing the spacing effect in software.

This is what spaced-repetition algorithms do. The history is worth a paragraph. Piotr Woźniak, a Polish researcher self-experimenting on his own retention through the 1980s, built SuperMemo and the SM-2 algorithm in 1985 — years before the cognitive psychology mainstream caught up to the practical importance of spacing. SM-2 dominated flashcard scheduling for 30 years. Anki, the most-used spaced-repetition app among medical students, ran SM-2 by default through 2023. In November 2023, Anki switched to FSRS (Free Spaced Repetition Scheduler), an open-source community-engineering project that models memory with three parameters — difficulty, stability, retrievability — and personalizes the schedule per card. FSRS produces roughly 20-30% fewer reviews for equivalent retention. Quiz Me runs FSRS.

A caveat the chapter has to flag, because the TIKTOC contested-claims table flags it: FSRS is demonstrably more *efficient* than SM-2. It is not separately demonstrated to produce better *learning outcomes* — students may save 25% of their review time at equivalent retention, but whether the saved time produces additional learning gains in the course is not a peer-reviewed claim. The chapter presents FSRS as the algorithm that scales the spacing effect efficiently to a curriculum's worth of material, not as a separate learning intervention.

The one-sentence version of the algorithm the reader can take to a budget meeting: *the more you struggle to retrieve a card — and still retrieve it correctly — the longer the algorithm waits before scheduling it again.* That is the rule. It is older than the algorithm; the algorithm just executes it precisely.

The very-long-tail evidence: Harry Bahrick, working at Ohio Wesleyan, ran a 50-year retention study published in 1984 — 733 former students of high-school Spanish, tested decades after their last formal study. The students whose original study had included spaced retrieval retained vocabulary in what Bahrick called "permastore" — a memory state that resists decay for decades. The students whose original study had been massed and re-reading lost their vocabulary on the timescale of years. Bahrick's permastore is the empirical ceiling of what spaced retrieval can produce in a learner. A daily Quiz Me habit in a 15-week pharmacology course is not just preparing the student for the final exam; it is, on the long-tail evidence, building a memory structure that can survive decades.

---

## What Quiz Me adds beyond Anki

This is where the chapter has to do specific work. Many curriculum directors have students using Anki. Many faculty have written or curated Anki decks. The "why pay for Quiz Me when Anki is free?" question is real and the chapter has to answer it honestly. Four differentiators, drawn from the Medhavy primary manuscript.

**Differentiator 1: Concept-map integration.** Anki cards are orphans. They exist in the deck, scheduled by FSRS, decoupled from any curriculum structure beyond the tags the student or deck author chose to apply. Quiz Me cards are pinned to nodes in a concept map — a graph the institution builds (or imports from Medhavy templates) that names the concepts in the curriculum and the prerequisite relationships between them. When the bandit (Chapter 8) decides whether to schedule a Quiz Me session on receptor pharmacology, it is operating on the same concept node that other modes operate on. The card's performance feeds the same measurement system. A struggle on a Quiz Me card on beta-1 selectivity becomes a signal the bandit can use to decide whether to deploy Ask AI on the prerequisite concept (sympathetic activation). The cards are not orphans; they are instrumented nodes in a measured curriculum.

**Differentiator 2: Priority weighting for high-importance concepts.** Anki treats every card equally — the algorithm schedules based on retention alone. Quiz Me weights concepts by institutional importance. A safety-critical concept (the difference between IV push and IV piggyback for a high-alert medication; the contraindications for beta blockade in decompensated heart failure) is weighted upward; the algorithm allocates more practice to it even if the student is consistently retrieving correctly. The instructor or curriculum designer assigns the weights. Quiz Me operationalizes them.

**Differentiator 3: The aviation pedagogy override.** The FAA Aviation Instructor's Handbook (FAA-H-8083-9) is the most explicit articulation of this principle outside the military. Commercial pilots review certain procedures — emergency descent, stall recovery, decision speed callouts — *regardless* of recent demonstrated competency. The recall score is irrelevant; the procedure is reviewed on a fixed schedule because the cost of forgetting is fatal. Aviation pedagogy has built this override into every flight school's curriculum for decades. Quiz Me brings the same override into health sciences, where the parallel is direct — code procedures, sterile technique, drug-dose ceilings, allergic reactions. The faculty designates certain concepts as safety-critical. Those concepts get reviewed on a regular schedule, never spaced out below a minimum interval, no matter how strong the student's retrieval has been. This is not an FSRS feature. This is not an Anki feature. This is a Quiz Me feature, and for a nursing or pharmacy program it is one of the most consequential differentiators.

**Differentiator 4: Prerequisite interleaving.** When FSRS schedules a card, it schedules that card. Quiz Me, because it knows the concept map, can interleave cards from the prerequisite chain — practicing the beta-1 receptor selectivity card alongside cards on adrenergic physiology and sympathetic activation. Interleaving forces discrimination learning, the kind of practice that distinguishes between similar-looking concepts. Two drugs with similar-sounding names and different mechanisms; two clinical syndromes with overlapping presentations and different management; two diagnostic criteria with the same threshold and different applications. The pedagogical literature on interleaved practice (Rohrer and colleagues, 2007 onward) is clean: interleaved practice produces better discrimination than blocked practice, and discrimination is what clinical performance under time pressure requires.

These four together are the answer to "why pay for Quiz Me when Anki is free?" Anki is free because it is an algorithm with a deck. Quiz Me is the algorithm with the deck *plus* the curriculum integration, the institutional weighting, the safety-critical override, and the prerequisite interleaving. For a self-directed student studying for a board exam, Anki is plausibly enough. For an institution trying to ensure that 300 students across five sections retain the safety-critical material before they touch a real patient, Anki is a free tool that does not do four of the things the institution needs.

---

## When Quiz Me is NOT the right mode

The four-mode sequence is, again, a sequence. Quiz Me is the *retention* mode. It does that job well. It does not do the others, and using it for jobs it was not designed for produces predictable failures.

**Failure case 1: Concepts requiring application under ambiguity.** Quiz Me cards have a correct answer. The student retrieves the answer; the card is scored; the algorithm schedules. This works for "what is the half-life of metoprolol" — there is a number, and either the student retrieves it or she does not. This does not work for "should this patient receive beta blockade?" Clinical decision-making under ambiguity has no card-correct answer; the cognitive operation is weighing competing considerations, not retrieving from memory. Forcing the operation into a flashcard format produces pattern-matching — students learn the surface cues that produce the answer the card expects, not the reasoning that produces a defensible decision. Case Study (Chapter 5) is the right mode for application under ambiguity.

**Failure case 2: Generative capability.** A student cannot retrieve a novel patient-education protocol from memory because she has not produced one yet. The cognitive operation is generative — building something new, defending it, revising it. Quiz Me does not build this. Glimmer (Chapter 5) does. Pretending retrieval practice produces generative capability is the most common over-promise in the spaced-repetition marketing literature, and the chapter has to refuse it.

**Failure case 3: Acquisition without a schema.** A student who has never encountered the concept cannot retrieve it. Quiz Me cards on first-encounter material produce the experience of failing every card, which is demoralizing and not pedagogically useful. The right mode is Ask AI (Chapter 3) for the acquisition stage; Quiz Me enters once the schema is forming and needs to be made durable. Some Medhavy deployments configure this as a phase gate — Quiz Me cards on a concept node unlock only after the student has demonstrated Ask AI engagement on that node. This is a curriculum-design choice; the institution can configure it differently, but the principle holds: retrieval practice without a schema to retrieve from is empty practice.

The principle the reader needs: Quiz Me is for the durable-retention job, and the durable-retention job is one of four jobs in the cognitive sequence. The other three jobs need their own modes. A program that deploys Quiz Me as if it were the whole learning system is using a hammer on every problem and missing the ones that are not nails.

---

## The habit loop

This is the part of the chapter most likely to surprise an institutional reader, and the part most predictive of whether Quiz Me will succeed in a particular deployment.

Quiz Me is designed as a *habit*, not an assessment. The interface is built around a due-count counter — the number of cards waiting for review today — and a completion event that registers as a reward (the counter going to zero). The design moves are taken straight from habit-formation research: a clear trigger (the daily due count), a small predictable behavior (12 minutes of cards), a satisfying completion signal (the counter reset). The instructor's gradebook does not look at Quiz Me. The institution does not punish missed days directly. Quiz Me is a maintenance habit the student installs, with the algorithm doing the work of deciding what gets practiced when.

This design choice has institutional consequences. Quiz Me works when students form the habit. Most deployments show a bimodal adoption pattern — roughly 20% of students never form the habit and largely ignore Quiz Me; roughly 60-80% form the habit and use it consistently; the remaining fraction adopts late. The institutional levers that move the bimodal distribution are not Quiz Me features — they are curriculum-design choices. Programs that make Quiz Me usage a graded component of the course (5% of the grade for hitting weekly retention thresholds, say) reliably achieve 80%+ adoption. Programs that make it optional reliably achieve 30-50%. The habit-gap problem (a well-known finding in spaced-repetition tool deployments) is not solvable by the software alone. The institution has to commit.

The aviation pedagogy parallel matters again here. The FAA does not make recurrent training optional. The reason aviation has the safety record it has — and the reason a 60-year-old pilot can perform a procedure she last used three years ago — is that the institution mandates the practice schedule. Health-sciences institutions that want the same retention pattern in their graduates need the same institutional commitment. Quiz Me provides the algorithm and the interface. The institution provides the requirement.

For Question 3 of the three-question test (willingness to act): in the Quiz Me context, willingness to act means willingness to make Quiz Me usage a graded or otherwise-enforced component of the curriculum. An institution that adopts Medhavy and then makes Quiz Me optional has not closed the loop on the retention layer. Most of the value evaporates.

---

## Worked example: two students preparing for a pharmacology board

Two PharmD students preparing for the same pharmacology board exam, 12 weeks out. Same content, same baseline, same target. Different study strategies.

**Student A: re-reading.** Studies for 90 minutes every Sunday afternoon. Re-reads chapters of the AI+1 pharmacology text. Highlights. Takes margin notes. Self-rates comprehension as high after each session. Two weeks before the board exam, takes a practice test offered by the program. Scores 78.

**Student B: Quiz Me.** Spends 12 minutes every morning before clinical rounds working through Quiz Me. The algorithm schedules cards based on her retention; she has 60-90 cards a day. Some are concepts she learned six months ago; some are concepts she learned this week. She finds the practice annoying — many days she retrieves cards wrong. She rates her comprehension as medium-to-low. Two weeks before the board, she takes the same practice test. Scores 72.

By the in-session-feeling metric, Student A is doing better. By the practice-test metric two weeks out, Student A is doing better. The dashboard would show Student A winning.

**The exam.** No AI, no notes, no review time. Twelve weeks of preparation tested at once. Student A scores 81. Student B scores 89.

What happened. Student A's re-reading produced strong recognition memory — the practice-test items, which had been written by the same faculty as her textbook, looked familiar; she could pick out the right answer through partial recognition. The board exam items, written by the national testing body, did not look familiar. Recognition memory does not transfer when the surface features change. Student A had the structure of a re-reader: high in-session performance, weak retrieval at delay.

Student B's spaced retrieval produced durable recall memory. The board exam items required retrieval, not recognition. She had practiced retrieval every morning for 12 weeks. The cards she had struggled with had been spaced longer; the cards she had retrieved easily had been spaced longer still. The algorithm had been operating on her actual forgetting curve, not on the curve she would have chosen. By exam day, her retention structure was the structure that survives the lossy transfer from study material to test material.

This is the testing effect in one scenario. Two students. Same material. Same time invested. The pattern Roediger and Karpicke documented in 2006 reproduces, decades later, in a board-exam preparation context. The student who felt she was working harder during practice produced worse outcomes; the student who felt she was working less effectively produced better ones.

For a curriculum director: the chapter is not asking you to require Quiz Me on faith. It is asking you to recognize that the dashboard signals your faculty currently trust — practice-test scores, student satisfaction, perceived comprehension — are signals from inside the practice window. The signal you care about is on the other side of the lossy transfer to the licensure exam, the clinical encounter, the situation 12 weeks or 12 months from now where the student will retrieve without scaffolding. That signal lives in cards being retrieved at delay. Quiz Me's FSRS schedule is designed to produce evidence on exactly that signal.

---

## Exercises

1. **(Apply, to your own curriculum)** Identify five concepts in your curriculum that require durable factual recall — drug names and dosing ranges, anatomical structures, clinical decision criteria, lab value thresholds. These are Quiz Me candidates. Then identify five concepts that require reasoning under ambiguity — when to escalate, how to weigh competing risks, when to deviate from protocol. These are not Quiz Me candidates; they are Case Study territory. The exercise is to make sure you can tell the difference between content types. If you find yourself wanting to put a concept in both lists, that concept probably has a retrieval-foundation component (Quiz Me) and an application component (Case Study) — note both.

2. **(Analyze)** Your institution currently uses Canvas quizzes for retrieval practice. What does Quiz Me's FSRS scheduling and concept-map integration add that Canvas quizzes cannot provide? Be specific: name at least two mechanisms (e.g., adaptive scheduling per card, concept-prerequisite interleaving, safety-critical override). The exercise tests whether you can defend the line item against the "we already do quizzes in Canvas" objection — which you will hear.

3. **(Evaluate, to your own deployment)** For a 15-week course, estimate the difference in total Quiz Me sessions a student would complete if the habit forms in week 2 versus week 6. Then identify the single curriculum-design choice that, in your judgment, would most affect when the habit forms. Common candidates: making usage a graded component, requiring a 7-day streak as a course participation gate, framing Quiz Me as professional habit-building in the first lecture rather than as a study tool. The exercise is testing whether you can name the institutional lever, not just the software feature.

---

## Common misconceptions

**"Quiz Me is Anki with the Medhavy logo."** The four differentiators (concept-map integration, priority weighting, aviation override, prerequisite interleaving) are real, and they matter to a health-sciences program. Anki is a free, excellent tool for self-directed learners. Quiz Me is an institutional tool that integrates with curriculum, instructor dashboards, and the rest of the loop. The reader needs to be able to articulate the four differentiators in a budget meeting; the meeting will go badly otherwise.

**"If students like a study technique, it's working."** Reliably wrong, predicted to be wrong by 30 years of cognitive science. Students like re-reading. Re-reading produces less learning than retrieval practice. Bjork's desirable-difficulties principle predicts the satisfaction-outcome inversion directly. The chapter's recommendation: do not act on student satisfaction signals in the first three weeks of Quiz Me deployment. Wait for the retention measurement.

**"Retrieval practice equals quiz-taking equals assessment."** Three different things. Quiz Me is *practice*, not assessment. The cards are not graded by the instructor. The point is to engage retrieval as a learning mechanism, not to evaluate the student. Faculty who conflate them often demand that Quiz Me replace exams, which it cannot; or that exams be downgraded because Quiz Me is doing the work, which is also wrong. Quiz Me supplements assessment; it does not replace it.

**"FSRS is just a better SM-2."** Technically true and mostly irrelevant. The algorithm switch is a footnote. The curriculum-integration differentiators are what matter. A reader who fixates on the algorithm has been pulled into the wrong conversation.

**"AI-generated flashcards from ChatGPT do the same thing."** They do not. They produce cards from a textbook chapter; they do not produce the institutional integration, the safety-critical override, or the prerequisite interleaving. They also produce cards of variable quality with no faculty review — for a pharmacology context where a confidently-wrong card on drug dosing could cascade into a clinical error, the absence of faculty review is not a minor concern.

---

## What would change my mind

The chapter's central claim is that Quiz Me's combination of FSRS scheduling, concept-map integration, priority weighting, and prerequisite interleaving produces meaningfully better retention than free flashcard alternatives in a health-sciences curriculum. A finding that would revise this claim: a large randomized trial — multi-institution, year-long, with delayed retention as the outcome — showing that student-curated Anki decks produce equivalent retention to faculty-curated Quiz Me decks at the same study time. The testing effect itself would survive; the case for Quiz Me's specific differentiators would not. The current evidence supports the differentiators on mechanism (interleaving research, safety-critical override literature, FSRS efficiency studies), not on direct outcome comparison; the outcome comparison study is, as far as the chapter knows, not yet published. The honest framing is that Quiz Me's differentiators are well-grounded design choices, not separately-tested effects.

---

## Still puzzling

- Why does adoption of spaced-repetition tools stall around 20% in many higher-ed deployments? The behavioral economics of habit formation in university students is undertheorized in the cognitive-science literature. Most of what is known is anecdotal, coming from medical-school cohorts where Anki adoption is unusually high (board-exam culture) and from undergraduate populations where adoption is unusually low (no equivalent driver).

- How much does FSRS efficiency convert into learning gains? The 20-30% review-time savings is documented. Whether the saved time gets reallocated to other learning activities or whether the student just spends less time on retention practice is not measured. The honest claim is *efficiency*; the gain in *learning* depends on what the student does with the freed time.

- What happens when students generate their own cards in addition to faculty-curated cards? Some evidence (Karpicke and Roediger 2008) that the act of generating a card is itself a retrieval-practice event; mixing student-generated with faculty-curated may produce additive gains. The curriculum-design implications are not well-worked-out.

- Cross-cultural generalization. Most spaced-repetition research has been in WEIRD samples. Whether the testing effect's mechanism is universal (likely yes, given the neurobiological argument) or whether the optimal scheduling parameters vary with cultural factors (possibly) is open.

---

## AI Wayback marginal callout — Piotr Woźniak

> *Piotr Woźniak, a Polish biology student studying English vocabulary in the early 1980s, decided he wanted to know exactly how long to wait between reviewing flashcards. He started running experiments on his own retention. By 1985 he had built SuperMemo, software that implemented his self-experimental findings as a scheduling algorithm — the original SM-2. He published the algorithm openly. He continued running experiments on himself for decades. The mainstream cognitive psychology literature on the spacing effect was developing in parallel, but Woźniak was operating ahead of it on the practical questions: how to space, by how much, when to adjust, what to do when retrieval fails. SuperMemo influenced Anki, which influenced the broader flashcard-app ecosystem, which influenced FSRS, which Quiz Me runs today. The lineage runs through a Polish researcher who never sought academic credentials in the field, doing self-experimental work that anticipated the literature by decades. The aviation pedagogy principle and the academic testing-effect literature are the institutional and laboratory versions of what Woźniak discovered by paying attention to how he forgot English vocabulary. The lesson for institutional decision-makers: the best evidence on spaced retrieval predates the technology by 40 years. The technology is the implementation. The mechanism is older and more settled than the software.*

---

## Bridge to Chapter 5

Quiz Me makes factual and conceptual knowledge durable. It does the retention job, and it does it well, on the most replicated finding in cognitive psychology.

It does not teach students to use that knowledge when the situation is ambiguous and the right answer is not obvious — when a patient presents with multiple competing considerations, when the textbook's clean case becomes the bedside's messy one, when the student has to decide what to do next without the safety of a card-correct answer. That cognitive operation is the gap between *knowing* and *practicing*, and it is the gap the Carnegie Foundation documented in medical education in 2010 and engineering education in 2008. Quiz Me does not close it. Neither does Ask AI. The next chapter introduces the two modes Medhavy uses to close it — Case Study, and a mode most readers have never encountered called Glimmer.

---

*Sources cited in this chapter: Roediger, H. L., & Karpicke, J. D. (2006). Test-Enhanced Learning. Psychological Science, 17(3), 249–255. · Karpicke, J. D., & Blunt, J. R. (2011). Retrieval Practice Produces More Learning than Elaborative Studying with Concept Mapping. Science, 331(6018), 772–775. · Cepeda, N. J., Pashler, H., Vul, E., Wixted, J. T., & Rohrer, D. (2006). Distributed practice in verbal recall tasks. Psychological Bulletin, 132(3), 354–380. · Dunlosky, J., Rawson, K. A., Marsh, E. J., Nathan, M. J., & Willingham, D. T. (2013). Improving Students' Learning With Effective Learning Techniques. Psychological Science in the Public Interest, 14(1), 4–58. · Bjork, R. A. (1994). Memory and metamemory considerations in the training of human beings. · Bahrick, H. P. (1984). Fifty years of memory for Spanish learned in school. JEP: General, 113(1), 1–29. · Rohrer, D., & Taylor, K. (2007). The shuffling of mathematics problems improves learning. Instructional Science. · Woźniak, P. (1990). SM-2 algorithm. SuperMemo documentation. · Ye, J., et al. (2022–present). FSRS — Free Spaced Repetition Scheduler. github.com/open-spaced-repetition/fsrs4anki. · Federal Aviation Administration. Aviation Instructor's Handbook, FAA-H-8083-9.*
