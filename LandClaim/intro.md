---
id: intro
title: Introduction
sidebar_position: 1
---

LandClaim is a land claiming plugin for **Paper** and **Folia** 26.2 and 26.3. Players select
an area with the WorldEdit wand, claim it with one command, and run everything else from in-game
menus: who is in the claim and at what rank, the claim's WorldGuard flags, a claim spawn and more.
Claims are ordinary WorldGuard regions, so WorldGuard does all the protecting and every WorldGuard
tool keeps working on them.

Claims grow with their community. The more players a claim has, the higher its tier, and each tier
unlocks something new: a village tag, a claim spawn, a town chat channel and a shared city bank.

## What's in this guide

- **[Getting Started](getting-started/quick-start.md)**: requirements, installation and a first claim in a few minutes.
- **[Core Reference](core-reference/commands-permissions.md)**: every command and permission, and every menu.
- **[Features](features-modules/claiming.md)**: claiming and resizing, ranks, invites and join requests, tiers, the economy, borders, flags and chat prompts.
- **[Configuration](configuration/main-configuration.md)**: every `config.yml` option and the message file.
- **[Integrations](integrations/worldguard-worldedit.md)**: WorldGuard and WorldEdit, Vault, BlueMap, ClearLaggEnhanced and the developer API.
- **[Advanced](advanced-optimization/folia-support.md)**: Folia details and troubleshooting.
- **[Support](support/faq.md)**: FAQ and common issues.

## Key features

- **Claims are WorldGuard regions**: protection, flags and `/rg` all work as usual, and non-members are locked out of doors, buttons and containers from the moment a claim is made.
- **Three ranks**: Owner, Officer and Member, with promote and demote buttons in the claim menu and a broadcast to the whole claim on every change.
- **Invites and join requests**: players are invited and accept with one click, or stand in a claim and ask to join it with `/lc requestjoin`.
- **Tiers that unlock features**: Settlement, Village, Town and City, based on how many players a claim has.
- **Fair claim pricing**: a free block allowance per player, unused allowance pooled from members, and a discount for every member.
- **Client-side claim borders** when you walk into a claim, and `/lc nearby` to find claims around you.
- **BlueMap markers** coloured by tier, with owner, member count and village tag.
- **ClearLaggEnhanced support**: its clears leave peaceful mobs inside claims alone.
- **Native Folia support**: every claim edit runs on the right region thread.

Ready to go? Start with the **[Quick Start](getting-started/quick-start.md)** guide.
