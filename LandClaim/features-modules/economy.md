---
id: economy
title: Economy
sidebar_position: 5
---

With Vault and an economy plugin installed, claiming land costs money once a player has used up a
free allowance. Without an economy plugin, or with `Economy.Enabled: false`, claiming is free.

## What gets charged

Only new blocks are charged: the whole area for a new claim, and only the added area for a resize.
Area means length × width; height doesn't count. Shrinking a claim is free and refunds nothing.

The added blocks are paid for in this order:

1. **Your free allowance.** Every player can claim `Economy.FreeBlocksPerPlayer` blocks (default
   500) in total for free, counted across every claim they own.
2. **Your members' free allowance.** When resizing, members and officers of that claim who have
   unused allowance chip in. Each one is listed in chat: *120 block(s) pooled from Steve's free allowance.*
   Pooled blocks are given for good: they count against that member's own allowance for as long as
   the claim exists, even if they leave it, so the same blocks can't be pooled twice.
3. **Money**, for whatever is left:

```
price = blocks left × Economy.PricePerBlock × (1 − discount)
discount = members × Economy.MemberDiscountPerMember, capped at Economy.MaxDiscount
```

"Members" here means the claim's members and officers, not its owners. With the defaults (0.75 per
block, 10% per member, at most 90%), a claim with 3 members pays 0.525 per block.

Resizing a [City](tiers.md) claim is always free.

## When it is charged

For a new claim, the money is taken when you click confirm in the claim menu; for a resize, when you
run `/lc resize`. If you can't afford it you are told how much you are missing, and nothing is
claimed or changed.

## Settings

```yaml
Economy:
  Enabled: true
  FreeBlocksPerPlayer: 500
  PricePerBlock: 0.75
  MemberDiscountPerMember: 0.10
  MaxDiscount: 0.90
```

The City bank also uses Vault; see [Tiers](tiers.md#city-bank-city). Messages are in the `economy`
section of `lang.yml`.
