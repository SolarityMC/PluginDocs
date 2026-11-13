---
id: items
title: Item Files
sidebar_position: 1
---

Every file in `plugins/SolarityItems/items/` is one item. The file name is only a hint; the item's
real id is its `id:` key. Reload with `/solarityitems reload` after any change.

```yaml
id: glass_dome
enabled: true
material: GLASS
glow: true
default-amount: 1
name: "&#FFDBF7&lGLASS DOME"
lore:
  - "&7Cooldown: %cooldown%"
cooldown-seconds: 180
consume-on-use: true
click: RIGHT
target: PLAYER
target-nearest: true
combat: true
permission: "solarityitems.use.glass_dome"
ability:
  type: GLASS_DOME
  radius: 3
  duration-seconds: 10
```

| Key | Default | What it does |
|---|---|---|
| `id` | file name | Item id used in commands, permissions and placeholders. Lower-cased |
| `enabled` | `true` | `false` keeps the item loaded but refuses every use with the `disabled` message |
| `material` | `PAPER` | Item material. Unknown names fall back to `PAPER` |
| `head-texture` | none | For `PLAYER_HEAD`: a base64 texture value |
| `head-url` | none | For `PLAYER_HEAD`: a `textures.minecraft.net` URL, used when `head-texture` is empty |
| `glow` | `true` | Enchantment glint |
| `default-amount` | `1` | Stack size when no amount is given |
| `name`, `lore` | id, none | Colour codes `&`, `&#RRGGBB` and `&x&R&R&G&G&B&B` work. `%cooldown%` in the lore shows the cooldown |
| `cooldown-seconds` | `0` | Per-player cooldown after a successful use |
| `consume-on-use` | `true` | Take one item from the stack after a successful use |
| `click` | `RIGHT` | `RIGHT` or `LEFT`. Left-click items also fire on a melee hit |
| `target` | `NONE` | `NONE`, `PLAYER` (a player you look at) or `BLOCK` (the block you look at). The old `requires-target: true` means `PLAYER` |
| `target-nearest` | `false` | With `target: PLAYER`, pick the closest player in range instead of the one you aim at |
| `combat` | `false` | PvP item: follows the [region rules](regions.md) |
| `permission` | `solarityitems.use.<id>` | Node needed to use it. `""` means only `solarityitems.use` |
| `ability` | none | The ability block. `type` picks the ability; the other keys tune it (see [Abilities](abilities.md)) |

An item is only charged (cooldown and consume) when its ability really fires, so a use with no
target in range costs nothing. Items are recognised by a tag stored on the item, not by name or lore,
so changing an item's name in its file only affects copies given after the change.
