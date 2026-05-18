# Research Notes — Appendix C: The GLP Framework — Technical Specification

*Pantry research note for the production appendix `C-glp-technical-specification.md`. Compiled 2026-05-17 for the Medhavy book project. Author: research subagent for Nik Bear Brown.*

> **Load-bearing preprint blocker.** The GLP preprint named in TIKTOC §App C (under the "Frictional / Irreducibly Human series") is **not present in the pantry**. The "Causal Graphs: A Testable Architecture for Pedagogical Research Using AI-Mediated Instruction" txt file is the Hattie-DAG / SUTVA-by-design paper, which is *adjacent* to GLP but is not the GLP technical specification. The Y1–Y7 framework, ensemble architecture, tier calibration, and validation methodology in these notes are *reconstructed* from existing pantry sources — primarily `05-the-measurement-layer_notes.md` §A–§D, the plain-English seven-signal sketch in `02-why-does-solving-it-require-a-platform.md`, and the ensemble-architecture sketch in `04-what-makes-this-different.md`. **Section G is the resolution path:** the author either (i) provides the preprint to the pantry, in which case this appendix is rewritten to match, or (ii) approves the reconstruction here as canonical, in which case Appendix C becomes the first formal published statement of the framework. The choice is consequential — the appendix is the document the rest of the book cites for GLP particulars. Do not draft the appendix from these notes without making this choice first.

---

## §A. What the appendix has to do

Appendix C is a technical reference, not a chapter. The reader who arrives here has already read Chapter 5 and wants the specification at engineering depth — the equations or operationalizations they would need to implement, the architecture they would need to replicate, and the validation methodology they would need to run to test the platform's measurement claims. The voice register shifts. Chapter 5 unfolds the framework as discovery; Appendix C states it as specification.

Three constraints organize the appendix:

1. **Cite Chapter 5 for motivation, not for specification.** The reader is here because they want the formal statement, not the narrative justification. Cross-reference Chapter 5 §A (the decoupling problem), §B (neurobiological grounding), and §E (the fluency trap) for the *why*. The appendix's job is the *what* and the *how*.

2. **Distinguish preprint-anchored from reconstructed material.** Where the seven components and the ensemble architecture are reconstructed from pantry sources rather than lifted from a published preprint, the appendix must flag this. The Medhavy book's epistemic commitment (Chapter 4 §J on building publicly) requires that this distinction be visible at the appendix level, not only in the front-matter caveats. Each section flags its provenance: `[preprint-anchored]`, `[reconstructed from Ch 5 notes]`, `[design specification — pending validation]`.

3. **Operationalize, do not narrate.** The appendix supplies the type signature for each GLP component: what is logged, how it is computed, what the output represents, what the failure modes are. A researcher who wants to replicate the framework on their own platform should be able to read Appendix C and know what to build.

The eight sections of the appendix below follow the TIKTOC §App C contents list, expanded with operational specifications drawn from the Ch 5 notes.

---

## §B. The seven GLP components — full specification

`[reconstructed from Ch 5 notes §C; canonical Y1–Y7 names pending preprint verification]`

The seven components are specified here with six fields each, matching the Ch 5 notes §C structure. The appendix should retain this six-field structure — it is the operational specification a research replicator needs.

### B.1 Y1 — Temporal Engagement Pattern

- **Construct.** Genuine engagement tracks the difficulty surface of the concept; borrowed certainty tracks output length. The cognitive-load translation: a learner working with material whose intrinsic load exceeds their automaticity spends disproportionately more time at the high-load moves (Sweller 1988; van Merriënboer & Sweller 2005).
- **Data logged.** Sub-section-granularity event timestamps; attention markers (scroll position, cursor activity, page focus, tab switches); edit traces in any productive interaction; paste-event flags.
- **Computed signal.** For each concept *c* with sub-sections {*s*₁ … *s*ₙ} of estimated intrinsic load *L*(*s*ᵢ), let *T*(*s*ᵢ) be the learner's time on *s*ᵢ. The engagement-vs-load fit is the rank correlation between *L*(*s*ᵢ) and *T*(*s*ᵢ) over the concept's sub-sections. A learner-relative version is the deviation of this fit from the learner's prior fit on similar-load material. `[reconstructed — exact metric pending preprint]`
- **Output.** Scalar in [0, 1] representing P(genuine engagement | Y1 alone), with associated variance. Low scores flag flat or output-proportional distributions.
- **Borrowed-certainty signature.** Flat distribution; time tracks word count or required output length; paste events at the boundary of high-load sub-sections.
- **Implementation.** Cheapest of the seven to instrument from existing telemetry. Sub-page granularity is required; page-level granularity is insufficient. Approximable from LMS clickstream only at page level, which loses most of the signal.

### B.2 Y2 — Error Trajectory Coherence

- **Construct.** Knowledge-component theory (Koedinger, Corbett & Perfetti 2012, *Cognitive Science* 36(5): 757–798) — learning is the acquisition of structured skill components; errors during learning trace which components are underdeveloped. Coherent errors share a latent cause; random errors do not.
- **Data logged.** The actual response (not just right/wrong); the timestamped sequence; the concept tag for each item; the misconception classification for each error, drawn from the misconception model produced by the curriculum design layer (Ch 8).
- **Computed signal.** Bayesian Knowledge Tracing-style posterior over (misconception state × concept) — see standard BKT formulation in Corbett & Anderson 1995 (*User Modeling and User-Adapted Interaction* 4(4): 253–278). Error coherence is the posterior probability that the error sequence is consistent with a single trajectory through the misconception graph. `[preprint may extend to Deep Knowledge Tracing (Piech et al. 2015); verify]`
- **Output.** Scalar in [0, 1] = P(genuine engagement | Y2 alone). Variance grows with sequence length until trajectory is identifiable.
- **Borrowed-certainty signature.** High variance in error type across closely related items; errors that look like content-pattern-matching errors (surface feature picked up and misapplied) rather than reasoning errors (wrong strategy attempted and discovered to fit poorly).
- **Implementation.** Requires the misconception model from the curriculum design layer. Uncomputable without it. The misconception model is the Y2 prerequisite — and the Y2 prerequisite is what differentiates Tic TOC-designed courses from prerequisite-mapping-free courses (Ch 8). Approximation from LMS data: possible only if LMS response data is post-processed against an externally supplied misconception model.

### B.3 Y3 — Cross-Context Transfer

