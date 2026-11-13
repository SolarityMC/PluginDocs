---
id: installation
title: Installation
sidebar_position: 2
---

1. Check the [Requirements](requirements.md): Java 25, Paper or Folia 26.2 or 26.3, WorldGuard and WorldEdit
   (FastAsyncWorldEdit-Folia on Folia).
2. Build the jar with `mvn clean package` (it lands in `target/`) or take it from a release, and drop
   it into `plugins/`.
3. Start the server. LandClaim creates:
   - `plugins/LandClaim/config.yml`: claim sizes, borders, timers, the economy, tiers and BlueMap.
   - `plugins/LandClaim/lang/lang.yml`: every chat message, in MiniMessage format.
   - `plugins/LandClaim/citybanks/`: one file per City bank, created the first time a bank is used.
4. Give your players permissions (see [Quick Start](quick-start.md#2-give-players-permission-to-claim)).
5. After editing a file, run `/lc reload` (permission `landclaim.reload`).

## Verifying it's working

Run `/lc` in-game. The LandClaim main menu opens with the claim wand, the how-to-claim book and
the Claims button. If nothing happens, check the console for WorldGuard or WorldEdit errors;
LandClaim needs both to enable.

## Updating

Replace the jar and restart. Nothing needs migrating:

- On start, settings and messages that are new in this version are added to your `config.yml` and
  `lang.yml` with their default values and comments. Values you already have are never changed, and
  a file is only rewritten when something was added (the console says how many). Rewriting puts the
  file in standard YAML layout, so a one-line entry like `Village: { Min: 4, Max: 6 }` comes back as
  two nested lines with the same values.
- On every start, claims made before the default member lock-out existed get it added (`interact` and
  `use` denied for non-members). Claims whose owner already set those flags are left as they are. The
  console reports how many claims were updated.

## Uninstalling

Remove the jar and restart. Your claims are WorldGuard regions and stay in WorldGuard's region files,
with their owners, members and flags. The `plugins/LandClaim/` folder (config, messages and city
bank balances) stays on disk until you delete it.
