---
id: data-storage
title: Data & Storage
sidebar_position: 2
---

Everything lives in `plugins/SolarityGens/`.

| File | Holds |
|---|---|
| `claimgens.db` | SQLite: claim gens, unlocks, player progress (started, collected, sold), gens waiting to be handed back, dev claims, the server booster queue, and the audit log |
| `gens.yml` | Placed click-to-mine gens (`world,x,y,z|type`) |
| `players.yml` | Auto-feature toggles that differ from the default |
| `boosters.yml` | Active booster vouchers per player |
| `minedstats.yml` | Lifetime click-to-mine gens mined per player |

## Claim gens

Every change (placing, selling, upgrading, picking up, unlocking) is written to `claimgens.db` straight
away by a background thread, so a crash loses nothing that was paid for. On shutdown the plugin waits
for queued writes before closing. The database has a schema version; a database from a newer
SolarityGens is refused rather than changed.

A gen item only carries its gen's id. The database says what the gen is, so an item copied by a glitch
can't become a second gen: placing it is refused because the gen is already placed, and an id the
server never made is refused as unknown.

## Audit log

Sales, upgrades, unlocks, purchases, pickups, placements, refused (copied or forged) items, admin
gives and resets, expansions, server boosters and gens taken out of deleted or left claims
(`claim_deleted`, `left_claim`, `returned`) are written to the `audit` table. `/gens admin audit
<player>` shows a player's newest 15 entries; any SQLite tool can read the rest.

## Safety for hand-edited files

If a YAML data file can't be read, it is copied to `<name>.broken-<time>` before the plugin carries on
with an empty one, so the next save can't wipe it. Fix the copy and put it back while the server is
stopped. Placed gens in a world that isn't loaded yet are kept in `gens.yml` and go live when the world
loads.
