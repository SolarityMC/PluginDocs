---
id: quick-start
title: Quick Start
sidebar_position: 3
---

1. Install the plugin, plus SolarityGens if you want Blocks Mined to count (see [Requirements](requirements.md)).
2. Open `plugins/SolarityMilestones/config.yml` and go through the tiers under `categories`. Playtime
   amounts are minutes and Store Support amounts are dollars.
3. Change each tier's `rewards` to commands that work on your server, and its `lore` to match.
4. For Store Support, fill in `paynow.api-key` and `paynow.store-id`, or set `paynow.enabled: false`
   if you don't use PayNow. The default config has PayNow on with an empty key, so the console warns
   until one of the two is done.
5. Run `/solaritymilestones reload`.
6. Open `/milestones` in game to see the categories.

To check a Store Support reward without a real purchase, run `/solaritymilestones addspent <player> 500`
(that's $5.00) and claim the tier from `/milestones`.
