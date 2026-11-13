---
id: flags
title: Flag Editor
sidebar_position: 7
---

Owners edit their claim's WorldGuard flags from the claim menu's **Flag Editor**, without `/rg` or
operator rights. It needs `landclaim.flageditor` (part of `landclaim.basic`). Admins with
`landclaim.inspect.others` can open it on any claim.

## Which flags a player sees

Each flag needs its own permission, `landclaim.flag.<name>`. A lime banner means the flag is set on
this claim, a grey one that it isn't.

| Group | Flags |
|---|---|
| `landclaim.flag.basic` (**everyone by default**) | `build`, `interact`, `chest-access`, `pvp` |
| `landclaim.flag.all` (part of `landclaim.admin`) | All of the above, plus `block-break`, `block-place`, `use`, `damage-animals`, `ride`, `sleep`, `respawn-anchors`, `tnt`, `vehicle-place`, `vehicle-destroy`, `lighter`, `block-trampling`, `entry`, `entry-deny-message`, `greeting`, `greeting-title`, `farewell`, `farewell-title`, `enderpearl`, `chorus-fruit-teleport`, `item-pickup`, `item-drop`, `deny-message` |

Give single flags to a rank or donor group with nodes like `landclaim.flag.greeting`.

## Allow/deny flags

| Button | Does |
|---|---|
| **Allow** / **Deny** | Sets the flag |
| **Delete Flag** | Removes it, so WorldGuard's normal rules apply again |
| **Set for everyone / members / owners / non-members / non-owners** | Who the flag applies to (WorldGuard's region group) |

The current choice is shown as an emerald block, the others as redstone.

`interact` and `use` are special. Every claim starts with both set to **deny for non-members**, and
**Delete Flag** on either puts that default back instead of removing it. Changing `interact` also
sets `use` to match, because WorldGuard checks both for doors, buttons and levers and a deny on
either one wins. To let visitors use doors, set `interact` to **Allow** for everyone.

## Temporary values

Another plugin can give a flag a value for a limited time, for example SolarityGens opening PvP during
a raid. While it runs, that flag's editor shows **Locked for now** with the minutes left, and its
value can't be changed; afterwards the flag goes back to what it was by itself.

## Text flags

`greeting`, `farewell`, their `-title` versions, `entry-deny-message` and `deny-message` take text.
Click **Enter New Value** and type the text in chat (see [Chat Prompts](chat-prompts.md)); **Delete
Flag** clears it.
