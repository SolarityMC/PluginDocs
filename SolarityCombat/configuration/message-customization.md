---
id: message-customization
title: Messages
sidebar_position: 2
---

Every message is under `messages` in `config.yml`. Colours use `&` codes and `&#RRGGBB` hex. An empty
message (`""`) isn't sent.

## Prefixes

| Key | Used for |
|---|---|
| `prefix-combat` | Every combat and item cap message |
| `prefix-killtokens` | Every Kill Token message |
| `prefix-koth` | Unused; left over from KOTH |

`action-bar` and `combat-log-broadcast` are sent without a prefix.

## Combat

| Key | When | Placeholders |
|---|---|---|
| `tagged` | A player is first tagged | `%seconds%` |
| `untagged` | The tag runs out (also shown in the action bar) | |
| `action-bar` | The countdown while tagged | `%seconds%` |
| `tag-status` | `/combattag` while tagged | `%seconds%` |
| `not-tagged` | `/combattag` while safe | |
| `command-blocked` | A command is denied | |
| `safezone-blocked` | Held out of a safezone | |
| `place-blocked`, `break-blocked` | Building is denied | |
| `pearl-blocked`, `lunge-blocked`, `elytra-blocked`, `chorus-blocked` | That action is denied | |
| `combat-log-broadcast` | Someone combat logged | `%player%` |

## Item caps

All take `%item%` (the cap's `display`) and `%max%`.

| Key | When | Extra placeholders |
|---|---|---|
| `itemcap-blocked` | `BLOCK_USE`: eating over the limit was refused | `%have%` |
| `itemcap-warn` | `BLOCK_USE`: the periodic reminder | `%have%` |
| `itemcap-full` | `DROP`/`DELETE`: a pickup was refused | |
| `itemcap-dropped` | `DROP`: the excess was dropped | |
| `itemcap-removed` | `DELETE`: the excess was removed | |

## Kill tokens

`%s%` is `s` when the amount isn't 1, so `Kill Token%s%` reads correctly.

| Key | When | Placeholders |
|---|---|---|
| `killtoken-earned` | A kill paid | `%amount%`, `%s%`, `%victim%` |
| `killtoken-dropped` | Some didn't fit and were dropped | `%amount%`, `%s%` |
| `killtoken-cooldown` | Same victim too soon | `%victim%`, `%time%` |
| `killtoken-same-ip` | Same IP | `%victim%` |
| `killtoken-given` | To the sender of `/killtokens` | `%amount%`, `%s%`, `%player%` |
| `killtoken-received` | To the player who was given tokens | `%amount%`, `%s%` |
| `killtoken-usage` | `/killtokens` used wrongly | |
| `killtoken-no-player` | No online player by that name | `%player%` |
| `killtoken-bad-amount` | Amount isn't 1 to the max | `%max%` |
| `killtoken-no-permission` | No permission | |

`koth-start`, `koth-captured` and `koth-stopped` are left over from KOTH and are never sent.
