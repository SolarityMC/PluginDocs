---
id: boards
title: Boards
sidebar_position: 1
---

| Board | Counts | When it changes |
|---|---|---|
| Kills | Players killed by the player (not themselves) | At once |
| Deaths | Times the player died, to anything | At once |
| Blocks Mined | SolarityGens click-to-mine gens mined, plus every other block broken | At once |
| Gens Sold | Lifetime money from selling SolarityGens claim gen output | At once |
| Baltop | The player's balance | Each refresh, for online players |
| Playtime | Minecraft's own play time statistic | Each refresh, and on join and quit, for online players |

A player only appears on a board once their value is above zero. Ties are ordered by name. The
rankings themselves are rebuilt every `refresh-seconds` (60 by default) and by `/leaderboards reload`.

## Blocks Mined

Every block a player breaks counts, in any world, unless `boards.blocks.count-every-block` is
`false` (then only SolarityGens gens count). Blocks broken in creative mode don't count unless
`boards.blocks.count-creative` is `true`. SolarityGens gens never count twice: SolarityGens cancels
the vanilla break for them and reports the mined count itself.

## Baltop

See [Economy](../integrations/economy.md) for where balances come from. With Vault, a player who
is offline shows the balance they had the last time they were online.
