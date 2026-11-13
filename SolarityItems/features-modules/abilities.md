---
id: abilities
title: Abilities
sidebar_position: 2
---

Set `ability.type` in an item file to one of these. Every key is optional and has the default shown.
`sound` takes a Bukkit sound name. `target-range` in any ability block overrides
`settings.target-range` for that item.

| Type | What it does | Keys (default) |
|---|---|---|
| `INSTANT_HEALTH` | Heals the user, capped at max health | `hearts` (2.0), `deny-when-full` (false), `sound` |
| `FEATHER_ASCENSION` | Launches the user up with slow falling | `launch-power` (1.7), `forward` (0.2), `slow-fall-seconds` (8), `sound` |
| `KB_STICK` | Heavy knockback on the target | `horizontal` (2.2), `vertical` (0.45), `sound` |
| `FORCE_PULSE` | Shockwave that pushes enemies away from the user | `radius` (5.0), `horizontal` (1.5), `vertical` (0.55), `only-target` (false), `sound` |
| `SOUL_SNARE` | Turns the ground around the target to soul sand and slows them, then puts the blocks back | `radius` (2), `duration-seconds` (6), `material` (SOUL_SAND), `slowness-level` (2), `blacklist` (materials never replaced), `sound` |
| `GLASS_DOME` | Traps the target in a hollow glass sphere, then restores the blocks | `radius` (2), `duration-seconds` (10), `material` (GLASS), `sound` |
| `GRAVE_CALLER` | Summons zombies at the target that never attack the user | `count` (2), `baby` (true), `despawn-seconds` (15), `speed-level` (1), `health` (24.0), `attack-damage` (4.0), `sound` |
| `TNT_CORE` | Drops primed TNT on the block the user looks at | `count` (1), `fuse-ticks` (40), `yield` (4.0), `break-blocks` (false), `sound` |
| `WEB_CLEAVER` | Clears every cobweb around the user | `radius` (5), `deny-when-none` (false), `sound` |
| `POCKET_WORKBENCH` | Opens a crafting table anywhere | `sound` |

## The starter items

The plugin ships one item per ability: `instant_health`, `feather_of_ascension`, `kb_stick`,
`force_pulse`, `soul_snare`, `glass_dome`, `grave_caller`, `tnt_core`, `web_cleaver` and
`pocket_workbench`. `kb_stick` and `pocket_workbench` are kept on use; the rest are used up.

## Notes

- Summoned zombies never burn in daylight, never target or hurt their summoner, and are removed when
  the server stops.
- TNT from `TNT_CORE` hurts players but leaves blocks alone unless `break-blocks: true`.
- Soul snares and glass domes never replace blocks inside a safe region; a shape that would touch
  one stops at its edge.
