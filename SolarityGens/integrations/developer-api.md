---
id: developer-api
title: Developer API
sidebar_position: 6
---

The API is in `fun.solaritymc.solaritygens.api`. It moved there from `gg.dytch.gens.api` in 26.11.0, and
the plugin is now named `SolarityGens`; update `softdepend` and any `isPluginEnabled("DytchsGens")` check.

## Dependency

SolarityGens is published to the private BusyBee repository, which needs a token in
`~/.m2/settings.xml` (server id `busybee`). Without one, `mvn install` SolarityGens to your local
Maven repository instead.

```xml
<repository>
    <id>busybee</id>
    <url>https://repo.busybeedev.net/private-releases</url>
</repository>

<dependency>
    <groupId>fun.solaritymc.solaritygens</groupId>
    <artifactId>SolarityGens</artifactId>
    <version>26.11.0</version>
    <scope>provided</scope>
    <exclusions>
        <exclusion>
            <groupId>*</groupId>
            <artifactId>*</artifactId>
        </exclusion>
    </exclusions>
</dependency>
```

Add `SolarityGens` to `softdepend` in your `plugin.yml`, check
`Bukkit.getPluginManager().isPluginEnabled("SolarityGens")` before touching the API, and keep the API
references in a class you only load when it is enabled.

## GensStatsAPI

Static and null-safe: every method returns zero or empty while SolarityGens isn't enabled.

| Method | Returns |
|---|---|
| `isAvailable()` | True once SolarityGens has enabled |
| `mined(UUID)` | Lifetime click-to-mine gens mined |
| `all()` | Every player's mined total, as an unmodifiable snapshot |
| `nameOf(UUID)` | The last name SolarityGens saw, or `Unknown` |
| `trackedPlayers()` | Players with a mined count |
| `collected(UUID)` | Lifetime items collected and sold from claim gens |
| `sold(UUID)` | Lifetime money made from claim gen sales |
| `allCollected()` | Every player's claim gen items sold, as an unmodifiable snapshot |
| `allSold()` | Every player's claim gen sale money, as an unmodifiable snapshot |

```java
long mined = GensStatsAPI.mined(player.getUniqueId());
long collected = GensStatsAPI.collected(player.getUniqueId());
```

## GeneratorBreakEvent

Fired after a player breaks a click-to-mine gen (drops already handled, mined count already
increased). The vanilla `BlockBreakEvent` for gens is cancelled, so listen to this instead.

| Method | Returns |
|---|---|
| `getPlayer()` | Who broke it |
| `getGeneratorId()` | The gen type id from `config.yml` |
| `getLocation()` | The gen's block |

It fires on the player's region thread.
