---
id: vault
title: Vault
sidebar_position: 1
---

All money goes through Vault (VaultUnlocked on Folia) and whatever economy plugin is registered with
it, such as SolarityEconomy or EssentialsX. SolarityGens reaches Vault by reflection, so it builds and
loads without it.

What uses it:

- Claim gens: Collect and Sell, Pick Up (it sells what is stored), Upgrade, the shop and `/gens expand`.
- Click-to-mine gens: `/autosell` payouts.

The economy is looked up the first time money moves, not at startup, so it doesn't matter which plugin
enables first. If no economy is registered, the console warns once and nothing can be bought or sold.

A payout the economy refuses (Vault reports `transactionSuccess() == false`) is undone: claim gen
output goes back into the gen, and autosold drops go to the inventory instead. A purchase is only made
after the money was taken; if the gen changed meanwhile (a second click), the money is refunded.
