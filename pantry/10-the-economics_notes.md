# Research Notes — Chapter 10: The Economics of Intelligent Textbooks

*Research note for the Medhavy book project. Companion to `educational-media-economics-research.md`, `domain-specific-instruction-research.md`, and the Homes of Hope Plus One pantry. Compiled 2026-05-17 for the Chapter Writer pipeline. Author: research subagent for Nik Bear Brown.*

> **Reader's compass.** This chapter has one job and a difficult honest layer. The job: argue that AI-generated content has collapsed the production-cost floor that Sesame Street established for forty years, and walk the reader through what that does — and does not — change. The honest layer: the cost-collapse claim is provable at the unit-production level and *not yet established* at the production-equivalent-quality level. The chapter has to make the economic argument without overclaiming the quality argument, because if it does the latter, the book becomes Khan's book. Treat the Sesame Street number as ground truth (Mares & Pan 2013; Kearney & Levine 2019). Treat the $5/AI-unit number as plausible-for-first-draft, contested-for-quality-equivalent. Treat the audience-size argument as the strong part — when fixed cost approaches zero, the minimum-viable audience collapses to one. Treat the binding-constraint shift (production cost → knowledge of the individual learner) as the chapter's real payload, because that is what tells the reader where to invest if they take the cost collapse seriously.

---

## §1. The opening case — Sesame Street as the forty-year floor

### 1.1 The number the chapter opens with `[Sesame-Street]` `[cost-effectiveness]`

The number is **$5 per child per year** in inflation-adjusted dollars, sustained from the late 1970s through the present. It is the most cost-effective educational intervention ever documented at scale.

