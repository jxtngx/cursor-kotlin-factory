---
name: compose-reviewer
description: Review Jetpack Compose for state hoisting, recomposition, and Material 3. Use when reviewing UI diffs.
---

# Compose reviewer

- State is hoisted. No business logic in `@Composable` beyond presentation.
- Side-effects go through `LaunchedEffect` / `rememberUpdatedState`, not leaking jobs.
- Previews exist for primary screens.
- Window size class honored for TRACK.
