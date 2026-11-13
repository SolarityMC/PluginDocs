---
id: categories
title: Categories
sidebar_position: 1
---

Each category is a section under `categories` in `config.yml`. Four keys have a source built in; the
key is what decides how a category counts, not its `display` name.

| Key | Counts | Config amounts are |
|---|---|---|
| `kills` | Player kills | kills |
| `blocks` | Generator blocks mined, read from SolarityGens | blocks |
| `playtime` | Time online | minutes |
| `spent` | Real-money store spending from PayNow | dollars |

A category with another key loads and shows in the menu, but nothing adds to it, so it stays at zero.
Set `enabled: false` on a category to hide it.

When a player passes a tier, they get the `milestone-reached` message and a level-up sound. The
reward waits until they claim it from `/milestones`.

## Kills

A kill counts when a player kills another player. Self-kills don't count, and two rules under
`kill-farming` stop farming:

- `ignore-same-ip`: kills between players on the same IP address don't count.
- `same-victim-cooldown-seconds`: killing the same player again inside this window doesn't count.
  `0` turns it off. The window is kept in memory, so it starts over on a restart.

## Blocks Mined

SolarityGens owns this number. SolarityMilestones keeps no count of its own: it reads the player's
lifetime total from SolarityGens and subtracts the total they had when the season started. See
[SolarityGens](../integrations/solaritygens.md).

The category that reads from SolarityGens is `blocks` by default. To point it at a different key, set
`blocks-category: <key>` at the top level of `config.yml` (it isn't in the default file).

## Playtime

Time online is added once a minute, so tiers pop while the player is on, and the rest is added when
they leave. Only time with this plugin running counts, and a season reset starts everyone's session
again from that moment.

## Store Support

Completed PayNow orders are added to the player who bought them. See [PayNow](../integrations/paynow.md).
