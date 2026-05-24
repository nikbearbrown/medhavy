# How to Build an Intelligent Textbook

### A design specification for the conductor era

**Author:** Humanitarians AI · ni.brown@neu.edu
**Publisher:** Bear Brown, LLC
**Format:** Kindle / KDP ($1 / Kindle Unlimited) + EPUB (direct distribution) + tight integration with [Medhavy](https://www.medhavy.com/)
**First edition:** 2026
**Status:** Draft — TIKTOC v1.2 complete, all 13 chapters drafted, ready for editorial review

---

## What the book argues

A student in the highest-funded AI tutoring deployment in human history types four characters into the Socratic prompt — `idk idk` — and presses return. The system logs her as engaged. She is not learning.

This is the moment the book starts.

The field has been arguing for fifteen years about whether AI in education works. The disagreement has been between people who cherry-pick the positive cases (Khan, Khanmigo, every TED talk between 2016 and 2024) and people who cherry-pick the negative cases (Horvath, the PISA correlations, the smartphone-bans-in-schools wave). The third position — the one this book occupies — is to read all of it. Not as a survey. As a design specification. *Given everything we know, what would the platform have to do to avoid producing the failures we have already produced and to capture the gains the evidence supports?*

The central claim: **the intelligent textbook is not a product category. It is a frame.** Within the frame, the load-bearing element is not the AI model, not the content, not the interface, not the LMS integration. It is the conductor — the system that decides which instrument plays for which learner on which concept at which moment, watches what happens, and adjusts.

The book is for two readers in the same room — the domain expert with content and conviction (the Charles Fadel type), and the developer who got handed an API spec — who do not yet share a language. After reading the book, they should be able to hold the same conversation about the same decisions in the same terms.

---

## Table of Contents

### Front matter

- `00-frontmatter.md` — Title page, Copyright, Dedication, Preface (includes the conductor-frame card)
- `00-introduction.md` — Roadmap, audience location, central concept, chapter-by-chapter map, the book-level AI note

### Act One — The Right Question

| Ch | File | Title |
|---:|---|---|
| 1 | `01-what-is-medhavy.md` | What is Medhavy? *(load-bearing)* |
| 2 | `02-what-is-an-intelligent-textbook.md` | What Is an Intelligent Textbook? |
| 3 | `03-when-anki-is-enough.md` | When Anki Is Enough |
| 4 | `04-the-evidence-base.md` | The Evidence Base *(load-bearing)* |

### Act Two — The Architecture

| Ch | File | Title |
|---:|---|---|
| 5 | `05-the-four-layers.md` | The Four Layers |
| 6 | `06-the-measurement-layer.md` | The Measurement Layer *(load-bearing)* |
| 7 | `07-the-four-modes.md` | The Four Modes |
| 8 | `08-the-adaptive-engine.md` | The Adaptive Engine *(load-bearing)* |
| 9 | `09-the-curriculum-design-layer.md` | The Curriculum Design Layer |
| 10 | `10-the-content-layer.md` | The Content Layer |
| 11 | `11-the-economics.md` | The Economics of Intelligent Textbooks |

### Act Three — The Map

| Ch | File | Title |
|---:|---|---|
| 12 | `12-what-the-platform-does-not-know-yet.md` | What the Platform Does Not Know Yet |
| 13 | `13-the-design-conversation.md` | The Design Conversation |

### Appendices

| App | File | Title |
|---:|---|---|
| A | `A-medhavy-lexicon.md` | The Medhavy Lexicon |
| B | `B-causal-knowledge-graph.md` | The Causal Knowledge Graph |
| C | `C-glp-technical-specification.md` | The GLP Framework: Technical Specification |
| D | `D-contextual-bandits.md` | Contextual Bandits: Implementation Notes |
| E | `E-medhavi-hub-architecture.md` | The Medhavi Hub: Architecture Reference |
| F | `F-medhavy-1.5-feature-roadmap.md` | Medhavy 1.5 Feature Roadmap |
| G | `G-medhavy-1.5-video-animation.md` | Medhavy 1.5 Video and Animation |
| H | `H-canvas-lti-research.md` | Canvas LTI Integration Research |
| I | `I-contextual-bandits-2.0.md` | Contextual Bandits for Learning Mode Selection (2.0) |

### Back matter

- `99-back-matter.md` — Acknowledgments, About the Author, Notes (by chapter), References, Glossary

**Load-bearing chapters (cannot be skipped):** 1, 4, 6, 8.

**For readers in a hurry:** Chapters 1 → 4 → 6 → 8 deliver the book's spine in four chapters and roughly 30,000 words.

---

## How to read this book

The book is built to read front to back. The argument compounds. Chapter 8 depends on Chapter 6. Chapter 9 depends on Chapter 7. Chapter 12 names what every prior chapter is honestly uncertain about. Every chapter ends with four features — *What would change my mind*, *Still puzzling*, *Exercises*, and a *Bridge* question — that are the chapter's contract with the reader.

The book pairs with [Medhavy](https://www.medhavy.com/), the platform the book describes from the inside. Reading the book inside Medhavy gives the reader access to the AI tutor that anchors Ask AI mode against the book's content, the spaced-repetition deck (Quiz Me) built from the book's load-bearing claims, and the design-conversation tool (Chapter 13's worked example) that the reader can run for their own project after finishing the book.

---

## What this book is not

Not a literature review. Not the optimistic case for AI in education (Khan's *Brave New Words* is). Not the pessimistic case (Horvath's *The Digital Delusion* is). Not a how-to for using ChatGPT in your classroom on Monday. Not a book about Medhavy the company — Medhavy is the illustrative platform that runs through the chapters because it is the platform the author has access to as a designer; it is not the only architecture that could implement the specification.

The book is a design specification an engineer hands to another engineer when the engineer-on-the-receiving-end is going to build something that has to work.

---

## Copyright

Copyright © 2026 Nik Bear Brown. All rights reserved.

Published by Bear Brown, LLC.

No part of this publication may be reproduced, distributed, or transmitted in any form or by any means without the prior written permission of the publisher, except in the case of brief quotations in critical reviews and certain other noncommercial uses permitted by copyright law.

ISBN: [INSERT ISBN]

First edition: 2026.

For permissions requests, write to the publisher at **bear@bearbrown.co**.

See [`LICENSE.md`](./LICENSE.md) for the full license text.

---

## Repository structure

```
book.md                   ← planning doc — book description and high-level outline
TIKTOC.md                 ← v1.2 — chapter list, learning outcomes, pantry index
outline.md, vision.md, architecture.md, chapters-spec.md, risks.md   ← Tic TOC planning
chapters/                 ← compiled body (front matter, 13 chapters, back matter)
    _archive/             ← pre-TIKTOC-v1.0 drafts (preserved voice samples)
pantry/                   ← 17 chapter research notes + 11 library files + Medhavy internal docs
    README.md             ← full pantry inventory + 22 flags requiring author attention
logs/log.csv              ← per-chapter writing log
images/                   ← figures (gitignored except for the placeholders)
styles/                   ← kindle.css base + per-book overrides
output/                   ← built EPUB (gitignored)
build.sh, graphs.sh       ← build pipeline
```

### Build

```bash
./build.sh
```

Output goes to `output/` (gitignored).

### Figures

```bash
./graphs.sh
```

Processes `<!-- → [TYPE: description] -->` comments in every chapter into either classed markdown tables or placeholder images.

### Publish

Upload `output/medhavy.epub` to [KDP](https://kdp.amazon.com). The book is also distributed direct via EPUB for colleague-to-colleague handoff before a build starts, and is suitable for course assignment in graduate EdTech, instructional-design, and learning-engineering programs.

---

## About the Author

**Nik Bear Brown** is an Associate Teaching Professor in the Northeastern University College of Engineering and the founder of Humanitarians AI, Bear Brown & Company, and Musinique LLC. PhD and MS in Computer Science from UCLA. MS in Information Design and Data Visualization, plus MBA, from Northeastern. Earlier in his career he worked as a molecular biologist at DNAX Research Institute and Cetus Corporation; later, a part-time postdoc at Harvard Medical School in deep learning while teaching at Northeastern.

He teaches AI, data science, programming, and visualization, and builds AI infrastructure for education, judgment-bearing documentation tools, and frameworks for what remains *irreducibly human* in an age of increasingly capable machines.

Connect at [nikbearbrown.com](https://www.nikbearbrown.com) · [irreducibly.xyz](https://irreducibly.xyz) · [skepticism.ai](https://www.skepticism.ai) · [bear@bearbrown.co](mailto:bear@bearbrown.co) · [LinkedIn](https://linkedin.com/in/nikbearbrown).

---

*मेधावी (Medhavy)* — from Sanskrit, meaning *intelligent* or *intellectually brilliant*.

**Come learn something with us.** → [www.medhavy.com](https://www.medhavy.com/)

---

## What This Book Is

This book is a design specification.

Not a survey of the field. Not a cheerleading document for AI in education. Not a warning about it. A specification: if you wanted to build a platform that avoided the failure modes the field has already demonstrated, and captured the gains the evidence supports, here is what the architecture would have to do, in the order the decisions depend on each other.

The vocabulary the book teaches is small: *conductor*, *instrument*, *four modes*, *seven signals*, *Genuine Learning Probability*, *within-learner bandit*, *cost-collapse asymmetry*, *IDK-IDK pattern*, *experiment-as-product*. Each term gets defined where it first appears. The book's Lexicon in Appendix A is the single-page index if you need to find a definition quickly.

The book is for two readers. The first is the domain expert — the experienced teacher, the curriculum designer, the person who has content and conviction and needs to know what she is commissioning when she commissions an intelligent textbook. The second is the developer who has been handed an API specification and needs to build what the first reader will use. After reading this book, both readers should be able to hold the same conversation about the same decisions in the same terms. That shared language is the book's primary product.

---

---

## Who This Book Is For

reader should see that most problems cluster in the middle and that the spectrum determines which layers are warranted] -->

---

## The Economics Change Everything Except the Target

There is a fact about the economics of intelligent textbooks that I want to name early because it changes the shape of several later chapters.

For decades, the high-quality intelligent tutoring systems that produced the large effect sizes in the ITS literature cost somewhere between $100 and $1,000 per student-hou

---

## How to Read It

<!-- TODO: populate from chapter content -->

---

## Signature Simulations

<!-- TODO: populate from chapter content -->

