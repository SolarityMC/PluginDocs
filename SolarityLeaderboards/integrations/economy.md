---
id: economy
title: Economy
sidebar_position: 2
---

The baltop board reads balances from the source in `boards.baltop.source`:

| Source | How it works |
|---|---|
| `auto` (default) | SolarityEconomy when it is installed, Vault otherwise |
| `vault` | Any economy plugin registered with Vault (EssentialsX, VaultUnlocked providers) |
| `solarityeconomy` | SolarityEconomy's own list of every balance |

## Vault

Vault can only read one player at a time, so each online player's balance is read on every refresh,
and on join and quit. It is saved in `stats.yml`, so an offline player shows the balance they had
when they were last online, and the board survives restarts. A player who hasn't been online since
the plugin was installed isn't on the board yet.

## SolarityEconomy

SolarityEconomy lists every balance at once, so offline players are always up to date. If it is
installed but its balances can't be read, the console says so once and `auto` falls back to Vault.

The console's `Baltop` line shows which source is in use (`no economy yet` when neither is there).
