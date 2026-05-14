# Chapter 5: What Doesn't It Know Yet?

In my Computational Skepticism textbook, the opening case is a Swedish emergency department. A 49-year-old woman died in a waiting room. The AI triage system was working exactly as designed. Its metrics were clean. Its validation had been published. By every measure the engineers had built into the system, it had succeeded.

The gap between "the system succeeded" and "the patient died" is not a calibration problem. It is a supervision problem. The engineers had built a system for evaluating the system. They had not built a system for supervising it. No one had asked: what does this system not yet know, and what happens to a patient when it doesn't know it?

Medhavy is a learning system. The stakes are different. But the structure of the failure is identical — a system that knows its own metrics are clean is not the same as a system that knows it is working.

So this is Chapter 5, not the fine-print disclosure buried in a third-year retrospective when the metrics can no longer be managed. The unknowns go here because this is where they belong: before the claims, not after the damage.

---

## What Medhavy Knows

Let me be specific about what the preceding four chapters have actually established.

The misallocation problem is real. Students are spending cognitive resources on the wrong things at the wrong times, and conventional platforms either don't know this or can't act on it. The platform architecture is sound — the four-layer integration of content, assessment, adaptation, and supervision is novel and theoretically grounded. The consent design is ethical. The GLP framework — the Genuine Learning Probability signal that drives the adaptive engine — is built on legitimate neurobiological priors. And the experiment is running. Physics is live at physics.medhavy.com. Cancer Biology is live at cancer.medhavy.com. The data is being generated right now.

That is what I know.

---

## What Medhavy Does Not Yet Know

### 1. The right weights for the GLP reward signal

The GLP framework specifies seven components of the evidence stream: temporal engagement pattern, error trajectory coherence, cross-context transfer, uncertainty calibration, social knowledge texture, retrieval strength decay signature, and scaffolding response curve. Each component is theoretically grounded in the neurobiological events that constitute genuine learning.

The theoretical grounding is real. The weights are not.

How much does error trajectory coherence matter relative to retrieval strength decay? Does the answer change by concept type — procedural versus conceptual versus causal? Does it change by learner? The framework says the weights should be per-learner adaptive. It does not say what they are. They have to be learned from deployment data.

Physics and Cancer Biology are generating that data now. The per-learner weight adaptation is the research program. Not the deployed product.

### 2. Which bandit arms work for which learners on which concepts

The bandit arms are fully specified: pedagogical approach (Socratic, direct, analogical, error-targeted), scaffolding level, transfer demand, timing, representation mode, confidence elicitation, misconception injection, predict-then-reveal. The arms exist. The policies for choosing among them do not yet exist at deployment resolution.

The literature gives priors. Spaced retrieval is robust. Interleaving is underused. Predict-then-reveal activates prediction error signaling. These findings are real. "Robust in the population" is not the same as "right for this learner on this concept today." The population finding is where the bandit starts. Where it ends depends on data it hasn't collected yet.

### 3. Whether content adaptation produces durable learning gains or just engagement

The base content library contains Physics rewritten for high school with LLMs, Organic Chemistry for pre-med, Prompt Engineering for Art and Design, sixty-plus subjects adapted by audience and framing. The hypothesis: a student who encounters the clinical framing of cancer biology rather than the biochemical framing will engage more deeply, and that engagement will produce better storage strength, and that storage strength will show up in the retrieval decay signature weeks later.

The hypothesis is a hypothesis. Whether personalization produces better durable learning outcomes — for this learner, on this concept — has not been measured at deployment scale. The Sesame Street research established that pedagogically designed multimedia works. It did not establish which personalization variables matter most. That is what the deployment is designed to find out.

### 4. Whether the gaming-resistance claim holds at scale

The theoretical argument is sound. Manufacturing convincing friction traces across all seven GLP components simultaneously — without performing the underlying cognitive work — is essentially equivalent in cost to performing the work. A student who successfully games error trajectory coherence, retrieval strength decay, and the scaffolding response curve in parallel has, in the only sense that matters, learned the material. The gaming becomes indistinguishable from learning.

The empirical test is pending. The labeled corpus is being built from deployment data. The information gain test has not been run at deployment scale. The framework is published openly precisely so that others can attempt to game it and report back.

### 5. What the ambient context evidence reveals

Medhavy is designed to travel — phone, Canvas, co-op placement, field trip, museum kiosk. The hypothesis: learning evidence from authentic contexts is richer than evidence from controlled platform interactions. Transfer observed while debugging real code on a co-op is not the same as transfer observed on a practice problem.

The instrumentation for this is being designed. Physics and Cancer Biology are platform-bound for now. The co-op integration, the field trip context, the museum kiosk — these are roadmap. Not product.

---

## The Student Consent Architecture

Most educational RCTs face an ethical problem that Medhavy's design dissolves.

The standard randomized controlled trial assigns students to conditions. Some receive the treatment. Some receive the control. Neither group chose. The ethics review asks: is the control condition degraded? If the treatment is believed to be better, is it ethical to withhold it?

Medhavy's students choose their own epsilon.

**The null arm** is not a degraded condition. Turn off the AI entirely. Download the Kindle. Take the content and leave. This is how education worked for five hundred years. A student who downloads the Physics textbook and reads it on the T is using a genuine learning tool that I wrote and made available. The null arm has dignity.

**Low epsilon** means mostly receiving what the system currently believes is best, with occasional exploration. The student who wants to benefit from what the system knows without being a full research participant. Low risk. Low disruption.

**Full RCT** means higher exploration rate and active contribution to the research program. The student who is willing to try things the system hasn't tried before.

