---
id: placeholders
title: Placeholders
sidebar_position: 2
---

Needs PlaceholderAPI. All of them are for the viewing player.

| Placeholder | Shows |
|---|---|
| `%solaritycombat_intag%` | `true` or `false`. Aliases: `_in_combat`, `_tagged`, `_combat` |
| `%solaritycombat_status%` | `placeholders.in-combat` or `placeholders.not-in-combat` from the config. Alias: `_intag_formatted` |
| `%solaritycombat_time%` | Seconds of combat left, `0` when safe |
| `%solaritycombat_time_formatted%` | Seconds left as `0:07`, blank when safe |
| `%solaritycombat_killtokens%` | Kill Tokens in their inventory, `0` when offline. Alias: `_kill_tokens` |

## Old KOTH placeholders

`%solaritycombat_koth_active%`, `_koth_name`, `_koth_capturer`, `_koth_progress`, `_koth_required`,
`_koth_remaining`, `_koth_percent` and `_koth_contested` still resolve so old holograms don't break,
but KOTH now lives in SolarityKoth and nothing starts an event here. They always show an inactive
KOTH (`false`, blank or `0`). Switch to SolarityKoth's placeholders.
