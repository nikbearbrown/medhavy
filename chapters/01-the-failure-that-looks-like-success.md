# Chapter 1 — The Failure That Looks Like Success

**The reader learns why AI in education can look like it's working while actively harming learning — and why that failure is architectural, not incidental.**

---

## Opening case

A university deploys an AI tutoring tool. Engagement metrics climb. Students report satisfaction. Session completion rates hit 94%. The end-of-term exam arrives. The students who used the AI most score lower than the students who used it least.

The vendor's dashboard showed success. The exam showed something else.

This is not a hypothetical. It is the Bastani 2025 PNAS finding, translated into plain language. Bastani and colleagues at Wharton ran a randomized trial across nearly 1,000 Turkish high-school students in 9th, 10th, and 11th grade math. Four 90-minute practice sessions. Three groups: one with access to a standard GPT-4 chatbot ("GPT Base"), one with access to the same GPT-4 model wrapped in a system prompt that committed it to giving hints rather than answers ("GPT Tutor"), and a no-AI control group that practiced from the same problem set without any AI.

During practice, both AI groups outperformed control. They worked through more problems. They reported higher satisfaction. Engagement metrics — the kind a vendor's dashboard would surface — were indistinguishable between the GPT Base and GPT Tutor groups.

Then the unassisted final exam. No AI access. Same content the students had been practicing on for four sessions.

**The students who used the unguarded GPT scored roughly 17 percentage points below the no-AI control group.** [verify against the corrected PNAS figure, 10.1073/pnas.2518204122] The students who used the guarded GPT Tutor matched the control group — neither helped nor harmed compared to practicing without AI at all.

Same AI model. Same students. Same content. Same four sessions of practice. Two wrappers. Opposite learning outcomes on the only measurement that mattered.

This is the finding the rest of the book responds to. Before you decide whether your institution should add Medhavy [Humanitarians AI internal framework] to a Canvas + AI+1 [Humanitarians AI internal framework] deployment, you need to install one distinction in working memory: **engagement evidence is not learning evidence, and a dashboard cannot tell them apart.** Everything downstream depends on it.

---

## The engagement-learning gap

The thing Canvas measures well is who showed up. Time on page. Clicks. Module completion. Quiz submission. These are real measurements of real behaviors, and they were never designed to be measurements of learning. They were designed to administer courses — to confirm that a student opened the file, submitted the assignment, finished the module by the deadline. That is a legitimate measurement category. It is just not the one institutional decision-makers usually think it is.

The gap between engagement evidence and learning evidence comes from a finding in cognitive psychology that predates LLMs by 30 years. Robert and Elizabeth Bjork, working at UCLA in the early 1990s, drew a hard line between two things students and teachers routinely confuse: *current performance* (what the student can do right now, with the textbook open or the tutor present) and *learning* (what the student can do later, unassisted, possibly months from now). Current performance, the Bjorks demonstrated, is a strikingly unreliable predictor of learning. Worse — interventions that produce the highest current performance are sometimes the ones that produce the worst learning. Re-reading is the canonical example. It feels productive. It produces less retention than retrieval practice that feels harder.

The Bjorks called the gap between these two measurements the performance-learning distinction. Bastani 2025 is what happens when an unguarded LLM amplifies that gap to its maximum: AI groups had the highest in-session performance and, in the unguarded condition, the lowest learning.

The implication for a vendor dashboard is direct. A dashboard that shows time-on-page, session completion, and in-session quiz scores is showing current performance. Current performance is upstream of two very different downstream outcomes — genuine learning, or borrowed competence that evaporates the moment the AI is removed. Without a measurement that distinguishes them, the dashboard cannot tell which one is happening. The dashboard does not have a bug. It is honestly reporting what it was designed to report. The category of evidence it provides is not the category of evidence the adoption decision requires.

---

## The fluency trap

There is a second mechanism running underneath the engagement-learning gap, and it is specific to the technology you are evaluating. A well-trained large language model produces text that reads like understanding. Coherent paragraphs. Confident hedges in the right places. Domain terms used in the right relations. When a student asks "what's the difference between a beta-1 selective and a non-selective beta blocker?" and an unguarded chatbot returns 300 fluent words, the surface of that text is indistinguishable from an explanation a hospital pharmacist would write.

