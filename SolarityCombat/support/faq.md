---
id: faq
title: FAQ
sidebar_position: 1
---

### Tagged players can still walk into spawn

Check the `Hooks` row in the startup block lists WorldGuard. Then make sure spawn either has
`pvp` set to `deny` or is listed under `combat.safezone.regions`.

### I'm never tagged when I test

You have `solaritycombat.bypass` (ops do by default). Run `/combattag bypass` to play as a normal
player, and again to switch it back.

### A player died when they disconnected but says they didn't log out

Check the console. A kick listed in `combat-log-exempt-kick-causes` logs a line and isn't punished.
`TIMEOUT` isn't on that list on purpose, because a pulled plug and a dropped connection look the same.

### My players need a command that's blocked in combat

Add its label (and each alias you want to allow) to `combat.restrictions.allowed-commands`, then run
`/solaritycombat`.

### Why didn't a kill pay a Kill Token?

The killer gets a message for a same-victim cooldown or a shared IP. No message means kill tokens are
off, the world is in `disabled-worlds`, or there was no player killer.

### My shopkeeper stopped accepting Kill Tokens

The token look was changed after the trades were made. Change `kill-tokens.item` back, or redo the
trades with a token from `/killtokens get`.

### Where did /koth go?

KOTH moved to the SolarityKoth plugin. The old `%solaritycombat_koth_*%` placeholders still resolve,
but always show no active KOTH.

### Where's the mace cap and spear cooldown?

Weapon balancing moved to SolarityCore (the `weapons` section of its config).
