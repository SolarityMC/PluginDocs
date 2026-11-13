---
id: placeholders
title: Placeholders
sidebar_position: 2
---

Needs PlaceholderAPI. `<category>` is a key under `categories` in `config.yml` (`kills`, `blocks`,
`playtime`, `spent`). All of them are for the viewing player.

| Placeholder | Shows |
|---|---|
| `%solaritymilestones_<category>%` | Their progress, formatted: `1,204`, `3.5 Hours`, `$25` |
| `%solaritymilestones_<category>_raw%` | Their progress as a plain number: seconds for playtime, cents for spent |
| `%solaritymilestones_<category>_claimed%` | How many tiers they've claimed |
| `%solaritymilestones_<category>_claimable%` | How many tiers are reached and waiting to be claimed |
| `%solaritymilestones_claimable%` | Tiers waiting to be claimed across every category |

A category that doesn't exist (or is disabled) returns nothing, so PlaceholderAPI leaves the text as it is.
