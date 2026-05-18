# Research Notes — Chapter 9: The Content Layer

*TIKTOC filename `10-the-content-layer.md`. Bloom's level: Evaluate. Not flagged load-bearing; the chapter inherits its heaviest evidence base from `domain-specific-instruction-research.md` (Ch 9 heavy use) and `educational-media-economics-research.md` (Ch 9 light use, Ch 10 heavy use — flagged for Batch 4 coordination). Compiled 2026-05-17.*

---

## A. Concept under examination — what the chapter teaches

The reader learns:

1. **Why content comes last in the four-layer architecture.** The book has deferred content to Chapter 9 deliberately. Most authors want to start here — content is what an author has, what an author knows, what an author is proud of. The architecture argument is that content is one layer among four, and the least interesting design decision *if the other three layers are wrong*. Saying so is the chapter's opening posture.
2. **The domain-specificity finding** — Level 1 (generic) vs. Level 2 (generic with a domain capstone) vs. Level 3 (domain-specific throughout, with a generic backbone). The evidence base supports Level 3 as capturing the bulk of transfer and motivation benefits at modestly higher production cost.
3. **The cost-collapse asymmetry.** AI content at ~$5/unit (a placeholder cost; verify against current Veo/Sora pricing) changes the burden of proof for content production *asymmetrically*. Low-risk content has its burden lowered. High-risk content does not. The chapter spells out what counts as which.
4. **The AI-generation policy.** Which content elements can be AI-generated with light review, which require domain-expert authorship, where the faculty review gate is not optional.
5. **The Sesame Street standard.** $5/child/year producing measurable learning gains, set against AI-generated content's *unknown* effectiveness for initial concept acquisition. Naming this as an open bet rather than a claim.
6. **The minimum viable content layer.** What the curriculum design layer (Ch 8) requires from the content layer — and what is sufficient to start a Medhavy deployment.

Bloom's level: Evaluate. The reader should leave able to assess an AI-generated content sample against the vetting requirements the evidence base specifies, and to specify the content layer for a given Medhavy build.

---

## B. Specification move — pulling apart vague terms

Terms doing too many jobs:

