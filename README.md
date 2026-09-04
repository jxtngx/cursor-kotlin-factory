# Cursor Kotlin Factory

A **factory**, not a lab.

This repo is boilerplate for a new Kotlin / Jetpack Compose product.
The default product class is an **ATAK-CIV / CivTAK plugin**.
A standalone Compose app is the other track.
Cursor's team implements from a spec you write in the first session.

> **Lab** = student writes the code. Mentors quiz and review.
> **Factory** = you define requirements. Chief Architect, SME, Scrum, and engineers ship tickets.

Sister factories: [cursor-swift-factory](https://github.com/jxtngx/cursor-swift-factory) · [cursor-langchain-factory](https://github.com/jxtngx/cursor-langchain-factory) · [cursor-fullstack-factory](https://github.com/jxtngx/cursor-fullstack-factory).

This factory is tightly coupled to **Kotlin**, **Jetpack Compose**, and (on the TAK track) the **official ATAK-CIV plugin SDK**.
One generated product, one primary track.

If you wanted to *learn* Kotlin by typing every type yourself, that would be a lab. This is not that.

Official references (do not vendor their trees):

- [ATAK-CIV](https://github.com/deptofdefense/AndroidTacticalAssaultKit-CIV)
- [CivTAK docs](https://www.civtak.org/documentation/)
- [tak.gov](https://tak.gov) SDK / plugin materials
- [Jetpack Compose](https://developer.android.com/compose)
- [Kotlin](https://kotlinlang.org)

Civil-use geospatial SA only (public safety, SAR, wildfire, event ops, field survey).
This factory does not implement targeting, weapons, or classified TAK variants.

---

## First command

Open this repo in Cursor and run:

```
@init-app
```

That command:

1. Asks **ATAK-CIV plugin or standalone Compose app** (one generated product, one primary track)
2. Asks **phone, tablet, or rugged** (rugged is TAK-track default)
3. Walks the same style of **requirements interview** as [cursor-swift-factory](https://github.com/jxtngx/cursor-swift-factory)
4. Writes `.cursor/plans/project-init/<name>-technical-requirements.plan.md`
5. Writes `TRACK.md`
6. Hands off to `@chief-architect` → `@kotlin-sme` / `@tak-sme` → `@scrum-master` → tickets

Do not ask an engineer to "just scaffold Gradle" before the spec exists.
That is the whole point of spec-driven init.

---

## Opinionated stack (not optional)

| Layer | Choice |
| --- | --- |
| Language | Kotlin, null-safe, no `!!` on production paths |
| UI | Jetpack Compose + Material 3. XML Views only as Adapter (ATAK map host) |
| Concurrency | Coroutines + Flow. No `GlobalScope` |
| Modules | Gradle feature modules. Domain does not depend on ATAK types |
| TAK host | Official ATAK-CIV plugin SDK. Load into the host. Do not fork ATAK-CIV |
| Messaging | Cursor-on-Target (CoT) with a checked schema on the TAK track |
| Tests | JUnit + Compose UI tests. Domain tests run without a device |
| Secrets | `local.properties` / env. Never in git |

You may add libraries the spec names.
You may not replace Compose with XML-first as the default without an ADR and Product Owner approval.
You may not copy the ATAK-CIV GPL tree into this repo as "the app."

---

## Team

| Agent | Job |
| --- | --- |
| Product Manager | `@init-app` / `@launch-product-discovery` — spec only |
| Chief Architect | Feasibility, Gradle module map, TRACK, Compose vs ATAK host seam |
| Kotlin SME | Official Kotlin / Android / Compose APIs |
| TAK SME | ATAK-CIV plugin lifecycle, CoT, map overlays. Civil use only |
| Scrum Master | Sprint + tickets from the spec |
| Feature Engineer | Compose flows + domain logic |
| Platform Engineer | Gradle / AGP / CI / ktlint / detekt |
| Data Engineer | Models, persistence, CoT parse/emit |
| Test Engineer | JUnit / Compose tests, TalkBack on primary flows |
| Reviewer | Correctness, null-safety, coroutine scopes, test gaps |

Engineers **do** implement here. That is the factory contract.
They implement *the spec*, not a surprise architecture.

---

## After init (typical)

```
@init-app
  → approve technical requirements
@chief-architect
@kotlin-sme
@tak-sme          # TAK tracks only
@scrum-master
@run-ticket-plan
@review-kotlin
```

---

## Repo layout (this boilerplate)

```
.cursor/
  commands/     init-app, launch-product-discovery, run-ticket-plan, review-kotlin
  agents/       factory team
  skills/       compose-reviewer, tak-cot
  templates/    technical-requirements, platform spec, sprint guide
  plans/project-init/   generated specs land here
templates/
  tak-phone/    walking-skeleton notes (used after spec)
  tak-tablet/
  tak-rugged/
  compose-phone/
  compose-tablet/
TRACK.md        written at init (product + device lock)
```

The tracks you did **not** pick stay in `templates/` as reference and are not the product.

---

## Related repos

| Repo | Kind |
| --- | --- |
| [cursor-swift-factory](https://github.com/jxtngx/cursor-swift-factory) | Factory — Swift / SwiftUI |
| [cursor-langchain-factory](https://github.com/jxtngx/cursor-langchain-factory) | Factory — LangChain agents |
| [cursor-fullstack-factory](https://github.com/jxtngx/cursor-fullstack-factory) | Factory — fullstack product |
| [cursor-ros2-factory](https://github.com/jxtngx/cursor-ros2-factory) | Factory — ROS 2 |
| [jxtngx/jxtngx design-philosophies.md](https://github.com/jxtngx/jxtngx/blob/master/design-philosophies.md) | Language contracts |

---

## License

Apache-2.0. See [LICENSE](LICENSE).
Not affiliated with the TAK Product Center, DoD, or Google.
ATAK-CIV is a separate work with its own license. Plugins you generate must honor that host license.
