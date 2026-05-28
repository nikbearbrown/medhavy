# Chapter 10 — Adding Medhavy to Canvas: What Actually Changes

**One-line capability:** The reader learns what LTI integration means in plain language, what changes for students, instructors, and the institution — and what the institution must actually provide.

---

## Opening

Adding Medhavy to a Canvas deployment is not a technical project. The LTI integration is straightforward. What takes time and requires institutional commitment is the curriculum design layer — specifying what the content map looks like, which concepts get which modes, and what the measurement thresholds are.

That sentence is the chapter, and the reason it deserves its own chapter is that vendor demos invert it. The demo shows the LTI handshake — install the tool, click the button, students appear in the system — and skips the part that takes six weeks of faculty time. The reader who is shopping for Medhavy has probably watched that demo. The reader who is *budgeting* for Medhavy needs to see the part the demo skips.

Start with a deployment that is already on the path. The pharmacology department from Chapter 9, Deployment C: three hundred and twenty students across four sections, three instructors, accreditation pressure, department chair with precommitted authority. The chair has decided to pilot Medhavy in one section first. She has signed the proposal in week zero. She wants to know when she will see the data she signed up for.

The answer is week twelve, and a lot has to happen between now and then. Some of it is fast. Most of it is not.

---

## Core content

### Block 1 — LTI integration in plain language

LTI stands for Learning Tools Interoperability. It is a specification — maintained by a nonprofit called 1EdTech, formerly IMS Global — that lets a learning management system like Canvas talk to an external tool like Medhavy securely and consistently `[verify against 1EdTech's current LTI 1.3 documentation]`.

You do not need to understand LTI to make a budget decision about Medhavy. You need to understand four things it does:

- **Single sign-on.** When a student clicks the Medhavy link in Canvas, she does not log in again. Canvas signs a token that says "this is Maria, she is a student in your Pharmacology 401 course, section 2," Medhavy verifies the signature, and Maria lands inside Medhavy already authenticated. No second password. No second account. This is what "SSO" means in the proposal.
- **Roster sync.** Medhavy receives the class list from Canvas automatically. When a student adds or drops the course, Medhavy knows within hours. The instructor does not maintain a parallel roster.
- **Grade passback.** When Medhavy completes a graded interaction — a Quiz Me session that counts, a Glimmer assignment with a faculty-reviewed score — the grade flows into the Canvas gradebook automatically. The instructor does not transcribe scores between systems. The student sees a unified gradebook.
- **Role awareness.** Canvas tells Medhavy whether the person clicking the link is a student, a teaching assistant, or an instructor. Medhavy shows the appropriate interface — student gets the four modes; instructor gets the GLP dashboard [Humanitarians AI internal framework]. Nothing is exposed to the wrong person.

The technical setup for all of this takes days. Your IT shop installs the Medhavy tool at the Canvas account level once, configures the cryptographic handshake (a key exchange your IT staff has done many times for other tools), and the integration is functionally complete. The protocol is stable; the principle is "Canvas vouches for the user, Medhavy trusts the vouch, grades flow back the same way" `[verify Canvas-specific admin UI against current Instructure documentation — the principles are stable but the interface evolves yearly]`.

That is the easy part.

The hard part is the institutional approval process that runs in parallel with the install. Six to sixteen weeks is normal for a tool of Medhavy's complexity — the variation depends on whether your institution is a small private (faster, sometimes four to six weeks) or a large public system (slower, eight to fourteen weeks). The institutional review touches multiple gates: security review (does the vendor pass your HECVAT vendor questionnaire?), data privacy review (FERPA compliance, plus whatever state laws apply — California's SOPIPA, Illinois's SOPPA, New York's Ed Law 2-d, and roughly forty similar state regimes), accessibility review (WCAG 2.1 AA compliance is increasingly enforced at procurement), and contract review (the standard legal pass through institutional counsel) `[verify current HECVAT version and your institution's specific gates]`.

Your IT shop knows this. The pattern is identical to the integration of any other LTI tool — Top Hat, Lumen, OpenStax, Cengage MindTap, Khanmigo. What is different about Medhavy is not the technical integration. It is what gets built on top.

> **One-line summary:** The LTI install is two days of IT work and eight to sixteen weeks of institutional review running in parallel. The IT work is the cheapest part.

---

### Block 2 — What changes for students