- **Construct.** Transfer-appropriate processing (Morris, Bransford & Franks 1977, *Journal of Verbal Learning and Verbal Behavior* 16(5): 519–533); Bjork & Bjork 1992 retrieval-strength / storage-strength duality; Barnett & Ceci 2002 taxonomy of far transfer. A representation that is learned (rather than memorized in context) retrieves under cue mismatch.
- **Data logged.** For each concept *c*, the contexts {*x*₁ … *x*ₘ} in which the learner has encountered it. For each subsequent encounter at context *x*ⱼ, the context-similarity *d*(*x*ⱼ, instructional-context) and the learner's performance.
- **Computed signal.** Performance × context-similarity curve. A flat curve is strong transfer evidence; a steep falloff is weak transfer evidence. Operationally: regression slope of performance against *d*(*x*ⱼ, instructional-context). A learner-relative version compares the slope against the population norm for that concept.
- **Output.** Scalar in [0, 1] = P(transfer | Y3 alone), with variance from limited context-diversity within the available data.
- **Borrowed-certainty signature.** Performance high in instructional-context items, near-zero in low-similarity-context items. The student does "this kind of problem" but not "this concept in a different problem."
- **Implementation.** Hardest signal to obtain cleanly — requires deliberately divergent contexts as part of the platform's content design. The Book Library's multi-framing content design (Ch 4 Layer 2; Ch 9) provides cross-context items as a byproduct. Not approximable from LMS data unless cross-context items were authored in.

### B.4 Y4 — Uncertainty Calibration

- **Construct.** Metacognitive monitoring (Nelson & Narens 1990 framework; Dunning, Heath & Suls 2004 review of miscalibration). The capacity to distinguish what you know from what you don't is a separable cognitive operation. Borrowed knowledge inherits the *certainty* of the source without the meta-experience that produces calibrated certainty.
- **Data logged.** Pre-response confidence rating (forced *before* the answer is revealed; otherwise the rating is post-hoc rationalization, not calibration). Accuracy on the response. The calibration curve aggregated across all rated items.
- **Computed signal.** Calibration index — slope of the confidence-accuracy regression, or the Brier score for probabilistic ratings. A slope of 1.0 is perfect calibration; near-zero slope means "confidence does not track accuracy"; negative slope means "the learner is more confident when wrong." `[verify preprint's specific metric]`
- **Output.** Scalar in [0, 1] = P(genuine engagement | Y4 alone). Y4 is one of the highest-information individual components when the learner population spans a range of self-evaluation skill.
- **Borrowed-certainty signature.** High confidence + low accuracy. The learner inherits the surface fluency of the AI response and reports confidence proportional to that fluency, but the underlying accuracy is the AI's, which the learner cannot evaluate. This is the *vetting failure* mechanism (Selwyn 2022; cf. `ask-ai-research.md`).
- **Implementation.** Requires a specific interaction design — pre-response confidence elicitation. Straightforward to add to any quiz interaction. Cannot be retrofitted from existing data; the rating must precede the answer.

### B.5 Y5 — Social Knowledge Texture

- **Construct.** The textural signature of authentic encounter with material — specific confusions, genuine surprise at unexpected results, position changes that track developing understanding rather than authority signals. Theoretically diffuse: draws on conversation analysis (Goodwin 1981), situated cognition (Lave & Wenger 1991), classroom-discourse analysis (Mehan 1979 on IRE patterns; Wells 1999 on dialogic inquiry).
- **Data logged.** Free-form text from chat-style interactions (Ask AI sessions; Glimmer reflections; mode-transition prompts). Position-change events (when the learner updates a stated belief). Surprise markers ("wait, I expected X" and behavioral analogs — long pause + revision, abandonment-and-return).
- **Computed signal.** Multiple sub-signals composed: specificity-of-confusion score (NLP classifier trained on the labeled corpus described in §E); position-change frequency over the session; surprise-marker frequency. The composite is the rank of this learner's session-level texture against the population for the same concept-and-mode. `[reconstructed — specific NLP pipeline pending preprint]`
- **Output.** Scalar in [0, 1] = P(genuine engagement | Y5 alone), with large variance because Y5 has the highest individual error rate of the seven.
- **Borrowed-certainty signature.** Generic questions; no position changes; no surprise. The learner is not encountering the material; they are processing it as a series of items to complete.
- **Implementation.** The most experimental of the seven. The NLP classification is non-trivial and may require domain-specific tuning. Y5 is also the most vulnerable to adversarial gaming (an LLM-driven gamer can generate textured-looking language). The honest framing for the appendix: Y5 is included for ensemble value, not as a standalone signal. See §D on ensemble weighting.

### B.6 Y6 — Retrieval Strength Decay Signature

- **Construct.** Bjork & Bjork (1992) storage-strength / retrieval-strength duality. Retrieval strength is the moment-to-moment accessibility of a memory; storage strength is the durability of the underlying trace. The two dissociate: a learner can have high retrieval strength right after instruction while having low storage strength. Population-level decay parameters come from the Cepeda et al. 2006 and 2008 spacing meta-analyses (*Psychological Bulletin* 132(3): 354–380; *Psychological Science* 19(11): 1095–1102).
- **Data logged.** Initial performance on the concept; scheduled retest performance at intervals (FSRS-style scheduling per `quiz-me-research.md`); fitted decay curve.
- **Computed signal.** Retention rate parameter from the fitted decay model. A rate within population norms indicates strong storage; a rate sharply steeper than the norm indicates "performance, not learning." Operationally: log-linear regression of accuracy against interval, compared to the population-norm slope for the concept.
- **Output.** Scalar in [0, 1] = P(durable learning | Y6 alone). Y6 is the highest-information *single* component because it is the most direct measurement of the storage strength the AI bypass cannot produce.
- **Borrowed-certainty signature.** Initial performance high (the artifact looked good); retest performance crashes (there was nothing consolidated to retest). This is the most directly observable artifact of the AI-bypass on the learning cascade — the student passed the immediate test, BDNF-mediated consolidation never happened, the retest catches the absence.
- **Implementation.** Requires the platform to retest on its own schedule (FSRS or equivalent), not the professor's syllabus schedule. This is a phase-gate decision (Ch 6) and a curriculum-design decision (Ch 8). The FSRS algorithm is the implementation engine. Not approximable from LMS data unless the LMS already includes platform-scheduled retest items.

### B.7 Y7 — Scaffolding Response Curve

