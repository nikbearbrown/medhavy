# Chapter 10 — When Kindle Is Enough

**One-line capability:** The reader gets the complexity threshold test — three questions that determine whether their deployment warrants Medhavy, or whether AI+1 on Kindle is the complete answer.

---

## Opening

The most expensive mistake in educational technology is solving the wrong problem correctly. A deployment that does not need the loop, given the loop, has spent money on overhead and added complexity without adding learning value. This chapter is the discipline that says: not always, and here is how to know.

You will read this chapter from inside a book about Medhavy, written by people who built it. That is the reason this chapter exists. A book that always concluded "yes, adopt" would be vendor literature. The thesis on the cover — *AI+1 is a better textbook, but a better textbook is not always enough, and this book tells you exactly when it isn't* — only earns its credibility if there are real, named, specific deployments where the honest recommendation is don't buy. There are. Most of them, actually.

Start with a deployment that fails the test. A nursing fundamentals class of twenty-eight students. One instructor, two-decade veteran. She teaches three days a week, holds office hours twice, and by the second week knows every student's name, their work shift at the local hospital, and which two are at risk of falling behind because of childcare. She uses an AI+1 pharmacology Kindle [Humanitarians AI internal framework] as her primary text, Anki for drug recall, Canvas for assignments. Her weekly quiz review is where she sees, in real time, which concepts the cohort has missed; her office hours are where she catches the students whose error patterns worry her.

She has a Medhavy proposal on her desk. Twelve thousand dollars a year per section. The proposal promises adaptive presentation, per-student measurement, and a dashboard that surfaces which students are struggling with which concepts.

She already has that dashboard. It is in her head. Twenty-eight students, one instructor, weekly contact, name-recognition by week two. The dashboard is staffed. Adding Medhavy here would not give her something she does not have. It would give her a second, slower, more expensive copy of what she has.

She should not buy Medhavy. And that recommendation is not a hedge. It is the right answer.

---

## Core content

### Block 1 — The three questions, stated cleanly

Earlier chapters built the loop [Humanitarians AI internal framework]: present differently, measure whether it helped, adapt, repeat. The four modes (Ask AI, Quiz Me, Case Study, Glimmer) [Humanitarians AI internal framework] are how Medhavy presents differently. The seven signals [Humanitarians AI internal framework] are how it measures. The contextual bandit is how it adapts. All of that machinery costs something — license fee, faculty time, institutional review, curricular labor — and the cost is the same whether the deployment needs the machinery or not.

The complexity threshold test is three questions. If the answers are not all yes, the machinery costs more than it returns.

> **The three questions**
>
> **Q1. Does the deployment need to present content differently to different learners, at scale?**
> "At scale" means more learners than any individual instructor can hold in working memory. The threshold is heuristic, not magic — somewhere between sixty students under one instructor and a hundred and twenty across multiple sections is where in-head adaptation typically stops being feasible. Smaller than that, and a thoughtful instructor is already doing what the loop would do.
>
> **Q2. Does someone need to know whether the variation is helping — not just whether students are engaged?**
> Canvas tells you who showed up. Medhavy tells you who learned. These are different questions. The second one only matters if someone — an instructor, a curriculum committee, an accreditation officer — actually needs the answer. If nobody is going to look, nobody needs to measure.
>
> **Q3. Is the institution willing to act on what the measurement reveals?**
> This is the hardest question, and the one most often answered yes too quickly. Measurement without willingness to change is expensive sentiment. The loop is not "look at the dashboard." The loop is "look at the dashboard and redesign the section that the dashboard says is failing." If that redesign step has no owner, the loop has no closing edge.

The questions are listed in this order because they fail in this order. Most deployments that should not adopt Medhavy fail Q1. Many that pass Q1 fail Q3. Q2 is rarely the binding constraint — once you have scale and willingness, the wanting-to-know follows.

---

### Block 2 — When all three are no: the nursing class

The nursing fundamentals class from the opening fails Q1 cleanly. Twenty-eight students, one instructor, two contact hours per student per week. The instructor's working memory holds the whole cohort. She does not need a system to tell her that Alicia is missing the loading-dose concept because Alicia told her so on Tuesday, and the system would not tell her about the childcare situation that is causing the missing — which is the actual variable.

It fails Q2 as well. The instructor already knows whether her variation is helping. She varies — Socratic on Mondays, problem-first on Wednesdays, drills on Fridays — and she knows what worked because she sees the same students three times a week. She does not need a measurement layer to confirm what office hours confirm.

And it fails Q3 implicitly. Even if she had a dashboard, who would act on it? She is the instructor. She is the curriculum committee. She is the accreditation contact. She would act on her own data, which is fine, but she already acts on her own observations, which she trusts more.