The student-facing change is the four-mode interface replacing or supplementing the standard textbook experience.

Before Medhavy, a student in the pharmacology course reads the AI+1 chapter on Kindle, takes a Canvas quiz at the end of the module, and submits a written assignment. After Medhavy, that same student opens a concept inside Medhavy and encounters a different shape:

- **Ask AI** [Humanitarians AI internal framework] becomes the first encounter for concepts she has no schema for yet — beta blockade, when she has not yet learned what receptor blockade is. The Ask AI session is not a chatbot conversation. It is a guided question-back that pushes her to articulate what she already knows before she receives anything new.
- **Quiz Me** [Humanitarians AI internal framework] becomes a daily habit, not an end-of-module event. Twelve minutes a morning, spaced repetition scheduled by the FSRS algorithm, due-count counter visible at the top of the screen. The habit is the architecture; the algorithm is what makes the habit produce durable retention. After the second week, the student opens Quiz Me out of habit, the way she opens her email.
- **Case Study** [Humanitarians AI internal framework] is the assignment that looks different from anything she has seen before. A pre-written, faculty-reviewed clinical scenario — a forty-three-year-old patient presents with symptoms consistent with three possible diagnoses, two of which contraindicate beta blockade. The AI facilitates discussion but never gives the answer. The student walks into the case with her concepts. She walks out having deployed them under ambiguity, or she walks out aware that she could not.
- **Glimmer** [Humanitarians AI internal framework] is the open-ended assignment with no single correct answer — design a clinical protocol for beta blockade in a novel patient context, defend every decision. The student does not know in week three that her Glimmer work will compile into a term project; the emergent structure is deliberate.

The student does not need to understand any of this architecture. She experiences four buttons that each do something a textbook cannot do. The first day she encounters it she gets a fifteen-minute orientation; by the second week she is using it without thinking about it.

What does *not* change for her: she still logs into Canvas. She still sees her gradebook there. She still submits Canvas assignments for non-Medhavy work. Medhavy is added to her experience, not substituted for the LMS.

---

### Block 3 — What changes for instructors

The instructor-facing change is the GLP dashboard, and the change is more cognitive than technical.

The Canvas gradebook tells the instructor four things per assignment: who submitted, when, what they scored, and whether the score meets her cutoff. The GLP dashboard tells her something different. For each student, for each concept, the dashboard shows the trajectory of the seven friction signals [Humanitarians AI internal framework] — temporal engagement, error trajectory coherence, cross-context transfer, uncertainty calibration, social knowledge texture, retrieval strength decay, and scaffolding response curve.

The instructor does not need to remember all seven signals or what each one indicates. The dashboard summarizes them into a per-concept GLP score and flags the students whose pattern looks like borrowed certainty rather than genuine learning. Maria scored 88% on the Canvas quiz; the GLP dashboard shows her temporal engagement collapsed on the second pass, her retrieval strength is decaying steeply at seven days, and her scaffolding response curve looks more like full-answer dependency than partial-hint activation. Maria's score looks fine. Her learning trace does not.

What the instructor does with that information is the meta-modeling step. She is not asked to trust the GLP score over the Canvas grade. She is asked to combine them — the score from the artifact, the signal from the behavior, and her own professional judgment from teaching and conversation — into a richer picture of where Maria actually is. The dashboard is not making the call. The instructor is. The dashboard surfaces the question.

This is the cognitive change. An instructor who has spent a career treating the gradebook as the source of truth now has a parallel source of truth that sometimes disagrees with the gradebook. The first time the two diverge is uncomfortable. The third or fourth time, it stops being uncomfortable and starts being useful — the instructor learns to read the divergence as information about the student, not as a malfunction of one of the systems.

This is also where the Educause data on faculty adoption becomes relevant. Surveys consistently find that thirty to fifty percent of newly-licensed edtech tools are used minimally or not at all. The technology is in the contract; the dashboard sits unopened. The binding constraint on the chapter's "willing to act" condition is not whether the institution can in principle act — it is whether the specific instructor whose section the data points to will open the dashboard at all.

---

### Block 4 — What the institution must provide

The institution provides three things, in roughly this order of difficulty.

