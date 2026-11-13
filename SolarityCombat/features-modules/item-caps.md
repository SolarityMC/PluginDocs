---
id: item-caps
title: Item Caps
sidebar_position: 3
---

Item caps limit how many of an item a player may benefit from. The default config caps enchanted
golden apples at 3. Staff with `solaritycombat.itemcap.bypass` ignore every cap.

## Modes

`item-caps.on-excess` picks what happens to a player over a limit.

| Mode | What happens |
|---|---|
| `BLOCK_USE` (default) | They can carry any amount, but can't eat or drink the item while over the limit. They're reminded every `warn-interval-seconds` and when they join |
| `DROP` | The excess is dropped at their feet, and they can't pick up more than the limit |
| `DELETE` | The excess is removed |

`BLOCK_USE` is a deliberately soft cap. A player can drop the extras, use one and pick them back up,
but mid-fight that costs a couple of exposed seconds and risks handing the items to their opponent.

`DROP` and `DELETE` are hard caps, but they can't tell hoarding apart from ordinary handling: buying a
stack from a shopkeeper, opening a kit or moving stock out of storage all put items on the floor the
player then can't pick up. In those modes inventories are re-counted every `check-interval-ticks`
and after inventory clicks, drags and closes.

## Adding a cap

```yaml
item-caps:
  limits:
    ENCHANTED_GOLDEN_APPLE:
      max: 3
      display: "Enchanted Golden Apples"
    TOTEM_OF_UNDYING:
      max: 1
      display: "Totems"
```

The key is a material name. `max` is 0 or more, and `display` is the name used in messages. An
unknown material or a negative `max` is skipped with a console warning. The startup block and the
`/solaritycombat` reply list every cap that loaded, so a typo is easy to spot.