- **Construct.** Vygotsky's zone of proximal development operationalized as a measurable curve. Pea 2004 (*Journal of the Learning Sciences* 13(3): 423–451) on contingent scaffolding. Atkinson, Renkl & Merrill 2003 (*Journal of Educational Psychology* 95: 774–783) on backwards-faded worked examples — scaffolding should fade as competence grows, and the fading rate is itself diagnostic.
- **Data logged.** Performance state before a hint; the hint itself (content and structural specificity tier); performance state after the hint; whether the learner requested a hint or it was offered.
- **Computed signal.** Δ(performance | partial hint) / Δ(performance | full explanation), aggregated per concept and learner. A high ratio indicates genuine partial understanding (the hint activated structure that was nearly there). A low ratio indicates no structure to activate.
- **Output.** Scalar in [0, 1] = P(genuine partial understanding | Y7 alone).
- **Borrowed-certainty signature.** Zero or near-zero response to hint. The learner needed the full answer, not a structural prompt. The hint had no underlying scaffold to engage with.
- **Implementation.** Requires the hint-not-answer interaction design (cf. Bastani et al. 2025 GPT-Tutor result, *PNAS* 122(26): e2422633122). The *quality* of the hint is itself a measurement instrument — a well-designed hint differentiates hint-responsive from hint-unresponsive learners; a poorly designed hint differentiates nothing. The Ask AI mode (Ch 6) and the measurement layer are the same design move at Y7. Not approximable from LMS data; Canvas-style platforms have no hint interaction.

---

## §C. The neurobiological grounding paragraph

`[from Ch 5 notes §B; appendix should retain at reference depth, not full chapter depth]`

The Y1–Y7 components are not arbitrary behavioral correlates. The framework's claim is that they are downstream consequences of the neurobiological cascade that constitutes genuine learning. The appendix's paragraph on neurobiology cites three load-bearing studies, each of which has translation caveats the chapter (and the appendix) must not paper over:

- **Schultz, Dayan & Montague 1997** (*Science* 275(5306): 1593–1599; DOI 10.1126/science.275.5306.1593) — midbrain dopaminergic neurons encode reward prediction error. Encoded learning requires a gap between expected and actual outcome. Borrowing the answer eliminates the gap and therefore eliminates the dopamine signal that drives encoding. Caveat: macaque cued-juice paradigm; translation to human classroom learning is consistent with the broader literature but not directly demonstrated by Schultz 1997. `[verify exact 1997 paper; multiple Schultz papers in this period]`

- **Cowansage, LeDoux & Monfils 2010** (*Current Molecular Pharmacology* 3(1): 12–29; PMID 20030624) — BDNF as the gatekeeper of synaptic plasticity. Consolidation of working-memory traces into durable memory requires BDNF and the slow consolidation cycle (hours to days, sleep involved). A student who used AI at midnight and submitted at 1 AM has not had the consolidation cycle. Caveat: Cowansage is a fear-extinction-focused review; the broader BDNF-consolidation literature (Lu, Christian & Lu 2008, *Nature Reviews Neuroscience* 9(6): 339–346) is the more canonical citation. Recommend the appendix cite both. `[verify Lu, Christian & Lu 2008 as the canonical reference if available]`

- **Yang, Pan & Gan 2009** (*Nature* 462(7275): 920–924; DOI 10.1038/nature08577) — in vivo two-photon imaging of motor learning shows that durable memory corresponds to formation and survival of new dendritic spines on layer-V pyramidal neurons. Caveat: mouse motor learning, not human declarative learning; the extrapolation is supported by Bailey, Kandel & Harris 2015 and Holtmaat & Svoboda 2009 but should be flagged in the appendix, not asserted.

The single load-bearing sentence the appendix needs: *the brain that submitted the AI-generated artifact never produced the prediction error, never recruited the BDNF, never formed the spines.* The seven GLP components are behavioral correlates of the absence of each of these molecular events. The link from molecular neurobiology to behavioral GLP signals is plausibility-grade, not direct-evidence-grade — the appendix should land it that way.

---

## §D. The three-layer ensemble architecture

`[reconstructed from Ch 5 notes §D and 04-what-makes-this-different.md ensemble sketch; specific weights and meta-model architecture are internal Medhavy design — pending preprint]`

The seven components are an ensemble in the technical sense: multiple noisy classifiers whose errors are partially independent, combined to produce a composite more reliable than any individual component (Dietterich 2000 in *Multiple Classifier Systems*; van der Laan, Polley & Hubbard 2007 super-learner, *Statistical Applications in Genetics and Molecular Biology* 6(1)). The argument for ensemble rests on three structural claims:

