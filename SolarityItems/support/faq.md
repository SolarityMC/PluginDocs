---
id: faq
title: FAQ
sidebar_position: 1
---

### An item does nothing when I click it

Check the button: items with `click: LEFT` fire on left-click only. Then check the player has
`solarityitems.use` and the item's own node, and that the item isn't `enabled: false`.

### Combat items say I can only use them in the warzone

The player is standing in a region listed under `settings.regions.safe`, or
`settings.regions.combat-required` has entries and they aren't in one of them.

### A dome or snare didn't cover the whole area

Blocks inside a safe region are never changed, so the shape stops at the region's edge.

### Can I rename an item without breaking copies players already have?

Yes. Items are matched by the `id` stored on them. Keep the `id` the same; old copies keep their old
name and lore, new copies get the new one.

### My new item file isn't loading

Run `/solarityitems reload` and watch the console for `Failed to load item file`. An unknown
`ability.type` loads the item but logs a warning the first time it is used.
