---
id: developer-api
title: Developer API
sidebar_position: 5
---

LandClaim offers two services to other plugins:

- **`LandClaimApi`**, one read-only check: may this player take a mob from this spot? SlimeFunCore
  and AnoModules use it.
- **`LandClaimApiV2`** (from 26.11.0), which adds claim reads, creating, resizing and deleting
  claims, flags, temporary flags and claim events. SolarityGens uses it to run its own claim rules.

`LandClaimApiV2` extends `LandClaimApi`, and `LandClaimApi` hasn't changed: plugins that use it keep
working without a rebuild.

## Dependency

```xml
<repository>
    <id>busybee</id>
    <url>https://repo.busybeedev.net/private-releases</url>
</repository>

<dependency>
    <groupId>dev.mrtroxy</groupId>
    <artifactId>landclaim</artifactId>
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

`LandClaimApi` needs 26.9.2 or newer, `LandClaimApiV2` 26.11.0 or newer. The repository is private
and needs BusyBee credentials (a `busybee` server in your Maven `settings.xml`). Add `LandClaim` to your plugin's `softdepend`, and never shade LandClaim
into your jar.

Look a service up each time you use it rather than keeping it, and keep every reference to the API
inside your optional LandClaim hook, so your plugin still loads without LandClaim.

## Capture check (`LandClaimApi`)

```java
LandClaimApi api = Bukkit.getServicesManager().load(LandClaimApi.class);
if (api != null) {
    ClaimDecision decision = api.checkCapture(player, mob.getLocation());
}
```

| `ClaimDecision` | Meaning                                                                                 |
|-----------------|-----------------------------------------------------------------------------------------|
| `ALLOWED`       | The player is an owner or member of every claim at that spot, or has `landclaim.bypass` |
| `DENIED`        | At least one claim at that spot doesn't include the player                              |
| `NOT_CLAIMED`   | No claim covers that spot                                                               |
| `UNAVAILABLE`   | LandClaim couldn't decide safely. **Treat it as a denial.**                             |

- Call it on the region thread that owns both the player and the location. A call from any other
  thread returns `UNAVAILABLE`.
- It only reads WorldGuard's region index: no chunk loads, disk access, scheduling or changes.
- Capture is stricter than visiting. Public `build`, `use` or `interact` flags don't let outsiders
  capture. Every overlapping claim has to include the player, whatever its priority.
- The answer covers LandClaim only. `ALLOWED` and `NOT_CLAIMED` don't override WorldGuard flags or
  other protection plugins; check those as well.
- Errors are logged at most once a minute and answered with `UNAVAILABLE`.

## Claims (`LandClaimApiV2`)

```java
LandClaimApiV2 api = Bukkit.getServicesManager().load(LandClaimApiV2.class);
if (api == null) return; // LandClaim missing or older than 26.11.0

api.createClaim(player.getUniqueId(), world, 100, 100, 114, 114, "starter_" + player.getName())
    .thenAccept(result -> {
        if (result.isSuccess()) {
            ClaimInfo claim = result.value().orElseThrow();
            // claim.id() is stable: store it rather than the name
        } else {
            player.sendMessage("Could not claim: " + result.message()); // result.failure() says why
        }
    });
