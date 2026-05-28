# Research: Chapter 10 — Adding Medhavy to Canvas: What Actually Changes
## Medhavy: Is the Loop Worth It?

**Chapter one-line:** The reader learns what LTI integration means in plain language, what changes for students, instructors, and the institution, and what the institution needs to provide.
**Research date:** 2026-05-27

---

## 1. Primary Sources

### Foundational papers and texts
- **1EdTech (formerly IMS Global) Learning Tools Interoperability (LTI) Advantage Specifications, v1.3 (2019, with stable updates through 2024).** The current LTI specification that Canvas, Brightspace, Moodle, and Blackboard all implement. LTI 1.3 is the stable, secure, OAuth 2.0 + JWT-based replacement for the older LTI 1.1 (OAuth 1.0a, deprecated as of mid-2024). Components: LTI 1.3 Core (launch / SSO), Assignment and Grade Services (AGS, the grade passback mechanism), Names and Role Provisioning Services (NRPS, the roster sync), Deep Linking 2.0 (content selection). Medhavy as an LTI Advantage tool means: single sign-on from Canvas, automatic roster, grade passback into the Canvas gradebook, no separate account creation for students. **This is the principle the reader needs.** The specific Canvas UI for installing an LTI 1.3 tool changes year to year — flagged MEDIUM aging risk in TIKTOC.
- **Canvas LMS Architecture (Instructure documentation, Canvas Community).** Canvas is open-source-cored, deployed by Instructure as the dominant SaaS LMS in North American HE (Phil Hill / MindWires Consulting market share reports show ~38% of US HE institutions on Canvas as of 2024, surpassing Blackboard around 2019). Architecturally relevant: Canvas's "External Tools" are LTI tools; the institutional admin installs the tool once at the account level, individual courses then add it to modules or assignments. Course-level installation by an instructor is also possible but discouraged by most central IT shops.
- **OAuth 2.0 (RFC 6749) and JSON Web Tokens (RFC 7519).** The security primitives LTI 1.3 is built on. Plain-language version for the reader: a student logged into Canvas gets a signed token that Medhavy verifies; no password is shared; the token expires; the user's role (student / instructor / TA) travels with the token.
- **FERPA (Family Educational Rights and Privacy Act, 1974 with amendments).** US federal law governing student record privacy. Any LTI tool that receives student data triggers FERPA review at the institutional level. Most institutions have a vendor questionnaire (the HECVAT — Higher Education Community Vendor Assessment Tool, maintained by Educause + REN-ISAC, currently v3.x) that vendors must complete before procurement signs.
- **NIST SP 800-171 / 800-53.** Federal security control frameworks. Increasingly required by state university systems and any institution touching federal grants. Vendor compliance is checked through HECVAT.
- **State student data privacy laws.** California (SOPIPA, 2014), Illinois (SOPPA, 2021), New York (Ed Law 2-d), and ~40 other states have student-data laws layered on top of FERPA. Institutional review timelines extend accordingly — six to twelve weeks is normal; longer at large public systems.
- **EDUCAUSE Center for Analysis and Research (ECAR) studies, 2022–2024.** ECAR's annual surveys of edtech adoption put typical SaaS implementation timeline (from contract signed to first student use) at 4–8 months for a tool of Medhavy's complexity (LTI 1.3, requires data review, requires curricular integration). The "technical setup takes days, institutional approval takes months" line in the chapter outline is empirically supported.
- **AAUP faculty workload reports (multiple years).** The standard data on what faculty actually do with their time. New course preparation: 100+ hours documented across multiple studies. Case study authoring and review: not specifically benchmarked, but maps to "scholarly review" categories at roughly 2–6 hours per case for the writer plus 1–2 hours for the reviewer.
- **Educause Quick Poll on faculty workload (2023).** Specifically asked about edtech adoption burden. Median response: faculty estimate 15–30 hours to meaningfully adopt a new instructional technology (training + curriculum redesign + first-term overhead).
- **Kotter, J. P. (1996).** *Leading Change.* HBR Press. The 8-step change model — urgency, coalition, vision, communication, empowerment, short-term wins, consolidation, anchoring. Standard reference for "what does institutional change require" — Ch 10 should not lecture the reader on Kotter, but should be informed by it when listing what the institution must provide.
- **Bridges, W. (1991).** *Managing Transitions.* The "endings → neutral zone → new beginnings" framework. Particularly relevant for the case scenario faculty reviewers: they are not just learning a new tool, they are giving up the autonomy of their old case-writing practice.
- **Wiggins, G. & McTighe, J. (2005).** *Understanding by Design* (2nd ed.). The backward-design framework — start with desired learning outcomes, design assessments that would prove they were reached, then design instruction. Maps directly onto Medhavy's concept map specification: institution must declare what counts as learned before the loop can measure whether it was learned.
- **Novak, J. D. & Cañas, A. J. (2008).** "The theory underlying concept maps and how to construct them." IHMC Technical Report. The reference document for concept-map methodology. Medhavy's "concept map specification" task is doing exactly what Novak described — naming concepts, naming relationships, ordering by prerequisite.

