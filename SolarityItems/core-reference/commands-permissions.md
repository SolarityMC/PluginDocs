---
id: commands-permissions
title: Commands & Permissions
sidebar_position: 1
---

## Commands

Aliases: `/sitems`, `/solitems`, `/siteme`. Every subcommand needs `solarityitems.admin`.

| Command | What it does |
|---|---|
| `/solarityitems give <player> <id> [amount]` | Give an online player an item. Amount is 1 to 64 (default 1). Items that don't fit are dropped at their feet |
| `/solarityitems list` | List every loaded item id and name |
| `/solarityitems reload` | Re-read `config.yml` and every file in `items/` |

Players use items by clicking them; there is no player command.

## Permissions

| Permission | Default | What it allows |
|---|---|---|
| `solarityitems.admin` | op | Every `/solarityitems` subcommand |
| `solarityitems.use` | everyone | Use custom items at all |
| `solarityitems.use.*` | everyone | Use every custom item |
| `solarityitems.use.<id>` | everyone (through `use.*`) | Use one item. Each item can set its own node with `permission:` |
| `solarityitems.bypass.cooldown` | op | Skip all item cooldowns |

To take one item away from a group, negate its node, e.g. `solarityitems.use.tnt_core: false`.
An item with `permission: ""` needs only `solarityitems.use`.
