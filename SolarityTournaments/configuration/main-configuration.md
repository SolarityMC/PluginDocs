---
id: main-configuration
title: Main Configuration
sidebar_position: 1
---

`plugins/SolarityTournaments/config.yml`. Apply changes with `/tournaments reload`. The file's own
comments explain every key as well.

## General

| Key | Default | What it does |
|---|---|---|
| `enabled` | `true` | Master switch. `false` stops counting and the weekly reset |

## schedule

| Key | Default | What it does |
|---|---|---|
| `timezone` | `America/New_York` | An IANA zone name |
| `day` | `SATURDAY` | `MONDAY` to `SUNDAY` |
| `time` | `"12:00"` | 24-hour `HH:mm` in the zone above |
| `catch-up-missed` | `true` | Finish (and pay) a week that ended while the server was off |

A bad timezone, day or time logs a warning and falls back to the default.

## prizes

| Key | Default | What it does |
|---|---|---|
| `1`, `2`, `3` | 3, 2 and 1 Seasonal Keys | `display` and `commands` for each place (1 to 10) |
| `delivery-delay-seconds` | `5` | Wait after a winner joins before paying them |
| `deliver-offline` | `false` | Run prize commands for offline winners |

## fair-play

| Key | Default | What it does |
|---|---|---|
| `ignore-creative` | `true` | Creative and spectator never count |
| `exempt-permission` | `solaritytournaments.exempt` | Players with this never count |

## moderation

| Key | Default | What it does |
|---|---|---|
| `player-reset` | `true` | Allow `/tournaments resetplayer` |
| `disqualify` | `true` | Use the disqualified list |
| `notify-player` | `false` | Tell players when they are reset, disqualified or requalified |

## boards

One section per board. See [Boards](../features-modules/boards.md) for every key.

## announce

| Key | Default | What it does |
|---|---|---|
| `chat` | `true` | The winners in chat for everyone online |
| `title` | `true` | A title card for everyone online |

## discord

See [Discord](../integrations/discord.md).

## storage and menus

| Key | Default | What it does |
|---|---|---|
| `storage.flush-seconds` | `5` | How often scores are written to `tournaments.db` |
| `menus.refresh-ticks` | `20` | How often an open menu redraws, in ticks |
| `menus.border` | `BLACK_STAINED_GLASS_PANE` | Menu border item |
| `menus.fill` | `GRAY_STAINED_GLASS_PANE` | Menu fill item |
| `menus.sounds.click` | `ui.button.click` | Click sound (empty for none) |
| `menus.sounds.prize` | `entity.player.levelup` | Prize sound (empty for none) |
