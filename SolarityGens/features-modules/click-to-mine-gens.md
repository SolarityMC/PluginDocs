---
id: click-to-mine-gens
title: Click-to-Mine Gens
sidebar_position: 5
---

Click-to-mine gens are public blocks for the warzone. Staff place them; every player mines them.

## Per-player breaking

The real block never breaks. When a player mines a gen, only they see it break: it comes back at
once (`respawn-seconds: 0`) or after a timer, during which that player sees the `regenerating-block`
and an action-bar countdown. Everyone else keeps mining the same block. Timers are kept across a
relog, so relogging doesn't skip them.

Each break gives the drops (with Fortune if the type has `fortune: true`), XP for XP gens, counts
towards the player's mined total and fires `GeneratorBreakEvent` for other plugins.

## Auto features

Each player toggles these for their own drops:

| Command | Does | Default |
|---|---|---|
| `/autopickup` | Drops go straight to the inventory | on |
| `/autosmelt` | Ores are smelted first (from the server's own furnace recipes) | on |
| `/autoblock` | Resources are compressed into blocks (9 to 1, quartz 4 to 1). Only plain items are compressed, never named or custom ones | on |
| `/autosell` | Drops are sold at ShopGUIPlus prices and paid through Vault. Anything ShopGUIPlus can't price goes to the inventory | off (a rank perk) |

A feature only works with its permission ([Commands & Permissions](../core-reference/commands-permissions.md)).
When the inventory is full, the player gets one warning every 10 seconds.

## Mine through players

Inside the WorldGuard regions in `settings.mine-through-regions`, attacks on players are cancelled,
and a player standing between you and a gen is hidden from you while you drill through them. With
PacketEvents they stay in your tab list. Needs WorldGuard.

## Picking a gen up

Staff with `solaritygens.admin` remove a gen by sneaking and breaking it, but only after arming
with `/gens pickup` (unless `pickup.require-arm` is false). Arming lasts `pickup.arm-seconds` and,
with `pickup.disarm-after-use`, covers one pickup. `/gens remove` turns the gen you look at back into a
normal block.

## Removed gen types

If a placed gen's type is removed from `config.yml`, the gen stays registered and protected: it can't
be broken, and staff are told to put the type back or use `/gens remove`. Gens in a world that isn't
loaded yet are kept and go live when the world loads.
