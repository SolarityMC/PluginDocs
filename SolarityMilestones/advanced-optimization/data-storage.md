---
id: data-storage
title: Data Storage
sidebar_position: 2
---

Each player has one YAML file, `plugins/SolarityMilestones/playerdata/<uuid>.yml`:

```yaml
name: Steve
paynow-baseline: 2500
blocks-baseline: 18342
counters:
  kills: 12
  playtime: 5400
  spent: 1000
claimed:
  kills: [1, 5, 10]
```

- `counters` are in the plugin's own units: seconds for `playtime`, cents for `spent`.
- `claimed` lists the tiers claimed this season, by amount in the same units.
- `paynow-baseline` (cents) and `blocks-baseline` survive season resets; see [Season Resets](../features-modules/seasons.md).
- Blocks Mined isn't in `counters`: it's read from SolarityGens.

A player's file is written when they leave, claim a tier, get a PayNow purchase, or are reset, and
every loaded player is written on shutdown. Kills and playtime in between are held in memory, so a hard
crash loses what was earned since the player last left.

Back up the `playerdata` folder with your worlds.
