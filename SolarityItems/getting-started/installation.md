---
id: installation
title: Installation
sidebar_position: 2
---

1. Download the latest release.
2. Drop `SolarityItems-<version>.jar` into your `plugins` folder. When upgrading from 2.0.0 or older,
   remove the old `SolarityItems.jar` first. Item files, `config.yml` and items already in player
   inventories keep working unchanged.
3. Restart the server.

On first start the plugin writes `config.yml` and the ten starter items into `plugins/SolarityItems/items/`.
The console shows one block when it is ready:

```
[SolarityItems] SolarityItems v26.11.0 on Folia
[SolarityItems]   Items    10
[SolarityItems]   Hooks    WorldGuard, PlaceholderAPI
[SolarityItems]   Ready in 42ms
```

`Hooks` lists the optional plugins it found.
