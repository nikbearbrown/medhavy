# How to Build an Intelligent Textbook

### A design specification for the conductor era

**Nik Bear Brown**

*Bear Brown, LLC*

---

## Copyright

Copyright © 2026 Nik Bear Brown. All rights reserved.

Published by Bear Brown, LLC.

No part of this publication may be reproduced, distributed, or transmitted in any form or by any means without the prior written permission of the publisher, except in the case of brief quotations in critical reviews and certain other noncommercial uses permitted by copyright law.

ISBN: [INSERT ISBN]

First edition: 2026

Cover and interior design: Bear Brown, LLC.

For permissions requests, write to the publisher at the email below.

**Bear Brown, LLC** · bear@bearbrown.co · [bearbrown.co](https://www.bearbrown.co)

---

## Dedication

*For the teachers who keep teaching while the ground shifts under their feet, and for the learners — Priya in Hyderabad, Ash in Boston, every name and unnamed one in between — who showed up to learn something the system did not yet know how to teach.*

---

## Preface

I started building Medhavy because I could not get a clear answer to what I thought was a simple question.

The question was this. I teach AI to engineers. The same engineers who, four years ago, were learning to use neural networks the way an electrical engineer learns to use a transistor — read the data sheet, study the failure modes, work the examples — are now learning to use language models the way you learn to play with a precocious child who is occasionally lying to you. The difference between those two postures is enormous. The pedagogy that worked for the first does not work for the second. And nobody — not the most experienced AI researcher I know, not the most committed EdTech vendor I have spoken to, not me — could give me a clear answer to *what works now*.

What I could see, and what every working teacher with three years of post-LLM classroom experience could see, was that something had changed. The essays were different. The questions were different. The fluency of work that students had no business producing was different. What I could not see — what nobody could give me clean evidence on — was what to do.

This book is what I built while I was trying to answer that question.

I should be clear about what kind of answer it is. It is not a defense of any particular AI tool. It is not a critique of any particular EdTech vendor. It is not a manifesto. It is a design specification — the kind of document an engineer hands to another engineer when the engineer-on-the-receiving-end is going to build something that has to work. The specification names what an intelligent textbook would have to do, what evidence it would have to gather, what decisions it would have to make on the learner's behalf, and what it would have to disclose about all of that. The specification is opinionated where the evidence supports an opinion, agnostic where it does not, and explicit about the difference.

The pace at which the underlying technology is changing makes this work hard. A book published in May of 2026 about generative AI in education will be partially obsolete by January of 2027. I have tried to write a book whose obsolete parts will be specific factual claims — *the model that was the state of the art when this paragraph was written* — and whose durable parts will be the architecture and the frame. The frame is what the title means by *intelligent textbook*. The architecture is what the rest of the book describes. The frame, I am betting, will outlast the specific tools.

The book is written for two readers in the same room. The first is the domain expert with content and conviction — the Charles Fadel type, the curriculum designer with a coherent argument about what education is missing, the working teacher who has spent twenty years getting good at teaching her subject and wants to know what AI requires her to change. The second is the developer who got handed an API spec and is now responsible for building something the first reader will use. Those two readers do not, today, share a language. Half of my work in the past three years has been translating between them, in real time, on calls that should have taken thirty minutes and took three hours because the vocabulary was wrong.

If this book does its job, those two readers will have the same conversation about the same decisions, in the same terms, on the first call. That is the deliverable.

I want to acknowledge what the book is not.

It is not a comprehensive review of the educational technology literature. The literature is real, and important, and the book cites it where it bears on a specific design decision. But the book is organized around what you would have to build if you took all the evidence seriously, not around a chronological survey of who said what when.

It is not a Khan Academy book, nor an anti-Khan book. The book takes Khan's promise seriously and asks what it would actually require to deliver it. The chapter on the Khanmigo IDK-IDK pattern is honest about what the most ambitious AI-tutoring deployment in history has so far produced; the rest of the book is honest about what would have to be different. Sal Khan has done more for free access to educational content than almost anyone alive, and I want that on the record, even where my technical conclusions diverge from his.

It is not an opposed-to-AI-in-education book. The opposition position is real, and Phil Horvath's *The Digital Delusion* is its sharpest current expression, and the book engages with it seriously — including in chapter 4, which is largely a critical reading of Horvath against the evidence Horvath himself cites. The book disagrees with Horvath about the scope of the conclusions the evidence supports. The book agrees with Horvath that the field has been confusing engagement with learning for fifteen years, and the book takes that confusion as the design problem to be solved.

It is not, finally, a book about Medhavy the company. Medhavy is the illustrative platform that runs through the chapters because it is the platform I have access to as a designer; it is not the only architecture that could implement the specification the book describes. The book describes the architecture I think the evidence licenses. Where Medhavy implements that architecture, the book shows you what Medhavy does. Where Medhavy does not yet implement it, the book says so. The eight open questions in chapter 12 are not embarrassing gaps. They are the active research agenda the platform is running in the open, with student consent and visible results, because the platform's design commitment is that what it does not yet know is more important to disclose than to hide.

---

The book's organizing claim is short enough to print on one card. The card is this:

> **What is Medhavy?**
>
> Not a feature. Not a product category. A frame.
>
> Medhavy is a system that conducts other AI systems — each one a specialist, each one shaped by an instructor's vision, each one in service of a learner who chose to be here.
>
> The conductor doesn't play the instruments. She decides which one plays, when, and for how long — based on evidence, not assumption. And she adjusts as the evidence changes.
>
> She exists because the impact of AI on learning is obvious. The right implementation is not. Nobody knows yet. Medhavy doesn't pretend to. It runs the experiment.
>
> **The frame that runs every decision** — every feature, every bot, every content rule — is measured against three questions, in this order. The order is not arbitrary. The order is the argument.
>
> **The learner comes first.** Does this genuinely help the person doing the learning? Not the institution that purchased the platform, not the instructor who built the course — the human sitting with the material, trying to understand something. If learners don't want to use it, or only use it because they're required to, the platform has failed. Full stop.
>
> **The instructor comes second.** Does this make it easier for the instructor to build what they actually want to build? Not a compromise with a rigid template, but a learning experience that reflects their real pedagogical vision. The easier it is to create something genuinely useful, the more they will create.
>
> **The organization comes third.** Institutional constraints are real — compliance, branding, data governance, accreditation. They need to be easy to configure. But an organization that forces a platform on instructors who resent it and learners who resist it has solved the wrong problem.
>
> **Experiment is the product.** The impact of AI on learning is obvious. What to do about it isn't. The tools are changing faster than any curriculum can track, and what works today may not work six months from now because the underlying technology has changed.
>
> Medhavy doesn't pick a model and defend it. It runs a continuously controlled experiment — on each learner, on each teaching approach, and on the AI itself as it evolves.
>
> *What's actually improving learning outcomes? What just feels impressive?*
>
> The experiment runs on both questions at once, and the results are visible to instructors, to institutions, to anyone who wants to look.
>
> **Without transparency, there is no trust. Without trust, there is no learning.**
>
> *Medhavy — the AI. Come learn something.*

That card is the frame. The chapters are what the frame requires.

A note on the byline. The book is written in the first person. The first person is mine. The conclusions are mine. Where I have changed my mind during writing — and there are several places — the prior view and the reason for the revision are named in the chapter where the revision happened. Where I am uncertain, I have tried to say so in the same sentence as the claim, not in a footnote where the reader is unlikely to find it. The book's epistemic posture is the one I would want from a writer I trusted on a topic where the evidence is moving faster than the writing.

The book takes seriously that you may not be reading it cover to cover. Chapter 1 is what Medhavy is. Chapter 2 is what an intelligent textbook is. Chapters 3 and 4 are the calibration — when the simple answer is right, and what the evidence base licenses. Chapters 5 through 11 are the architecture, layer by layer. Chapter 12 is what the platform does not yet know. Chapter 13 is the design conversation that produces the specification a developer can build from. The introduction tells you which chapters can be skipped, in which order, and at what cost.

What I want from you, the reader, is the willingness to hold one frame in your head long enough to read the book through it. The frame is on the card above. If you cannot live with the order of the three questions, the rest of the book will not land. If you can, you will, by the end, hold a design map you can use to build something, audit something, or defend something against a vendor who is selling you the wrong thing.

That is what this book exists to do.

— Nik Bear Brown
Boston, May 2026

---
