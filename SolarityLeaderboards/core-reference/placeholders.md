---
id: placeholders
title: Placeholders
sidebar_position: 2
---

Needs PlaceholderAPI. `<board>` is `kills`, `deaths`, `blocks`, `sold`, `baltop` or `playtime`
(`crystals` and `money` also mean baltop, `gens` means sold). `<n>` is a position, starting at 1.

## Any position

| Placeholder | Returns |
|---|---|
| `%solarityleaderboards_top_<board>_<n>_name%` | The player's name, or `placeholders.empty-name` (`---`) when nobody is there |
| `%solarityleaderboards_top_<board>_<n>_value%` | The value as the board shows it (`1,234`, `$1,234`, `2d 3h 4m`), or `0` |
| `%solarityleaderboards_top_<board>_<n>_raw%` | The plain number, or `0` |

## The viewing player

| Placeholder | Returns |
|---|---|
| `%solarityleaderboards_position_<board>%` | Their position, or `0` when they aren't on the board |
| `%solarityleaderboards_value_<board>%` | Their value as the board shows it |
| `%solarityleaderboards_raw_<board>%` | Their plain number |

## The board

| Placeholder | Returns |
|---|---|
| `%solarityleaderboards_size_<board>%` | How many players are on it |

Placeholders read the last ranking, so they change when the boards refresh (every
`refresh-seconds`, 60 by default).
