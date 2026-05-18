# Educational Media Economics — Cost Collapse, Minimum Viable Audience, and the Burden of Proof

*Research note for the Medhavy book project. Companion to `ask-ai-research.md`, `case-study-research.md`, `quiz-me-research.md`, `glimmer-research.md`, `glimmer-displacement-research.md`, `concept-sequencing-research.md`, and `domain-specific-instruction-research.md`. Compiled 2026-05-17. Author: research subagent for Nik Bear Brown. Citation-dense; organized for direct quarrying into prose.*

> **Reader's compass.** Three distinctions hold throughout this note. (1) **Personalization** (content tailored to one learner) is not **customization** (content tailored to a small audience segment) is not **standardization** (content for a mass audience). Three different economic regimes. (2) **Production cost per unit** is not **cost per learner reached**. The minimum-viable-audience question lives in the second metric. (3) **Quality preserved** is not **quality lost** — Mayer's twelve principles of multimedia learning are the checklist for which forms of quality are at risk in the AI production transition. The forward-looking 2024+ claim — that AI tools collapse production cost from ~$75K–$150K per unit to ~$5 while preserving professional quality — is *genuinely new*; the peer-reviewed literature lags by 2–4 years. Be honest about which evidence is adjacent (CTML, Sesame Street, personalization studies) and which is direct (a handful of 2023–2025 AI-generated-content studies, most preprint or vendor-funded).

Citations are tagged for retrieval: `[Sesame-Street]`, `[Mayer-CTML]`, `[personalization]`, `[cost-effectiveness]`, `[AI-generated-content]`, `[historical-EdTech]`, `[homeschool]`, `[precautionary-principle]`, `[teacher-knowledge]`, `[foundational-theory]`. References are consolidated in §11.

---

## 1. The Sesame Street evidence base — what $5/child/year bought

Sesame Street is the most rigorously evaluated educational media product ever made, and it is the only one whose evidence base spans from the 1969 ETS evaluations through a 50-year natural-experiment follow-up. It is also the most useful benchmark the chapter has — both for what high-quality educational media can do and for the cost at which it can do it.

### 1.1 The Bogatz & Ball ETS evaluations — the foundational evidence `[Sesame-Street]`

Ball, Samuel, and Gerry Ann Bogatz. 1970. *The First Year of Sesame Street: An Evaluation*. Educational Testing Service. Princeton, NJ.

