---
id: main-configuration
title: Main Configuration
sidebar_position: 1
---

`plugins/SolarityItems/config.yml`. Reload with `/solarityitems reload`.

```yaml
settings:
  target-range: 12.0
  feedback-sounds: true
  regions:
    safe:
      - spawn
      - plots
    combat-required: []
```

| Key | Default | What it does |
|---|---|---|
| `settings.target-range` | `12.0` | How far, in blocks, items look for a target player or block. An item's `ability.target-range` overrides it |
| `settings.feedback-sounds` | `true` | Reserved. Not read by this version |
| `settings.regions.safe` | `[spawn, plots]` | WorldGuard regions where combat items are refused and blocks are never changed |
| `settings.regions.combat-required` | `[]` | If not empty, combat items only work inside one of these regions |

Items themselves live in `items/`, one file each. See [Item Files](../features-modules/items.md).
The `messages` section is covered in [Messages](message-customization.md).