**Change settings at any time.** No student is trapped. If the experiment stops working for this learner, they can leave. The data from their sessions before they left is still informative. The act of leaving is itself data.

The student-controlled epsilon is genuinely novel. Most experiments assign treatment. Students who opt into full RCT are motivated participants — their engagement signal is cleaner than a randomly assigned cohort. Students who hold at low epsilon are revealing something about their learning risk tolerance. Students who download the Kindle and leave are providing the honest null arm without contamination.

The traditional RCT treats attrition as a validity threat. This architecture treats it as a measurement.

---

## The Switching Behavior as Signal

The most interesting data the consent architecture generates is not the steady-state choices. It is the switching behavior.

A student who starts at low epsilon and moves to full RCT mid-semester is showing you something — possibly that the system earned their trust, possibly that they became curious about what else it might try. A student who starts engaged and downloads the Kindle at week eight is showing you something else — possibly that something stopped working, possibly that they got what they needed and are done. A student who turns off the AI entirely the week before the exam is showing you their mental model of what the system is for.

None of this is available in a traditional RCT. A traditional RCT treats switching as a compliance problem to be corrected. Medhavy treats switching as signal to be read. The within-learner bandit doesn't need stable treatment assignment — it adapts continuously. The switching behavior is part of the evidence stream.

---

## The Physics and Cancer Biology Pairing

The first two deployments are not accidents.

Physics has clear prerequisite structure. Impulse requires momentum requires force requires Newton's laws. The concept node graph is deep and well-specified. Right and wrong answers are unambiguous. Transfer tasks are well-defined. The GLP error trajectory coherence component should produce clean signal — errors in Physics follow conceptually meaningful developmental paths. A student with genuine partial understanding of momentum responds differently to a partial hint than a student who memorized a formula. The scaffolding response curve is testable in the way that matters: it distinguishes between those two students.

Cancer Biology has different structure. The concepts are more narrative, more interconnected, less hierarchically ordered. The clinical case study mode is the natural instrument — the Warburg Effect means something different in a biochemical explanation than in a clinical oncology context. The Glimmer assignments — creative non-trivial proposals that build into a term project — are designed for exactly this kind of material. The social knowledge texture component of the GLP should produce richer signal here than in Physics, because genuine encounter with clinical ambiguity leaves a different conversational texture than borrowed certainty.

Two different content types. Two different GLP signal profiles. Running simultaneously. The comparison across deployments is not a convenience. It is a designed natural experiment.

---

## What the Running Experiment Is Designed to Find Out

The five unknowns are not permanent. They are the current experimental frontier — what the system is actively trying to learn from data it is now generating.

Which GLP components produce the strongest independent information gain over artifact quality alone? This partially resolves the reward weight question. The highest-gain components should receive the highest weight. Physics will give us the answer for procedural and causal concepts first.

Which bandit arms produce the strongest GLP signal for which concept types? Physics will map procedural and causal concepts. Cancer Biology will map narrative and clinical concepts. The overlap and divergence between those maps is the finding.

Does the content adaptation hypothesis hold? Do students who receive framing matched to their background produce stronger retrieval decay signatures than those who receive generic framing? The base library exists. The matched cohorts are enrolling. The decay signatures will accumulate.

What does the switching behavior reveal about the consent architecture's predictive validity? Does early switching predict final GLP trajectory? Does the pattern of setting changes tell us something about the student's theory of their own learning?

Does the GLP composite score predict subsequent performance better than engagement metrics alone? If GLP adds nothing over behavioral data, the framework needs revision. That is a real possibility and a real test.

Results will be reported in subsequent work as they accumulate. The experiment is visible. The URLs are real.

---

## The Honest Statement

Medhavy knows this: the misallocation problem is real, the platform architecture is sound, the consent design is ethical, the GLP framework is theoretically grounded, the four-layer integration is novel, and the experiment is running.

Medhavy does not yet know this: which weights, which arms, whether the adaptation produces durable learning, whether the gaming-resistance holds at scale, what the ambient context reveals.

The difference between this chapter and every prior platform's disclosure is the location. This is Chapter 5. Not the footnote to Chapter 17, after the TED stage claim has already circulated for three years.

The unknowns are in the argument, not after it. That is the only position consistent with the book this chapter is part of.

The system is working. Whether it is working the way it should — that is what the experiment is for.


---

## A note about AI

This chapter is about what Medhavy does not yet know — about the gaps in the platform's understanding of itself. The model will fill those gaps confidently if asked, which is the exact opposite of what the chapter requires.

Where the model genuinely helps: naming the categories of things a platform like Medhavy typically does not yet know — adoption patterns, edge cases, user behavior under stress, scaling failures. Categories are useful. The model is good at categories.

Where the model does damage: filling specific gaps with confident-sounding answers. A list of *what we do not yet know* that has been smoothed by the model is no longer a list of what you do not yet know. It is a list of what the model thinks platforms like this typically do not know — which is different.

The rule: keep the specific gaps in your own voice. The model can scaffold the categories of unknowns; you have to write the unknowns themselves.

---

## AI Wayback Machine

**Donald Schön** was philosopher whose The Reflective Practitioner (1983) framed expertise as a knowing-in-action that no static codification can fully capture.

**Run this:**

```
Who is Donald Schön, and how does their work connect to what a tool doesn't know yet we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Donald Schön"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Donald Schön's ideas to a specific platform decision.
- Add a constraint: "Answer including criticisms or limits of Donald Schön's framework."

What changes? What gets better? What gets worse?