**The concept map.** Medhavy needs to know what concepts are in the course, in what order they are taught, which concepts are prerequisites for which, and which concepts get which modes. This is not a casual exercise. It is the institutional analog of what Wiggins and McTighe called backward design — you specify what counts as learned before you build the loop that measures whether it was learned. For a one-semester pharmacology course covering roughly two hundred concepts, the map typically requires three sessions of three hours each between the lead course instructor and an instructional designer, plus another five to ten hours of asynchronous revision. The instructor is the only person who can name what counts as a concept in her course. The designer's job is to structure her tacit knowledge into a graph Medhavy can use.

**Faculty review for Case Study scenarios.** Case Studies cannot be generated by AI without faculty review, because a plausible-sounding wrong clinical claim in a case scenario is a patient safety risk. The starter set is typically four to eight scenarios per term per course; each scenario takes a faculty author roughly four to six hours to draft and a second faculty reviewer one to two hours to audit. The numbers are not large; the constraint is calendar — getting two faculty members to commit four to eight hours each, before the term begins, is harder than it looks `[verify Medhavy's current scenario-authoring workflow against vendor documentation]`. Pharmacology programs that have done case-based learning before know this rhythm. Programs that have not done it before underestimate it the first time.

**Willingness to act.** Chapter 9 named this as the Q3 condition. Chapter 10 names what it actually looks like in operation. The institution needs a person — the department chair, the curriculum committee chair, the program director — whose calendar time is reserved for the redesign step that happens when the dashboard flags a section or a concept as underperforming. The willingness has to exist before the data does. Buying Medhavy and figuring out the redesign owner later is the documented institutional failure mode that produces dashboards nobody opens.

These three are the curriculum design layer the vendor demo elides. They are not optional. They are the actual work.

---

### Block 5 — What Medhavy does not require from the institution

Equal in importance to what the institution must provide is what it does not.

The institution does not need to understand the contextual bandit. The algorithm is the vendor's responsibility; the institution's responsibility is the inputs (concept map, cases, willingness to act) and the outputs (interpretation of GLP signals). The math is invisible to the user the same way the math behind Canvas's enrollment management is invisible to the registrar.

The institution does not need to retrain its faculty in pedagogy. The four modes are pedagogical instruments; the institution does not need to teach its instructors what spaced retrieval is or why the testing effect works. The instructor uses the dashboard. The dashboard is built on the pedagogy. The instructor benefits from the pedagogy without being asked to become an expert in it.

The institution does not need to replace Canvas. This is the most common worry and the easiest to dispatch. Medhavy lives inside Canvas. Canvas remains the LMS. The gradebook is still Canvas's gradebook. Course administration — announcements, modules, discussion boards, calendar, grade exports for registrar reporting — is still Canvas. Medhavy adds a layer on top of one component of the course (the textbook-and-assignments component) and does not touch the rest.

And the institution does not need to commit to using Medhavy across the program before piloting it on one course. The right adoption shape for most institutions is one course, one term, real measurement, then expand if the measurement justifies it. The technology supports per-course adoption. The chapter's earlier framing about institutional capacity also supports it — start where Q1 through Q3 are most clearly yes, prove the loop closes, then scale.

The Canadian researcher Tony Bates spent decades documenting what institutions do and do not need to provide when they adopt educational technology — his book *Teaching in a Digital Age* is open-licensed and worth a look. His central observation, repeated across decades of work, was that the technology is the easy part and the institutional change is the hard part. Chapter 10 is one chapter; Bates wrote a career on the same observation. The Medhavy-specific version of his finding is in the contrast between Blocks 4 and 5: what the institution must provide is not technical, and what the institution must accept is not pedagogical retraining.

---

## Worked example — pharmacology, six-week setup, week-eight payoff

The pharmacology department from Chapter 9's Deployment C is the worked example. The chair has decided to pilot Medhavy in one section of the four — eighty students, one instructor (the chair herself, deliberately, because she wanted the early adoption headache to land on her own calendar before her two colleagues had to absorb it).

**Week zero.** The chair signs the proposal. She sends the standard procurement packet to the institutional review office: HECVAT response from Medhavy, FERPA addendum, state-data-privacy attestations for the two states where her institution serves out-of-state students, WCAG 2.1 AA documentation, accessibility VPAT, contract draft.

**Weeks one through two — IT track.** Her IT shop installs Medhavy as an LTI 1.3 external tool at the Canvas account level. The cryptographic handshake takes one afternoon. The integration is technically live by the end of week two, even though no students will use it for another ten weeks.

