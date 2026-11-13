---
id: menu
title: Menu
sidebar_position: 2
---

## Hub

`/leaderboards` opens the hub (`gui.hub-rows` rows, 3 by default). Each enabled board has an icon at
its `hub-slot` showing the top 3 and your own rank and value. Click an icon to open that board.

Default slots in the 3-row hub: kills 10, deaths 11, blocks 13, gens sold 14, baltop 15, playtime 16.

## Board

A board shows the top `gui.top-size` players (45 by default), 45 heads per page.

| Slot | Item |
|---|---|
| 0-44 | One head per player, with rank and value |
| 45 | Previous page (when there is one) |
| 47 | Back to the hub |
| 49 | Your standing |
| 53 | Next page (when there is one) |

The menus are display only: every click and drag in them is cancelled, so nothing can be taken out
or put in.
