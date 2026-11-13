---
id: quick-start
title: Quick Start
sidebar_position: 3
---

1. Install the plugin, plus WorldGuard if you want the safezone barrier (see [Requirements](requirements.md)).
2. Open `plugins/SolarityCombat/config.yml` and check `combat.restrictions.allowed-commands`. While
   tagged, every other command is denied, so add anything harmless your players rely on.
3. Make sure your spawn region has `pvp` set to `deny` in WorldGuard. That is what marks it as a
   safezone. You can also list region names under `combat.safezone.regions`.
4. Set the Kill Token look under `kill-tokens.item` **before** you create shopkeeper trades for it.
5. Run `/solaritycombat` to reload.
6. Hit another player and run `/combattag` to see the tag.

Staff with `solaritycombat.bypass` (ops by default) are never tagged. Run `/combattag bypass` to turn
that off for yourself while you test, and again to turn it back on.
