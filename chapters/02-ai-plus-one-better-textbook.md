# Chapter 2 — AI+1 Is a Better Textbook. Is That Enough?

**The reader learns what AI+1 is, what it adds to a Kindle or Canvas deployment, and the specific condition under which that is not sufficient.**

---

## Opening case

Most educational technology fails not because it does its job badly but because it is asked to do three jobs at once: be a better textbook, be a measurement system, and be an adaptive engine. Each job is a different product. Stacking them inside a single piece of software produces a tool that is mediocre at all three and excellent at none. The marketplace is littered with the remains.

AI+1 [Humanitarians AI internal framework] is explicitly the first thing only. It is a domain-specific, practitioner-voice textbook produced at the intersection of human domain expertise and AI fluency. It is not a platform. It is not a measurement system. It is not adaptive. It is a book — sold for roughly a dollar on Kindle, paired with Brutalist slides [Humanitarians AI internal framework] for in-class delivery, and graded inside whatever Canvas instance the institution already runs.

For a significant fraction of deployments — likely most of them — that stack is exactly what the deployment needs. AI+1 + Kindle + Brutalist slides + Canvas is a complete learning environment, and adding anything to it would be overhead, not value. For a smaller fraction, it is not enough. This chapter is the diagnostic that tells you which kind of deployment you have.

The diagnostic is three questions. Before the chapter ends, you will run your own deployment through them.

---

## What AI+1 actually is

The phrase "AI+1" is doing specific work. It is not "AI plus one feature" or "AI plus one human." It is the framework's claim about authorship: every AI+1 textbook is co-produced by a domain practitioner — a hospital pharmacist for a pharmacology text, a charge nurse for a med-surg text, a board-certified physician for a clinical reasoning text — plus AI used as a drafting and synthesis tool. The "+1" is the irreducibly human contributor [Humanitarians AI internal framework] whose judgment the reader is meant to encounter on the page. The text reads as one expert practitioner explaining the material to a single student, because that is the production model the framework specifies.

The intellectual lineage runs through Paul Daugherty and James Wilson's 2018 *Human + Machine*, which argued that the durable AI deployments are the ones that find the "missing middle" — the work that humans do badly alone and machines do badly alone, but the pair does well together. AI+1 is a specific instance of that pattern in the publishing context. The expert practitioner alone produces high-quality text slowly. The AI alone produces fluent text without grounded judgment. The pair produces high-quality text fast enough to actually ship a domain-specific textbook at a price the student can afford. The "+1" is the load-bearing element of the framework's name; without the human expert anchoring it, what is left is a generated textbook, and a generated textbook is not the same product.

What AI+1 is *not*: an AI running at read time. The reader does not query the model when she opens the Kindle. The text was produced with AI; the text does not run AI. This is the most common confusion among institutional decision-makers, and it matters because Medhavy is the *other* thing — a system that does run AI at read time, on top of the AI+1 content. Conflating the two is the error that leads readers to think "we already have AI+1 textbooks, so we already have Medhavy." You do not. You have the content layer. Medhavy is a measurement and adaptation layer that can sit on top of the content layer if the deployment warrants it.

The Irreducibly Human [Humanitarians AI internal framework] taxonomy that runs through the AI+1 catalog is a labeling of the components of a domain that cannot be reliably automated — clinical judgment under ambiguity, the ethical weighting of competing harms, the contextual interpretation of a finding. An AI+1 textbook is, in part, an extended argument for which parts of a domain practitioner's work are in this category, because those are the parts the human reader needs to be apprenticed into and the AI cannot be trusted to teach unsupervised. The taxonomy matters here because Medhavy's four modes (Chapters 3–5) are calibrated against it — each mode is designed for a different cognitive operation, and the calibration assumes that some of those operations belong to humans permanently.

---

## The standard AI+1 deployment stack

What does the stack actually look like in a real institutional deployment? Four components, no more, and each one does a specific job.

**Kindle + AI+1 text.** The content. A $1 Kindle edition produced under the AI+1 framework. The student reads it, highlights, takes notes inside the Kindle ecosystem. The text reads as a single practitioner's voice — not a committee-edited textbook, not a publisher's flagship, not a generated synthesis. The cost structure (cheap distribution, premium content, no platform lock-in) was deliberate: the framework is incompatible with $200 textbook economics because the framework's value proposition is that the content is good and the delivery is cheap.

