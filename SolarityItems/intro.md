---
id: intro
title: Introduction
sidebar_position: 1
---

SolarityItems adds config-driven custom items with click abilities to Solarity's servers, for **Paper**
and **Folia** 26.3. Each item is one file in the `items/` folder with its own name, lore, cooldown,
permission and ability. Drop in a new file, run `/solarityitems reload`, and the item exists.

## What's in this guide

- **[Getting Started](getting-started/quick-start.md)**: requirements, installation and a first run.
- **[Core Reference](core-reference/commands-permissions.md)**: commands, permissions and placeholders.
- **[Features](features-modules/items.md)**: item files, the ten abilities and region rules.
- **[Configuration](configuration/main-configuration.md)**: `config.yml` and its messages.
- **[Integrations](integrations/worldguard.md)**: WorldGuard and PlaceholderAPI.
- **[Advanced](advanced-optimization/folia-support.md)**: Folia and data storage.
- **[Support](support/faq.md)**: FAQ.

## Key features

- **One file per item**: name, lore, material, custom head textures, glow and cooldown, all in YAML.
- **Ten abilities**: healing, launches, knockback, shockwaves, soul sand snares, glass domes, minions, TNT, web clearing and a portable workbench.
- **Per-item permissions and cooldowns**, with a bypass permission for staff.
- **WorldGuard region rules**: PvP items stay out of safe zones, and block-changing abilities never edit them.
- **Crash-safe glass domes**: replaced blocks are journaled and put back on the next start.
- **PlaceholderAPI placeholders** for cooldowns, and native Folia support.

## Quick links

- [GitHub repository](https://github.com/SolarityMC/SolarityItems)
- [GitHub Issues](https://github.com/SolarityMC/SolarityItems/issues)

Ready to go? Start with the **[Quick Start](getting-started/quick-start.md)**.
