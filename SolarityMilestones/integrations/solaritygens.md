---
id: solaritygens
title: SolarityGens
sidebar_position: 1
---

With SolarityGens installed, the Blocks Mined category counts generator blocks players mine. Without
it, Blocks Mined stays at zero. The startup block shows `blocks (SolarityGens)` when it's reading from
SolarityGens and `blocks (no SolarityGens)` when it isn't.

- The number comes from SolarityGens' lifetime count (the same one behind `%solaritygens_mined%`), minus
  where the player stood when the season started. Nothing is counted twice, and it can't drift from
  SolarityGens.
- Each generator break checks for a tier passed, so the `milestone-reached` message arrives straight away.
- A season reset or `resetplayer` moves the starting point to the player's current total. SolarityGens'
  own numbers are never changed.
- Until the first season reset, a player's starting point is zero, so their whole SolarityGens history
  counts.

A SolarityGens too old to have the stats API logs a warning at startup and Blocks Mined stays at zero
until it's updated.
