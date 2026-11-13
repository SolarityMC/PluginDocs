---
id: faq
title: FAQ
sidebar_position: 1
---

## Why isn't a player on baltop?

With Vault, a balance is only known once the player has been online with this version. See
[Economy](../integrations/economy.md).

## Why is the gens sold board empty?

SolarityGens 26.11.0 or newer isn't installed, or nobody has sold claim gen output yet. See
[SolarityGens](../integrations/solaritygens.md).

## A number changed but the board didn't

The boards re-rank every `refresh-seconds` (60). `/leaderboards reload` re-ranks at once.

## Do gen blocks count twice on the blocks board?

No. SolarityGens cancels the vanilla break for its gens, and the plugin only counts breaks that
weren't cancelled. The gens are added once, from SolarityGens' own count.

## Can I hide a board?

Yes: `boards.<board>.enabled: false`, then `/leaderboards reload`.

## Does it work with my 2.0.0 config?

Yes, unchanged. See [Upgrading from 2.0.0](../getting-started/installation.md#upgrading-from-200).
