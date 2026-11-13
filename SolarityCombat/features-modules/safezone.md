---
id: safezone
title: Safezone Barrier
sidebar_position: 2
---

With `combat.restrictions.block-safezone-entry: true`, a tagged player can't get into a safezone until
their tag runs out. Needs WorldGuard; without it nothing counts as a safezone and the barrier never
triggers.

## What counts as a safezone

- With `combat.safezone.use-pvp-flag: true` (the default), anywhere WorldGuard resolves the `pvp`
  flag to `deny`. Region priority is respected, so it matches exactly where players can't be hit.
- Any region listed under `combat.safezone.regions` (`spawn` by default), whatever its flags.

## How it holds players back

- **Walking**: the player is held at the border. With `push-back: true` they're also nudged back the
  way they came (`push-strength`, default `0.4`), so the edge feels like a wall.
- **Riding**: boats, horses and other vehicles are snapped back with their momentum stopped, and the
  rider stays seated.
- **Teleporting**: any teleport into a safezone from outside one is cancelled.

Players already inside a safezone can move around in it freely.
