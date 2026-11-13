---
id: troubleshooting
title: Troubleshooting
sidebar_position: 3
---

## The startup block says "Storage YAML (claim gen database failed, see above)"

`claimgens.db` could not be opened or read. The error above it says why (a locked or damaged file, or a
database from a newer SolarityGens). Click-to-mine gens still work; claim gen commands answer "Claim gens
are off right now". Nothing in the database is changed, so restore or fix the file and restart.

## SolarityGens disabled itself on the first start

The copy from `plugins/DytchsGens/` failed (the console says why, usually folder permissions). Nothing
was written. Fix it, or copy the files into `plugins/SolarityGens/` by hand, and restart.

## "Couldn't set up your claim"

`/gens start` couldn't create the claim. The reason is in the message. Common ones:

- `claims.world` names a world that isn't loaded.
- LandClaim is missing or older than 26.11.0, and dev claims are off. The console says which at startup.
- "LandClaim doesn't allow plugin claims in that world": add the world to `Api.Worlds` in LandClaim's
  `config.yml`, or leave that list empty.
- "it would overlap another claim or protected area": the next 20 grid cells were all taken by other
  regions. Move `claims.grid.origin-x` / `origin-z` somewhere free.

## Nothing can be bought or sold

Vault has no economy registered. The console says "Vault has no economy provider" once. Install an
economy plugin (and VaultUnlocked on Folia).

## Holograms are missing or doubled

Holograms come back when their chunk loads and refresh every `hologram.update-seconds`. A copy left
by a plugin reload is removed on the next refresh. If an entity clearer removes them, set it to skip
entities tagged `solaritygens:hologram`.

## A copied item or a "isn't recognised" message

That is the dupe protection working. `/gens admin audit <player>` shows the refused attempt.
