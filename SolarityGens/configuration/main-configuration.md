---
id: main-configuration
title: Main Configuration (config.yml)
sidebar_position: 2
---

`plugins/SolarityGens/config.yml` covers click-to-mine gens, the auto features, booster vouchers and
messages. `/gens reload` applies changes.

## autosell

| Key | Meaning |
|---|---|
| `backend` | Kept for old configs. Only `VAULT` exists (ShopGUIPlus prices, Vault payout) |
| `debug` | Log every autosold item, its price and each payout |

## settings

| Key | Meaning |
|---|---|
| `xp-applies-mending` | XP from XP gens repairs Mending gear first, like a real orb |
| `break-effects` | Break sound and particles, shown only to the player breaking |
| `mine-through-players` | Master switch for mine-through |
| `mine-through-regions` | WorldGuard region name, or a list. Empty = off. The old `mine-through-region` key still works |
| `mine-through-reach` | How far behind a player a gen can be for mine-through (4.5) |

## interact-blocks

| Key | Meaning |
|---|---|
| `anvil`, `enchanting` | Right-clicking a placed anvil or enchanting table opens the enhanced menu |
| `regions` | Limit that to these WorldGuard regions. Empty = anywhere |

## mined-stats

| Key | Meaning |
|---|---|
| `enabled` | Count click-to-mine gens mined per player |
| `save-interval-seconds` | How often `minedstats.yml` is written (at least 30) |

## respawn-actionbar

`enabled` and `message` for the countdown a player sees after breaking a delayed gen. Placeholders:
`{gen}`, `{time}` (`m:ss`), `{seconds}`.

## boosters

`block-voucher` and `sell-voucher` set each voucher's `material`, `name`, `glow` and `lore`
(placeholders `{multiplier}` and `{duration}`). `status` sets the `/boosters` panel: `header`,
`active-line` (`%type%`, `%multiplier%`, `%time%`), `none`, `footer`, and `global-line` for the server
booster (`%multiplier%`, `%time%`, `%by%`).

## generators

One section per click-to-mine gen type; the key is its id.

| Key | Meaning |
|---|---|
| `material` | The block (also the item you place) |
| `respawn-seconds` | `0` = comes back instantly; otherwise seconds until it comes back for that player |
| `regenerating-block` | What the player sees while it respawns (default `BEDROCK`) |
| `break-permission` | Only players with this node can break it (optional) |
| `item-name`, `item-lore`, `glow` | The gen item's look |
| `drops` | List of `"MATERIAL AMOUNT"`. Left out = drops the block itself; `[]` = drops nothing |
| `fortune` | A Fortune tool multiplies the drops like real ore |
| `xp` | XP per break, a number (`30`) or a range (`15-43`) |

## pickup

| Key | Meaning |
|---|---|
| `require-arm` | Staff must run `/gens pickup` before sneak-breaking a gen removes it |
| `arm-seconds` | How long arming lasts (at least 5) |
| `disarm-after-use` | One arming covers one pickup |

## utility-commands

`anvil` and `enchanting` turn `/gens anvil` and `/gens enchanting` on or off.

## messages

See [Messages](message-customization.md).
