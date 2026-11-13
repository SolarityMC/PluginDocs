---
id: installation
title: Installation
sidebar_position: 2
---

1. Download the latest release.
2. Drop `SolarityCombat-<version>.jar` into your `plugins` folder.
3. Restart the server.

The first start writes `config.yml` to `plugins/SolarityCombat/`. The startup block in the console
shows which modules are on, the item caps that loaded and which plugins were hooked:

```
[SolarityCombat] SolarityCombat v26.11.0 on Folia
[SolarityCombat]   Modules  3/3 enabled
[SolarityCombat]   Caps     ENCHANTED_GOLDEN_APPLE x3 (BLOCK_USE)
[SolarityCombat]   Hooks    WorldGuard, PlaceholderAPI
[SolarityCombat]   Ready in 12ms
```

## Upgrading from 1.x or 2.0.0

Remove the old `SolarityCombat.jar` and drop in the new one. The plugin name and data folder are the
same, so `config.yml` carries over untouched, and Kill Tokens already in players' inventories are
still recognised.
