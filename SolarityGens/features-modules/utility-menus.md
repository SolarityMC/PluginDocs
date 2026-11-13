---
id: utility-menus
title: Anvil & Enchanting
sidebar_position: 6
---

Two convenience menus, each turned on or off under `utility-commands:` in `config.yml`.

- `/gens anvil` (permission `solaritygens.anvil`): an anvil that never wears out.
- `/gens enchanting` (permission `solaritygens.enchant`): an enchanting table at full level-30 power
  with no bookshelves. Each slot rolls a random set of 2 to 5 enchantments at or near their top
  level, and the hint shown is one of the enchantments you will actually get.

## Right-clicking real blocks

With `solaritygens.interact`, right-clicking a placed anvil or enchanting table opens the same
enhanced menus (sneaking places a block against it instead). `interact-blocks.anvil` and
`interact-blocks.enchanting` turn this on or off, and `interact-blocks.regions` limits it to WorldGuard
regions (empty = anywhere).