This is the fluency trap. The text reads as understanding on the page; the student reads it nodding; the student moves on. What did not happen during that interaction is the cognitive work that produces a durable schema — retrieving prior knowledge, generating a hypothesis, encountering a prediction error, repairing the schema. Reception, however fluent, is not generation. Bender and colleagues described this in 2021 from the model side: a language model's surface coherence is not a reliable signal of comprehension on either side of the conversation. The reader infers understanding from the fluency. The reader is sometimes correct. The reader is sometimes — measurably, in Bastani's data, roughly 17 points worth — wrong.

The fluency trap is not specific to "bad" AI tools. It is specific to *competent* AI tools deployed without architectural commitments about what they will and will not do. The better the model is at sounding like an expert, the more powerful the trap, because the perceived value of the interaction goes up while the cognitive work going into it stays low or goes lower. This is the failure mode the rest of the book is organized around preventing.

---

## The wrapper is the variable

Now the central architectural claim. In Bastani, the only difference between the harm group and the no-harm group was a system prompt. Same GPT-4 model. Same students. Same content. Same four sessions. The GPT Base condition handed the model to students with no constraints on its behavior. The GPT Tutor condition wrapped the same model in instructions that committed it to giving hints and asking questions rather than producing complete solutions. That wrapper was the entire architectural intervention. It was not a different AI. It was the same AI committed to do a different thing.

The 17-point gap is what that wrapper bought.

This is the foundational claim under every subsequent chapter of this book: **the AI is not the variable. The wrapper around the AI is the variable.** Two products can be built on the same underlying model and produce opposite learning outcomes. Two vendor proposals that both say "powered by GPT-4" or "powered by Claude" are not the same product. The architecture — what the platform commits the AI to doing and refusing to do — is the unit of analysis. The base model is a component.

You can see why this matters for the decision in front of you. When the vendor's feature sheet for Medhavy says "AI-powered tutoring," that phrase contains zero information about whether the system will help or harm your students. It is consistent with both outcomes Bastani observed. The relevant question is not "does this product use AI?" — every plausible product does. The relevant question is "what architectural commitments does this product make about how the AI behaves, and how would I know if it failed at them?" That is the question the rest of this book is built to help you ask of any AI layer, Medhavy or otherwise.

There is a parallel from the pre-LLM era worth keeping in mind. The ASSISTments tutoring system, developed at WPI by Neil Heffernan and colleagues, produced roughly three-quarters of a year of math gain in Maine middle schools — same content as the textbook, different architecture (immediate scaffolded feedback, teacher report-back). Same problem set, different wrapper, opposite outcome from what Bastani saw with unguarded GPT. The architecture-matters claim is not new. The stakes are new because the wrappers are now capable of producing fluent answers to almost any question, which means the architectural commitments matter more, not less, than they did when the underlying tool was a hint database.

---

## What this means for the decision in front of you

The question this chapter is not asking is "is AI bad for learning?" The answer to that question, on current evidence, is "it depends on the architecture, and Bastani gives us one well-measured data point on what the dependency looks like." That is not a useful question for a curriculum director with a budget meeting in six weeks. The useful question is sharper.

**Given that the same AI can produce opposite outcomes depending on what the platform commits it to doing — what specific architectural commitments would you require any AI tool to make before you added it to your Canvas instance?**

Bastani gives you a starting list. At a minimum:

1. *A commitment about what the AI will not do.* In Bastani's GPT Tutor, the commitment was: do not produce complete solutions; produce hints and questions that redirect the student to their own reasoning. Medhavy's Ask AI mode [Humanitarians AI internal framework] is built on this commitment — Chapter 3 explains what that looks like in practice.

2. *A measurement that is not in-session performance.* In Bastani, the measurement that revealed the gap was a delayed, unassisted exam. In a Medhavy deployment, the equivalent is the Frictional Framework [Humanitarians AI internal framework] — the seven signals that measure whether a student is learning or borrowing. Chapter 7 covers them.

3. *A grounding source.* In Bastani, both AI conditions used the same problem set; the AI did not roam. In a Medhavy deployment, Ask AI is grounded by RAG to the textbook the student is reading. The AI cannot wander into off-curriculum content the institution has not approved.

You do not need to take Medhavy as the answer to these requirements. Other architectures could meet them. What you need from this chapter is the *categorical* shift: that the question "should I adopt this AI tool?" cannot be answered from a feature sheet, because the feature sheet describes capabilities, not commitments. The next chapter starts the diagnostic that tells you whether your deployment needs an architecture with these commitments at all — or whether the simpler answer (AI+1 on Kindle, no measurement layer, no adaptation) is the right one for the context you are actually operating in.