This is not a deployment that is *almost* ready for the loop. It is a deployment where the loop is the wrong shape entirely. The simpler stack — AI+1 on Kindle, Anki, Canvas, an attentive instructor — is not a compromise. It is the architecturally correct answer.

The AI+1 stack here is doing what edtech researchers have spent four decades documenting that most educational technology never does: it stays out of the way of the human relationship that produces the learning. Larry Cuban, the Stanford historian who watched personal computers arrive in K-12 classrooms in the 1980s, called this the "high access, low use" pattern: institutions buy the technology, teachers use it for whatever is most administratively convenient, and the curricular gravity field pulls usage back toward the easiest tasks. The nursing instructor is not at risk of that pattern because she is not buying anything new. She is using a textbook that happens to be better.

---

### Block 3 — When all three are yes: the four-section pharmacology course

Now run the same test against a different deployment. Three hundred and twenty pharmacology students across four sections, three instructors (one teaches two sections), a shared final exam, and an accreditation review next year that has flagged inter-section variance in board pass rates as a concern.

Q1: yes. Three hundred students is past any single instructor's in-head capacity, and the four sections are taught by people who do not coordinate weekly. The heterogeneity is real — students arrive with different prerequisite strengths, and within each section the instructor cannot tell which students are following which path to mastery.

Q2: yes. The accreditation review wants to know which section is producing the gap and why. The current data — final exam scores broken down by section — tells the committee that variance exists, but not which concepts cause it, which interventions narrow it, or whether the underperforming section's students are struggling with the same things as the overperforming section's high-risk students.

Q3: yes — but only because the department chair has explicitly precommitted. She has told her three instructors, in writing, that whichever section the measurement identifies as underperforming will be redesigned next term, with the chair's authority and budget. The chair has named what acting looks like before the data arrives.

This is the deployment where the loop earns its cost. The institution has scale (320 students), heterogeneity (four sections, three instructors, two course modalities), accountability (accreditation pressure), and pre-committed willingness to redesign. Medhavy here is not overhead. It is the only mechanism that produces the per-section, per-concept, per-student evidence the chair will need when she walks into the redesign conversation.

The drivers of "yes, yes, yes" are not features of Medhavy. They are features of the deployment. **Scale** forces the limits of human attention. **Heterogeneity** makes a single instructional approach mathematically wrong for some students. **Accountability** creates a use for the measurement. Strip any one of these out and the case collapses.

---

### Block 4 — The partial cases

Most real deployments do not score three yeses or three nos. They score two and one, or one and two, and the chapter has to be honest about what those partial answers mean.

**One yes, two no.** A small graduate seminar — twelve students, one instructor, fixed cohort — that happens to be using a difficult interdisciplinary text. Q1 fails (no scale). Q2 might pass (the instructor genuinely wants to know which students are bouncing off which concepts). Q3 fails (the instructor will not change the course because she designed it carefully and the cohort changes every year). One yes is not enough. The deployment is fine with the simpler stack. The yes on Q2 means the instructor would benefit from better notes and more thoughtful debriefs, not from a measurement-and-adaptation layer.

**Two yes, one no.** This is the painful case, because it almost works. A two-section anatomy course of sixty students each, with two instructors. Q1: yes (the heterogeneity across sixty students with two instructors is real). Q2: yes (someone — the program director — wants to know which approach is producing better retention). Q3: no. The two instructors will not coordinate. The senior one has taught this course for fifteen years and is not interested in changing her approach because someone else's data says she should. The program director knows this and will not force the issue.

Two yeses is not enough. The barrier is not technology. It is institutional capacity, the binding constraint that researchers like Cohen and Ball have documented for thirty years: the institution can only absorb improvements it has the capacity to act on, and capacity is faculty time plus willingness to change practice, not budget. The right move here is not to buy Medhavy. The right move is to address the institutional barrier — which may take three years and a personnel change. Until then, the simpler stack is correct.

**The "yes, but not yet" case.** A program that is two yeses today but is growing into three. The pharmacology service course that has one section of eighty this year, two sections next year, four sections two years from now. Q1 will pass when section three opens. Q3 might pass when the accreditation cycle starts. The right answer for *this* year is the simpler stack with a calendar reminder to revisit when scale arrives. Adopting eighteen months early is a faculty-time tax for capacity nobody is using yet.

---

### Block 5 — What "willing to act" actually requires

Q3 deserves its own block because it is the question most often answered yes too quickly, and it is the question that — when answered honestly — fails the most deployments.

Willing to act does not mean willing to receive a dashboard. It means the institution is prepared to change something based on what the measurement reveals. Concretely, three things:

