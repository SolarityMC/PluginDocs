---
id: rewards
title: Tiers & Rewards
sidebar_position: 2
---

Each category has a `milestones` list. Every entry is one tier:

```yaml
- amount: 50
  name: "50 Kills"          # optional
  rewards: [money give %player% 25920]
  lore:                     # optional
    - '&8- &7Reward for reaching this milestone:'
    - '&#57F287+$25,920'
```

| Key | What it does |
|---|---|
| `amount` | Where the tier sits. Minutes for `playtime`, dollars for `spent` (`2.50` works), a count for the rest |
| `name` | The tier's name in the menu and messages. Left out, it's made from the amount: `50 Kills`, `1.5 Hours Played`, `$25 Spent` |
| `rewards` | Console commands run when the tier is claimed. `%player%` is the player's name |
| `lore` | Lines shown on the tier's icon, so players can see the reward before claiming |

Tiers are sorted by `amount`, whatever order they're written in. The menu has room for 11 per category.

## Claiming

A tier can be claimed once it's reached. Clicking it in the menu marks it claimed, runs every command
in `rewards` from the console, sends the `claimed` message and plays a sound. Each tier can be claimed
once per season.

A tier with an empty `rewards` list can still be claimed. The player gets the `claimed-no-reward`
message instead, which says the reward is coming soon.
