# Launch Product Discovery (Kotlin factory)

Same *shape* as [cursor-swift-factory](https://github.com/jxtngx/cursor-swift-factory) discovery: questionnaire → technical requirements → architect → scrum.
Questions are about a **Kotlin / Compose product**, with TAK-aware items when TRACK starts with `tak-`.

Called from `@init-app` after TRACK is locked. If `TRACK.md` is missing, run `@init-app` instead.

## Question sequence

### Q1 — Job

Conversational, then lock it:

- One-sentence description
- Problem statement
- Product name

Give two examples first:

- TAK: "A wildfire field plugin: drop a CoT marker for a water source, show it on the ATAK map, work offline on a rugged tablet."
- Compose: "A phone app for a SAR team to log check-ins and export a GPX later."

Civil geospatial SA only.

### Q2 — Users

```
Who is the primary user?
- Individual field operator
- Small team (incident / event)
- Public-safety org
- Mixed
```

### Q3 — Auth

```
- None
- Org SSO / custom backend (name it)
- TAK server credentials (never stored in git)
```

### Q4 — Data

```
- On-device only
- TAK network (CoT)
- Custom API
```

Name entities they care about (3–7). On TAK tracks, name CoT types.

### Q5 — Offline

```
- Must work fully offline
- Offline cache, radio when available
- Online-only
```

Rugged TRACK defaults to fully offline unless they override.

### Q6 — Host / store

TAK tracks: plugin for official ATAK-CIV (version pin).
Compose tracks: sideload / Play / neither (dev).

### Q7 — Capabilities (track-aware)

Ask only what the locked track can do. Examples:

- TAK: map overlay, marker, drawing, video, CoT send/receive, contact list (yes/no, must-have vs later)
- Phone: camera, GNSS, background location
- Tablet: dual pane
- Rugged: large touch, no Play Services, radio bearer

### Q8 — Non-goals

Force an out-of-scope list (at least three items).
Always include: not a fork of ATAK-CIV; not a targeting system.

### Q9 — Repo

- GitHub `owner/repo` for the *generated* product
- Sprint plan filename
- ApplicationId prefix if they have one — do not invent a Play signing key

## Write the spec

Use [technical-requirements-template.md](../templates/technical-requirements-template.md) and [platform-spec-template.md](../templates/platform-spec-template.md).

Do not implement.
Hand back to `@init-app` step 3 if invoked from there; otherwise hand off to `@chief-architect`.
