# Pantry Index — Medhavy: How to Build an Intelligent Textbook

Last updated: 2026-05-17 (revised — adds Appendix A–E research notes)

Scratch storage for research notes ahead of chapter drafting. Nothing here compiles into the book. Move material into `chapters/` when ready.

This pantry serves the 12-chapter TIKTOC v1.0 chapter list plus five appendices. Chapter notes follow the standard 7-section gatherer format (Chapter summary / A. Conceptual foundations / B. Domain examples / C. Connections / D. Field state / E. Teaching considerations / F. Library files / G. Gaps and flags).

**Total research notes produced:** 17 files (12 chapters + 5 appendices), ~97,440 words.

---

## Research notes (generated 2026-05-17 — 12 chapters, ~71,740 words)

### Act One — The Right Question (Ch 1–3)

| File | Chapter | Words | Description |
|------|---------|------:|-------------|
| `01-what-is-an-intelligent-textbook_notes.md` | Ch 1 — What Is an Intelligent Textbook? | 6,732 | IDK-IDK Khanmigo incident; MIT OCW enrollment data; no-AI vs all-AI failure modes; four-layer architecture sketch; "the platform is opinionated" |
| `02-when-anki-is-enough_notes.md` | Ch 2 — When Anki Is Enough | 6,700 | Priya case; complexity threshold test (three questions); the three conditions that earn the full architecture; cross-references Homes of Hope +1 book |
| `03-the-evidence-base_notes.md` | Ch 3 — The Evidence Base | 7,848 | Butter Knife Fallacy; PISA 49-point (not 66) figure verified; Horvath audit; Khan rebuttal; Bastani PNAS 2025 fully verified citation; ITS / spaced repetition / CBL / generative-assignment evidence consolidated |

### Act Two — The Architecture (Ch 4–10)

