---
id: placeholders
title: Placeholders
sidebar_position: 2
---

Needs PlaceholderAPI. `<board>` is a key under `boards` in `config.yml` (`kills`, `blocks`, `money`),
and `<n>` is a place from 1 to 10.

## The week

| Placeholder | Example |
|---|---|
| `%solaritytournaments_time_left%` | `2d 4h 11m` (empty while `enabled` is false) |
| `%solaritytournaments_ends%` | `Saturday, Oct 3 at 12:00 PM EDT` |
| `%solaritytournaments_week%` | `Week Ending Sep 27` |
| `%solaritytournaments_enabled%` | `true` / `false` |

## The viewing player

| Placeholder | Shows |
|---|---|
| `%solaritytournaments_<board>_score%` | Their score. Also `_score_raw` and `_score_short` |
| `%solaritytournaments_<board>_place%` | `#4`, or `-` when not placed. Also `_place_raw` |
| `%solaritytournaments_disqualified%` | `true` / `false` |

## The board

| Placeholder | Shows |
|---|---|
| `%solaritytournaments_<board>_players%` | How many players are on the board |
| `%solaritytournaments_<board>_top_<n>_name%` | Who is in place `n` |
| `%solaritytournaments_<board>_top_<n>_score%` | Their score. Also `_score_raw` and `_score_short` |
| `%solaritytournaments_<board>_prize_<n>%` | What place `n` wins |
| `%solaritytournaments_last_<board>_winner%` | Last week's winner |
| `%solaritytournaments_last_<board>_score%` | Last week's winning score |
| `%solaritytournaments_disqualified_count%` | How many players are disqualified (`0` while `moderation.disqualify` is off) |

The text for an empty place and for a disqualified player is set under `placeholder` in `messages.yml`.