---

## Worked example: Bastani as a deployment case

It is worth walking the study itself one more time, slowly, in the shape an institutional reader will need to recognize when she sees a similar deployment in her own program.

**The setup.** A consortium of Turkish high schools agreed to a randomized trial. Roughly 50 9th–11th grade math classes. Nearly 1,000 students. Each class assigned to one of three conditions. The content was identical across conditions: four 90-minute practice sessions on procedural and conceptual math problems aligned with the school curriculum.

**The conditions.** GPT Base students worked the problems with access to an unmodified GPT-4 chatbot. They could ask anything. The model would answer. GPT Tutor students worked the same problems with access to the same model — but the model had been given a system prompt that committed it to a tutoring stance: ask clarifying questions, offer hints, refuse to produce a complete worked solution. The no-AI control worked the same problems with the textbook and pencil and paper.

**The in-session metrics.** Both AI conditions outperformed control during practice. They completed more problems. They reported the sessions as helpful. If you had run an LMS dashboard over the data and stopped there, you would have concluded that both AI conditions were producing strong engagement and the unguarded version was producing slightly better in-session performance. You would have written a positive report to your dean.

**The exam.** At the end of the four sessions, every student took an unassisted exam — no AI, no notes — on the same content. GPT Base students scored substantially below control. GPT Tutor students scored comparably to control. The students who had the *strongest* in-session performance — the unguarded AI group — produced the *weakest* learning by the time the AI was removed.

**The institutional translation.** Imagine the same shape in your own program. A pharmacology section uses an unguarded AI study companion. Practice quiz scores are strong. Student satisfaction is high. The dashboard shows healthy engagement. The mid-term and the board exam are unassisted. The students who used the AI most score lower than the students who used it least.

You would not have seen this coming from the dashboard. You would have seen something the dashboard does not show: a behavioral pattern in how the AI was used and what cognitive work the student did or did not do while using it. The vendor would not have flagged it. The platform was honestly reporting what it was designed to report.

That is the failure that looks like success. The book exists because the technology has made this failure mode more available, not less, and the standard institutional measurement stack does not catch it.

---

## Exercises

1. **(Analyze)** Open the Canvas analytics dashboard for one course you know well. Identify three metrics it presents — for example, time-on-page, module completion rate, quiz score average. For each, write one sentence on what behavior it measures and one sentence on what genuine learning signal it would miss. The point is not to dismiss the metrics — they measure real things. The point is to name precisely what they do not measure.

2. **(Analyze)** Describe a time in your career when you watched student engagement look high and learning look low. (Most curriculum directors have an example.) What did the dashboard or the gradebook show? What would a learning-evidence measurement — performance on an unassisted, delayed assessment — have shown? Write the comparison as two sentences. If you cannot recall a specific case, describe the kind of course or student population where you would predict this gap, and what evidence would resolve it.

3. **(Evaluate, applied to your own deployment)** Given Bastani's finding, write down the single architectural commitment you would require any AI tool to make before adding it to your Canvas instance. State the commitment plainly — what the AI will do, what it will not do, and how you would know if it failed at the commitment. Keep this answer; you will return to it in Chapter 11.

---

## Common misconceptions

**"If students are using the tool and saying they like it, they're learning."** This is the engagement-learning conflation. It is the single most prevalent misreading among institutional decision-makers and it is what Bastani most directly rebuts. The GPT Base students in Bastani used the tool more and reported satisfaction; they learned less. Student satisfaction is a real measurement of a real thing — student satisfaction. It is not a measurement of learning, and the correlation between the two is unreliable enough that you cannot use one as a proxy for the other on a high-stakes adoption decision.

**"AI is bad for education."** The chapter does not say this and you should not leave with it. Bastani's GPT Tutor matched the control group — neither helped nor harmed compared to no-AI practice. The harm was specific to the unguarded condition. The architectural commitments are the variable. A categorical position on "AI in education" is the wrong unit of analysis. The right unit of analysis is the specific commitments a specific tool makes.

**"A higher score during practice means a higher score on the exam."** This is the performance-learning conflation, formalized by the Bjorks 30 years before LLMs existed. It was wrong then. It is more wrong now, because the technology can produce in-session performance gains that are decoupled from learning to a degree the pre-LLM literature had not anticipated.

