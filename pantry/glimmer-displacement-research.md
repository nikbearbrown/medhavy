# Glimmer — AI Displacement, Studio vs. Engineering Pedagogy, and the Pseudocode Problem

*Research note for Medhavy's "Glimmer" mode. Companion to `glimmer-research.md` (the construct-mapping note: GLA, EI, ISP, PBL, emergent-portfolio, AI feedback, anxiety failure modes). Compiled 2026-05-17. Author: research subagent for Nik Bear Brown. The companion note covers what Glimmer **is** in the pedagogy literature. This note covers **why** Glimmer is the right bet now — the theoretical argument that fully-specifiable tasks are losing educational value, the empirical record of studio-style pedagogy in engineering, and the documented failure mode (the pseudocode problem) that Glimmer's scaffolding sequence must address.*

> **Reader's compass.** Three new angles, in this order: (1) the AI-displacement-of-educational-value argument — recent, theoretical, peer-reviewed lit lags by 1–3 years; (2) the studio-vs-engineering field divide — Schön, Cross, the Carnegie engineering studies, what happens when critique-based assessment is transplanted into STEM; (3) the pseudocode problem — students who execute pseudocode flawlessly but cannot formulate an approach; scaffolding-fading research, problem-finding-vs-problem-solving, expertise-reversal, the discovery-vs-direct-instruction debate. Brief integration sections at the end bridge to the companion note. Rubric-validation pass closes. Citations consolidated with tags at the bottom.

---

## 0. The argument restated, so the evidence has a target

The book's working claim, in one sentence:

> **If a task can be fully specified in advance, AI can now execute it; therefore the educational value of practicing fully-specifiable tasks is declining rapidly, and the tasks that retain educational value are those requiring judgment, defensibility, and novel problem framing.**

This is a **2024+ argument**. The peer-reviewed literature has not had time to test, refute, or canonize it. The closest evidence base is (a) labor-economics task-displacement theory (Acemoglu & Restrepo; Autor; Frey & Osborne) updated by post-LLM occupation exposure studies (Eloundou et al.; Brynjolfsson, Li & Raymond) and (b) a much older art-school / design-studio tradition that has been quietly running the experiment of "teach judgment under ambiguity rather than execution of specifiable procedure" for a hundred years. The transposition from "AI displaces specifiable labor in firms" to "AI displaces the educational value of specifiable assignments in schools" is the move the book is making. **It is a working hypothesis with an evidence-shaped hole at the center.** The honest chapter says so. The honest research note names what is sitting around the edges of the hole and what is not yet sitting where the hole is.

Three tags structure this note's citations:

- `[AI-displacement]` — labor-displacement theory and its educational translation.
- `[art-design-pedagogy]` — Schön, Cross, Lawson, design studio, critique, transplant to engineering.
- `[scaffolding-fading]` — Pea, van de Pol, Puntambekar, the pseudocode problem.
- `[problem-framing]` — Getzels & Csikszentmihalyi, Chi/Voss novice-expert work on problem representation.
- `[discovery-vs-direct-instruction]` — Kirschner/Sweller/Clark, Hmelo-Silver response.
- `[generative-assignment]` — bridges to companion note.
- `[foundational-theory]` — Klein, Cyert & March, naturalistic decision-making.
- `[failure-mode]` — anxiety/avoidance/superficial-compliance under USMLE-trained learners.

---

## 1. The AI displacement argument

### 1.1 The task-not-occupation move — Autor 2015 `[AI-displacement]`

