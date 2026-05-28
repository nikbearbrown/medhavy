# Chapter 10 — The Content Layer


## TL;DR

- Production costs fell three orders of magnitude.
- The chapter moves through Why domain specificity is not a nice-to-have, What collapsed, what did not, The three-tier policy, The benchmark, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

*Production costs fell three orders of magnitude. Design costs did not. The asymmetry is the point.*

---

Here is the most natural mistake a teacher makes when building a platform.

She starts with the content.

She has twenty years of pharmacology lectures. She has a copy of Goodman and Gilman with three thousand marginal notes. She has case files, slide decks, annotated papers. She knows where students get confused — she has watched it happen in the same places, with the same misconceptions, for two decades. Her instinct is to start with what she has, and her instinct is reasonable. It is what teaching looks like.

The instinct produces platforms that fail. Not because the content is bad. Because content that is not constrained by what the rest of the architecture needs becomes the platform's purpose instead of its substrate. The modes have no specifications to satisfy. The engine has no outcome statements to optimize against. The measurement layer has no probe items calibrated to the curriculum. The result is a sophisticated system optimized around producing content — which is like building an orchestra and forgetting to decide what music to play.

This chapter is the last architectural chapter on purpose. Everything that comes before it — the measurement layer, the modes, the engine, the curriculum design layer — specifies what the content has to do. The content layer's job is to satisfy those specifications. Not to define them. A teacher who arrives at this chapter having worked through the architecture arrives at it knowing exactly what each piece of content has to accomplish. A teacher who starts here produces a hammer-shaped platform.

That said, this chapter is where the most important economic change of the last five years lands. AI generation has lowered production costs by roughly one to three orders of magnitude — for some things. Not for all things. The asymmetry between what collapsed and what did not is the central argument. Get the asymmetry right and you can now build domain-specific content at multi-domain scale that was simply unaffordable before. Ignore it and you produce more content faster while lowering the quality of the part of content production that was never a bottleneck.

---

## Why domain specificity is not a nice-to-have

In 1986 Lee Shulman introduced the term *pedagogical content knowledge* — the knowledge of how students learn a specific subject, not just the subject itself.[^1] The distinction matters because subject-matter knowledge and PCK predict student achievement independently, and PCK predicts it more strongly.

The cleanest demonstration is Sadler et al. 2013, a study of middle-school physical science teachers.[^2] Teachers were given a diagnostic test — not "what is the right answer to this physics question" but "which wrong answer will your students predictably give?" The teachers who could identify their students' misconceptions produced substantially larger learning gains than teachers who could not, controlling for subject-matter knowledge itself. The diagnostic move — knowing what *learners in this domain* get wrong — is what carries the effect.

Hill, Rowan, and Ball 2005 produced the same finding in mathematics.[^3] Teachers' Mathematical Knowledge for Teaching, a PCK-aligned construct, predicted student achievement gains beyond what general teaching skill or subject content knowledge alone predicted.

Thirty years of consistent empirical record. *Knowing the content* is necessary but not sufficient. The diagnostic move that depends on knowing what this population of students gets wrong, in this domain, at this level, is what makes instruction effective.

Now translate this directly into content production.

There are three levels of domain specificity in instructional content. **Level 1** is generic: the principle is taught abstractly, with no domain-specific examples or scenarios. The theoretical case for Level 1 is maximum transfer. The empirical reality is motivational fragility — abstract instruction is hard to attend to, and the transfer benefit assumes a student who has already done the work of staying engaged with an abstraction, which is the exact work the abstraction makes harder.

**Level 2** is generic with a domain capstone: the bulk is abstract, with one domain-specific application at the end. Common in corporate L&D and many professional development courses. The capstone gives a concrete anchor; the bulk is still abstract. The transfer benefit is real but partial.

**Level 3** is domain-specific throughout, with the generic principles extracted and made visible across domain examples rather than introduced first and then illustrated. Level 3 captures the bulk of the transfer-appropriate processing benefit — the finding from Morris, Bransford, and Franks 1977 that cognitive operations at study and at test must overlap for transfer to occur.[^4] It also captures the situated learning benefit — Lave and Wenger's 1991 finding that knowledge is partly constituted by the activity and context in which it develops, and that decontextualized knowledge transfers poorly to authentic practice.[^5]

