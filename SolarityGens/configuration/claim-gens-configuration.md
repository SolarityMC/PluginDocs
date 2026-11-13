---
id: claim-gens-configuration
title: Claim Gens (claimgens.yml)
sidebar_position: 1
---

`plugins/SolarityGens/claimgens.yml` holds everything about claim gens. `/gens reload` applies
changes; placed gens keep their level and stored output. A bad entry is logged and skipped, never
fatal, and an unreadable file is copied to `claimgens.yml.broken-<time>` before defaults are used.

## levels

Shared by every type. Number them `1`, `2`, `3` ... with no gaps.

| Key | Meaning |
|---|---|
| `interval-seconds` | Time per production cycle (decimals allowed, e.g. `4.5`) |
| `per-cycle` | Items made each cycle |
| `storage` | The most a gen holds; it stops producing when full |
| `sell-multiplier` | Multiplies the type's `sell-price` |
| `upgrade-cost` | Price to reach this level, times the type's `sell-price` (ignored on level 1) |

A gen above the top level after an edit uses the top level.

## categories

Shop categories in display order: `name` (with colour codes) and `icon` (a material). A type that
names a category not listed here gets one made with its id.

## types

One section per gen type; the key is its id (used in commands, lower case).

| Key | Meaning |
|---|---|
| `category`, `tier` | Where it sits in the shop (sorted by category order, then tier) |
| `block` | The block it places as, and its item. Must be a placeable block |
| `name` | Display name, e.g. `"&8Coal"` |
| `sell-price` | Money per item at level 1. Must be above 0 |
| `unlock-cost` | One-time price in the shop. `0` = free |
| `buy-price` | Price of each extra gen once unlocked. `-1` = can't be bought again |
| `requires` | `{ type: <id>, level: <n> }`: a gen the player must already own at that level. Leave out for none |
| `lore` | Extra item lore lines (optional) |

Removing a type doesn't delete gens of it: they stay where they are, their menu shows "Unknown type",
and they can't be placed again until the type is back.

## claims

| Key | Meaning |
|---|---|
| `provider` | `landclaim` (default) or `dev`. See [Claims & Slots](../features-modules/claims-and-slots.md#claim-provider). Restart to change |
| `world` | World for starter claims |
| `grid.origin-x`, `origin-z` | Corner of the starter claim grid |
| `grid.cell-size` | Distance between cell centres (at least the largest size plus 4) |
| `grid.columns` | Cells per row |
| `sizes` | List of `{ size, slots, cost }`: claim side length, gen slots at that size, and the `/gens expand` price to reach it. The first entry is the starter claim |
| `landclaim.name` | Name of a new LandClaim claim. `%player%` is the player's name. A taken name gets `-2`, `-3` ... added |
| `landclaim.flags` | Flags every new claim gets, as `flag: value` (default `pvp: deny`) |
| `dev.enabled` | Allow SolarityGens' own test claims, as the provider or as a stand-in when LandClaim is missing. Keep it off on a live server |

Files from before the LandClaim provider kept `world` and `grid` under `dev`; they are still read
from there when the new keys are missing.

## starter

| Key | Meaning |
|---|---|
| `type` | Gen type `/gens start` unlocks and gives |
| `amount` | How many starter gens |
| `teleport` | Teleport the player to their claim after `/gens start` |

## hologram

| Key | Meaning |
|---|---|
| `enabled` | Show floating text above gens |
| `height` | Blocks above the gen's block |
| `update-seconds` | How often every loaded hologram refreshes (at least 5). Takes effect on restart |
| `lines` | Text lines. Placeholders: `{name}`, `{level}`, `{max_level}`, `{stored}`, `{cap}` |

## menu and global-booster

| Key | Meaning |
|---|---|
| `menu.click-cooldown-ms` | Clicks closer together than this are ignored (300) |
| `global-booster.max-multiplier` | The highest server booster allowed (2.0) |
