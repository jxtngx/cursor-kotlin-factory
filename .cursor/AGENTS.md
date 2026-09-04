# AGENTS.md — Cursor Kotlin Factory

This repository is a **factory**, not a lab.

Canonical contract: [cursor-swift-factory](https://github.com/jxtngx/cursor-swift-factory) and [cursor-langchain-factory](https://github.com/jxtngx/cursor-langchain-factory).

> **Lab** = the human writes the code. Mentors quiz and review.
> **Factory** = the human defines requirements. Chief Architect, SME, Scrum Master, and engineers **ship tickets**.

## Before the spec

Only `@init-app` / `@launch-product-discovery`.
No Gradle product code, no Compose screens, no ATAK plugin class.

## After the spec is approved

Engineers implement the ticket.
Do not send the Product Owner to type the app themselves.
If they wanted that, they would open a lab.

## Platform lock

`TRACK.md` is the source of truth after init:

- `tak-phone`
- `tak-tablet`
- `tak-rugged`
- `compose-phone`
- `compose-tablet`

One product, one primary track. Do not scaffold the other templates as the app.

TAK tracks load a **plugin** into official ATAK-CIV. Do not vendor the ATAK-CIV source tree.

## Stack

Kotlin, Jetpack Compose, coroutines, official ATAK-CIV plugin SDK on TAK tracks.
Cite Android / Kotlin / tak.gov docs over blogs.
No secrets in git.
Civil-use geospatial SA only.

## Markdown

No emojis. Semantic line breaks (one sentence per line).
