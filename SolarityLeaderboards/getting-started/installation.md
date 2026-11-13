---
id: installation
title: Installation
sidebar_position: 2
---

1. Check the [Requirements](requirements.md): Java 25 and Paper or Folia 26.3.
2. Build the jar with `mvn clean package` (it lands in `target/` as `SolarityLeaderboards-<version>.jar`)
   or take it from a release, and drop it into `plugins/`.
3. Start the server. SolarityLeaderboards creates `plugins/SolarityLeaderboards/config.yml`, and
   `stats.yml` once the first player is counted.
4. After editing `config.yml`, run `/leaderboards reload` (permission `solarityleaderboards.admin`).

## Verifying it's working

The console prints one block when the plugin is ready:

```
[SolarityLeaderboards] SolarityLeaderboards v26.11.0 on Folia
[SolarityLeaderboards]   Players  3 tracked
[SolarityLeaderboards]   Boards   kills, deaths, blocks, sold, baltop, playtime
[SolarityLeaderboards]   Baltop   Vault
[SolarityLeaderboards]   Hooks    SolarityGens, Vault, PlaceholderAPI
[SolarityLeaderboards]   Ready in 12ms
```

In game, `/leaderboards` opens the hub.

## Upgrading from 2.0.0

Replace `SolarityLeaderboards-2.0.0.jar` with the new jar and restart. Nothing else is needed:

- `config.yml` and `stats.yml` are read as they are and never rewritten on startup.
- The command, its aliases, both permissions and every placeholder keep their names.
- The new **Gens Sold** board uses built-in defaults (hub slot 14) when `config.yml` has no `sold`
  section. Add one to change it (see [Configuration](../configuration/configuration.md)).
- The blocks board now reads SolarityGens instead of DytchsGens. SolarityGens 26.11.0 or newer is
  needed for gen blocks to count.
- Baltop now works with Vault too. Players appear on it once they have been online with the new jar.
