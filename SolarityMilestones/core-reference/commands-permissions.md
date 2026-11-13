---
id: commands-permissions
title: Commands & Permissions
sidebar_position: 1
---

## Commands

### Players

Aliases: `/milestone`, `/ms`.

| Command | What it does | Permission |
|---|---|---|
| `/milestones` | Open the milestones menu | none |
| `/milestones <category>` | Open one category straight away, e.g. `/milestones kills` | none |

`<category>` is a key under `categories` in `config.yml`. An unknown category opens the main menu.

### Admins

Alias: `/smilestones`. Every subcommand needs `solaritymilestones.admin`.

| Command | What it does |
|---|---|
| `/solaritymilestones reload` | Re-read `config.yml`: categories, tiers, messages and PayNow settings |
| `/solaritymilestones reset` | Start a season reset. Shows a warning |
| `/solaritymilestones reset confirm` | Wipe every player's progress and claims. Must follow `reset` within 30 seconds |
| `/solaritymilestones resetplayer <player>` | Wipe one player's progress and claims. Works for offline players |
| `/solaritymilestones stats [player]` | One player's progress and claims in every category. The player must be online |
| `/solaritymilestones addspent <player> <cents>` | Add test spending to an online player's Store Support, in cents (`500` = $5.00) |

See [Season Resets](../features-modules/seasons.md) for what a reset keeps.

## Permissions

| Permission | Default | What it allows |
|---|---|---|
| `solaritymilestones.use` | everyone | Declared for the milestones menu. `/milestones` doesn't check it yet, so every player can open the menu |
| `solaritymilestones.admin` | op | Every `/solaritymilestones` subcommand |