- **Production budget (recent seasons):** ~$25M/year for ~26 episodes (~$960K–$1M per episode) ([Slate 2012](https://slate.com/business/2012/01/does-sesame-street-lose-money.html); [Hollywood Reporter 2019](https://www.hollywoodreporter.com/news/general-news/sesame-street-gets-funding-how-it-went-broke-1183032/)).
- **Reach (global, co-productions):** ~156M children/year through ~30 co-productions including *Plaza Sésamo*, *Galli Galli Sim Sim*, *Iftah Ya Simsim* (Bridgespan case study).
- **Production cost per child:** $25M ÷ 156M = **$0.16/child/year for production**. Adaptation, distribution, licensing, formative research bring total to ~**$5/child/year**.
- **Effect size:** *d* ≈ 0.29 across 24 studies, 10,000+ children, 15 countries (Mares & Pan 2013, *J. Applied Developmental Psychology* 34(3): 140–151, [DOI](https://www.sciencedirect.com/science/article/abs/pii/S0193397313000026)). Cognitive *d* = 0.27; learning about the world *d* = 0.30; social attitudes *d* = 0.31. Effect is virtually identical in low/middle-income (0.29) and high-income (0.285) countries.
- **Cost per 0.1 SD gain:** $5 ÷ 2.9 = **$1.72/child** — roughly 300–500× more cost-effective per 0.1 SD than high-dose tutoring (Nickow, Oreopoulos & Quan 2024, *d* ≈ 0.37 at ~$2,000–$3,500/child = $540–$945/0.1 SD).

### 1.2 The long-run causal evidence `[Sesame-Street]`

Kearney & Levine 2019 (*AEJ: Applied Economics* 11(1): 318–350, [DOI](https://www.aeaweb.org/articles?id=10.1257/app.20170300)) exploits geographic variation in 1969 PBS reception (VHF strong-signal vs. UHF weak-signal counties) as a natural experiment. **Headline:** preschool-age children in strong-reception counties were **14% less likely to be behind their expected grade level** decades later, with effects driven primarily by boys and Black children. Long-run educational and labor-market outcomes directionally positive but statistically imprecise. **Comparison to Head Start:** Sesame Street's grade-for-age effect is *comparable in magnitude* to Head Start's, at **~1,500–2,000× lower cost** ($5 vs. $8,500–$10,000/child/year for Head Start; $18,500/child/year for Perry/Abecedarian).

This is the cost-effectiveness fact the chapter is built on. It is the strongest single number in the educational-media literature, and the chapter should treat it as ground truth — multi-method, multi-decade, multi-replication.

### 1.3 What $5/child actually bought — the machinery `[Sesame-Street]`

The $5 paid for **designed coherence with cognitive architecture**, not for production polish per se. Gerald Lesser's *Children and Television: Lessons from Sesame Street* (Vintage, 1974) documents the machinery: cognitive scientists on staff (Edward Palmer's research department reviewed every script with the "distractor methodology" measuring attention shifts); formative pre-air testing of every segment on the target audience; dual-channel processing (visual+verbal aligned); high repetition (each concept across multiple segments per week); rhythm and phonemic structure (letters chanted, not just shown); narrative arc and parasocial relationships with stable characters.

**For Medhavi:** this is the quality target the AI production transition has to clear. If AI-generated content cannot reliably produce dual-channel alignment, formative validation, signaling and temporal contiguity, then "$5/unit at professional quality" is a claim about a different kind of quality — engagement quality, perhaps, or polish quality — not learning quality. The chapter should be explicit about this. Sesame Street is the floor *and* the design standard. AI matches the floor in cost. Whether AI matches the standard in design is the open bet.

---

## §2. The cost collapse — the asymmetry the chapter argues

### 2.1 The production-cost numbers, by example `[AI-generated-content]` `[cost-effectiveness]`

The chapter needs specific examples to anchor the abstraction. The honest brackets are roughly:

- **$0.10–$1/unit — generated text explanation.** A 500-word AI-generated explanation of a concept, with retrieval-augmented grounding to a textbook, costs cents at current GPT-4o-mini pricing. Producing the same explanation from a domain expert: ~$50–$200 if it goes through review.
- **$1–$10/unit — generated assessment item.** An AI-generated Quiz Me card or short worked example, faculty-reviewed in batch, costs ~$1–$5 per item with structured prompting; professionally authored multiple-choice items in psychometric literature run $30–$100 per item with pretest validation (NBME estimates for high-stakes item authoring).
- **$5–$30/unit — generated short educational video.** Google Veo 2 at $0.50/second = $30/minute of generated video ([vidpros pricing summary](https://vidpros.com/breaking-down-the-costs-creating-1-minute-videos-with-ai-tools/)). Synthesia avatar-based: $20–$300/month subscription. Lower-budget pipelines (image generation + TTS + slide composition): $1–$10/minute. **Per-unit historical comparison:** Professional educational video production cost ~$75,000–$150,000 per 60–90 second segment for fifty years (medical education vendor estimates; consistent across DEKKER, Lippincott, Elsevier internal pipelines).
- **$50–$500/unit — generated case study or Glimmer scaffolding.** Pre-written, faculty-reviewed clinical case with AI scaffolding around it. Most of the cost is faculty time, not AI generation.
- **$5,000–$50,000/unit — Sesame Street-quality animation segment.** The floor that the cost collapse claims to displace. Most of this cost is design, formative research, and review — not raw production.

**The verification flag.** The most defensible cost-collapse claim in the chapter is for *text generation* and *quiz item generation*, where the cost has genuinely collapsed three orders of magnitude. The least defensible is *animation at Sesame-Street design quality*, where the production cost has fallen but the *design cost* (formative research, coherence-principle enforcement, signaling enforcement) has not collapsed in proportion. The chapter should hold these in tension. Verify cost numbers against vendor pricing pages at draft time — pricing has been moving monthly through 2025–2026.

### 2.2 The asymmetry — burden of proof `[precautionary-principle]`

Sunstein 2005 (*Laws of Fear*, Cambridge UP) and Sunstein 2003 (*U. Pa. L. Rev.* 151(3): 1003–1058, [Chicago Unbound](https://chicagounbound.uchicago.edu/law_and_economics/87/)) make the cleanest available argument that the strong precautionary principle is incoherent (it forbids action and inaction simultaneously when both carry risk). The defensible frame is cost-benefit under uncertainty, with extra precaution for irreversible or catastrophic outcomes.

**Translation to AI-generated educational content.** When production cost approaches zero, the question "should we produce this?" no longer turns on whether the production cost is justified. It turns on whether the *risk of being wrong* is acceptable. The asymmetry the chapter argues:

- **Low-stakes content** (interest-matched practice items on already-mastered material, retrieval prompts, surface personalization of names and contexts): the cost of being wrong is small and reversible. The cost-collapse lowers the deployment threshold cleanly. *Produce it.*
- **High-stakes content** (initial concept acquisition, clinical decision-making, content where a misconception will compound, unfamiliar domains, expertise-level adaptation): the cost of being wrong is large and may be irreversible. Singhal et al. 2023 (*Nature* 620: 172–180) found Med-PaLM produced wrong answers in ~1/7 cases with the same fluent confidence as correct ones. Pal et al. 2025 (MedHallu, arXiv:2502.14302) found frontier LLMs hallucinate medical content at 5–35% rates depending on adversarial setting. The cost-collapse does **not** lower the deployment threshold here. *Burden of proof unchanged.*

**This is Sunstein's burden-of-proof inversion applied to AI educational content.** The argument is *not* "cheap content lowers the burden everywhere." It is "cheap content lowers the burden where wrongness is recoverable and leaves the burden in place where wrongness compounds." The chapter should be explicit that this is the architecture Medhavy enforces: AI-generated text is licensed at light review for low-stakes content; AI-generated cases are prohibited in v1.5 because case content is high-stakes; faculty review gates the high-stakes layer regardless of production cost.

### 2.3 Bastani as the in-the-wild proof `[AI-generated-content]`

Bastani et al. 2025 (*PNAS* 122(26): e2422633122, [DOI](https://www.pnas.org/doi/10.1073/pnas.2422633122)) is the cleanest available evidence that the cost-collapse *does not by itself* produce learning. ~1,000 Turkish high school students, three arms: no AI, GPT-4 base, GPT-Tutor with teacher-designed guardrails. During practice: GPT-Base +48%, GPT-Tutor +127% over no-AI. **On subsequent unassisted exam:** GPT-Base **−17 percentage points** vs. control; GPT-Tutor statistically indistinguishable from control. Same AI. Same content. Opposite outcomes. The variable was the guardrail design.

For the chapter: cheap content delivered through the wrong architecture *actively harms learning*. The cost-collapse argument cannot be made without the architecture argument the rest of the book delivers. This is the through-line back to the IDK-IDK opening case.

---

## §3. The binding cost shift — the chapter's payload

### 3.1 What becomes the binding constraint when production cost collapses `[teacher-knowledge]`

The argument the chapter has to land cleanly: **when production cost collapses, the binding constraint shifts to *knowledge of the individual learner*.** This is the move that converts the cost-collapse argument from a Khan-style optimism into a design specification.

The cleanest empirical anchor is **Sadler, Sonnert, Coyle, Cook-Smith & Miller 2013** (*American Educational Research Journal* 50(5): 1020–1049, [DOI](https://journals.sagepub.com/doi/abs/10.3102/0002831213477680)). 9,556 middle-school students; 181 physical-science teachers; 20 common items; pre/post administered to students *and teachers* across the year.

**Two findings.**

- On items **without** common misconceptions, teacher subject-matter knowledge alone predicted student gains.
- On items **with** common misconceptions, teachers who could identify the popular wrong answer produced **substantially larger** student gains than teachers who only knew the right answer. The pedagogical content knowledge — knowing what students get wrong and why — was a distinct and powerful predictor.

The chapter can quote the Sadler et al. AFT/American Educator summary ([2016 AFT version](https://www.aft.org/ae/spring2016/sadler_sonnert)): teachers who anticipated student misconceptions delivered measurably larger gains; teachers who knew the correct answer but not what students get wrong did not. **The chapter's move:** when production cost ≈ 0, the bottleneck on learning is *which variant to deliver to which learner at which moment*. That requires knowing the learner's current state, their interest, their misconception risk, and the relationship within which the right intervention will be welcomed. AI can produce variants cheaply; AI cannot, without instrumentation, know which variant the learner needs.

### 3.2 The Hattie magnitude check `[teacher-knowledge]`

Hattie's *Visible Learning* (Routledge 2009, updated through MetaX 2023+). Effect sizes on the inputs the cost-collapse argument shifts toward:

- Feedback: *d* ≈ 0.70.
- Teacher-student relationships: *d* ≈ 0.62 (Cornelius-White 2007 finds *r* = 0.31).
- Teacher clarity: *d* ≈ 0.75.
- Formative evaluation by teacher: *d* ≈ 0.68.

Caveats Hattie's meta-meta has received (Bergeron 2017, Wecker et al. 2017): combining heterogeneous meta-analyses without enough attention to comparability. The numbers are approximate magnitudes; the directional point is robust across the critique. The chapter's use: **the inputs that become more valuable when production is cheap are precisely the inputs that are *not yet automatable* — feedback calibrated to a specific learner, relationship-mediated trust, clarity about what *this* student needs.** This is the bridge to the Trust the Teacher book and to Medhavy's Chapter 12 design conversation.

### 3.3 Cornelius-White 2007 — the relationship anchor `[teacher-knowledge]`

Cornelius-White 2007 (*Review of Educational Research* 77(1): 113–143, [DOI](https://journals.sagepub.com/doi/10.3102/003465430298563)). 119 studies, 1,450 findings, 355,325 students. Mean *r* = 0.31 between learner-centered teacher-student relationship quality and student outcomes. Effect larger for affective and behavioral outcomes than purely cognitive, but positive across all three. **For the chapter:** the relationship effect is not displaced by AI; it is amplified by it. The teacher's judgment about *this* child becomes the highest-leverage input when the cost of acting on that judgment falls to near zero.

---

## §4. Minimum viable audience — the arithmetic

### 4.1 The break-even calculation `[cost-effectiveness]`

Levin & McEwan 2001 (*Cost-Effectiveness Analysis: Methods and Applications*, 2nd ed., Sage) provides the canonical methodology. The comparable unit is **cost per standard-deviation gain in learning**, which converts dollars-per-student into a metric that crosses intervention types. The IES What Works Clearinghouse Cost-Effectiveness Practice Guide (2020) recommends this metric.

**The AI-content math.** With production cost ~$5/unit and a conservatively assumed *d* = 0.1 SD per unit when targeted at the right learner (~1/3 of Sesame Street's whole-curriculum effect):

$$\text{Cost per 0.1 SD per learner} = \frac{\$5}{\text{N learners} \times (d/0.1)}$$

- N = 1: $5/0.1 SD. Already comparable to Sesame Street's $1.72.
- N = 10 (a microschool cohort): $0.50/0.1 SD.
- N = 100: $0.05/0.1 SD — an order of magnitude below Sesame Street.

**The economic break-even has collapsed to N = 1.** This is the strong form of the cost-collapse argument and it is correct at the level of unit production. The chapter should treat it as established.

### 4.2 The Learning Engineering community as minimum viable audience for *this book* `[cost-effectiveness]`

From the TIKTOC: ~**3,600 Learning Engineering community members** is the minimum viable audience for the Medhavy book itself, distributed through Kindle/$1/Kindle Unlimited. At $1/copy with KDP royalty rates (~30–70% depending on KDP Select participation and price-band), ~3,600 readers generate $1,000–$2,500 in direct revenue. The book is not financed by direct revenue; it is financed by the community feedback loop it creates and the platform deployment it enables.

**This is itself an instance of the cost-collapse argument.** Twenty years ago, a field-defining monograph aimed at 3,600 readers could not amortize the production cost of a publisher-quality book. AI-assisted production (with a faculty review gate) collapses that production cost to roughly $0 in marginal terms — the author writes, the system structures, the human reviews. The 3,600-reader audience is now economically feasible *because the cost-collapse hits authoring as well as content*.

### 4.3 The three-project worked example `[cost-effectiveness]`

The TIKTOC specifies three illustrative projects for the chapter's worked example:

- **Project A — $15K (Dirac Quantum Tutor).** Single-subject intelligent textbook with a contained concept map. What it can build: Layer 1 (content with Level-3 specificity, AI-generated text + faculty review on ~60 concept nodes); Layer 2 (Tic TOC session producing one chapter spec with phase gates); Layer 4 (minimum viable measurement layer — Y1 temporal engagement, Y6 retrieval decay from existing LMS clickstream + Quiz Me ratings). What it cannot build: Layer 3 (no adaptive engine — the bandit needs more deployment data than $15K supports); Glimmer (no faculty time for AI pre-grading review at this budget).
- **Project B — $150K (medical school pilot).** Multi-chapter platform with adaptive engine at minimum viable scope. What it can build: all four layers; ~200 concept nodes; Quiz Me + Ask AI live; Case Study with pre-written faculty-reviewed cases; bandit running cross-mode with cold-start defaults. What it cannot build: full Glimmer term-project architecture (instructor-grading time is the binding constraint); video and animation layer at scale; full GLP seven-component instrumentation (likely 3 components, not 7).
- **Project C — $1.5M (full-scale platform).** What the Medhavi Hub deployment looks like with all four layers fully instrumented, Glimmer with pre-grading reviewer, Video/Animation layer for dynamic-content concepts, full seven-component GLP, multi-tenant Hub architecture. What it still cannot build: cross-platform integration with hospital EMR for clinical-rotation transfer instrumentation (this is roadmap, not v1).

The pedagogical move: **what cost-collapse changes is which projects are feasible at which budget tiers.** Project A at $15K was not feasible in 2020; it is feasible in 2026. Project B was a $1.5M project in 2020; it is a $150K project in 2026. The architecture decisions inside each project are unchanged — only the budget threshold to access each architecture decision has moved.

### 4.4 The homeschool and micro-audience market `[homeschool]` `[cost-effectiveness]`

NCES 2024 release ([press release Sept 2024](https://nces.ed.gov/whatsnew/press_releases/9_17_2024.asp)): ~5.2% of U.S. children ages 5–17 received academic instruction at home in 2022–23, up from 3.7% in 2018–19 — a 40% relative increase post-COVID. ~2.7M U.S. homeschooled children; microschool/pod adds ~150K–500K. Total addressable U.S. micro-audience ~3M.

Current homeschool family spend ~$700–$1,800/child/year on curriculum (DreamBox surveys, Great Homeschool Conventions data). At $5/unit AI customization × ~50 units of customized content/year/subject across 3–4 subjects = **~$750–$1,000/child/year for fully-customized content** — *within* current spend, with full interest-matching, pace-matching, and prior-knowledge-aware adaptation. **Market opening:** ~3M children × $500–$1,000/child/year addressable = $1.5–3B U.S. market for AI-customized homeschool content. Outschool's revenue (~$100M, 2023) is the existing benchmark for the live-class version.

### 4.5 The Homes of Hope case — Anki wins on economics, not just pedagogy `[homeschool]` `[cost-effectiveness]`

This is the cross-book anchor. Homes of Hope Plus One (Unit 2: "AI as Work Tool"; running learner-vignette Priya) is the minimum-viable case where the architecture *does not* clear the complexity threshold and a simpler tool wins.

Priya's profile from the HoH+1 chapters: 19 years old, six years in a Hyderabad Homes of Hope residence, ~350-word working English vocabulary, smartphone-only, Telugu and Hindi native, applying for BPO/healthcare/NGO entry-level roles, zero curriculum budget. The HoH+1 book's argument: she needs a 500-word job-functional vocabulary, spaced repetition to retain it, a human volunteer from the sector she is entering, and AI as a checker (drafting + register translation + vocabulary expansion + explaining unfamiliar words) — not AI as a thinker.

**Why Anki wins for Priya on economics.** The full Medhavy architecture is over-engineered for Priya's learning problem in two ways. (1) **Pedagogically:** her learning problem is well-structured vocabulary acquisition with high transfer to a known job market — exactly the case where spaced retrieval is the dominant intervention (Roediger & Karpicke 2006; Cepeda 2006/2008; Kerfoot et al. 2010 in the medical analog). No adaptive engine learning across (mode × concept × time) is needed when one mode is the right mode. (2) **Economically:** Priya has $0 budget. Anki is free. A Kindle book ($1) plus a Zoom volunteer (free) plus Anki (free) is the whole stack. The full architecture's $15K minimum even at Project A scale fails the affordability test by four orders of magnitude.

**This is the strong form of the cost-collapse argument running backwards.** Cost collapse makes intelligent textbooks viable for previously too-small audiences (Project A is feasible where it was not). It does not make intelligent textbooks the right tool for every learning problem. For Priya, the right architecture is Anki + Kindle + a human volunteer — three tools chosen on the *complexity threshold test* (Chapter 2), not on the cost-collapse argument. The chapter should be explicit: the cost-collapse argument expands the *set of cases* where the full architecture is economically viable; it does not expand the *set of cases* where the full architecture is pedagogically warranted.

The cross-book reference is: see HoH+1 Unit 2 for the running Priya vignette and the Anki-plus-volunteer architecture; see Medhavy Chapter 2 for the complexity threshold test that produces this answer; see this chapter for why the economics confirm the pedagogical answer rather than overriding it.

---

## §5. What economics do NOT change

This is the chapter's honest layer. The cost-collapse argument is real and large. Five things it does not change.

### 5.1 Burden of proof for high-stakes content `[precautionary-principle]`

Singhal et al. 2023 (Med-PaLM, *Nature* 620: 172–180, [Nature link](https://www.nature.com/articles/s41586-023-06291-2)). Med-PaLM achieved 67.6% on MedQA; human evaluators rated most answers comparable to clinicians on factuality but identified hallucinations and bias risks at clinically meaningful rates. Pal et al. 2025 (MedHallu, arXiv:2502.14302, [arXiv](https://arxiv.org/html/2502.14302v1)). Frontier LLMs hallucinate medical content at 15–35% on adversarial benchmarks; 5–15% on standard QA. The accuracy ladder is steeper at higher expertise levels: K–12 factual content is safest (dense training data, cheap verification); graduate-level domain content is most dangerous (sparse training data, expensive verification, plausible-sounding errors most likely).

**Implication for the chapter.** Cheap production of high-stakes content does *not* clear the deployment threshold. The threshold is set by the asymmetric risk of being wrong (§2.2), not by the production cost. Medical, legal, financial, regulatory, and safety-critical content retains its full burden of proof regardless of how cheap it is to generate. This is the principled answer to the question "if AI-generated content is so cheap, why don't we just deploy it everywhere?"

### 5.2 Faculty review gate `[AI-generated-content]`

The faculty review gate is the operational mechanism that enforces §5.1 in Medhavy specifically. **Pre-written, faculty-reviewed Case Study cases are required by v1.5 design** — AI-generated cases are explicitly prohibited because case content drives clinical reasoning and a hallucinated drug interaction or staging criterion propagates as a student misconception that may persist through clinical training. Yan et al. 2024 (*BJET*, "Practical and ethical challenges of large language models in education: A systematic scoping review") confirms the pattern: AI-generated lesson plans rate as comparable to human on structure; **systematically lower on differentiation, contextual awareness, and inclusive instructional strategies**. The gap is where pedagogical content knowledge lives. It cannot be patched with more LLM compute.

### 5.3 Domain expert curriculum design `[curriculum-design]`

The chapter has to defend the position that *curriculum design itself* — the work of producing the concept map, the prerequisite dependencies, the phase-gate logic, the Bloom's-level assignments, the mode-appropriateness flags — is not displaced by cost-collapse. The "suggest 15 chapters" failure mode (Chapter 8 opens with this) is the proof. Cheap content generated against an underspecified concept map produces an adaptive engine flying blind. The curriculum design layer requires human expertise about *what to teach in what order and why*. AI is excellent at producing variants; AI without instrumentation cannot tell which variant should land first.

The cost-collapse argument *amplifies* the value of curriculum design rather than displacing it. When variants are cheap, the question of which variant to produce becomes the binding question — and that question is curriculum-design work.

### 5.4 GLP instrumentation `[measurement]`

Genuine Learning Probability instrumentation is the seven-component measurement layer the book has built. The cost of generating a Quiz Me item or an Ask AI response has collapsed. The cost of *measuring whether that item or response produced durable learning* has not collapsed at the same rate. The decoupling problem (Chapter 5 opens with this) — the artifact can no longer be trusted as sole evidence of the process that produced it — means the measurement infrastructure is more, not less, valuable as content production gets cheaper. A platform that generates content at $5/unit and measures with engagement metrics is the IDK-IDK problem at industrial scale.

### 5.5 The arms-race risk `[precautionary-principle]`

Carr 2010 (*The Shallows*) and Risko & Gilbert 2016 (*Trends in Cognitive Sciences* 20(9): 676–688, "Cognitive Offloading") establish that habits of relying on a tool can degrade the underlying skill. Bastani's GPT-Base condition is the within-session instance of this. The cost-collapse makes it cheap to deploy interventions that *feel* helpful while *producing* offloading. The asymmetric-risk frame is the only defense: when content production is cheap, it is *easier* to produce content that harms learning while looking like it helps. The measurement infrastructure is the only thing that can tell the difference. This is the recursive argument for why the architecture chapters precede the economics chapter rather than the reverse.

---

## §6. Verification flags and open questions

### 6.1 Numbers to verify at draft time `[verify]`

- **Sesame Street $5/child/year.** Verify against current Sesame Workshop financials and the Bridgespan case study. Cooney 1968 budget memo ($28K/episode = ~$230K in 2025) is the historical anchor.
- **AI content production cost figures.** Pricing has moved monthly through 2025–2026. Verify against current Veo, Sora, Synthesia, and OpenAI API pricing pages at draft time. The peer-reviewed *educational* AI video production cost literature is largely absent; vendor sources are 70–90% reduction claims (Zebracat, vidBoard.ai) that should be tagged as vendor-derived.
- **NCES homeschool 5.2% figure.** The September 2024 NCES press release is the canonical source; verify against any 2025–2026 update.
- **Sadler et al. 2013 sample sizes.** 9,556 students, 181 teachers, 20 common items — confirmed against ResearchGate version ([researchgate link](https://www.researchgate.net/publication/276891366)).
- **Kearney & Levine 14% grade-for-age effect.** Confirmed in AEJ paper; the comparison to Head Start is in the published article.
- **Hattie 0.70 feedback / 0.62 relationship effect sizes.** Verify against MetaX 2023+ update; the magnitudes have moved slightly in later updates.

### 6.2 Open questions the chapter raises but does not resolve

- *Does AI-generated educational content produce durable learning outcomes comparable to professionally produced content?* (Open bet #8 from Chapter 11. Not resolved by cost-collapse — only by deployment measurement.)
- *Does the $5/unit production cost preserve Sesame Street-comparable design quality?* (No published evidence as of 2026. The chapter should be explicit that production cost and production quality are not the same metric.)
- *At what audience scale does the marginal-customization story stop adding value?* (Walkington & Bernacki 2019 show *d* = 0.39 favoring deep personalization for high-engagement students but *d* = −0.43 favoring surface for low-engagement students — depth-matching matters more than depth itself.)

### 6.3 What would change the chapter's reading

A high-quality RCT comparing AI-generated educational content matched on Mayer's twelve principles against professionally produced equivalents, with delayed retention and transfer outcomes, would settle Open Bet #8 and change the chapter's hedging. The Bastani-equivalent for content rather than for tutor mode. Pre-registration desirable. No such study exists in the peer-reviewed literature as of 2026.

---

## §7. Consolidated citations and pantry cross-reference

### 7.1 Existing pantry sources (cite by filename)

- `educational-media-economics-research.md` — Sesame Street primary evidence, Mayer CTML, cost-collapse asymmetry, minimum viable audience arithmetic, Sunstein burden-of-proof inversion, homeschool market data. Heavy use throughout this chapter.
- `domain-specific-instruction-research.md` — Sadler 2013 pedagogical content knowledge, PCK theoretical anchor, Level-3 specificity. Use for §3.
- `_lib_co-intelligence__living_and_working_with_ai.md` (Mollick) — human+AI framing for the Conductor argument; relevant for §3.
- HoH+1 pantry (cross-reference) — Priya case, Anki-plus-volunteer architecture, complexity threshold worked example.

### 7.2 New citations introduced in this note (Chicago author-date, link-bearing)

Bastani, Hamsa, Osbert Bastani, Alp Sungu, Haosen Ge, Özge Kabakcı, and Rei Mariman. 2025. "Generative AI without guardrails can harm learning: Evidence from high school mathematics." *PNAS* 122(26): e2422633122. [https://www.pnas.org/doi/10.1073/pnas.2422633122](https://www.pnas.org/doi/10.1073/pnas.2422633122)

Cornelius-White, Jeffrey H. D. 2007. "Learner-Centered Teacher-Student Relationships Are Effective: A Meta-Analysis." *Review of Educational Research* 77(1): 113–143. [https://journals.sagepub.com/doi/10.3102/003465430298563](https://journals.sagepub.com/doi/10.3102/003465430298563)

Hattie, John. 2009. *Visible Learning: A Synthesis of Over 800 Meta-Analyses Relating to Achievement.* Routledge.

Kearney, Melissa S., and Phillip B. Levine. 2019. "Early Childhood Education by Television: Lessons from Sesame Street." *American Economic Journal: Applied Economics* 11(1): 318–350. [https://www.aeaweb.org/articles?id=10.1257/app.20170300](https://www.aeaweb.org/articles?id=10.1257/app.20170300)

Levin, Henry M., and Patrick J. McEwan. 2001. *Cost-Effectiveness Analysis: Methods and Applications.* 2nd ed. Sage.

Mares, Marie-Louise, and Zhongdang Pan. 2013. "Effects of *Sesame Street*: A Meta-Analysis of Children's Learning in 15 Countries." *Journal of Applied Developmental Psychology* 34(3): 140–151. [https://www.sciencedirect.com/science/article/abs/pii/S0193397313000026](https://www.sciencedirect.com/science/article/abs/pii/S0193397313000026)

National Center for Education Statistics. 2024. "A Higher Percentage of K–12 Students are Receiving Academic Instruction at Home." IES Press Release, September 17. [https://nces.ed.gov/whatsnew/press_releases/9_17_2024.asp](https://nces.ed.gov/whatsnew/press_releases/9_17_2024.asp)

Nickow, Andre, Philip Oreopoulos, and Vincent Quan. 2024. "The Promise of Tutoring for PreK–12 Learning: A Systematic Review and Meta-Analysis of the Experimental Evidence." *American Educational Research Journal* 61(1): 74–107.

Pal, Ankit, et al. 2025. "MedHallu: A Comprehensive Benchmark for Detecting Medical Hallucinations in Large Language Models." Preprint, arXiv:2502.14302. [https://arxiv.org/html/2502.14302v1](https://arxiv.org/html/2502.14302v1)

Sadler, Philip M., Gerhard Sonnert, Harold P. Coyle, Nancy Cook-Smith, and Jaimie L. Miller. 2013. "The Influence of Teachers' Knowledge on Student Learning in Middle School Physical Science Classrooms." *American Educational Research Journal* 50(5): 1020–1049. [https://journals.sagepub.com/doi/abs/10.3102/0002831213477680](https://journals.sagepub.com/doi/abs/10.3102/0002831213477680). AFT/American Educator summary: [https://www.aft.org/ae/spring2016/sadler_sonnert](https://www.aft.org/ae/spring2016/sadler_sonnert)

Singhal, Karan, et al. 2023. "Large Language Models Encode Clinical Knowledge." *Nature* 620: 172–180. [https://www.nature.com/articles/s41586-023-06291-2](https://www.nature.com/articles/s41586-023-06291-2)

Sunstein, Cass R. 2005. *Laws of Fear: Beyond the Precautionary Principle.* Cambridge University Press.

Sunstein, Cass R. 2003. "Beyond the Precautionary Principle." *University of Pennsylvania Law Review* 151(3): 1003–1058. [https://chicagounbound.uchicago.edu/law_and_economics/87/](https://chicagounbound.uchicago.edu/law_and_economics/87/)

Yan, Lixiang, et al. 2024. "Practical and ethical challenges of large language models in education: A systematic scoping review." *British Journal of Educational Technology* 55(1): 90–112.

---

*End of research note for Chapter 10. ~4,900 words.*
