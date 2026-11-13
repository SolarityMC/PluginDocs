---
id: regions
title: Region Rules
sidebar_position: 3
---

Region rules need WorldGuard. Without it every item works everywhere.

- **Safe regions** (`settings.regions.safe`, default `spawn` and `plots`): items with `combat: true`
  can't be used while the user stands in one, and soul snares and glass domes never place or replace
  blocks inside one.
- **Combat-required regions** (`settings.regions.combat-required`, default empty): when the list has
  entries, `combat: true` items also need the user to stand inside one of them, for example a
  `warzone` region.

A refused use shows the `combat-region-only` message and costs nothing. Region names are WorldGuard
region ids in the user's world.

## Glass dome safety

While a dome is up its glass can't be broken, blown up or pushed by pistons. Every block a dome
replaces is written to `dome-restores.yml` first, so if the server crashes with a dome standing,
the original blocks are put back on the next start.
