---
id: placeholders
title: Placeholders
sidebar_position: 2
---

Needs [PlaceholderAPI](../integrations/placeholderapi.md). Every placeholder works under both
identifiers: `%solaritygens_<key>%` and the old `%dytchsgens_<key>%` give the same value, so existing
scoreboards and tab lists keep working.

## Claim gens

| Placeholder | Value |
|---|---|
| `%solaritygens_collected%` | Items the player has collected and sold from claim gens, comma formatted |
| `%solaritygens_collected_raw%` | The same, unformatted |
| `%solaritygens_sold%` | Money made from claim gen sales, e.g. `12,345.60` |
| `%solaritygens_slots_used%` | Claim gens the player has placed |
| `%solaritygens_slots_max%` | Gen slots the player has (from their claim size) |
| `%solaritygens_booster%` | The running server booster, e.g. `1.50x`, or empty |
| `%solaritygens_booster_time%` | Time left on the running server booster, e.g. `42m 10s`, or empty |

## Click-to-mine gens

| Placeholder | Value |
|---|---|
| `%solaritygens_mined%` | Click-to-mine gens the player has mined, lifetime, comma formatted |
| `%solaritygens_mined_raw%` | The same, unformatted |
| `%solaritygens_top_<n>_name%` | Name of the player in place `n` of the mined board (`---` when empty) |
| `%solaritygens_top_<n>_mined%` | Their count, comma formatted (`_value` is the same) |
| `%solaritygens_top_<n>_raw%` | Their count, unformatted |
| `%solaritygens_placed%` | Click-to-mine gens placed on the server |
| `%solaritygens_regenerating%` | Delayed gens currently respawning for someone (`_active` is the same) |
| `%solaritygens_types%` | Click-to-mine gen types in `config.yml` |
| `%solaritygens_tracked%` | Players with a mined count on record |

The mined board is sorted at most once a second, however often a scoreboard asks for it.
