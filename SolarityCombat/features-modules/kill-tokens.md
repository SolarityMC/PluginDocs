---
id: kill-tokens
title: Kill Tokens
sidebar_position: 4
---

Killing another player pays the killer `kill-tokens.per-kill` Kill Tokens: a real item, set up as a
currency in your shopkeeper trades. The killer is whoever last hurt the victim, so knocking someone
into lava or a combat-log death still pays. Tokens that don't fit in the killer's inventory drop at
their feet.

## When a kill doesn't pay

- No player killer, or the player killed themself.
- Either player is a plugin NPC.
- The victim died in a world listed in `disabled-worlds`.
- `ignore-same-ip: true` and both players share an IP address. The killer gets `killtoken-same-ip`.
- The killer was already paid for this victim within `same-victim-cooldown-seconds` (60 by default,
  `0` turns it off). The killer gets `killtoken-cooldown` with the time left. Relogging doesn't reset it.
- `kill-tokens.enabled: false`. `/killtokens` still works.

## The token item

Every token is built from `kill-tokens.item`, so they all stack and match your trades:

| Key | Default | What it does |
|---|---|---|
| `material` | `RED_DYE` | The item. Anything that isn't an item falls back to `NETHER_STAR` |
| `name` | `&#ff2121&lKILL TOKEN` | Display name |
| `lore` | 6 lines | Lore lines |
| `glow` | `false` | Enchantment glint |
| `item-model` | empty | A resource-pack model, e.g. `nexo:kill_token` |
| `custom-model-data` | `0` | Custom model data. `0` leaves it unset |

Change the look **before** creating trades. A token made after a change no longer matches trades set
up for the old look. The plugin still knows old tokens are tokens, though (they carry a hidden
marker), so the guards below keep working on them.

## Guards

Tokens can't be used in crafting, put in an anvil (so a rename can't break the trades) or placed as a
block.
