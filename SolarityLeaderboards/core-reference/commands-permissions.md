---
id: commands-permissions
title: Commands & Permissions
sidebar_position: 1
---

## Commands

Aliases: `/leaderboard`, `/lb`, `/tops`.

| Command | What it does | Permission |
|---|---|---|
| `/leaderboards` | Open the hub | `solarityleaderboards.use` |
| `/leaderboards <board>` | Open one board: `kills`, `deaths`, `blocks`, `sold`, `baltop`, `playtime` | `solarityleaderboards.use` |
| `/leaderboards reload` | Re-read `config.yml` and re-rank every board. Works from the console | `solarityleaderboards.admin` |

`crystals` and `money` still open baltop, and `gens` opens gens sold.

## Permissions

| Permission | Default | What it allows |
|---|---|---|
| `solarityleaderboards.use` | everyone | Open the menu |
| `solarityleaderboards.admin` | op | Reload |