| File | Chapter | Words | Description |
|------|---------|------:|-------------|
| `04-the-four-layers_notes.md` | Ch 4 — The Four Layers | 4,868 | Bolt-on failure; seven signals requiring live instrumentation; Book Library / Tic TOC / Adaptive Engine / Measurement integration |
| `05-the-measurement-layer_notes.md` | Ch 5 — The Measurement Layer (**LOAD-BEARING**) | 6,975 | Decoupling problem; biological substrate of friction; seven GLP components Y1–Y7 reconstructed from chapter source files (preprint missing — see Flag #3); fluency trap; arms-race problem; minimum viable measurement layer |
| `06-the-four-modes_notes.md` | Ch 6 — The Four Modes | 5,306 | Hammer-problem-at-mode-level; Ask AI (context-anchoring); Case Study (Thistlethwaite, pre-written faculty-reviewed); Quiz Me (FSRS, due-today counter); Glimmer (backwards-faded scaffolding, novice anxiety failure); phase gates as measurement decisions |
| `07-the-adaptive-engine_notes.md` | Ch 7 — The Adaptive Engine (**LOAD-BEARING**) | 6,245 | Casino opening; Robbins 1952 vs Thompson 1933 priority; epsilon-greedy / UCB1 / Thompson sampling; within-learner vs cross-learner generalization; engagement trap; reward function specification |
| `08-the-curriculum-design-layer_notes.md` | Ch 8 — The Curriculum Design Layer | 5,640 | "Suggest 15 chapters" failure; backward design (Wiggins & McTighe); concept map requirements; three curriculum design failure modes; Tic TOC as the meta-instrument |
| `09-the-content-layer_notes.md` | Ch 9 — The Content Layer | 6,330 | Domain-specificity finding (Sadler 2013 PCK); Level-1/2/3 stratification; cost-collapse asymmetry; AI-generation policy; faculty review gate; Sesame Street standard |
| `10-the-economics_notes.md` | Ch 10 — The Economics of Intelligent Textbooks | 4,592 | Sesame Street as floor + AI collapse below; binding-cost shift (Sadler 2013); minimum viable audience math; homeschool/microschool market; five things economics do NOT change |

### Act Three — The Map (Ch 11–12)

| File | Chapter | Words | Description |
|------|---------|------:|-------------|
| `11-what-the-platform-does-not-know-yet_notes.md` | Ch 11 — What the Platform Does Not Know Yet | 5,496 | Montaigne *Essais* register; the eight open questions enumerated, each with adjacent evidence / direct evidence gap / RCT design; FERPA + COPPA 2026 status; switching behavior as signal |
| `12-the-design-conversation_notes.md` | Ch 12 — The Design Conversation | 5,008 | Book-as-Tic-TOC meta-move; tool/thinking labor separation; platform-vs-instrument distinction; six design-conversation moves; Gru "80/20" framing (no single canonical source — Osmani / Dasika / Vance / Brockman distributed attribution) |

### Appendices A–E (generated 2026-05-17, second-pass research, ~25,700 words)

| File | Appendix | Words | Description |
|------|----------|------:|-------------|
| `A-medhavy-lexicon_notes.md` | App A — The Medhavy Lexicon | 5,200 | 13 platform-specific terms (IDK-IDK, four layers, four modes, seven signals, phase gates, within-learner bandit, GLP reward, ambient infrastructure, conductor, fluency trap, cost-collapse asymmetry, due-today counter, GLP itself) with definitions + first-appearance chapter map; NanoLex / Wikipedia Pipeline status (Pipeline B paper not yet published — see Flag #17) |
| `B-causal-knowledge-graph_notes.md` | App B — Causal Knowledge Graph | 6,000 | Hattie *Visible Learning* MetaX current state; Intervention / Diagnostic / Context taxonomy; DAG framework; Adherence Classifier architecture **([VERIFY URGENT] no public-facing source — see Flag #18)**; connection to Ch 7 reward-function priors; causal discovery vs expert elicitation debate; critique-citation [verify] flags (Wecker, Simpson, Snook, Topphol) |
| `C-glp-technical-specification_notes.md` | App C — GLP Technical Specification | 5,800 | Seven GLP components reconstructed with per-section provenance tags `[preprint-anchored]` / `[reconstructed from Ch 5 notes]` / `[design specification — pending validation]`; three-layer ensemble architecture; tier calibration table (thinnest reconstruction — see Flag #19); validation methodology (design spec, not completed validation); arms-race problem anchored to Liang 2023, Sadasivan 2023/2025, OpenAI Classifier discontinuation; preprint blocker resolution path (provide / approve reconstruction / defer) |
| `D-contextual-bandits_notes.md` | App D — Contextual Bandits | 4,700 | Contextual bandit formulation; context features; reward signal; exploration strategy (Thompson sampling recommended); update mechanics; cold-start strategies; **MVAL is misnamed in TIKTOC — actually "Minimum Viable Analytical Log" not "Medhavy Value"** (see Flag #20); Contextual Bandits.txt does not exist in pantry (see Flag #21) |
| `E-medhavi-hub-architecture_notes.md` | App E — Medhavi Hub Architecture | 4,000 | Tech stack (Next.js, Clerk, Supabase, AWS S3, PostHog); Clerk + Supabase native JWT integration (April 2025 pattern, not the deprecated JWT-template pattern); dynamic CORS in Next.js 14 App Router; service-role → secret-key model with auto-revocation; database schema; concept map editor workflow; **neither API.md nor ARCHITECTURE.md exists in pantry — reconstruction is pattern-derived, not document-derived** (see Flag #22) |

---

## Existing thematic research notes (pre-existing — heavy use across chapters)

| File | Primary chapters | Description |
|------|------------------|-------------|
| `ask-ai-research.md` | Ch 1, 3, 6 | ITS and generative-AI chatbot effectiveness, Bastani PNAS 2025, guardrail design |
| `case-study-research.md` | Ch 3, 6 | CBL literature, Thistlethwaite 2012, pre-written vs on-demand cases |
| `quiz-me-research.md` | Ch 2, 3, 6 | Retrieval practice, spaced repetition, FSRS, SM-2, Cepeda 2006/2008 |
| `quiz-me-habit-research.md` | Ch 2, 6 | Anki habit system, due-today counter, Zeigarnik closure, Fogg/Eyal/Wood |
| `glimmer-research.md` | Ch 3, 6 | Generative learning, ill-structured problems, Jonassen 1997, Fiorella & Mayer 2016 |
| `glimmer-displacement-research.md` | Ch 3, 6 | AI displacement, studio-critique, scaffolding fading, Renkl, van Merriënboer |
| `concept-sequencing-research.md` | Ch 7, 8 | Frequency sequencing, BKT, DKT, prerequisite chaining, importance weighting |
| `domain-specific-instruction-research.md` | Ch 3, 9 | PCK, situated learning, Level-3 specificity, Sadler 2013 |
| `educational-media-economics-research.md` | Ch 2, 3, 9, 10 | Sesame Street, Mayer CTML, cost-collapse asymmetry, minimum viable audience, Sunstein burden-of-proof inversion |

---

## Medhavy internal docs (.txt and supplementary research)

| File | Primary chapters | Description |
|------|------------------|-------------|
| `Lexicon.txt` | Ch 12, App A | Medhavy vocabulary/lexicon features |
| `MVAL.txt` | Ch 7, App D | Medhavy learning value features |
| `PEDAGOGY ARCHITECTURE.txt` | Ch 6, 8 | Medhavy pedagogical architecture (modes + curriculum) |
| `Causal Graphs_ A Testable Architecture for Pedagogical Research Using AI-Mediated Instruction.txt` | Ch 4, 5, App B | Hattie-DAG framework; SUTVA-by-design; **NOT the GLP preprint** (see Flag #3) |
| `AI Chatbots in Education Research.txt` | Ch 1, 6 | Supplementary chatbot research |
| `AI and the Nature of Interestingness.txt` | Ch 5, 6 | Supplementary on what makes content engaging without sacrificing learning |
| `Case-Based Learning Effectiveness Research.txt` | Ch 3, 6 | Supplementary CBL synthesis |
| `Generative Assignments, AI, and Education.txt` | Ch 3, 6 | Supplementary generative-assignment research |
| `Sequencing and Prioritizing Learning Concepts.txt` | Ch 7, 8 | Supplementary on concept sequencing |
| `medhavy-1.5-feature-roadmap-complete.md` | Ch 11, 12 | Current platform features (epistemic inventory for Ch 11) |
| `medhavy-1.5-feature-roadmap-complete (1).md` | — | **DUPLICATE** of `medhavy-1.5-feature-roadmap-complete.md` — recommend deleting one |

---

## Library files (copied from shared MD library 2026-05-17)

| File | Relevant to | Notes |
|------|-------------|-------|
| `_lib_edtech-.md` | Ch 1, 3 | General EdTech context book |
| `_lib_co-intelligence__living_and_working_with_ai.md` | Ch 1, 6 | Mollick *Co-Intelligence* — human + AI framing |
| `_lib_neu_global_collaboration_chatbot.md` | Ch 1, 6 | NEU chatbot deployment context |
| `_lib_teaching-for-deeper-learning_-tools-to-engage-students-in-meaning-making.md` | Ch 4, 6, 8 | McTighe & Silver — backward design and meaning-making |
| `_lib_reinforcement_learning_an_introduction.md` | Ch 7, App D | Sutton & Barto — bandits canonical reference |
| `_lib_everything-is-predictable_-how-bayesian-statistics-explain-our-world.md` | Ch 7 | Bayesian framing for bandit reward updating |
| `_lib_applied-causal-inference-powered-by-ml-and-ai.md` | App B | Causal DAGs for the Hattie-DAG appendix |
| `_lib_the_art_of_statistics__how_to_learn_from_data.md` | Ch 3, 11 | Spiegelhalter — evidence reading discipline |
| `_lib_case_study_prompts.md` | Ch 6 | Practical CBL prompt templates |
| `_lib_humanitarians_ai_course_template.md` | Ch 2 | Priya / Homes of Hope volunteer context |
| `_lib_how-to-measure-anything_-finding-the-value-of-_intangibles_-in-business.md` | Ch 5 | Hubbard — measurement-of-intangibles framing for GLP |

---

## Chapter source files (pre-TIKTOC v1.0 drafts — not research notes)

These are older drafts predating TIKTOC v1.0's 12-chapter scheme. They are **source material**, not research notes. Useful for voice calibration and for reconstructing the GLP framework (see Flag #3).

| File | Notes |
|------|-------|
| `00-frontmatter.md` | Old frontmatter draft |
| `00-introduction.md` | Old introduction draft |
| `01-what-is-medhavy.md` | Predecessor of Ch 1 (different framing) |
| `02-why-does-solving-it-require-a-platform.md` | Predecessor of Ch 4; contains plain-English seven-component sketch (GLP source) |
| `03-chapter-02.md` | Stub |
| `04-what-makes-this-different.md` | Contains seven-component GLP listing and ensemble-architecture sketch |
| `05_what_doesnt_it_know_yet.md` | Predecessor of Ch 11 |
| `06-medhavy-conducting-ai.md` | Predecessor of Ch 12 |
| `99-back-matter.md` | Old back matter |

---

## Top flags requiring author attention before drafting

1. **TIKTOC PISA figure is wrong.** TIKTOC §Ch 3 hook cites "6+ hours / 66-point drop." The verified OECD PISA 2022 finding is **49 points** at the 5–7 hours vs. ≤1 hour comparison (OECD PISA 2022 Volume I). The 66 number does not appear in primary OECD sources. The Trust the Teacher Ch 1 fact-check caught the same problem. **Action:** update TIKTOC, use 49 points / 5–7 hours in Ch 3 draft.

2. **Bastani PNAS 2025 citation now locked.** Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., & Mariman, R. (2025). *PNAS* 122(26), e2422633122. DOI 10.1073/pnas.2422633122. The headline figure is **17 percentage points lower** (NOT "17% lower") on the post-practice exam for the GPT Base group vs. the no-AI control. Used canonically across all chapter notes. **Action:** propagate the canonical form to every chapter draft.

3. **The GLP preprint as a standalone document does not exist in this pantry.** The "Causal Graphs..." txt file is the Hattie-DAG / SUTVA-by-design paper, not the GLP preprint. The seven Y1–Y7 components are reconstructed in `05-the-measurement-layer_notes.md` §A from (a) the plain-English description in `02-why-does-solving-it-require-a-platform.md` and (b) the seven-component listing with ensemble-architecture sketch in `04-what-makes-this-different.md`. **Appendix C is blocked on this preprint.** Recommend the author either (i) provide the preprint to pantry/, or (ii) approve the reconstruction in the Ch 5 notes as the canonical version.

4. **Khanmigo IDK-IDK quote — primary venue [verify].** The Kristen DiCerbo quote ("we see more 'IDK IDK,' more passive kinds of interaction than we would like") is widely reported (Dan Meyer Substack, itutorsoft, CompleteAI Training) but the primary venue (likely EdSurge or Education Next 2024–2025 interview) needs confirmation before the Ch 1 draft cites it directly. The directional Khanmigo failure is unambiguous; the precise venue for the quote is the open item.

5. **Neurobiology citations need verification.** Schultz 1997 *Science* 275:5306 cross-check needed against multiple Schultz papers; Cowansage 2010 BDNF may be less canonical than Lu, Christian & Lu 2008 *Nat Rev Neurosci*; Yang/Pan/Gan 2009 *Nature* 462 is a mouse motor-learning study and the extrapolation to human declarative learning should be flagged, not asserted.

6. **FSRS lacks a peer-reviewed academic citation.** The "Quiz Me uses an evidence-based algorithm" claim rests on internal benchmark data (~20–30% fewer reviews, ±5.3% retention error), not on RCT learning-outcome comparison. Ch 6 should cite open-spaced-repetition project documentation as primary and flag as open question.

7. **Robert C. Gray bandit explanation cannot be verified.** TIKTOC §Ch 7 asks the chapter writer to reference Gray's slot-machines-first style, but no Robert C. Gray bandit reference exists in pantry or in standard web/academic returns. **Recommendation:** adopt the style (slot machines first, vocabulary second — Sutton & Barto Ch 2 already exemplifies) without naming Gray, pending confirmation from the author.

8. **Robbins 1952 vs. Thompson 1933 priority.** TIKTOC names Robbins 1952 as the bandit formalization. Robbins is the standard sequential-experiments citation, but Thompson 1933 (*Biometrika* 25: 285–294) introduced the Bernoulli bandit two decades earlier. Ch 7 draft should cite both; using only Robbins is slightly misleading.

9. **Sesame Street $5/child/year temporal anchoring.** The figure characterizes current fully-amortized operations, not Cooney's 1969 launch costs. Ch 9 and Ch 10 must not slip into "Cooney's 1969 program cost $5/child/year." Cooney feasibility-study date variously cited as 1966 / 1967 / 1968 in different sources.

10. **Gru "80% thinking / 20% coding" framing has no single canonical source.** Distributed across Osmani's "80% Problem in Agentic Coding" Substack, Dasika's blog, Vance's Medium piece, and Brockman quotes. Ch 12 note §7.1 flags this. Osmani is the safest single citation if one is required.

11. **AI content production cost figures move monthly.** Ch 10 §2.1 numbers ($0.50/sec Veo, $20–$300/mo Synthesia, etc.) need draft-time re-verification. Peer-reviewed cost-to-equivalent-quality benchmarks for educational AI educational video do not exist.

12. **Ch 12 worked example labeling is contingent on Medhavy-instrument deployment state.** If the instrument is not built at draft time, the worked example must be labeled "design specification" not "product demo" — flagged in Ch 12 note §10. This is TIKTOC open question #1.

13. **MIT OCW "one-third of incoming freshmen" figure.** MIT-internal self-report (D'Oliveira & Lerman, MIT Faculty Newsletter / MIT OCW 2011 Evaluation Summary). Directional claim uncontested; specific figure carries institutional-self-report caveat. Ch 1 §G.1 flags.

14. **Coordination flag between Ch 9 and Ch 10.** `educational-media-economics-research.md` — Ch 9 uses §1 (Sesame Street intro) and §8 (Sunstein); Ch 10 should not repeat these. Detailed in Ch 9 notes §K.

15. **Appendices A–E researched in second pass (2026-05-17 evening).** All five appendix notes files now exist. Three carry primary-source-mismatch flags against TIKTOC (Flags #21, #22) and two carry validation-blocker flags (Flags #18, #19, #3). See Flags #17–#22 below for the appendix-specific issues.

16. **Duplicate file in pantry.** `medhavy-1.5-feature-roadmap-complete (1).md` is identical to `medhavy-1.5-feature-roadmap-complete.md`. Recommend deleting the parenthesized copy.

### Appendix-specific flags (second pass)

17. **App A — NanoLex Pipeline B paper status.** TIKTOC §Appendix A names *"Automated Lexical Entry Generation for Nanomedicine"* as the publishable Pipeline B output. No published or preprint version surfaced on 2026-05-17. The pipeline is documented internally in `Lexicon.txt` v0.2 (March 2026) with Pipeline A blocked on Dhruv's MDX component contract decision and Pipeline B blocked on Prof. Brown's system prompt review. Treat as forthcoming, not published.

18. **App B — Adherence Classifier public-facing status `[VERIFY URGENT]`.** No public paper, repository, or project page found for "Adherence Classifier" in connection with Medhavy, Nik Bear Brown, or Satwik Reddy Sripathi. The architecture is reconstructed in the App B notes from the Causal Graphs draft §4.3 plus contemporary LLM-judge fidelity-measurement literature. The appendix should either cite a Sripathi project the author can provide, or describe the architecture as "currently being developed" without claiming deployed validation.

19. **App C — Tier calibration table is thinnest reconstruction.** No pantry source enumerates the "seven cognitive tiers, primary friction signal per tier" the TIKTOC names. The Bloom-adjacent tier scheme in the App C notes §F is plausible-but-speculative. If the GLP preprint specifies a different scheme, §F requires wholesale replacement. Author confirmation needed before App C drafting. (Compounds Flag #3 — the same preprint blocker.)

20. **App D — MVAL is misnamed in TIKTOC.** TIKTOC §App D says *"MVAL (Medhavy Value) — the platform's internal value metric."* The actual `MVAL.txt` in pantry is the **Minimum Viable Analytical Log** protocol — a six-field discipline (WHAT/WHY/HOW/ENVIRONMENT/RESULTS/QUESTIONS) for research logging. App D notes reframe MVAL as the *audit discipline* that produces the data the bandit's offline evaluation requires, not as a value metric. **Action:** correct TIKTOC §App D description, or rename if a "Medhavy Value" metric exists separately.

21. **App D — `Contextual Bandits.txt` does not exist in pantry.** TIKTOC §App D names it as a primary source; the file is absent. App D notes reconstruct from `07-the-adaptive-engine_notes.md` plus Sutton & Barto. Either provide the txt file or remove the TIKTOC reference.

22. **App E — neither `API.md` nor `ARCHITECTURE.md` exists in pantry.** TIKTOC §App E (and Ch 4, Ch 12 source lists) name both; both are absent. App E reconstruction is **pattern-derived** (canonical 2025–2026 Clerk + Supabase + Next.js + S3 + PostHog stack), not document-derived from deployed code. Database schema and endpoint signatures should be cross-checked against actual deployed code before publication. Either provide the two docs to pantry/ or treat the App E notes as a design specification rather than a documentation reference.

---

*Next step: run the Chapter Writer prompt against this book directory. The pantry contains all gathered material. No chapter prose has been written for the TIKTOC v1.0 schema yet.*
