---
id: seasons
title: Season Resets
sidebar_position: 3
---

Run `/solaritymilestones reset`, then `/solaritymilestones reset confirm` within 30 seconds. Every
player, online or not, goes back to zero.

## What a reset does

- Wipes every category's progress and every claimed tier.
- Sets each player's Blocks Mined starting point to their current SolarityGens total, so the new season
  counts from zero without touching SolarityGens' own numbers.
- Restarts playtime sessions from that moment.

## What a reset keeps

- **PayNow baselines.** The plugin remembers how much each player has spent in total, so orders from
  past seasons are never counted again. Store Support starts at $0 and only new purchases count.
- Your `config.yml`.

`/solaritymilestones resetplayer <player>` does the same for one player.

The reset is written to the console with who ran it and how many players were wiped.
