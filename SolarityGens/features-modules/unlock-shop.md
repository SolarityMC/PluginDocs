---
id: unlock-shop
title: Unlock Shop
sidebar_position: 2
---

`/gens` opens the generator shop ([menu layout](../core-reference/menus.md#generator-shop)).

## Unlocking a tier

Each type has an `unlock-cost` and usually a `requires` entry: a type and level the player must
already own. The default ladder needs the previous tier's gen at level 3:

| Tier | Type | Sells for | Unlock cost | Extra gens |
|---|---|---|---|---|
| 1 | Oak Log (starter) | $1 | free | $500 |
| 2 | Coal | $2 | $2,200 | $1,000 |
| 3 | Iron | $4 | $4,300 | $2,000 |
| 4 | Gold | $8 | $13,000 | $4,000 |
| 5 | Redstone | $16 | $57,600 | $8,000 |
| 6 | Lapis | $32 | $184,300 | $16,000 |
| 7 | Nether Quartz | $64 | $806,400 | $32,000 |
| 8 | Diamond | $128 | $2,534,400 | $64,000 |
| 9 | Emerald | $256 | $7,741,400 | $128,000 |

The requirement counts any gen the player owns of that type, placed or held as an item. Unlocking
charges the cost and gives one gen of the new type. It never replaces or touches an existing gen.

## Buying more gens

Once a type is unlocked, clicking it again buys another gen of that type for its `buy-price`. A type
with `buy-price: -1` can't be bought again.

The default `buy-price` is 500 times the sell price, so an extra gen pays for itself in about 40
minutes of its own level 3 output. Unlocking is the expensive step; filling your slots with the new
tier is meant to be cheap.

## Pacing

The defaults aim for the first tier-up after about an hour of play, tier 5 after about six hours and
the top tier after about 42. Every price is in `claimgens.yml`, and `/gens reload` applies changes.
