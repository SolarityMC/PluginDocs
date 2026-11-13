---
id: shopguiplus
title: ShopGUIPlus
sidebar_position: 3
---

ShopGUIPlus is used for click-to-mine gens only:

- **`/autosell` prices.** Each drop is priced with ShopGUIPlus's sell price for that player and paid
  through [Vault](vault.md). Items ShopGUIPlus has no price for go to the inventory.
- **Sell vouchers on manual sells.** A player's active sell voucher also multiplies their sells in the
  ShopGUIPlus shop (`SELL` and `SELL_ALL`).

Both are reached by reflection, so there is no build dependency and nothing breaks without it.

Claim gens never use ShopGUIPlus: their prices are in `claimgens.yml`, so a shop price change can't
upset the claim gen economy.
