---
id: worldguard-worldedit
title: WorldGuard & WorldEdit
sidebar_position: 1
---

Both are required. LandClaim adds claiming, ranks and menus on top of them; WorldGuard does the
protecting.

## WorldEdit

Players select a claim with WorldEdit's wand: left-click one corner, right-click the other. `/lc wand`
hands out a wooden axe, WorldEdit's default wand item. If you changed `wand-item` in WorldEdit's
config, players need that item instead.

On Folia, use [FastAsyncWorldEdit-Folia](https://github.com/ANO-Development/FastAsyncWorldEdit-Folia).
It provides WorldEdit, so nothing else is needed.

## WorldGuard

Every claim is a WorldGuard region, so:

- Protection inside a claim is WorldGuard's: members build, others don't, and flags decide the rest.
- `/rg info`, `/rg flag`, `/rg addmember` and the rest work on claims. Changes made that way show up in
  LandClaim straight away.
- WorldGuard's own bypass (`worldguard.region.bypass.*`) lets staff build in claims. LandClaim's
  permissions never override WorldGuard or another plugin's protection.

### Flags LandClaim registers

| Flag | Values | Purpose |
|---|---|---|
| `land-claim-region` | `region` or `plot` | Marks a region as a claim. Regions without it are left alone. |
| `land-claim-village-tag` | text | The [village tag](../features-modules/tiers.md#village-tag-village) |
| `land-claim-officers` | list of UUIDs | Which members are [officers](../features-modules/ranks.md#how-ranks-are-stored) |
| `land-claim-pooled` | list of `uuid:blocks` | Free blocks members have [pooled](../features-modules/economy.md) into this claim |
| `land-claim-plot-of` | region id | On a [plot](../features-modules/claiming.md#plots): the claim it belongs to |
| `land-claim-plot-staff` | list of UUIDs | On a plot: which members are there only because they run its claim |

They are registered when the server loads plugins. If another plugin already registered a flag
with the same name, LandClaim uses that one.

### Things to know

- `/lc claim` refuses an area that overlaps **any** region the player doesn't own, including spawn and
  other server regions. That is how you keep areas unclaimable: cover them with a region.
- **Your Claims** lists every region a player owns, including regions an admin made for them with `/rg`.
- Removing a player with `/rg removemember` leaves their UUID in `land-claim-officers`. It does
  nothing there, and it is cleaned up the next time that player's rank changes in LandClaim.
