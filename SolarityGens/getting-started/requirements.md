---
id: requirements
title: Requirements
sidebar_position: 1
---

## Server

- **Paper or Folia 26.3** or newer (Canvas works too). The plugin is built against the 26.3 API.
- **Java 25**.

## Plugins

None are required. Each of these adds something when it is installed:

| Plugin | What it adds |
|---|---|
| Vault (VaultUnlocked on Folia) and an economy | All money: claim gen sales, upgrades, unlocks, `/gens expand` and `/autosell`. Without an economy nothing can be bought or sold. |
| LandClaim 26.11.0+ (with WorldGuard) | The claims claim gens live in, with their protection and members. Without it claim gens can't be placed, unless the test claims are turned on. |
| PlaceholderAPI | The `%solaritygens_*%` and `%dytchsgens_*%` [placeholders](../core-reference/placeholders.md). |
| ShopGUIPlus | Prices for `/autosell` on click-to-mine gens, and personal sell boosters on manual shop sells. |
| WorldGuard | Needed by LandClaim. Also mine-through-players on click-to-mine gens, and limiting the enhanced anvil and enchanting table to regions. |
| PacketEvents | Keeps a drilled-through player in the tab list during mine-through. |

See [Integrations](../integrations/vault.md) for the details of each.

SolarityGens uses the SQLite driver that ships with Paper. Nothing else needs to be installed for
claim gen storage.
