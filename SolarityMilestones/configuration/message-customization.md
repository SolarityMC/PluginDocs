---
id: message-customization
title: Messages
sidebar_position: 2
---

Every message is under `messages` in `config.yml` and starts with `prefix`. Set a message to `""` to
turn it off. Colours use `&` codes and `&#RRGGBB` hex.

| Key | When it's sent | Fills in |
|---|---|---|
| `prefix` | In front of every message | |
| `milestone-reached` | A player passes a tier | `%milestone%`, `%category%` |
| `purchase-tracked` | A PayNow purchase is added to an online player | `%amount%` |
| `claimed` | A tier with rewards is claimed | `%milestone%` |
| `claimed-no-reward` | A tier with no rewards is claimed | `%milestone%` |
| `no-permission` | An admin command without `solaritymilestones.admin` | |
| `player-only` | `/milestones` from the console | |
| `reloaded` | After `/solaritymilestones reload` | |
| `reset-warning` | After `/solaritymilestones reset` | |
| `reset-not-pending` | `reset confirm` with no reset started in the last 30 seconds | |
| `reset-done` | After a season reset | `%count%` |
| `reset-player-done` | After `resetplayer` | `%player%` |
| `player-not-found` | `stats` or `addspent` on a player who isn't online | `%player%` |
| `invalid-amount` | `addspent` with an amount that isn't a whole number | |
| `addspent-done` | After `addspent` | `%amount%`, `%player%` |
| `stats-header` | First line of `stats` | `%player%` |
| `admin-usage` | `/solaritymilestones` with a missing or unknown subcommand | |

The menu titles and item text are built in and can't be changed from the config.
