---
id: commands-permissions
title: Commands & Permissions
sidebar_position: 1
---

The main command is `/solaritygens`, also answering to `/gens`, `/dytchsgens`, `/dgens` and
`/dytchgens` (the last three are the names from before the rename, kept for store deliveries and
scripts). On its own, `/gens` opens the [generator shop](menus.md#generator-shop).

## Player commands

| Command | Does | Permission |
|---|---|---|
| `/gens` | Open the generator shop | `solaritygens.use` |
| `/gens start` | Get a starter claim and the starter gens (3 by default), and teleport there. Once per player | `solaritygens.use` |
| `/gens home` | Teleport to your claim | `solaritygens.use` |
| `/gens expand` | Show the price of the next claim size. `/gens expand confirm` buys it | `solaritygens.use` |
| `/gens help` | List the commands you can use | none |
| `/gens anvil` | Open an anvil that never wears out | `solaritygens.anvil` |
| `/gens enchanting` (`enchant`, `enchanttable`) | Open a level-30 enchanting table, no bookshelves needed | `solaritygens.enchant` |
| `/autopickup`, `/autoblock`, `/autosmelt` | Toggle that auto feature for click-to-mine drops | `solaritygens.autopickup`, `.autoblock`, `.autosmelt` |
| `/autosell` | Toggle selling click-to-mine drops to ShopGUIPlus | `solaritygens.autosell` |
| `/boosters` (`/booster`, `/myboosters`) | Your active booster vouchers and the server booster | `solaritygens.boosters` |

## Claim gen admin commands

All need `solaritygens.admin`. Commands that act on "the gen you look at" use the claim gen within
6 blocks of your crosshair.

| Command | Does |
|---|---|
| `/gens admin give <player> <type> [amount]` | Give new claim gen items (1 to 36). Logged in the audit log |
| `/gens admin unlock <player> <type>` | Unlock a type without charging or giving a gen |
| `/gens admin setlevel <level>` | Set the level of the gen you look at (stored output is settled at the old level first) |
| `/gens admin debug` | Show the id, owner, level, stored output and clock of the gen you look at |
| `/gens admin audit <player>` | The newest 15 audit log lines for a player |
| `/gens admin reset <player> confirm` | Remove all of a player's claim gens (placed ones vanish from the world), their unlocks and their start, so they can `/gens start` again. Their claim stays |
| `/gens admin globalbooster <multiplier> <duration> [activated by]` | Start the [server booster](../features-modules/boosters.md#server-booster), or queue it behind the running one |
| `/gens admin globalbooster stop` | End the running server booster now |
| `/gens admin addmember <owner> <member>` | Add a member to a dev claim (for testing team claims) |

## Click-to-mine admin commands

All need `solaritygens.admin`. Their form is unchanged from DytchsGens.

| Command | Does |
|---|---|
| `/gens give <player> <type> [amount]` | Give click-to-mine gen items (1 to 64) |
| `/gens booster give <player> <block\|sell> <multiplier> <duration> [amount]` | Give booster vouchers. Block multipliers are whole numbers from 2, sell multipliers from 1.01, both up to 100 |
| `/gens list` | List click-to-mine gen types |
| `/gens remove` | Remove the click-to-mine gen you look at (it becomes a normal block) |
| `/gens pickup` | Arm sneak-break pickup of a click-to-mine gen (see [Click-to-Mine Gens](../features-modules/click-to-mine-gens.md#picking-a-gen-up)) |
| `/gens resetstats confirm` | Wipe every player's mined count |
| `/gens reload` | Reload `config.yml` and `claimgens.yml`. Placed gens and player data are not touched |

## Permissions

| Permission | Default | Allows |
|---|---|---|
| `solaritygens.*` | op | Everything below |
| `solaritygens.use` | everyone | Claim gens: placing, the menus, the shop, `start`, `home`, `expand` |
| `solaritygens.admin` | op | Every admin command, and sneak-break pickup of click-to-mine gens |
| `solaritygens.autopickup` | everyone | `/autopickup`, and the feature itself |
| `solaritygens.autoblock` | everyone | `/autoblock`, and the feature itself |
| `solaritygens.autosmelt` | everyone | `/autosmelt`, and the feature itself |
| `solaritygens.autosell` | nobody | `/autosell`, and the feature itself (a rank perk) |
| `solaritygens.boosters` | everyone | `/boosters` |
| `solaritygens.booster.use` | everyone | Right-clicking a booster voucher |
| `solaritygens.anvil` | everyone | `/gens anvil` |
| `solaritygens.enchant` | everyone | `/gens enchanting` |
| `solaritygens.interact` | everyone | Right-clicking an anvil or enchanting table for the enhanced menu |

### Old permission names

Each `dytchsgens.<name>` node from before the rename (`admin`, `autopickup`, `autoblock`, `autosmelt`,
`autosell`, `boosters`, `booster.use`, `anvil`, `enchant`, `interact`) still exists and passes its value
on to `solaritygens.<name>`. A LuckPerms group that grants `dytchsgens.autosell` still grants autosell,
and one that sets `dytchsgens.autopickup` to false still takes it away. New grants should use the
`solaritygens.*` names.