**Weeks one through ten — institutional review track.** Security review, privacy review, accessibility review, contract review. These run in parallel. Her institution is a mid-size public university; the security review takes six weeks; the privacy review takes four weeks (one extra because of the data-residency questions); the accessibility review takes three weeks; the contract goes through legal in two weeks. The pacing item is security review. By week ten, all gates are cleared.

**Weeks three through eight — concept map.** The chair meets with the instructional designer for three sessions of three hours each — week three, week four, week six. She maps the first six weeks of the pharmacology curriculum to roughly seventy-five concepts. She names the prerequisite graph: receptor pharmacology before drug class behavior; pharmacokinetics before dosing decisions. She assigns modes — Ask AI as the entry mode for unfamiliar concepts, Quiz Me as the daily habit for receptor names and drug classifications, Case Study and Glimmer reserved for the second half of the term when students have built enough schema to deploy it. Between sessions she revises asynchronously, roughly four hours over the six weeks. The instructional designer formalizes the map into Medhavy's content structure.

**Weeks six through eight — case study authoring.** The chair drafts four starter Case Studies, four hours each. Her colleague, the most senior pharmacology faculty member, reviews each one, two hours each. Two of the four cases come back with revisions — one for a plausible-sounding but slightly outdated dosing range, one for a scenario that was ambiguous in the wrong way. The revised cases are finalized by end of week eight.

**Week eleven — student onboarding.** Students return to the course in week eleven (the spring term began the week before in Canvas; Medhavy was activated for them in week eleven). The chair spends fifteen minutes in the first lab walking students through the four modes — what Ask AI does, what Quiz Me does, what to expect from the first Case Study. Students leave the lab with access to the tool. Quiz Me daily habits start forming by the end of week eleven.

**Week twelve — first data.** Two weeks of student use produces enough signal for the GLP dashboard to populate. By end of week twelve, the chair sees per-student trajectories for the first set of concepts. She sees patterns the Canvas gradebook had not shown her: one student with high Canvas quiz scores but rapidly decaying retrieval strength, three students whose temporal engagement looks like genuine processing on harder concepts and like skimming on easier ones, one student whose scaffolding response curve suggests genuine partial understanding (a partial hint activates a complete answer — the chapter eight signal).

The chair did not know that any of this was visible until the end of week twelve. The Canvas gradebook had told her these students were performing at 84 to 92 percent. The dashboard tells her something different. The willingness to act on the difference is what the next twelve weeks will test.

Total institutional time across all tracks: roughly eighty hours of faculty time (chair plus reviewer), thirty hours of instructional designer time, six hours of IT time, twenty hours of institutional review across security, privacy, accessibility, and legal. The license fee is the smallest line. The faculty time is the largest. The willingness to act has no line item and is the gating condition.

---

## AI Wayback marginal callout — Tony Bates

There is a Canadian researcher named **Tony Bates** who has spent four decades documenting a single observation: in educational technology adoption, the technology is the easy part and the institutional change is the hard part. His 2015 book *Teaching in a Digital Age*, currently in its third edition and freely available under a Creative Commons license, is structured around that observation. Bates worked at the UK Open University, then Athabasca University in Canada, then the University of British Columbia, and across those institutions he watched the same pattern: software arrives, integrates technically within weeks, and then sits in tension with institutional habits for years. His most useful contribution for a reader of this chapter is his insistence that the cost of educational technology be calculated in faculty hours and institutional change capacity, not licenses. The chapter's Block 4 — what the institution must provide — is the Medhavy-specific application of what Bates spent his career documenting. The chapter is a paragraph. Bates wrote a book. The book is free.

---

## Exercises

**Exercise 1 (Apply) — Identify your most likely early adopter.**
Pick the single faculty member in your program most likely to volunteer for a Medhavy pilot. Write three sentences describing why — what about her course, her teaching style, or her institutional position makes her the right first volunteer. Then write what she would need from you: the calendar time you would need to clear, the instructional designer support you would need to staff, the political cover you would need to provide. If you cannot name a specific person, that is information about Q3.

**Exercise 2 (Apply) — Map your institutional approval process.**
Sketch the approval gates a new LTI tool would go through at your institution. Who runs security review, and what is their typical turnaround? Who runs privacy review, and which state laws apply to your student population? Who runs accessibility review? Who signs the contract? What does each gate's queue look like right now? The output is a timeline estimate from "decision to add" to "approval complete." Compare it to the pharmacology worked example's ten-week pacing.