**Brutalist slides.** The in-class delivery vehicle. The name comes from Brutalist Web Design (Copeland 2014) — the manifesto that says content should be readable on all devices, only hyperlinks and buttons should respond to clicks, performance is a feature, decoration only when needed. Translated into instructional slides, this means: text-heavy, no clip-art, no animations, no theme-of-the-month design system. A Brutalist slide is one or two propositions, possibly a diagram, sometimes a citation. The aesthetic is not a personal preference; it is a deliberate refusal of the cognitive-load tax that decorative slide design imposes. If you have ever sat through a 90-minute lecture and remembered the transitions better than the content, you have lived the problem Brutalist slides exist to solve.

**Canvas (or equivalent LMS).** The administrative layer. Assignment posting, grade collection, attendance, discussion forums, deadline reminders. Canvas does this job well. It was designed for it. The chapter is not going to argue that Canvas should do more — most of the harm in edtech comes from asking Canvas to do more.

**The instructor.** The active learning layer. Discussion. Office hours. Real-time adaptation. Knowing which students are confused this week and why. For a class of 30 with one instructor, the instructor *is* the measurement and adaptation layer; she does it manually, in real time, with her professional judgment as the algorithm.

That is the stack. AI+1 + Brutalist slides + Canvas + an instructor who knows her students. For most deployments in most institutions, it is complete. Active learning literature — Freeman et al.'s 2014 PNAS meta-analysis of 225 STEM studies found that active-learning sections cut failure rates from 34% to 22% — supports the structural prediction that this stack outperforms passive lecture even without any AI running at read time. The AI ran at write time, when the textbook was produced. The active learning runs at class time, when the instructor uses the textbook and the slides as raw material for discussion. The retrieval practice runs at study time, when the student tests herself on the content. None of these layers needs AI to run on the device while the student is reading.

This is the baseline. Adding anything to this stack is a decision that requires justification. The three-question test is the diagnostic.

---

## The three sufficiency questions

The chapter's load-bearing artifact. Three questions you will return to in Chapter 9, in Chapter 11, and probably in the budget meeting six weeks from now.

**Question 1: Does the deployment need to present content differently to different learners at scale?**

Not "present different content" — that is the curriculum question, and AI+1 handles it at the textbook level. The question is whether different learners need different *pedagogical approaches* to the same content. A student who has never encountered the citric acid cycle needs a different entry point than a student who studied it three years ago and is rebuilding the schema. A student strong on mechanism but weak on clinical application needs a different sequence than a student strong on application but weak on mechanism. If your deployment serves one cohort with similar entry points and you have an instructor who can adjust her teaching in real time, the answer to Question 1 is plausibly no. If your deployment serves multiple sections with heterogeneous entry points and no instructor can see the whole picture at once, the answer is plausibly yes.

The honest version of the question is: *at the scale you are operating, can a human instructor present the content differently to each learner who needs it?* If yes, you have not yet exhausted the human layer; adding a software layer is premature. If no — if the scale or the heterogeneity has pushed past what a human can do — Question 1 is a yes.

**Question 2: Does someone need to know whether the variation is helping?**

This question presupposes Question 1. If you are not varying delivery, you have nothing to measure. If you are varying delivery — either through a software layer or through faculty who teach different sections differently — the question is whether your institution needs to know whether the variation is producing learning or just producing variation. For a single-instructor class of 30, the instructor knows. For a 300-student program across five sections with three instructors, no one knows by default. You can find out — by adding measurement. The question is whether you need to.

The honest version: *if a section was performing worse than another section, when would you find out, and by what mechanism?* If the answer is "the board exam in 18 months" or "the licensure pass rate next year," your current measurement system is end-of-pipeline. End-of-pipeline measurement is useful but it does not let you intervene. If the answer is "I cannot find out at all," and that is unacceptable, Question 2 is a yes.

**Question 3: Is the institution willing to act on what the measurement reveals?**

This is the question most curriculum directors discover, in retrospect, was the binding constraint. You can add a sophisticated measurement layer to a deployment. You can produce dashboards that show exactly where students are struggling and which interventions are working. Then the institution does nothing with the information, because acting on it would require changing a curriculum, replacing a course, restructuring a sequence, or having a conversation with a tenured colleague whose section is producing the weakest outcomes. Measurement without willingness to act is expensive Canvas analytics. The information sits in a dashboard nobody operationalizes.