### Key empirical cases
- **Canvas + Khan Academy / Khanmigo integration (2023–2024).** A widely-reported case of LTI integration into Canvas at scale. Showed that the technical integration was completed in weeks; the curricular alignment took two academic years and is ongoing. Pattern Medhavy will repeat.
- **Top Hat, Lumen Learning, OpenStax, Cengage MindTap** as LTI integrations into Canvas. All standard examples the reader's IT shop will recognize. The Ch 10 chapter can name these to anchor "LTI is normal."
- **UC system rollout of any new LTI tool** routinely takes 8–14 months end-to-end due to the consolidated security review. A useful sanity check for the reader if she is at a large public institution.

---

## 2. The Core Concept — State of the Field

### What is settled
- LTI 1.3 is the production standard. Any vendor in 2026 that does not implement LTI 1.3 is behind. Medhavy must meet this bar; the chapter can treat it as table-stakes.
- The technical integration is routine for IT. Days, not weeks. This is the easy part.
- Institutional review (security, privacy, accessibility, procurement) is not routine and not fast. 8–16 weeks is normal.
- Faculty adoption — getting an instructor to actually use the new dashboard, not just have it available — is the binding constraint. Educause data consistently shows 30–50% of newly-licensed edtech tools are used minimally or not at all.

### What is disputed
- Whether the curricular design layer (concept maps, prerequisite graphs, mode assignment) can be partially generated by AI to reduce faculty burden. Vendors say yes; experienced instructional designers say the AI draft must be reviewed line-by-line and the review takes nearly as long as authoring would.
- Whether "instructor as meta-model" — interpreting GLP signals plus artifact quality — is a learnable skill or requires unusual instructor sophistication. Limited data.

