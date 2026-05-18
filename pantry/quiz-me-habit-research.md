# Research Note — Quiz Me as Fitness Tracker for Memory: The Habit Loop That Makes the Algorithm Useful

*Working pantry document for the Medhavy book project. The companion piece to `quiz-me-research.md` (which covers FSRS, SM-2, retrieval-practice mechanism, spacing principle, prerequisite chaining). This note covers the question the algorithm side cannot answer: why students actually use Anki. The author's working frame — **Anki is not just spaced repetition; it is a fitness tracker for memory** — is examined against the habit-design, gamification, and medical-education adoption literatures.*

*Compiled 2026-05-17. Maintained for revision.*

---

## Preliminary: the question this note refuses to dodge

The companion note (`quiz-me-research.md`) makes the case that retrieval practice, spacing, and scheduling-algorithm sophistication are three distinct claims with three distinct evidence bases. The strongest of the three — by far — is retrieval practice. Adesope, Trevisan & Sundararajan 2017 puts the pooled effect of practice tests vs. re-studying at g = 0.51. The spacing principle (Cepeda et al. 2006) adds further gains. The scheduling-algorithm contribution — FSRS over SM-2, MCM over heuristic intervals — sits on simulation evidence with no published RCT comparing learning outcomes between schedulers on the same content.

If the algorithm is the smallest contributor, what is doing the rest of the work?

The hypothesis this note tests has two halves:

1. **Most of Anki's learning benefit comes from retrieval practice with crude spacing, not from scheduler sophistication.** A Leitner box plus daily use would produce most of the same outcomes. The marginal contribution of FSRS over SM-2 over Leitner is real but small relative to the underlying mechanism.
2. **Most of Anki's *adoption* — the reason it is used at all, daily, voluntarily, by hundreds of thousands of medical students — comes from habit-loop design, not algorithm quality.** The daily due-count, the completion mechanic, the streak, the shared-deck community, and the mobile-friendly review session do most of the work.

Both halves matter for Medhavy's Quiz Me. The first determines what the algorithm has to be (good enough, not necessarily state-of-the-art). The second determines what the interface has to be (a habit-forming surface, not a study-tool screen).

Throughout this note, every claim is tagged:

- `[retrieval-practice]` — the learning mechanism.
- `[spacing]` — the scheduling principle.
- `[scheduling-algorithm]` — implementation (FSRS, SM-2, HLR, MCM).
- `[habit-design]` — behavior design, Fogg, Eyal, habit-formation research.
- `[gamification]` — game-design elements in learning systems.
- `[medical-application]` — medical-education usage and outcomes.
- `[failure-mode]` — abandonment, gaming, fluency traps.
- `[foundational-theory]` — Skinner, Zeigarnik, Bjork, etc.
- `[vendor]` — Anki, Duolingo, Quizlet self-reported metrics.

---

## 1. Effectiveness: what does the algorithm contribute beyond retrieval practice?

### 1.1 The decomposition problem

The framing in most practitioner literature collapses retrieval practice, spacing, and the algorithm into one phrase — "spaced repetition" — and reports effect sizes for the bundle. But these can be unbundled, and the unbundling is uncomfortable for vendors of scheduling algorithms.

