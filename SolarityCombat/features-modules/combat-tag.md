---
id: combat-tag
title: Combat Tag
sidebar_position: 1
---

Any PvP damage tags both players for `combat.tag-seconds` (15 by default). Arrows and other
projectiles count for whoever shot them. Hitting yourself and hits that do no damage don't tag.
Every new hit resets the timer. Players get the `tagged` message on the first hit, an action-bar
countdown while tagged, and `untagged` when it runs out. Dying clears the tag, and the killer's tag
is cleared too.

Staff with `solaritycombat.bypass` are never tagged. `/combattag bypass` turns that off for yourself
until you run it again or the server restarts.

## What tagged players can't do

Each one is a toggle under `combat.restrictions`. Spam-clicking a blocked action shows the message at
most once a second.

| Toggle | Default | Blocks |
|---|---|---|
| `block-commands` | `true` | Commands. See below |
| `block-safezone-entry` | `true` | Walking, riding or teleporting into a safezone. See [Safezone Barrier](safezone.md) |
| `block-spear-lunge` | `true` | Using a spear |
| `block-elytra` | `true` | Starting to glide |
| `block-chorus-fruit` | `true` | Eating chorus fruit |
| `block-ender-pearl` | `false` | Throwing ender pearls |
| `block-place` | `false` | Placing blocks |
| `block-break` | `false` | Breaking blocks |

Building is left to WorldGuard by default: players build wherever its flags already allow.

## Commands while tagged

With `block-all-commands: true` (the default) every command is denied **except** those in
`allowed-commands`. A blocked list can never keep up with every new command, and one missed entry is a
free escape from a fight. Set `block-all-commands: false` to use `blocked-commands` instead, which
denies only what's listed.

Both lists are labels without the slash, and aliases count separately (`msg` and `tell` are two
entries). `/plugin:command` is checked as `command`.

## Combat logging

With `punish-combat-log: true`, a player who disconnects while tagged is killed, so their items drop
and death events fire as normal (the last player to hit them gets the kill). With
`broadcast-combat-log: true` the server sees `combat-log-broadcast`.

A disconnect the **server** caused isn't punished. Paper's flying check kicks players knocked into the
air mid-fight, and those players used to die for a disconnect they never chose. Kick causes in
`combat-log-exempt-kick-causes` skip the punishment (the console logs one line when it happens).
`TIMEOUT` is deliberately not in the default list: pulling the plug looks exactly like a dropped
connection. Add `PLUGIN` if anticheat kicks should skip it too.