Level 3 costs more to produce. Published estimates from curriculum-variant production put the premium at roughly 1.5 to 2 times the Level 1 cost. For a multi-domain deployment — ten domains, each requiring separate variants — the total cost is approximately 15 to 20 times the Level 1 baseline per finished unit.

| Level | Structure | Evidence base | Theoretical claim | Empirical failure mode |
| --- | --- | --- | --- | --- |
| Level 1 (generic, abstract throughout, TAP and situated learning benefits absent, motivational fragility, 1× | The pattern becomes easy to misuse or overlook. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | The pattern becomes easy to misuse or overlook. |
| Level 2 (generic + domain capstone, TAP benefit only at capstone, partial transfer benefit, 1.2–1.5× | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | The pattern becomes easy to misuse or overlook. |
| Level 3 (domain-specific throughout, full TAP and situated learning benefits, most evidence-aligned, 1.5–2× per variant). Reader should see at a glance that Level 3 is the evidence-supported default and that the pre-AI cost is the main reason it has not been the standard. | It makes the underlying reasoning visible instead of implied. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | The pattern becomes easy to misuse or overlook. |

This is where the cost-collapse argument changes the calculation. But first, the asymmetry.

---

## What collapsed, what did not

Some content production costs have fallen by one to three orders of magnitude since 2023. Some have not moved. The asymmetry is not incidental — it is the structural fact that determines what the cost-collapse licenses and what it does not.

**What collapsed:**

Text generation. Marginal cost per 1,000 words for current LLMs: roughly $0.01 to $0.10. Professional educational technical writing at the same quality: roughly $100 to $1,000 per 1,000 words. Approximately three to four orders of magnitude.

AI video generation. Google Veo 2, OpenAI Sora, and Runway are all in the range of roughly $0.50 per second of generated video, or $30 per minute. Pre-AI narrated explanatory animation: $1,000 to $5,000 per minute at low-budget educational rates. Professional production: considerably more. Two to four orders of magnitude depending on the comparison.

Image generation. Per-image cost from current models: $0.001 to $0.10. Pre-AI illustration: $50 to $500. Three orders of magnitude.

Voice synthesis. Per-minute cost from ElevenLabs or OpenAI TTS: $0.01 to $0.30. Pre-AI professional voice talent: $5 to $50 per minute. Two to three orders of magnitude.

**What did not collapse:**

Expert review. A domain expert reviewing AI-generated content for accuracy, conceptual fidelity, appropriate scaffolding, and misconception coverage still takes 5 to 15 minutes per 500-word passage. The expert's hourly rate has not dropped because the underlying production became cheap. Cost essentially unchanged.

Curriculum design. The work of specifying outcomes, prerequisite graphs, mode flags, and assessment evidence is human-judgment-intensive and has not been automated. Cost largely unchanged.

Empirical validation. Running a controlled study on content effectiveness costs what it has always cost. The cost of producing content has dropped; the cost of knowing whether the content works has not.

Domain-expert authorship for high-stakes content. A practicing oncologist writing a clinical scenario from her case experience cannot be replaced by AI generation. The cost lives in the expertise that produces the scenario, not in the keyboard time that records it.

![Two-column bar chart comparing pre-AI vs](images/10-the-content-layer-fig-01.png)
*Figure 10.1 — Two-column bar chart comparing pre-AI vs*

The asymmetry has a consequence that needs to be stated plainly. The burden of proof required before deploying a piece of content should scale with the asymmetry of the failure modes the content can produce. Cass Sunstein's argument in *Laws of Fear* applies directly: the strong precautionary principle is incoherent because it forbids action and inaction simultaneously when both carry risk; the defensible frame is cost-benefit analysis under uncertainty, with extra precaution proportional to the irreversibility of the failure.[^6]

Failure mode A: AI content fails to help. Small loss, reversible. Burden of proof lowered.

Failure mode B: AI content actively misleads. Larger loss, harder to detect. The Bastani PNAS 2025 finding is the prototype: 17 percentage points lower on the post-practice exam for the unguarded GPT group versus the no-AI control.[^7] Burden of proof unchanged or higher.

Failure mode C: AI content develops a durable wrong model of the domain. Largest loss, hardest to reverse. The cognitive-offloading literature suggests this failure mode is real, though the content-layer evidence is thin.[^8] Burden of proof much higher.

The honest answer to *"does cost collapse lower the burden of proof?"* is: yes, asymmetrically. Lower for content where failure is small and reversible. Unchanged for content where failure is large or persistent. Higher for content where failure produces a durable wrong model that compounds.

| Example | Loss magnitude | Reversibility | Evidence threshold before deployment | Tier implication |
| --- | --- | --- | --- | --- |
| Failure Mode A (content fails to help | The pattern becomes easy to misuse or overlook. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| Failure Mode B (content actively misleads | The pattern becomes easy to misuse or overlook. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| Failure Mode C (content develops durable wrong model | The pattern becomes easy to misuse or overlook. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| columns: Example, Loss magnitude, Reversibility, Evidence threshold before deployment, Tier implication. The three rows show a clear escalation: small | reversible → lowered threshold → Tier 1 eligible | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| larger | harder to detect → unchanged threshold → Tier 2 minimum | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| durable | compounds → higher threshold → Tier 3 required. Reader should be able to use this table as a decision tool when assigning tier to a new content unit. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |

What the cost-collapse does open up — and this is the genuinely consequential change — is the Level 3 multi-domain case. The pre-AI arithmetic: Level 3 at 10 domain variants cost approximately 15 to 20 times the Level 1 baseline. The post-AI arithmetic: if AI generation drops per-unit production cost by 10 times for appropriate content, the Level 3 multi-domain cost can fall below the pre-AI Level 1 cost per unit of finished domain-variant content. The Sadler 2013 finding — domain-specific instruction, with misconception coverage, is what carries the PCK effect — is becoming economically tractable at multi-domain scale. That is the actual change worth getting excited about. Not *we can produce more content cheaply.* That, alone, is a faster route to mediocre. The change is *we can now afford domain-specific content for audiences that could never have justified the production cost before.*

The minimum viable audience calculation has inverted. At pre-AI production costs, the audience required to justify Level 3 production at any reasonable cost-per-learner was in the tens of thousands. At AI-generation costs, a single section of thirty students justifies production if the content produces any measurable learning gain at all. The question is no longer *does this audience justify the enormous additional cost?* It is *given that this costs essentially nothing to produce, when would we not produce it?* The answer is: when the content is in the high-burden-of-proof category and the deployment has not yet earned the burden.

---

## The three-tier policy

The asymmetry produces an operational policy. Three tiers and one non-optional gate.

**Tier 1 — AI-generated, light review.** Lexicon entries. Vocabulary definitions. First-draft explanatory text on well-established concepts where the AI is paraphrasing standard sources and the human reviewer is checking for errors and adding voice. Quiz Me items probing factual recall on items with clean answer keys. Reading comprehension passages used as Ask AI context, where the AI surfaces what the textbook says rather than adds new content.

**Tier 2 — AI-drafted, substantial expert review.** Explanatory text on concepts where misconception traps are present and the explanation has to anticipate the misconception. Case Study scenarios at moderate stakes. Worked examples in domains the expert can verify quickly. Glimmer prompts and rubrics for low-stakes generative work.

**Tier 3 — Domain-expert authorship required.** Clinical case scenarios. Worked examples in mathematics, physics, and engineering where the steps must be valid and the pedagogy appropriate to the learner's level. Glimmer rubrics that score generative work — a wrong rubric trains wrong behavior. Cross-context transfer scenarios, where the validity of the test depends on the validity of the scenario. Misconception-targeted content — the Sadler 2013 finding makes this central, and the misconceptions are domain- and learner-population-specific in ways that AI generation does not reliably reproduce.

The operational test for tier assignment: *if a content unit's failure could not be detected and corrected within one session, it requires Tier 3 authorship.* Reversibility within a single session is the threshold. Failures that are larger, slower, or harder to detect require human expertise upstream of the failure.

**The faculty review gate is not optional.** Every Tier 2 and Tier 3 unit passes through expert review before deployment. Tier 1 units are sampled — say, 10% — to catch systematic errors. The gate is a workflow stage, not a one-time event. Revised content is re-reviewed. Deployment data triggers re-review when measurement signals indicate something has gone wrong.

One failure mode needs to be named specifically. Generating Tier 2 or Tier 3 content with AI and relying on sampling-based review to catch errors sounds defensible. It is not. Sampling catches errors that are randomly distributed. AI generation produces systematically biased errors. The MedHallu benchmark documents this for medical content: hallucinations cluster around drug-drug interactions and rare conditions, the exact areas where the stakes are highest.[^9] The same generation mechanism predicts systematic clustering in other domains; the empirical work has not yet been done for most fields, but the structural inference holds. Random sampling misses systematic clustering with a probability that does not vanish with sample size. The discipline is: every Tier 2 and Tier 3 unit is reviewed. Cost collapse at production; cost retained at review. That is the asymmetry made operational.

---

## The benchmark

Here is the standard that AI-generated educational content is implicitly being compared against, whether platform builders know it or not.

Sesame Street has historically cost approximately $5 per child per year on a fully-amortized basis — Sesame Workshop's production budget across a global reach of roughly 156 million children annually.[^10] The effect size: Mares and Pan 2013, a meta-analysis of 24 studies across 15 countries, *d* ≈ 0.29 on cognitive outcomes.[^11] Moderate by Cohen's conventions; large by EdTech-intervention conventions. The long-run natural experiment: Kearney and Levine 2019 found that preschoolers in counties with strong Sesame Street reception were 14% less likely to be behind their expected grade level later in school, effects comparable in magnitude to Head Start at three to four orders of magnitude lower per-child cost.[^12]

Compute the benchmark: $5 per child per year at *d* = 0.29 is approximately $1.72 per 0.1 standard-deviation gain. Compare to high-dose tutoring: Nickow, Oreopoulos, and Quan's 2024 meta-analysis found *d* ≈ 0.37 at $2,000 to $3,500 per child, roughly $540 to $945 per 0.1 SD gain.[^13] Sesame Street is approximately 300 to 500 times more cost-effective per 0.1 standard deviation of gain than tutoring at scale.

![Log-scale bar chart of cost per 0](images/10-the-content-layer-fig-02.png)
*Figure 10.2 — Log-scale bar chart of cost per 0*

This is the floor. AI-generated content at production cost parity — roughly $5 per finished content unit — has achieved cost parity with Sesame Street. Whether it has achieved design quality parity is genuinely unknown, and that is the open question.

What Sesame Street built that AI content has not yet demonstrated:[^14] dual-channel alignment, where visual and verbal channels are coordinated frame by frame rather than assembled from separately generated streams; repetition with variation, where the same concept is introduced in multiple modalities with deliberate variation to produce transfer-appropriate processing; and formative research integration, where every episode is tested with children before broadcast and design choices are revised based on what worked. AI-generated content has not built this discipline into the production pipeline.

The chapter's point is honest. AI production has achieved cost parity with one of the most effective educational interventions ever deployed. It has not been shown to achieve the design-quality that made that intervention effective. The open bet — does AI-generated content produce durable learning outcomes comparable to professionally produced content? — is genuinely open. No peer-reviewed RCT has compared AI-generated educational content to expert-produced content on durable learning outcomes at controlled curriculum and engine layers. Vendor claims of comparable effectiveness are typically engagement-based or single-session-performance-based. Both are inappropriate proxies, for reasons this book has spent several chapters developing.

The policy this produces is the operational form of the Sunstein inversion. Deploy AI-generated content where the failure mode is small and reversible. Retain expert authorship where the failure mode is large or persistent. Treat the cost-collapse as a license to produce more good content, not as a license to lower the standard for what counts as good.

---

## Two versions of one concept

Let me make the asymmetry concrete. The concept is first-pass metabolism and its clinical implications for oral-to-IV dose conversion of beta-blockers. The Apply-level outcome the curriculum specifies: *given a patient on a beta-blocker, predict the qualitative change in plasma concentration when oral dose is converted to IV.*

**Version A** was generated by a generic LLM prompt: *write a 600-word explanation of first-pass metabolism for medical students.* No domain-specific examples. No misconception scaffold. No cross-context link. The output reads like a textbook passage — a definition, the portal circulation, the CYP enzymes, a statement that oral bioavailability is lower than IV bioavailability for drugs with high first-pass effect. Nothing in it is factually false. Nothing in it anticipates the predictable student error.

Deployed without review. The student reads it. The temporal engagement signal looks fine — expected reading time. The error trajectory signal is uninformative — the passage does not address the predictable misconception, so the engine cannot see whether the student is making it. The cross-context transfer signal is absent — no cross-domain link was built into the content. At seven days, the delayed retrieval probe — given a patient on metoprolol transitioning from oral to IV, predict the dose adjustment — comes back wrong. The student cannot apply the concept to the clinical case because the encoding was abstract and the misconception went unaddressed.

**Version B** is a Tier 2 / Tier 3 hybrid. The passage opens with a specific patient: *a 65-year-old with heart failure who can no longer tolerate oral medications is being transitioned from oral metoprolol 50 mg twice daily to IV metoprolol 5 mg every 6 hours. Is this dose conversion appropriate?* The passage explains why the answer is no — the oral dose is roughly 5 to 10 times the IV dose because metoprolol undergoes substantial first-pass hepatic metabolism. It names the misconception explicitly: *students often assume oral and IV doses are interchangeable on a milligram basis. They are not for drugs with high first-pass effect.* It links the concept to propranolol, which has an even higher first-pass fraction, and cross-references a class of oncology drugs where the same calculation appears.

Faculty review took twelve minutes. The reviewer confirmed the dose conversion factors, refined the misconception scaffold — the original draft had the student assumption slightly wrong, treating it as equivalent on a percentage basis rather than a milligram basis — and added the oncology cross-context link, which the AI draft had not produced.

Both versions produced indistinguishable engagement signals. Both students spent the expected reading time. Both clicked through. A platform that measures only engagement cannot distinguish them.

The platform that measures the error trajectory, the cross-context transfer signal, and the delayed retrieval probe at seven days sees the divergence clearly. The Version A student fails the delayed probe, and the engine records the failure — but cannot determine whether the student failed to understand the concept or whether the content the student was given failed to teach the concept the curriculum was targeting. The Version B student passes. The engine's posterior updates cleanly. The reward signal flows back into the bandit.

This is the reason the measurement layer exists. This is also the reason content choices that look identical on engagement can produce dramatically different downstream learning. The content layer's failures are mostly invisible until the measurement layer has instruments sensitive enough to see them.

---

## What the architecture requires per concept node

The minimum viable content layer is specified by what the curriculum design layer has requested. Content is minimum viable when it supplies enough material per concept node, at sufficient quality, for the engine to run the modes the curriculum's mode flags allow.

Per concept node: substrate text at the Bloom level the curriculum specifies; at least three to five Quiz Me items calibrated to the outcome statement; an Ask AI context block with prerequisite hooks identified; a Case Study scenario with rubric if the mode flags admit it; a Glimmer prompt and rubric if the mode flags admit it; and one seven-day delayed retrieval probe item distinct from the Quiz Me items and calibrated to the Bloom-level outcome.

Each of those gets a tier assignment from the production policy. The substrate text on a foundational pharmacokinetics concept is Tier 2 — AI-drafted, expert-reviewed. The Quiz Me items on the substrate table are Tier 1 — AI-generated with answer-key confirmation. The Case Study scenario is Tier 3 — domain-expert authorship from clinical experience. The probe item is Tier 2 — AI-drafted but reviewed against the outcome statement specifically. The misconception-targeted items are Tier 3 — they require knowing what students in this domain at this level get wrong, which is exactly the PCK Sadler 2013 measured.

The economic envelope this produces for a single chapter at 10 to 20 concept nodes: Tier 1 units at roughly $0.50 production plus $0.50 review; Tier 2 units at roughly $2 production plus $10 review; Tier 3 units at $20 to $100 in expert-author time. Total per chapter, order of magnitude: $600 to $3,000. The pre-AI baseline for the same chapter at the same depth: roughly $5,000 to $20,000 in writer and reviewer time. The collapse is real. The remaining cost is real too, and concentrated exactly where the asymmetry says it should stay — in the expert authorship that AI generation cannot replace.

| tier | unit count | per-unit production cost | per-unit review cost | subtotal |
| --- | --- | --- | --- | --- |
| Tier 1 (80–150 units, $0.50 production + $0.50 review each, subtotal $80–$150 | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| Tier 2 (30–60 units, $2 production + $10 review each, subtotal $360–$720 | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| Tier 3 (10–20 units, $20–$100 expert-author time each, subtotal $200–$2,000 | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| Total ($640–$2,870 | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| Pre-AI baseline ($5,000–$20,000). A final row showing the cost reduction factor: 2–7×. Columns: tier, unit count, per-unit production cost, per-unit review cost, subtotal. The table makes the economic argument concrete and shows that the remaining cost is concentrated in Tier 3 | exactly where the asymmetry says it should be. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |

---

## What would change my mind

A published RCT comparing AI-generated content with light review to expert-authored content on durable learning outcomes — 30-day-plus retention with transfer probes — at controlled curriculum and engine layers, showing no significant difference at the content layer. That would weaken the Tier 3 case and shift the boundary between Tier 2 and Tier 3 upward. The faculty review gate would still be necessary; only the placement of which content requires expert authorship versus expert review would change.

A reproducible finding that AI generation errors in non-medical domains are randomly distributed rather than systematically clustered. That would shift the case for full Tier 2 and Tier 3 review toward sampling-based review for those domains. The structural argument the chapter makes — same generation mechanism, same clustering expected — would be empirically wrong, and the policy would change to match.

A demonstrated AI production pipeline that meets the Sesame Street dual-channel alignment, signaling, temporal contiguity, and formative-research standards at $5 per unit. That would change the open-bet status of whether AI content achieves design-quality parity from *genuinely unknown* to *likely supported*. The design discipline would have been learned, not just the cost structure.

---

## Exercises

The following exercises are for practice with large language models in an educational context. Use an LLM of your choice for each.

1. **(Cost-collapse audit — LLM exercise)** Describe a specific educational content unit to an LLM — a worked example, a case study scenario, or a set of practice items in a domain you know well. Ask the LLM to produce a draft of that unit. Then ask it to identify the failure modes in its own output: where might it be inaccurate, where might it mislead without being technically wrong, and where would the output require expert review that could not be delegated to sampling? Evaluate whether the LLM correctly identifies its own systematic error tendencies or defaults to generic disclaimers about possible inaccuracy.

2. **(Tier assignment — LLM exercise)** Take a chapter from a course you know and list ten content units it would require — some Quiz Me items, some explanatory text, a case scenario, a generative assignment rubric, a misconception-targeted item. Ask an LLM to assign each unit to Tier 1, Tier 2, or Tier 3 using the reversibility criterion: *if this unit's failure could not be detected and corrected within one session, it requires Tier 3 authorship.* Evaluate whether the LLM's assignments match your own judgment, and where the disagreements are. Are the disagreements about the reversibility criterion or about whether AI can produce the unit accurately?

3. **(Version comparison — LLM exercise)** Pick a concept from your field that has a predictable student misconception — something you have seen students get wrong consistently. Ask an LLM to produce a Version A draft: generic, no misconception scaffold, no cross-context link. Then ask it to produce a Version B draft: domain-specific, with the misconception named and addressed, with at least one cross-context link. Then ask the LLM to predict what each version would produce in the measurement layer — specifically which GLP components would be informative and which would be silent. Evaluate whether the LLM correctly diagnoses the downstream measurement divergence between the two versions, or whether it treats engagement as a sufficient proxy for learning.

4. **(Burden-of-proof inversion — LLM exercise)** Present the Sunstein argument to an LLM: the burden of proof should scale asymmetrically with the irreversibility of the failure mode. Ask it to apply this argument to three content units of different types — a vocabulary definition, a misconception-targeted explanation, and a clinical case scenario — and specify what evidence threshold would be required before deploying each one. Then push back: ask the LLM to identify the weakest link in its own argument. Where is the reversibility criterion genuinely ambiguous, and how would the platform operationalize a sharper version of it?

---

## References

[^1]: Shulman, L. S. (1986). Those who understand: Knowledge growth in teaching. *Educational Researcher*, 15(2), 4–14.

[^2]: Sadler, P. M., Sonnert, G., Coyle, H. P., Cook-Smith, N., & Miller, J. L. (2013). The influence of teachers' knowledge on student learning in middle school physical science classrooms. *American Educational Research Journal*, 50(5), 1020–1049. https://doi.org/10.3102/0002831213477680

[^3]: Hill, H. C., Rowan, B., & Ball, D. L. (2005). Effects of teachers' mathematical knowledge for teaching on student achievement. *American Educational Research Journal*, 42(2), 371–406. https://www.jstor.org/stable/3699380

[^4]: Morris, C. D., Bransford, J. D., & Franks, J. J. (1977). Levels of processing versus transfer appropriate processing. *Journal of Verbal Learning and Verbal Behavior*, 16(5), 519–533.

[^5]: Lave, J., & Wenger, E. (1991). *Situated Learning: Legitimate Peripheral Participation*. Cambridge University Press.

[^6]: Sunstein, C. R. (2005). *Laws of Fear: Beyond the Precautionary Principle*. Cambridge University Press.

[^7]: Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., & Mariman, R. (2025). Generative AI without guardrails can harm learning: Evidence from high school mathematics. *Proceedings of the National Academy of Sciences*, 122(26), e2422633122. https://doi.org/10.1073/pnas.2422633122

[^8]: Risko, E. F., & Gilbert, S. J. (2016). Cognitive offloading. *Trends in Cognitive Sciences*, 20(9), 676–688. https://doi.org/10.1016/j.tics.2016.07.002

[^9]: Pal, A., et al. (2025). MedHallu: A comprehensive benchmark for detecting medical hallucinations in large language models. arXiv:2502.14302. https://arxiv.org/abs/2502.14302

[^10]: Sesame Street cost-per-child figure: Bridgespan case study (https://www.bridgespan.org/insights/audacious-philanthropy-case-studies/sesame-street); Slate 2012 (https://slate.com/business/2012/01/does-sesame-street-lose-money.html). The $5/child/year figure is a fully-amortized operations estimate; the 1969 per-child production cost was substantially different and harder to verify.

[^11]: Mares, M. L., & Pan, Z. (2013). Effects of Sesame Street: A meta-analysis of children's learning in 15 countries. *Journal of Applied Developmental Psychology*, 34(3), 140–151. https://doi.org/10.1016/j.appdev.2013.01.001

[^12]: Kearney, M. S., & Levine, P. B. (2019). Early childhood education by television: Lessons from Sesame Street. *American Economic Journal: Applied Economics*, 11(1), 318–350. https://doi.org/10.1257/app.20170300

[^13]: Nickow, A., Oreopoulos, P., & Quan, V. (2024). The impressive effects of tutoring on PreK-12 learning: A systematic review and meta-analysis of the experimental evidence. *Quarterly Journal of Economics*, 138(4), 2451–2512.

[^14]: Mayer, R. E. (Ed.). (2014). *The Cambridge Handbook of Multimedia Learning* (2nd ed.). Cambridge University Press.