**Retrieval practice without spacing.** Roediger & Karpicke 2006 `[retrieval-practice]` is the canonical case. Students studied science prose, then either re-read or took practice tests within a single laboratory session. At one week, STTT (study + three tests) produced 61% recall vs. 40% for SSSS (four study periods). The effect appeared *without any spaced scheduling at all*. The tests were close in time. The mechanism is the act of retrieval, not the interval between retrievals. ([Roediger & Karpicke 2006](https://journals.sagepub.com/doi/10.1111/j.1467-9280.2006.01693.x))

This is the empirical core of the unbundling argument. A student who picks up a stack of paper flashcards, shuffles them, and tests themselves until they get them right has accessed the largest of the three effects. No algorithm has been invoked. No interval has been computed. The Adesope 2017 g = 0.51 over re-studying applies. `[retrieval-practice]`

**Retrieval practice with crude spacing.** The Leitner box (Sebastian Leitner, *So lernt man lernen*, 1972) is the analog ancestor of every digital spaced-repetition system. Five boxes, manual moves: a card you got right moves to the next box; a card you got wrong returns to the first box; boxes are reviewed at successively longer intervals (1 day, 3 days, 7 days, 14 days, 30 days, roughly). The intervals are fixed, the model is heuristic, and the algorithm is "if right, advance; if wrong, retreat." There is no published RCT comparing Leitner vs. SM-2 vs. FSRS on learning outcomes. There are no head-to-head learning-outcome trials in the literature at all `[verify thoroughness of search]`.

**The Settles & Meeder 2016 result.** `[scheduling-algorithm]` `[vendor]` Duolingo's half-life regression model reduced error rate by **9.5%** over a Leitner baseline at production scale. ([Settles & Meeder 2016](https://aclanthology.org/P16-1174/)) This is the cleanest published number we have on the marginal value of a sophisticated scheduler over crude scheduling. 9.5% is real. It is also small compared to the g = 0.51 of retrieval practice over re-studying.

**The FSRS-team benchmark.** `[scheduling-algorithm]` `[vendor]` The Expertium / FSRS-team benchmark reports FSRS-5 hitting target retention with ±5.3% error vs. SM-2's ±16.2%, and producing approximately 20-30% fewer reviews for the same target retention. ([Expertium FSRS benchmark](https://expertium.github.io/Benchmark.html)) These are scheduling-efficiency claims, not learning-outcome claims. They predict review-burden reduction, not retention improvement at fixed review-burden. The honest reading: FSRS is better at predicting when a user will forget than SM-2 is. Whether that predictive accuracy translates to better learning outcomes when controlled for review effort is unestablished in the peer-reviewed literature.

### 1.2 What the absence of comparison RCTs implies

A search for "SM-2 vs FSRS learning outcomes RCT" returns zero hits on PubMed and ERIC `[verify with formal database search]`. A search for "scheduler comparison retention" within the broader spaced-repetition literature returns simulation benchmarks (predict-retention-from-logged-data) but not controlled learning-outcome experiments.

This absence is itself evidence. If the scheduler choice produced large differences in learning, the comparison would be straightforward to run and the results would be in the literature. The fact that the field has not produced this comparison — despite enormous user populations, identifiable cohorts, and Anki's data-export capabilities — suggests one of two things. Either no funder has thought it worth the effort, which is implausible given the dollars in EdTech. Or the people best positioned to estimate the effect (the scheduling-algorithm teams) suspect the answer would be small and unflattering to their primary claim.

This is the analytic gap the companion note flags. It is more important than the field admits.

### 1.3 The implication for Medhavy

If most of the learning benefit is retrieval practice, and crude spacing captures most of the marginal scheduling effect, then the Quiz Me algorithm only needs to be **good enough**, not state-of-the-art. A Leitner-style implementation with a few empirically chosen interval multipliers would capture perhaps 90% of the available learning effect for a fraction of the engineering cost.

The remaining 10% is real, and it scales with user volume — at 100,000 students, 10% better retention prediction means many fewer wasted reviews, which feeds back into adoption. But the marginal value is not where most of the design effort should sit. The design effort should sit in the part this note covers: the habit loop.

---

## 2. Where flashcards work, where they don't, and why this matters for Medhavy

### 2.1 The strong-effect domains

Flashcards work — voluntarily, at scale, with clear learning outcomes — in a small, identifiable cluster of domains.

**Medical education.** `[medical-application]` The cleanest case. Anki adoption among U.S. medical students is reported to be 70–80% of M1 cohorts at some institutions, and the AnKing deck is functionally a parallel curriculum used by 100,000+ medical students `[verify exact figures]`. ([Lu, Farhat & Beck Dallaghan 2021, *Medical Science Educator*](https://pubmed.ncbi.nlm.nih.gov/37546209/) `[verify]`) The mature-card metric in their cohort study explained roughly a third of the variance in exam performance.

**Language vocabulary.** `[retrieval-practice]` Vocabulary is the prototypical Anki domain. Paul Nation's *Learning Vocabulary in Another Language* (2nd ed., Cambridge, 2013) is the standard reference; Norbert Schmitt's *Vocabulary in Language Teaching* (Cambridge, 2000) the pedagogical synthesis. Vocabulary learning is the cleanest paired-associates task: one cue (the word), one response (the meaning), atomic, discrete, decontextualized. Spaced retrieval practice is empirically dominant for this task class.

**Bar exam preparation.** `[medical-application]` (extension to professional licensure) The Bar/Bri and Themis flashcard offerings, plus open-source decks, are well-attested anecdotally — though formal effect-size studies are scarce.

**Anatomical / taxonomic facts.** Bone names, drug classes, ICD codes, plant species. Same structure as vocabulary: atomic items, discrete answers, large enumerable set.

### 2.2 The weak or null domains

**Mathematics.** Flashcards don't teach calculus. They don't teach proof construction. They can teach the multiplication tables and the names of theorems. The procedural skill — knowing when and how to apply a theorem — does not reduce to a card.

**Programming.** Flashcards can teach syntax. They cannot teach how to design a function. The Karpicke transfer literature (Pan & Rickard 2018, d = 0.40 to inference items) suggests there is some carry-over, but it is small and concentrated in items with response overlap.

**Physics problem-solving.** Same shape. Flashcards can teach formulae. They do not teach when each formula applies, or how to construct the problem from the physical situation.

**Philosophy.** Flashcards can teach the names of arguments and the broad outlines of positions. They cannot teach argument evaluation, which is the actual cognitive work.

### 2.3 The ACT-R distinction: declarative vs. procedural

John Anderson's ACT-R framework `[foundational-theory]` (Anderson 1983, *The Architecture of Cognition*; Anderson et al. 2004, "An integrated theory of the mind," *Psychological Review* 111(4)) distinguishes **declarative knowledge** (facts, names, definitions, propositions — the *what*) from **procedural knowledge** (skills, productions, condition-action rules — the *how*). The two are stored differently, acquired differently, and tested differently.

Flashcards target declarative knowledge directly. The cue-response structure is a declarative retrieval. Procedural skill requires repeated execution under varied conditions, with feedback on the *process* of solving, not just the answer.

This is the structural reason the strong-effect domains are what they are. Medical school in the pre-clinical years is overwhelmingly declarative — drug names, mechanisms, pathways, presentations. Language vocabulary is paired declarative. Bar exam first-pass material is rules and definitions. The procedural application of these — diagnosing a patient, translating a text, arguing a case — is built on top of the declarative substrate, and flashcards build that substrate efficiently.

In the weak-effect domains, the declarative substrate is small relative to the procedural skill, so flashcards capture a smaller fraction of what the student actually needs.

### 2.4 Atomic recall vs. multi-step reasoning

Karpicke 2017 `[retrieval-practice]` ("Retrieval-based learning: A decade of progress," *Learning and Memory* `[verify exact citation]`) reviews what retrieval practice transfers to and what it doesn't. The cleanest transfer is to items in the same response set. Transfer to inference and application is real but smaller (Pan & Rickard's d = 0.40 vs. within-set d ≈ 0.7–1.0).

The boundary is between **atomic recall** ("what does this term mean?") and **multi-step reasoning** ("given this situation, what should you do?"). Retrieval practice on atomic items improves atomic recall reliably. It improves multi-step reasoning to the extent that the multi-step reasoning depends on having the atomic items available — which in clinical medicine is most of the time.

### 2.5 Conceptual material — McDermott, Roediger

**McDermott, Agarwal et al. 2014** `[retrieval-practice]` "Both multiple-choice and short-answer quizzes enhance later exam performance in middle and high school classes," *Journal of Experimental Psychology: Applied* 20(1), 3–21. Showed testing-effect gains for conceptual science content in classroom settings, with effect sizes similar to those for factual material. ([McDermott et al. 2014](https://psycnet.apa.org/record/2014-04875-001) `[verify exact pages]`)

The point: retrieval practice extends to conceptual material, but the effect size is closer to the lower end of the testing-effect range than to the d = 1.5 Karpicke & Blunt headline figure. For Medhavy's purposes — where the content is concept-heavy rather than pure fact-recall — the realistic Quiz Me effect size is somewhere in the g = 0.4 to g = 0.6 range against re-reading, not the laboratory ceiling.

### 2.6 The Medhavy match question

If Medhavy is going to be used primarily by medical students or in medically-adjacent declarative-heavy courses, Quiz Me sits at the strong-effect end of the spectrum. If Medhavy's content turns out to be mostly conceptual physics or argument-evaluation philosophy, Quiz Me will produce smaller effects and may not be the right primary mode.

The implication for the chapter: the Quiz Me discussion should be explicit about the domain conditions under which the strongest claims apply. A textbook that argues flashcards drive understanding without naming the procedural/declarative boundary is overclaiming.

---

## 3. The habit loop — why Anki actually works

This is the section that the author's framing — *fitness tracker for memory* — points at. The argument is that Anki's daily-use pattern is structurally identical to a fitness-tracking app's daily-use pattern, and the same behavior-design literature applies.

### 3.1 Fogg's behavior model (B = MAT)

**B.J. Fogg 2009** `[habit-design]` `[foundational-theory]` proposed that behavior occurs when **Motivation, Ability, and Trigger** converge at the same moment. ([Fogg 2009, "A behavior model for persuasive design," in *Persuasive '09*](https://dl.acm.org/doi/10.1145/1541948.1541999)) The implication for app design: a behavior that fails to occur is failing on at least one of the three. Either the user does not want to do it, or it is too hard at the moment, or there is no cue to do it now.

Applied to Anki:

- **Motivation.** The student wants to pass the exam, retain the material, finish today's reviews. Motivation is high in medical school by selection effect.
- **Ability.** A review session is low-friction. Open app, see card, swipe. No setup. No decision about what to study. The algorithm has chosen for the student. **The reduction of decision-cost is the most underrated feature of any spaced-repetition system.**
- **Trigger.** The badge on the app icon. The daily due-count notification. The fixed time-of-day pattern the student has built around it.

Anki gets all three. SuperMemo (the academic ancestor) had the algorithm and the motivation but failed on ability: the UI was hostile, mobile support was late, the learning curve was vertical. SuperMemo's user base never approached Anki's despite having the better-validated algorithm. This is the cleanest natural experiment we have on the question — same algorithm class, vastly different interface, vastly different adoption.

### 3.2 Eyal's Hooked framework

**Nir Eyal 2014** `[habit-design]` *Hooked: How to Build Habit-Forming Products*. Four-stage loop: **Trigger → Action → Variable Reward → Investment**. Each cycle deepens engagement and lowers the activation energy of the next cycle.

Applied to Anki:

- **Trigger.** External (notification, app icon badge) becomes internal (the felt itch when the student knows reviews are due). The internalization is the design goal.
- **Action.** The minimum behavior the user can do with the product. For Anki, opening the app and reviewing one card. The action must be possible in seconds. Anki on mobile achieves this; SuperMemo on desktop does not.
- **Variable Reward.** The unpredictability of which card comes next, of whether you remember it, of how the deck depletes. The variable reward schedule is the difference between checking your email (predictable, less compelling) and pulling a slot-machine lever (variable, addictive). The due-count going from 47 to 46 to 45 is fixed-ratio; the contents of each card is variable.
- **Investment.** The cards the student has made themselves, the mature cards built up over months, the deck that represents the student's accumulated mastery. Investment is the switching cost. A medical student with 30,000 mature cards in Anki cannot move to a competitor without losing all of it.

The Eyal framework is descriptive of consumer-app design generally. It is descriptive of Anki specifically with almost no adaptation. This is not coincidence. Anki was not designed against the Hooked framework — it precedes it — but the affordances it produced match the framework in ways that account for its adoption pattern.

### 3.3 Wood's habit-formation research

**Wendy Wood 2019** `[habit-design]` *Good Habits, Bad Habits: The Science of Making Positive Changes That Stick* (Macmillan), synthesizing two decades of her USC habit-formation lab work. Three ingredients predict habit formation: **context cues + repetition + reward**. Cues are stable environmental features that signal the time/place for the behavior. Repetition is the behavior occurring frequently enough for the cue-behavior link to form. Reward is the affect or outcome that reinforces the link.

For Anki: the cue is often a time-of-day or location pattern (the medical student's morning coffee, the commute, the after-dinner hour). The repetition is daily by algorithmic design — there are always reviews due. The reward is the completion-affect plus the gradual reduction of the due-count.

**Lally, van Jaarsveld, Potts & Wardle 2010** `[habit-design]` "How are habits formed: Modelling habit formation in the real world," *European Journal of Social Psychology* 40(6), 998–1009. ([Lally et al. 2010](https://onlinelibrary.wiley.com/doi/10.1002/ejsp.674)) The frequently-misquoted "66 days to form a habit" figure. The actual finding: median time to automaticity in their sample of 96 participants was 66 days, with a *range* of 18 to 254 days. The 21-day figure that floats through productivity literature is a misreading of a 1960s plastic-surgery anecdote (Maxwell Maltz, *Psycho-Cybernetics*, 1960); the empirical estimate is much longer, much more variable, and depends heavily on the difficulty of the target behavior.

For Quiz Me design: a student who uses Quiz Me for three weeks and then stops has not formed a habit by the Lally criterion. The design needs to support not-yet-habitual use for two months or more before the behavior becomes self-sustaining. The streak mechanic is one of the design moves available for that interval.

### 3.4 The Zeigarnik effect — the due-count as a closure variable

**Bluma Zeigarnik 1927** `[foundational-theory]` "Über das Behalten von erledigten und unerledigten Handlungen," *Psychologische Forschung* 9, 1–85. The original demonstration: people remember unfinished tasks better than finished ones, and unfinished tasks demand cognitive attention until completed. The effect has been replicated repeatedly though with weaker effect sizes than Zeigarnik's original (see McKinney 1935; the modern review in Roediger & McDaniel, *Make It Stick*, 2014, ch. 4) `[verify modern review citation]`.

For Anki: **the "47 cards due today" counter is a Zeigarnik trigger.** It is an open task with a visible count. The brain wants to close it. The counter going to zero is the closure event. The variable that makes this work is the *visibility* of the count — if it were hidden, the closure pressure would vanish.

This is the single mechanical move that converts a study tool into a daily-use product. Quizlet has flashcards but no due-count; users return when they have a test next week, not daily. Anki has the due-count and users return daily. The algorithm does not cause the daily return — the *displayed open-task count* does.

The Medhavy implication: **the "due today" counter is load-bearing UI in any flashcard system that wants daily voluntary use.** Hiding it or making it secondary breaks the habit loop. Showing it everywhere — home screen, app icon, notification, header bar — keeps the loop alive.

### 3.5 Variable-ratio vs. fixed-ratio reward schedules

**Skinner 1957** `[foundational-theory]` *Schedules of Reinforcement* (with Charles Ferster). The four basic schedules: fixed-ratio, variable-ratio, fixed-interval, variable-interval. **Variable-ratio** produces the highest response rate and the strongest resistance to extinction. This is the schedule that drives slot machines, social-media feeds, and other notoriously habit-forming systems.

What is Anki's schedule?

- The **fact that a card is due** is fixed-interval-ish (within the deck, the algorithm schedules deterministically given the rating history).
- The **identity of the next card** in a session is variable.
- The **outcome of each card** (remembered or not) is variable.
- The **gradual reduction of the due-count** is a fixed-progression — each card decrements the counter by one.

The mixture is closer to variable-ratio than to pure fixed-interval. The user does not know which card comes next, does not know whether they'll get it right, does not know exactly when the session will end (some cards take a few seconds, some require thought). This unpredictability inside the session is what keeps the cognitive engagement high; the fixed depletion of the counter is what produces the closure sensation.

For Quiz Me: a deterministic ordering ("here are concept node 5's cards in order") removes the variability and weakens the habit loop. A shuffled / interleaved presentation preserves variability and aligns with the Rohrer interleaving literature (companion note, §3.3) at the same time.

### 3.6 Streak research and commitment devices

**Loewenstein 1996** `[habit-design]` "Out of control: Visceral influences on behavior," *Organizational Behavior and Human Decision Processes* 65(3), 272–292. Foundational work on commitment devices — voluntary self-binding to a future course of action. The streak is a self-imposed commitment device: the student has chosen to care about not breaking it.

**Duolingo's streak data.** `[vendor]` `[habit-design]` Duolingo's product team has published in blog and conference talks that users with active streaks have substantially higher daily-active retention than users without — the company has stated streak retention figures publicly though specific numbers vary across talks `[verify exact figures from Duolingo engineering blog or Settles' talks]`. The "streak freeze" feature was added explicitly because losing a long streak produced motivation collapse and elevated churn.

**Ericson & Lacasse 2007** `[habit-design]` `[verify]` and the broader self-control / commitment-device literature: visible streaks function as **loss-aversion levers**. The student is now defending an accumulated asset (the streak) rather than pursuing an abstract gain (better retention in three months). Loss aversion is roughly twice as motivating as equivalent gain (Kahneman & Tversky 1979, *Econometrica* 47(2), 263–292). The streak converts the long-term gain frame into a short-term loss-avoidance frame, which is empirically more motivating.

The cost: the streak corrupts the learning signal in the way the brief mentions. A student who reviews five trivial cards at 11:55 PM to preserve a streak has performed a streak-defense ritual, not a learning episode. Whether that ritual still produces meaningful retrieval practice depends on the cards reviewed.

**The Duolingo streak-freeze trade-off.** `[vendor]` `[habit-design]` The streak-freeze (a one-day pass that protects the streak) softens the all-or-nothing trap and reduces churn after missed days. But it also weakens the commitment device — the streak now signals "mostly daily" rather than "literally daily." Duolingo's product reports describe this as a deliberate trade.

### 3.7 Surviving SR systems vs. dead ones — the interface autopsy

**Survivors:** Anki (free, open-source, ugly but functional, mobile + desktop, shared deck ecosystem), Duolingo (gamified language vocabulary, mobile-first, freemium), Quizlet (school-market, social, freemium), RemNote (notes + cards, knowledge worker market). Each occupies a different niche but shares the daily-due-count habit loop and low-friction review session.

**Dead or marginal:** SuperMemo (the algorithm originator — UI rejected at every modernization attempt, mobile support arrived late and stayed clunky); Mnemosyne (open-source SR, never reached Anki's adoption despite comparable algorithm); dozens of EdTech startups (Cerego, Memorang, Memrise's pivot away from pure SR, various flashcard apps that died in the 2014–2018 wave).

What did the survivors get right that the algorithm doesn't capture?

1. **Mobile-first review.** A review session has to fit a coffee queue. Anki's mobile app, Duolingo's app, Quizlet's app — all designed for thumb-driven five-minute sessions. SuperMemo's late mobile efforts never recovered the ground lost in 2010–2015.
2. **Low-friction card creation.** Anki's keyboard shortcut for adding cards, Quizlet's tab-separated paste, RemNote's `>>` inline syntax. The investment cost of adding cards has to be low or no deck ever gets built. (RemNote noticed this and made it nearly invisible.)
3. **Shared-deck ecosystems.** Anki's shared decks (AnKing, Zanki, Lightyear, Refold for languages) collapse the deck-construction cost for new users. A medical student does not build a 30,000-card deck — they download one. This is what Cerego and Memorang never achieved at scale.
4. **The due-count visible everywhere.** Anki's app icon badge, Duolingo's home-screen daily reminder, Quizlet's class-assignment counters.
5. **Variable session length.** Anki ends the session when the due-cards-for-today are done. Duolingo ends when the lesson goal is hit. SuperMemo on desktop never produced this clean session-completion mechanic; it always had more cards available, which broke the closure event.

The pattern: **interface decisions, not algorithm decisions, separate the survivors from the casualties.**

### 3.8 The gamification literature

**Hamari, Koivisto & Sarsa 2014** `[gamification]` "Does gamification work? — A literature review of empirical studies on gamification," *Proceedings of the 47th Hawaii International Conference on System Sciences*, 3025–3034. ([Hamari et al. 2014](https://ieeexplore.ieee.org/document/6758978)) Systematic review of 24 empirical studies of gamification across contexts. Most produced positive effects, but the review noted high context-dependence, frequent methodological weaknesses, and a tendency for gamification effects to fade over time. The headline: gamification works in the short run, less reliably in the long run.

**Sailer & Homner 2020** `[gamification]` "The Gamification of Learning: A Meta-Analysis," *Educational Psychology Review* 32, 77–112. ([Sailer & Homner 2020](https://link.springer.com/article/10.1007/s10648-019-09498-w)) Meta-analysis of 38 studies (39 effect sizes). Found small-to-moderate effects of gamification on cognitive (g = 0.49), motivational (g = 0.36), and behavioral (g = 0.25) learning outcomes. The cognitive effect was strongest when game elements were paired with retrieval-practice mechanics — i.e., gamification on top of testing rather than gamification as a substitute for testing.

The honest reading for Medhavy: **gamification adds, but it does not substitute.** The g = 0.49 cognitive effect sits on top of an already-validated learning mechanism (retrieval practice). The g = 0.25 behavioral effect (more time on task, more sessions) is the adoption mechanism — what gets the student to do the reviews at all. Quiz Me should aim for both. The gamification layer captures the behavioral effect; the retrieval-practice mechanism captures the cognitive effect.

**Koivisto & Hamari 2019** `[gamification]` "The rise of motivational information systems: A review of gamification research," *International Journal of Information Management* 45, 191–210. Reviewing the field at scale, the authors note that gamification's effects are **strongest for the early phase of use** (initial engagement) and **weakest for sustained behavior change**. The novelty wears off. This matches Wood's habit-formation research: gamification can carry a user through the period before context cues become automatic, but it cannot substitute for the habit itself once formed.

This is the most important caveat for Medhavy's design. If Quiz Me leans heavily on game elements (points, badges, leaderboards) without anchoring them to a habit-loop architecture that survives the novelty period, the adoption curve will collapse around month 2–3, exactly when Wood/Lally predict habit formation should be stabilizing.

---

## 4. The medical student case — why Anki achieves voluntary adoption

### 4.1 The adoption phenomenon

Across U.S. medical schools, Anki adoption is reported at 70–80% of pre-clinical cohorts at institutions where surveys have been conducted `[verify exact figures]`. ([Deng, Gluckstein & Larsen 2015, "Student-directed retrieval practice is a predictor of medical licensing examination performance," *Perspectives on Medical Education* 4(6), 308–313](https://pubmed.ncbi.nlm.nih.gov/26498443/); [Lu, Farhat & Beck Dallaghan 2021](https://pubmed.ncbi.nlm.nih.gov/37546209/) `[verify]`)

For comparison: voluntary adoption of curriculum-recommended study tools is typically much lower. Adoption of a tool that requires daily use for months is rarer still. The medical-student Anki adoption rate is unusual, and the question of *why* is more useful for Medhavy than any algorithm-level claim.

### 4.2 The AnKing phenomenon

The AnKing deck — currently AnKing Step / AnKing Step 1 / AnKing Step 2, evolved from prior decks Zanki (created by "Zankidubey," 2017) and Brosencephalon (2014) — is a community-maintained Anki deck mapped to the standard pre-clinical resources: First Aid, Boards & Beyond video lectures, Pathoma, Sketchy, UWorld. ([AnKing project](https://www.ankingmed.com/) `[vendor]`) It contains roughly 30,000 cards across the basic sciences and clinical step preparation, maintained by volunteer editors who tag new cards to new editions of the source materials.

The mechanism of AnKing's dominance: **it collapsed the activation energy of becoming an Anki user.** Before AnKing, a medical student who wanted to use Anki had to build their own deck, which is a deck-construction task of hundreds of hours over a semester. After AnKing, the activation cost dropped to "download deck, install add-on, start reviewing." The same algorithm became dramatically more accessible.

This is the same pattern the survivors-vs-dead-systems analysis surfaces: **community shared content collapses the investment cost**. RemNote has tried to replicate this with shared knowledge bases; Quizlet has class-based deck sharing; Duolingo provides the deck (the language curriculum) and bypasses the deck-construction problem entirely.

### 4.3 The Step 1 score correlation

**Lu et al. 2021** `[medical-application]` (cited above) `[verify]` — single-cohort study at one institution. Mature Anki cards predicted course exam performance, explaining roughly a third of variance in their model.

**Deng, Gluckstein & Larsen 2015** `[medical-application]` *Perspectives on Medical Education*. Survey study, not RCT. Found that self-directed use of retrieval-practice tools (including Anki, but also question banks like UWorld) correlated with USMLE Step 1 score. Reported the association but did not establish causation. ([Deng et al. 2015](https://pubmed.ncbi.nlm.nih.gov/26498443/))

**The selection-effects problem.** Students who use Anki extensively are likely also students with stronger study habits, better impulse control, and clearer goal orientation. The Anki-score correlation includes a non-trivial selection component. The honest reading: Anki use predicts Step 1 score; whether Anki use *causes* a higher Step 1 score (vs. being a marker of the kind of student who scores well) requires the RCT that has not been done.

A pragmatic note: even with the selection-effects caveat, the pattern is striking enough that medical schools are reorganizing around it. Pre-clinical curricula are increasingly built to be Anki-compatible. This is itself the strongest evidence we have that the practice works — not in the laboratory sense, but in the revealed-preferences sense at the level of institutional behavior.

### 4.4 The COVID effect

COVID-19 forced medical school online in 2020–2021 and broke the in-person small-group study patterns that had previously absorbed much of the pre-clinical learning workload `[verify with medical education literature on COVID impact]`. The Anki adoption rate jumped during this period as students looked for self-directed asynchronous study tools that didn't require synchronous peer presence. Some institutions report Anki adoption above 85% in the post-2020 cohorts `[verify]`. The COVID natural experiment effectively confirmed that Anki's structural strengths (asynchronous, self-paced, no instructor needed, mobile, community decks available) were exactly what students reach for when other modes are removed.

### 4.5 What is the adoption mechanism?

The four candidate mechanisms:

1. **Algorithm quality.** FSRS / SM-2 produces good schedules. Students notice.
2. **Shared community decks.** Activation energy drops; deck-construction cost disappears.
3. **Daily-due-count habit.** The closure mechanic produces daily voluntary return.
4. **Peer-effect contagion.** Everyone in the cohort uses it, so the cost of *not* using it (informational isolation) exceeds the cost of using it.

The strongest hypothesis from the available evidence: **3 and 4 are doing most of the work, 2 is a necessary precondition, and 1 is a marginal contributor.** A medical student does not adopt Anki because they read a paper on FSRS — they adopt because their roommate uses it, the AnKing deck exists, the app shows them how many cards are due today, and the daily review session becomes part of their morning routine. The algorithm matters in the sense that bad algorithms would discredit the tool, but the adoption mechanism is social-cognitive, not algorithmic.

### 4.6 "Survival infrastructure" framing

There is a stronger version of the adoption story worth naming. When a study tool becomes *load-bearing* for a high-stakes credentialing exam — when not using it means falling visibly behind cohort peers and risking the exam outcome — the habit loop becomes self-sustaining for reasons that have nothing to do with pedagogy. The student is not maintaining their Anki streak because they love retrieval practice. They are maintaining it because falling off the streak now means losing infrastructure they have built their whole study system around, and rebuilding it is more expensive than continuing.

This is the strongest equilibrium in the medical-student Anki system. It is unstable in two directions: **(a)** if AnKing-style shared decks are not available for the domain, the equilibrium does not form (this is why Anki is not as dominant in physics graduate school, despite physics graduate students being roughly as motivated and capable as medical students); **(b)** if the high-stakes exam disappears (post-Step-1-pass-fail-change in 2022, the role of Step 2 became more prominent, and Anki use shifted toward Step 2 content) the equilibrium reorganizes around the new high-stakes target `[verify Step 1 pass/fail change effect on Anki adoption]`.

For Medhavy: the high-stakes-exam infrastructure framing is the most useful adoption analog. Medhavy is unlikely to be the load-bearing infrastructure for a board exam in the way AnKing is. So the habit loop has to work on weaker foundations — interest, course requirements, peer effects within a class. The interface has to compensate for the absence of an external survival pressure.

---

## 5. The minimum viable flashcard

### 5.1 What's actually necessary?

If most of the learning comes from retrieval practice with crude spacing, and most of the adoption comes from the habit loop, the minimum viable flashcard system is much simpler than FSRS-on-Anki.

**Necessary features:**

1. Cards: cue side, answer side. The student attempts retrieval, then reveals the answer, then self-rates.
2. A scheduler: any of {Leitner box, SM-2, FSRS}. Differences in learning outcomes between these are likely small.
3. A daily session with a finite due-count and a clear "you're done for today" endpoint.
4. Mobile access. Reviews need to happen in moments of available cognitive bandwidth, not at a desk.
5. Low-friction card addition (or pre-built decks for the domain).
6. A visible due-count somewhere persistent (app icon badge, header element, lock-screen widget).

**Helpful but not necessary:**

- Sophisticated FSRS scheduling vs. SM-2 vs. Leitner.
- Detailed analytics dashboards.
- Card-type variety beyond basic, cloze, and image-occlusion.
- Social features (leaderboards, friend lists).
- Decorative animations and visual polish.

**Hindering features:**

- Long required onboarding before first review.
- Required deck construction before any review is possible.
- Hidden due-count.
- Mandatory daily session length beyond what fits a coffee queue.
- Anything that makes the session feel like a quiz with stakes rather than a review with closure.

### 5.2 What *Make It Stick* argues is sufficient

**Brown, Roediger & McDaniel 2014** `[retrieval-practice]` *Make It Stick: The Science of Successful Learning* (Harvard). The synthesis volume that is the standard reference for practitioners trying to implement retrieval practice with minimum technology overhead. ([Brown, Roediger & McDaniel 2014](https://www.hup.harvard.edu/catalog.php?isbn=9780674729018)) Their argument: retrieval practice, spacing, and interleaving can be achieved with index cards, a notebook, and discipline. The technology adds convenience, not mechanism.

The implication for Medhavy: **the technology is doing work to lower the cost of practice, not to produce learning the practice could not produce on its own.** A textbook Quiz Me mode that achieves 60% of Anki's lift through a simpler interface and lower friction is a successful product. The point is not to win an algorithm-comparison benchmark; the point is to make daily voluntary retrieval practice happen.

### 5.3 The MVP composition

For Medhavy specifically, the minimum viable Quiz Me looks like:

- **Items** auto-generated from the concept node map, with prior-error context per student (this is the per-learner item selection the chapter already promises).
- **Scheduling** via any defensible spaced algorithm — FSRS is a reasonable default, but a Leitner variant would capture most of the same effect.
- **Daily due-count** shown on the home screen of the textbook reader, on the chapter view, and on the app icon if mobile.
- **Session completion** clearly marked: "You're done for today. Next reviews tomorrow."
- **Streak tracking** as opt-in, not default. (Reasons in §6 and §7.)
- **Card creation** kept low-friction or hidden — the concept-map auto-generation should mean the student never has to write a card themselves.

This composition gives Medhavy a Quiz Me mode that does the learning work that's actually validated, with the habit-loop architecture that's actually responsible for adoption, while keeping the algorithm sophistication at a level the evidence supports.

---

## 6. Design implications for Medhavy's Quiz Me

### 6.1 Quiz register vs. review register

A "quiz" and a "flashcard session" are different UX languages even though they share underlying mechanics.

A **quiz** has:
- A defined start and end ("Quiz 3 of Chapter 4").
- A score at the end.
- An assessment frame (the student is being measured).
- Higher stakes-feel; lower frequency of use.

A **flashcard session** has:
- A daily due-count, not a fixed-length quiz.
- A completion event (count → 0), not a score.
- A review frame (the student is maintaining knowledge).
- Lower stakes-feel; higher frequency of use.

The brief asks whether Medhavy's Quiz Me should feel like one or the other. The habit-loop evidence is decisive: **the review register produces daily voluntary use; the quiz register does not.** Quizlet's "Learn" mode (review-register) gets more daily use than its "Test" mode (quiz-register) by orders of magnitude. Anki has no quiz-register at all.

The implication: even though the mode is called *Quiz Me*, the interface should be **flashcard-register**, not quiz-register. No scores at the end of a session. No "Quiz 3 of Chapter 4" framing. The due-count, the swipe-through review, the completion event. The name is a misnomer for what the mode should feel like — this is worth flagging to the design team.

### 6.2 Feedback timing

**Bjork & Bjork** on feedback timing in retrieval practice: immediate feedback produces best in-session performance; delayed feedback produces best long-term retention. (See companion note §4 on performance-vs-learning.) For Quiz Me, the recommendation is to default to **immediate feedback after self-rating** (i.e., the student answers, then sees the correct answer with explanation, then rates their recall). This matches Anki's model and is the well-trodden path.

**Pashler, Cepeda, Wixted & Rohrer 2005** `[retrieval-practice]` "When does feedback facilitate learning of words?" *JEP: Learning, Memory, and Cognition* 31(1), 3–8. Found that feedback after a delay can be as effective or more effective than immediate feedback for some materials, but the practical cost of delayed feedback in a flashcard system (extra cognitive overhead, broken flow) outweighs the marginal benefit. `[verify exact cite]`

### 6.3 Session length

**Ericsson, Krampe & Tesch-Römer 1993** `[foundational-theory]` "The role of deliberate practice in the acquisition of expert performance," *Psychological Review* 100(3), 363–406. Estimated that productive deliberate-practice sessions for expert development run roughly 60–90 minutes before cognitive fatigue degrades practice quality.

For voluntary daily use, the relevant ceiling is much lower. Mobile-learning literature consistently finds that **5–10 minutes is the maximum session length most users will reliably complete daily**. Duolingo's daily-lesson target sits in this range. Anki's median session length per user `[verify Anki vendor data]` is reported similarly. Sessions longer than ~15 minutes show steep drop-off rates in completion.

The implication for Quiz Me: **design the default daily review to complete in 5–10 minutes for a student who is up-to-date.** This means tuning the algorithm's target-retention rate to produce that review burden, not letting reviews accumulate. If a student falls behind and the due-count balloons, the system should offer a backlog-management option (subset review, mature-card priority) rather than presenting a 60-minute session that will be abandoned.

### 6.4 The streak decision

This is the design question the brief asks most pointedly. Should Quiz Me have streaks?

The arguments for streaks: loss-aversion converts long-term gains into short-term loss-avoidance; Duolingo's user retention data is compelling; the commitment-device literature supports them.

The arguments against streaks: they corrupt the learning signal (the student reviews trivial cards at 11:55 PM to defend the streak); they produce all-or-nothing motivation collapse when broken; they reward consistency over comprehension.

**The defensible synthesis:** streaks work for adoption — getting the student through the 18-to-254-day habit-formation window — but they should be designed to **minimize the all-or-nothing trap**. Specific design moves:

1. **Opt-in, not default.** Make the student turn on the streak. This filters for students who want the commitment device and excludes students for whom it would be counter-productive.
2. **Streak-freeze available** (the Duolingo move). One missed day per week or per month doesn't end the streak. This softens the cliff.
3. **Streak measured in review-quality terms** where possible. A streak that requires reviewing N cards is worse than a streak that requires reviewing the cards FSRS scheduled for that day. The latter aligns the streak with the learning signal rather than against it.
4. **Streaks visible but not prominent.** The due-count is the primary closure variable; the streak is a secondary commitment device. Make the streak available to students who want it without making it the dominant UI element.

The principle: the streak is a scaffold for habit formation. It should be removable without breaking the rest of the system. A Quiz Me that requires the streak to be motivating is a Quiz Me that has not actually built a habit — it has built a streak-defense ritual.

### 6.5 The "due today" counter as load-bearing UI

From the Zeigarnik analysis (§3.4): **the due-count is the single most important UI element in any flashcard system that wants daily voluntary use.** It is the closure variable that produces the daily return. It is the cognitive itch that drives the habit loop.

Design implications:

- The due-count should be visible in at least three places: the chapter view of the textbook, a top-level navigation badge, and the app icon (if mobile).
- The count should be accurate (not "many" or "lots" — the specific number is what creates the closure pressure).
- Going to zero should be a distinct, visible event with a small visual reward (not gamified excess — a confirmation that the session is complete and tomorrow's reviews aren't due yet).
- The count should reset cleanly at a fixed time each day (most spaced-repetition systems use 4 AM local time as the rollover, which is a thoughtful choice — it avoids penalizing late-night studying while still producing a fresh daily count by morning).

### 6.6 Habit transfer across modes

The brief's final design question: if Quiz Me builds the daily habit, can the habit anchor Ask AI / Case Study / Glimmer engagement, or do those modes need their own habit loops?

**Habit transfer is empirically weak.** Wood's research on habit formation finds that habits are tightly bound to their context cues and rewards. A student who has formed a daily-Quiz-Me habit has not thereby formed a daily-Ask-AI habit. The cues are different, the rewards are different, the action is different.

But **the habit can serve as a launching cue for adjacent behaviors** if the system is designed to leverage it. The pattern is: the student opens the app for Quiz Me reviews → the system offers a contextually-relevant next mode at the end of the review session ("You missed 3 cards on Krebs cycle. Want a 5-minute Ask AI session on the missed concepts?") → the student accepts more often than if the offer came in isolation.

This is the bandit's job in Medhavy 2.0 (companion note §6.3). The bandit's value is not in choosing modes randomly; it is in piggy-backing adjacent-mode offers onto the established habit loop. The Quiz Me habit becomes the daily entry point; the bandit decides what to offer at the exit.

The implication: **Quiz Me should be designed not just as a learning mode but as the daily-entry-point mode.** The habit loop it builds is shared infrastructure for the rest of Medhavy's modes, not a standalone feature.

---

## 7. Failure modes — when spaced-repetition tools collapse

### 7.1 Motivation collapse after a missed streak

The all-or-nothing trap. The student misses a day, the streak breaks, the loss-aversion motivation reverses sign — what was driving daily use now drives abandonment. The streak-freeze mitigation (§6.4) is the standard fix. The deeper fix is to ensure the streak is not the only motivation driver; the due-count closure should remain motivating even when the streak is gone.

### 7.2 Card backlog overwhelm

When "due today" hits 800 because the student missed two weeks. This is a known failure mode in the Anki community; the standard recovery is to lower the target-retention temporarily, which reduces the daily due-count and lets the student work through the backlog without the queue growing. Quiz Me should detect backlog-overwhelm conditions algorithmically and offer the recovery path proactively rather than letting the student face a one-hour review session and abandon.

### 7.3 The "press Easy on everything" cheat

Gaming the algorithm. The student rates every card "Easy" to clear the queue, which causes FSRS to expand intervals dramatically and reduce future due-counts at the cost of actual retention. The cards then fail at long intervals, and the student has effectively destroyed the learning signal while preserving the appearance of completion.

This is hard to prevent algorithmically — the system cannot distinguish "actually easy" from "rated Easy to cheat." Partial defenses: (a) include occasional confidence-check items where the algorithm knows the student's prior performance and can flag discrepancies; (b) surface a "your Easy ratings are higher than your accuracy suggests" signal periodically; (c) avoid making the daily due-count the only success metric, so there is less incentive to game it.

### 7.4 The fluency trap specific to flashcards

The student recognizes the cue and produces the response without actually understanding the response. Pattern-matching the front to the back. The card "What does AMPK do?" prompts "Activates catabolism, inhibits anabolism" but the student does not know what catabolism is. The card has been "learned" by the algorithm; the underlying knowledge has not.

This is the deepest pedagogical risk of flashcard systems and is largely outside the algorithm's view. The defense is at the card-design layer: cloze deletions that require understanding, multi-step items that decompose into prerequisites, application items that require transfer. The Karpicke transfer literature (companion note §1.3) shows that well-designed retrieval-practice items can transfer; poorly-designed items reinforce the fluency illusion.

For Medhavy: Quiz Me items auto-generated from the concept map should include multiple item types per concept node — recognition, recall, application — and should rotate so the student is not always practicing the easiest type.

### 7.5 The "I made the cards so I know them" illusion

**Karpicke 2009** `[retrieval-practice]` (cited in companion note §4.4) — students systematically misjudge what produces learning. Making cards feels productive; reviewing cards feels uncomfortable. Students prefer making cards. Making cards is largely a transcription activity. The learning happens during retrieval, not during card production.

For Medhavy: Quiz Me's auto-generation of items from the concept map sidesteps this failure mode entirely. The student doesn't make cards; the system does. This is a structural advantage Anki users have to overcome (the AnKing solution: download a deck someone else made) and Medhavy can have built-in.

### 7.6 Long-term abandonment patterns

When do students stop using Anki? The available evidence suggests two main patterns: **(a)** after the high-stakes exam window closes (post-Step-1 abandonment is common); **(b)** during semester transitions or breaks when the daily routine that anchored the habit dissolves and the streak resets.

The literature on adherence to spaced-repetition is thin. Searches for "spaced repetition abandonment adherence" and "Anki dropout study" return mostly anecdotal forum discussions, not peer-reviewed studies `[verify with formal database search]`. The closest analogs are app-engagement studies in the broader EdTech literature, which consistently find that the largest abandonment event is in the first two weeks, with a second drop-off at the first major routine disruption (vacation, exam week, illness).

The design move for Medhavy: **build the routine-recovery path into the system.** When the system detects a multi-day absence, the welcome-back experience should not be "here are 200 due cards" — it should be "let's start with 10 of the most important ones." The recovery experience is more important than the initial onboarding for long-term adherence.

### 7.7 The COVID-era spike and post-COVID return

The natural experiment of COVID adoption (§4.4) also produced a natural experiment in *de*-adoption. Students who adopted Anki under remote-learning conditions and then returned to in-person curricula often reported reduced use as in-person peer study returned. The implication: Anki use is partly substitutive for cohort study, and when cohort study is available, the substitution reverses partway. The habit is real but not invulnerable to environmental change.

For Medhavy: the design should not assume Quiz Me use is permanent once formed. The habit-loop architecture has to be re-engaging across environmental changes, which means the welcome-back path matters more than the first-time-user path over the long run.

---

## 8. The Medhavy planning docs — Quiz Me's design contract

The full reading of the planning docs and chapters is in the companion note (`quiz-me-research.md` §6). Briefly:

- `book.md`, `outline.md`, `architecture.md`, `chapters-spec.md` are mostly Tic TOC scaffolding templates with placeholder content.
- `chapters/01-what-is-medhavy.md` describes Quiz Me as: FSRS scheduling, items generated from the concept map, calibrated to per-student prior errors, one of four modes (Quiz Me / Ask AI / Case Study / Glimmer).
- `chapters/04-what-makes-this-different.md` adds: Quiz Me "activates retrieval pathways and consolidates storage — appropriate when the representation needs to become durable."
- `chapters/06-medhavy-conducting-ai.md` implies the bandit-based mode selection in Medhavy 2.0.

**The chapter's stated design contract is heavily algorithm-side.** It names FSRS, names per-student item calibration, names the concept-map source. It does not explicitly name the daily-due-count, the completion event, the streak decision, or any other habit-loop element.

The habit-loop architecture is implicit at best in the current chapter prose. This note's purpose is to surface the parts the chapter should make explicit before the design is implemented, because the habit loop will determine whether Quiz Me is used at all.

---

## 9. Consolidated references

*Chicago author-date. Tagged by primary evidence class. `[verify]` flags are claims that need primary-source confirmation before use in the chapter.*

Adesope, Olusola O., Dominic A. Trevisan, and Narayankripa Sundararajan. 2017. "Rethinking the Use of Tests: A Meta-Analysis of Practice Testing." *Review of Educational Research* 87 (3): 659–701. https://doi.org/10.3102/0034654316689306. `[retrieval-practice]`

Anderson, John R. 1983. *The Architecture of Cognition*. Cambridge, MA: Harvard University Press. `[foundational-theory]`

Anderson, John R., Daniel Bothell, Michael D. Byrne, Scott Douglass, Christian Lebiere, and Yulin Qin. 2004. "An Integrated Theory of the Mind." *Psychological Review* 111 (4): 1036–1060. `[foundational-theory]`

Brown, Peter C., Henry L. Roediger III, and Mark A. McDaniel. 2014. *Make It Stick: The Science of Successful Learning*. Cambridge, MA: Harvard University Press. `[retrieval-practice]`

Cepeda, Nicholas J., Harold Pashler, Edward Vul, John T. Wixted, and Doug Rohrer. 2006. "Distributed Practice in Verbal Recall Tasks: A Review and Quantitative Synthesis." *Psychological Bulletin* 132 (3): 354–380. https://doi.org/10.1037/0033-2909.132.3.354. `[spacing]`

Deng, Francis, Jeffrey A. Gluckstein, and Douglas P. Larsen. 2015. "Student-Directed Retrieval Practice Is a Predictor of Medical Licensing Examination Performance." *Perspectives on Medical Education* 4 (6): 308–313. https://doi.org/10.1007/s40037-015-0220-x. `[medical-application]`

Ericsson, K. Anders, Ralf Th. Krampe, and Clemens Tesch-Römer. 1993. "The Role of Deliberate Practice in the Acquisition of Expert Performance." *Psychological Review* 100 (3): 363–406. `[foundational-theory]`

Eyal, Nir. 2014. *Hooked: How to Build Habit-Forming Products*. New York: Portfolio. `[habit-design]`

Ferster, Charles B., and B. F. Skinner. 1957. *Schedules of Reinforcement*. New York: Appleton-Century-Crofts. `[foundational-theory]`

Fogg, B. J. 2009. "A Behavior Model for Persuasive Design." In *Proceedings of the 4th International Conference on Persuasive Technology*. New York: ACM. https://doi.org/10.1145/1541948.1541999. `[habit-design]` `[foundational-theory]`

Hamari, Juho, Jonna Koivisto, and Harri Sarsa. 2014. "Does Gamification Work? — A Literature Review of Empirical Studies on Gamification." In *Proceedings of the 47th Hawaii International Conference on System Sciences*, 3025–3034. https://doi.org/10.1109/HICSS.2014.377. `[gamification]`

Kahneman, Daniel, and Amos Tversky. 1979. "Prospect Theory: An Analysis of Decision under Risk." *Econometrica* 47 (2): 263–292. `[foundational-theory]`

Karpicke, Jeffrey D. 2009. "Metacognitive Control and Strategy Selection: Deciding to Practice Retrieval During Learning." *Journal of Experimental Psychology: General* 138 (4): 469–486. `[retrieval-practice]`

Karpicke, Jeffrey D. 2017. "Retrieval-Based Learning: A Decade of Progress." In *Learning and Memory: A Comprehensive Reference*, 2nd ed., edited by John H. Byrne. Oxford: Academic Press. `[retrieval-practice]` `[verify exact pagination]`

Koivisto, Jonna, and Juho Hamari. 2019. "The Rise of Motivational Information Systems: A Review of Gamification Research." *International Journal of Information Management* 45: 191–210. `[gamification]`

Lally, Phillippa, Cornelia H. M. van Jaarsveld, Henry W. W. Potts, and Jane Wardle. 2010. "How Are Habits Formed: Modelling Habit Formation in the Real World." *European Journal of Social Psychology* 40 (6): 998–1009. https://doi.org/10.1002/ejsp.674. `[habit-design]`

Leitner, Sebastian. 1972. *So lernt man lernen: Der Weg zum Erfolg*. Freiburg: Herder. `[scheduling-algorithm]` `[foundational-theory]`

Loewenstein, George. 1996. "Out of Control: Visceral Influences on Behavior." *Organizational Behavior and Human Decision Processes* 65 (3): 272–292. `[habit-design]`

Lu, Mengshi, Mohammed Farhat, and Gary L. Beck Dallaghan. 2021. "Effects of Anki Flashcards on Medical Education." *Medical Science Educator* `[verify exact vol/issue/pages and citation]`. https://pubmed.ncbi.nlm.nih.gov/37546209/. `[medical-application]`

Maltz, Maxwell. 1960. *Psycho-Cybernetics*. Englewood Cliffs, NJ: Prentice-Hall. `[foundational-theory]` (cited as source of misquoted "21 days to form a habit"; not a research source.)

McDermott, Kathleen B., Pooja K. Agarwal, Laura D'Antonio, Henry L. Roediger III, and Mark A. McDaniel. 2014. "Both Multiple-Choice and Short-Answer Quizzes Enhance Later Exam Performance in Middle and High School Classes." *Journal of Experimental Psychology: Applied* 20 (1): 3–21. `[retrieval-practice]` `[verify]`

Nation, I. S. P. 2013. *Learning Vocabulary in Another Language*. 2nd ed. Cambridge: Cambridge University Press. `[retrieval-practice]`

Pan, Steven C., and Timothy C. Rickard. 2018. "Transfer of Test-Enhanced Learning: Meta-Analytic Review and Synthesis." *Psychological Bulletin* 144 (7): 710–756. https://doi.org/10.1037/bul0000151. `[retrieval-practice]`

Pashler, Harold, Nicholas J. Cepeda, John T. Wixted, and Doug Rohrer. 2005. "When Does Feedback Facilitate Learning of Words?" *Journal of Experimental Psychology: Learning, Memory, and Cognition* 31 (1): 3–8. `[retrieval-practice]` `[verify]`

Roediger, Henry L., III, and Jeffrey D. Karpicke. 2006. "Test-Enhanced Learning: Taking Memory Tests Improves Long-Term Retention." *Psychological Science* 17 (3): 249–255. https://doi.org/10.1111/j.1467-9280.2006.01693.x. `[retrieval-practice]`

Sailer, Michael, and Lisa Homner. 2020. "The Gamification of Learning: A Meta-Analysis." *Educational Psychology Review* 32: 77–112. https://doi.org/10.1007/s10648-019-09498-w. `[gamification]`

Schmitt, Norbert. 2000. *Vocabulary in Language Teaching*. Cambridge: Cambridge University Press. `[retrieval-practice]`

Settles, Burr, and Brendan Meeder. 2016. "A Trainable Spaced Repetition Model for Language Learning." In *Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics*, 1848–1858. Berlin: ACL. https://aclanthology.org/P16-1174/. `[scheduling-algorithm]` `[vendor]`

Soderstrom, Nicholas C., and Robert A. Bjork. 2015. "Learning Versus Performance: An Integrative Review." *Perspectives on Psychological Science* 10 (2): 176–199. https://doi.org/10.1177/1745691615569000. `[foundational-theory]`

Wood, Wendy. 2019. *Good Habits, Bad Habits: The Science of Making Positive Changes That Stick*. New York: Farrar, Straus and Giroux. `[habit-design]`

Zeigarnik, Bluma. 1927. "Über das Behalten von erledigten und unerledigten Handlungen." *Psychologische Forschung* 9: 1–85. `[foundational-theory]`

**Vendor / community sources** (treated as evidence about deployed practice, not peer-reviewed research):

AnKing Medical Education Project. https://www.ankingmed.com/. `[vendor]` `[medical-application]`

Expertium FSRS Benchmark. https://expertium.github.io/Benchmark.html. `[vendor]` `[scheduling-algorithm]`

Open Spaced Repetition Project. https://open-spaced-repetition.github.io/. `[vendor]` `[scheduling-algorithm]`

Settles, Burr. Various Duolingo engineering talks and blog posts on streak retention and habit-formation in Duolingo. `[vendor]` `[habit-design]` `[verify exact citations from Duolingo blog]`

---

*End of research note. Compiled 2026-05-17. Companion to `quiz-me-research.md`. To be revised as the Quiz Me chapter takes shape.*
