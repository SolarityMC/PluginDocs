---
id: vault
title: Vault
sidebar_position: 2
---

Vault is optional. With Vault and an economy plugin (EssentialsX, CMI and so on), LandClaim:

- charges for claimed land beyond the free allowance (see [Economy](../features-modules/economy.md)), and
- runs the City bank (see [Tiers](../features-modules/tiers.md#city-bank-city)).

LandClaim looks for Vault's economy service, so Vault-compatible forks work too. If the economy plugin
loads after LandClaim, LandClaim tries again one tick later.

## Without an economy plugin

Claiming and resizing are free, whatever `Economy.Enabled` says, and amounts in messages are shown
as plain numbers (`$1,234.00`). The City bank can't be used: deposits are refused, so banks stay empty.
