# Technical Requirements Template (Kotlin factory)

Write to `.cursor/plans/project-init/[slug]-technical-requirements.plan.md`.

```markdown
---
name: [App name]
overview: [One sentence]
track: [tak-phone | tak-tablet | tak-rugged | compose-phone | compose-tablet]
problem_statement: [Why this product]
github_repo: [owner/repo]
application_id_prefix: [e.g. dev.example]
sprint_plan_file: .cursor/plans/project-init/[slug]-sprint.plan.md
todos:
  - id: spec
    content: Spec approved
    status: pending
  - id: skeleton
    content: Walking skeleton builds on locked TRACK
    status: pending
  - id: mvp
    content: Must-have flows + tests
    status: pending
isProject: false
---

# [App name] — Technical Requirements

## User Story

As a [user], I want [behavior] so that [benefit].

## Problem Statement

[Pain. Why a generic notes/map template is not enough.]

## Platform (locked)

- **TRACK**: [tak-phone | tak-tablet | tak-rugged | compose-phone | compose-tablet]
- **Min SDK**: [e.g. 26]
- **UI**: Jetpack Compose
- **Language**: Kotlin
- **TAK host**: [ATAK-CIV version pin | n/a]

See sibling `[slug]-platform.plan.md`.

## Users

- Primary: [who]
- Secondary: [who or none]

## Auth

- [none | custom | TAK server]

## Data

- Persistence: [Room | files | none]
- Network: [none | CoT | custom API]
- Entities / CoT types (MVP): [list]

## Offline

- [full | cache | online-only]

## Must-have flows (MVP)

| Flow | Device notes | Must-have |
| --- | --- | --- |
| [name] | [e.g. rugged gloves] | yes |

## Non-goals

- Not a fork of ATAK-CIV
- Not a targeting system
- [ ]

## Definition of Done (MVP)

- [ ] Spec approved
- [ ] Builds on the locked TRACK
- [ ] TAK: plugin loads in official host (stub overlay acceptable for skeleton)
- [ ] Must-have flows in Compose (Adapter at ATAK map)
- [ ] Domain tests green without a device
- [ ] TRACK honored

## Next

1. @chief-architect validates
2. @kotlin-sme notes official APIs
3. @tak-sme if tak-*
4. @scrum-master writes sprint
```
