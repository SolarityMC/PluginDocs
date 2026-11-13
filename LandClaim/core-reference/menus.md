---
id: menus
title: Menus
sidebar_position: 2
---

Almost everything about a claim is managed from menus. Every menu has **Back** and **Close** buttons.

## Main menu (`/lc`)

| Button | Does |
|---|---|
| Wooden axe | Gives you the claim wand |
| Book | How to claim, step by step |
| Grass block | Opens **Your Claims** |

## Your Claims (`/lc list`)

Every claim you own, then every claim you belong to, 28 per page. Diamond blocks are claims you own,
iron blocks claims you are a member or officer of. The lore shows the world and your status. Click a
claim to open its menu.

## Claim menu (`/lc inspect <claim>`)

| Button | Shown to | Opens |
|---|---|---|
| Player head: **Players** | Everyone in the claim | The players menu below |
| Ender pearl: **Teleport** | `landclaim.teleport` | The teleport menu |
| Banner: **Flag Editor** | Owners with `landclaim.flageditor`, or `landclaim.inspect.others` | The [Flag Editor](../features-modules/flags.md) |
| Structure void: **Remove** | Owners with `landclaim.delete.own`, or `landclaim.edit.others` | A confirmation to delete the claim |

## Players menu

| Button | Shown to | Does |
|---|---|---|
| **Manage Players** | Everyone in the claim | Lists everyone in the claim, owners first |
| **Add Player to Claim** | Owners and officers with `landclaim.addplayer`, and admins | Invite a player (admins can also add directly) |
| **Pending Join Requests (n)** | Owners, officers and admins | Join requests waiting for an answer |
| **Leave Claim** | Everyone in the claim | Sends the leave confirmation to chat |

### Manage Players

Each player's head shows their rank: a wither skeleton skull for owners, a zombie head for
officers and a skeleton skull for members. Click one to manage that player:

| Slot | Button | Does |
|---|---|---|
| Left | Lime dye: **Promote to …** | Moves them up one rank |
| Right | Orange dye: **Demote to …** | Moves them down one rank |
| Bottom | Barrier: **Remove from claim** | Asks for confirmation, then removes them |

Only the buttons your rank allows are shown. When you look at the claim's only owner, a grey
**Last owner** note explains why there is no Demote or Remove button. See [Ranks](../features-modules/ranks.md).

### Add Player to Claim

- **Invite Player** asks you to type the name of an online player in chat and sends them an invite.
- Admins (`landclaim.edit.others`) also see **Add Owner** and **Add Member**, which add a player
  straight away without an invite. The player must have joined the server before.

### Pending Join Requests

Left-click a player to approve them as a member, right-click to decline. The list keeps requests
that came in while you were offline, until they expire.

## Teleport menu

Claims below the Village tier show **Claim Spawn Locked** instead. From Village up:

| Button | Shown to | Does |
|---|---|---|
| Ender pearl: **Teleport to …** | Everyone who can open the menu | Teleports you to the claim spawn |
| Crafting table: **Set Teleport Point** | Owners and admins | Sets the claim spawn where you stand. You must be inside the claim. |
| Furnace: **Remove Teleport Point** | Owners and admins | Clears the claim spawn |

## Claim confirmation

Opened by `/lc claim <name>`. The green block confirms and charges the claim's price, if any. Close
the menu to back out; nothing is claimed until you confirm.
