---
id: solaritygens
title: SolarityGens
sidebar_position: 1
---

The Blocks Mined board counts SolarityGens' `GeneratorBreakEvent`: one point for every click-to-mine
generator block a player mines. No other block counts.

- Limit it to some generators with `boards.blocks.generators` (generator ids). Empty means all.
- SolarityGens is also a default money source: `/autosell` and claim gen sales count towards Money
  Earned (`DytchsGens`, its old name, also works in `sources`).

If SolarityGens is missing or too old to have `GeneratorBreakEvent`, the console warns at startup and
the Blocks Mined board stays at zero.
