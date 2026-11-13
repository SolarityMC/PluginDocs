---
id: commands-permissions
title: Commands & Permissions
sidebar_position: 1
---

## Commands

Aliases: `/tournament`, `/tourney`, `/tourneys`.

### Players

| Command | What it does | Permission |
|---|---|---|
| `/tournaments` | Open the menu (help in the console) | `solaritytournaments.use` |
| `/tournaments top <board>` | This week's top 10 in chat | `solaritytournaments.use` |
| `/tournaments time` | When this week ends | `solaritytournaments.use` |
| `/tournaments history` | Past weeks | `solaritytournaments.use` |
| `/tournaments guide` | How it all works | `solaritytournaments.use` |
| `/tournaments help` | The command list | `solaritytournaments.use` |

`<board>` is a key under `boards` in `config.yml`: `kills`, `blocks` or `money` by default.

### Moderators

Without `confirm` typed on the end, `resetplayer` and `disqualify` only show what they would wipe.

| Command | What it does | Permission |
|---|---|---|
| `/tournaments resetplayer <player> [board\|all] confirm` | Wipe one player's week on one board or all. Alias `resetp` | `solaritytournaments.moderate` |
| `/tournaments disqualify <player> [reason] confirm` | Wipe their week and bar them from every tournament. Alias `dq` | `solaritytournaments.moderate` |
| `/tournaments requalify <player>` | Let them compete again. Aliases `undq`, `undisqualify` | `solaritytournaments.moderate` |
| `/tournaments disqualified [page]` | Who is barred, why, by whom and when. Alias `dqlist` | `solaritytournaments.moderate` |

### Admins

| Command | What it does | Permission |
|---|---|---|
| `/tournaments add <board> <player> <amount>` | Add to a score (money is in dollars) | `solaritytournaments.admin` |
| `/tournaments take <board> <player> <amount>` | Take from a score | `solaritytournaments.admin` |
| `/tournaments payouts` | Prizes still waiting for their winner | `solaritytournaments.admin` |
| `/tournaments end confirm` | End this week now and hand out the prizes | `solaritytournaments.admin` |
| `/tournaments reset confirm` | Wipe this week's scores, no prizes | `solaritytournaments.admin` |
| `/tournaments reschedule confirm` | Move this week's end to match `schedule` in `config.yml` | `solaritytournaments.admin` |
| `/tournaments preview` | Print the Discord post to the console | `solaritytournaments.admin` |
| `/tournaments post confirm` | Send the live standings to Discord now | `solaritytournaments.admin` |
| `/tournaments reload` | Re-read `config.yml` and `messages.yml` | `solaritytournaments.admin` |

## Permissions

| Permission | Default | What it allows |
|---|---|---|
| `solaritytournaments.use` | everyone | Open `/tournaments` and see the boards |
| `solaritytournaments.moderate` | op | Reset a player's week, disqualify and requalify, see the disqualified list |
| `solaritytournaments.admin` | op | The admin commands. Includes `solaritytournaments.moderate` |
| `solaritytournaments.exempt` | nobody | Nothing this player does counts towards a tournament |

`solaritytournaments.exempt` is declared with `default: false` on purpose, so operators still compete.
The node can be changed with `fair-play.exempt-permission`.
