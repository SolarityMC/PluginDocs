---
id: placeholders
title: Placeholders
sidebar_position: 2
---

Needs PlaceholderAPI. `<id>` is an item id from `/solarityitems list`.

| Placeholder | Returns |
|---|---|
| `%solarityitems_cooldown_<id>%` | Time left on the player's cooldown, e.g. `1m 30s`, or `Ready` |
| `%solarityitems_cooldown_raw_<id>%` | Seconds left, `0` when ready |
| `%solarityitems_ready_<id>%` | `true` or `false` |
| `%solarityitems_count%` | Number of loaded items |

The per-player placeholders return an empty string for offline players and unknown ids.
