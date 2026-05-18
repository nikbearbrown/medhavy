# Chapter 11 — The Economics of Intelligent Textbooks

---

## Learning Objectives

By the end of this chapter, you will be able to:

1. **(Understand)** Explain why cost collapse changes the economics of intelligent textbook production *asymmetrically* — and name which costs collapsed, which did not, and why the difference is structural rather than incidental.
2. **(Analyze)** Calculate the minimum viable audience for an intelligent textbook at a given production cost and price point — and identify when the audience size is the binding constraint and when it is not.
3. **(Evaluate)** Assess a proposed intelligent textbook investment against the cost-collapse asymmetry, distinguishing where the economics support the build from where they do not.
4. **(Apply)** Specify the minimum viable investment for a given intelligent textbook — naming what subset of the four-layer architecture is feasible at $15K, $150K, and $1.5M.

**Prerequisites:** Chapters 1–9. You should already know the four-layer architecture, the burden-of-proof argument for high-stakes content, the Sadler 2013 pedagogical content knowledge finding, and the complexity threshold test from Chapter 2.

**Skippable?** Yes, if your build decision is already made. You will lose the cost-collapse argument and the homeschool-microaudience worked example, but you will not lose a capability the rest of the book delivers.

---

## Where this fits the conductor frame

This chapter primarily serves the organization — the third of the three questions, in order. The learner-first and instructor-second commitments of the earlier chapters have to land inside an institution that can fund the conducting. The chapter asks the question the procurement officer is going to ask anyway: when does the four-layer build pay back, and when is Chapter 3's smaller arrangement still the right answer?

What this chapter specifies for the conductor is the cost of conducting at different scales. The Sesame Street floor — about $5 per child per year producing roughly *d* = 0.29 — is the calibration anchor any new instrument has to clear or explain. The cost collapse for production has lowered the floor; the persistent cost of design discipline has not. The conductor's instrument selection now depends on a calculation: at this audience size, at this cost-per-0.1-SD, with this measurement budget, does the heavier instrument set earn its keep, or does the Anki-plus-volunteer arrangement still dominate?

The chapter runs the experiment by treating each cost-collapse claim as a falsifiable bet. The vendor pitch deck that asserts "AI-generated content is as effective as professionally produced content" is not what the chapter delivers; the chapter specifies what evidence such a claim would have to bring. Transparency about the cost structure — what collapsed, what did not, what remains a bet — is what lets an institution decide honestly whether to fund the deployment or wait for the experiment to mature.

---

## The Floor That Held for Forty Years

Sesame Street has cost roughly **$5 per child per year** for as long as I have been alive.

