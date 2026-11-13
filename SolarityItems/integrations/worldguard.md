---
id: worldguard
title: WorldGuard
sidebar_position: 1
---

SolarityItems reads WorldGuard regions to decide where PvP items work and where abilities may change
blocks. It is optional: the plugin loads without it and then applies no region rules.

What it checks:

- The regions at the user's position, for `combat: true` items.
- The regions at each block a soul snare or glass dome would replace.

Set the region ids in `settings.regions` (see [Region Rules](../features-modules/regions.md)). The
`Hooks` row in the startup block shows `WorldGuard` when it was found.
