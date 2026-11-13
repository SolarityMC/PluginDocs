---
id: worldguard
title: WorldGuard
sidebar_position: 1
---

WorldGuard is optional. SolarityCombat only reads from it, to decide where the
[Safezone Barrier](../features-modules/safezone.md) is. The `Hooks` row in the startup block shows
whether it was found.

- **PvP flag**: with `combat.safezone.use-pvp-flag: true`, any area where the `pvp` flag resolves to
  `deny` is a safezone. Set it on your spawn region with `/rg flag spawn pvp deny`.
- **Named regions**: regions listed in `combat.safezone.regions` are always a safezone, whatever their
  flags. Names aren't case sensitive.

Without WorldGuard (or if a lookup ever fails) nothing counts as a safezone, so the barrier never
traps anyone; it just stops working.

Building while tagged is also left to WorldGuard by default (`block-place` and `block-break` are
`false`), so its build flags decide where players can build mid-fight.