The honest version: *if Medhavy showed you, in week 8, that Section 3 is producing weaker durable learning than Section 1 on the same content, what would happen?* If your answer is "I would convene a meeting, identify the cause, change something" — Question 3 is a yes. If your answer is some version of "I would note it" — Question 3 is a no, and adding the measurement layer is a budget mistake regardless of how good the technology is.

**If any of the three answers is no, stop here.** AI+1 on Kindle is the right answer. Not a compromise — the right answer. Adding Medhavy to a deployment that does not need the loop produces overhead without value. The honest case for not adopting is, in many institutions, the strongest case the book makes. If all three answers are yes, the rest of this book is what tells you what the loop looks like and what it would cost.

---

## What Medhavy adds to the stack — in plain language

Medhavy is not a replacement for AI+1. It is a layer on top. The relationship is structural: AI+1 is the content; Medhavy is the loop [Humanitarians AI internal framework] that presents that content differently to different learners, measures whether the variation is helping, and adapts. Chapter 8 will get to the technical details. The plain-language version is sufficient here.

*Present differently.* Medhavy can deliver an AI+1 chapter to one student as a Socratic question sequence (Ask AI mode) and to another student as a retrieval-practice flow (Quiz Me mode), depending on what the student has demonstrated in prior sessions. The content is the same — same chapter, same expert practitioner's voice. The pedagogical approach is different.

*Measure whether it helped.* Canvas measures time on page, completion, quiz score. Medhavy measures the seven friction signals (Chapter 7) — behavioral traces that distinguish a student who learned from a student who performed. The two measurement categories are not interchangeable; the Bastani finding in Chapter 1 was the most extreme demonstration of why.

*Adapt.* Medhavy runs a contextual bandit per student per concept — an algorithm that learns, over the course of a term, which pedagogical approach produces the strongest learning signal for this particular student on this particular concept, and surfaces that approach more often. The bandit is not a recommendation engine. It is an experiment that runs continuously, with delayed learning outcomes as the reward signal.

That is the loop. Three components, each one impossible without the other two. Present differently with no measurement is variation without information. Measurement with no adaptation is dashboards. Adaptation without presenting differently is a recommendation engine with nothing to recommend. The whole loop is what Medhavy is; partial versions of it have been tried, and most have failed to produce the durable learning gains they were designed for.

The distinction the reader has to leave the chapter with: **a better textbook is a better textbook.** It is not a measurement system. It is not an adaptation engine. AI+1 is the first thing only. Medhavy is the second and third things, sold separately, and warranted by a specific institutional need that not every deployment has.

Beverly Park Woolf made an early version of this argument in *Building Intelligent Interactive Tutors* (2009, Morgan Kaufmann). She has a PhD in computer science and an EdD, which is unusual, and her position was unusually precise: an intelligent tutor adds value beyond a well-designed textbook when the deployment cannot rely on a human teacher to do the adaptation, and the conditions under which that holds are conditions of scale, heterogeneity, and accountability. Sixteen years later, Woolf's conditions are an early form of the three-question test. The book is not inventing the diagnostic. It is naming it for the curriculum director who needs to apply it.

---

## Worked example: two deployments side by side

The diagnostic is easier to see in two concrete cases. Both real-shaped, drawn from common health-sciences program configurations.

**Deployment A.** A nursing pharmacology course. Thirty students in one section. One instructor — a nurse educator with twelve years of clinical experience and four years teaching the course. The AI+1 pharmacology Kindle is required reading. Brutalist slides for in-class delivery. Canvas for assignments and grades. The instructor knows every student by week three. She can tell from the Tuesday discussion who has done the reading and who has not. She adapts in real time — slowing down on receptor binding when students are struggling, pushing harder on dose calculation when they are not. She runs office hours; she answers the questions students were too embarrassed to ask in class. She is the loop.

Run the three questions:
- Q1 (present differently at scale)? No — n=30, one instructor, manageable by the human layer.
- Q2 (need to know whether variation helped)? The instructor knows.
- Q3 (willing to act)? She is already acting, in real time, in every class.

All three no. AI+1 on Kindle is the right answer. Adding Medhavy here would be overhead. The instructor is already doing what the loop does, and she is doing it with judgment a contextual bandit cannot match in a class this small. The right institutional move is to support her — give her the Brutalist slides, the Canvas integration, the Kindle access — and stop. Not adopting Medhavy is the correct decision, and it does not become correct only after the budget is tight.