Autor, David H. 2015. "Why Are There Still So Many Jobs? The History and Future of Workplace Automation." *Journal of Economic Perspectives* 29 (3): 3–30. ([DOI: 10.1257/jep.29.3.3](https://www.aeaweb.org/articles?id=10.1257/jep.29.3.3))

- **The frame.** Autor's central move was to stop asking "will this occupation be automated?" and start asking "which tasks within this occupation will be automated, and which tasks will be complemented (made more valuable) by automation?" The unit of analysis is the task, not the job. A radiologist's job is a bundle of tasks; image classification is one task; explaining the implication to a worried patient is another; consulting on which scan to order is another. Automation pressure falls on the tasks individually, not on the bundle uniformly.
- **The routine-task hypothesis.** Tasks that are routine — codifiable in a clear set of rules, with predictable inputs and verifiable outputs — are the tasks machines do first. Non-routine cognitive tasks (judgment under ambiguity, problem framing, persuasion, novel synthesis) and non-routine manual tasks (situational physical work, eldercare) have, historically, resisted automation. Autor's 2015 claim was that the routine-cognitive boundary was the one being eaten, but the non-routine-cognitive boundary was holding.
- **What Autor explicitly did not predict.** The post-2022 LLM era. Autor was writing about narrow ML and rule-based automation. His task taxonomy is the scaffolding the post-LLM updates (§1.3–§1.4) hang on, but his specific predictions about *which* cognitive tasks would resist automation were calibrated to a different machine.
- **For Medhavy.** The educational translation Autor enables: if the educational value of a task is correlated with the labor-market value of that task, and automation collapses the labor-market value of routine-cognitive tasks, then the educational value of *practicing* routine-cognitive tasks should also collapse — eventually. The "eventually" is the lag the chapter must name. Schools are slow to change; jobs change faster; the assignment that prepared a student well in 2018 may not prepare a student well in 2028. The educational value of an assignment is not stable across automation regimes.

### 1.2 The task-content-of-occupations machinery — Acemoglu & Restrepo 2022 `[AI-displacement]`

Acemoglu, Daron, and Pascual Restrepo. 2022. "Tasks, Automation, and the Rise in U.S. Wage Inequality." *Econometrica* 90 (5): 1973–2016. ([DOI: 10.3982/ECTA19815](https://www.econometricsociety.org/publications/econometrica/2022/09/01/Tasks-Automation-and-the-Rise-in-U-S-Wage-Inequality))

- **The contribution.** Acemoglu & Restrepo formalize Autor's intuition: occupations are baskets of tasks; automation reallocates tasks between humans and machines; wages adjust based on the residual non-automatable task share. They estimate that **50–70% of the increase in U.S. wage inequality between 1980 and 2016** can be attributed to task displacement of routine-task occupations. This is a strong empirical claim — the task-displacement model fits the wage data better than competing accounts (skill-biased technical change in the original Katz-Murphy form, China shock alone, decline-of-unions alone).
- **The mechanism that matters for Medhavy.** A & R are explicit that **the educational system tracks the task structure of the labor market with a multi-decade lag**. Workers trained to perform tasks that have been automated do not retrain instantly; institutions of higher education do not redesign curricula instantly; the mismatch produces a wage premium for the un-displaced tasks and a wage depression for the displaced ones. *The educational value of a curriculum is partly the labor-market value of the tasks it trains.*
- **The honest gap.** A & R's 2022 data ends before the LLM shock. Their model predicts the *pattern* of displacement but not its post-2022 *acceleration*. The chapter should cite A & R for the framework (tasks displace; wages follow; education lags) and Eloundou et al. (§1.3) for the LLM-specific empirical update.

### 1.3 The LLM occupation-exposure study — Eloundou et al. 2023 `[AI-displacement]`

Eloundou, Tyna, Sam Manning, Pamela Mishkin, and Daniel Rock. 2023. "GPTs are GPTs: An Early Look at the Labor Market Impact Potential of Large Language Models." OpenAI working paper / arXiv preprint 2303.10130. ([arXiv: 2303.10130](https://arxiv.org/abs/2303.10130))

- **Method.** Eloundou and colleagues used the O\*NET task taxonomy (over 19,000 tasks across U.S. occupations) and rated each task on whether a current LLM could reduce the time to complete the task by at least 50%. Two rating regimes: human raters and GPT-4 itself as rater (with strong inter-rater agreement reported). They also rated whether *LLM-powered software* (LLMs plus simple tooling) could reduce task time.
- **Headline findings.**
  - About **80% of the U.S. workforce** has at least 10% of their tasks exposed to LLM time-reduction. About 19% of workers have at least 50% of their tasks exposed. Exposure is heavily concentrated in higher-wage, college-degree-requiring occupations.
  - **The occupations most exposed:** mathematicians, tax preparers, financial analysts, writers, web designers, accountants, journalists, paralegals, technical writers, interpreters. The occupations *least* exposed: skilled manual trades (cooks, masons, plumbers, equipment operators).
  - **The reversal of the prior automation pattern.** Frey & Osborne 2013/2017 had predicted that routine manual labor would be automated first; Eloundou et al. show LLMs invert this — cognitive routine labor is being eaten first.
- **For Medhavy.** This is the closest empirical anchor for the displacement claim. The educational consequence: students entering 2026 finance, accounting, legal, writing, or analyst training are preparing for occupations where 30–50% of the current task load has 2× LLM speedup available. The educational value of practicing those tasks at human speed is — at minimum — *changing*, and the direction is down.
- **Caveats Eloundou et al. acknowledge.** Exposure is not displacement. Time-reduction is not job-elimination. Complementarity (humans + LLMs more productive than either alone) is the modal pattern in their data. The paper is careful; the headlines about it have been less careful.
- **The educational translation Eloundou et al. do not make.** They are an economics paper, not an education paper. The translation — "if the labor task is automatable, the practice version of the task is losing educational value" — is the chapter's move, supported by Eloundou et al. for the labor side, unsupported on the education side. *This is the empirical gap to name.*

### 1.4 The productivity-at-work field experiments — Brynjolfsson, Li & Raymond 2023 `[AI-displacement]`

Brynjolfsson, Erik, Danielle Li, and Lindsey Raymond. 2023. "Generative AI at Work." NBER Working Paper 31161. ([NBER: w31161](https://www.nber.org/papers/w31161))

- **Design.** A staggered rollout of a conversational AI assistant to 5,179 customer-support agents at a single Fortune 500 firm, with 3 million chat conversations as the unit of observation. The natural-experiment design exploits which agents got access to the tool when.
- **Headline.** **14% increase in issues resolved per hour on average.** Effects concentrated heavily among **novice and low-skilled workers** — they gained 35%; high-skilled workers gained little or nothing. The tool encoded the tacit knowledge of the top performers and made it available to everyone else. *AI compressed the skill distribution.*
- **For Medhavy.** Two implications, both load-bearing for the displacement argument:
  - **The "AI raises the floor more than the ceiling" pattern** is a specific prediction about which educational tasks lose value first. Tasks that distinguished the strong performer from the weak performer get compressed by AI; the *floor* rises. The educational value of teaching the floor declines. The educational value of teaching what the *ceiling* requires (judgment, framing, decisions the AI cannot make) holds or rises.
  - **Tacit knowledge becomes legible.** The AI in Brynjolfsson et al. worked by capturing the patterns of top performers and surfacing them to novices. If this generalizes — and the Microsoft Copilot field studies and McKinsey 2024 case studies suggest a similar pattern, though with publication-bias caveats — then a substantial chunk of what schooling used to do (acculturate novices into the tacit norms of professional work through years of practice) is now done faster by AI tooling. The educational value of slow tacit-knowledge acquisition through repetition declines.
- **Caveat.** This is one firm, one job category, one tool, one year. The replication and generalization studies have not yet run. The chapter should cite as illustrative, not definitive.

### 1.5 Frey & Osborne 2013/2017 — the predecessor study and what it got right and wrong `[AI-displacement]`

Frey, Carl Benedikt, and Michael A. Osborne. 2017. "The Future of Employment: How Susceptible Are Jobs to Computerisation?" *Technological Forecasting and Social Change* 114: 254–280. (Originally circulated as Oxford Martin School working paper 2013.) ([DOI: 10.1016/j.techfore.2016.08.019](https://www.sciencedirect.com/science/article/abs/pii/S0040162516302244))

- **The famous number.** 47% of U.S. employment was at "high risk" of computerisation within one to two decades.
- **What it got right.** The methodology — rate each occupation on a set of automation-bottleneck dimensions (perception/manipulation, creative intelligence, social intelligence) — established the template all subsequent occupation-exposure studies (including Eloundou et al.) build on. The general direction of the prediction (routine cognitive work is more exposed than non-routine cognitive work) was correct.
- **What it got wrong (or had no way of knowing).** The specific timing was off — the 2013 predictions assumed automation pressure would come from narrow ML and robotics. The actual 2022+ LLM shock came from a different direction and hit different tasks first (writing, analysis, code — not driving and warehouse work, which has stayed stubbornly human-shaped). Several occupations Frey & Osborne flagged as low-risk (writers, paralegals) were among the most LLM-exposed in Eloundou et al.
- **For Medhavy.** Cite for: (a) the methodological lineage; (b) the cautionary epistemics — task-displacement predictions on a decade horizon are reliably *directionally* right and reliably *specifically* wrong about which jobs go first. The chapter should claim the *direction* of the displacement argument without claiming the *specific tasks* it names will be exactly the ones displaced first.

### 1.6 Industry reports — PwC, McKinsey, BCG `[AI-displacement]` `[vendor]`

- **PwC 2025 Global AI Jobs Barometer.** Reports that occupations highly exposed to AI saw productivity growth at 4× the rate of low-exposure occupations between 2022 and 2024. Wage premiums for AI-skill-complementary roles are rising. ([PwC 2025 report](https://www.pwc.com/gx/en/issues/artificial-intelligence/ai-jobs-barometer.html) `[verify exact 2025 publication date and figures]`)
- **McKinsey 2023, 2024 generative AI reports.** Estimate $2.6–4.4 trillion of annual value addition from generative AI across 63 use cases, with banking, technology, life sciences, and retail capturing the largest share. The 2024 update reports that 65% of organizations regularly use generative AI in at least one function, double the prior year. ([McKinsey "The state of AI 2024"](https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai)).
- **Caveat — these are vendor / consultancy publications.** They are useful as signal that the productivity effect is now legible to large firms; they are not peer-reviewed evidence. Tag `[vendor]` in the chapter and never cite as primary evidence for a contested claim. Use them, if at all, to corroborate the academic literature's direction, not to substitute for it.

### 1.7 The educational-value translation — what the lit does and does not yet say `[AI-displacement]`

The chapter's central claim — that AI displacement of labor implies educational devaluation of fully-specifiable assignments — is not yet directly supported by peer-reviewed empirical work in education. The closest gestures in the right direction:

- **OECD's 2023 *Is Education Losing the Race with Technology?* (Working Paper).** Argues that the gap between educational task content and labor-market task content is widening post-LLM and that curricula optimized for "knowledge work" tasks as practiced in 2015 are now training students for tasks under active automation pressure. The recommendation is a curricular shift toward "AI-complementary skills" — judgment, creativity, social intelligence, complex problem-solving. ([OECD Education Working Paper, 2023](https://www.oecd.org/education/) `[verify exact title, author, and publication number]`)
- **Bastani et al. 2025 (preprint, Wharton)** "Generative AI Can Harm Learning." Reports an experiment in which students with access to GPT-4 during practice problems performed better than the control during practice but **worse than the control on an exam without access**. The displacement worry made concrete in an experiment: when students offload the cognitive work that practice is supposed to build, the practice no longer builds it. ([SSRN preprint](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4895486) `[verify]`)
- **Stadler et al. 2024 / Krupp et al. 2024 / and adjacent 2024–2025 ChatGPT-in-classroom studies.** Mixed findings; most report short-term performance gains in AI-supported conditions, with concerns about durable learning, transfer, and metacognitive accuracy unresolved. The field is moving fast and most published work is one-semester one-cohort one-task; nothing yet has the design to settle the educational-value-displacement claim.
- **Discussions in *Educational Researcher* and *Computers & Education* (2023–2025).** A growing essay literature framing the question in terms similar to the chapter's. None is yet an empirical answer.

**The honest sentence.** *The peer-reviewed empirical literature has not yet caught up with the educational-displacement claim. Labor economics gives strong evidence that AI is displacing specifiable cognitive tasks at scale; education research has not yet shown that the educational value of practicing those tasks has declined commensurately. The chapter's claim is a theoretical bet supported by adjacent evidence, not a settled empirical finding.* The reader is owed this sentence.

### 1.8 The residual category — judgment under ambiguity `[foundational-theory]` `[AI-displacement]`

If "fully-specifiable, AI can do it" is the displacement edge, what is the residual category that retains educational value? The literature on professional expertise gives several names for the same shape.

- **Klein, Gary. 1998.** *Sources of Power: How People Make Decisions.* MIT Press. Klein's naturalistic-decision-making research with firefighters, nurses, military commanders, ICU staff. The central finding: in real high-stakes work, experts do not enumerate alternatives and compute optimal choices; they recognize the situation as a member of a class they have seen before and execute a satisficing action. *Recognition-primed decision-making.* The expertise that matters is the ability to read the ambiguous situation, not the ability to compute the answer given a clear specification.
- **Klein 2010** *Streetlights and Shadows: Searching for the Keys to Adaptive Decision Making.* MIT Press. Klein's update: classical decision theory (and, by extension, fully-specifiable algorithmic decisions) operate "under the streetlight" — where information is clean and rules apply. Adaptive decision-making operates in the shadows — where information is incomplete, the rules don't fit, and judgment is required. The shadows are where human expertise has its comparative advantage and where AI, even now, struggles. **The Glimmer is asking students to operate in the shadows, deliberately.**
- **Cyert, Richard M., and James G. March. 1963.** *A Behavioral Theory of the Firm.* Prentice-Hall. The classical source for *satisficing* (Simon 1956): organizations facing ambiguity do not optimize; they search for acceptable solutions, accept them, and move on. The cognitive labor in real decision-making is the *framing of acceptability*, not the optimization given a frame. Specifying the problem is the work; once specified, the solution often follows.
- **Schön 1983** (covered in detail in §2) — reflective practice as the residual mode of professional knowledge that resists codification.
- **Recent AI-adjacent work.**
  - **Mollick, Ethan. 2024.** *Co-Intelligence: Living and Working with AI.* Portfolio. Mollick's "jagged frontier" frame: AI is shockingly good at some tasks within a discipline and shockingly bad at adjacent-seeming ones, with the boundary unpredictable from the outside. The educational consequence: students need to develop *taste* for which tasks the AI does well and which it confabulates on — a judgment skill that is itself ill-structured.
  - **Dell'Acqua et al. 2023** (Harvard Business School working paper, "Navigating the Jagged Technological Frontier"). BCG consultants with GPT-4 access outperformed controls on tasks inside the AI's frontier and *underperformed* controls on tasks outside the frontier (because they trusted the AI's confident-but-wrong output). The expertise that mattered was knowing when to trust the AI — a meta-judgment that the consultants who developed it (the "centaur" mode) outperformed those who delegated wholesale (the "cyborg" mode). ([HBS WP](https://www.hbs.edu/faculty/Pages/item.aspx?num=64700) `[verify]`)
- **For Medhavy.** The residual category — judgment under ambiguity, satisficing, framing, knowing when to trust — is the category Glimmer's rubric (WHY / usefulness / mechanism / defensibility / specificity) targets directly. *The Glimmer is the assignment shape for the work that does not have a fully-specified answer to delegate to AI.* The displacement argument and the Glimmer rubric are tied at their roots: each is about what survives automation.

### 1.9 The strongest one-sentence read on the displacement question `[AI-displacement]`

> **The peer-reviewed labor literature (Acemoglu & Restrepo; Eloundou et al.; Brynjolfsson, Li & Raymond) supports that AI is displacing specifiable cognitive tasks at scale and compressing the skill distribution by raising the novice floor faster than the expert ceiling; the educational translation — that practicing fully-specifiable tasks therefore loses educational value while practicing judgment under ambiguity retains it — is a theoretically defensible 2024+ working hypothesis with adjacent but not yet direct empirical support in the education literature.**

That sentence is the honest one. Anything stronger overclaims the educational evidence; anything weaker fails to credit the labor evidence.

---

## 2. The art-school vs. engineering field divide

### 2.1 Schön 1983 — reflective practice and the studio `[art-design-pedagogy]`

Schön, Donald A. 1983. *The Reflective Practitioner: How Professionals Think in Action.* New York: Basic Books. (Companion volume: Schön 1987, *Educating the Reflective Practitioner.* San Francisco: Jossey-Bass.)

- **The diagnosis.** Schön's argument begins as a critique of what he calls **technical rationality** — the model of professional knowledge that treats practice as the application of scientific theory to predefined problems. Technical rationality is what engineering, medical, and management curricula teach. The problem: real professional practice rarely encounters predefined problems. The actual professional work is **problem-setting** (framing what kind of problem this is) before problem-solving. Schön's word for this is *reflection-in-action*.
- **The studio as model.** Schön spent extended time observing the architecture design studio at MIT. What he found was a pedagogical mode the engineering schools did not have: a master designer (the studio critic) working alongside students on real, ill-structured design problems, demonstrating the framing move, the back-talk between drawing and intention, the willingness to abandon a frame and start over. The studio teaches what technical rationality cannot teach because technical rationality presupposes a frame the student is just supposed to apply.
- **The mechanism — three moves Schön names.** *Knowing-in-action* (the tacit performance of competent practice). *Reflection-in-action* (the in-the-moment surfacing of a problem and reconsideration of approach). *Reflection-on-action* (the after-the-fact reconstruction of what just happened and why). Studio critique teaches all three by making them visible. Lecture-and-problem-set teaches only the first, and only the kind of first that follows from a frame already given.
- **For Medhavy.** Glimmer's rubric — especially defensibility — asks the student to make their *framing* visible. "Why did you treat this as a protocol-design problem rather than a workflow-redesign problem?" is a reflection-in-action prompt; the AI reviewer surfacing weakness is the studio critic's move. The Glimmer is *importing the studio critique pattern into medical/engineering education at the assignment level*. This is the most precise theoretical identity for what Glimmer is doing, and Schön is the canonical reference.

### 2.2 Cross 2006 — designerly ways of knowing `[art-design-pedagogy]`

Cross, Nigel. 2006. *Designerly Ways of Knowing.* London: Springer. (Earlier essays collected; original 1982 essay "Designerly Ways of Knowing" in *Design Studies* 3 (4): 221–227.)

- **The argument.** Designers do not think like scientists; they do not think like artists either. They have their own cognitive mode — *solution-led* rather than *problem-led* — characterized by working on the problem and the solution simultaneously, by treating ill-defined problems as natural, by reasoning through external representations (sketches, prototypes), and by tolerating ambiguity as a feature rather than a defect.
- **The four characteristics Cross names.**
  1. Designers tackle "ill-defined" problems.
  2. Designers' mode of problem-solving is "solution-focused" — they explore possible solutions to learn about the problem.
  3. Designers' mode of thinking is "constructive" — building artifacts that embody partial understanding.
  4. Designers use "codes" — drawings, models, prototypes — that translate abstract requirements into concrete objects.
- **The empirical record.** Cross drew on protocol studies (think-aloud studies of designers at work) by Suwa, Cross, Akin, and others. Across studies, the consistent pattern is that experienced designers spend more time on problem framing than novices and less time on detail elaboration. The expert does not jump to a solution faster; the expert specifies the problem more carefully first. *Expertise in design is expertise in problem framing.*
- **For Medhavy.** The translation to medical and engineering education is direct. A medical student trained on USMLE questions has been trained almost entirely on solution-led work *given a fully-specified problem*. The clinical reality — patient walks in, presenting complaint vague, history incomplete, history-taking itself a choice that shapes what comes next — is designerly work in Cross's sense. The pedagogy that produces excellent USMLE scores does not produce excellent clinical framing. The Glimmer is one mechanism to bridge that gap; Cross is the theorist who names the gap.

### 2.3 Lawson 2005 — how designers think `[art-design-pedagogy]`

Lawson, Bryan. 2005. *How Designers Think: The Design Process Demystified.* 4th ed. Oxford: Architectural Press. (First edition 1980; the 2005 fourth edition is the standard reference.)

- **The contribution.** Lawson is the empirical complement to Cross. Across decades of studies (architects, engineers, product designers, fashion designers, music composers), Lawson documents the actual cognitive moves designers make and shows they are largely *not* the linear analyze-synthesize-evaluate model that engineering education had institutionalized.
- **The five-level model Lawson proposes.** Designers operate simultaneously at five levels — assembling/spatial, environmental, aesthetic, structural, and constructional — and the design move is to *integrate constraints across levels* rather than to satisfy them sequentially. Engineering education tends to teach each level in isolation and then leave the integration as the student's silent problem.
- **The framing-vs-solving balance.** Lawson reports time-share studies: experienced designers allocate 40–60% of working time to framing, 25–35% to solution generation, and 15–25% to evaluation. Novice designers invert this — most time on solution generation, very little on framing. *The educational consequence: if a curriculum only assesses solutions to pre-framed problems, it cannot teach the framing move that is most of the expert's working time.*
- **For Medhavy.** Cite Lawson for the empirical claim that framing is the dominant mode of expert design cognition and the under-taught mode in engineering education. Glimmer's "WHY" and "specificity" rubric dimensions correspond directly to framing moves.

### 2.4 The crit — Webster 2005, 2008 `[art-design-pedagogy]` `[failure-mode]`

- **Webster, Helena. 2005.** "The Architectural Review: A Study of Ritual, Acculturation and Reproduction in Architectural Education." *Arts and Humanities in Higher Education* 4 (3): 265–282.
- **Webster, Helena. 2008.** "Architectural Education After Schön: Cracks, Blurs, Boundaries and Beyond." *Journal for Education in the Built Environment* 3 (2): 63–74.
- **The contribution.** Webster documents the *crit* (the studio critique session) as both a pedagogical mechanism and a ritual of professional acculturation. The crit teaches design judgment by making the criteria visible through their application. Students learn what "works" means by hearing experienced critics talk about specific work in specific terms.
- **The dark side.** Webster is honest about the failure modes of the crit. When the crit becomes a performance of authority by the critic rather than a teaching moment, it produces anxiety, conformity, and disengagement. The same critique mechanism that makes judgment visible can shut down the student's voice if it is done badly. *Studio critique is a high-risk, high-reward pedagogy; when it works, it teaches what nothing else teaches; when it fails, it scars.*
- **For Medhavy.** The AI pre-grading reviewer (companion note §3) is functionally an automated crit. The Webster work is the reminder that the *quality* of the crit matters enormously — supportive, specific, focused on the work rather than the student. The chapter should cite Webster as the canonical evidence that critique-based assessment is powerful when done well and harmful when done badly. The AI reviewer's prompt design carries the entire weight that a good studio critic would carry; if the prompt is generic or harsh, the Webster failure mode reappears in algorithmic form.

### 2.5 Comparative outcomes — design vs. engineering graduates `[art-design-pedagogy]`

Direct head-to-head studies comparing design and engineering graduates on novel-problem performance, ambiguity tolerance, and creative-fluency measures are scarce. The closest evidence:

- **The Atman et al. studies.** Atman, Cynthia J., Robin S. Adams, Monica E. Cardella, Jennifer Turns, Susan Mosborg, and Jason Saleem. 2007. "Engineering Design Processes: A Comparison of Students and Expert Practitioners." *Journal of Engineering Education* 96 (4): 359–379. Atman's group has documented persistent differences between engineering students and practicing engineers on a structured design task, with the most pronounced gap in **problem-scoping behavior** — practicing engineers spent 4× more time gathering information and framing the problem than students did. The students jumped to solutions; the experts framed. *Engineering education does not yet teach the framing move at scale.*
- **The Daly et al. studies of "designerly thinking" in engineering students.** Daly, Shanna R., Erika A. Mosyjowski, and Colleen M. Seifert. 2014. "Teaching Creativity in Engineering Courses." *Journal of Engineering Education* 103 (3): 417–449. Documents that engineering students who receive explicit creative-process instruction perform better on open-ended design tasks; without that instruction, they perform worse than design students even on engineering-domain problems. The skill is teachable but does not emerge from technical curriculum alone.
- **NSSE / VALUE rubric data.** Kuh's National Survey of Student Engagement (NSSE) and the AAC&U VALUE rubric pilot data report higher self-reported gains for design students on "ability to deal with complex issues" and "ability to think creatively" than for engineering students with otherwise similar profiles. But self-report and rubric data are not direct performance measures; this is suggestive, not dispositive.
- **The honest accounting.** There is no large, well-designed comparative study of engineering vs. design graduates on novel-problem performance. There is *consistent indirect signal* across protocol studies, alumni surveys, and rubric data that design pedagogy produces students more comfortable with ambiguity and faster at framing. There is no study that controls for selection (design vs. engineering attracts different students to begin with). **The pattern is real enough to motivate the Glimmer's design move; not strong enough to claim the design move is empirically proven.**

### 2.6 Engineering education's discovery of design thinking — Stanford d.school, MIT, Olin `[art-design-pedagogy]`

- **The Stanford d.school.** Founded 2005 (formally the Hasso Plattner Institute of Design at Stanford). Imports the architecture studio pattern — critique, prototyping, iteration — into a cross-disciplinary program. The "design thinking" curriculum (empathize, define, ideate, prototype, test) is essentially the framing-first design process Schön and Cross described, packaged for non-design students. ([dschool.stanford.edu](https://dschool.stanford.edu))
- **MIT's hands-on design pedagogy.** MIT's Department of Mechanical Engineering's 2.007 (Robot Design Competition) and 2.009 (Product Engineering Processes) have a long history of project-based learning with studio-like critique. The 2009 NRC report on engineering education credited MIT's hands-on curriculum with producing graduates who outperformed peers from more traditional programs on design-task measures. ([NRC, *Engineering in K-12 Education*, 2009, National Academies Press](https://nap.nationalacademies.org/catalog/12635/engineering-in-k-12-education))
- **Olin College of Engineering.** Founded 1997, opened 2002. The most aggressive engineering-education experiment of the last 25 years: no tenure, projects from the first semester, no traditional weed-out courses, integrated studio-style critique throughout. Olin's outcomes have been studied by the National Academy of Engineering and others. The Olin graduates report — and external observers confirm — strong performance on ill-structured design tasks; the trade-off has been less depth in some traditional engineering science topics. ([Olin's published curriculum and outcomes](https://www.olin.edu) and Kerns, S. E. 2010. *Curriculum Re-Imagined.* in *Olin College of Engineering: A Case Study*).
- **The "studio transplant" pattern.** When engineering programs adopt critique-based studio methods (Cornell's project-based ECE program; the University of Sydney's design studios; UCL's integrated engineering program), the consistent pattern is gains on **design-task performance** and **ambiguity tolerance** with stable or slight declines on **content recall** (Brodeur, Young & Blair 2002 on CDIO; Sheppard & Jenison 1997 on freshman-engineering design). The same trade Hmelo-Silver and Dochy identified for PBL in the companion note appears in the studio transplant. **The trade is real and goes the direction the Glimmer wants.**
- **For Medhavy.** Glimmer is the d.school move at the *assignment* level rather than the program level. The evidence base for the program-level studio transplant supports the *direction* of the Glimmer's bet. It does not say "Glimmer in week 3 of a medical course will produce these specific outcomes" — that is the validation Medhavy will produce.

### 2.7 The Carnegie engineering studies — Sheppard et al. 2008 `[art-design-pedagogy]`

Sheppard, Sheri D., Kelly Macatangay, Anne Colby, and William M. Sullivan. 2008. *Educating Engineers: Designing for the Future of the Field.* San Francisco: Jossey-Bass / The Carnegie Foundation for the Advancement of Teaching.

- **The study.** Carnegie Foundation's longitudinal study of engineering education across eleven U.S. institutions. Companion volume to the Carnegie studies of medicine (Cooke et al. 2010), law (Sullivan et al. 2007), and nursing (Benner et al. 2010). Each volume documents the gap between professional education and professional practice.
- **The central finding for engineering.** Engineering practice is fundamentally about *design under constraint with incomplete information and contested goals* — an ill-structured-problem activity. Engineering education is fundamentally about *analytical problem-solving with given specifications and known methods* — a well-structured-problem activity. The four-year curriculum does not bridge the gap. Most engineering students graduate having never been asked to specify a problem; they have always been given one already specified.
- **Sheppard's recommendation.** Restructure engineering education around integrated design experiences from the first semester, with studio-style critique replacing some lecture-and-problem-set hours. **This is essentially the d.school / Olin move, recommended by the Carnegie Foundation in 2008 for engineering broadly.** Adoption has been partial, slow, and uneven.
- **For Medhavy.** Sheppard is the institutional voice — Carnegie Foundation — backing the diagnosis that Glimmer is responding to. The chapter can cite Sheppard as evidence that "engineering education trains for the wrong task structure" is not a niche claim; it is the canonical Carnegie finding. The Medhavy / Glimmer answer is one possible operationalization at the platform level.

### 2.8 The companion Carnegie volume on medicine — Cooke et al. 2010 `[clinical]` `[art-design-pedagogy]`

Cooke, Molly, David M. Irby, and Bridget C. O'Brien. 2010. *Educating Physicians: A Call for Reform of Medical School and Residency.* San Francisco: Jossey-Bass / The Carnegie Foundation.

- **The parallel finding for medicine.** The 2010 Carnegie report on medical education identified the same gap Sheppard et al. found in engineering: medical education trains memorization, recognition, and well-structured-problem performance; medical practice requires diagnostic reasoning under uncertainty, communication with anxious patients, and ethical judgment in cases where guidelines do not resolve. The USMLE-driven curriculum optimizes for what is tested, not what is practiced.
- **The four recommendations.** (1) Standardize learning outcomes and individualize the learning process; (2) integrate formal knowledge and clinical experience; (3) develop habits of inquiry and improvement; (4) focus on professional identity formation.
- **For Medhavy.** Glimmer's port into medical education is the Cooke et al. recommendation operationalized — habits of inquiry and improvement, formal knowledge integrated with clinical reasoning, individualized practice on ill-structured cases. *The Glimmer is the Cooke recommendation as a weekly assignment.* This is the strongest available framing for why Glimmer in medical education is not a curricular novelty but a delayed implementation of an established recommendation.

### 2.9 The most consequential finding for the field-divide section `[art-design-pedagogy]`

> **Both Carnegie Foundation studies (engineering 2008, medicine 2010) reached the same diagnosis a generation apart: the curriculum trains for well-structured-problem performance; the profession requires ill-structured-problem judgment; the gap has been recognized for at least 25 years; the studio-style critique pedagogy that closes the gap in art and design schools has been adopted only in isolated programs (Olin, d.school) at high cost; Glimmer is one mechanism to retrofit the studio-critique pattern into existing engineering and medical curricula at the assignment level without requiring institutional restructuring.**

That sentence is what the field-divide research supports. It is a strong claim and well-grounded.

---

## 3. The pseudocode problem — scaffolding fading and the failure mode it creates

### 3.1 The named pattern `[scaffolding-fading]` `[failure-mode]`

The pattern is documented across computing education, mathematics education, and engineering design education with different vocabularies for the same phenomenon:

- **Students given step-by-step pseudocode can implement; students given only the goal cannot formulate the approach.**
- The pseudocode does the formulation. The student does the translation. The translation skill is what the curriculum was supposed to build. The student leaves the course able to *execute* and not able to *formulate*.
- **Soloway 1986** ("Learning to Program = Learning to Construct Mechanisms and Explanations," *Communications of the ACM* 29 (9): 850–858) was the original named identification of the problem in computer science. The "plan composition" skill — knowing how to assemble micro-procedures into a coherent solution — is the residual after syntax and individual operations are taught. Soloway's data showed students who could write loops and conditionals in isolation could not write a working program that combined them when the problem was not pre-structured.
- **Lister et al. 2004** ("A Multi-National Study of Reading and Tracing Skills in Novice Programmers," *ACM SIGCSE Bulletin* 36 (4): 119–150) replicated the finding internationally: novice CS students could trace code (execute pseudocode in their heads) far better than they could write code from scratch to a specification. The gap was wide and persistent.
- **For Medhavy.** This is the failure mode the Glimmer's *first three weeks* must navigate. Medical and engineering students arriving from USMLE-style multiple-choice training have been trained almost entirely on the recognition-and-execution side of the divide. Glimmer asks for formulation, which the student has not been asked to do at scale. Predictable response: anxiety, avoidance, and superficial compliance — produce *something* that looks Glimmer-shaped, but with the framing imported from the textbook rather than constructed by the student. Detection requires the rubric's specificity dimension and the AI reviewer's targeted-weakness questions.

### 3.2 Pea 2004 — scaffolding withdrawal and its discontents `[scaffolding-fading]`

Pea, Roy D. 2004. "The Social and Technological Dimensions of Scaffolding and Related Theoretical Concepts for Learning, Education, and Human Activity." *Journal of the Learning Sciences* 13 (3): 423–451. ([DOI: 10.1207/s15327809jls1303_6](https://www.tandfonline.com/doi/abs/10.1207/s15327809jls1303_6))

- **The conceptual contribution.** Pea pulled the term *scaffolding* back to its original Wood, Bruner & Ross (1976) meaning — *temporary* support, calibrated to the learner's current need, withdrawn as competence grows. Pea's complaint was that EdTech systems had begun treating scaffolding as a permanent feature ("we have scaffolds!") rather than a transient one. **Permanent scaffolding is not scaffolding; it is dependency.**
- **The three load-bearing properties Pea names.** Scaffolding must be (a) **contingent** on the learner's current state; (b) **faded** as competence grows; (c) **transferred** so the learner internalizes what the scaffold was doing externally. All three are required; any one missing produces a failure mode. Contingent-without-fading produces dependency. Fading-without-contingent produces gaps. Contingent-and-faded without transfer produces brittle competence — the learner can do it with scaffold, cannot do it without, has not internalized the structure.
- **For Medhavy.** Glimmer's design must specify all three. The AI reviewer's questions must be contingent on what the learner produced (not a generic checklist). The reviewer's intervention must reduce as the learner's framing matures (not constant pressure on every dimension every week). The scaffold must transfer — the learner who has done 10 Glimmers should be able to ask themselves the reviewer's questions without the reviewer present.

### 3.3 Puntambekar & Hübscher 2005 — the scaffolding-literature gap `[scaffolding-fading]`

Puntambekar, Sadhana, and Roland Hübscher. 2005. "Tools for Scaffolding Students in a Complex Learning Environment: What Have We Gained and What Have We Missed?" *Educational Psychologist* 40 (1): 1–12.

- **The diagnosis.** A meta-review of the scaffolding literature found that most educational-technology systems claiming "scaffolding" implemented only the *initial support* component and neither the *contingency* component nor the *fading* component. The reason: contingency and fading are hard to implement at scale. Initial support — pre-built worksheets, decision trees, structured templates — is easy. The systems that did the easy part and called it scaffolding mis-named what they were doing.
- **The empirical consequence.** P & H's review of intervention studies found that systems with full contingency-and-fading scaffolding produced reliably larger learning gains than systems with initial-support-only scaffolding. The effect was particularly strong on *transfer* — students with faded scaffolding could perform the task in new contexts; students with permanent scaffolds could not.
- **For Medhavy.** The chapter must be honest about what Medhavy's scaffolding actually is. If the AI reviewer asks the same five questions on every Glimmer regardless of the learner's prior performance, that is initial-support, not scaffolding in the P & H sense. The Medhavy 2.0 bandit (chapter 4) is the proposed mechanism for contingency. The fading mechanism is not yet explicit in the Medhavy documents I have seen; the chapter should flag this as a design specification still to be written.

### 3.4 van de Pol, Volman & Beishuizen 2010 — operationalizing scaffolding `[scaffolding-fading]`

van de Pol, Janneke, Monique Volman, and Jos Beishuizen. 2010. "Scaffolding in Teacher–Student Interaction: A Decade of Research." *Educational Psychology Review* 22 (3): 271–296.

- **The operationalization.** Three core elements of scaffolding from a decade-long review: **contingency** (adjusting support to the learner's current level), **fading** (gradually withdrawing support), and **transfer of responsibility** (moving the cognitive work from teacher to learner over time). The three are interdependent — contingency without fading produces dependency; fading without contingency produces drop-out; transfer of responsibility is the goal both serve.
- **The teacher-interaction signal.** Studies in this review document the actual interactional moves teachers make to scaffold contingently: diagnostic questions to assess current state, recasts of student responses to surface partial understanding, hand-off prompts ("can you say more about why?"). These moves are the human implementation of what an AI reviewer would need to do.
- **For Medhavy.** Translation to the AI reviewer: the reviewer needs to *diagnose* (read the learner's submission against the rubric), *recast* (surface what is partial), and *hand off* ("what is the strongest case against your protocol?"). The Graham 2015 questioning-feedback literature (companion note §3.2) sits naturally inside this scaffolding-fading framework. **The AI reviewer is a scaffolding move in the van de Pol sense — it diagnoses, recasts, hands off. The question is whether it fades.**

### 3.5 Getzels & Csikszentmihalyi 1976 — problem-finding vs. problem-solving `[problem-framing]`

Getzels, Jacob W., and Mihaly Csikszentmihalyi. 1976. *The Creative Vision: A Longitudinal Study of Problem Finding in Art.* New York: Wiley.

- **The original distinction.** Studied art students at the School of the Art Institute of Chicago in the 1960s. Set up a task: from a set of objects, the student chose some, arranged them, and produced a drawing. Two scored dimensions: time spent **handling and manipulating objects before drawing started** (a proxy for problem-finding effort) and **degree of exploration during drawing** (revising the composition mid-work, a proxy for openness to reformulating the problem).
- **The longitudinal finding.** Seven years after graduation, the students who had scored high on problem-finding behavior were significantly more successful as practicing artists. The students who scored high on problem-solving (technical execution) but low on problem-finding had largely left art. *Problem-finding predicted long-term creative success; problem-solving did not.*
- **The 30-year follow-up — Csikszentmihalyi 1996.** *Creativity: Flow and the Psychology of Discovery and Invention.* HarperCollins. The pattern held. The problem-finders were the ones still making art and still recognized for it three decades later.
- **For Medhavy.** Getzels & Csikszentmihalyi is the foundational empirical evidence that *problem-formulation is a distinct skill and a predictor of long-term performance, separable from problem-solving skill.* The Glimmer's "WHY" and "specificity" rubric dimensions target problem-finding. The medical / engineering curricula students arrive from have measured only problem-solving (USMLE, FE exam). Glimmer is the assignment that surfaces and trains the missing skill.

### 3.6 Chi, Glaser & Rees 1982 — novice-expert problem representation `[problem-framing]`

Chi, Michelene T. H., Robert Glaser, and Ernest Rees. 1982. "Expertise in Problem Solving." In *Advances in the Psychology of Human Intelligence*, Vol. 1, edited by R. J. Sternberg, 7–75. Hillsdale, NJ: Erlbaum. (Companion to Chi, Feltovich & Glaser 1981 on physics problem categorization.)

- **The finding.** When asked to sort physics problems into categories, expert physicists sorted by *deep principle* (conservation of energy, conservation of momentum, Newton's second law); novice students sorted by *surface features* (inclined plane, pulley, spring). The experts saw the same problem-classes as functionally equivalent (sharing a solution principle); the novices saw the same problem-classes as superficially similar (sharing a geometry).
- **The implication for instruction.** Expertise is *reorganization of knowledge around principles*, not addition of more knowledge. A curriculum that drills students on surface-level problem-pattern recognition produces students who can recognize the geometry but cannot select the principle. The novice-expert gap is in *problem representation*, not in problem-solving steps once represented.
- **For Medhavy.** The Glimmer's "mechanism" rubric dimension is, in Chi terms, asking the student to make the *principle* visible — to demonstrate they have reorganized the surface features into a deeper structure. A Glimmer that the student answers by surface-feature pattern-match (this case is like the textbook case, so I'll do what the textbook did) scores poorly on mechanism. A Glimmer that the student answers by naming the deep principle and showing how it applies scores well. **The rubric is correctly designed to detect expert-style reorganization vs. novice-style pattern-match.**

### 3.7 Voss & Post 1988 — problem representation in social science domains `[problem-framing]`

Voss, James F., and Timothy A. Post. 1988. "On the Solving of Ill-Structured Problems." In *The Nature of Expertise*, edited by Michelene T. H. Chi, Robert Glaser, and Marshall J. Farr, 261–285. Hillsdale, NJ: Erlbaum.

- **The contribution.** Voss & Post extended Chi's work from physics (well-structured) to political science and economic policy (ill-structured). The novice-expert gap they documented was even more pronounced in ill-structured domains: experts spent significantly more time **constructing a representation** of the problem before attempting a solution, and the representation experts built included *constraints, stakeholders, and consequences* that novices either omitted or treated as fixed.
- **The 60% rule.** Across their studies, Voss reports that experts in policy problems spent roughly 60% of working time on representation and 40% on solution; novices inverted this ratio. (Compare to Lawson's design data — same pattern, different domain.)
- **For Medhavy.** Voss & Post is the closest analog for clinical-reasoning ill-structured-problem work. A clinical case is more like a policy problem than a physics problem — multiple stakeholders, contested goals, incomplete information, no agreed evaluation criterion. The expert clinician spends time on representation (history-taking, framing the differential, deciding what to test). The novice clinician jumps to action. **The Glimmer is asking students to do the representation work the expert spends 60% of their time on, in an assignment shape that makes the representation visible and gradeable.**

### 3.8 Kalyuga, Ayres, Chandler & Sweller 2003 — the expertise reversal effect `[scaffolding-fading]` `[discovery-vs-direct-instruction]`

Kalyuga, Slava, Paul Ayres, Paul Chandler, and John Sweller. 2003. "The Expertise Reversal Effect." *Educational Psychologist* 38 (1): 23–31.

- **The effect.** Instructional supports that help novices *hurt* experts. A worked example that scaffolds a beginner's understanding wastes the time of someone who already has the schema; the beginner needs the example, the expert needs the open problem. The reverse holds — open problems that productively challenge experts overwhelm novices who lack the schemas to make sense of them.
- **Why this matters specifically for fading.** The expertise-reversal effect *is* the theoretical justification for fading. If you do not fade, you will eventually be supporting an expert with novice scaffolding, hurting performance. If you do not fade contingently, you will fade too fast for some and too slow for others.
- **For Medhavy.** Reinforces companion note §2.2. The Glimmer's scaffolding must fade *as the learner becomes more expert at Glimmer-style work*, not on a fixed schedule. The Medhavy 2.0 bandit is the proposed contingency mechanism. The chapter must be honest that without the bandit working well, Glimmer will under-perform for either the early learners (under-scaffolded) or the late learners (over-scaffolded), depending on what the static scaffolding is calibrated to.

### 3.9 Renkl on worked examples `[scaffolding-fading]`

- **Renkl, Alexander. 2014.** "Toward an Instructionally Oriented Theory of Example-Based Learning." *Cognitive Science* 38 (1): 1–37.
- **Renkl, Alexander, and Robert K. Atkinson. 2003.** "Structuring the Transition From Example Study to Problem Solving in Cognitive Skill Acquisition: A Cognitive Load Perspective." *Educational Psychologist* 38 (1): 15–22.
- **The contribution.** A worked example is a fully-solved problem the learner studies before attempting similar problems. Renkl's program of research shows worked examples produce reliably larger learning gains than equivalent problem-solving practice for novices on well-structured problems. The mechanism is reduction of extraneous cognitive load: the learner can attend to the *structure* of the solution because they do not have to *generate* the steps.
- **Worked-example fading.** The instructional design move Renkl emphasizes: as the learner gains competence, *fade the worked example* by removing one step at a time, replacing it with a blank the learner fills in. This is the *backwards-faded worked example* sequence: full worked example → partial worked example → independent problem.
- **For Medhavy.** Renkl provides the canonical scaffolding-fading sequence: full example → partial example → independent. The Glimmer's first three weeks should arguably operate in this mode — week 1 a Glimmer with the framing pre-supplied (worked example of framing), week 2 a Glimmer with the framing partially supplied (student fills in the WHY), week 3 a Glimmer with no framing supplied. Whether Medhavy actually does this in week 1 is a design choice; the Renkl evidence supports doing it.

### 3.10 van Merriënboer's 4C/ID model `[scaffolding-fading]`

van Merriënboer, Jeroen J. G., and Paul A. Kirschner. 2018. *Ten Steps to Complex Learning: A Systematic Approach to Four-Component Instructional Design.* 3rd ed. New York: Routledge. (First edition 2007; original 4C/ID paper, van Merriënboer 1997.)

- **The model.** Complex learning is built around four components: (1) learning tasks (whole-task practice in increasing complexity), (2) supportive information (the "theory" the learner needs), (3) procedural information (just-in-time instruction for routine sub-skills), and (4) part-task practice (drill on automatable sub-procedures).
- **The fading move.** Within the learning-tasks component, van Merriënboer specifies a *whole-task scaffolding-fading* sequence: the learner starts on a complete (but simplified) version of the task, supported heavily; as competence grows, the support fades and the task complexity increases. The empirical claim — backed by his lab's experimental work and applied across aviation, medical, and engineering training — is that this whole-task fading sequence produces stronger transfer than either part-task drill or unscaffolded whole-task practice.
- **For Medhavy.** The Glimmer's design is essentially a whole-task practice sequence in van Merriënboer's sense. Each Glimmer is a whole task (specify a problem, propose a solution, defend it). The complexity escalates across the term. The scaffolding fades. If the chapter wants the cleanest single instructional-design theory to cite, 4C/ID is it — it covers the whole-task structure, the fading sequence, and the transfer claim in one integrated frame.

### 3.11 Kirschner, Sweller & Clark 2006 — the conservative-instruction position `[discovery-vs-direct-instruction]`

Kirschner, Paul A., John Sweller, and Richard E. Clark. 2006. "Why Minimal Guidance During Instruction Does Not Work: An Analysis of the Failure of Constructivist, Discovery, Problem-Based, Experiential, and Inquiry-Based Teaching." *Educational Psychologist* 41 (2): 75–86. ([DOI: 10.1207/s15326985ep4102_1](https://www.tandfonline.com/doi/abs/10.1207/s15326985ep4102_1))

- **The argument.** Pure discovery learning, minimal-guidance approaches, and unscaffolded inquiry produce worse learning than direct instruction for novices. The cognitive-load mechanism: without schemas in long-term memory to organize incoming information, novices overload working memory trying to discover what they have not yet been taught.
- **The empirical case.** Kirschner et al. cite evidence from cognitive load theory (Sweller's program), worked-example research (Renkl), and instructional-design studies showing direct instruction outperforms discovery for novices. Their position is not that discovery is never appropriate; it is that *novice-level discovery in a complex domain is a setup for failure unless heavily scaffolded.*
- **For Medhavy.** This is the most consequential cautionary citation for Glimmer. If Glimmer is interpreted as "give the student an open problem and let them discover the answer," Kirschner-Sweller-Clark predicts the modal student will fail. The Glimmer's design must take this prediction seriously. The Glimmer is *not* discovery learning in their critical sense — it has heavy scaffolding (the rubric, the AI reviewer's questions, the concept anchor). But it shares structural features with the methods K-S-C critique, and the chapter must be explicit about which features it shares and which it doesn't.

### 3.12 Hmelo-Silver, Duncan & Chinn 2007 — the response `[discovery-vs-direct-instruction]`

Hmelo-Silver, Cindy E., Ravit Golan Duncan, and Clark A. Chinn. 2007. "Scaffolding and Achievement in Problem-Based and Inquiry Learning: A Response to Kirschner, Sweller, and Clark (2006)." *Educational Psychologist* 42 (2): 99–107.

- **The response's core move.** Well-designed PBL and inquiry learning are *not* minimal-guidance — they are heavily scaffolded by problem structure, expert facilitators, peer collaboration, and embedded resources. Kirschner-Sweller-Clark are critiquing a strawman; the actual implementations they criticize don't exist in well-designed programs. *Scaffolded inquiry is not the same as minimal-guidance discovery.*
- **The empirical claim.** Meta-analyses of well-designed PBL (Dochy et al. 2003; Hmelo-Silver 2004) consistently show skill gains over direct instruction with modest losses in knowledge breadth. The trade is real and goes the direction proponents claim.
- **The Sweller-Kirschner-Clark rebuttal 2007.** They argue much-cited PBL implementations are still under-scaffolded for novices; the apparent skill gains may not reflect genuine learning so much as familiarization with task surface features. Debate continues.
- **For Medhavy.** The Hmelo-Silver position is the more defensible reading for Glimmer. Glimmer is *not* minimal-guidance — it has the rubric, the AI reviewer, the concept anchor. The chapter should cite K-S-C as the cautionary frame and H-S-D-C as the more accurate description of what well-designed scaffolded inquiry actually looks like. Glimmer must hold to the well-scaffolded end; if it drifts toward minimal guidance, K-S-C's critique lands.

### 3.13 The medical-curriculum implication `[failure-mode]` `[clinical]`

The pre-clerkship medical curriculum is dominated by USMLE Step 1 preparation. The exam is multiple-choice. The exam-driven study habits are: read First Aid, drill UWorld questions, repeat. *This is the most extreme form of well-structured-problem training in higher education.* Students arrive at clinical training having spent two years optimizing for recognition-and-execution on closed problems.

When this population is asked to do Glimmer-style work — specify, propose, defend — the predictable response sequence is:

1. **Confusion phase (week 1).** "What does it want? What's the right answer?" The student frames the assignment as a hidden well-structured problem and asks how to find the framing.
2. **Avoidance phase (week 2–3, if confusion not resolved).** Effort shifts to Quiz Me. The student produces a Glimmer that looks compliant — a few paragraphs in the right shape — but does not contain genuine framing work.
3. **Anxiety stabilization (weeks 4–6, if confusion *is* resolved).** The student begins to do the framing work. Quality is low but improving. The AI reviewer's targeted weaknesses become legible as guidance rather than as criticism.
4. **Generative phase (week 7+, if stabilization holds).** The student begins to find Glimmer interesting. Framing becomes the work the student wants to do.

This sequence is what the Glimmer's first three weeks must navigate. **The single largest determinant of whether the population reaches phase 3 vs. ossifies in phase 2 is the quality of the AI reviewer's questions in weeks 1–2.** Generic questions ("be more specific!") confirm phase 1 confusion as evidence the student cannot do the work and accelerate phase 2 avoidance. Targeted questions that name a specific reasoning gap and ask the student to address *just that gap* convert phase 1 into an actionable next step and accelerate phase 3.

The interventions that work, from the scaffolding literature applied to this population:

- **Worked-example openers (Renkl).** Week 1 Glimmer with the framing pre-supplied as a worked example — the student fills in the mechanism and defends it. This is the backwards-faded sequence Renkl recommends.
- **Specific weakness prompts (van de Pol).** AI reviewer questions name exactly which rubric dimension is weak and what specifically would strengthen it. Not "your defensibility is weak"; rather "you argued for X but did not say what observation would lead you to change your mind to Y — what observation would it be?"
- **Pre-frame examples (4C/ID supportive information).** Surface the schema the rubric is asking for before the student attempts Glimmer 1, not during. The student needs the schema in long-term memory before discovery on a complex task is productive (Kirschner-Sweller-Clark).
- **Public visibility of expert framings (Schön's studio).** Surfacing 1–2 anonymized strong Glimmers from prior cohorts in the first three weeks gives the student a visible target — the studio-critique model's missing piece for solo learners.

### 3.14 The most actionable scaffolding-fading recommendation for the Glimmer's first three weeks `[scaffolding-fading]`

> **Week 1 should be a backwards-faded worked example: present a complete Glimmer (problem framed, mechanism explained, defensibility argued) and ask the student to fill in only the specificity layer, while the AI reviewer comments only on specificity; week 2 should fade the worked example by leaving the defensibility layer blank for the student to construct, with the AI reviewer commenting on defensibility and specificity; week 3 is the first complete Glimmer with the student supplying framing, mechanism, defensibility, and specificity, with the AI reviewer commenting on all four rubric dimensions. This sequence implements the Renkl backwards-faded worked example pattern inside the van Merriënboer whole-task escalation, with the contingency / fading / transfer trio of van de Pol made operational across the first three Glimmers.**

This is the strongest single recommendation the scaffolding-fading literature supports for Medhavy's Glimmer design.

---

## 4. Brief integration sections (bridges to the companion note)

### 4.1 Effectiveness of generative assignments `[generative-assignment]`

The companion note (`glimmer-research.md` §1) covers this in detail: GLA effect sizes from Fiorella & Mayer 2016 (d ≈ 0.40–0.55 across the eight activities); Nesbit & Adesope 2006 on concept mapping (d ≈ 0.74); Chen & Yang 2019 PBL meta-analysis (g = 0.71 on academic achievement); Belland et al. 2017 on STEM scaffolding (g = 0.46). The displacement argument here adds *why now* — even if Glimmer's session-level effect size matches generative work generally, the *educational-value differential vs. Quiz Me* should be growing as the labor-market value of pure recall declines and the labor-market value of judgment work holds or rises. Glimmer-style work is becoming more valuable per unit of student time relative to closed-problem practice. **The relative argument may matter more than the absolute effect size.**

### 4.2 AI as pre-grading reviewer `[generative-assignment]`

The companion note (`glimmer-research.md` §3) covers Hattie & Timperley 2007, Graham et al. 2015, Cho & MacArthur 2010/2011, Steiss et al. 2024, and the cognitive-offloading concerns. The displacement argument bridges as follows: the AI reviewer is doing the work AI does well (preliminary structured review of an artifact against a rubric — a partially specifiable task) so that the instructor can do the work only she can do (judgment on novel reasoning — the residual category from §1.8). **This is the labor-division the displacement argument predicts is the productivity-maximizing allocation at every level — including inside an educational system.** Don't have the human do what AI does well; don't have AI do what human does well; design the workflow so each is doing what comparative advantage assigns to them. The pre-grading reviewer is that workflow at the assignment level.

### 4.3 Term-project emergence `[generative-assignment]`

The companion note (`glimmer-research.md` §4) covers Murray, Elbow, Flower & Hayes, Locke & Latham, the implicit-learning literature, the gap in direct evidence for emergent vs. announced project structures. The displacement argument bridges as follows: a fully-specifiable term project (announced driving question, prescribed milestones, evaluation criteria fixed in advance) is exactly the kind of task that *can be done by AI start to finish.* It is the *emergent* term project — where the student's own framing of what the term project is and what it should contain is the visible learning — that retains educational value. **You cannot fully-specify in advance the term project Glimmer produces, precisely because the educational value is in what the student frames, not in what was specified for them.** The displacement argument and the emergent-portfolio design are not separate Medhavy commitments; they are the same commitment from two angles.

---

## 5. Glimmer rubric dimensions — validation pass

### 5.1 What the companion note already covered

The companion note (`glimmer-research.md` §2.3, §2.4) covered the AAC&U VALUE rubrics (Critical Thinking, Creative Thinking, Inquiry and Analysis), Anderson & Krathwohl's revised Bloom's, Berliner on expert-teacher description, and Reeves on rubric dimensions that distinguish elaborated reasoning from summary. The mapping established there was that Glimmer's five-dimension rubric (WHY / usefulness / mechanism / defensibility / specificity) corresponds well to Critical Thinking + Inquiry VALUE rubric dimensions with specificity pulled out as its own.

### 5.2 The specificity dimension — additional grounding `[problem-framing]` `[foundational-theory]`

The companion note treated specificity briefly. Two additional anchors deepen the case:

- **Anderson & Krathwohl revised Bloom's** (already in companion note) is the conventional citation, but the *operational test* it provides is: a specifiable objective uses a measurable verb ("explain the difference between X and Y") and names a concrete target. A non-specifiable objective uses a non-measurable verb ("understand X") and leaves the target implicit. The same logic applies to a Glimmer's product. *Specificity is the operational signal that the learner has moved from the inert verb to the measurable verb.*
- **Berliner 2001** (already in companion note) on expert-teacher descriptors. Expert teachers describe student performance, learning situations, and instructional decisions with more conditional and contextual specificity than novices. *Specificity in description tracks expertise in description.* When applied to learner work, this means: a learner whose Glimmer-product is specific is producing work in the descriptive register of someone who has internalized the concept; a learner whose work stays at "in general" / "broadly" / "for example" levels has not.
- **The Chi 1981 / Voss 1988 reframe.** A specific Glimmer response is evidence of expert-style problem representation (the deep principle is operationalized to a concrete case); a non-specific Glimmer response is evidence of novice-style problem representation (surface features only). Specificity *is* the signal of representation depth.
- **Reeves 2000 on rubric validity** (already in companion note). Specificity as a rubric dimension cannot be satisfied by quotation — you cannot quote yourself into being specific about a case you do not understand. This is what makes specificity an evidence-bearing dimension and not a stylistic one.

### 5.3 The defensibility dimension — additional grounding `[problem-framing]` `[art-design-pedagogy]`

Defensibility maps to:

- **Jonassen 2000** (companion note): defensibility-of-reasoning as the central evaluation criterion for ill-structured-problem-solving. *The ISP cannot be evaluated by correctness; it can only be evaluated by whether the solver can argue for their choice and identify what would change it.*
- **Toulmin model** (Toulmin, Stephen. 1958. *The Uses of Argument.* Cambridge University Press). The canonical model of argument structure: claim, data, warrant, qualifier, rebuttal. A defensible Glimmer answer makes the warrant explicit and acknowledges qualifiers. The student who cannot identify their warrant cannot defend.
- **Schön 1983** (this note §2.1): reflection-in-action is, operationally, articulating the warrant for a design move while making it. Defensibility-as-rubric-dimension is the same move at the assessment level.
- **Counterfactual reasoning research** (Pearl 2009, *Causality*, Cambridge; Roese 1997 on counterfactual thinking in *Psychological Bulletin*). Strong defensibility includes naming what would change the choice — the counterfactual move. A Glimmer that says "I would change my recommendation if X" is doing causal-counterfactual reasoning the literature treats as the highest-rung explanation skill (Pearl's Rung 3).

### 5.4 The mechanism dimension — additional grounding `[problem-framing]`

Mechanism maps to:

- **Chi 1981 / Chi-Glaser-Rees 1982** (this note §3.6): mechanism is the deep principle, the conservation law, the why-the-thing-works. Mechanism is the signal that the student has reorganized the surface features into the principle. *Mechanism is the expert-novice diagnostic in the rubric.*
- **Bechtel 2008** (*Mental Mechanisms*, Routledge): the philosophy-of-science account of mechanistic explanation. A mechanism specifies the parts, their organization, and the operations they perform that produce the phenomenon. A Glimmer that scores well on mechanism specifies parts and operations; one that scores poorly invokes a phenomenon as if it were a mechanism ("homeostasis maintains stability" is invocation; "negative feedback loops detect deviation and trigger compensatory action" is mechanism).
- **Hempel and Salmon's covering-law tradition.** Useful as the conceptual antecedent. The Glimmer rubric is not asking for a covering-law explanation (which is largely abandoned in philosophy of science), but the rubric does ask the student to articulate the *generative process* the phenomenon emerges from. Mechanism-in-the-rubric is closer to Salmon's later causal-mechanical account.

### 5.5 The usefulness and WHY dimensions

These map most cleanly to the AAC&U Critical Thinking VALUE rubric's "student's position" + Inquiry and Analysis "topic selection" / "conclusions" — covered in the companion note. The new note here adds:

- **Klein 1998/2010 naturalistic decision-making** (§1.8): usefulness in a clinical or engineering context means *operationally usable by the practitioner in the situation*. A protocol that is theoretically sound but operationally impossible scores low on usefulness. The rubric dimension is targeting Klein's "what the firefighter actually does" rather than the textbook normative answer.
- **Reflective-practitioner usefulness — Schön 1983.** What works in the messy, low-ground swamp of actual practice rather than what works on the high, hard ground of theoretical clarity. *Usefulness in the rubric is asking the student to make the swamp-test visible.*

### 5.6 The honest gap on rubric validation

The five-dimension Glimmer rubric has been *constructed* from established conceptual anchors. It has not been *validated* psychometrically — no inter-rater reliability data, no factor analysis showing the five dimensions are statistically distinct, no convergent-validity studies with other rubrics. The published VALUE rubrics have been through this kind of validation; the Glimmer rubric has not.

The honest framing for the chapter: the Glimmer rubric is **a principled construction grounded in established conceptual frames**, **not yet psychometrically validated**, **and validation work is one of the instruments Medhavy's deployment will produce.** The instrumentation Medhavy is building (GLP, mode-switching logs, rubric scores over time) is what would generate the data for validation; the validation is not yet in.

---

## 6. Consolidated references (Chicago author-date)

*New citations introduced in this note are tagged with their primary angle. References cross-referenced from the companion note (already cited in `glimmer-research.md`) are marked **\[cross-ref\]** with a brief note on how the new angle uses them.*

### AI-displacement and labor economics

- Acemoglu, Daron, and Pascual Restrepo. 2022. "Tasks, Automation, and the Rise in U.S. Wage Inequality." *Econometrica* 90 (5): 1973–2016. `[AI-displacement]`
- Autor, David H. 2015. "Why Are There Still So Many Jobs? The History and Future of Workplace Automation." *Journal of Economic Perspectives* 29 (3): 3–30. `[AI-displacement]`
- Brynjolfsson, Erik, Danielle Li, and Lindsey Raymond. 2023. "Generative AI at Work." NBER Working Paper 31161. National Bureau of Economic Research. `[AI-displacement]`
- Dell'Acqua, Fabrizio, Edward McFowland III, Ethan R. Mollick, Hila Lifshitz-Assaf, Katherine Kellogg, Saran Rajendran, Lisa Krayer, François Candelon, and Karim R. Lakhani. 2023. "Navigating the Jagged Technological Frontier: Field Experimental Evidence of the Effects of AI on Knowledge Worker Productivity and Quality." Harvard Business School Working Paper 24-013. `[AI-displacement]` `[verify]`
- Eloundou, Tyna, Sam Manning, Pamela Mishkin, and Daniel Rock. 2023. "GPTs are GPTs: An Early Look at the Labor Market Impact Potential of Large Language Models." arXiv preprint 2303.10130. `[AI-displacement]`
- Frey, Carl Benedikt, and Michael A. Osborne. 2017. "The Future of Employment: How Susceptible Are Jobs to Computerisation?" *Technological Forecasting and Social Change* 114: 254–280. `[AI-displacement]`
- McKinsey Global Institute. 2023, 2024. "The State of AI" annual surveys; "The Economic Potential of Generative AI" (June 2023). `[AI-displacement]` `[vendor]`
- Mollick, Ethan. 2024. *Co-Intelligence: Living and Working with AI.* New York: Portfolio. `[AI-displacement]`
- OECD. 2023. *Is Education Losing the Race with Technology? AI's Progress in Math and Reading.* OECD Education Working Papers. `[AI-displacement]` `[verify exact author and publication number]`
- PwC. 2025. *Global AI Jobs Barometer.* `[AI-displacement]` `[vendor]` `[verify]`

### Judgment under ambiguity / naturalistic decision-making

- Cyert, Richard M., and James G. March. 1963. *A Behavioral Theory of the Firm.* Englewood Cliffs, NJ: Prentice-Hall. `[foundational-theory]`
- Klein, Gary. 1998. *Sources of Power: How People Make Decisions.* Cambridge, MA: MIT Press. `[foundational-theory]`
- Klein, Gary. 2010. *Streetlights and Shadows: Searching for the Keys to Adaptive Decision Making.* Cambridge, MA: MIT Press. `[foundational-theory]`
- Simon, Herbert A. 1956. "Rational Choice and the Structure of the Environment." *Psychological Review* 63 (2): 129–138. `[foundational-theory]`

### Art / design / studio pedagogy

- Atman, Cynthia J., Robin S. Adams, Monica E. Cardella, Jennifer Turns, Susan Mosborg, and Jason Saleem. 2007. "Engineering Design Processes: A Comparison of Students and Expert Practitioners." *Journal of Engineering Education* 96 (4): 359–379. `[art-design-pedagogy]`
- Brodeur, Doris R., Peter W. Young, and Kim B. Blair. 2002. "Problem-Based Learning in Aerospace Engineering Education." *Proceedings of the 2002 ASEE Annual Conference.* (CDIO context.) `[art-design-pedagogy]`
- Cooke, Molly, David M. Irby, and Bridget C. O'Brien. 2010. *Educating Physicians: A Call for Reform of Medical School and Residency.* San Francisco: Jossey-Bass / Carnegie Foundation. `[art-design-pedagogy]` `[clinical]`
- Cross, Nigel. 2006. *Designerly Ways of Knowing.* London: Springer. (Original 1982 essay in *Design Studies* 3 (4): 221–227.) `[art-design-pedagogy]`
- Daly, Shanna R., Erika A. Mosyjowski, and Colleen M. Seifert. 2014. "Teaching Creativity in Engineering Courses." *Journal of Engineering Education* 103 (3): 417–449. `[art-design-pedagogy]`
- Kerns, Sherra E. 2010. *Curriculum Re-Imagined* in *Olin College of Engineering: A Case Study.* `[art-design-pedagogy]` `[verify exact citation]`
- Lawson, Bryan. 2005. *How Designers Think: The Design Process Demystified.* 4th ed. Oxford: Architectural Press. `[art-design-pedagogy]`
- National Research Council. 2009. *Engineering in K-12 Education: Understanding the Status and Improving the Prospects.* Washington, DC: National Academies Press. `[art-design-pedagogy]`
- Schön, Donald A. 1983. *The Reflective Practitioner: How Professionals Think in Action.* New York: Basic Books. `[art-design-pedagogy]`
- Schön, Donald A. 1987. *Educating the Reflective Practitioner.* San Francisco: Jossey-Bass. `[art-design-pedagogy]`
- Sheppard, Sheri D., Kelly Macatangay, Anne Colby, and William M. Sullivan. 2008. *Educating Engineers: Designing for the Future of the Field.* San Francisco: Jossey-Bass / Carnegie Foundation. `[art-design-pedagogy]`
- Webster, Helena. 2005. "The Architectural Review: A Study of Ritual, Acculturation and Reproduction in Architectural Education." *Arts and Humanities in Higher Education* 4 (3): 265–282. `[art-design-pedagogy]`
- Webster, Helena. 2008. "Architectural Education After Schön: Cracks, Blurs, Boundaries and Beyond." *Journal for Education in the Built Environment* 3 (2): 63–74. `[art-design-pedagogy]`

### Scaffolding fading

- Pea, Roy D. 2004. "The Social and Technological Dimensions of Scaffolding and Related Theoretical Concepts for Learning, Education, and Human Activity." *Journal of the Learning Sciences* 13 (3): 423–451. `[scaffolding-fading]`
- Puntambekar, Sadhana, and Roland Hübscher. 2005. "Tools for Scaffolding Students in a Complex Learning Environment: What Have We Gained and What Have We Missed?" *Educational Psychologist* 40 (1): 1–12. `[scaffolding-fading]`
- Renkl, Alexander. 2014. "Toward an Instructionally Oriented Theory of Example-Based Learning." *Cognitive Science* 38 (1): 1–37. `[scaffolding-fading]`
- Renkl, Alexander, and Robert K. Atkinson. 2003. "Structuring the Transition From Example Study to Problem Solving in Cognitive Skill Acquisition: A Cognitive Load Perspective." *Educational Psychologist* 38 (1): 15–22. `[scaffolding-fading]`
- van de Pol, Janneke, Monique Volman, and Jos Beishuizen. 2010. "Scaffolding in Teacher–Student Interaction: A Decade of Research." *Educational Psychology Review* 22 (3): 271–296. `[scaffolding-fading]`
- van Merriënboer, Jeroen J. G., and Paul A. Kirschner. 2018. *Ten Steps to Complex Learning: A Systematic Approach to Four-Component Instructional Design.* 3rd ed. New York: Routledge. `[scaffolding-fading]`
- Wood, David, Jerome S. Bruner, and Gail Ross. 1976. "The Role of Tutoring in Problem Solving." *Journal of Child Psychology and Psychiatry* 17 (2): 89–100. `[scaffolding-fading]` `[foundational-theory]`

### Problem-framing / novice-expert

- Bechtel, William. 2008. *Mental Mechanisms: Philosophical Perspectives on Cognitive Neuroscience.* New York: Routledge. `[problem-framing]`
- Chi, Michelene T. H., Robert Glaser, and Ernest Rees. 1982. "Expertise in Problem Solving." In *Advances in the Psychology of Human Intelligence*, Vol. 1, edited by R. J. Sternberg, 7–75. Hillsdale, NJ: Erlbaum. `[problem-framing]`
- Csikszentmihalyi, Mihaly. 1996. *Creativity: Flow and the Psychology of Discovery and Invention.* New York: HarperCollins. `[problem-framing]`
- Getzels, Jacob W., and Mihaly Csikszentmihalyi. 1976. *The Creative Vision: A Longitudinal Study of Problem Finding in Art.* New York: Wiley. `[problem-framing]`
- Lister, Raymond, Elizabeth S. Adams, Sue Fitzgerald, William Fone, John Hamer, Morten Lindholm, Robert McCartney, Jan Erik Moström, Kate Sanders, Otto Seppälä, Beth Simon, and Lynda Thomas. 2004. "A Multi-National Study of Reading and Tracing Skills in Novice Programmers." *ACM SIGCSE Bulletin* 36 (4): 119–150. `[problem-framing]` `[failure-mode]`
- Pearl, Judea. 2009. *Causality: Models, Reasoning, and Inference.* 2nd ed. Cambridge: Cambridge University Press. `[problem-framing]`
- Roese, Neal J. 1997. "Counterfactual Thinking." *Psychological Bulletin* 121 (1): 133–148. `[problem-framing]`
- Soloway, Elliot. 1986. "Learning to Program = Learning to Construct Mechanisms and Explanations." *Communications of the ACM* 29 (9): 850–858. `[problem-framing]` `[failure-mode]`
- Toulmin, Stephen. 1958. *The Uses of Argument.* Cambridge: Cambridge University Press. `[problem-framing]`
- Voss, James F., and Timothy A. Post. 1988. "On the Solving of Ill-Structured Problems." In *The Nature of Expertise*, edited by Michelene T. H. Chi, Robert Glaser, and Marshall J. Farr, 261–285. Hillsdale, NJ: Erlbaum. `[problem-framing]`

### Discovery vs. direct instruction

- Hmelo-Silver, Cindy E., Ravit Golan Duncan, and Clark A. Chinn. 2007. "Scaffolding and Achievement in Problem-Based and Inquiry Learning: A Response to Kirschner, Sweller, and Clark (2006)." *Educational Psychologist* 42 (2): 99–107. `[discovery-vs-direct-instruction]`
- Kirschner, Paul A., John Sweller, and Richard E. Clark. 2006. "Why Minimal Guidance During Instruction Does Not Work: An Analysis of the Failure of Constructivist, Discovery, Problem-Based, Experiential, and Inquiry-Based Teaching." *Educational Psychologist* 41 (2): 75–86. `[discovery-vs-direct-instruction]`
- Sweller, John, Paul A. Kirschner, and Richard E. Clark. 2007. "Why Minimally Guided Teaching Techniques Do Not Work: A Reply to Commentaries." *Educational Psychologist* 42 (2): 115–121. `[discovery-vs-direct-instruction]`

### Recent AI-in-education

- Bastani, Hamsa, Osbert Bastani, Alp Sungu, Haosen Ge, Özge Kabakcı, and Rei Mariman. 2025. "Generative AI Can Harm Learning." Wharton Working Paper. `[AI-displacement]` `[failure-mode]` `[verify exact author list, year, outlet]`
- Krupp, Lisa, Steffen Steinert, Maximilian Kiefer-Emmanouilidis, Karina E. Avila, Paul Lukowicz, Jochen Kuhn, Stefan Küchemann, and Jakob Karolus. 2024. "Unreflected Acceptance — Investigating the Negative Consequences of ChatGPT-Assisted Problem Solving in Physics Education." Preprint / Proceedings. `[failure-mode]` `[verify]`
- Stadler, Matthias, Manuel Bannert, and Marcus Sailer. 2024. "Cognitive Ease at a Cost: LLMs Reduce Mental Effort but Compromise Depth in Student Scientific Inquiry." *Computers in Human Behavior* 160: 108333. `[failure-mode]` `[verify]`
- Steiss, Jacob, et al. 2024. "Comparing the Quality of Human and ChatGPT Feedback of Students' Writing." *Learning and Instruction* 91. **[cross-ref]** — companion note §3.5. Used here as direct evidence on AI-feedback quality bridging the displacement claim to the assignment level. `[verify]`

### Cross-referenced (already cited in companion note; used in this note for new angles)

- Belland, Brian R., Andrew E. Walker, Nam Ju Kim, and Mason Lefler. 2017. "Synthesizing Results From Empirical Research on Computer-Based Scaffolding in STEM Education: A Meta-Analysis." *Review of Educational Research* 87 (2): 309–344. **[cross-ref]** — used here for scaffolding effect-size baseline. `[scaffolding-fading]`
- Chi, Michelene T. H., Paul J. Feltovich, and Robert Glaser. 1981. "Categorization and Representation of Physics Problems by Experts and Novices." *Cognitive Science* 5 (2): 121–152. **[cross-ref]** — companion note cited for expertise-as-chunking; this note cites for novice-expert problem representation as the rubric-mechanism diagnostic. `[problem-framing]`
- Dochy, Filip, Mien Segers, Piet Van den Bossche, and David Gijbels. 2003. "Effects of Problem-Based Learning: A Meta-Analysis." *Learning and Instruction* 13 (5): 533–568. **[cross-ref]** — PBL trade-off cited here for the studio-transplant analogue. `[art-design-pedagogy]`
- Graham, Steve, Michael Hebert, and Karen R. Harris. 2015. "Formative Assessment and Writing: A Meta-Analysis." *Elementary School Journal* 115 (4): 523–547. **[cross-ref]** — used here in the scaffolding-fading frame as the empirical anchor for questioning-feedback as a contingent scaffold. `[generative-assignment]`
- Hattie, John, and Helen Timperley. 2007. "The Power of Feedback." *Review of Educational Research* 77 (1): 81–112. **[cross-ref]** — used here to frame the AI-as-pre-grader bridge to displacement. `[generative-assignment]`
- Hmelo-Silver, Cindy E. 2004. "Problem-Based Learning: What and How Do Students Learn?" *Educational Psychology Review* 16 (3): 235–266. **[cross-ref]** — used here for the studio-transplant pattern. `[art-design-pedagogy]`
- Jonassen, David H. 1997, 2000. **[cross-ref]** — ISP framework cited here for the defensibility rubric dimension. `[problem-framing]`
- Kalyuga, Slava, Paul Ayres, Paul Chandler, and John Sweller. 2003. "The Expertise Reversal Effect." *Educational Psychologist* 38 (1): 23–31. **[cross-ref]** — companion note §2.2; this note uses for scaffolding-fading rationale. `[scaffolding-fading]`
- Norman, Geoffrey. 2005. "Research in Clinical Reasoning: Past History and Current Trends." *Medical Education* 39 (4): 418–427. **[cross-ref]** — used here for clinical reasoning as ill-structured-problem activity. `[clinical]`

---

## 7. Items flagged `[verify]` for citation cleanup before publication

1. **Eloundou et al. 2023** — preprint vs. published version; the arXiv preprint is the canonical reference but check whether a peer-reviewed publication has appeared.
2. **Bastani et al. 2025 "Generative AI Can Harm Learning"** — confirm exact author list, year, and outlet (Wharton working paper vs. published).
3. **OECD 2023 *Is Education Losing the Race with Technology?*** — confirm exact title, author, and OECD working paper number.
4. **PwC 2025 *Global AI Jobs Barometer*** — vendor publication; cite for trend signal, not as primary evidence. Verify publication date and key figures before quoting.
5. **Dell'Acqua et al. 2023 (HBS WP 24-013)** — confirm working paper number and author list; check for updated version.
6. **Krupp et al. 2024** and **Stadler et al. 2024** — both recent ChatGPT-in-classroom studies; confirm publication status (preprint vs. published) and exact author lists before citing.
7. **Kerns, Sherra E. 2010 Olin case study** — find canonical citation (book chapter, report, or article).
8. **Frey & Osborne 2013** — original 2013 Oxford Martin School working paper title is "The Future of Employment: How Susceptible Are Jobs to Computerisation?"; published version 2017 in *Technological Forecasting and Social Change* — use the 2017 published reference as primary.

---

## 8. Summary — three sentences, one each per angle

**On displacement:** The peer-reviewed labor literature (Acemoglu & Restrepo; Eloundou et al.; Brynjolfsson, Li & Raymond) establishes that AI is displacing specifiable cognitive tasks at scale and compressing the skill distribution by raising the novice floor faster than the expert ceiling; the educational translation — that the educational value of practicing fully-specifiable tasks therefore declines while practice in judgment under ambiguity retains its value — is a theoretically defensible 2024+ working hypothesis with adjacent empirical support in labor economics but not yet direct empirical support in education research.

**On the field divide:** Both Carnegie Foundation studies (engineering 2008, medicine 2010) reached the same diagnosis a generation apart — the curriculum trains for well-structured-problem performance while the profession requires ill-structured-problem judgment — and the studio-style critique pedagogy that closes the gap in art and design schools has only been adopted in isolated programs (Olin, d.school) at high cost; the Glimmer is the studio-critique pattern retrofitted at the assignment level into existing engineering and medical curricula without institutional restructuring.

**On scaffolding-fading and the pseudocode problem:** Medical and engineering students arrive from USMLE / FE-exam-style training optimized for closed-problem recognition-and-execution and predictably respond to early Glimmer prompts with confusion-then-avoidance unless the first three weeks operate as a backwards-faded worked-example sequence (week 1: framing supplied, student fills specificity; week 2: framing supplied, student fills defensibility and specificity; week 3: full Glimmer with all four rubric dimensions on the student), implementing the Renkl backwards-faded worked-example pattern inside van Merriënboer's whole-task escalation with van de Pol's contingency/fading/transfer triple operationalized through the AI reviewer's targeted-weakness questions.

---

*End of research note. Tag distribution: AI-displacement: 11; art-design-pedagogy: 14; scaffolding-fading: 8; problem-framing: 11; discovery-vs-direct-instruction: 3; foundational-theory: 5; failure-mode: 4; clinical: 2; generative-assignment: 3 (cross-ref bridges); verify-flagged: 8. New unique primary citations: 41. Cross-referenced from companion note: 9. Total unique primary citations across both notes: ~89.*
