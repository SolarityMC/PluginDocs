---
id: folia-support
title: Folia Support
sidebar_position: 1
---

SolarityLeaderboards runs natively on Folia (`folia-supported: true`), and the same jar runs on Paper.

- **Counting** happens in each event's own thread: kills and deaths on the victim's region, blocks
  on the breaker's. Each player's counters change under that player's own lock.
- **Playtime and balances** are read on each online player's own thread.
- **Ranking** runs on the global region a few ticks after those reads, and swaps the whole set of
  boards in at once. Menus and placeholders only read the finished, unchangeable rankings, so they
  are safe from any thread.
- **Saving** writes `stats.yml` on an async thread.
- **Menus** open on the viewing player's thread.