**Deployment B.** Nursing pharmacology across five sections. Three hundred students total. Three instructors of varying experience. The sections share a common syllabus but the instructors teach differently; students place into sections by registration order, not by entry level. The program director — the reader of this book — has no shared visibility into which students are struggling with which drug classes. The board exam is 14 months out. The dean wants to know why one section had a lower NCLEX pass rate last year, and the director's honest answer is "I don't know."

Run the three questions:
- Q1 (present differently at scale)? Yes — 300 students, multiple instructors, no human can do this manually.
- Q2 (need to know whether variation helped)? Yes — the director cannot answer the dean's question with current measurements, and the cost of the unknown is showing up in board pass rates.
- Q3 (willing to act)? Yes — the dean has explicitly authorized intervention based on measurement, and the director has a curriculum committee she can convene.

All three yes. This deployment warrants Medhavy. The loop is the answer to a problem the program is actually having, and the cost of the loop is justified by the size of the problem.

The two deployments use the same AI+1 content. They have the same students entering with similar prior knowledge. They differ in scale, heterogeneity, and accountability — exactly the three drivers the three-question test was built to detect. Deployment A is well-served by the simpler stack. Deployment B is not. The diagnostic does not say one is better than the other; it says they are different deployments that warrant different answers.

The hardest version of the case — and the most common — is the in-between. A program of 90 students across two sections with one experienced instructor and one new instructor. Question 1 is a tentative yes. Question 2 is a tentative yes. Question 3 depends on whether the senior faculty member who teaches Section 1 is willing to have her teaching examined alongside the new instructor's. Most institutions hesitate at Question 3, and that hesitation is the most important data point the diagnostic produces. If Question 3 is uncertain, the right move is to *resolve Question 3 before buying Medhavy*, not to buy Medhavy and hope.

---

## Exercises

1. **(Evaluate, applied to your own deployment)** Describe your primary deployment in three sentences: how many students, how many sections, how many instructors, what scale of program. Then run the three questions. Record your honest answers. If any answer is uncertain, write one sentence on what evidence would resolve it. Keep the answers — you will return to them in Chapter 9 and Chapter 11.

2. **(Apply)** For a deployment where all three answers are yes, name one specific piece of information the loop would produce that your current Canvas dashboard cannot. Not a category of information — a specific concrete piece. (Example: "Whether the students who scored 78 on the dosage calculation quiz in week 6 are likely to retain that knowledge for the board exam in 14 months.") The exercise is testing whether you can describe the value proposition in operational terms.

3. **(Evaluate)** For a deployment where at least one answer is no, write a one-paragraph defense of why the simpler stack is the *correct* answer, not a compromise. Address the reader who will say "but if Medhavy is even slightly better, shouldn't we adopt it?" The point of the exercise is to make sure you can defend the no answer with confidence to a colleague or a vendor.

---

## Common misconceptions

**"AI+1 already does what Medhavy does."** No. AI+1 is the content; Medhavy is the measurement and adaptation layer. They are different products from the same publisher in the same lineage, sold separately because they serve different institutional needs. A program that has adopted AI+1 textbooks has not adopted Medhavy. A program that wants only the content has the right answer in AI+1 alone.

**"An adaptive textbook is AI+1."** Adaptive textbooks (ALEKS-style platforms where the *content* shifts based on student performance) are a different category. AI+1 is content written by a domain expert with AI assistance and then frozen — the book does not adapt at read time; the *student* adapts to the book. Whether you also want a layer that adapts at read time is the Medhavy question.

**"More features mean better outcomes."** They usually do not. The active-learning literature is dense with examples where adding features to a course (more videos, more interactive quizzes, more digital handouts) produced no learning gain and sometimes a learning loss. The deployment is the unit of analysis; the feature count is a proxy. Run your deployment through the three questions before you run it through a feature comparison.

**"If we don't adopt now, we'll fall behind."** Vendor framing. There is no "behind" in educational technology — there is "what your deployment needs" and "what your deployment does not need." A program that buys a measurement layer it cannot operationalize is more behind, not less, than a program that buys nothing and runs the simpler stack well.

---

## What would change my mind

