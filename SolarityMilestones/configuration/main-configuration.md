---
id: main-configuration
title: Main Configuration
sidebar_position: 1
---

Everything is in `plugins/SolarityMilestones/config.yml`. Run `/solaritymilestones reload` after
changing it. Colours use `&` codes and `&#RRGGBB` hex.

## PayNow

```yaml
paynow:
  enabled: true
  api-key: ""
  store-id: ""
  refresh-seconds: 60
  connect-timeout-ms: 5000
  read-timeout-ms: 8000
  base-url: "https://api.paynow.gg/v1"
```

| Key | Default | What it does |
|---|---|---|
| `enabled` | `true` | Track Store Support from PayNow |
| `api-key` | empty | Management API key with order read access |
| `store-id` | Solarity's store | The numeric store id |
| `refresh-seconds` | `60` | How often new orders are checked. Lowest is 15 |
| `connect-timeout-ms` | `5000` | Connect timeout per request. Lowest is 500 |
| `read-timeout-ms` | `8000` | Read timeout per request. Lowest is 1000 |
| `base-url` | `https://api.paynow.gg/v1` | PayNow API address. Leave it unless PayNow changes it |

See [PayNow](../integrations/paynow.md).

## Kill farming

```yaml
kill-farming:
  ignore-same-ip: true
  same-victim-cooldown-seconds: 300
```

| Key | Default | What it does |
|---|---|---|
| `ignore-same-ip` | `true` | Kills between players on the same IP don't count |
| `same-victim-cooldown-seconds` | `300` | Killing the same player again inside this many seconds doesn't count. `0` turns it off |

## Categories

```yaml
categories:
  kills:
    enabled: true
    display: "&#FF6B6BKills"
    icon: IRON_SWORD
    milestones:
      - amount: 1
        rewards: [money give %player% 675]
```

| Key | What it does |
|---|---|
| `enabled` | `false` hides the category |
| `display` | Its name in the menu and in the `milestone-reached` message |
| `icon` | The material shown in the menu. An unknown one falls back to `PAPER` |
| `milestones` | The tiers. See [Tiers & Rewards](../features-modules/rewards.md) |

The default file has 11 tiers in each of `kills`, `blocks`, `playtime` and `spent`. What each key
counts is on [Categories](../features-modules/categories.md).

## Blocks category

`blocks-category` (not in the default file, default `blocks`) is the category that reads from
SolarityGens.

## Messages

The `messages` section. See [Messages](message-customization.md).
