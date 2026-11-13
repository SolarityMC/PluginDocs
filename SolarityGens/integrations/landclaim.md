---
id: landclaim
title: LandClaim
sidebar_position: 5
---

With `claims.provider: landclaim` (the default), claim gens live in LandClaim claims. LandClaim
26.11.0 or newer is needed (its API v2), with WorldGuard and FAWE.

## Who does what

- **SolarityGens** owns the season rules: it creates each player's starter claim on the grid with
  `/gens start`, grows it with `/gens expand` and charges for it. LandClaim's own claim prices are
  not used for these.
- **LandClaim** stores the claims, protects them, and keeps their owners, officers and members.
  Invites, join requests, `/lc leave` and the flag editor work as usual.

Owners, officers and members of a claim can all place gens in it. Each gen still belongs to the player
who placed it: only they can collect, sell, upgrade or pick it up.

## New claims

A claim made by `/gens start` is named after the player (`claims.landclaim.name`, default
`%player%`) and gets the flags in `claims.landclaim.flags` (default `pvp: deny`). It is a normal
LandClaim claim, so `/lc` shows it.

## Permissions to take away from players

SolarityGens is the only thing that should size claims during the season. In LuckPerms, take these away
from the default group (they are part of `landclaim.basic`):

| Node | Why |
|---|---|
| `landclaim.claimregion` | Players would make claims outside the grid, for free |
| `landclaim.resize` | `/lc resize` would grow claims without `/gens expand` |
| `landclaim.flag.pvp` | Owners could turn PvP on in their claim |

## Claims deleted or left

When a claim is deleted (`/lc delete`, an admin, or another plugin), every gen in it goes back to its
owner as an item and what it had stored is sold to them. A player who leaves a claim or is removed from
it gets their own gens back the same way. Offline owners are paid at once and get the items when they
next join. See [Claims & Slots](../features-modules/claims-and-slots.md#when-a-claim-is-deleted-or-someone-leaves).

Changes made straight through WorldGuard (`/rg remove`, `/rg removemember`) aren't reported by
LandClaim, so gens are not handed back for those. Use `/lc` instead.

## LandClaim settings

- `Api.Worlds` in LandClaim's `config.yml` must include `claims.world`, or be empty (every world).
- A claim resized by staff with `/lc resize` keeps its gens. Gens left outside the new area keep
  working for their owner.
