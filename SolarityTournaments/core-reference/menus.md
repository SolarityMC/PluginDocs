---
id: menus
title: Menus
sidebar_position: 3
---

Everything opens from `/tournaments`.

- **Main menu**: every running board, your own place and score, and how long the week has left.
- **Board**: the top 10 of one board as player heads, with what each place wins.
- **History** (`/tournaments history`): finished weeks, with your own results for each.
- **Past week** and **past board**: one finished week, then one board in it, with the final standings.
- **Guide** (`/tournaments guide`): what each board counts and doesn't, from each board's
  `description`, `counts` and `not-counted` lines.

Open menus redraw every `menus.refresh-ticks` ticks, so scores tick up live. Titles, item names and lore
are in the `menu` section of `messages.yml`; the border and fill glass and the sounds are under `menus`
in `config.yml`.