**Exercise 3 (Evaluate) — Is the realistic timeline acceptable?**
Take your timeline from Exercise 2 and add the parallel curriculum-design timeline (six to ten weeks for the concept map and case authoring, depending on your faculty's case-based learning experience). From the day the decision is made to the day the first student is in the loop, what is the realistic total? Is that timeline acceptable given the deployment need? If the deployment is accreditation-driven and the next review is in nine months, twelve weeks of setup is fine. If the deployment is driven by a problem that needs solving by the end of this term, the answer may be that the timeline does not fit and the right move is to start the institutional review now and adopt next term.

---

## Common misconceptions

**"LTI is hard."** It is not. LTI 1.3 has been the production standard since 2019 and your IT shop has done this integration many times. If your IT shop tells you LTI is hard, they are either describing the institutional approval gates (which are real and not LTI's fault) or they have not done LTI 1.3 yet, which they will need to. The protocol is stable.

**"If the LTI works, we are done."** No. The LTI install is two days. The work that produces value is the concept map, the case authoring, and the willingness to act. The LTI is the doorway. The room is what matters.

**"Concept maps can be generated by AI."** Partially. An AI can draft a concept map from a syllabus. The draft must be reviewed line-by-line by the course instructor, and the review takes nearly as long as authoring would have taken. Instructional designers who have tried the AI-draft route report that the review burden is roughly seventy percent of the from-scratch time. Useful, but not the labor-saver vendors imply.

**"We can skip faculty review on Case Studies because the AI generates them."** No. A plausible-sounding wrong clinical claim in a Case Study is a patient safety risk. The faculty review gate is not optional and is not bureaucratic — it is the architecture's safety case. Vendors who suggest otherwise are selling a different product.

**"Medhavy will replace Canvas."** It will not. It lives inside Canvas. Canvas remains your LMS. The gradebook is still Canvas's. Course administration is still Canvas's. Medhavy is a layer; it is not a replacement.

**"Twelve weeks is too long."** It might be, for your situation. That is the point of Exercise 3. If twelve weeks is too long, the institutional review process is the rate-limiting step, not Medhavy. Start the review process now and adopt next term — or accept that this is not the right adoption window.

---

## What would change my mind

A reader who has worked through this chapter may reasonably wonder under what conditions the institutional-time estimates would shift enough to matter.

Two conditions. First, if AI-assisted concept-map drafting reached a quality threshold where faculty review of a generated map took twenty percent of authoring time rather than seventy, the concept-map step would shrink from three sessions of three hours to roughly one session of two hours with revisions. The total institutional time would drop by a third, and Q1's scale threshold from Chapter 9 might soften correspondingly. There is published debate about whether AI tools can reach that quality; the experienced instructional designers I have read are skeptical, but the question is empirical and not settled. Second, if institutional review processes for AI-enabled tools became standardized across higher education — a "HECVAT-AI" extension widely adopted, common state-law compliance frameworks, shared accessibility attestations — the eight-to-sixteen-week parallel review track could compress to four weeks. Educause is working in this direction. If it succeeds, the chapter's pacing changes. Neither has happened yet. If either happens, this chapter is the one that gets rewritten.

---

## Still puzzling

- The faculty time estimates in Block 4 — three sessions of three hours for concept map, four to six hours per Case Study — are drawn from comparable case-based learning programs and from Educause's faculty workload surveys. Medhavy-specific data does not yet exist. What would tighten these estimates from heuristic to empirical?
- The chapter assumes the lead course instructor is the right partner for the concept map. In some departments, that role belongs to an instructional designer with subject knowledge, or to a senior faculty member who no longer teaches the course. Who is the right partner when the lead instructor is junior, overworked, or only in the role for one term?
- The "instructor as meta-model" cognitive change in Block 3 is real and uncomfortable for instructors who have built their professional identity around the gradebook. What support do instructors need to absorb that change, beyond the dashboard interface?
- The chapter treats willingness to act as a precommitment. But willingness is not static — chairs leave, accreditation pressure shifts, faculty turnover. What is the right cadence for re-confirming Q3 during a multi-year deployment?

---

## Bridge

You have the framework. You have the implementation picture. Chapter 11 is the decision.