- **Content.** In platform speak, content is "what fills the screen" — text, video, audio, interactive elements. The chapter should use the narrower sense: *content is the substrate on which the engine and the modes operate*. A textbook passage, a worked example, a case scenario, a Quiz Me item, a Glimmer rubric — each is content. The platform UI is not content. The reward function is not content. Content is what the student reads, watches, or works with directly.
- **AI-generated.** "AI-generated" collapses three distinct production processes: (a) AI-drafted, human-reviewed-and-revised; (b) AI-drafted, human-light-reviewed; (c) AI-drafted, no human review. The chapter must keep these distinct because the evidence base treats them very differently.
- **Domain-specific.** The Sadler 2013 / PCK literature distinguishes Level 1 (no domain content; generic skills only), Level 2 (generic skills plus one domain capstone), Level 3 (generic skills woven through domain content from the start). The chapter should use this three-level taxonomy; "domain-specific" without the level is too vague.
- **Production cost.** Per-unit content production cost has collapsed for some kinds of content (text, basic explanatory video, image generation) and not for others (high-production-value studio video; original empirical illustration; expert-vetted case scenarios). The chapter must specify which content type's cost has collapsed and which has not.
- **Burden of proof.** The phrase invokes a legal-philosophical framework (Sunstein's *Laws of Fear*). The chapter should use it precisely: the burden of proof is the evidence threshold required *before deployment*, and it shifts with the asymmetry of the failure mode (Sunstein 2003, 2005 — see §E).
- **Minimum viable.** "Minimum viable" should be specified relative to *the curriculum design layer's requirements* (Ch 8). The content layer is minimum viable when it supplies enough content per concept node, at sufficient quality, for the engine to run the modes the curriculum's mode flags allow. Not when it "feels complete."

---

## C. Content last. Deliberately. — the opening posture

The TIKTOC's hook for the chapter is the posture itself. The chapter writer should land it as the opening move:

> Every author wants to start here. Content is what you have. Content is what you know. Content is what your reputation rests on. This is the chapter that says: content is the *last* of the four layers in this book, and on purpose. The measurement layer (Ch 5) decides what the engine can learn. The mode layer (Ch 6) decides what the engine can offer. The engine itself (Ch 7) decides what gets selected. The curriculum design layer (Ch 8) decides what the engine's choices are constrained by. By the time we get to content, the other three layers have specified what the content has to do — what kind of artifact each mode needs at each concept node at each Bloom level. The job of the content layer is to satisfy those specifications, not to define them.

This is the chapter's posture. The reader should feel slightly resisted at the opening — *wait, my content is the least interesting decision?* — and then talked through *why*. The resistance is productive; it is the chapter's defining move.

---

## D. The domain-specificity finding — the chapter's central evidence section

### D.1 The Sadler 2013 reference — verify carefully

The TIKTOC names Sadler 2013 in the PCK context. The most relevant Sadler paper to "domain specificity in PCK" is:

- Sadler, Philip M., Gerhard Sonnert, Harold P. Coyle, Nancy Cook-Smith, and Jaimie L. Miller. 2013. **"The Influence of Teachers' Knowledge on Student Learning in Middle School Physical Science Classrooms."** *American Educational Research Journal* 50 (5): 1020–1049. ([DOI: 10.3102/0002831213477680](https://doi.org/10.3102/0002831213477680)) `[verify exact volume/pagination]`

The key finding from Sadler et al. 2013 (drawn from `domain-specific-instruction-research.md`): teachers who could *identify their students' likely misconceptions* — a specifically domain-bound piece of pedagogical content knowledge — produced substantially larger learning gains than teachers who could not, controlling for content knowledge itself. Subject-matter knowledge alone was not sufficient; the diagnostic move that depended on knowing the *student-side* errors particular to the domain is what carried the effect.

`[verify]` the Sadler 2013 citation. The chapter writer should confirm volume/issue/pagination against AERJ. The companion finding from Hill, Rowan & Ball 2005 (`domain-specific-instruction-research.md` §2.2) is the cleaner empirical PCK-to-outcomes link.

### D.2 The PCK lineage — Shulman 1986 → Hill, Rowan & Ball 2005 → Sadler 2013

The chapter should sketch the PCK lineage briefly:

- **Shulman 1986** introduced Pedagogical Content Knowledge as distinct from subject-matter knowledge — *knowing how to make the content learnable* requires domain-specific knowledge of student misconceptions, illuminating analogies, and revealing problem types.
- **Hill, Rowan & Ball 2005** produced the cleanest empirical link: teachers' Mathematical Knowledge for Teaching (a PCK-aligned construct) predicted student achievement gains beyond what general teaching skill or subject content knowledge predicted.
- **Sadler 2013** extended the finding to physical science teachers: PCK matters more than content knowledge alone, and the diagnostic move (identifying student-side misconceptions) carries the effect.

Cross-reference `domain-specific-instruction-research.md` §2 in full. The chapter writer should not re-research; cite the pantry note and pull the three key citations forward.

### D.3 The Level 1 / Level 2 / Level 3 framing

The TIKTOC names three levels:

- **Level 1: Generic backbone.** All content is generic; no domain-specific examples, problems, or scenarios. The student gets the principles abstractly. Theoretical advantage: maximum transfer (the student can apply the principle to any domain). Empirical reality: motivation collapse; abstract instruction is fragile because the learner has no anchor to make the content stick. (Cross-reference `domain-specific-instruction-research.md` §1.5 table on TAP costs — the fourth row is Level 1.)
- **Level 2: Generic with a domain capstone.** The bulk of instruction is generic, with one domain-specific application at the end. Common in current professional development courses. Improvement over Level 1 — the capstone gives a concrete anchor — but the bulk of the content is still abstract, so the transfer-appropriate processing benefit comes only from the capstone fraction.
- **Level 3: Domain-specific throughout, with a generic backbone.** The principles are taught in the domain. The examples, problems, scenarios, and worked solutions are drawn from the student's field. The generic principles are extracted and made visible across domain examples. Costs more to produce (1.5× to 2× — see §D.4) but captures the bulk of TAP, situated learning, and motivation benefits.

The chapter argues for Level 3 as the right default, with two caveats:

1. The cost premium is real. A program that cannot afford 1.5× cost for Level 3 has to choose: produce Level 1 content (motivationally fragile) or Level 2 content (the capstone-only compromise). The chapter should not pretend the cost is free.
2. The Level 3 prescription requires *knowing the learner's domain*. If the platform serves multiple domains (e.g., a multi-discipline Medhavy deployment), Level 3 means *producing separate domain variants*. This multiplies the production cost by the number of domains. The cost-collapse argument (§E) is what makes multi-domain Level 3 newly feasible.

### D.4 The cost premium — verify the 1.5× to 2× figure

`[verify]` — the 1.5× to 2× production cost figure for Level 3 vs. Level 1 is given in the TIKTOC and in `domain-specific-instruction-research.md`. The figure originates in the curriculum-design-and-MOOC-personalization literature (`domain-specific-instruction-research.md` §6 on curriculum variant production). The chapter writer should pull the specific source — likely vendor data from professional-development providers (`[verify]` exact citation) — and label it appropriately. If the figure is vendor-derived rather than peer-reviewed, label it as such.

### D.5 Situated learning and transfer-appropriate processing as the cognitive engine

The mechanism that makes Level 3 work, drawn from `domain-specific-instruction-research.md` §1:

- **Transfer-Appropriate Processing (Morris, Bransford & Franks 1977).** The cognitive operations at study and test must overlap; encoding the principle in domain context produces durable retrieval in domain context.
- **Situated learning (Lave & Wenger 1991; Brown, Collins & Duguid 1989 — `[verify]`).** Knowledge is partly constituted by the activity, context, and culture in which it is developed; decontextualized knowledge transfers poorly to authentic practice.
- **Barnett & Ceci 2002 transfer taxonomy.** Far transfer is rare; near transfer is the modal positive finding. Level 3 optimizes for near transfer to the learner's intended domain.

The chapter should land these as the *cognitive engine* of the domain-specificity argument: Level 3 works because cognition is context-bound at the level of operation; the principle and the domain context are not separable in the way the abstract-first instructional tradition assumes.

---

## E. The cost-collapse asymmetry

### E.1 The cost-collapse claim

Production cost for some content has collapsed by approximately one to three orders of magnitude in the AI-generation transition (2023–2026). Reference points from `educational-media-economics-research.md` §1 and §4:

- **Text generation.** Marginal cost per 1,000 words for GPT-class models: $0.01–$0.10 (2025 pricing). Pre-AI cost for the same quality of explanatory text: $100–$1,000 (writer time at professional rates). Roughly four orders of magnitude.
- **AI video generation.** Google Veo 2 (December 2024): $0.50/second = $30/minute of generated video. OpenAI Sora and Runway: in similar ranges. Pre-AI cost for comparable narrated explanatory video (script + narrator + animation): $1,000–$5,000/minute at low-budget educational rates. Roughly two orders of magnitude.
- **Image generation.** Per-image cost (DALL-E, Midjourney, Stable Diffusion): $0.001–$0.10. Pre-AI illustration cost: $50–$500. Roughly three orders of magnitude.
- **Voice synthesis.** Per-minute cost (ElevenLabs, OpenAI TTS): $0.01–$0.30. Pre-AI voice talent: $5–$50/minute. Two to three orders of magnitude.

What has *not* collapsed:

- **Expert review.** A domain expert reviewing AI-generated content for accuracy, conceptual fidelity, and appropriate scaffolding still takes ~5–15 minutes per 500-word passage. Cost unchanged.
- **Curriculum design.** The work of specifying outcomes, prerequisites, mode flags, and assessment evidence (Ch 8) is human-judgment intensive and has not been automated. Cost largely unchanged.
- **Empirical validation.** Running RCTs or quasi-experiments on content effectiveness costs what it has always cost. The cost of *producing* content has dropped; the cost of *knowing whether the content works* has not.
- **Domain-expert authorship for high-stakes content.** A practicing oncologist writing a clinical scenario from their case experience cannot be replaced by AI generation. The cost is in the expertise, not the keyboard time.

### E.2 The asymmetry, made specific

The TIKTOC names it: *AI content at $5/unit changes burden of proof asymmetrically; low-risk content burden lowered; high-risk content burden unchanged*.

The chapter should walk through what counts as which:

**Low burden of proof — content where AI generation with light review is acceptable:**

- *First-draft explanatory text* on well-established concepts (the substance is in standard textbooks; the AI is paraphrasing; the human reviewer is checking for errors and adding voice).
- *Quiz Me items* probing factual recall — multiple-choice questions on the substrate of CYP3A4; the AI generates the item, the human reviewer confirms the answer key.
- *Vocabulary definitions* and lexicon entries.
- *Reading comprehension passages* used as Ask AI context, where the AI's role is to surface what the textbook says rather than to add new content.

**High burden of proof — content where AI generation is insufficient and domain-expert authorship is required:**

- *Clinical case scenarios* where the patient's specific presentation, the differential diagnostic move, the treatment plan, and the failure mode are drawn from real clinical judgment. AI-generated clinical cases hallucinate plausibly and dangerously (cross-reference Pal et al. 2025 MedHallu benchmark in `educational-media-economics-research.md`).
- *Worked examples* in mathematics, physics, engineering, where the steps must be valid and the explanation pedagogically appropriate.
- *Glimmer rubrics* that score the student's generative work. A wrong rubric trains wrong behavior.
- *Cross-context transfer scenarios* (the Ch 5 Y3 GLP component) where the test of understanding is whether the principle generalizes; if the scenario is itself AI-generated and slightly wrong, the test is invalid.
- *Misconception-targeted content* — the Sadler 2013 finding makes this central: knowing which misconceptions students bring to physical science is what carries the PCK effect, and the misconceptions are domain- and learner-specific. AI generation of misconception-aware content is at best a draft for expert review.

The cost-collapse asymmetry has a corollary the chapter should land: *AI generation makes the cheap content cheaper; it does not make the expensive content cheap*. The total content production cost for a Level 3 Medhavy deployment falls — possibly substantially — but the human expert authorship cost for high-stakes content remains the binding constraint.

### E.3 Sunstein and burden-of-proof inversion

The Sunstein reference, verified against `educational-media-economics-research.md` §8.1:

- Sunstein, Cass R. 2005. *Laws of Fear: Beyond the Precautionary Principle*. Cambridge University Press. ISBN 978-0-521-61512-4 (paperback). [Cambridge University Press page](https://www.cambridge.org/9780521615129) `[verify ISBN]`.
- Sunstein, Cass R. 2003. "Beyond the Precautionary Principle." *University of Pennsylvania Law Review* 151 (3): 1003–1058. ([Chicago Unbound link in pantry source](https://chicagounbound.uchicago.edu/law_and_economics/87/))

Sunstein's argument:

- The strong precautionary principle is incoherent (it forbids action and inaction simultaneously when both carry risk).
- The defensible frame is cost-benefit analysis under uncertainty, with extra precaution for irreversible or catastrophic outcomes.
- The burden of proof should be *asymmetric to the asymmetry of the failure modes*: if the harm of acting wrongly is small and reversible, the evidence threshold for action can be lower; if the harm is large and irreversible, the threshold must be higher.

The translation to educational content (drawn directly from `educational-media-economics-research.md` §8.3–8.5):

- **Failure mode A: AI content fails to help.** Small loss, reversible. Burden of proof lowered.
- **Failure mode B: AI content actively misleads.** Larger loss, harder to detect. Burden of proof unchanged or higher. Bastani 2025 PNAS is the prototype data point.
- **Failure mode C: AI content develops bad habits.** Largest loss, hardest to reverse. Burden of proof much higher. The cognitive-offloading literature (Carr 2010; Risko & Gilbert 2016) suggests the failure mode is real, though the evidence at content-layer specificity is thin.

The chapter should *not* paraphrase Sunstein as "AI content needs less evidence now." The chapter should paraphrase Sunstein as "the burden of proof shifts with the failure mode, and AI content has multiple failure modes that load up differently." This is the precise reading; the loose paraphrase is exactly what the precautionary-principle literature warns against.

The honest answer to *"does cost collapse change the burden of proof?"* — drawn from `educational-media-economics-research.md` §8.5 — is *yes, asymmetrically; lower for content where failure is small and reversible, unchanged for content where failure is large or persistent, higher for content where failure produces durable bad habits*.

---

## F. The Sesame Street standard — and what AI content actually produces

### F.1 The Sesame Street cost-effectiveness benchmark — verify carefully

The TIKTOC names: *$5/child/year producing measurable learning gains; what AI-generated content produces is genuinely unknown for initial concept acquisition — named as an open bet*.

The Sesame Street benchmark, verified against `educational-media-economics-research.md` §1:

- **The $5/child/year figure.** Drawn from Sesame Workshop financial reporting and the Bridgespan case study. $25M annual production budget producing ~26 episodes per recent season; ~156M children reached annually through global co-productions; arithmetic: $25M / 156M children = $0.16/child/year for production proper, with adaptation/distribution/licensing/formative research bringing total to ~$5/child/year ([Bridgespan case study](https://www.bridgespan.org/insights/audacious-philanthropy-case-studies/sesame-street); [Slate 2012](https://slate.com/business/2012/01/does-sesame-street-lose-money.html); [Hollywood Reporter](https://www.hollywoodreporter.com/news/general-news/sesame-street-gets-funding-how-it-went-broke-1183032/)).
- **The effect-size benchmark.** Mares & Pan 2013 meta-analysis across 15 countries: *d* ≈ 0.29 on cognitive outcomes. A moderate effect by Cohen conventions; a large effect by EdTech-intervention conventions.
- **The long-run natural experiment.** Kearney & Levine 2019 (*AEJ: Applied Economics* 11 (1): 318–350): preschoolers in counties with strong Sesame Street reception were 14% less likely to be behind their expected grade level later in school. Effects comparable in magnitude to Head Start, at three to four orders of magnitude lower per-child cost.
- **The Cooney / Children's Television Workshop origin.** Joan Ganz Cooney's 1968 feasibility study (*The Potential Uses of Television in Preschool Education*) commissioned by Carnegie Corporation laid the methodological foundation: measurement before claims; readiness skills operationalized before show design; formative research integrated into production. This is the methodological commitment that distinguishes Sesame Street from every subsequent educational-media product. `[verify exact title and year of Cooney feasibility study — sometimes cited as "Cooney Memo," sometimes as the published 1966/1967/1968 study]`.

The benchmark for the chapter: *$5/child/year + d=0.29 = ~$1.72 per 0.1 SD gain*. Compare to high-dose tutoring (Nickow, Oreopoulos & Quan 2024 meta-analysis: *d* ≈ 0.37 at $2,000–$3,500/child = ~$540–$945 per 0.1 SD). Sesame Street is ~300–500× more cost-effective per 0.1 SD than tutoring.

### F.2 What AI content actually produces — the open bet

The TIKTOC frames this as bet #8: *Does AI-generated educational content produce durable learning outcomes comparable to professionally produced content?* The chapter should treat this as **genuinely unknown for initial concept acquisition**, with the honest reading from `educational-media-economics-research.md`:

- The Bastani 2025 PNAS finding shows AI tutoring *can* produce harm under the wrong guardrail design — concrete evidence that the relationship between AI-generated content and learning outcomes is non-trivial.
- No peer-reviewed RCT has compared AI-generated educational content to expert-produced content on durable learning outcomes (defined as 7-day or longer retention with transfer probes) at the same production budget.
- The vendor case-study claims of "comparable effectiveness" are typically engagement-based or single-session-performance-based; both are inappropriate proxies (Ch 5, Ch 7).
- The closest validated finding: AI content has not been shown to clear the Sesame Street design quality bar (dual-channel alignment per Mayer's CTML; signaling, segmentation, temporal contiguity; formative research validation). Cost parity has been achieved; quality parity for *initial concept acquisition* has not.

The chapter should land this honestly: *the cost-collapse argument for AI content is strong; the effectiveness argument is weak; the honest position is to deploy AI-generated content where the failure mode is small and reversible, and to retain expert authorship where the failure mode is large or persistent*. This is the burden-of-proof inversion applied operationally.

### F.3 What Sesame Street actually built that AI content has not replicated

From `educational-media-economics-research.md` §1.4 (the production-cost detail and the design machinery):

- **Dual-channel alignment.** Visual and verbal channels coordinated frame-by-frame, derived from Mayer's Cognitive Theory of Multimedia Learning (CTML). AI-generated video has not been shown to produce this alignment reliably.
- **Repetition with variation.** The same concept introduced in multiple modalities, with deliberate variation that produces transfer-appropriate processing.
- **Rhythm and phoneme work.** Music, rhyme, and phonological emphasis tuned to readiness-skill targets — a design discipline that originated in Joan Ganz Cooney's formative research and persists in current Sesame Street production.
- **Formative research integration.** Every episode is tested in formative research with children before broadcast; design choices are revised based on what worked. AI-generated content has not built this discipline into the production pipeline.

The chapter's point: *the Sesame Street machinery is the quality target the AI production transition has to clear. AI content at $5/unit is achieving cost parity. Whether it is achieving design quality is the open bet.*

---

## G. The AI-generation policy — what gets generated, what gets authored

### G.1 The three-tier policy

The chapter should specify a clear policy:

**Tier 1 — AI-generated with light review (1–2 minutes per unit).**

- Lexicon entries and vocabulary definitions.
- First-draft explanatory text on well-established concepts.
- Quiz Me items on factual recall (with answer-key confirmation).
- Reading comprehension passages used as Ask AI context.

**Tier 2 — AI-drafted with substantial expert review (5–15 minutes per unit, with revision).**

- Explanatory text on concepts where misconception traps are present.
- Case study scenarios at moderate stakes (not clinical decision-making).
- Worked examples in domains the expert can verify quickly.
- Glimmer prompts and rubrics for low-stakes generative work.

**Tier 3 — Domain-expert authorship required (no AI draft sufficient).**

- Clinical case scenarios in medical education.
- Misconception-targeted content (Sadler 2013 finding).
- High-stakes Glimmer rubrics (capstone projects, assessment-bearing).
- Cross-context transfer probes (the Ch 5 Y3 component).
- Any content whose failure mode is large, irreversible, or develops durable bad habits.

The chapter should give a specific operational instruction: *if a content unit's failure could not be detected and corrected within one session, it requires Tier 3 authorship*. This is the operational analog of the Sunstein burden-of-proof inversion.

### G.2 The faculty review gate

The TIKTOC names: *the faculty review gate is not optional*. The chapter should specify what this means:

- Every content unit in Tier 2 and Tier 3 passes through expert review before deployment.
- Tier 1 units are sampled for review (e.g., 10% random sample) to catch systematic AI errors.
- The faculty review gate is a *workflow stage*, not a one-time event; revised content is re-reviewed; deployment data triggers re-review when GLP signals indicate drift.

This is the same architectural discipline as the bandit's reward-function audit (Ch 7) — a gate that audits the system's outputs against the discipline the system claims to implement.

### G.3 The "AI generation is fine, sampling protects us" failure mode

The chapter should warn against a specific failure mode: *generating Tier 2/3 content with AI and relying on sampling-based review to catch errors*. This sounds defensible. It is not. The reason:

- Sampling catches the *errors that are randomly distributed*.
- AI generation produces *systematically biased errors* — hallucinations cluster around certain failure modes (e.g., medical hallucinations cluster around drug-drug interactions and rare conditions; Pal et al. 2025 MedHallu benchmark).
- Random sampling misses systematic errors with probability that does not vanish with sample size; the bias is in the generation, not in the noise.

The discipline: every Tier 2/3 unit gets reviewed, not sampled. This is the engineering cost of the cost-collapse argument honestly applied. Cost collapse for *production*; cost retained for *review*.

---

## H. Connection to existing pantry

Cite by filename:

- `domain-specific-instruction-research.md` — primary source for the domain-specificity argument. §1 on TAP; §2 on PCK (Shulman 1986; Hill, Rowan & Ball 2005; Sadler 2013); §6 on curriculum variant production and Level 1/2/3 framing. The chapter inherits this evidence base wholesale; cite by section.
- `educational-media-economics-research.md` — primary source for cost-collapse, Sesame Street benchmark, Sunstein burden-of-proof inversion. §1 on the Sesame Street evidence base (Bogatz & Ball, Mares & Pan 2013, Kearney & Levine 2019); §4 on the cost-effectiveness arithmetic; §8 on the burden-of-proof inversion (Sunstein 2003, 2005). The chapter uses this note heavily for §F and §E.
- `ask-ai-research.md` — Bastani 2025 PNAS finding as the concrete data point on AI-produced learning harm; ITS effect sizes as the upper bound on what well-designed AI-assisted instruction can produce.
- `_lib_teaching-for-deeper-learning_-tools-to-engage-students-in-meaning-making.md` — backward-design and meaning-making framing.
- `PEDAGOGY ARCHITECTURE.txt` §6 — assertion density principle and the content requirements per mode. The chapter's "what each mode needs from content" section draws on this.
- `Lexicon.txt` — the platform's content-layer terminology.

Cross-reference Ch 7 notes for the engagement-trap discussion (Ch 9 is where content can leak engagement information into the reward signal). Cross-reference Ch 8 notes for the curriculum-layer specification that the content layer must satisfy. Cross-reference Ch 10 notes (Batch 4) for the cost-collapse economic argument; Ch 9 uses cost-collapse asymmetry as a constraint, Ch 10 uses it as the economic case for the build.

---

## I. Open questions, gaps, and verify flags

### I.1 Sadler 2013 citation

`[verify]` — confirmed against `domain-specific-instruction-research.md`. Sadler et al. 2013 in *American Educational Research Journal* 50 (5): 1020–1049. Chapter writer should verify exact pagination at AERJ before citing.

### I.2 Sesame Street $5/child/year — verify against Cooney origin

`[verify]` — the $5/child/year figure is well-established for current Sesame Street operations. The chapter writer should verify whether the figure as stated also accurately characterizes the *original* Cooney/Children's Television Workshop 1969 launch costs. The original 1969 per-episode production cost was $28,000 (~$230,000 in 2025 dollars per `educational-media-economics-research.md`); the per-child cost calculation depends on assumptions about audience reach in the launch year. The chapter writer should be careful to say "Sesame Street has historically cost approximately $5/child/year on a fully-amortized basis" rather than "Cooney's 1969 program cost $5/child/year" — the second statement is harder to verify and may be wrong.

Original Cooney source: Cooney, Joan Ganz. 1968. *The Potential Uses of Television in Preschool Education*. Carnegie Corporation report. `[verify exact title and date]` — sometimes cited as 1966 or 1967 working paper; the 1968 publication date is the most commonly given but some sources differ.

### I.3 Sunstein citation

Verified against `educational-media-economics-research.md` §8.1. Both the 2003 *U Penn L Rev* article and the 2005 *Laws of Fear* book are appropriate; the book is the more comprehensive reference. `[verify]` the ISBN for the 2005 Cambridge UP edition.

### I.4 The 1.5×–2× Level 3 cost premium

`[verify]` — the figure is sourced in the curriculum-design literature on MOOC personalization and corporate L&D variant production. The chapter writer should pull the specific citation from `domain-specific-instruction-research.md` §6 and confirm whether it is peer-reviewed or vendor-derived.

### I.5 The Pal et al. 2025 MedHallu benchmark

Pal, Ankit, et al. 2025. "MedHallu: A Comprehensive Benchmark for Detecting Medical Hallucinations in Large Language Models." arXiv:2502.14302. ([arXiv link in pantry source](https://arxiv.org/html/2502.14302v1)). Preprint; not yet peer-reviewed at the time of writing. The chapter should cite as preprint and flag accordingly. The finding is the closest available evidence for the "AI medical content hallucinates systematically" claim that justifies Tier 3 authorship for clinical content.

### I.6 The Bastani 2025 PNAS finding — verify carefully

The TIKTOC notes Bastani 2025 PNAS as the single most important finding to verify across the book. From `medhavy-1.5-feature-roadmap-complete.md` key citations: "Bastani, Hamsa, Osbert Bastani, et al. 2025. 'Generative AI Can Harm Learning.' *PNAS* 122(26): e2422633122." `[verify]` the exact volume/issue/article number and the GPT-Base vs. GPT-Tutor experimental design. The Ch 9 use of Bastani is narrower than the Ch 3 evidence-base use — Ch 9 cites it specifically as the data point that AI content with the wrong guardrail can produce *measurable persistent harm to learning*, which sets the lower bound on the burden of proof for high-stakes content.

### I.7 The "AI generation is fine, sampling protects us" claim

The chapter argues this is a failure mode. The argument depends on the empirical claim that *AI generation errors are systematically clustered rather than randomly distributed*. The MedHallu benchmark (Pal et al. 2025) is the closest evidence for systematic clustering in medical content. The generalization to other domains is an inference, not a direct finding. The chapter should be explicit: *for medical content, the evidence supports systematic clustering; for other domains, we infer it from the same generation mechanism but the empirical case is thinner*. Label appropriately.

### I.8 The Level 3 multi-domain cost multiplier

A Level 3 curriculum serving multiple domains requires producing separate domain variants. The chapter implicitly argues that cost-collapse makes this newly feasible. The arithmetic: Level 1 cost = 1 unit; Level 3 single-domain cost = 1.5–2 units; Level 3 with *k* domain variants = 1.5k–2k units. For k=1, the premium is modest. For k=10 (a multi-discipline Medhavy deployment), the premium is 15×–20× over Level 1.

Cost-collapse changes the calculation: if AI generation drops the per-unit production cost by 10× for Tier 1 content, the Level 3 multi-domain cost can fall below the pre-AI Level 1 cost. *Per unit of finished domain-variant content.* Expert review costs do not scale this way; they scale roughly linearly with the number of variants. The honest claim: *Level 3 multi-domain is newly feasible at the production layer; the binding cost is now expert review for Tier 2/3 content, not production for Tier 1*.

### I.9 The worked-example design

The TIKTOC names: *Two versions of the same pharmacology concept explanation. Version A: AI-generated, generic, unreviewed. Version B: domain-specific, faculty-reviewed, cross-domain comparison included. What each version produces in the measurement layer.*

The chapter writer should make this specific. Recommended concept: *first-pass metabolism and its implication for oral bioavailability of beta-blockers*.

- **Version A.** AI-generated, generic, unreviewed. Reads like a textbook passage with no specific clinical examples; no misconception scaffold; no cross-domain link to (say) the equivalent kinetics in oncology drug dosing.
- **Version B.** Domain-specific, faculty-reviewed. Opens with a specific patient (illustrative, labeled): a 65-year-old with heart failure prescribed metoprolol; the passage explains why the oral dose is 5–10× the IV dose; names the misconception (students often assume oral and IV doses are interchangeable); cross-references the equivalent calculation for a chemotherapy drug to show the principle generalizes.

What each version produces in the measurement layer:

- Version A: Y1 (engagement) may look fine — students read it, click through. Y2 (error trajectory coherence) is uninformative — there are no characteristic error patterns to track because the version does not address the specific misconception. Y3 (cross-context transfer) is absent because the version makes no cross-context link. Y6 (retrieval strength decay) at 7 days: the student remembers the abstract definition but cannot apply it to a clinical case.
- Version B: Y2 is informative because the misconception is named and the student's response to misconception-targeted probes is trackable. Y3 is informative because the cross-context link gives a transfer probe. Y6 at 7 days: the student remembers the principle *and* the application — both because the encoding was in clinical context (TAP) and because the misconception was explicitly addressed.

The chapter should show this trajectory walked through, with explicit reference to which GLP components diverge between Versions A and B. This is the chapter's emotional center: *the AI-generated version looks fine on the engagement signals; the domain-expert version looks better on the learning signals; the platform that measures engagement cannot distinguish them; the platform that measures learning can*.

---

## J. Assessable exercises — TIKTOC names three

1. (Apply) Given a content production budget and a domain, specify the content layer: which elements get AI-generated with light review, which require domain-expert authorship, and why.
2. (Evaluate) An AI-generated explanation contains one factual error and two conceptually misleading simplifications. What does the GLP measurement layer capture — and when? What is the faculty review gate's job?
3. (Analyze) A platform claims their AI-generated content is "as effective as professionally produced content" based on engagement metrics. What evidence would actually support this claim?

Worked-answer sketches for the chapter writer's reference:

- *Exercise 1 sketch.* Provide a budget ($50,000) and a domain (pharmacology Module 1: pharmacokinetics). The student must produce a budget allocation across the three tiers, justified by the content type and the failure-mode analysis. The Tier 1 allocation (vocabulary, factual recall items, first-draft explanatory text) should be cost-efficient; the Tier 2 allocation (case study scenarios, worked examples) should consume the bulk of expert review hours; the Tier 3 allocation (clinical case scenarios, cross-context transfer probes) should consume the bulk of expert authorship hours. A working answer demonstrates the cost-collapse asymmetry applied operationally.
- *Exercise 2 sketch.* The GLP layer can capture the factual error if a probe item targets it (within a few days, depending on FSRS scheduling). The misleading simplifications are harder — they may not be detected until the student fails a downstream transfer task (weeks later) or a Case Study scenario probes them. The faculty review gate's job is to catch errors *before deployment*; the GLP layer is the *backup* for errors the review missed. The student should articulate the dependency: a strong gate reduces the burden on GLP; a weak gate forces GLP to do diagnostic work it is poorly suited for.
- *Exercise 3 sketch.* The evidence required: a RCT or quasi-experiment with (a) randomized assignment of content type, (b) durable learning outcomes measured at 30+ days post-instruction, (c) transfer probes that go beyond the trained material, (d) a control for the curriculum-design and adaptive-engine layers (i.e., the comparison must isolate the content layer). Engagement metrics are not evidence for learning equivalence — they are evidence for engagement equivalence. The student should be able to articulate this distinction precisely.

---

## K. Bridge to Chapter 10

The TIKTOC bridge: *The architecture is complete. Chapter 10 delivers the economic argument for why this moment — this specific convergence of cost collapse, AI capability, and evidence base — is the right moment to build it.*

The bridge is right. Ch 9 establishes the cost-collapse asymmetry as a *content-production* fact; Ch 10 takes the same fact and asks the *whole-architecture* question: when does the four-layer build pay back? The two chapters share the cost-collapse evidence base but ask different questions of it.

**Coordination flag for Batch 4 (Ch 10 author):** `educational-media-economics-research.md` is labeled "Ch 10 heavy use, Ch 9 light use." This means Ch 9 uses §1 (Sesame Street) and §8 (Sunstein) but leaves §2 (Mayer CTML), §3 (personalization and the Bloom 2-sigma critique), §5 (homeschool and minimum viable audience), and §10 (the full cost-effectiveness arithmetic) for Ch 10. Ch 9 should reference but not consume these sections; Ch 10 should not repeat the Sesame Street benchmark introduction that Ch 9 has already done. The two chapters should read as additive uses of the same pantry note.

---

## L. Word-count target and chapter shape

The TIKTOC implies 5,000–7,000 words for a non-load-bearing chapter at Evaluate level. Recommended internal allocation:

- §1 Opening ("Content last. Deliberately.") — ~500 words.
- §2 The domain-specificity finding (PCK; Sadler 2013; Level 1/2/3) — ~1,000 words.
- §3 The cost-collapse asymmetry — ~900 words. The cost-collapse evidence and what it changes; what it does not change.
- §4 The Sunstein burden-of-proof inversion — ~600 words.
- §5 The AI-generation policy (three tiers, faculty review gate) — ~900 words.
- §6 The Sesame Street standard — and what AI content actually produces — ~800 words.
- §7 The minimum viable content layer — ~400 words.
- §8 Worked example (pharmacology Version A vs. B) — ~700 words.
- §9 Exercises, what-would-change-my-mind, still-puzzling, bridge — ~600 words.

Total: ~6,400 words.

---

## M. What would change the chapter's reading

- A published RCT comparing AI-generated content (with light review) to expert-authored content on durable learning outcomes (30+ day retention with transfer probes), at controlled curriculum and engine layers, showing no significant difference at the content layer. *That* would weaken the Tier 3 case and shift the boundary between Tier 2 and Tier 3 upward.
- A reproducible finding that AI generation errors in non-medical domains are *randomly distributed* rather than systematically clustered. *That* would shift the case for full-review-of-Tier-2-3 toward sampling-based review.
- A demonstrated AI production pipeline that meets Sesame Street's dual-channel alignment / signaling / temporal contiguity / formative-research standards at $5/unit. *That* would change the open-bet status of bet #8 from "genuinely unknown" to "likely supported."
- A documented case where Level 1 (generic) instruction in a domain with strong situated-learning expectations outperformed Level 3 (domain-specific) instruction on transfer probes outside the original domain. *That* would weaken the Level 3 case as the default; the framework would have to specify *when* Level 3 is right and when generic instruction's transfer advantage dominates.

---

## N. Still puzzling

Two to four open questions:

1. **The boundary between Tier 2 and Tier 3.** The chapter draws a line, but the line is fuzzy and domain-dependent. What is the test that determines whether content requires expert authorship vs. expert review of an AI draft? The chapter offers heuristics (failure mode size; reversibility; misconception-targeting), but a sharper test is not yet specified.
2. **The misconception-encoding problem.** Sadler 2013 finds that misconception-aware content produces large learning gains. Who encodes the misconceptions? They are partly domain-specific, partly learner-population-specific, partly evolving as curricula change. The platform needs a process for collecting and updating misconception data; the process is not yet specified.
3. **The AI-content-quality drift problem.** AI generation quality is improving rapidly. A Tier 3 boundary that is correct in 2026 may be too conservative in 2028. How does the platform update the AI-generation policy as the underlying model capability changes? The faculty review gate gives ongoing evidence — but who is reading that evidence and updating policy?
4. **The Sesame Street design machinery — can AI learn it?** The dual-channel alignment, signaling, temporal contiguity, and rhythm/phoneme work are design disciplines, not content. Whether AI content production can *learn the discipline* (rather than just generate content) is genuinely unknown. This is the deeper version of bet #8.

---

*End of research notes for Ch 9. Estimated chapter word count from these notes: 5,500–6,500. Coordination flag with Ch 10 (Batch 4): split the educational-media-economics pantry note across the two chapters as specified in §K.*