That number is doing real work, so let me unpack it before the argument leans on it. The recent production budget is approximately $25 million per year for ~26 episodes — roughly $960,000 to $1 million per episode ([Slate 2012](https://slate.com/business/2012/01/does-sesame-street-lose-money.html); [Hollywood Reporter 2019](https://www.hollywoodreporter.com/news/general-news/sesame-street-gets-funding-how-it-went-broke-1183032/)). The Sesame Workshop reaches approximately 156 million children per year through about 30 international co-productions — *Plaza Sésamo*, *Galli Galli Sim Sim*, *Iftah Ya Simsim*, the list goes on. Divide $25M by 156M children and you get production cost per child of **$0.16**. Add adaptation, distribution, licensing, formative research, and the fully-amortized number lands around **$5/child/year**.

The effect size, averaged across 24 studies, 10,000+ children, 15 countries: *d* ≈ 0.29 on cognitive outcomes, learning about the world, and social attitudes combined (Mares & Pan 2013, *Journal of Applied Developmental Psychology* 34(3): 140–151, [DOI](https://www.sciencedirect.com/science/article/abs/pii/S0193397313000026)). The effect size is virtually identical in low/middle-income (0.29) and high-income (0.285) countries.

Run that division. **Cost per 0.1 standard-deviation gain: about $1.72 per child.** Compare to high-dose tutoring at *d* ≈ 0.37 and $2,000–$3,500/child (Nickow, Oreopoulos & Quan 2024): tutoring is ~300–500× more expensive per 0.1 SD of measured gain than Sesame Street.

And it gets stronger. Kearney & Levine 2019 (*AEJ: Applied Economics* 11(1): 318–350, [DOI](https://www.aeaweb.org/articles?id=10.1257/app.20170300)) used geographic variation in 1969 PBS reception — VHF strong-signal vs. UHF weak-signal counties — as a natural experiment. **Preschool-age children in strong-reception counties were 14% less likely to be behind their expected grade level decades later.** Grade-for-age effect comparable in magnitude to Head Start, at roughly 1,500–2,000× lower cost ($5 vs. $8,500–$10,000/child/year for Head Start).

For forty years this was the floor. The most cost-effective educational intervention ever documented at scale, sustained across three decades of replication, across continents. Anyone proposing an educational technology investment had to clear it, or explain why their cost-per-0.1-SD number was higher.

Then the floor collapsed.

**An AI-generated 500-word explanation of a concept, retrieval-augmented to a textbook, costs cents.** A faculty-reviewed AI-generated quiz item costs a few dollars. Veo-style AI-generated short educational video lands at roughly $30/minute at vendor pricing ([vidpros pricing summary](https://vidpros.com/breaking-down-the-costs-creating-1-minute-videos-with-ai-tools/)). Compare that to the $75,000–$150,000 per 60–90-second segment that medical education vendors paid for fifty years.

This chapter is about what that collapse changes — and what it does not.

---

## §1. The Cost Collapse and Its Asymmetry

I want to be careful here. The cost-collapse claim is real and large. It is also being deployed by every EdTech vendor in 2026 as if it were a general license to ship content without architecture. The honest version of the claim has a structure, and the structure is the chapter.

### What collapsed

A 500-word explanation that would cost $50–$200 in faculty time to produce and review costs cents in generated text plus a structured prompt. A Quiz Me card that ran $30–$100 per item in psychometric pretest validation now runs $1–$5 with AI generation and batch faculty review. A short educational video that was $75K–$150K per 60–90 seconds for fifty years across DEKKER, Lippincott, and Elsevier internal pipelines is now roughly $30/minute at vendor pricing for Google Veo 2, or $1–$10/minute with lower-budget image-plus-TTS-plus-slide-composition pipelines.

The collapse is on the order of **three orders of magnitude** at the unit-production level for text and quiz items. The collapse for educational video is similarly large in raw production cost — vendor sources claim 70–90% reduction (Zebracat, vidBoard.ai) `[verify these specific vendor figures at draft time — pricing has moved monthly through 2025-2026]`.

### What did not collapse

Here is the part the vendor pitch decks leave out. **Design cost has not collapsed in proportion to production cost.**

What did Sesame Street's $5 buy? Not production polish. It bought *designed coherence with cognitive architecture*. Gerald Lesser's *Children and Television: Lessons from Sesame Street* (Vintage, 1974) documents the machinery: cognitive scientists on staff, Edward Palmer's research department reviewing every script with the "distractor methodology" measuring attention shifts, formative pre-air testing of every segment on the target audience, dual-channel visual+verbal alignment, high repetition across segments, rhythm and phonemic structure, narrative arc and parasocial relationships with stable characters.

That is the design layer. AI-generated content matches the unit-production cost. **Whether AI-generated content reliably matches the design discipline — temporal contiguity, signaling, segmenting, coherence — is the open bet (Question 8 in Chapter 11).** Production cost ≠ production quality. The chapter has to hold these in tension or it becomes Khan's book.

### The Bastani anchor

The cleanest available evidence that cheap content delivered through the wrong architecture *actively harms* learning is Bastani et al. 2025 (*PNAS* 122(26): e2422633122, [DOI](https://www.pnas.org/doi/10.1073/pnas.2422633122)). Roughly 1,000 Turkish high school students, three arms: no AI, GPT-4 base, GPT-Tutor with teacher-designed guardrails.

During practice, both AI conditions outperformed control: GPT-Base +48%, GPT-Tutor +127% over no-AI on practice problems.

On the **subsequent unassisted exam**: GPT-Base scored **17 percentage points below control**. GPT-Tutor was statistically indistinguishable from control.

Same content. Same students. Same AI base model. Opposite outcomes. **The variable was guardrail design.** Cheap content delivered through GPT-Base — which gives answers fluently and confidently when asked — produced measurable harm to durable learning. Cheap content delivered through GPT-Tutor — which refuses answers and gives hints — did not.

This is the through-line back to Chapter 1's IDK-IDK opening. The cost collapse argument cannot be made without the architecture argument the rest of this book delivers. Cheap content without architecture is the failure mode at industrial scale.

### Sunstein's burden-of-proof inversion

The cost-collapse asymmetry is not "cheap content lowers the burden everywhere." It is something more precise.

Sunstein 2003 (*U. Pa. L. Rev.* 151(3): 1003–1058, [Chicago Unbound](https://chicagounbound.uchicago.edu/law_and_economics/87/)) and Sunstein 2005 (*Laws of Fear*, Cambridge UP) argue that the strong precautionary principle is incoherent — it forbids action and inaction simultaneously when both carry risk. The defensible frame is cost-benefit under uncertainty, with extra precaution where outcomes are irreversible or catastrophic.

Translate that to educational content:

- **Low-stakes content** — practice items on already-mastered material, retrieval prompts that vary surface features, personalization of names and example contexts. The cost of being wrong is small and reversible. A student who encounters a slightly suboptimal practice variant on Newton's third law next Tuesday is not damaged. *Cost-collapse lowers the deployment threshold cleanly here. Produce it.*
- **High-stakes content** — initial concept acquisition, clinical decision-making content, unfamiliar domains, expertise-level adaptation, anywhere a misconception will compound. Singhal et al. 2023 ([Med-PaLM, *Nature* 620: 172–180](https://www.nature.com/articles/s41586-023-06291-2)) found high accuracy with clinically meaningful hallucination rates. Pal et al. 2025 (MedHallu, [arXiv:2502.14302](https://arxiv.org/html/2502.14302v1)) found frontier LLMs hallucinate medical content at 5–35% rates depending on adversarial setting. *Cost-collapse does not lower the deployment threshold here. Burden of proof unchanged.*

The asymmetry has a name. **Cheap content lowers the deployment threshold where wrongness is recoverable and leaves the threshold in place where wrongness compounds.** This is what Medhavy's architecture enforces operationally: AI-generated text gets light review for low-stakes content; AI-generated Case Study content is prohibited in v1.5 because case content is high-stakes; the faculty review gate is non-optional regardless of how cheaply the variants can be produced.

A chapter that argued "the cost collapse changes everything" would be the EdTech sales deck. A chapter that argued "the cost collapse changes nothing" would be the Horvath book. **The cost collapse changes some things sharply and other things not at all, and the architecture has to encode the distinction.**

---

## §2. The Binding Cost Shift

Here is the chapter's real payload. The cost-collapse argument is interesting at the unit-production level. It is *consequential* at the binding-constraint level.

When production cost collapses, the binding constraint shifts. It does not disappear. It moves. And where it moves to is the question that determines what becomes valuable to invest in.

The binding constraint shifts to **knowledge of the individual learner**.

### Sadler 2013 — the empirical anchor

The cleanest evidence is Sadler, Sonnert, Coyle, Cook-Smith & Miller 2013 (*American Educational Research Journal* 50(5): 1020–1049, [DOI](https://journals.sagepub.com/doi/abs/10.3102/0002831213477680)). 9,556 middle-school students, 181 physical-science teachers, 20 common items administered to *students and teachers* across the year.

Two findings, and the second is the one that matters.

On items **without** common misconceptions, teacher subject-matter knowledge alone predicted student gains. That is the result anyone would predict.

On items **with** common misconceptions — items where students reliably reach for a specific wrong answer — teachers who could identify the popular wrong answer produced **substantially larger student gains than teachers who only knew the right answer.** The pedagogical content knowledge — knowing what students get wrong and why — was a distinct and powerful predictor on top of subject-matter knowledge.

The AFT/American Educator summary ([2016 version](https://www.aft.org/ae/spring2016/sadler_sonnert)) puts it cleanly: teachers who anticipated student misconceptions delivered measurably larger gains. Teachers who knew the right answer but not what students get wrong did not.

### The implication for cost-collapse

When production cost approaches zero, the question is no longer "can we afford to make the variant?" The question is **"which variant should this learner see at this moment?"** That requires knowing what this learner currently believes, what wrong answer they are likely to reach for, what their current misconception risk is, and the relationship within which the right intervention will be welcomed.

AI can produce variants cheaply. AI cannot, without instrumentation, know which variant the learner needs. The misconception map is human work. It is the input the platform requires from the domain expert and the input AI cannot generate on its own.

The Hattie magnitude check supports this directionally. From *Visible Learning* (Routledge 2009, updated through MetaX 2023+): feedback at *d* ≈ 0.70, teacher-student relationships at *d* ≈ 0.62, teacher clarity at *d* ≈ 0.75, formative evaluation by teacher at *d* ≈ 0.68. Hattie's meta-meta-analysis has received fair criticism (Bergeron 2017; Wecker et al. 2017) for combining heterogeneous meta-analyses, and the numbers are approximate magnitudes. **The directional point is robust across the critique: the inputs that become more valuable when production is cheap are precisely the inputs that are not yet automatable.**

Cornelius-White 2007 (*Review of Educational Research* 77(1): 113–143, [DOI](https://journals.sagepub.com/doi/10.3102/003465430298563)) — 119 studies, 1,450 findings, 355,325 students — found mean *r* = 0.31 between learner-centered teacher-student relationship quality and student outcomes. **The relationship effect is not displaced by AI; it is amplified by it.** When the cost of acting on a teacher's judgment about *this* child falls to near zero, the teacher's judgment becomes the highest-leverage input in the system.

This is the bridge to *Trust the Teacher*. It is also the answer to the question the cost-collapse argument cannot answer on its own: *if content is cheap, what is now expensive?* Knowing the learner. Specifying what they need. Calibrating the variant to the moment. That work has not collapsed and is not going to.

---

## §3. The Minimum Viable Audience

Levin & McEwan 2001 (*Cost-Effectiveness Analysis: Methods and Applications*, 2nd ed., Sage) provides the canonical methodology for comparing educational interventions: **cost per standard-deviation gain in learning**, which converts dollars-per-student into a metric that crosses intervention types. The IES What Works Clearinghouse Cost-Effectiveness Practice Guide (2020) recommends this metric for federal funding decisions.

Run the math with AI-content economics.

At production cost ~$5/unit and a conservatively assumed *d* = 0.1 SD per unit when targeted at the right learner (~1/3 of Sesame Street's whole-curriculum effect):

$$\text{Cost per 0.1 SD per learner} = \frac{\$5}{N_{\text{learners}} \times (d/0.1)}$$

- N = 1 learner: $5 per 0.1 SD. Already comparable to Sesame Street's $1.72.
- N = 10 (a microschool cohort): $0.50 per 0.1 SD. Below Sesame Street.
- N = 100: $0.05 per 0.1 SD. An order of magnitude below the historical floor.

**The economic break-even for AI-customized educational content has collapsed to N = 1.** That is the strong form of the cost-collapse argument and it is correct at the unit-production level. The marginal-audience calculation no longer eliminates microaudiences from feasibility.

It does *not* establish that AI-customized content actually produces *d* = 0.1 SD at quality-equivalent design. That is Open Question 8, and Chapter 11 will name it as a bet awaiting direct evidence. The arithmetic is unimpeachable at the unit-production layer. The quality-equivalence claim is still adjacent evidence, not direct.

### The minimum viable audience for *this book*

The TIKTOC names the Learning Engineering community — roughly **3,600 members** as of 2026 — as the minimum viable audience for the Medhavy book itself, distributed through Kindle/$1/Kindle Unlimited. At $1/copy with KDP royalty rates (~30–70% depending on KDP Select participation and price-band), 3,600 readers generate $1,000–$2,500 in direct revenue.

The book is not financed by direct revenue. It is financed by the community feedback loop it creates and the platform deployment it enables. **This is itself an instance of the cost-collapse argument running on its author.** Twenty years ago, a field-defining monograph aimed at 3,600 readers could not amortize the production cost of a publisher-quality book. AI-assisted production — with a faculty review gate — collapses authoring cost to roughly $0 in marginal terms. The author writes. The system structures. The human reviews. The 3,600-reader audience is now economically feasible *because the cost collapse hits authoring as well as content.*

The book you are reading is itself a worked example of the chapter you are reading. The reflexive move is not decorative. It is the proof of concept.

---

## §4. The Homeschool and Micro-Audience Market

The audience size that the architecture can serve has expanded sharply. Where the audience expansion has been most consequential is the micro-audience market — homeschool families, microschools, small cohort programs that were structurally too small to amortize platform development under 2020 economics.

NCES September 2024 release ([press release Sept 17 2024](https://nces.ed.gov/whatsnew/press_releases/9_17_2024.asp)): **5.2% of U.S. children ages 5–17 received academic instruction at home in 2022–23**, up from 3.7% in 2018–19. A 40% relative increase post-COVID. Roughly 2.7M U.S. homeschooled children; microschool/pod adds an additional ~150K–500K. Total addressable U.S. micro-audience: approximately 3M children.

Current homeschool family spend runs $700–$1,800 per child per year on curriculum (DreamBox surveys, Great Homeschool Conventions data). At $5/unit AI customization × ~50 units of customized content per year per subject across 3–4 subjects = **~$750–$1,000 per child per year for fully-customized content** — *within* current spend, with full interest-matching, pace-matching, and prior-knowledge-aware adaptation. Market opening: ~3M children × $500–$1,000 per child = $1.5–3B U.S. market for AI-customized homeschool content. Outschool's revenue (~$100M, 2023) is the existing benchmark for the live-class version.

That is the optimistic frame. The honest frame is harder, and the chapter has to deliver it without flinching.

### Anki Wins for Priya on Economics

Priya is the running learner-vignette from Homes of Hope Plus One Unit 2 (the cross-book anchor we set up in Chapter 2). 19 years old, six years in a Hyderabad Homes of Hope residence, ~350-word working English vocabulary, smartphone-only, Telugu and Hindi native, applying for entry-level roles in BPO, hospital support, and NGO administration. Zero curriculum budget.

She needs a 500-word job-functional vocabulary. Spaced repetition to retain it. A human volunteer from the sector she is entering. AI as a checker — drafting, register translation, vocabulary expansion, explaining unfamiliar words — not AI as a thinker.

The full Medhavy architecture is over-engineered for Priya's learning problem in two ways. **Pedagogically:** her learning problem is well-structured vocabulary acquisition with high transfer to a known job market — exactly the case where spaced retrieval is the dominant intervention and no adaptive engine learning across (mode × concept × time) is needed. **Economically:** Priya has $0 budget. Anki is free. A Kindle book ($1) plus a Zoom volunteer (free) plus Anki (free) is the whole stack. The full architecture's $15K minimum at Project A scale fails the affordability test by four orders of magnitude.

This is the strong form of the cost-collapse argument running backwards. **Cost collapse expands the set of cases where the full architecture is economically viable. It does not expand the set of cases where the full architecture is pedagogically warranted.** For Priya, the right architecture is Anki + Kindle + a human volunteer. Three tools chosen on the complexity threshold test from Chapter 2, not on the cost-collapse argument from this chapter. The economics here confirm the pedagogical answer rather than overriding it.

---

## §5. What the Economics Do Not Change

This is the chapter's honest layer. Five things the cost collapse does not change. None of these are decorative — each one is a constraint the architecture has to keep enforcing even after the production-cost argument has done its work.

### 5.1 Burden of proof for high-stakes content

Singhal et al. 2023 ([Med-PaLM, *Nature* 620: 172–180](https://www.nature.com/articles/s41586-023-06291-2)) achieved 67.6% on MedQA; human evaluators rated most answers comparable to clinicians on factuality but identified hallucinations and bias risks at clinically meaningful rates. Pal et al. 2025 (MedHallu, [arXiv:2502.14302](https://arxiv.org/html/2502.14302v1)) found frontier LLMs hallucinate medical content at 15–35% on adversarial benchmarks; 5–15% on standard QA. The accuracy ladder is steeper at higher expertise levels: K–12 factual content is safest (dense training data, cheap verification); graduate-level domain content is most dangerous (sparse training data, expensive verification, plausible-sounding errors most likely).

Cheap production of high-stakes content does *not* clear the deployment threshold. The threshold is set by the asymmetric risk of being wrong, not by the production cost. Medical, legal, financial, regulatory, and safety-critical content retains its full burden of proof regardless of how cheap it is to generate.

### 5.2 The faculty review gate

The faculty review gate is the operational mechanism that enforces 5.1. **Pre-written, faculty-reviewed Case Study content is required by Medhavy v1.5 design.** AI-generated cases are explicitly prohibited because case content drives clinical reasoning and a hallucinated drug interaction or staging criterion propagates as a student misconception that may persist through clinical training.

Yan et al. 2024 (*BJET* 55(1): 90–112, "Practical and ethical challenges of large language models in education: A systematic scoping review") confirms the pattern: AI-generated lesson plans rate as comparable to human on structure; **systematically lower on differentiation, contextual awareness, and inclusive instructional strategies.** The gap is where pedagogical content knowledge lives. It cannot be patched with more LLM compute.

### 5.3 Domain expert curriculum design

The curriculum design layer — the concept map, the prerequisite dependencies, the phase-gate logic, the Bloom's-level assignments, the mode-appropriateness flags — is not displaced by cost-collapse. The "suggest 15 chapters" failure mode (Chapter 8 opens with this) is the proof: cheap content generated against an underspecified concept map produces an adaptive engine flying blind.

**The cost-collapse argument amplifies the value of curriculum design rather than displacing it.** When variants are cheap, the question of which variant to produce becomes the binding question — and that question is curriculum-design work, not generation work.

### 5.4 GLP instrumentation

The cost of generating a Quiz Me item or an Ask AI response has collapsed. The cost of *measuring whether that item or response produced durable learning* has not collapsed at the same rate. The decoupling problem from Chapter 5 — the artifact can no longer be trusted as sole evidence of the process that produced it — means the measurement infrastructure is more, not less, valuable as content production gets cheaper.

A platform that generates content at $5/unit and measures with engagement metrics is the IDK-IDK problem at industrial scale.

### 5.5 Institutional approval is not technical integration

This is the variable that vendor pitch decks systematically ignore. Canvas LTI 1.3 with LTI Advantage is now the standard for institutional integration; Canvas's Dynamic Registration (added 2025) eliminates manual JSON config copy-paste. The *technical* integration takes days.

The *institutional* approval — security review, legal review, accessibility review, data processing agreements — takes weeks to months. The University of Washington's November 2024–March 2025 LTI freeze is the cautionary example: institutions stop accepting new LTI integrations for months at a time when staffing gets thin or compliance review backs up. The cost-collapse argument expands the set of deployments that are *technically* feasible at low audience scale. It does not collapse the *institutional* timeline for deploying them into LMS-embedded contexts.

For a Project A or B deployment that lives outside an LMS — a homeschool family, a microschool, a co-op program — this is not the binding constraint. For a Project B or C deployment targeting credentialed institutions, **the institutional-approval timeline is now the deployment-cost variable**, not the code.

---

## §6. Worked Example — Three Projects at Three Budgets

The TIKTOC specifies three illustrative project tiers. Walk through each. Specify what gets built, what does not, and which subset of the architecture is feasible at that investment.

### Project A — $15K (Dirac Quantum Tutor)

A single-subject intelligent textbook with a contained concept map. Audience: ~500–2,000 learners (an upper-division physics course at a single institution, plus interested independent learners). Production: one principal author, ~3 months of part-time work, AI-assisted content production with one faculty reviewer.

**What it can build:**

- **Layer 1 — Content.** AI-generated text + faculty review on ~60 concept nodes. Level-3 domain specificity for the upper-division physics audience. No video; static figures only.
- **Layer 2 — Curriculum design.** One Tic TOC session producing one chapter specification with phase gates, prerequisite map, and mode-appropriateness flags. Bear-textbooks workshop pattern adapted.
- **Layer 4 — Measurement (minimum viable).** Y1 Temporal Engagement and Y6 Retrieval Strength Decay from existing LMS clickstream data plus Quiz Me ratings. Three of seven GLP components, not seven.

**What it cannot build:**

- **Layer 3 — Adaptive engine.** Skip. The bandit needs more deployment data than $15K supports for meaningful per-learner convergence. Use cold-start defaults from the concept map and let humans select modes.
- **Glimmer at full instrumentation.** Skip. No faculty time for AI pre-grading review at this budget; offer Glimmer as a manual assignment with rubric only.
- **Video and animation layer.** Skip. Below the threshold where coherence-principle review can be done well at this budget.

Project A in 2020 was not feasible. Project A in 2026 is feasible because authoring, content production, and measurement instrumentation costs all collapsed in parallel. This is the project tier where the cost-collapse argument is most consequential.

### Project B — $150K (medical school pilot)

A multi-chapter platform with adaptive engine at minimum viable scope. Audience: ~200–500 medical students, one institution, one pilot term plus one validation term. Production: principal author + 1 part-time faculty reviewer + 1 part-time engineer.

**What it can build:**

- **All four layers** at minimum viable scope.
- **~200 concept nodes** with Level-3 domain specificity, AI-generated text, faculty-reviewed Case Study cases (pre-written, AI-generation prohibited per §5.2).
- **Quiz Me and Ask AI** live; Case Study with pre-written faculty-reviewed cases; bandit running cross-mode with cold-start defaults from the concept map.
- **GLP — 3 components instrumented**, not 7. Y1 (Temporal Engagement), Y6 (Retrieval Decay), and Y2 (Error Trajectory Coherence) from quiz response patterns.

**What it cannot build:**

- **Full Glimmer term-project architecture.** Instructor-grading time is the binding constraint. Offer scaffolded Glimmer with weekly rubric review, not full pre-grading.
- **Video and animation layer at scale.** Limit to ~10 highest-leverage dynamic-concept segments.
- **Full GLP seven-component instrumentation.** Defer Y3 (Cross-Context Transfer), Y4 (Uncertainty Calibration), Y5 (Social Knowledge Texture), Y7 (Scaffolding Response Curve) to Project C.

Project B in 2020 was a $1.5M project. The collapse of content-production cost and the maturation of open-source bandit libraries (Vowpal Wabbit, CB libraries in scikit-learn-contrib) moved it to $150K in 2026. The architecture decisions are unchanged. Only the budget threshold to access them moved.

### Project C — $1.5M (full-scale platform)

What the Medhavi Hub deployment looks like with all four layers fully instrumented. Audience: multi-institutional, multi-subject, ~5,000+ learners across cohorts. Production: a small team — 3–5 engineers, 2–3 faculty reviewers across subjects, 1 instructional designer, 1 measurement engineer.

**What it builds:**

- **All four layers fully instrumented.** All seven GLP components live.
- **Glimmer with pre-grading reviewer** in the loop, scaffolded according to backwards-faded design (Chapter 6).
- **Video and animation layer** for dynamic-content concepts (physics, dynamic biological processes, time-evolution diagrams).
- **Multi-tenant Hub architecture** — multiple textbook deployments sharing infrastructure, separate institutional auth pathways.
- **Within-learner bandit** running on full reward signal with all seven GLP components weighted.

**What it still cannot build at v1.x:**

- **Cross-platform integration with hospital EMR** for clinical-rotation transfer instrumentation. This is roadmap, not v1.
- **Ambient deployment outside the platform** — museum kiosks, field trip context, co-op placements. Roadmap.

**The pedagogical move across the three tiers: the architecture decisions inside each project are unchanged. Only the budget threshold to access each architecture decision moved.** Project A at $15K was not feasible in 2020. Project B was a $1.5M project in 2020 and is a $150K project in 2026. Project C in 2020 was a $15M project and is a $1.5M project in 2026. **The collapse is in the budget threshold, not in the architecture.**

---

## §7. Common Misconceptions

### "Cost collapse means we can deploy AI-generated content everywhere"

The plausible claim: production cost is now negligible, so the marginal cost of trying AI-generated content in any context is also negligible, so the burden of proof is lower across the board.

**Why it fails.** The argument confuses production cost with deployment risk. For low-stakes content, the burden is in fact lowered — the cost of being wrong is small and recoverable. For high-stakes content, the cost of being wrong is large and may compound across cohorts. Singhal 2023 and Pal 2025 establish that frontier LLMs still hallucinate medical content at clinically meaningful rates. Bastani 2025 establishes that cheap content delivered without architecture *actively harms* learning. The deployment threshold is set by the cost of being wrong, not the cost of producing the content. Sunstein's burden-of-proof inversion is not a license to deploy. It is a structured statement about where the burden lowers and where it does not.

### "If the audience is small, the architecture is over-engineered"

The plausible claim: intelligent textbooks were built for large audiences (Khan Academy scale, MOOC scale). For a 30-student microschool, the architecture is decorative.

**Why it fails.** This was true in 2020. It is not true in 2026. The cost-collapse argument is precisely that the *minimum viable audience* has collapsed — to single-student in the limit, to 30-student-microschool comfortably. What remains true is that the *complexity threshold test* (Chapter 2) governs whether the full architecture is *pedagogically* warranted, separately from whether it is economically viable. Priya's case is the proof: economically the architecture would be affordable; pedagogically Anki + a volunteer is the right tool. **The architecture is over-engineered when the complexity threshold says it is, not when the audience is small.**

### "AI-generated content matches professionally produced content"

The plausible claim: with Mayer's CTML principles encoded in the prompt, AI-generated content has the same design discipline as professionally produced equivalents.

**Why it fails.** There is no published RCT comparing AI-generated educational content matched on Mayer's twelve principles against professionally produced equivalents with delayed retention and transfer outcomes as primary endpoints. Yan et al. 2024 found AI-generated lesson plans rate comparable on structure but systematically lower on differentiation and contextual awareness. Bryant et al. 2024 ([arXiv:2504.05449](https://arxiv.org/html/2504.05449v1)) found educators preferred AI-generated plans on surface quality and human plans on fit-to-student-need. **The cost-equivalence claim is established. The quality-equivalence claim is Open Question 8 in Chapter 11, and the honest answer in 2026 is "we do not yet know."**

---

## §8. Exercises

### Exercise 10.1 — Cost-collapse audit (Apply)

A school district administrator says: "Our new AI tutoring platform produces a 0.45 effect size on standardized assessments at $30 per student per year. That is cost-effective compared to Head Start."

Using the chapter's framework, identify three questions you must ask before accepting this claim. Frame each question against a specific argument from the chapter (Sunstein's burden-of-proof inversion, the engagement-vs-learning distinction, or the design-cost vs production-cost gap).

### Exercise 10.2 — Minimum viable audience calculation (Apply)

A medical residency program wants to build an intelligent textbook for board-exam preparation. Target audience: ~120 residents per year across 3 cohort years (~360 active learners). Available content production budget: $50,000.

(a) Specify which subset of the four-layer architecture is feasible at this budget. Name what gets built and what gets deferred. Use the Project A/B/C tiers from §6 as the scaffold.

(b) Calculate cost-per-0.1-SD assuming $50K total content production cost, 360 active learners, and *d* = 0.2 SD (a generous estimate for a well-designed intervention on board-exam material). Compare to Sesame Street's $1.72 baseline.

(c) Identify one element of the build that crosses the §5 high-stakes-content threshold and explain why faculty review of that element is non-optional regardless of cost.

### Exercise 10.3 — The institutional bottleneck (Evaluate)

A vendor proposes deploying a Medhavy-style intelligent textbook to a state university system. They estimate technical Canvas LTI 1.3 integration at $20K and three weeks of engineering time.

Using §5.5, identify what the $20K and three-week estimates leave out. Name three categories of institutional approval cost the vendor's estimate does not include, and propose a realistic timeline range from contract to deployment.

### Exercise 10.4 — Priya, revisited (Produce)

A well-meaning EdTech vendor visits Homes of Hope and proposes replacing Priya's Anki + Kindle + Zoom volunteer stack with a $50/year subscription to their AI-customized vocabulary platform.

Write a one-page memo to the Homes of Hope program director recommending whether to accept. Use the chapter's complexity threshold test and the cost-collapse asymmetry to structure the recommendation. Identify what the AI platform would and would not change about Priya's learning trajectory. Identify one circumstance under which the recommendation would flip.

### Exercise 10.5 — Audience-scale specification (Produce)

Pick a learning problem you actually know — a subject you teach, a topic you would build an intelligent textbook for, or a domain you are commissioned in. Specify:

(a) The target audience size and learner profile.
(b) The complexity threshold test answers (three questions from Chapter 2).
(c) The budget tier (Project A, B, or C) the build fits into.
(d) Which subset of the architecture is feasible at that tier.
(e) Which elements cross the §5 burden-of-proof threshold and require faculty review regardless of cost.

Hand the specification to a colleague who was not in the conversation. Ask whether they could begin a build from it. The exercise is the test of whether the chapter has made the cost-collapse argument operational.

---

## What Would Change My Mind

A high-quality RCT comparing AI-generated educational content matched on Mayer's twelve principles against professionally produced equivalents on the same concepts, with delayed retention at 90 days and transfer to novel application items as primary endpoints — pre-registered, with cost-per-0.1-SD breakdown — would settle Open Question 8 and change the chapter's hedging on the design-quality layer. If AI-generated content matched professionally produced content on delayed retention and transfer at substantially lower cost, the asymmetry would weaken; the chapter would have to soften the design-quality reservation. If AI-generated content fell behind on delayed retention and transfer at any cost level, the asymmetry would strengthen; the chapter would have to harden it. No such study exists in the peer-reviewed literature as of 2026. The Bastani-equivalent for content rather than for tutor mode would settle this.

## Still Puzzling

How much of the $5/child Sesame Street effect is design and how much is the parasocial relationship with stable characters across decades? If the latter is doing more work than the former, the AI-generated-content cost collapse does not buy back the relational layer, and the cost-collapse argument is weaker than the unit-production arithmetic suggests.

At what audience scale does the marginal-customization story stop adding value? Walkington & Bernacki 2019 (*IJAIED* 29(1): 58–88) found *d* = 0.39 favoring deep personalization for high-engagement students but *d* = −0.43 favoring surface for low-engagement students — depth-matching matters more than depth itself. The architecture has to read the learner before choosing depth, and the read takes time the smallest audiences may not have.

How fast will the institutional-approval bottleneck (§5.5) move? If Dynamic Registration adoption broadens and FERPA/COPPA compliance certifications become standardized across vendors, the institutional-deployment timeline could compress sharply. If it does not — if every new institutional deployment requires bespoke legal and security review — the binding constraint on Project B and C scale builds will remain institutional rather than technical, regardless of how cheap the content layer becomes.

---

## Bridge to Chapter 11

The architecture is complete. The economics are specified. Act Three begins.

The temptation at this point in a textbook is to claim more than the evidence supports — to assert that what has been built works as designed, because the design is internally coherent and the cost arguments support the build. Chapter 11 refuses that move.

Honesty about what is not yet known is the position consistent with the book. The next chapter delivers it. Eight open questions the platform is designed to answer, what adjacent evidence each rests on, what direct evidence does not yet exist, and what a published RCT would have to look like to settle it. The Montaigne register the chapter takes is not a hedge. It is the strongest epistemic position the book can hold at this stage of the deployment — *que sais-je?* applied to a platform that has just been described as if it were finished.

After Chapter 11 names the gaps, Chapter 12 delivers the instrument that converts the architecture, the economics, and the honest inventory into a specification a developer can build from. The map. The conversation the platform was built to enable.

---

**Tags:** intelligent-textbook, cost-collapse, educational-economics, Sesame-Street, pedagogical-content-knowledge, minimum-viable-audience