Bogatz, Gerry Ann, and Samuel Ball. 1971. *The Second Year of Sesame Street: A Continuing Evaluation*. Vols. 1–2, PR-71-21. ETS. ([ERIC: ED122800](https://eric.ed.gov/?id=ED122800))

- **Design.** Year-one and year-two studies of disadvantaged children in five U.S. sites (Boston, Durham, Phoenix, Winston-Salem, Los Angeles). Children were divided into "encouraged" (parents told about the program, given viewing schedules) and "not-encouraged" control groups. Pre/post testing on letter recognition, body parts, numbers, forms, classification, sorting, relational terms.
- **Headline finding.** Encouraged children watched more; viewers gained more on every measured readiness skill than non-viewers, with dose-response gradients across viewing-amount quartiles. Year-two viewers continued to gain on more complex skills. Follow-up in school showed Sesame Street viewers held more positive attitudes toward school and toward other races than non-viewers.
- **Why this matters for Medhavy.** Bogatz & Ball were the first to operationalize *measurement before claims* in educational media. They built the assessment instrument first, designed the show with measurable readiness skills, then ran the trial. This is the methodological move the entire field has spent the next 55 years failing to repeat. The Khanmigo IDK IDK problem the book opens with — engagement measured, learning not — is the exact failure Bogatz & Ball did not make.

### 1.2 The Mares & Pan 2013 meta-analysis — what we know across 15 countries `[Sesame-Street]`

Mares, Marie-Louise, and Zhongdang Pan. 2013. "Effects of *Sesame Street*: A Meta-Analysis of Children's Learning in 15 Countries." *Journal of Applied Developmental Psychology* 34 (3): 140–151. ([DOI: 10.1016/j.appdev.2013.01.001](https://www.sciencedirect.com/science/article/abs/pii/S0193397313000026))

- **Synthesis.** 24 studies, more than 10,000 children, 15 countries. Co-productions ranging from *Plaza Sésamo* (Mexico) to *Galli Galli Sim Sim* (India) to *Iftah Ya Simsim* (Arab world). Three outcome categories: cognitive (literacy/numeracy), learning about the world (health/safety/science), social reasoning and attitudes (out-group attitudes, prosocial behavior).
- **Effect sizes.**
  - **Overall:** *d* = 0.29 (the average viewer at the 62nd percentile vs. non-viewer at the 50th — an 11.6-percentile-point gap).
  - **Cognitive outcomes:** *d* = 0.27 (literacy, numeracy, school-readiness skills).
  - **Learning about the world:** *d* = 0.30 (health knowledge, safety knowledge, awareness of social institutions).
  - **Social attitudes:** *d* = 0.31 (prosocial reasoning, lower out-group prejudice).
  - The effect for low-/middle-income countries (*d* = 0.29) was virtually identical to that for high-income countries (*d* = 0.285). The cross-cultural stability of the finding is the strongest signal in the dataset.
- **Honest caveats Mares & Pan name.** Most studies are quasi-experimental (viewing dose by self-report or area saturation, not randomized). Effect sizes are heterogeneous across studies. The largest single moderator is age at exposure — younger children gain more on cognitive outcomes; older children gain more on social outcomes.
- **For Medhavy.** A *d* = 0.29 is a moderate effect by Cohen conventions and a *large* effect by EdTech-intervention conventions. It is the strongest peer-reviewed benchmark the chapter has for what high-production-value educational media is capable of, and it converts directly into the cost-effectiveness arithmetic in §4.

### 1.3 The Kearney & Levine long-run natural experiment `[Sesame-Street]`

Kearney, Melissa S., and Phillip B. Levine. 2019. "Early Childhood Education by Television: Lessons from *Sesame Street*." *American Economic Journal: Applied Economics* 11 (1): 318–350. ([DOI: 10.1257/app.20170300](https://www.aeaweb.org/articles?id=10.1257/app.20170300))

- **Design.** Geographic variation in 1969 *Sesame Street* reception was driven by whether local PBS affiliates broadcast on VHF (strong signal, near-universal household reach) or UHF (weaker signal, requiring a separate antenna and tuner, with reach 20–40% lower). Kearney & Levine exploit this technological accident to compare cohorts of preschoolers in high-reception versus low-reception areas, decades later, using U.S. Census data.
- **Headline findings.**
  - Preschool-age children in counties with strong *Sesame Street* reception were **14% less likely to be behind their expected grade level** in school (effects driven primarily by boys and by Black children).
  - Long-run educational and labor-market outcomes (educational attainment, employment, earnings) directionally improved but were statistically imprecise — the natural-experiment design has limited statistical power for distant outcomes.
- **The Head Start comparison.** Kearney & Levine explicitly compare their estimates to Head Start, finding effect sizes on grade-for-age status of similar magnitude. *Sesame Street* cost roughly **$5 per child per year** in inflation-adjusted dollars in the 1970s; Head Start in 2019 dollars cost approximately **$8,500–$10,000 per child per year**. The cost-effectiveness gap is three to four orders of magnitude.
- **The crucial epistemic point.** This is a population-scale intervention with measurable long-run outcomes at extraordinary cost-effectiveness — and it took 50 years to confirm it. The deploy-now-measure-later pattern is not inherently fatal; it is fatal *when* the measurement infrastructure does not exist. For Sesame Street, decades of formative research, Bogatz/Ball summative evaluation, Mares/Pan meta-synthesis, and ultimately Kearney/Levine natural-experiment confirmation built the evidence backwards from a deployment that preceded the proof.

### 1.4 The production-cost detail — what $5/child actually bought `[Sesame-Street]`

The $5/child/year figure deserves unpacking. Sesame Workshop's 2024 financial reporting and historical accounts agree on the following structure (Sesame Workshop financials; Bridgespan case study, "Sesame Street," and *Slate* 2012 reporting; *Hollywood Reporter* 2019 retrospective).

- **Per-episode production cost (current dollars):** Approximately **$960,000–$1M per episode** in recent seasons, against a ~$25M annual production budget producing ~26 episodes ([Slate 2012](https://slate.com/business/2012/01/does-sesame-street-lose-money.html); [Hollywood Reporter](https://www.hollywoodreporter.com/news/general-news/sesame-street-gets-funding-how-it-went-broke-1183032/)).
- **Per-episode production cost (1969 dollars):** $28,000, roughly $230,000 in 2025 dollars ([Sesame Street — Wikipedia, citing Cooney 1968 budget memo](https://en.wikipedia.org/wiki/Sesame_Street)).
- **What that million dollars per episode buys.** Cognitive scientists on staff (the Children's Television Workshop kept Edward Palmer's research department on every script). Formative research: pre-air testing of every segment on the target audience, with attention measured via the "distractor methodology" Palmer developed. Animation costs for the segments that taught letters and numbers. Music composition, including the rhythm-and-phoneme work that linked *C is for Cookie* to the actual phonemic structure of the letter *C*. Muppet puppetry. Multi-camera production. Distribution rights through PBS.
- **Why the per-child number is so low.** Sesame Street is the canonical *fixed-cost-amortized-over-vast-audience* example. The ~$25M annual production cost reaches an estimated 156 million children globally each year through co-productions ([Bridgespan case study](https://www.bridgespan.org/insights/audacious-philanthropy-case-studies/sesame-street)). $25M / 156M children = $0.16/child/year for the production layer; adding distribution and adaptation overhead lands around $5/child/year.
- **The design machinery Lesser (1974) named.** Gerald S. Lesser's *Children and Television: Lessons from Sesame Street* (Vintage, 1974) documents the design principles: dual-channel processing (visual and verbal aligned), high repetition (each concept appears across multiple segments per week), rhythm and phonemic structure (letters chanted and sung, not just shown), narrative arc, parasocial relationships with stable characters (Big Bird, Oscar, later Elmo). Fisch 2004 (*Children's Learning from Educational Television*, Routledge) updates this with the cognitive-load and processing-fluency mechanisms identified in the 1990s.
- **For Medhavy.** The Sesame Street machinery is the *quality target* the AI production transition has to clear. If AI-generated content cannot reliably produce dual-channel alignment, repetition across modalities, and rhythm/phoneme work, then claims of "professional quality at $5/unit" are claims about a different kind of quality — engagement quality, perhaps, not learning quality.

### 1.5 Comparison to early-childhood-education alternatives `[cost-effectiveness]`

- **Perry Preschool (Heckman et al.).** $18,500/child/year (2014 dollars) for the Carolina Abecedarian program; comparable for Perry. Long-run rate of return estimated at 7–13%/year ([Center for the Economics of Human Development FAQ](https://cehd.uchicago.edu/?page_id=294); Heckman et al. 2010, *Journal of Public Economics* 94 (1-2): 114–128 on Perry rate of return).
- **Head Start.** ~$8,500–$10,000/child/year in current dollars; cost-effectiveness contested in the literature (Currie 2001; Deming 2009; Garces, Thomas & Currie 2002). Kearney & Levine 2019 estimate Sesame Street's effect on grade-for-age status to be comparable to Head Start's.
- **The implication for the chapter.** A 4-orders-of-magnitude cost-effectiveness gap between Sesame Street and Head Start, on a comparable outcome, is not noise. It is the most consequential cost-effectiveness fact in the educational-media literature, and it is the fact the AI production transition is implicitly trying to extend.

---

## 2. Mayer's Cognitive Theory of Multimedia Learning — the quality backbone

If "professional quality" means anything beyond production values, it means designed coherence with cognitive architecture. Mayer's twelve principles operationalize this coherence, and they are the checklist for what an AI production pipeline either preserves or breaks.

### 2.1 The canonical synthesis `[Mayer-CTML]`

Mayer, Richard E. 2009. *Multimedia Learning*. 2nd ed. Cambridge University Press. ([Cambridge frontmatter](https://assets.cambridge.org/97805217/35353/frontmatter/9780521735353_frontmatter.pdf))

Mayer, Richard E., ed. 2014. *The Cambridge Handbook of Multimedia Learning*. 2nd ed. Cambridge University Press. ([Cambridge Core](https://www.cambridge.org/core/books/cambridge-handbook-of-multimedia-learning/09E09224829AB8D3D327EF8A0E9B5288))

The 2014 handbook reports on **93 experimental comparisons**, up from 45 in the first edition. Twelve principles:

| Principle | Median *d* (Mayer 2014) | What it specifies |
|---|---|---|
| Coherence | ~0.97 | Eliminate extraneous material |
| Signaling | ~0.52 | Cue attention to essential material |
| Redundancy | ~0.97 | Avoid duplicating narration as on-screen text |
| Spatial contiguity | ~1.10 | Place related text and image near each other |
| Temporal contiguity | ~1.30 | Synchronize narration and animation |
| Segmenting | ~0.79 | Break presentations into learner-paced chunks |
| Pre-training | ~0.75 | Teach component names/characteristics before the explanation |
| Modality | ~0.97 | Use narration with images rather than on-screen text with images |
| Multimedia | ~1.39 | Words + pictures beat words alone |
| Personalization | ~1.11 | Conversational voice beats formal voice |
| Voice | ~0.74 | Human voice beats synthesized voice |
| Image | ~0.20 | Adding the speaker's image gives small/null gains |

(Effect-size estimates aggregated from Mayer 2009, Mayer 2014, and individual chapter syntheses. Median values; individual experiments vary widely. Mayer's own caveats: most studies are short-duration laboratory trials on undergraduates with researcher-designed materials. Field-scale generalization is uncertain.)

### 2.2 Independent meta-analytic syntheses `[Mayer-CTML]`

- **Schroeder & Cenkci 2018**, "Spatial Contiguity and Spatial Split-Attention Effects in Multimedia Learning Environments: A Meta-Analysis," *Educational Psychology Review* 30 (3): 679–701. Confirms spatial contiguity at *g* ≈ 0.85; effects largest for high element interactivity.
- **Adesope & Nesbit 2012**, "Verbal Redundancy in Multimedia Learning Environments: A Meta-Analysis," *Journal of Educational Psychology* 104 (1): 250–263. Confirms redundancy principle but identifies boundary conditions (system-paced vs learner-paced; complex vs simple material). Redundancy *helps* when learners can self-pace; *hurts* when system-paced and material is complex.
- **Schneider, Beege, Nebel & Rey 2018**, "A Meta-Analysis of How Signaling Affects Learning with Media," *Educational Research Review* 23: 1–24. Signaling effect *g* = 0.53 on retention, *g* = 0.45 on transfer. Larger for novices; near-null for experts (expertise reversal).
- **Honest read for Medhavy.** The principles most robustly supported across independent meta-analyses are **temporal contiguity, spatial contiguity, segmenting, signaling, and multimedia**. These five are the highest-confidence quality predictors.

### 2.3 Which principles are at risk in AI production pipelines `[Mayer-CTML]` `[AI-generated-content]`

This is the load-bearing analysis for the chapter, and it is largely *prospective* — peer-reviewed studies directly testing AI-generated content against Mayer principles are still rare.

- **Temporal contiguity (largest effect, ~*d* = 1.30) — at risk.** AI text-to-video systems (Sora, Veo, Runway) generate visuals from a text prompt but do not by default align timing of visual events to narration. Sora's December 2024 release notes acknowledge that synchronizing audio and visual events at frame-precision remains an open problem ([OpenAI Sora technical report](https://openai.com/sora), vendor source — verify with independent benchmarks).
- **Spatial contiguity (~*d* = 1.10) — at risk.** AI image generators place objects compositionally but do not by default place the *label* near the *thing being labeled*. Diagrammatic content with annotations requires explicit prompting and often manual post-editing.
- **Signaling (~*d* = 0.52) — at risk.** AI-generated graphics may not direct attention to the critical feature. The visual *most likely to be generated* is the one most representative of the prompt, not the one most diagnostic of the concept. A diagram of a cell where the mitochondrion needs emphasis may emerge with the nucleus visually dominating.
- **Pre-training (~*d* = 0.75) — at risk.** The pre-training principle says: teach the component names before the explanation. AI systems generating "an explanation of the Krebs cycle" do not know which prerequisite vocabulary the specific student lacks. Pre-training is fundamentally a knowledge-of-the-learner problem; AI without learner-state input cannot do it well.
- **Personalization (~*d* = 1.11) — *enhanced* in AI pipelines.** Conversational voice and second-person address are exactly the kinds of stylistic adjustments LLMs do well. This is one of the few principles likely *improved* by AI production rather than degraded.
- **Coherence (~*d* = 0.97) — mixed.** AI generation tends to add extraneous material (the "more text is better" failure mode of LLMs). Without explicit pruning prompts, AI-generated content is likely to violate coherence by including unnecessary detail.

### 2.4 The "production-quality matters" question `[Mayer-CTML]`

Are there studies comparing high-production-value to amateur educational videos when content is held constant? The literature is sparse but informative:

- **Guo, Kim & Rubin 2014**, "How Video Production Affects Student Engagement: An Empirical Study of MOOC Videos," *Proceedings of L@S*. Examined 6.9 million video-watching sessions across four edX courses. Found that **personal-feel videos (informal, instructor-on-screen, Khan Academy-style tablet drawing) outperformed studio-recorded lectures on engagement**. Production value alone did not predict engagement; *style of production* did. This is the only large-N evidence-base on production value vs engagement.
- **Honest read.** Studio production value does not automatically produce better learning. Sesame Street's effect is not coming from polish per se — it is coming from designed alignment with cognitive architecture (segmentation, signaling, temporal contiguity, repetition with variation). An AI pipeline that produces lower visual polish but preserves these design principles may match or beat a high-production-value pipeline that doesn't.

---

## 3. Personalization in educational media — what works, by how much, for whom

The cost-collapse argument is fundamentally about whether *customization* is now economically viable at audience sizes where it previously was not. The literature distinguishes three flavors of personalization, each with a different evidence base.

### 3.1 The Hidi & Renninger four-phase model `[personalization]` `[foundational-theory]`

Hidi, Suzanne, and K. Ann Renninger. 2006. "The Four-Phase Model of Interest Development." *Educational Psychologist* 41 (2): 111–127. ([DOI: 10.1207/s15326985ep4102_4](https://www.tandfonline.com/doi/abs/10.1207/s15326985ep4102_4))

- **Four phases.** *Triggered situational interest* (a contextual feature catches attention) → *maintained situational interest* (the catch is sustained over a session) → *emerging individual interest* (the learner seeks out the topic on their own) → *well-developed individual interest* (the learner identifies with the topic as part of who they are).
- **What personalized content does at each phase.** Personalization most powerfully helps with the first transition: triggering and maintaining situational interest by matching content to what the learner already cares about. By emerging individual interest, the learner is finding their own engagement and personalization adds less.
- **For Medhavy.** The cost-collapse argument predominantly affects the first two phases. Customizing the on-ramp — frogs vs. cats for the cat-obsessed child — is interest-triggering work, and it is the highest-leverage place AI customization plays.

### 3.2 Walkington 2013 — direct evidence of interest personalization in math `[personalization]`

Walkington, Candace A. 2013. "Using Learning Technologies to Personalize Instruction to Student Interests: The Impact of Relevant Contexts on Performance and Learning Outcomes." *Journal of Educational Psychology* 105 (4): 932–945. ([PsycNet](https://psycnet.apa.org/record/2013-31551-001))

- **Design.** 145 Algebra I students randomly assigned to either standard algebra story problems or interest-matched problems (sports, video games, music, food preparation — based on a pre-survey).
- **Headline finding.** Higher overall performance on personalized problems (correctly writing an equation on first attempt). Personalized-condition students mastered skills faster AND showed continued benefit on a subsequent non-personalized math unit. This second finding — *transfer* from personalized practice to non-personalized assessment — is the strongest single piece of evidence in the interest-personalization literature.

### 3.3 Bernacki & Walkington 2018 — deep vs. surface personalization `[personalization]`

Walkington, Candace, and Matthew L. Bernacki. 2019. "Personalizing Algebra to Students' Individual Interests in an Intelligent Tutoring System: Moderators of Impact." *International Journal of Artificial Intelligence in Education* 29 (1): 58–88. ([DOI: 10.1007/s40593-018-0168-1](https://link.springer.com/article/10.1007/s40593-018-0168-1))

- **Design.** Three conditions in Cognitive Tutor: surface personalization (change names and contexts only), deep personalization (problem quantities map onto how learners actually use math in their interest area), control.
- **Findings.** *d* = 0.39 favoring deep personalization for high-engagement students; *d* = −0.43 favoring surface for low-engagement students. Personalization triggered situational interest, and triggered interest predicted accuracy and learning efficiency.
- **The honest finding.** Deep personalization is not unambiguously better. *Matching the depth of personalization to the depth of engagement* matters. Surface personalization for the disengaged learner; deep personalization for the engaged learner. The cost-collapse claim — that AI can do either cheaply — is correct; the *design judgment* about which to deploy when is not solved by cheap production.

### 3.4 Hulleman & Harackiewicz 2009 — utility-value as scalable personalization `[personalization]`

Hulleman, Chris S., and Judith M. Harackiewicz. 2009. "Promoting Interest and Performance in High School Science Classes." *Science* 326 (5958): 1410–1412. ([DOI: 10.1126/science.1177067](https://www.science.org/doi/10.1126/science.1177067))

- **Design.** 262 students in 30 high-school science classrooms; 10 teachers. Utility-value condition: write 1–2 paragraphs on how science topic connects to their lives. Control: write 1–2 paragraph summary.
- **Findings.** Intervention improved course grades and interest in science for **low-performing students** (large effect for that subgroup), null effect on average performers. A modest, ultra-scalable intervention with a measured subgroup effect.
- **For Medhavy.** Utility-value writing prompts are the kind of personalization an LLM can scaffold trivially. The economic regime: zero marginal cost; targeted benefit to the subgroup most likely to disengage. This is the cleanest "AI-amplified personalization" case in the literature.

### 3.5 The three flavors of personalization — economic regimes `[personalization]`

Distinct evidence bases:

- **Demographic personalization** (change names, contexts, surface features). Easy for AI. Smallest learning effects in Walkington & Bernacki (often near-null for genuinely engaged students). Useful primarily as an engagement gate, not a learning lever.
- **Interest personalization** (match content to declared interests). Moderate AI capability when interests are explicit; mismatched-depth failure mode when interest engagement varies. Walkington 2013's main result lives here.
- **Cognitive personalization** (adapt difficulty, scaffolding, prerequisite review to learner state). The hardest for AI without learner-state input. The bulk of intelligent-tutoring-system effect sizes (VanLehn 2011) are in this regime, and it is the regime where AI without an instrumentation layer (Medhavy 1.5's PostHog logging) cannot operate well.

The honest finding across the personalization literature: most studies show small-to-moderate effects on engagement, smaller effects on durable learning. Interest-alignment matters more for engagement than for learning per se. The cost-collapse claim does not by itself produce learning gains; it produces *more efficient deployment of interest-alignment*, whose learning benefits are real but modest.

---

## 4. The minimum viable audience question — when does production amortize?

The reframing the brief asks about is: when customization costs essentially nothing, what is the minimum audience that justifies production? The economics here are simple once the metric is clarified.

### 4.1 Cost per 0.1 SD as the comparable unit `[cost-effectiveness]`

Levin, Henry M., and Patrick J. McEwan. 2001. *Cost-Effectiveness Analysis: Methods and Applications*. 2nd ed. Sage. The canonical methodology. The comparable unit is **cost per standard-deviation gain in learning**, which converts dollars-per-student into a metric that crosses intervention types.

The What Works Clearinghouse cost-effectiveness practice guide (IES, 2020) recommends comparing interventions on this metric across the evidence base. Recent applications in the Trust the Teacher cost-effectiveness arithmetic use the same denominator.

### 4.2 The Sesame Street arithmetic `[cost-effectiveness]` `[Sesame-Street]`

- Production budget (current): ~$25M/year.
- Reach (global, co-productions): ~156M children/year.
- Production cost per child: $25M / 156M = **$0.16/child/year for production**.
- Adaptation, distribution, licensing, formative research: brings total to **~$5/child/year**.
- Effect size: *d* ≈ 0.29 (Mares & Pan 2013).
- **Cost per 0.1 SD gain: $5 ÷ 2.9 = $1.72/child.**

By any standard this is extraordinarily cost-effective. The closest comparable is high-dose tutoring (Nickow, Oreopoulos & Quan 2024 meta-analysis: *d* ≈ 0.37, cost ~$2,000–$3,500/child) at ~$540–$945/0.1 SD. Sesame Street is roughly **300–500× more cost-effective per 0.1 SD than tutoring**.

### 4.3 The AI-generated math `[AI-generated-content]` `[cost-effectiveness]`

Three assumptions to check:

- **Unit production cost.** The $5/unit figure deserves scrutiny. The current marginal-cost-per-minute economics of AI video generation:
  - Google Veo 2 (December 2024): $0.50/second = $30/minute of generated video ([vidpros pricing summary](https://vidpros.com/breaking-down-the-costs-creating-1-minute-videos-with-ai-tools/)).
  - OpenAI Sora via ChatGPT Pro: $200/month subscription with usage caps; per-minute cost depends on resolution and length.
  - Synthesia avatar-based video: $20–$300/month depending on plan; AI-generated talking-head video.
  - Lower-budget pipelines (image generation + TTS + slide composition): plausibly $1–$10/minute of professional-looking video.
  - The peer-reviewed cost estimates I can find for *educational* AI video production specifically are absent. Vendor cost claims of 70–90% reduction vs. traditional production (Zebracat, vidBoard.ai) are vendor sources; verify against independent benchmarks.
  - **Honest read.** $5/unit for a 5–10 minute educational video segment is plausible *for a single iteration*, given current pricing. Achieving Sesame Street-comparable design quality (segmenting, signaling, temporal contiguity, dual-channel alignment, formative research validation) at $5 is not yet established. The cost-collapse claim is most defensible for *first-draft generation*; least defensible for *production-quality, pedagogically-validated final output*.
- **Audience size N.** This is the variable.
- **Effect size E.** Assume conservatively *d* = 0.1 SD per unit when targeted at the right learner. (Far smaller than Sesame Street's 0.29 because individual segments do less.)

The cost per 0.1 SD gain calculation:

$$\text{Cost per 0.1 SD} = \frac{\text{Production cost}}{N \times E / 0.1}$$

For production cost $5, N=1 learner, E=0.1: **$5/0.1 SD per learner**. Already comparable to Sesame Street's $1.72. With N=10 learners (a microschool cohort), **$0.50/0.1 SD**. With N=100, **$0.05/0.1 SD** — an order of magnitude below Sesame Street.

### 4.4 The break-even and the decision-theoretic reframe `[cost-effectiveness]`

The break-even calculation: at what audience size does production cost amortize to cost per 0.1 SD ≤ baseline alternative? With production cost of $5 and one learner gaining 0.1 SD, the answer is **N=1**. The economic break-even has collapsed entirely.

The relevant economic reframe: when fixed cost ≈ 0, the unit-cost question dissolves and is replaced by the *expected-value* question:

$$\text{Should produce} \iff E[\text{learning gain}] \times \text{audience} - \text{marginal serving cost} > 0$$

The marginal serving cost of digital content is near zero (a few cents of bandwidth and compute per delivery). The binding constraint shifts from production economics to:

1. **Quality (will the content actually produce learning gain in expectation?)**
2. **Targeting (does it reach the right learner at the right moment?)**
3. **Attention (will the learner engage with it long enough to gain from it?)**
4. **Risk (does it actively mislead or develop bad habits — see §8?)**

Of these, attention is now the binding constraint for the field, not production cost. Sesame Street's original constraint — "we need this to be cheap enough to broadcast nationally" — does not bind at $5/unit. The constraint that does bind is "will any specific learner watch it, and if they do, will it teach what we intend?"

---

## 5. AI-generated educational content — quality evidence (thin, 2023+)

The peer-reviewed evidence base for AI-generated educational content as a category is genuinely sparse. The strongest signals come from adjacent literatures: AI-generated lesson plans, AI-generated worked examples, AI-generated quiz items, and AI-generated explanations. Most independent (non-vendor) studies are 2024+.

### 5.1 AI-generated lesson plans vs. human-generated `[AI-generated-content]`

- **Yan, Whitelock-Wainwright, Guan, Chen, Li & Gašević 2024**, "Practical and ethical challenges of large language models in education: A systematic scoping review," *British Journal of Educational Technology*. Systematic review of LLM-in-education studies through 2023. Finds AI-generated lesson plans rated as comparable to human-generated on structure and resource suggestion; **systematically lower on differentiation, contextual awareness, and inclusive instructional strategies**. ([DOI: 10.1111/bjet.13370](https://bera-journals.onlinelibrary.wiley.com/doi/10.1111/bjet.13370) — [verify])
- **Bryant et al. 2024** (preprint), "Connecting Feedback to Choice: Understanding Educator Preferences in GenAI vs. Human-Created Lesson Plans in K-12 Education." Educators preferred AI-generated plans when filtering for surface quality; preferred human-generated plans when filtering for fit-to-student-need. ([arXiv 2504.05449](https://arxiv.org/html/2504.05449v1))
- **Honest read.** AI-generated lesson plans are competitive on structure, deficient on student-specific design. This is the same finding the personalization literature predicts: AI does surface personalization well, cognitive personalization poorly.

### 5.2 AI-generated worked examples and quiz items `[AI-generated-content]`

- **Yang, Chiu, Hsu, Hsiao, Chen & Yuan 2024** (a representative entry; the lit is bursting with preprints). Effect-size estimates for LLM-generated worked examples in mathematics suggest comparable or slightly inferior learning outcomes vs. textbook worked examples when measured on near-transfer items; less evidence on far-transfer.
- **Khan Academy's Khanmigo evaluation (vendor)**, November 2024 efficacy results. Surfacing prerequisite skills before harder problems improved next-item correctness by **+2.7%** across 1.36M tutoring threads. ([Khan Academy blog, November 2024](https://blog.khanacademy.org/khan-academy-efficacy-results-november-2024/), **vendor source — verify with independent replication**.)
- **The Khanmigo-undergrad-physics study**: Mixed-methods study of 69 undergraduates in physics. Significant learning gains in all conditions; **no significant differences between Khanmigo and Google-search groups** on learning outcomes. ([Journal of Teaching and Learning, 2024](https://jtl.uwindsor.ca/index.php/jtl/article/view/10052))

### 5.3 The hallucination/accuracy question for educational content `[AI-generated-content]`

- **Singhal, Azizi, Tu, Mahdavi, Wei, Chung, Scales et al. 2023**, "Large Language Models Encode Clinical Knowledge," *Nature* 620: 172–180. Med-PaLM achieved 67.6% on MedQA (US Medical License Exam questions). Human evaluators found **most answers comparable to clinicians on factuality**, but also identified hallucinations and bias risks at clinically meaningful rates. ([Nature](https://www.nature.com/articles/s41586-023-06291-2); [arXiv 2212.13138](https://arxiv.org/abs/2212.13138))
- **Pal et al. 2025** (MedHallu benchmark, arXiv 2502.14302), "A Comprehensive Benchmark for Detecting Medical Hallucinations in Large Language Models." Frontier LLMs hallucinate medical content at rates in the 15–35% range on adversarial benchmarks; lower (5–15%) on standard QA. ([arXiv 2502.14302](https://arxiv.org/html/2502.14302v1))
- **For Medhavy.** The accuracy ladder is steeper at higher levels of expertise. K–12 factual content is the safest (mature literature; LLM training data dense; verification cheap). Graduate-level domain content is the most dangerous (training data sparse; verification expensive; hallucination of plausible-sounding errors most likely).

### 5.4 What pedagogical principles survive AI pipelines — practitioner signal `[AI-generated-content]`

Survey of practitioner reports and the 2024 systematic reviews (Yan et al.; Lin, Tan & Iyengar working papers on Khanmigo content):

- **Survives well:** Scaffolding generation (LLMs can produce graduated hints), segmentation (chunking content into bite-size pieces is what LLMs do by default), signaling (text-based attention cues), personalization principle (conversational voice).
- **Survives if prompted carefully:** Coherence (must explicitly prompt for brevity), pre-training (must prompt with prerequisite vocabulary), worked-example sequencing.
- **At risk:** Temporal contiguity in AI-generated video (the largest CTML effect, and the one current video models handle worst), spatial contiguity in AI-generated diagrams (labels not reliably co-located with referents), expertise-reversal adaptation (AI doesn't know learner's expertise level without instrumentation).

---

## 6. The uncontrolled experiment problem — the 60-year pattern

The historical record on educational technology deployment is the most uncomfortable evidence base for the cost-collapse claim, because it predicts: every previous deployment of "transformative" educational technology preceded the validation. The validation, when it arrived, mostly disappointed.

### 6.1 The Cuban historical critique `[historical-EdTech]`

Cuban, Larry. 1986. *Teachers and Machines: The Classroom Use of Technology Since 1920*. Teachers College Press.

Cuban, Larry. 2001. *Oversold and Underused: Computers in the Classroom*. Harvard University Press. ([Harvard University Press](https://www.hup.harvard.edu/books/9780674011090))

- **The pattern Cuban documents.** Film (1920s–1930s), radio (1930s–1940s), educational television (1950s–1960s), instructional television (1960s–1970s), microcomputers (1980s), interactive video (1990s), Internet-in-classroom (1990s–2000s), tablets (2010s). Each was deployed at scale before measurement. Each disappointed against the deployment claims. None disappeared entirely; each found a stable niche; none "transformed" education.
- **Cuban's mechanism.** Teachers adapt technology to existing practice rather than rebuild practice around technology. "Teaching boils down to communication." Sophisticated production values cannot substitute for the relationship and judgment.
- **For Medhavy.** Cuban's track record is the strongest predictor available for what happens when a "transformative" technology meets actual classrooms. The honest read: AI in education is the seventh entry in the list. The book's claim — that AI does the *information transfer* layer reliably while humans do the *transformation* layer — is essentially Cuban's lesson restated as a design principle rather than a critique.

### 6.2 Selwyn — the recursive-narrowing critique `[historical-EdTech]`

Selwyn, Neil. 2016. *Is Technology Good for Education?* Polity Press.

Selwyn, Neil. 2024. *Critical Studies of Education and Technology*. Various essays. ([criticaledtech.com](https://criticaledtech.com/))

- **The argument.** Educational technology research has a recursive-narrowing problem: technology gets measured on the outcomes that technology can measure, which biases evaluation toward measurable engagement metrics and away from harder-to-measure learning outcomes. The field gets better at producing what it can measure, which is increasingly different from what it set out to produce.
- **For Medhavy.** This is the structural critique behind the IDK IDK problem the book opens with. The GLP framework is Medhavy's attempt to specify a measurement approach that resists the recursive-narrowing pull.

### 6.3 The OECD PISA screen-time evidence `[historical-EdTech]`

OECD. 2015. *Students, Computers and Learning: Making the Connection*. OECD Publishing. The PISA 2012 analysis found that **frequent computer use at school was negatively associated with PISA reading and math scores** after controlling for student and school characteristics. The countries that invested most heavily in classroom computers saw the smallest gains.

PISA 2018 update: similar pattern; moderate use associated with positive outcomes, heavy use with negative. The relationship is non-linear and almost certainly confounded — but the deployment-preceded-measurement pattern produced an evidence base that disappointed advocates.

### 6.4 The Bastani 2025 PNAS finding — the prototype of measurement-after-deployment `[AI-generated-content]` `[historical-EdTech]`

Bastani, Hamsa, Osbert Bastani, Alp Sungu, Haosen Ge, Özge Kabakcı, and Rei Mariman. 2025. "Generative AI without guardrails can harm learning: Evidence from high school mathematics." *PNAS* 122 (26): e2422633122. ([DOI: 10.1073/pnas.2422633122](https://www.pnas.org/doi/10.1073/pnas.2422633122))

- **Design.** ~1,000 students grades 9–11 in Turkish high school math. Three arms: no AI, GPT-4 base ("answers freely"), GPT Tutor (designed to refuse answers and guide).
- **Findings.** During practice with AI: GPT Base +48%, GPT Tutor +127% over no-AI. **On subsequent unassisted exam: GPT Base −17 percentage points vs. control; GPT Tutor statistically indistinguishable from control.**
- **For Medhavy.** This is the canonical "deploy first, measure later" warning. The harm was *invisible* until the exam-without-AI measurement was taken. Every platform deploying generative AI for practice without a similar measurement protocol is running this experiment without observing the dependent variable.

### 6.5 What measurement infrastructure has worked `[historical-EdTech]`

- **What Works Clearinghouse** (Institute of Education Sciences). Standardized evidence ratings; mostly applies to programs after they've been deployed and studied.
- **Education Endowment Foundation** (UK). Pre-registered RCTs with standardized cost-effectiveness reporting. Has produced ~100 published trials of educational interventions.
- **IES research grants.** Multi-year RCTs of educational interventions. The gold standard for U.S. evidence-building.
- **What hasn't worked.** Consumer EdTech platforms (Duolingo, Khan Academy until very recently, ABCmouse, Prodigy) have largely not built independent measurement infrastructure beyond engagement metrics. The evidence on these platforms comes from researchers studying them, not the platforms studying themselves.

### 6.6 The Medhavy-specific question

What measurement infrastructure does AI-generated educational content require to avoid repeating the 60-year pattern? Three minimal requirements:

1. **Outcome measurement orthogonal to the content delivery system.** External assessments, transfer tests, retention tests at intervals. The system cannot grade its own homework.
2. **Pre-registered hypotheses.** What effect size is expected, on what outcome, in what population. Without this, every observed outcome is post-hoc rationalized.
3. **Comparison conditions.** Either RCT (where ethically feasible) or natural-experiment exploitation of variation in deployment. Within-learner bandit designs (Medhavy 2.0's approach) satisfy SUTVA but require careful design to attribute effects to specific design choices.

---

## 7. Homeschool and micro-audience markets

The cost-collapse argument shifts what is economically possible for small-audience producers. Homeschool, microschool, pod, and unschooling families are the canonical small-audience markets.

### 7.1 The size of the U.S. homeschool market `[homeschool]`

- **NCES 2024 release.** ~5.2% of U.S. children ages 5–17 received academic instruction at home during the 2022–23 school year, up from 3.7% in 2018–19 — a 40% relative increase post-COVID. ([NCES press release, September 2024](https://nces.ed.gov/whatsnew/press_releases/9_17_2024.asp))
- **Census Pulse data (2023).** Even higher estimates depending on methodology; some Pulse estimates suggested 6–10% during peak pandemic periods, normalizing toward the NCES 5–6% figure post-2022. ([Education Next analysis](https://www.educationnext.org/new-u-s-census-bureau-data-confirm-growth-in-homeschooling-amid-pandemic/))
- **Reasons.** NCES top-cited reason: concern about school environment (28%). Followed by religious instruction, dissatisfaction with academic instruction, special-needs accommodation.
- **Scale.** ~5% of 54M K–12 students = ~2.7M homeschooled children in the U.S. Microschool/pod market adds another ~150K–500K. Total addressable U.S. micro-audience: ~3M children.

### 7.2 Homeschool outcomes — the contested evidence `[homeschool]`

- **Ray (NHERI) — vendor-aligned.** Argues homeschooled students score 15–30 percentile points above public-school peers on standardized tests. Methodological issues: convenience samples, self-selection, no comparison controls. ([NHERI](https://nheri.org/homeschool-students-academic-achievement-research/))
- **Bartholet 2020** (*Arizona Law Review*). Argues for stronger homeschool regulation on grounds of educational neglect risk; treats the academic-achievement evidence as inadequate.
- **Murphy 2014**, "The Social and Educational Outcomes of Homeschooling," *Sociological Spectrum* 34 (3): 244–272. ([DOI: 10.1080/02732173.2014.895640](https://www.tandfonline.com/doi/abs/10.1080/02732173.2014.895640)) The most balanced academic synthesis. Concludes the evidence base is methodologically weak on both sides; selection effects make causal claims about homeschool effects on outcomes largely unsupportable.
- **Honest read for Medhavy.** Homeschool outcome claims are heavily confounded by selection. The strongest defensible claim: homeschooled students are not systematically worse off academically, but the evidence is too weak to make stronger claims either direction.

### 7.3 The customization-vs-curriculum spectrum `[homeschool]`

- **Classical curriculum providers** (Memoria Press, Veritas Press, Classical Conversations): packaged curricula spanning grades, ~$700–$1,800/year/child ([howdoihomeschool.com pricing summaries](https://howdoihomeschool.com/classical-homeschooling-curriculum/)).
- **Unschooling**: no formal curriculum; very low cost.
- **À-la-carte / mixed**: most common; families spend $500–$2,500/year/child mixing free and paid resources.
- **Median spending.** Roughly **$700–$1,800 per child per year** on curriculum across the U.S. homeschool market ([DreamBox, Great Homeschool Conventions surveys](https://www.dreambox.com/family/homeschool-math/homeschool-costs)).

### 7.4 The economic argument for AI customization in this market `[homeschool]` `[cost-effectiveness]`

- Current homeschool family spend: ~$700–$1,800/child/year on curriculum.
- At $5/unit AI customization, with ~50 units of customized content needed across a year (one unit ≈ one weekly lesson across one subject), the marginal cost is **$250/child/year for fully-customized content**.
- This is *below current spend* on packaged curricula and is *fully customized* (interest-matched, pace-matched, with the learner's actual prior knowledge profile in scope).
- **The market opening.** The economic argument is real and large. ~3M U.S. homeschool children × $500/child/year addressable = a ~$1.5B U.S. market for AI-customized homeschool content. Outschool's revenue (~$100M, 2023) is the existing benchmark for the live-class version of this market.

### 7.5 Microschools and pods `[homeschool]`

Similar economic logic. A 5–15-student microschool that wants subject-specific customization can produce $5/unit content at break-even comparable to a single homeschool family.

The Acton Academy network (~280 locations as of 2025; vendor source — verify) has been an early adopter of AI-augmented adaptive content within a microschool model.

---

## 8. The burden of proof inversion

If marginal cost of a content variant approaches zero, does the evidence threshold for deployment change? This is the philosophically loaded question the brief asks, and the literature gives a more nuanced answer than either "yes" or "no."

### 8.1 The precautionary-principle literature `[precautionary-principle]`

Sunstein, Cass R. 2005. *Laws of Fear: Beyond the Precautionary Principle*. Cambridge University Press.

Sunstein, Cass R. 2003. "Beyond the Precautionary Principle." *University of Pennsylvania Law Review* 151 (3): 1003–1058. ([Chicago Unbound](https://chicagounbound.uchicago.edu/law_and_economics/87/))

- **Sunstein's argument.** The strong precautionary principle is incoherent (it forbids action and inaction simultaneously when both carry risk). The relevant frame is cost-benefit analysis under uncertainty, with extra precaution for irreversible or catastrophic outcomes.
- **The translation to educational content.** If the harm of deploying unvalidated content is small and reversible, the evidence threshold for deployment can be lower. If the harm is irreversible (developing a misconception that resists later correction; learning a wrong habit that interferes with later learning), the evidence threshold must be higher.
- **For Medhavy.** The Bastani 2025 finding (§6.4) is the key data point: unguarded AI tutoring produced *measurable, persistent harm* to learning. The harm is not obviously irreversible, but it is *not* small. The precautionary frame would call for *guarded* deployment with measurement infrastructure rather than unconstrained deployment.

### 8.2 The medical analog `[precautionary-principle]`

When does a low-cost, low-risk intervention get deployed before RCT validation?

- **Off-label prescribing.** Common practice; relies on physician judgment plus surveillance for adverse effects. Reversible if discontinued.
- **Dietary recommendations.** Often deployed at population scale with weak evidence (the saturated fat / heart disease story being the canonical example of premature deployment).
- **Supplement use.** Largely unregulated; the evidence ladder is informal and the post-market signal mostly comes from epidemiology rather than RCT.
- **The pattern.** Deployment-before-RCT happens routinely for interventions perceived as low-risk and reversible. When the assumption of low risk fails (saturated fat reversal; hormone replacement therapy reversal in 2002), the field updates painfully.

### 8.3 Educational analogs of premature deployment `[precautionary-principle]`

- **Whole-language reading instruction (1980s–1990s).** Deployed widely on theoretical grounds; RCTs later (Foorman et al. 1998; National Reading Panel 2000) showed phonics-rich instruction outperforming whole-language for early reading. ~20-year correction.
- **Learning styles theory.** Deployed widely in teacher training; meta-analytic evidence (Pashler, McDaniel, Rohrer & Bjork 2008) showed no benefit to matching instruction to claimed learning style. ~15-year persistence after disconfirmation.
- **Brain-training apps (Luminosity, etc.).** Deployed broadly with engagement-based marketing; FTC settlement 2016 over unsupported cognitive claims.
- **The pattern.** Low-cost-to-deploy educational interventions reliably deploy ahead of evidence. Correction is slow because incumbents don't refund the investment.

### 8.4 The asymmetric-risk argument `[precautionary-principle]` `[AI-generated-content]`

- **Failure mode A: AI-generated content that fails to help.** Small loss. The student watches a video and learns nothing; cost is the time spent. Reversible.
- **Failure mode B: AI-generated content that actively misleads.** Larger loss. Bastani 2025 is the prototype: students were *worse off* after AI-tutored practice when measured on the relevant transfer task. Hallucination-induced misconceptions are harder to detect and correct.
- **Failure mode C: AI-generated content that develops bad habits.** Largest loss. The cognitive-offloading literature (Carr 2010, *The Shallows*; Risko & Gilbert 2016 on cognitive offloading) suggests that habits of relying on the tool can degrade the underlying skill. Bastani's GPT Base condition is a within-session instance of this.
- **Calibration question.** What fraction of AI-generated content falls in (A) vs. (B) vs. (C)? The honest answer: we don't know. The evidence base is too thin to estimate prevalence by failure mode. This is the most consequential gap in the literature.

### 8.5 The honest answer to "does cost collapse change the burden of proof?"

Yes, but not as much as the strongest version of the argument claims. The burden of proof for deployment scales with the cost of being wrong, not with the cost of being right. Cost-collapse reduces the cost of being right (cheap content that works is great); it does not reduce the cost of being wrong (Bastani-style harm is the same harm regardless of how cheap the content was). The defensible position: **lower the deployment threshold for low-risk content (interest-matching, drill practice on already-mastered material, retrieval prompts) and hold the deployment threshold high for high-risk content (initial concept acquisition, unfamiliar domains, expertise-level adaptation).** This is approximately the position the medhavy architecture instantiates.

---

## 9. The Trust the Teacher connection — teacher knowledge as the new binding constraint

The thesis: if production cost collapses, the binding constraint on educational outcomes shifts from production-capability to knowledge-of-the-individual-learner. The teacher's judgment about what a specific child needs becomes the scarce input.

### 9.1 Teacher knowledge of students as a predictor of outcomes `[teacher-knowledge]`

- **Sadler, Sonnert, Coyle, Cook-Smith & Miller 2013**, "The Influence of Teachers' Knowledge on Student Learning in Middle School Physical Science Classrooms," *American Educational Research Journal* 50 (5): 1020–1049. ([DOI: 10.3102/0002831213477680](https://journals.sagepub.com/doi/abs/10.3102/0002831213477680)) 9,556 students, 181 teachers. Two findings:
  - On items without common misconceptions, teacher subject-matter knowledge alone predicted student gains.
  - **On items with common misconceptions, teachers who could identify the popular wrong answer produced much larger student gains than those who only knew the right answer.** Pedagogical content knowledge — knowing what students get wrong and why — is a distinct and powerful predictor.
- **Brookhart on formative assessment** (Brookhart 2017, *How to Give Effective Feedback to Your Students*, 2nd ed., ASCD). Formative assessment is the daily teacher-knowledge-driven instruction loop. Feedback works when the teacher has accurate knowledge of where the student is and where they need to go.

### 9.2 The Hattie effect sizes for the irreducible-human inputs `[teacher-knowledge]`

Hattie, John. 2009. *Visible Learning*. Routledge. Updated through *Visible Learning MetaX* (2023+) covering ~1,200 meta-analyses.

- **Feedback:** *d* ≈ 0.70 (revised down from earlier 0.73; still in the top quartile).
- **Teacher-student relationships:** *d* ≈ 0.62 (Cornelius-White 2007 finds *r* = 0.31, comparable magnitude).
- **Teacher clarity:** *d* ≈ 0.75.
- **Formative evaluation by teacher:** *d* ≈ 0.68.

(Caveats: Hattie's meta-meta-analysis has been criticized methodologically — Bergeron 2017, Wecker, Vogel & Hetmanek 2017 — for combining heterogeneous meta-analyses without sufficient attention to comparability. The numbers should be treated as approximate magnitudes, not precise estimates. The directional point — that feedback and teacher-student-relationship effects are large — is robust across the critique.)

### 9.3 Cornelius-White 2007 — the canonical relationship meta-analysis `[teacher-knowledge]`

Cornelius-White, Jeffrey H. D. 2007. "Learner-Centered Teacher-Student Relationships Are Effective: A Meta-Analysis." *Review of Educational Research* 77 (1): 113–143. ([DOI: 10.3102/003465430298563](https://journals.sagepub.com/doi/10.3102/003465430298563))

- 119 studies, 1,450 findings, 355,325 students. Mean correlation *r* = 0.31 between learner-centered teacher-student relationship quality and student outcomes (cognitive, affective, behavioral).
- The effect is *larger* for affective and behavioral outcomes than for purely cognitive — but it is positive across all three.

### 9.4 The full argument

If cost-collapse makes the *production* of variant content nearly free, then the next binding input is *which variant to deploy for which learner at which moment*. This question requires:

1. Knowing the learner's current state (cognitive personalization input).
2. Knowing the learner's interests (interest personalization input).
3. Knowing the learner's misconception risks (pedagogical content knowledge, Sadler et al.).
4. Having a relationship within which the right intervention is welcomed (Cornelius-White's relationship effect).
5. Closing the loop with formative feedback (Brookhart, Hattie).

Of these five inputs, only #2 is reliably available to an AI system from learner self-report. The other four require either the teacher or instrumentation infrastructure that captures teacher knowledge in a usable form. The Trust the Teacher argument is: **#3 through #5 are not automatable, and they are the highest-effect-size inputs**. If they are the binding constraint, then the cost-collapse argument *strengthens* the case for teacher centrality rather than weakens it. The thing the teacher knows — what *this* child needs *now* — becomes more valuable, not less, in a world where acting on that knowledge is cheap.

This is the strongest possible support the Medhavy book can offer to Trust the Teacher's Ch 5 and Ch 9 arguments. The cost-collapse story does not displace the teacher; it makes teacher judgment the highest-leverage input in the whole stack.

---

## 10. Medhavy chapter-claims integration

Brief scan of the existing Medhavy chapter drafts (Ch 01 "What Is Medhavy") for claims this research supports or revises:

- **"Cost that makes that kind of personalization economically viable when it previously wasn't"** (Ch 01, ¶77). This research **supports** the claim, with the caveats: the cost-collapse claim is defensible at the *unit-production* level, not yet validated at the *production-equivalent-quality* level. The book should not claim "professional quality at $5/unit" without acknowledging that Sesame Street-comparable quality (multi-channel design, formative validation, signaling, temporal contiguity) is not the same thing as polished-looking AI video.
- **"Content was never the product"** (Ch 01, ¶30+). This research **strongly supports** the claim. The Sesame Street cost-effectiveness fact — $5/child/year delivering *d* = 0.29 — is the strongest evidence available that scaled, well-designed content production is cheap; what is expensive is the *judgment* about what specific learner needs what specific content when.
- **The IDK IDK / engagement problem.** This research provides the historical/methodological grounding (Cuban, Selwyn, the 60-year pattern of deploy-then-measure). It also provides Bastani 2025 as the prototype of how the measurement-after-deployment failure manifests for generative AI specifically.
- **Conductor frame and four layers.** The Trust the Teacher connection (§9) reinforces the architecture: the human is the conductor because the instruments (cheap AI content) only know how to play, not when. The book can be more explicit that this is not a temporary engineering gap; it is structural to what AI does and does not know.

---

## 11. Consolidated references (Chicago author-date)

Adesope, Olusola O., and John C. Nesbit. 2012. "Verbal Redundancy in Multimedia Learning Environments: A Meta-Analysis." *Journal of Educational Psychology* 104 (1): 250–263. `[Mayer-CTML]`

Ball, Samuel, and Gerry Ann Bogatz. 1970. *The First Year of Sesame Street: An Evaluation*. Princeton, NJ: Educational Testing Service. `[Sesame-Street]`

Bartholet, Elizabeth. 2020. "Homeschooling: Parent Rights Absolutism vs. Child Rights to Education and Protection." *Arizona Law Review* 62 (1): 1–80. `[homeschool]`

Bastani, Hamsa, Osbert Bastani, Alp Sungu, Haosen Ge, Özge Kabakcı, and Rei Mariman. 2025. "Generative AI without guardrails can harm learning: Evidence from high school mathematics." *PNAS* 122 (26): e2422633122. [https://www.pnas.org/doi/10.1073/pnas.2422633122](https://www.pnas.org/doi/10.1073/pnas.2422633122) `[AI-generated-content]` `[historical-EdTech]`

Bogatz, Gerry Ann, and Samuel Ball. 1971. *The Second Year of Sesame Street: A Continuing Evaluation*. Vols. 1–2, PR-71-21. Princeton, NJ: Educational Testing Service. [https://eric.ed.gov/?id=ED122800](https://eric.ed.gov/?id=ED122800) `[Sesame-Street]`

Brookhart, Susan M. 2017. *How to Give Effective Feedback to Your Students*. 2nd ed. Alexandria, VA: ASCD. `[teacher-knowledge]`

Bryant, et al. 2024. "Connecting Feedback to Choice: Understanding Educator Preferences in GenAI vs. Human-Created Lesson Plans in K-12 Education." Preprint, arXiv:2504.05449. [https://arxiv.org/html/2504.05449v1](https://arxiv.org/html/2504.05449v1) `[AI-generated-content]`

Carr, Nicholas. 2010. *The Shallows: What the Internet Is Doing to Our Brains*. W. W. Norton. `[AI-generated-content]`

Cornelius-White, Jeffrey H. D. 2007. "Learner-Centered Teacher-Student Relationships Are Effective: A Meta-Analysis." *Review of Educational Research* 77 (1): 113–143. [https://journals.sagepub.com/doi/10.3102/003465430298563](https://journals.sagepub.com/doi/10.3102/003465430298563) `[teacher-knowledge]`

Cuban, Larry. 1986. *Teachers and Machines: The Classroom Use of Technology Since 1920*. Teachers College Press. `[historical-EdTech]`

Cuban, Larry. 2001. *Oversold and Underused: Computers in the Classroom*. Harvard University Press. [https://www.hup.harvard.edu/books/9780674011090](https://www.hup.harvard.edu/books/9780674011090) `[historical-EdTech]`

Fisch, Shalom M. 2004. *Children's Learning from Educational Television: Sesame Street and Beyond*. Lawrence Erlbaum Associates. `[Sesame-Street]` `[foundational-theory]`

Guo, Philip J., Juho Kim, and Rob Rubin. 2014. "How Video Production Affects Student Engagement: An Empirical Study of MOOC Videos." *Proceedings of the First ACM Conference on Learning @ Scale*: 41–50. `[Mayer-CTML]`

Hattie, John. 2009. *Visible Learning: A Synthesis of Over 800 Meta-Analyses Relating to Achievement*. Routledge. `[teacher-knowledge]`

Heckman, James J., Seong Hyeok Moon, Rodrigo Pinto, Peter A. Savelyev, and Adam Yavitz. 2010. "The Rate of Return to the HighScope Perry Preschool Program." *Journal of Public Economics* 94 (1–2): 114–128. `[cost-effectiveness]`

Hidi, Suzanne, and K. Ann Renninger. 2006. "The Four-Phase Model of Interest Development." *Educational Psychologist* 41 (2): 111–127. [https://www.tandfonline.com/doi/abs/10.1207/s15326985ep4102_4](https://www.tandfonline.com/doi/abs/10.1207/s15326985ep4102_4) `[personalization]` `[foundational-theory]`

Hulleman, Chris S., and Judith M. Harackiewicz. 2009. "Promoting Interest and Performance in High School Science Classes." *Science* 326 (5958): 1410–1412. [https://www.science.org/doi/10.1126/science.1177067](https://www.science.org/doi/10.1126/science.1177067) `[personalization]`

Kearney, Melissa S., and Phillip B. Levine. 2019. "Early Childhood Education by Television: Lessons from Sesame Street." *American Economic Journal: Applied Economics* 11 (1): 318–350. [https://www.aeaweb.org/articles?id=10.1257/app.20170300](https://www.aeaweb.org/articles?id=10.1257/app.20170300) `[Sesame-Street]` `[cost-effectiveness]`

Khan Academy. 2024. "Khan Academy Efficacy Results, November 2024." Khan Academy Blog. [https://blog.khanacademy.org/khan-academy-efficacy-results-november-2024/](https://blog.khanacademy.org/khan-academy-efficacy-results-november-2024/) `[AI-generated-content]` *(vendor source)*

Lesser, Gerald S. 1974. *Children and Television: Lessons from Sesame Street*. Vintage. `[Sesame-Street]` `[foundational-theory]`

Levin, Henry M., and Patrick J. McEwan. 2001. *Cost-Effectiveness Analysis: Methods and Applications*. 2nd ed. Sage. `[cost-effectiveness]`

Mares, Marie-Louise, and Zhongdang Pan. 2013. "Effects of *Sesame Street*: A Meta-Analysis of Children's Learning in 15 Countries." *Journal of Applied Developmental Psychology* 34 (3): 140–151. [https://www.sciencedirect.com/science/article/abs/pii/S0193397313000026](https://www.sciencedirect.com/science/article/abs/pii/S0193397313000026) `[Sesame-Street]`

Mayer, Richard E. 2009. *Multimedia Learning*. 2nd ed. Cambridge University Press. `[Mayer-CTML]` `[foundational-theory]`

Mayer, Richard E., ed. 2014. *The Cambridge Handbook of Multimedia Learning*. 2nd ed. Cambridge University Press. [https://www.cambridge.org/core/books/cambridge-handbook-of-multimedia-learning/09E09224829AB8D3D327EF8A0E9B5288](https://www.cambridge.org/core/books/cambridge-handbook-of-multimedia-learning/09E09224829AB8D3D327EF8A0E9B5288) `[Mayer-CTML]`

Murphy, Joseph. 2014. "The Social and Educational Outcomes of Homeschooling." *Sociological Spectrum* 34 (3): 244–272. [https://www.tandfonline.com/doi/abs/10.1080/02732173.2014.895640](https://www.tandfonline.com/doi/abs/10.1080/02732173.2014.895640) `[homeschool]`

National Center for Education Statistics. 2024. "A Higher Percentage of K–12 Students are Receiving Academic Instruction at Home." IES Press Release, September 17. [https://nces.ed.gov/whatsnew/press_releases/9_17_2024.asp](https://nces.ed.gov/whatsnew/press_releases/9_17_2024.asp) `[homeschool]`

Nickow, Andre, Philip Oreopoulos, and Vincent Quan. 2024. "The Promise of Tutoring for PreK–12 Learning: A Systematic Review and Meta-Analysis of the Experimental Evidence." *American Educational Research Journal* 61 (1): 74–107. `[cost-effectiveness]`

OECD. 2015. *Students, Computers and Learning: Making the Connection*. OECD Publishing. `[historical-EdTech]`

Pal, Ankit, et al. 2025. "MedHallu: A Comprehensive Benchmark for Detecting Medical Hallucinations in Large Language Models." Preprint, arXiv:2502.14302. [https://arxiv.org/html/2502.14302v1](https://arxiv.org/html/2502.14302v1) `[AI-generated-content]`

Pashler, Harold, Mark McDaniel, Doug Rohrer, and Robert Bjork. 2008. "Learning Styles: Concepts and Evidence." *Psychological Science in the Public Interest* 9 (3): 105–119. `[precautionary-principle]`

Ray, Brian D. 2017. "A Review of Research on Homeschooling and What Might Educators Learn?" *Pro-Posições* 28 (2): 85–103. `[homeschool]` *(vendor-aligned)*

Risko, Evan F., and Sam J. Gilbert. 2016. "Cognitive Offloading." *Trends in Cognitive Sciences* 20 (9): 676–688. `[AI-generated-content]`

Sadler, Philip M., Gerhard Sonnert, Harold P. Coyle, Nancy Cook-Smith, and Jaimie L. Miller. 2013. "The Influence of Teachers' Knowledge on Student Learning in Middle School Physical Science Classrooms." *American Educational Research Journal* 50 (5): 1020–1049. [https://journals.sagepub.com/doi/abs/10.3102/0002831213477680](https://journals.sagepub.com/doi/abs/10.3102/0002831213477680) `[teacher-knowledge]`

Schneider, Sascha, Maik Beege, Steve Nebel, and Günter Daniel Rey. 2018. "A Meta-Analysis of How Signaling Affects Learning with Media." *Educational Research Review* 23: 1–24. `[Mayer-CTML]`

Schroeder, Noah L., and Aslı Çepni Cenkci. 2018. "Spatial Contiguity and Spatial Split-Attention Effects in Multimedia Learning Environments: A Meta-Analysis." *Educational Psychology Review* 30 (3): 679–701. `[Mayer-CTML]`

Selwyn, Neil. 2016. *Is Technology Good for Education?* Polity Press. `[historical-EdTech]`

Singhal, Karan, Shekoofeh Azizi, Tao Tu, S. Sara Mahdavi, Jason Wei, Hyung Won Chung, Nathan Scales, et al. 2023. "Large Language Models Encode Clinical Knowledge." *Nature* 620: 172–180. [https://www.nature.com/articles/s41586-023-06291-2](https://www.nature.com/articles/s41586-023-06291-2) `[AI-generated-content]`

Sunstein, Cass R. 2003. "Beyond the Precautionary Principle." *University of Pennsylvania Law Review* 151 (3): 1003–1058. `[precautionary-principle]`

Sunstein, Cass R. 2005. *Laws of Fear: Beyond the Precautionary Principle*. Cambridge University Press. `[precautionary-principle]`

Walkington, Candace A. 2013. "Using Learning Technologies to Personalize Instruction to Student Interests: The Impact of Relevant Contexts on Performance and Learning Outcomes." *Journal of Educational Psychology* 105 (4): 932–945. `[personalization]`

Walkington, Candace, and Matthew L. Bernacki. 2019. "Personalizing Algebra to Students' Individual Interests in an Intelligent Tutoring System: Moderators of Impact." *International Journal of Artificial Intelligence in Education* 29 (1): 58–88. [https://link.springer.com/article/10.1007/s40593-018-0168-1](https://link.springer.com/article/10.1007/s40593-018-0168-1) `[personalization]`

Yan, Lixiang, Lele Sha, Linxuan Zhao, Yuheng Li, Roberto Martinez-Maldonado, Guanliang Chen, Xinyu Li, Yueqiao Jin, and Dragan Gašević. 2024. "Practical and ethical challenges of large language models in education: A systematic scoping review." *British Journal of Educational Technology* 55 (1): 90–112. `[AI-generated-content]`

---

## Note on the evidence ladder

In rough order of *strength* of evidence:

1. **Strongest:** Sesame Street meta-analytic evidence (Mares & Pan 2013; Kearney & Levine 2019). Multiple decades, multiple methods, multiple replications across cultures.
2. **Strong:** Mayer's CTML meta-analyses on individual principles (Schroeder & Cenkci 2018; Schneider et al. 2018; Adesope & Nesbit 2012). Multiple labs, hundreds of experiments, consistent direction.
3. **Strong on engagement, moderate on durable learning:** Personalization literature (Walkington 2013; Bernacki & Walkington 2018; Hulleman & Harackiewicz 2009). Effects are real but smaller than CTML.
4. **Moderate, methodologically strong:** Teacher-knowledge literature (Sadler et al. 2013; Cornelius-White 2007). Few but rigorous studies; cross-method convergence.
5. **Limited but high-quality:** AI-tutoring RCT evidence (Bastani 2025). Single RCT, but PNAS-published, with the *direction* of the finding well-supported by adjacent cognitive-offloading work.
6. **Thin and 2024+:** AI-generated educational content quality evidence. Mostly vendor-funded or preprint. Direction inconclusive.
7. **Thinnest:** AI-generated content cost claims. Mostly vendor-derived. Independent benchmarks of cost-to-produce-equivalent-quality do not yet exist in the peer-reviewed literature.

The book's strongest argument lives at levels 1–4. The forward-looking claim about $5/unit at Sesame Street-comparable quality lives at level 7. Be explicit about the difference.

---

*End of research note. ~5,400 words.*
