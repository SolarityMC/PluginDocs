---
id: economy
title: Economy
sidebar_position: 2
---

The Money Earned board counts only money the server pays for items, never money between players. Only
payouts from a plugin listed in the board's `sources` count.

## SolarityEconomy (preferred)

SolarityEconomy 1.1.0 or newer reports every deposit with the plugin that made it. Only plugin deposits
from a listed source count, so `/pay` and `/eco give` never do.

## EssentialsX

Used when SolarityEconomy isn't installed. EssentialsX's own `/sell` counts when `Essentials` is in
`sources`. A payment a plugin makes through Vault counts when that plugin is in `sources`. `/pay`,
`/eco` and anything else never count.

## Default sources

| Source | What it covers |
|---|---|
| `ShopGUIPlus` | `/shop`, `/sell` and `/sellgui` |
| `ShopGUIPlus-SellGUI` | Its `/sellgui` menu, if it ever pays on its own |
| `SolarityGens` | `/autosell` and claim gen sales |
| `Essentials` | EssentialsX's `/sell` (`worth.yml` prices) |

Add any other plugin by its plugin name. If neither economy is hooked while a Money Earned board is on,
the console warns at startup and the board stays at zero.