```

A claim here is a region LandClaim marks as a claim. Plots are never returned or changed; a spot
inside a plot belongs to the claim around it.

### Reads

Callable from any thread. They read WorldGuard's region index and never load chunks, touch disk or
schedule work.

| Method | Returns |
|---|---|
| `claimAt(Location)` | The claim covering the spot |
| `claimsOf(UUID owner)` | Every claim the player owns, in every loaded world |
| `claim(String world, String regionId)` | A claim by name |
| `claim(UUID claimId)` | A claim by its stable id |
| `isMember(world, regionId, player)` | Owner, officer or member |
| `roleOf(world, regionId, player)` | `ClaimRank` `OWNER`, `OFFICER` or `MEMBER` |
| `temporaryFlagExpiry(world, regionId, flag)` | When a temporary flag runs out |

`ClaimInfo` is a snapshot: `id`, `world`, `regionId`, `owner` (the first owner), `owners`,
`officers`, `members` (plain members only), `minX`, `minZ`, `maxX`, `maxZ` (inclusive) and `tier`
(1 Settlement to 4 City). It doesn't change when the claim does; read it again for fresh data.

### Changes

Callable from any thread. Each one runs on the region thread that owns the claim's center chunk and
returns a `CompletableFuture` completed there. A future never fails: a refusal is a `Result` with a
`Failure` and a message.

| Method | Does |
|---|---|
| `createClaim(owner, world, minX, minZ, maxX, maxZ, name)` | Makes a claim covering the full height of the world, with the owner as its only owner and the usual new-claim defaults |
| `resizeClaim(world, regionId, minX, minZ, maxX, maxZ)` | Moves the claim's corners; keeps its id, name, players, flags and claim spawn |
| `deleteClaim(world, regionId)` | Deletes the claim and its plots. A City bank balance is split between the owners |
| `setFlag(world, regionId, flag, value)` | Sets a state flag (`allow`/`deny`) or text flag for everyone; `null` removes it |
| `setTemporaryFlag(world, regionId, flag, value, duration)` | Sets a flag for up to 7 days, then puts back what it was |
| `clearTemporaryFlag(world, regionId, flag)` | Ends a temporary flag now |
| `safeSpawn(world, regionId)` | The claim spawn, or the highest safe block near the claim's center |

Changes skip LandClaim's permissions, menus, prompts and economy. Your plugin decides who may do
what and charges for it. They still follow the claim rules:

| `Failure` | When |
|---|---|
| `OVERLAP` | The area overlaps any other WorldGuard region, including the owner's own claims |
| `TOO_SMALL`, `TOO_LARGE`, `RATIO` | Outside `Claims.Regions.MinSize`, `MaxSize` or `MaxLWRatio` |
| `INVALID_NAME`, `NAME_TAKEN` | Not a valid region name, or the world already has one by that name |
| `NOT_FOUND` | No claim by that name |
| `WORLD_NOT_ALLOWED` | The world isn't listed in `Api.Worlds` (an empty list allows every world) |
| `PLOTS_OUTSIDE` | A resize would leave one of the claim's plots outside it |
| `INVALID_FLAG`, `INVALID_VALUE`, `UNSUPPORTED_FLAG` | Unknown flag, a value that doesn't fit, or a flag that isn't a state or text flag |
| `INVALID_DURATION`, `NO_TEMPORARY_FLAG` | A temporary flag of 0 or over 7 days, or nothing to end |
| `UNAVAILABLE` | LandClaim couldn't complete the change safely; the reason is logged |

### Temporary flags

A temporary flag is saved on the claim with its expiry and what to put back, so it reverts on time
across `/lc reload` and restarts. One that ran out while the server was off reverts while LandClaim
starts, before players can join. Setting it again while it runs keeps the original value and
replaces the temporary value and the expiry. `setFlag` on a flag with a temporary value changes what
it goes back to instead. Players can't change it in the Flag Editor while it runs.

```java
api.setTemporaryFlag("world", claimId, "pvp", "allow", Duration.ofMinutes(10)); // a raid opens
api.clearTemporaryFlag("world", claimId, "pvp");                                // the raid ended early
```

### Events

| Event | Fired when |
|---|---|
| `ClaimCreateEvent` | A claim is created |
| `ClaimResizeEvent` | A claim's corners change (`getPrevious()` has the old area) |
| `ClaimDeleteEvent` | A claim is deleted (`getClaim()` is the claim as it was) |
| `ClaimMemberChangeEvent` | A member or officer joins, leaves or changes rank |
| `ClaimOwnerChangeEvent` | Someone becomes an owner or stops being one |

They are in `dev.mrtroxy.landclaim.api.event`, report changes that already happened (they can't be
cancelled), and are fired on the region thread that owns the claim's center chunk. `getCause()` is
`API` or `PLAYER`, and `getActor()` the player who made the change. Changes made through API calls,
`/lc` commands, menus, invites and join requests all fire them; changes made directly with `/rg` and
anything about plots don't.
