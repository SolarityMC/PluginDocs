---
id: quick-start
title: Quick Start
sidebar_position: 3
---

This gets a player from nothing to a selling claim gen.

## 1. Claims and the claim world

Claims come from [LandClaim](../integrations/landclaim.md) (26.11.0 or newer, with WorldGuard).
`claimgens.yml` puts starter claims in `claims.world` (default `world`) on a grid starting at
`claims.grid.origin-x` / `origin-z` (default 20000, 20000). Change these if that area is not where
starter claims should go, then `/gens reload`.

To try SolarityGens without LandClaim, set `claims.provider: dev` and `claims.dev.enabled: true` and
restart. Dev claims protect nothing; see [Claims & Slots](../features-modules/claims-and-slots.md).

## 2. Make sure there is an economy

Claim gens sell through Vault. Install Vault (VaultUnlocked on Folia) and an economy plugin.

## 3. Start

A player runs:

```
/gens start
```

They get a 15x15 claim, one Oak Log generator item, and a teleport to the claim centre. `/gens start`
works once per player; `/gens home` takes them back later.

## 4. Place, wait, sell

1. Place the generator inside the claim. A line of floating text above it shows its level and
   how much it holds.
2. Wait. At level 1 it makes one log every 10 seconds, up to 180.
3. Right-click it and click **Collect and Sell**. The money goes straight to the player.

## 5. Grow

- **Upgrade Level** in the same menu makes the gen faster, holds more and sells for more.
- `/gens` opens the shop. The next tier (Coal) unlocks once an Oak Log gen reaches level 3 and the
  player has $2,200.
- `/gens expand` grows the claim for more gen slots.

Next: [Commands & Permissions](../core-reference/commands-permissions.md).