- **A named owner of the redesign step.** Not "the curriculum committee." A person, with calendar time, who is on the hook when the measurement says one section is failing and a new approach is needed.
- **A budget for the act.** Faculty time to redesign a section is not free; it competes with research, service, and other teaching. If the redesign step happens after-hours on someone's good will, it is one resignation away from disappearing.
- **A political precommitment.** The senior faculty member whose section is most likely to be identified as the underperforming one needs to have agreed — out loud, before the data arrives — that she will participate in the redesign. The willingness to act must include the willingness of the people most at risk of being asked to change.

If any of those three is missing, Q3 is no. Not "yes, but we'll figure it out." No. Medhavy without willingness to act is expensive Canvas analytics — a measurement layer attached to nothing — and the literature on educational technology has been documenting this failure mode for a long time. The 2014 LAUSD iPad rollout — a 1.3 billion dollar program that put Pearson-curriculum iPads in the hands of every student in the Los Angeles Unified School District — collapsed not because the iPads failed but because the district had no curricular owner for what the iPads were supposed to deliver. The infrastructure was there. The capacity was not. The program wound down within two years.

The smaller cousin of LAUSD is the inBloom project — a Gates Foundation-funded student data infrastructure that was shut down fifteen months after launch in 2014. The technology worked. The institutions could not absorb what it asked of them. Parents revolted. State legislatures pulled out. The platform was sound. The institutional readiness was not. Adopting any measurement layer without the readiness to use it is buying inBloom in miniature.

---

## Worked example — five deployments through the test

These are the five deployments to run the test on. Each takes one paragraph and ends with a verdict.

**Deployment A.** Nursing fundamentals, single section of twenty-eight, one instructor with twenty years' experience, weekly contact, name-recognition by week two. **Q1 no** (scale). **Q2 no** (instructor already adapts in real time). **Q3 no implicitly** (the instructor is the institution; she acts on her own observations). **Verdict: AI+1 on Kindle is the complete answer.** Adding Medhavy is overhead, not value.

**Deployment B.** Anatomy and physiology, two sections of sixty taught by two instructors who do not coordinate. **Q1 yes** (heterogeneity across 120 students with two instructors is real). **Q2 yes** (the program director wants to know which approach retains better). **Q3 no** (the senior instructor will not change her practice, and the director will not force it). **Verdict: not yet.** The barrier is institutional, not technological. Address the coordination problem first; revisit when leadership or accreditation pressure changes the answer.

**Deployment C.** Pharmacology, 320 students across four sections, three instructors, shared final, accreditation review next year, chair has precommitted to redesigning whichever section underperforms. **Q1 yes** (scale and heterogeneity). **Q2 yes** (accreditation). **Q3 yes** (named owner, budgeted time, political precommitment). **Verdict: this is the deployment where the loop earns its cost.**

**Deployment D.** Pre-clinical clerkship, 240 students rotating through eight clinical sites with different attendings, different patient mixes, and no shared progress tracking. The clerkship director has authority and budget. **Q1 yes** (scale, heterogeneity, geographic dispersion makes in-head tracking impossible). **Q2 yes** (the variance is hidden by current measurement and the director needs to surface it). **Q3 contingent** (the curriculum committee has authority to redesign but has not precommitted to using it). **Verdict: yes — conditional on Q3 becoming an unambiguous yes before the contract is signed.** Get the precommitment in writing, then proceed.

**Deployment E.** Pharmacy continuing-education modules, five hundred enrollees per quarter, asynchronous, no live instructor, completion is the regulator-relevant outcome. **Q1 yes formally** (scale). **Q2 no** (completion is what matters; durable learning at six months is not what the regulator counts). **Q3 no** (the institution will not act on durable-learning data because the regulator does not ask for it). **Verdict: AI+1 on Kindle is the right answer.** The loop has no reward signal — Medhavy would be measuring something nobody is going to use.

Run your own deployment through the same template. The verdict should fall out in under three minutes. If you find yourself negotiating with the questions, that is information: the deployment is probably not a three-yes case.

---

## AI Wayback marginal callout — Audrey Watters

There is a recurring pattern in the history of educational technology that researchers have documented for over a century, and a writer worth knowing about it is **Audrey Watters**. Watters spent twelve years running Hack Education, a blog that did what mainstream tech journalism would not: cover edtech procurement decisions as if they were consequential. Her 2021 book *Teaching Machines* traces the arc from Sidney Pressey's 1920s testing devices through B. F. Skinner's teaching machines to today's adaptive platforms. Each generation, she shows, oversold personalization. Each generation discovered the rate-limiting step was not the algorithm but the curricular labor surrounding it. The reader who runs the three-question test honestly and lands at "no" is participating in the pattern Watters' work most respects — refusing to buy what the institution cannot use.

---

## Exercises

