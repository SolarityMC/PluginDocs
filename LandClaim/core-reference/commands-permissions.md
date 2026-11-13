---
id: commands-permissions
title: Commands & Permissions
sidebar_position: 1
---

Everything runs under one command, `/lc`. On its own, `/lc` opens the [main menu](menus.md).

Wherever a command takes a `<claim>`, you can type the claim's name (`farm`) or `world:name`
(`world:farm`) when two worlds have a claim with the same name. Clickable chat buttons always use
the `world:name` form.

## Commands

| Command | Does | Permission |
|---|---|---|
| `/lc`, `/lc gui` | Open the main menu | none |
| `/lc wand` | Give a wooden axe, WorldEdit's default selection wand | none |
| `/lc claim <name>` | Claim your current wand selection | `landclaim.claimregion`, plus a claim limit and a world (see below) |
| `/lc list` | Open the menu of claims you own or belong to | `landclaim.list` |
| `/lc inspect <claim>` | Open a claim's menu | `landclaim.inspect.own` for your own claims, `landclaim.inspect.others` for any |
| `/lc resize <claim>` | Move a claim you own to your current wand selection | `landclaim.resize` |
| `/lc delete <claim>` | Delete a claim you own, after a confirmation menu | `landclaim.delete.own`; `landclaim.delete.others` for any claim |
| `/lc teleport <claim>` | Teleport to the claim spawn | `landclaim.teleport` |
| `/lc nearby [on\|off]` | List claims around you and show their borders. `on`/`off` also turns the automatic border on entry on or off for you | `landclaim.nearby` |
| `/lc accept [claim]` | Accept a claim invite | none |
| `/lc deny [claim]` | Decline a claim invite | none |
| `/lc requestjoin` | Ask to join the claim you are standing in | `landclaim.requestjoin` (everyone by default) |
| `/lc approve <player> <claim>` | Accept a join request (owners and officers) | none; your rank decides |
| `/lc reject <player> <claim>` | Decline a join request (owners and officers) | none; your rank decides |
| `/lc leave <claim> [confirm]` | Leave a claim. Without `confirm` it asks first, with a clickable **[Confirm]** | none |
| `/lc tag <claim> <text>` | Set the claim's village tag (Village tier and up) | `landclaim.tag` |
| `/lc townchat` | Toggle town chat (Town tier and up) | `landclaim.townchat` |
| `/lc bank deposit <claim> <amount>` | Put money in the claim's bank (City tier) | `landclaim.bank.deposit` |
| `/lc bank withdraw <claim> <amount>` | Take money out of the claim's bank | `landclaim.bank.withdraw` |
| `/lc bank log <claim>` | Show the bank's transactions | `landclaim.bank.log` |
| `/lc leaderboard [size\|members\|bank]` | Top 5 claims by area, player count or bank balance. Defaults to `size` | `landclaim.leaderboard` |
| `/lc cancel` | Cancel the chat prompt you are answering | none |
| `/lc reload` | Reload `config.yml`, `lang.yml` and the BlueMap layer | `landclaim.reload` (the console can always) |

You can always accept or decline an invite with `/lc accept` and `/lc deny`, approve and reject
join requests with `/lc approve` and `/lc reject`, and leave a claim with `/lc leave`. A rank
decides what a player may do inside a claim, not a permission node. See [Ranks](../features-modules/ranks.md).

## Claiming permissions

`/lc claim` checks three things. Operators skip the last two.

| Node | Meaning |
|---|---|
| `landclaim.claimregion` | May claim at all. Part of `landclaim.basic`. |
| `landclaim.regions.<number>` | May own up to this many claims, e.g. `landclaim.regions.3`. The highest number wins. Not part of `landclaim.basic`. |
| `landclaim.regions.*` | No limit on claims. |
| `landclaim.claimplot` | May make [plots](../features-modules/claiming.md#plots) in claims they own or are an officer of. Part of `landclaim.basic`. |
| `landclaim.plots.<number>` | May own up to this many plots. The highest number wins. Not part of `landclaim.basic`. |
| `landclaim.plots.*` | No limit on plots. |
| `landclaim.world.<world>` | May claim in this world, e.g. `landclaim.world.world`. One node per world. Not part of `landclaim.basic`. |
| `landclaim.world.*` | May claim in every world. |

## Permission groups

### `landclaim.basic`

The normal player set. Not given by default; grant it to your default group.

| Node | Grants |
|---|---|
| `landclaim.claimregion` | `/lc claim` |
| `landclaim.list` | `/lc list` |
| `landclaim.inspect.own` | `/lc inspect` on claims you are in |
| `landclaim.delete.own` | `/lc delete` and the **Remove** button on claims you own |
| `landclaim.resize` | `/lc resize` on claims you own |
| `landclaim.teleport` | `/lc teleport` and the Teleport button |
| `landclaim.nearby` | `/lc nearby` |
| `landclaim.addplayer` | The **Add Player to Claim** button for owners and officers |
| `landclaim.flageditor` | The **Flag Editor** button for owners |
| `landclaim.flag.basic` | The `build`, `interact`, `chest-access` and `pvp` flags (everyone has this by default) |
| `landclaim.tag` | `/lc tag` |
| `landclaim.townchat` | `/lc townchat` |
| `landclaim.requestjoin` | `/lc requestjoin` |
| `landclaim.leaderboard` | `/lc leaderboard` |
| `landclaim.bank.deposit`, `landclaim.bank.withdraw`, `landclaim.bank.log` | The three `/lc bank` actions |

### `landclaim.admin`

Defaults to operators.

| Node | Grants |
|---|---|
| `landclaim.edit.others` | Act as an owner in every claim: manage players, edit teleport points, tag, resize and remove claims you are not in. Adds the direct **Add Owner** and **Add Member** buttons, which skip the invite. |
| `landclaim.inspect.others` | Open any claim's menu, including its Teleport and Flag Editor buttons |
| `landclaim.delete.others` | `/lc delete` on any claim |
| `landclaim.flag.all` | Every flag in the [Flag Editor](../features-modules/flags.md) |
| `landclaim.reload` | `/lc reload` |
| `landclaim.bypass` | The [developer API](../integrations/developer-api.md) treats you as part of every claim |
| `landclaim.resize` | `/lc resize` |

### Other nodes

| Node | Meaning |
|---|---|
| `landclaim.flag.<flag>` | One flag in the Flag Editor, e.g. `landclaim.flag.greeting`. See [Flags](../features-modules/flags.md) for the list. |
| `lc.bypass` | Older name for `landclaim.bypass`. |

`landclaim.bypass` only affects the developer API. It does not let anyone build in a claim; that is
WorldGuard's own bypass.