The chapter's central claim is that a better textbook is sufficient for most deployments, and that adding a measurement-and-adaptation layer is warranted only when scale, heterogeneity, and willingness-to-act are all present. A finding that would revise this claim: a large randomized trial — multi-institution, mixed deployment sizes — showing that adding a Medhavy-style loop produced meaningful learning gains over AI+1 alone *even in small single-instructor classes where the human teacher could plausibly handle adaptation manually*. If the loop turned out to outperform a strong human instructor at small scale, the three-question test would need to be retired or substantially loosened. The current evidence does not support that result; the analogous studies in adaptive courseware (mostly in larger sections) show modest gains that disappear or invert in small sections with strong instructors. But the result is conceivable and would change the chapter's diagnostic.

---

## Still puzzling

- What is the actual size threshold where the human instructor stops being able to do the loop manually? The chapter uses 30 and 300 as the extremes. The middle range — 60, 90, 120 — is where most curriculum directors live, and the diagnostic does not give a sharp answer there.

- How do you measure "willingness to act" before you have committed to a measurement system? Asking the question in the abstract produces yes answers that do not survive contact with the first inconvenient finding. There is no clean way to test the institution's tolerance for what the measurement will reveal short of running the experiment.

- Are there deployments where AI+1 is *not* enough and Medhavy is *also* not enough — where the missing layer is something neither product provides? Possibly. Clinical placement, faculty mentorship, and curriculum committee work are not in the AI+1 stack and are not in the Medhavy stack. The book is not claiming this stack solves all of educational delivery. It is claiming this stack solves the textbook-and-content-delivery problem and adjacent problems, well enough to bracket the rest.

- What happens to the three-question test when LLM-bundled LMS features (Canvas Cody, etc.) become more capable? If Canvas ships its own measurement layer in 2027, Question 2 may be answerable inside Canvas for some deployments. The category distinction between *administrative measurement* and *learning measurement* should survive feature creep, but the boundary will move.

---

## AI Wayback marginal callout — J.C.R. Licklider

> *In 1960, before AI was a marketing category and decades before Kindle, J.C.R. Licklider — working at the Pentagon-adjacent BBN — published "Man-Computer Symbiosis," a paper arguing that the durable design problem in computing was not whether machines would replace humans but how the interface between the two could be made productive. Licklider's argument: the human and the machine each do something the other cannot, and the work of design is to specify the seam between them clearly enough that the combination produces value neither could produce alone. Sixty-five years later, the AI+1 framework — domain expert plus AI fluency, with the human providing the irreducibly human judgment and the AI providing scale — is Licklider's symbiosis applied to publishing. The "+1" is what Licklider would have called the human side of the seam. The chapter's three-question test is what Licklider would have called the question of whether the seam needs to be moved further toward the machine for a particular task, or held where it is.*

---

## Bridge to Chapter 3

If you ran your deployment through the three questions and the answer is no — or even one no — AI+1 on Kindle is the right stack and the book has done its job. You can stop here. You can return when the deployment changes.

If the answer is yes — three yeses, or three plausible yeses pending resolution of one — the next three chapters explain what the loop actually does. The loop has four pedagogical interventions ("modes") and Medhavy chooses among them based on what the measurement layer is telling it. Each mode is a different cognitive operation with a different evidence base and a different deployment context. The next chapter starts with the most distinctive of the four — the mode that does not answer questions, which is the mode most easily mistaken for a chatbot and the mode whose architecture most directly responds to the Bastani finding. Ask AI.

---

*Sources cited in this chapter: Daugherty, P. R., & Wilson, H. J. (2018). Human + Machine: Reimagining Work in the Age of AI. HBR Press. · Bloom, B. S. (1984). The 2 Sigma Problem. Educational Researcher, 13(6), 4–16. · Freeman, S., Eddy, S. L., McDonough, M., et al. (2014). Active learning increases student performance in science, engineering, and mathematics. PNAS, 111(23), 8410–8415. · Bruner, J. S. (1966). Toward a Theory of Instruction. Harvard University Press. · Copeland, D. B. (2014). Brutalist Web Design. brutalist-web.design. · Hilton, J., et al. (2016). Open educational resources and college textbook choices. IRRODL. · Woolf, B. P. (2009). Building Intelligent Interactive Tutors. Morgan Kaufmann. · Licklider, J. C. R. (1960). Man-Computer Symbiosis. IRE Transactions on Human Factors in Electronics.*
