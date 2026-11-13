---
id: message-customization
title: Messages
sidebar_position: 2
---

Every message lives under `messages` in `config.yml`. `prefix` is put in front of each one. Colour
codes `&`, `&#RRGGBB` and `&x&R&R&G&G&B&B` work. Leave a message empty (`""`) to turn it off.

| Key | When it's sent | Tokens |
|---|---|---|
| `prefix` | Before every message | |
| `no-permission` | Missing `solarityitems.use`, the item's node, or `solarityitems.admin` | |
| `disabled` | The item has `enabled: false` | |
| `on-cooldown` | The item is on cooldown | `%time%` |
| `needs-target` | A player-target item found no player | |
| `needs-block` | A block-target item found no block | |
| `combat-region-only` | A combat item used outside the allowed regions | |
| `used` | After every successful use. Empty by default | |
| `player-not-found` | `give` to a player who isn't online | `%player%` |
| `item-not-found` | `give` with an unknown id | `%id%` |
| `given` | To the admin after `give` | `%amount%`, `%item%`, `%player%` |
| `received` | To the player after `give` | `%amount%`, `%item%` |
| `reloaded` | After `reload` | `%count%` |
| `list-header`, `list-entry` | `list` | `%id%`, `%name%` in `list-entry` |
| `usage` | Wrong or missing subcommand | |

`target-too-far` is in the default file but isn't sent by this version.
