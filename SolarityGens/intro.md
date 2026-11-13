---
id: intro
title: Introduction
sidebar_position: 1
---

SolarityGens is the generator plugin behind Solarity's GenSMP, for **Paper** and **Folia** 26.3. It
was called DytchsGens until version 26.11.0 and upgrades from it in place.

It runs two kinds of generator side by side:

- **Claim gens**, the main mode. Players own them and place them inside their claim. They produce
  over time into a stored count, and the owner collects and sells, upgrades them and unlocks the
  next tier in the `/gens` shop. Nothing ticks: output is worked out from the clock when a gen is
  looked at, so a thousand gens cost the server nothing between clicks.
- **Click-to-mine gens**, for the warzone. Public blocks that every player mines on their own (the
  real block never breaks), with auto pickup, smelt, block and sell, and personal booster vouchers.

## What's in this guide

- **[Getting Started](getting-started/quick-start.md)**: requirements, installation, upgrading from DytchsGens and a first claim gen.
- **[Core Reference](core-reference/commands-permissions.md)**: every command, permission, placeholder and menu.
- **[Features](features-modules/claim-gens.md)**: claim gens, the unlock shop, claims and slots, boosters, click-to-mine gens and the utility menus.
- **[Configuration](configuration/claim-gens-configuration.md)**: `claimgens.yml`, `config.yml` and messages.
- **[Integrations](integrations/vault.md)**: Vault, PlaceholderAPI, ShopGUIPlus, WorldGuard and PacketEvents, and the developer API.
- **[Advanced](advanced-optimization/folia-support.md)**: Folia, data storage and troubleshooting.
- **[Support](support/faq.md)**: FAQ and common issues.

## Key features

- **Passive claim gens** with levels (speed, storage, sell price) and a 9-tier ladder from oak logs to emeralds.
- **A slow economy by design**: storage holds 30 minutes of output, so grinding never beats collecting every half hour.
- **An unlock shop** where each tier needs money and the previous tier's gen at level 3.
- **Gen slots from claim size**, with `/gens expand` to grow the claim.
- **A server-wide sell booster** for store purchases, capped and queued, that survives restarts.
- **Dupe-proof**: every gen has its own id, collect and sell is atomic, and copied items are refused.
- **Native Folia support**, with every disk write off the game threads.

Ready to go? Start with the **[Quick Start](getting-started/quick-start.md)** guide.
