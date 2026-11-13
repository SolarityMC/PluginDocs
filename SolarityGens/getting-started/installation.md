---
id: installation
title: Installation
sidebar_position: 2
---

1. Check the [Requirements](requirements.md): Java 25 and Paper or Folia 26.3.
2. Build the jar with `mvn clean package` (it lands in `target/` as `SolarityGens-<version>.jar`;
   `fun.solaritymc:solarity-common` must be in the local Maven repo, `mvn install` it first) or take
   it from a release, and drop it into `plugins/`.
3. Start the server. SolarityGens creates:
   - `plugins/SolarityGens/config.yml`: click-to-mine gen types, auto features, booster vouchers and messages.
   - `plugins/SolarityGens/claimgens.yml`: claim gen levels, types, prices, claim sizes and the server booster.
   - `plugins/SolarityGens/claimgens.db`: claim gens, unlocks, player progress, dev claims and the audit log (SQLite).
4. After editing a file, run `/gens reload` (permission `solaritygens.admin`).

## Verifying it's working

The console prints one block when the plugin is ready:

```
[SolarityGens] SolarityGens v26.11.0 on Folia
[SolarityGens]   Storage  SQLite + YAML
[SolarityGens]   Gens     9 claim types, 32 click-to-mine types
[SolarityGens]   Placed   0 claim, 0 click-to-mine
[SolarityGens]   Claims   dev (test claims)
[SolarityGens]   Hooks    Vault, PlaceholderAPI
[SolarityGens]   Ready in 120ms
```

In game, `/gens` opens the generator shop.

## Upgrading from DytchsGens

Remove `DytchsGens.jar`, add `SolarityGens-<version>.jar` and restart. Nothing else is needed:

- On the first start, everything in `plugins/DytchsGens/` is copied to `plugins/SolarityGens/`. Files
  that already exist there are never overwritten, and the old folder is left as it was (with a
  `COPIED-TO-SOLARITYGENS.txt` note) as a backup. The startup block says how many files were copied.
  If the copy fails, SolarityGens turns itself off rather than start with empty files.
- Gen items and booster vouchers players already have keep working.
- `/dytchsgens`, `/dgens`, `/dytchgens` and `/gens` still work, and so does every `dytchsgens.*`
  permission (each one passes its value on to the matching `solaritygens.*` node).
- `%dytchsgens_*%` placeholders keep working next to the new `%solaritygens_*%` ones.
- Plugins built against the old API package (`gg.dytch.gens.api`) need updating to
  `fun.solaritymc.solaritygens.api`; see the [Developer API](../integrations/developer-api.md).

## Updating

Replace the jar and restart. The claim gen database upgrades its own schema; a database from a
newer SolarityGens than the jar is refused (claim gens stay off and nothing is changed) instead of
being damaged.
