---
id: quick-start
title: Quick Start
sidebar_position: 3
---

1. Install the plugin (see [Installation](installation.md)).
2. Run `/solarityitems list` to see the loaded item ids.
3. Give yourself one: `/solarityitems give <your name> instant_health 3`.
4. Right-click it. You heal two hearts and the item goes on a 90 second cooldown.
5. If WorldGuard is installed, open `config.yml` and set `settings.regions.safe` to the regions where
   PvP items must not work (the default is `spawn` and `plots`). Run `/solarityitems reload`.

To make your own item, copy one of the files in `items/`, change its `id`, name and ability, and
reload. See [Item Files](../features-modules/items.md).
