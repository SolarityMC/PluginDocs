---
id: quick-start
title: Quick Start
sidebar_position: 3
---

1. Install the plugin and the ones you want feeding the boards (see [Requirements](requirements.md)).
2. Open `plugins/SolarityTournaments/config.yml` and set when the week ends under `schedule`
   (`timezone`, `day`, `time`). The default is Saturday at 12:00 New York time.
3. Check the `prizes` commands match your crate plugin. The defaults give ExcellentCrates `seasonal` keys.
4. If Money Earned should count other shops, add their plugin names to `boards.money.sources`.
5. Run `/tournaments reload`. If you changed the schedule and want the week in progress to follow it,
   run `/tournaments reschedule confirm`.
6. Open `/tournaments` in game to see the boards.

To check the Discord post before going live, set `discord.webhook-url`, turn `discord.enabled` on and
run `/tournaments preview` (prints it to the console) or `/tournaments post confirm`.