1. **Each component is individually noisy.** Y1 is confounded by external interruption; Y4 by personality factors; Y5 by NLP classifier error.
2. **The errors are partially independent.** Y1's confound (interruption) does not produce Y6's confound (the platform's retest schedule). A learner who games Y4 by under-reporting confidence does not thereby game Y2 (their error trajectory remains incoherent if it was incoherent before).
3. **The composite is more reliable.** Standard ensemble theory bounds the composite error rate below the worst individual rate and approaches the best individual rate when combination weights are well-chosen.

### D.1 Layer 1 — Component models

Seven independent models, one per Y1–Y7, each producing a probabilistic output *p*(genuine learning | component evidence) with associated variance. Each component model is trained on (or specified against) the labeled corpus described in §E below. The component models do not interact directly — they read disjoint slices of the session data and produce disjoint outputs.

The TIKTOC's mathematical-specification requirement applies here: each component model has a documented type signature (inputs from §B "Data logged"; outputs in [0, 1] with variance). The seven type signatures are the operational specification a research replicator needs.

### D.2 Layer 2 — Tier-conditioned combination

The component outputs are combined with weights that depend on the *cognitive tier* of the current activity (see §F on tier calibration). The combination function — `[reconstructed; exact form pending preprint]` — is plausibly a tier-indexed linear combination:

GLP-composite(tier *t*) = Σᵢ *w*ᵢ(*t*) · *p*ᵢ(genuine learning | component evidence)

where *w*ᵢ(*t*) is the weight on component *i* for tier *t*. The weights are constrained to sum to one for each tier. The hypothesis is that different tiers privilege different components — for recall-heavy tiers, Y4 (calibration) and Y6 (decay) carry more weight; for transfer-heavy tiers, Y3 (cross-context) and Y7 (scaffolding response) carry more weight. The weight specification is *the* technical commitment of the framework — and is the locus of the largest uncertainty in the reconstruction.

### D.3 Layer 3 — Meta-model

A final calibration step that maps the tier-conditioned composite onto the scalar (and its uncertainty) the adaptive engine (Ch 7) consumes as part of its reward signal. The meta-model's job is *uncertainty quantification*: a high-confidence GLP score and a low-confidence GLP score are different inputs to the engine, and the engine is expected to be more conservative when the GLP signal is low-confidence.

The type signature the engine consumes:

```
GLP-output = {
  glp_estimate: float ∈ [0, 1],          // tier-conditioned composite
  glp_variance: float ≥ 0,                // uncertainty
  component_contributions: dict[Y_i, float],  // for diagnostics, not used by engine
  tier: enum(T1..T7),                     // tier this estimate applies to
  concept_id: string,
  session_id: string,
  learner_id: string,
  timestamp: ISO-8601
}
```

This is the appendix's most consequential operational specification. The engine consumes this object; the rest of the platform produces it. The interface between the measurement layer and the adaptive engine is this type signature. `[verify exact field names against preprint; the schema is a reconstruction.]`

### D.4 Why three layers and not one big model

The candidate alternative is a single end-to-end learned classifier that takes the raw session data and produces GLP. The architectural argument for the three-layer decomposition:

- **Interpretability.** Each component has a documented construct from cognitive science. A clinician or researcher can read the component score and know what the framework is claiming. An end-to-end black box loses this.
- **Modular validation.** Each component can be validated independently against its construct (§E). End-to-end validation conflates multiple sources of error.
- **Tier-conditioned reasoning.** The weights *w*ᵢ(*t*) are themselves an empirical commitment. They can be learned, audited, and revised. A single end-to-end model would learn the same weights implicitly without ever surfacing them for inspection.
- **Failure-mode isolation.** When the composite fails, the three-layer decomposition allows diagnosis to a specific component or weight. End-to-end models leave the failure undiagnosed.

The Hubbard "How to Measure Anything" framing (in `_lib_how-to-measure-anything_-finding-the-value-of-_intangibles_-in-business.md`) is useful for the appendix's framing of the ensemble: a measurement is an information state that *reduces uncertainty*. The ensemble's job is not to declare "genuine learning happened / did not happen" but to update the engine's prior about whether genuine learning happened. This is an explicitly Bayesian framing the appendix should adopt.

---

## §E. Validation methodology

`[design specification — pending validation. No published RCT exists. Ch 11 confirms this gap as Open Question 1 of the eight.]`

The validation methodology is the part of the appendix where the gap between specification and evidence is widest. The platform has not yet produced a published validation study. The appendix must make this gap visible — it is consistent with the book's epistemic commitment (Ch 4 §J; Ch 11). The validation specification below is therefore *what would have to be done* to validate the framework, not *what has been done*.

### E.1 Labeled corpus construction

The framework requires a labeled corpus where ground-truth "genuine learning happened / did not happen" is known. Construction strategy:

- **Recruit two groups with verified status.** Group A: students who completed a concept under instructor proctoring (genuine learning verified by proctored exam at delay). Group B: students who completed the same concept by using an AI assistant with no instructor proctoring (artifact submitted; no proctored verification). The instructor-verified delayed-exam outcome is the ground-truth label.
- **Collect the full session data stream for each student through Medhavy.** All seven component data streams logged at platform-native granularity.
- **Label sessions, not students.** A student can have a genuine-learning session and a borrowed-certainty session in the same week. The unit of analysis is the session-concept pair, not the student.
- **Sample size.** Power analysis for component-level reliability requires at least 500 sessions per group per concept tier. For seven tiers, this is roughly 7,000 labeled sessions — within reach for a deployment with reasonable enrollment.

`[verify preprint's actual corpus design — the construction above is a reconstruction from standard ML-labeled-corpus practice plus the Ch 5 notes' suggestion that labeled data is the path forward.]`

### E.2 Calibration assessment

For each component Y1–Y7 and the composite, calibration assessment uses standard probabilistic-classifier diagnostics:

- **Reliability diagram.** Bin predicted probabilities; compare bin midpoints to observed fractions of genuine-learning labels. A well-calibrated model has bin midpoints lying on the diagonal.
- **Brier score decomposition.** Brier = reliability − resolution + uncertainty. Reliability is the calibration; resolution is the discriminative power; uncertainty is the irreducible.
- **AUC-ROC.** For binary genuine-vs-borrowed labels, the area under the ROC curve as a discrimination metric. Component-level AUCs in the 0.6–0.7 range would be expected for individually noisy signals; composite AUC in the 0.8+ range would be the ensemble payoff if the partial-independence assumption holds.

### E.3 Information gain test

The Hubbard framing — measurement as uncertainty reduction — yields a specific test the appendix should include: the *information gain* of the GLP signal over the artifact-only baseline. Operationally:

- Train a baseline classifier that predicts genuine-vs-borrowed from the artifact alone (essay text, quiz scores, submission timestamps — i.e., what Canvas already logs).
- Train the GLP composite classifier on the same labeled corpus.
- The information gain is the reduction in cross-entropy from baseline to GLP composite.
- The framework's claim — that GLP measures something the artifact does not — requires information gain ≥ some pre-specified threshold (e.g., 0.2 nats per session). If information gain is near zero, the framework is no better than artifact-only classification, and the case for the measurement layer collapses.

This is the *falsifiability test* for the GLP framework. The appendix should state this test explicitly, with the threshold pre-registered, and commit to publishing the result — positive or negative — when the labeled corpus is available. This is the Chapter 4 §J commitment operationalized at appendix depth.

### E.4 Construct validation per component

Each component should additionally be validated against its construct, separately from the composite validation:

- Y1: Does temporal engagement pattern correlate with cognitive-load measures (NASA-TLX, dual-task secondary-task performance) on the same sessions? `[design specification]`
- Y2: Does error trajectory coherence correlate with instructor-coded misconception identification on the same response sequences? `[design specification]`
- Y3: Does cross-context performance correlate with transfer-task performance on instructor-designed transfer items? `[design specification]`
- Y4: Does calibration correlate with Brier-scored confidence-rating tasks outside the platform? `[design specification]`
- Y5: Does textural classification correlate with expert raters' assessment of authentic engagement in the same sessions? `[design specification]`
- Y6: Does the decay parameter correlate with delayed-exam performance at the platform-scheduled retest delay? `[design specification — this is the most directly observable test]`
- Y7: Does scaffolding response curve correlate with instructor-observed zone-of-proximal-development assessment on the same concept? `[design specification]`

Each construct-validation test is a smaller research project. The appendix should name them as the construct-validation program the framework is committed to — not claim them as done.

### E.5 The honest disclosure

The appendix's validation section should close with the honest disclosure that Chapter 11 §2.1 develops at length: no published RCT has tested the GLP framework as an integrated unit against a control. The construct-validation program above is the *plan*. The labeled corpus is *being collected* by the Medhavy 1.5 deployment. The information gain test is *pre-registered* in this appendix and will be reported when the data are available.

This is consistent with the book's commitment (Ch 4 §J) to publishing the framework before the validation results exist. The appendix is the technical specification of what is being validated, not the report of what has been validated.

---

## §F. Tier calibration — seven cognitive tiers

`[reconstructed from Ch 5 notes ensemble-architecture sketch; the "seven tiers" naming aligns with the TIKTOC §App C contents list but the tier-by-friction-signal mapping is the appendix's most under-specified section. Recommend the author either supply the canonical tier scheme from the preprint or approve the reconstruction below.]`

The tier calibration table is the part of the appendix where the reconstruction is thinnest. The TIKTOC names "seven cognitive tiers, primary friction signal per tier" but no pantry source explicitly enumerates them. The reconstruction below is a plausible mapping that respects the structure of the seven Y1–Y7 components — it is *one* tier scheme consistent with the framework, not necessarily *the* canonical one.

### F.1 Reconstructed tier scheme

| Tier | Cognitive operation | Primary friction signal | Secondary signals | Notes |
|---|---|---|---|---|
| T1 | Recall (recognize) | Y6 — retrieval decay | Y1, Y2 | The recall-only tier — Anki territory. Y6 dominant. |
| T2 | Recall (free) | Y6 — retrieval decay | Y4, Y1 | Free recall is harder than recognition; calibration enters. |
| T3 | Comprehend (paraphrase) | Y5 — knowledge texture | Y2, Y4 | Texture is informative when the operation is understanding. |
| T4 | Apply (within-context) | Y2 — error trajectory | Y7, Y1 | Application within the instructional context — trajectory matters. |
| T5 | Apply (cross-context) | Y3 — cross-context transfer | Y7, Y4 | Transfer tier — Y3 dominant by construction. |
| T6 | Analyze / evaluate | Y7 — scaffolding response | Y4, Y5 | The ZPD tier — scaffolding response curve is the diagnostic. |
| T7 | Create / synthesize | Y5 — knowledge texture | Y7, Y3 | The Glimmer tier — texture and scaffolding response together. |

The framing maps approximately onto Bloom's revised taxonomy (Anderson & Krathwohl 2001 revision; original Bloom 1956) — though "seven tiers" is one tier off from Bloom's six revised categories, and the appendix should not claim a Bloom-mapping unless the preprint does. `[verify whether the preprint's seven-tier scheme is Bloom-derived or independent.]`

### F.2 What the tier scheme is for

Operationally, the tier scheme does three things:

1. **Indexes the weights *w*ᵢ(*t*) in the Layer-2 combination.** Different tiers privilege different components — see column 3 of the table above.
2. **Constrains the engine's mode selection.** The Adaptive Engine (Ch 7) reads the tier of the next concept-node and selects the mode whose evidence stream is informative *at that tier*. Quiz Me is informative at T1–T2; Case Study at T5–T6; Glimmer at T7.
3. **Calibrates the expected GLP-output's reliability per tier.** A low GLP-output at T1 is more interpretable than a low GLP-output at T7 — T7's measurement is intrinsically harder and the meta-model should propagate that.

### F.3 The tier-mapping flag

The TIKTOC's "primary friction signal per tier" phrasing suggests a one-to-one tier-to-signal mapping. The reconstruction above is one-to-one in the "primary" column but acknowledges secondary signals. If the preprint specifies strict one-to-one mapping (no secondaries), the appendix needs revision. If the preprint specifies a richer combination, the reconstruction here is roughly the right shape.

**Open recommendation to the author:** the tier calibration table is the section where preprint provision would most change the appendix. Without the preprint, this section is a *plausible specification consistent with the framework*, not a *canonical specification of the framework*. Mark it as such.

---

## §G. The preprint blocker and the resolution path

`[load-bearing flag — repeated from front-matter for emphasis]`

The appendix is the most preprint-dependent document in the book. Three options for the author:

### G.1 Option A — Provide the preprint

If the GLP preprint exists in Nik's files outside the pantry, the cleanest resolution is to add it to `pantry/` and rewrite Appendix C against it. This is the canonical-path option. The reconstruction in these notes becomes obsolete the moment the preprint arrives. Section provenance flags can then move from `[reconstructed from Ch 5 notes]` to `[preprint §X.Y]`.

**Action required from the author:** locate and provide the GLP preprint (the "Frictional / Irreducibly Human series" document named in TIKTOC §App C).

### G.2 Option B — Approve the reconstruction as canonical

If the GLP preprint does not yet exist as a standalone document — if the seven Y1–Y7 components and the ensemble architecture have not yet been formally published — then Appendix C *becomes* the first formal published statement of the framework. This is a meaningful authorial decision:

- The book's epistemic commitment (Ch 4 §J) is consistent with publishing the framework before validation. The reconstruction in these notes is more developed than the seven-signal sketches in `02-why-does-solving-it-require-a-platform.md` or `04-what-makes-this-different.md`. Promoting it to canonical specification is defensible.
- The reconstruction has known weak points: the exact metric for each component (§B), the precise ensemble weight scheme (§D), and the tier-to-signal mapping (§F) are *plausible specifications consistent with the chapter narrative*, not *load-bearing canonical statements*. Promoting them to canonical requires the author's review of each — the appendix's section-by-section provenance flags become the author's review checklist.

**Action required from the author:** review §B (component specifications), §D (ensemble architecture), and §F (tier calibration) and approve, revise, or replace. Each section's provenance flag becomes a sign-off.

### G.3 Option C — Defer the appendix

If neither A nor B is feasible — if the preprint is not available and the reconstruction is not yet ready to publish — the cleanest move is to ship the book without Appendix C and cite Chapter 5 as the canonical reference. The TIKTOC's "GLP preprint → Chapters 4, 5, 11, Appendix C" pointer becomes "GLP preprint → Chapters 4, 5, 11" and Appendix C is deferred to a second edition or a separate technical paper.

**Action required from the author:** decide whether the book ships with Appendix C at all.

### G.4 Recommendation

The research subagent's recommendation: **Option B is the path most consistent with the rest of the book.** The book argues (Ch 4 §J) that the field's epistemic problem is the gap between confident claim and published evidence. The appendix is an opportunity to model the alternative — to publish a specification that *can* be falsified by the §E validation methodology, with the construct-validation program named explicitly. Appendix C becomes part of the contribution rather than a placeholder.

The reconstruction in these notes is the *draft* of that contribution. Section-by-section review is needed before it ships.

---

## §H. The arms-race problem — process vs. artifact measurement

`[from Ch 5 notes §A and §G; appendix should compress to one section]`

The arms-race section in the appendix has two jobs: anchor the empirical claim that artifact-based AI detection is failing, and develop the structural argument that process-based measurement is categorically different.

### H.1 The artifact-detection failure — current evidence

The empirical literature on artifact-based AI detection has converged on three findings:

- **False-positive harm concentrates on non-native English writers.** Liang, Yuksekgonul, Mao, Wu & Zou (2023, *Patterns* 4(7): 100779; arXiv:2304.02819) tested seven major GPT detectors on 91 TOEFL essays written entirely by non-native English speakers. The detectors flagged 61.3% as AI-generated; 97.8% were flagged by at least one detector; 19.8% were unanimously misclassified by all seven. The same essays by US-born students were flagged at substantially lower rates. The discrimination signal the detectors were finding is *low perplexity*, which non-native writers also produce. The harm fell on the students least able to contest the accusation. ([Patterns: GPT detectors are biased against non-native English writers](https://www.cell.com/patterns/fulltext/S2666-3899(23)00130-7))

- **Paraphrase attacks defeat detectors.** Sadasivan, Kumar, Balasubramanian, Wang & Feizi (2023; v4 revised January 17, 2025; arXiv:2303.11156) showed both empirically and theoretically that recursive paraphrasing reduces detection accuracy to near-chance while only slightly degrading text quality. The theoretical analysis: as language models improve, the statistical distinguishability of their output from human writing approaches zero. Subsequent work (Krishna et al. 2023; "Adversarial Paraphrasing," NeurIPS 2025) generalizes the attack. ([arXiv:2303.11156](https://arxiv.org/abs/2303.11156))

- **Vendor and institutional retreat.** OpenAI discontinued its AI Classifier in July 2023 for "low rate of accuracy" ([OpenAI release note, archived July 2023](https://web.archive.org/web/20230724072139/https://openai.com/blog/new-ai-classifier-for-indicating-ai-written-text)). Turnitin's AI detection has been disabled by at least 12 elite institutions including Vanderbilt, Yale, Johns Hopkins, and Northwestern, citing unreliability — Penn State labeled it "unreliable"; University of Minnesota labeled it "NOT recommended." Subsequent peer-reviewed reviews (e.g., Weber-Wulff et al. 2023 in *International Journal for Educational Integrity*) found accuracy below 80% even before paraphrase attacks. `[verify the specific 12-institution claim and the Weber-Wulff citation against current sources at appendix draft time — institutional positions are moving.]`

The structural conclusion: artifact-based detection is a post-hoc adversarial classification problem where the adversary's tools improve faster than the detector's. The detection-versus-paraphrase loop has no equilibrium that favors the detector.

### H.2 The structural difference

Process-based measurement is categorically different from artifact-based detection. The argument runs as follows:

1. **Artifact-based detection retrains on the same substrate as the adversary.** Both sides work with the artifact (text). The discriminability of human and machine text approaches zero as models improve. The detection problem becomes statistically unsolvable in the limit.

2. **Process-based measurement instruments the cognitive work directly.** The seven GLP signals are *byproducts of the cognitive interaction* that produces learning. They exist as a function of the interaction design, not as a function of distinguishing one text from another. The signals are generated whether or not anyone is trying to detect anything.

3. **Gaming the ensemble approaches the cost of learning.** Manufacturing all seven signals simultaneously requires *doing the cognitive work*. Producing a credible Y1 (temporal engagement) requires actually spending the time on the difficult sub-concepts. Producing a coherent Y2 (error trajectory) requires producing errors in a misconception sequence — requiring a misconception, requiring an attempt. Producing a calibrated Y4 requires having the answer accuracy to calibrate against. Producing Y6 (decay signature) requires the BDNF-mediated consolidation that the decay reveals. The gaming cost rises to the cognitive cost of genuine learning.

4. **The ensemble penalizes partial gaming.** Y3 (cross-context) and Y5 (texture) are the more vulnerable signals — an AI-assisted gamer can in principle improve Y3 by having the AI solve the cross-context items and Y5 by having the AI generate textured questions. But gaming Y3 and Y5 without also gaming Y1, Y2, Y4, Y6, Y7 produces a moderate composite, not a high one. The combination weights (§D) can be tuned to penalize the suspicious-coherence-of-the-vulnerable-signals pattern.

The appendix's honest qualifier: the framework is *not* gaming-proof. It is *gaming-expensive*. The cost of gaming the full ensemble approaches the cost of learning. The target is not "make AI use undetectable" but "make genuine engagement competitive with gaming." These are different design targets.

### H.3 The connection to formative assessment literature

The structural argument has a precedent the appendix should name: the formative-assessment literature has long distinguished *evidence of process* from *evidence of product*. Black & Wiliam (1998, "Inside the Black Box: Raising Standards Through Classroom Assessment," *Phi Delta Kappan* 80(2): 139–148) argued that effective formative assessment requires *eliciting evidence of learning as it occurs*, not inferring learning from completed work. Sadler (1989, *Instructional Science* 18: 119–144; and continuing work through 2013) developed the framework where the teacher's job is to detect the gap between current state and target state during the learning, not after. ([Black & Wiliam, *Inside the Black Box*, Phi Delta Kappan 2010 reprint](https://journals.sagepub.com/doi/10.1177/003172171009200119))

GLP is a *machine-instrumentation translation* of the formative-assessment insight. The seven components are the byproducts the formative-assessment literature identified at the classroom-discourse level — specific confusions, position changes, scaffolding response — operationalized as logged signals rather than as teacher-observed signals. The appendix should claim this lineage explicitly. It is not Medhavy's invention that process evidence matters; what Medhavy claims is the platform instrumentation that produces process evidence at scale.

This is the *epistemological* difference between the GLP framework and AI-detection tooling: GLP is in the lineage of formative assessment; AI detection is in the lineage of plagiarism detection. The former measures learning; the latter classifies artifacts. Conflating them is the field's confusion the appendix should resolve.

---

## §I. Implementation guidance — clickstream measurability

`[from Ch 5 notes §F; appendix should retain at reference depth]`

The minimum-viable measurement layer question — what can be measured from existing LMS clickstream alone — is the appendix's pragmatic close. The honest answer:

| Component | LMS-only approximation feasibility | Additional instrumentation required |
|---|---|---|
| Y1 Temporal engagement | Page-level only (loses sub-page granularity) | Sub-section event logging |
| Y2 Error trajectory | Requires misconception model (LMS does not have) | Misconception model from curriculum design layer (Ch 8) |
| Y3 Cross-context transfer | Requires cross-context items (LMS does not have) | Multi-framing Book Library content (Ch 4 Layer 2) |
| Y4 Uncertainty calibration | Not feasible (no pre-response confidence in LMS) | Confidence-rating interaction design |
| Y5 Social knowledge texture | Not feasible (no chat-style interaction in LMS) | Ask AI mode + NLP classifier (Ch 6) |
| Y6 Retrieval decay | Not feasible (LMS schedule is professor-set) | FSRS-scheduled retest (Quiz Me mode, Ch 6) |
| Y7 Scaffolding response | Not feasible (no hint interaction in LMS) | Hint-not-answer interaction (Ask AI, Ch 6) |

**One component (Y1) is partially recoverable from LMS clickstream alone. Six components require additional instrumentation that does not exist in a general-purpose LMS.** This is the operational form of Ch 4's "bolt-on doesn't work" argument: the measurement layer cannot be added to Canvas as an analytics overlay; the interactions that produce the signals have to be the interactions the learner is using. The appendix should state this conclusion at the same depth as Ch 4 does, but operationalized to the component level.

### I.1 The deployment path

For a platform without the full Medhavy stack, the appendix can identify a sequence of investments that produces the framework incrementally:

1. **Sub-section logging.** Cheapest single investment. Produces Y1 in clean form. Useful as a confound check against more sophisticated components.
2. **Confidence rating before response.** Adds Y4. Single interaction-design change. Produces calibration data.
3. **Hint-not-answer interaction.** Adds Y7. Requires the hint authoring (or LLM-generated hints with quality control). The hint itself is also a learning mechanism.
4. **FSRS-style retest scheduling.** Adds Y6. Requires the platform to retest on its schedule, which requires the curriculum-design commitment that the retest is part of the course.
5. **Misconception model.** Adds Y2. Requires the curriculum-design layer; cannot be added downstream.
6. **Multi-framing content.** Adds Y3. Requires the Book Library investment.
7. **Chat-style interaction + NLP classifier.** Adds Y5. The most experimental investment.

The order is rough; (3) and (4) are interchangeable depending on the platform's existing interactions. The bottom line: each component costs something specific, and the order matters less than the fact that each costs something. There is no free ride to the seven-component ensemble.

### I.2 What this implies for institutions

An institution considering adopting GLP-style measurement on its existing LMS faces a structural decision: invest in the seven instrumentation changes above, or accept that the measurement they can do is Y1-only-in-partial-form. The appendix should land this without polemic: the framework is what it is, the instrumentation is what it costs, and the platform integration the book has argued for is the cheapest path to the full ensemble.

---

## §J. Cross-references to existing pantry

The appendix depends on the following pantry material. Cite by exact filename:

- `05-the-measurement-layer_notes.md` — **primary source.** Sections A (decoupling), B (neurobiology), C (Y1–Y7 specification), D (ensemble architecture), E (fluency trap), F (minimum viable measurement layer), G (arms race), H (worked example) are the load-bearing reconstruction this appendix builds on. Every §B–§I in these notes is derived from `05-the-measurement-layer_notes.md`.

- `02-why-does-solving-it-require-a-platform.md` — the plain-English seven-signal sketch. Useful for the appendix's introductory framing and for verifying that the reconstruction matches the original chapter's framing.

- `04-what-makes-this-different.md` — the ensemble architecture sketch (Layer 1 component models → Layer 2 tier-conditioned combination → Layer 3 meta-model). Origin of the three-layer architecture §D reconstructs.

- `11-what-the-platform-does-not-know-yet_notes.md` — for the validation-gap framing (§E). The eight open questions there include the GLP-validation gap; the appendix's §E.5 honest disclosure is the appendix-depth version of the chapter's §2 gap analysis.

- `Causal Graphs_ A Testable Architecture for Pedagogical Research Using AI-Mediated Instruction.txt` — the Hattie-DAG paper. Useful for the SUTVA-by-design claim if the appendix wants to argue that within-learner randomization makes GLP validation practically tractable. **Not the GLP preprint.** Do not cite this txt file as if it were.

- `_lib_how-to-measure-anything_-finding-the-value-of-_intangibles_-in-business.md` — Hubbard. Useful for the framing in §D and §E of measurement as Bayesian uncertainty reduction. Hubbard's clarification chain ("if it matters, it can be observed; if it can be observed, it can be measured") supports the framework's bet that genuine learning is observable through behavioral consequences.

- `ask-ai-research.md` — for Bastani et al. 2025 *PNAS* on the hint-not-answer guardrail finding. Y7 (scaffolding response curve) is the appendix's operationalization of the Bastani guardrail insight.

- `quiz-me-research.md` — for FSRS, Cepeda 2006 / 2008 spacing meta-analyses, Bjork & Bjork 1992 retrieval/storage duality. Y6 (decay signature) leans on this directly.

- `concept-sequencing-research.md` — for BKT/DKT and knowledge-component theory underlying Y2 (error trajectory).

- `domain-specific-instruction-research.md` — for Sadler 2013 misconception-identification and PCK. Cited in §H.3 for the formative-assessment lineage and in §B.2 for the misconception-model requirement.

---

## §K. Citations introduced or anchored by this note

Anderson, L. W., and D. R. Krathwohl, eds. 2001. *A Taxonomy for Learning, Teaching, and Assessing: A Revision of Bloom's Taxonomy of Educational Objectives.* Allyn & Bacon.

Atkinson, R. K., A. Renkl, and M. M. Merrill. 2003. "Transitioning From Studying Examples to Solving Problems: Effects of Self-Explanation Prompts and Fading Worked-Out Steps." *Journal of Educational Psychology* 95(4): 774–783.

Bailey, C. H., E. R. Kandel, and K. M. Harris. 2015. "Structural Components of Synaptic Plasticity and Memory Consolidation." *Cold Spring Harbor Perspectives in Biology* 7(7): a021758.

Bastani, H., O. Bastani, A. Sungu, H. Ge, Ö. Kabakcı, and R. Mariman. 2025. "Generative AI Can Harm Learning." *PNAS* 122(26): e2422633122. DOI: 10.1073/pnas.2422633122.

Bjork, R. A., and E. L. Bjork. 1992. "A New Theory of Disuse and an Old Theory of Stimulus Fluctuation." In *From Learning Processes to Cognitive Processes: Essays in Honor of William K. Estes*, edited by A. F. Healy, S. M. Kosslyn, and R. M. Shiffrin, 2:35–67. Erlbaum.

Black, P., and D. Wiliam. 1998. "Inside the Black Box: Raising Standards Through Classroom Assessment." *Phi Delta Kappan* 80(2): 139–148. ([Sage reprint, 2010](https://journals.sagepub.com/doi/10.1177/003172171009200119))

Bloom, B. S., ed. 1956. *Taxonomy of Educational Objectives: The Classification of Educational Goals, Handbook I: Cognitive Domain.* David McKay.

Cepeda, N. J., H. Pashler, E. Vul, J. T. Wixted, and D. Rohrer. 2006. "Distributed Practice in Verbal Recall Tasks: A Review and Quantitative Synthesis." *Psychological Bulletin* 132(3): 354–380.

Cepeda, N. J., E. Vul, D. Rohrer, J. T. Wixted, and H. Pashler. 2008. "Spacing Effects in Learning: A Temporal Ridgeline of Optimal Retention." *Psychological Science* 19(11): 1095–1102.

Corbett, A. T., and J. R. Anderson. 1995. "Knowledge Tracing: Modeling the Acquisition of Procedural Knowledge." *User Modeling and User-Adapted Interaction* 4(4): 253–278.

Cowansage, K. K., J. E. LeDoux, and M. H. Monfils. 2010. "Brain-Derived Neurotrophic Factor: A Dynamic Gatekeeper of Neural Plasticity." *Current Molecular Pharmacology* 3(1): 12–29. PMID: 20030624.

Dietterich, T. G. 2000. "Ensemble Methods in Machine Learning." In *Multiple Classifier Systems* (Lecture Notes in Computer Science 1857), 1–15. Springer.

Dunning, D., C. Heath, and J. M. Suls. 2004. "Flawed Self-Assessment: Implications for Health, Education, and the Workplace." *Psychological Science in the Public Interest* 5(3): 69–106.

Holtmaat, A., and K. Svoboda. 2009. "Experience-Dependent Structural Synaptic Plasticity in the Mammalian Brain." *Nature Reviews Neuroscience* 10(9): 647–658.

Hubbard, D. W. 2014 [3rd ed.]. *How to Measure Anything: Finding the Value of Intangibles in Business.* Wiley.

Koedinger, K. R., A. T. Corbett, and C. Perfetti. 2012. "The Knowledge-Learning-Instruction Framework: Bridging the Science-Practice Chasm to Enhance Robust Student Learning." *Cognitive Science* 36(5): 757–798.

Krishna, K., Y. Song, M. Karpinska, J. Wieting, and M. Iyyer. 2023. "Paraphrasing Evades Detectors of AI-Generated Text, but Retrieval Is an Effective Defense." *Advances in Neural Information Processing Systems* 36. ([arXiv:2303.13408](https://arxiv.org/abs/2303.13408))

Lave, J., and E. Wenger. 1991. *Situated Learning: Legitimate Peripheral Participation.* Cambridge University Press.

Liang, W., M. Yuksekgonul, Y. Mao, E. Wu, and J. Zou. 2023. "GPT Detectors Are Biased Against Non-Native English Writers." *Patterns* 4(7): 100779. ([Cell Press](https://www.cell.com/patterns/fulltext/S2666-3899(23)00130-7); [arXiv:2304.02819](https://arxiv.org/abs/2304.02819))

Lu, Y., K. Christian, and B. Lu. 2008. "BDNF: A Key Regulator for Protein Synthesis-Dependent LTP and Long-Term Memory?" *Nature Reviews Neuroscience* 9(6): 339–346.

Mehan, H. 1979. *Learning Lessons: Social Organization in the Classroom.* Harvard University Press.

Morris, C. D., J. D. Bransford, and J. J. Franks. 1977. "Levels of Processing Versus Transfer Appropriate Processing." *Journal of Verbal Learning and Verbal Behavior* 16(5): 519–533.

Nelson, T. O., and L. Narens. 1990. "Metamemory: A Theoretical Framework and New Findings." In *The Psychology of Learning and Motivation*, edited by G. H. Bower, 26:125–173. Academic Press.

OpenAI. 2023. "New AI Classifier for Indicating AI-Written Text." (Released January 2023; discontinued July 2023.) [Archive of release note](https://web.archive.org/web/20230724072139/https://openai.com/blog/new-ai-classifier-for-indicating-ai-written-text).

Pea, R. D. 2004. "The Social and Technological Dimensions of Scaffolding and Related Theoretical Concepts for Learning, Education, and Human Activity." *Journal of the Learning Sciences* 13(3): 423–451.

Sadasivan, V. S., A. Kumar, S. Balasubramanian, W. Wang, and S. Feizi. 2023. "Can AI-Generated Text Be Reliably Detected?" Preprint, v4 revised January 17, 2025. [arXiv:2303.11156](https://arxiv.org/abs/2303.11156)

Sadler, D. R. 1989. "Formative Assessment and the Design of Instructional Systems." *Instructional Science* 18(2): 119–144.

Schultz, W., P. Dayan, and P. R. Montague. 1997. "A Neural Substrate of Prediction and Reward." *Science* 275(5306): 1593–1599. DOI: 10.1126/science.275.5306.1593.

Selwyn, N. 2022. "The Future of AI and Education: Some Cautionary Notes." *European Journal of Education* 57(4): 620–631.

Sweller, J. 1988. "Cognitive Load During Problem Solving: Effects on Learning." *Cognitive Science* 12(2): 257–285.

van der Laan, M. J., E. C. Polley, and A. E. Hubbard. 2007. "Super Learner." *Statistical Applications in Genetics and Molecular Biology* 6(1): Article 25.

van Merriënboer, J. J. G., and J. Sweller. 2005. "Cognitive Load Theory and Complex Learning: Recent Developments and Future Directions." *Educational Psychology Review* 17(2): 147–177.

Weber-Wulff, D., A. Anohina-Naumeca, S. Bjelobaba, T. Foltýnek, J. Guerrero-Dib, O. Popoola, P. Šigut, and L. Waddington. 2023. "Testing of Detection Tools for AI-Generated Text." *International Journal for Educational Integrity* 19(1): 26. `[verify exact title and pages]`

Wells, G. 1999. *Dialogic Inquiry: Towards a Sociocultural Practice and Theory of Education.* Cambridge University Press.

Yang, G., F. Pan, and W.-B. Gan. 2009. "Stably Maintained Dendritic Spines Are Associated with Lifelong Memories." *Nature* 462(7275): 920–924. DOI: 10.1038/nature08577.

---

## §L. Three top flags for author attention

1. **The preprint blocker is the headline issue.** Appendix C cannot be drafted to canonical depth without either (i) the GLP preprint or (ii) the author's review and approval of the reconstruction in §B–§F as canonical. The §G resolution path lays out the three options. The research subagent's recommendation is Option B (approve the reconstruction, ship the appendix as the framework's first formal published statement) — but the decision is the author's. Until the decision is made, the appendix is in a holding pattern.

2. **The tier calibration table (§F) is the thinnest part of the reconstruction.** No pantry source explicitly enumerates the "seven cognitive tiers, primary friction signal per tier" the TIKTOC names. The Bloom-adjacent tier scheme in §F.1 is plausible but speculative. If the preprint specifies a different scheme — particularly if it does not align with Bloom — the §F reconstruction is the section most likely to require wholesale replacement. Recommend the author confirm or supply the tier scheme before the appendix is drafted.

3. **The validation methodology (§E) is design specification, not completed validation.** No published RCT exists. Chapter 11 confirms this in §2.1. The appendix's §E.5 honest disclosure must remain visible — not buried in a footnote. The information-gain test (§E.3) is the framework's falsifiability commitment; if the appendix promises it, the platform owes a published result. This is the highest-stakes commitment in the appendix and should be authored carefully.

---

*End of appendix research notes. ~5,800 words. Status: reconstructed from existing pantry due to preprint absence. Resolution path for the author flagged in §G. Ready for appendix drafting once the author chooses Option A, B, or C in §G.*