**Exercise 1 (Evaluate) — Run your primary deployment through the three questions.**
Pick the deployment most likely to receive a Medhavy proposal in your institution. Answer each of the three questions honestly. For each answer, write one sentence of reasoning that names the specific feature of the deployment driving the yes or no. If any question gives you trouble, note the trouble — that is information. The exercise is finished when you can defend each answer to a skeptical colleague.

**Exercise 2 (Evaluate) — Identify the strongest three-yes deployment in your institution.**
Find the deployment where all three answers are most clearly yes. Then write the success criterion: what would Medhavy need to show in this deployment within one term to justify renewal? Be specific. Not "improved learning." Something like "section-to-section pass-rate gap narrows by 50% by end of term 2." If you cannot write a measurable success criterion, the deployment may not actually be a three-yes case yet — Q3 is probably wobbling.

**Exercise 3 (Create) — Write a one-paragraph recommendation for or against Medhavy.**
Pick one deployment. Write a single paragraph, six to eight sentences, recommending for or against. The paragraph must cite the three questions, name which answers were uncertain, and arrive at a verdict that a budget committee could act on. The writing is the exercise — clarity in the writing forces clarity in the thinking. If the paragraph hedges, the recommendation is not ready.

---

## Common misconceptions

**"Bigger deployments always benefit from Medhavy."** Scale is necessary but not sufficient. The 500-enrollee CE module from Deployment E has scale and still fails the test because Q2 and Q3 are no. Scale without accountability and willingness is a population, not a use case.

**"If we have the budget, we should adopt."** Budget is the smallest cost. Faculty time on concept maps, case scenarios, and ongoing review is the larger cost. Institutional willingness to act is the cost with no line item. The license fee is what you can see; the rest is what determines whether the loop closes.

**"Medhavy will help me convince faculty to coordinate."** No technology causes coordination. Coordination is a leadership and incentive problem, and adopting a measurement layer before the institution can act on its measurements creates a more visible, more documented version of the underlying dysfunction. The two-yes-one-no anatomy course in Deployment B does not become a three-yes case by buying a tool. It becomes a three-yes case by addressing the coordination barrier first.

**"AI+1 on Kindle is the compromise option."** It is not. For most deployments it is the architecturally correct option. The "simpler stack" framing in this chapter is shorthand; it should not be read as "the lesser stack." A well-resourced AI+1 deployment with an attentive instructor outperforms a poorly-resourced Medhavy deployment without willingness to act. The technology is not the variable. The deployment is.

**"We can adopt now and figure out willingness to act later."** This is the inBloom failure mode. The institutional readiness to act on data has to precede the deployment of the measurement, or the deployment becomes politically toxic the first time the data is uncomfortable. Get the willingness in writing first, then sign the contract.

---

## What would change my mind

A reader who finishes this chapter with the three-question test in hand may reasonably ask: under what conditions would the framework itself be wrong?

Two conditions. First, if it turned out that the cost of running Medhavy at a small deployment — twenty students, one instructor — fell by an order of magnitude, the Q1 threshold would shift down. Faculty time on concept maps and case review is currently the binding cost; if AI tooling reduced that to a few hours per term and produced acceptable quality without faculty review, the deployment-size threshold could plausibly drop to thirty students with a still-positive return. The chapter would need rewriting. Second, if the seven-signal evidence base — currently strong theoretically but limited at scale — were shown across multiple deployments to produce learning gains that simpler interventions did not, the burden of proof would shift. The chapter would still maintain Q3 as a hard requirement (no measurement without willingness to act), but Q1's threshold would soften. Neither of these conditions holds today. If either changes, the three-question test gets revised, and this chapter is the first one rewritten.

---

## Still puzzling

- The Q1 scale threshold is heuristic — somewhere between sixty and a hundred and twenty students. The actual cutoff depends on instructor experience, course structure, and student heterogeneity. What measurement would tighten this from a heuristic to a defensible number?
- The "yes, but not yet" case (Deployment B and the growing-program example) is real and common. What is the right cadence for revisiting the three questions — annually, at accreditation cycles, at every faculty turnover?
- Q3 currently treats willingness as binary. But willingness varies by data shape: an institution may be willing to act on aggregate inter-section variance and unwilling to act on individual-student signals. Should the question be split?
- The chapter argues against adoption in named deployment types. It does not address the case where a single deployment within a portfolio is a three-yes case and the rest are not. Is partial adoption (one course, not the whole program) institutionally viable, or does that fragment the curricular consistency the institution needs?

---

## Bridge

If the answer is yes, what does adding Medhavy to Canvas actually involve? Chapter 11 walks through the technical integration in plain language, the institutional approval process that runs in parallel, and the curricular work that takes the longest and matters the most.