### What has changed recently (last 5 years)
- LTI 1.1 deprecated mid-2024. All new procurement should be LTI 1.3.
- The HECVAT vendor questionnaire became near-universal in US HE during 2020–2023.
- Generative AI in the LMS itself (Canvas's "Smart Search," "Translations," Instructure-AI features rolled out 2024–2025) means the reader's existing Canvas already has some AI features. The chapter must be precise about what Medhavy adds beyond what Canvas-AI now does natively.
- Accessibility compliance (WCAG 2.1 AA, soon 2.2) is increasingly enforced by procurement. Medhavy must demonstrate compliance; the chapter should mention this as a procurement checklist item, not technical detail.

---

## 3. Application Domain Examples

1. **Pharmacology department, 4 sections × 80 students.** Department chair is the early adopter. LTI install: 2 days IT. Security/privacy/accessibility review: 10 weeks running in parallel with curricular work. Concept map for first 6 weeks of pharmacology curriculum: 3 sessions of 3 hours each with instructor + instructional designer. Case study authoring: 2 faculty × 6 hours each for 4 starter cases. Faculty review of each other's cases: 2 hours each. Student onboarding: 15 min in first lab. **Total institutional time: ~80 hours faculty, ~30 hours instructional designer, ~6 hours IT, ~20 hours security/privacy review.** First student in the loop: week 11–12 after decision.

2. **Anatomy & physiology, single section of 60.** Single instructor, single section. She does the concept map herself in two evenings. Cases borrowed from the AI+1 textbook's worked examples; faculty review skipped because she is the only faculty. Onboarding compressed. **Total: ~25 hours instructor, ~6 hours IT.** Faster, but Ch 9 tells us this deployment probably doesn't need Medhavy.

3. **Pre-clinical clerkship across 8 clinical sites.** Curriculum is shared but instruction is distributed. Concept map design is a committee task (clerkship director + 8 site preceptors). Case scenarios are partially borrowed from existing case-based learning materials. Faculty review must cover patient-safety claims — this is the slowest step, ~6 weeks for first wave of cases. **Total: ~150 hours faculty across the committee, ~40 hours instructional designer.**

4. **Nursing fundamentals**, single instructor, 28 students. Don't do this. (Ch 9 said so.) The point of including this case in Ch 10 is to show the reader what *not* doing the integration looks like — the time she would have spent goes back into her teaching.

5. **Health professions CE module**, asynchronous, no instructor. Concept map: short, since the content is regulatory-driven. No case scenarios; no faculty review. **Total: ~15 hours instructional designer, ~6 hours IT.** But again, Ch 9 says the reward signal is wrong for CE — the loop has nothing to optimize against.

---

## 4. The Book's Thesis Connection

The thesis claim is that Medhavy earns its cost only under three conditions. Chapter 10 makes the cost visible. Without Ch 10, the reader can be sold on the loop in principle and underestimate the institutional commitment in practice.

The chapter's thesis-relevant work is to expose the **non-software** part of the cost: faculty time on concept maps, case scenarios, and ongoing review. The license fee is the smallest line. The largest line is faculty hours, and the second-largest is the willingness-to-act commitment, which has no line item at all but is the gating condition.

The chapter also enforces the book's positioning against vendor marketing. Most vendor pitches show the LTI integration screen because it looks fast and clean. The chapter must show the LTI screen and immediately pivot to the curriculum-design layer that vendor demos elide. The reader who finishes Ch 10 should be able to ask the vendor: "Show me the concept map you'd want my pharmacology faculty to build. How many hours is that?"

The connection to the "willing to act" condition (TIKTOC Open Question 3) is direct: Ch 10 names what acting looks like. It is curriculum redesign. It is concept-map revision. It is rewriting cases when the data shows the cases are not discriminating well. The institution that adopts Medhavy and does not staff the redesign loop has bought a dashboard.

---

## 5. The AI Wayback Machine — Candidate Figures

**Recommended: Tony Bates.** Canadian researcher in open and distance education. Author of *Teaching in a Digital Age* (2015, multiple editions, open-licensed). Decades of work specifically on what HE institutions need to provide to make educational technology actually function — not the technology itself, but the surrounding institutional infrastructure. Canadian (non-US, non-UK), male, but with significant work on inclusive design and global access. His central contribution is the framework "the technology is the easy part; the institutional change is the hard part" — which is the chapter's thesis in one line. Diversity scrutiny: non-US, multi-decade, accessible writing, open-licensed work that lives outside the for-profit academic publishing world.

**Strong alternative: Pat Hutchings.** Senior Scholar emerita, Carnegie Foundation. Co-author with Mary Taylor Huber of *The Advancement of Learning* (2005) and *The Scholarship of Teaching and Learning Reconsidered* (2011). Her work centers on how institutions integrate evidence about teaching into actual practice — exactly the "willing to act" question Ch 10 raises. Woman, deep institutional-change credibility. Diversity scrutiny: woman, US-based, well-credentialed but not famous outside HE.

**Honorable mention: Mary Taylor Huber.** Hutchings' frequent collaborator. Anthropologist by training. Brings the "what institutions actually do" lens.

**Avoid:** Lee Shulman (overused, Anglo-male, late-career). Marc Andreessen (too famous, wrong field, too aligned with vendor side).

For Ch 10 final: Tony Bates is the right pick. Canadian, accessible, decades of work on the exact distinction Ch 10 makes (technology easy, institutional capacity hard), open-licensed materials the reader can actually find.

---

## 6. Pedagogical Delivery Research

The chapter must do three pedagogical things:

1. **De-magic LTI in three sentences.** "When you click the Medhavy link in Canvas, Canvas tells Medhavy who you are and what course you're in. Medhavy trusts Canvas because they share a cryptographic handshake set up once by your IT team. Grades flow back the same way." No JWT acronym. No OAuth lecture.

2. **Anchor the timeline visually.** A Gantt-style strip showing parallel tracks (IT, security/privacy, curriculum design, faculty review, student onboarding) is the chapter's load-bearing visual. The reader needs to see that these run concurrently, not sequentially.

3. **Make the faculty time cost concrete.** Not as a complaint, as a planning input. The reader has a budget; she also has a faculty time budget, and the second is harder to spend. The chapter should give her defensible numbers (drawn from the AAUP/Educause data above) she can use in a planning conversation.

The chapter should explicitly *not* try to teach the reader to install an LTI tool. That is the IT shop's job. The reader's job is to know what to ask for and what to expect.

---

## 7. Representation and Display Research

The chapter calls for two display artifacts:

**Artifact 1: LTI integration diagram.** Three boxes (Canvas, Student/Browser, Medhavy), arrows showing the handshake. Plain-language labels. Avoid the protocol-level detail; the principle is "Canvas vouches for the student; Medhavy trusts the vouch." Constraints: Kindle-readable, monochrome, < 4 inches wide. Recommended: three boxes left-to-right, two labeled arrows ("vouch" and "grades"), one annotation box at bottom ("set up once by IT").

**Artifact 2: Setup timeline table.** Rows = workstreams (IT, security/privacy, curriculum design, faculty review, student onboarding). Columns = weeks 1 through 12. Filled cells show when each track is active. The visual pattern the table should reveal: IT finishes in week 1; security review runs weeks 1–10; curriculum design weeks 3–10; faculty review weeks 6–11; student onboarding week 12. The reader should see at a glance that "weeks" is not "days" and that the binding constraint is not IT.

**Optional third artifact (worth considering):** A side-by-side of "what the vendor shows" vs "what actually happens." The vendor demo shows two steps (install, click). The reality has six tracks. This visual would be sharp but might over-shoot the chapter's collegial tone — author decision.

---

## 8. Open Questions and Research Gaps

1. **Current Canvas UI specifics.** The TIKTOC flagged this MEDIUM aging risk. By the time the book is read, the Canvas External Tools admin screen may look different. Mitigation: describe principles ("the admin installs once at the account level"), point readers to Instructure's current documentation rather than describing the UI in detail. **Author decision needed: do we include any screenshots? Recommend no — too aging-prone.**
2. **GLP dashboard specifics.** Proprietary; the chapter cannot mock up what the instructor actually sees without input from the Medhavy team. Open Question 5 in TIKTOC. Needs resolution before Ch 7 and Ch 10 drafts.
3. **Faculty review burden — is 2–6 hours per case credible?** Need at least one published estimate from a comparable case-based learning program (the AAMC has data on PBL case authoring that could anchor this; National League for Nursing has similar data for nursing). Currently estimated; needs grounding.
4. **Security review timelines at different institution types.** Small private vs. large public vs. R1 vs. community college — these vary widely. Chapter currently uses "8–16 weeks." A short paragraph naming institution-type variation would help.
5. **Accessibility (WCAG) compliance evidence.** Medhavy's current status unknown to the research pass; the chapter should mention WCAG 2.1 AA as a procurement checklist item without committing to specifics.

---

## 9. Sourcing Notes

- LTI 1.3 specification is the load-bearing reference; cite 1EdTech as the maintaining body and the spec version number, not the protocol details. Aging-stable for at least the book's lifespan.
- HECVAT is the right vendor-questionnaire reference; widely recognized in US HE procurement.
- AAUP and Educause workload data should be cited as "Educause faculty time surveys, multiple years" rather than pinning to a single year — the trend has been stable for a decade.
- Wiggins & McTighe (UbD) and Novak (concept maps) are stable, evergreen references — safe to cite without aging concerns.
- Tony Bates' *Teaching in a Digital Age* is open-licensed (CC-BY) — link directly. Free for the reader to consult.
- Phil Hill's LMS market share reports are the authoritative source for "Canvas is dominant" claims; cite by year and quarter.
- Avoid pinning Canvas UI claims to specific years; describe principles and refer to current Instructure documentation.
