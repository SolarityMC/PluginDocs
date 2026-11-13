---
id: folia-support
title: Folia Support
sidebar_position: 1
---

SolarityItems runs natively on Folia (and Canvas) as well as Paper. The startup block says which one
it's on.

- Abilities run on the user's region thread. A target in a different region (far enough away to be
  on another thread) is skipped; nearby players always share a region.
- Snare and dome blocks are put back on the region that owns them.
- `/solarityitems give` hops to the receiving player's thread before touching their inventory.
- A reload builds a new item list and swaps it in at once, so it never breaks an ability in use.
