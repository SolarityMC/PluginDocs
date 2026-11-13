---
id: main-configuration
title: Main Configuration
sidebar_position: 1
---

Everything is in `plugins/SolarityCombat/config.yml`. Run `/solaritycombat` after changing it.
Colours use `&` codes and `&#RRGGBB` hex.

## Combat

```yaml
combat:
  enabled: true
  tag-seconds: 15
  action-bar: true
  punish-combat-log: true
  broadcast-combat-log: true
  combat-log-exempt-kick-causes: [FLYING_PLAYER, FLYING_VEHICLE, IDLING, KICK_COMMAND, ...]
```

| Key | Default | What it does |
|---|---|---|
| `enabled` | `true` | `false` turns combat tagging and every restriction off |
| `tag-seconds` | `15` | How long a tag lasts after the last hit |
| `action-bar` | `true` | Show the countdown in the action bar |
| `punish-combat-log` | `true` | Kill players who disconnect while tagged |
| `broadcast-combat-log` | `true` | Announce it with `combat-log-broadcast` |
| `combat-log-exempt-kick-causes` | 9 causes | Server kicks that aren't punished. See [Combat Tag](../features-modules/combat-tag.md#combat-logging) |

### Safezone

| Key | Default | What it does |
|---|---|---|
| `safezone.use-pvp-flag` | `true` | Anywhere WorldGuard denies PvP is a safezone |
| `safezone.regions` | `[spawn]` | Regions that are always a safezone |
| `safezone.push-back` | `true` | Nudge blocked players back from the border |
| `safezone.push-strength` | `0.4` | How hard |

See [Safezone Barrier](../features-modules/safezone.md).

### Restrictions

| Key | Default | What it does |
|---|---|---|
| `restrictions.block-commands` | `true` | Restrict commands while tagged |
| `restrictions.block-all-commands` | `true` | Deny every command except `allowed-commands` |
| `restrictions.allowed-commands` | 25 commands | The only commands usable while tagged |
| `restrictions.blocked-commands` | 33 commands | Denied while tagged, only used when `block-all-commands` is `false` |
| `restrictions.block-place` | `false` | Deny placing blocks |
| `restrictions.block-break` | `false` | Deny breaking blocks |
| `restrictions.block-ender-pearl` | `false` | Deny ender pearls |
| `restrictions.block-safezone-entry` | `true` | Hold tagged players out of safezones |
| `restrictions.block-spear-lunge` | `true` | Deny spears |
| `restrictions.block-elytra` | `true` | Deny gliding |
| `restrictions.block-chorus-fruit` | `true` | Deny chorus fruit |

## Item caps

```yaml
item-caps:
  enabled: true
  on-excess: BLOCK_USE
  warn-interval-seconds: 300
  check-interval-ticks: 20
  message-cooldown-millis: 3000
  limits:
    ENCHANTED_GOLDEN_APPLE:
      max: 3
      display: "Enchanted Golden Apples"
```

| Key | Default | What it does |
|---|---|---|
| `enabled` | `true` | `false` turns item caps off |
| `on-excess` | `BLOCK_USE` | `BLOCK_USE`, `DROP` or `DELETE`. Anything else falls back to `BLOCK_USE` with a warning |
| `warn-interval-seconds` | `300` | `BLOCK_USE` only: how often players over a limit are reminded |
| `check-interval-ticks` | `20` | `DROP`/`DELETE` only: how often inventories are re-counted |
| `message-cooldown-millis` | `3000` | How long before a player is told about the same cap again |
| `limits` | golden apples x3 | The caps. See [Item Caps](../features-modules/item-caps.md) |

## Kill tokens

| Key | Default | What it does |
|---|---|---|
| `enabled` | `true` | Pay tokens for kills. `/killtokens` works either way |
| `per-kill` | `1` | Tokens per kill |
| `same-victim-cooldown-seconds` | `60` | No pay for killing the same player again within this time. `0` turns it off |
| `ignore-same-ip` | `true` | No pay when killer and victim share an IP |
| `disabled-worlds` | `[]` | Worlds where kills never pay |
| `earn-sound` | `ENTITY_EXPERIENCE_ORB_PICKUP` | Played to the killer. `NONE` is silent |
| `item` | red dye | The token item. See [Kill Tokens](../features-modules/kill-tokens.md#the-token-item) |

## Placeholders

| Key | Default | What it does |
|---|---|---|
| `placeholders.in-combat` | `&#FF6B6B&l⚔ In Combat` | `%solaritycombat_status%` while tagged |
| `placeholders.not-in-combat` | `&#57F287&l✔ Safe` | `%solaritycombat_status%` when safe |

## Other sections

- `koth`: left over from when KOTH lived here. It has no effect; KOTH is in SolarityKoth.
- `messages`: see [Messages](message-customization.md).