**"The vendor's dashboard reflects whether students are learning."** It reflects whether students are using the platform. Different measurement category. A vendor that conflates the two is selling you a metric, not a finding.

---

## What would change my mind

The central claim of this chapter is that the wrapper around an AI is the variable that determines whether the deployment produces learning or harm, and that engagement-style measurements cannot distinguish the two. A finding that would revise this claim: a well-powered randomized trial — comparable in size to Bastani, run in a different domain and at a different age band — showing that unguarded chatbot access produces *equivalent or better* learning on a delayed, unassisted assessment compared to no-AI control. If such a study were published and held up to replication, the architectural argument would still survive (the wrapper is still a variable; some wrappers happen to be neutral), but the urgency would drop sharply. The Bastani finding is currently one RCT in one country in one subject; the chapter's argument is held up by the *strongest available evidence*, not by settled science, and an institutional decision-maker is entitled to know that.

---

## Still puzzling

- How far does the Bastani finding generalize beyond Turkish high-school mathematics? Health-sciences-specific replication does not yet exist. The mechanism (offloading produces fluent performance without schema formation) is plausibly general; the effect size at health-sciences ages and content levels is not measured.

- Are prompt-level guardrails enough, or do you need system-level architecture (RAG grounding, retrieval over a curated corpus, explicit refusal policies)? Bastani tested only the prompt-level case and found a clear separation. Whether prompt-level guardrails remain sufficient as students become more sophisticated at routing around them is an open empirical question.

- Do students adapt to guarded AI tools by switching to unguarded ones when the institution is not looking? A guardrail at the curriculum tool does not bind a student's behavior on their own laptop. The institutional implications of that are a Chapter 9 problem.

- Is there a deployment context where unguarded AI does produce durable learning? Possibly — for advanced learners with strong existing schemas, the offloading risk drops because the schema is already in place. The chapter has not tested this, and the Bastani sample (9th–11th grade) does not speak to it.

---

## AI Wayback marginal callout — Richard Atkinson

> *Long before LLMs, before adaptive learning had a marketing budget, Richard Atkinson at Stanford built a computer-aided instruction system in the 1960s that delivered individualized math and reading practice to elementary students. The system worked — published results showed real gains — but it did not claim to replace teachers. It was sized to what the technology could honestly do. Atkinson's CAI failed commercially anyway, killed by the economics of mainframe hardware and the politics of school adoption, not by pedagogy. The lesson rhymes uncomfortably with today: the architecture mattered, the wrapper around the computation was what made the difference, and the institutional decision to buy or not buy ran on factors mostly unrelated to whether the system worked. The "wrapper is the variable" finding is not new. The Bastani study is the cleanest contemporary measurement of a pattern Atkinson would have recognized from a different decade and a different machine.*

---

## Bridge to Chapter 2

The failure is architectural. The fix is architectural. The four modes Medhavy introduces — Ask AI, Quiz Me, Case Study, and Glimmer [Humanitarians AI internal framework] — are each a different architectural commitment, designed to prevent a different specific form of the failure this chapter described.

Before you can decide whether your deployment needs those commitments, you need a sharper question. Most edtech failures come from solving the wrong problem correctly — adding measurement and adaptation to deployments that did not need them. Chapter 2 starts with the simplest version of the right question: *do you even need this layer?* Some deployments are well-served by a better textbook on Kindle, full stop. Others are not. The next chapter is the three-question test that tells you which kind you have.

---

*Sources cited in this chapter: Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., & Mariman, R. (2025). Generative AI without guardrails can harm learning: Evidence from high school mathematics. Proceedings of the National Academy of Sciences, 122(26), e2422633122. Correction at 10.1073/pnas.2518204122. · Bjork, R. A., & Bjork, E. L. (1992). A new theory of disuse and an old theory of stimulus fluctuation. · Bender, E. M., Gebru, T., McMillan-Major, A., & Shmitchell, S. (2021). On the Dangers of Stochastic Parrots. FAccT '21. · Roschelle, J., Feng, M., Murphy, R. F., & Mason, C. A. (2016). Online Mathematics Homework Increases Student Achievement. AERA Open, 2(4). · Atkinson, R. C. (1968). Computerized instruction and the learning process. American Psychologist, 23(4), 225–239.*
