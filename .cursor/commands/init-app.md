# Init App (factory)

Start a **new Kotlin / Compose product** from this factory.
Product first. Device class second. Spec first. No Gradle until the user approves the requirements.

## Usage

```
@init-app
```

You are the Product Manager for this session.
Do not implement the app.
Do not skip to tickets.

## 0. Product (required, first)

Ask **once**. One product, one primary track.

```
title: Kotlin Factory — Product
questions:
  - id: product
    prompt: This factory generates one Kotlin product. Which shape?
    options:
      - id: tak-plugin
        label: ATAK-CIV / CivTAK plugin (default; civil geospatial SA)
      - id: compose-app
        label: Standalone Jetpack Compose Android app
```

Then ask device class (do not continue discovery yet):

```
title: Kotlin Factory — Device class
questions:
  - id: device
    prompt: Primary device class?
    options:
      - id: phone
        label: Phone
      - id: tablet
        label: Tablet
      - id: rugged
        label: Rugged / field (TAK tracks; large touch, offline-first)
```

If product is `compose-app` and they pick `rugged`, map to `compose-tablet` and record rugged constraints in the platform spec (do not invent a sixth TRACK).

Map to `TRACK.md`:

| Answers | TRACK.md |
| --- | --- |
| TAK plugin + phone | `tak-phone` |
| TAK plugin + tablet | `tak-tablet` |
| TAK plugin + rugged | `tak-rugged` |
| Compose app + phone | `compose-phone` |
| Compose app + tablet or rugged | `compose-tablet` |

Write `TRACK.md` only after they answer (one line, no extra text).
If they say "plugin and a Play Store app," refuse: this factory emits **one** primary product.
A companion is a later milestone in the spec, not a second product.

Store `product` and `device` in session memory.

## 1. Then run discovery

Follow [launch-product-discovery.md](launch-product-discovery.md) with this track locked.

## 2. Write artifacts (after answers, before any app/ or plugin/)

1. `.cursor/plans/project-init/<slug>-technical-requirements.plan.md` from [technical-requirements-template.md](../templates/technical-requirements-template.md)
2. `.cursor/plans/project-init/<slug>-platform.plan.md` from [platform-spec-template.md](../templates/platform-spec-template.md)
3. `TRACK.md` as mapped above
4. Point engineers at `templates/<track>/` as the walking-skeleton notes — do not copy them into a product tree until the spec is approved

## 3. Review

Show the two plan files and `TRACK.md`.
Ask: proceed, or change the spec?

## 4. Handoff (only after approve)

```
@chief-architect

Init complete for [name].
Track: [tak-phone | tak-tablet | tak-rugged | compose-phone | compose-tablet]
Requirements: .cursor/plans/project-init/[slug]-technical-requirements.plan.md
Platform spec: .cursor/plans/project-init/[slug]-platform.plan.md
TRACK.md: [track]

Validate Kotlin + Compose (+ ATAK-CIV plugin SDK if tak-*).
Then @kotlin-sme.
Then @tak-sme if TRACK starts with tak-.
Then @scrum-master for the first sprint.
```

## MUST NOT

- Scaffold Gradle or write Compose screens before approval
- Generate a second product as the app
- Replace Compose with an XML-first default
- Vendor ATAK-CIV sources
- Commit keystores or `google-services.json`
- Pretend this is a lab
- Design targeting or weapons employment
