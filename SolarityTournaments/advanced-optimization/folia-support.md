---
id: folia-support
title: Folia Support
sidebar_position: 1
---

SolarityTournaments runs natively on Folia (and Canvas) as well as Paper. The startup block says which
one it's on.

- The week clock, score saving and menu refreshes run on the global scheduler.
- Prize delivery and menus for a player run on that player's own thread.
- SQLite runs on its own thread, never on a game thread.
- Scores are kept in thread-safe memory, so kills, mining and sales count from any region.
