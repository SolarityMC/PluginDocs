---
id: configuration
title: Configuration
sidebar_position: 1
---

Everything is in `plugins/SolarityLeaderboards/config.yml`. Run `/leaderboards reload` after
editing it. A key that is missing uses the default below, so a config from 2.0.0 works unchanged.

Colours use `&` codes, `&#RRGGBB` hex and MiniMessage tags.

## Timing

| Key | Default | What it does |
|---|---|---|
| `refresh-seconds` | `60` | How often the boards re-rank and online players' balance and playtime are read. Minimum 10 |
| `save-seconds` | `120` | How often `stats.yml` is saved when something changed. Minimum 30 |

## Menu (`gui`)

| Key | Default | What it does |
|---|---|---|
| `hub-title` | `&0Solarity Leaderboards` | Hub title |
| `hub-rows` | `3` | Hub height, 1 to 6 |
| `board-title` | `&0Solarity Leaderboards &8» &0%board%` | Board title; `%board%` is the board name |
| `top-size` | `45` | How many players a board shows |
| `filler` | `BLACK_STAINED_GLASS_PANE` | Background item |
| `hub-empty` | `&7Nobody on this board yet.` | Hub icon text for an empty board |
| `previous` / `next` | arrows | Page button names |
| `back` | `&7&l« &7All leaderboards` | Back button name |
| `back-material` | `OAK_DOOR` | Back button item |

## Boards (`boards.<board>`)

`<board>` is `kills`, `deaths`, `blocks`, `sold`, `baltop` or `playtime`.

| Key | What it does |
|---|---|
| `enabled` | `false` hides the board everywhere (menu, command, placeholders return empty boards) |
| `name` | Display name |
| `color` | Colour for its values |
| `icon` | Hub icon item |
| `hub-slot` | Hub slot (0 to rows x 9 - 1) |
| `row-label` | Label before the value on each head, such as `Kills` |
| `format` | `number` (`1,234`), `money` (`$1,234`) or `playtime` (`2d 3h 4m`) |
| `unit` | Text after each value, such as `coins`. Empty by default |

Defaults per board:

| Board | Name | Icon | Slot | Format |
|---|---|---|---|---|
| kills | Kills | `DIAMOND_SWORD` | 10 | number |
| deaths | Deaths | `SKELETON_SKULL` | 11 | number |
| blocks | Blocks Mined | `DIAMOND_PICKAXE` | 13 | number |
| sold | Gens Sold | `EMERALD` | 14 | money |
| baltop | Baltop | `SUNFLOWER` | 15 | number |
| playtime | Playtime | `CLOCK` | 16 | playtime |

Extra keys:

| Key | Default | What it does |
|---|---|---|
| `boards.blocks.count-every-block` | `true` | Count every block broken, not only SolarityGens gens |
| `boards.blocks.count-creative` | `false` | Count blocks broken in creative mode |
| `boards.baltop.source` | `auto` | `auto`, `vault` or `solarityeconomy` (see [Economy](../integrations/economy.md)) |

## Placeholders and messages

| Key | Default | What it does |
|---|---|---|
| `placeholders.empty-name` | `---` | Name shown for an empty position |
| `messages.prefix` | `&#55E0FF&lLeaderboards &8» &7` | Put before every message |
| `messages.no-permission` | | No permission |
| `messages.players-only` | | The console tried to open the menu |
| `messages.unknown-board` | | `%board%` is what was typed, `%boards%` the enabled boards |
| `messages.reloaded` | | After `/leaderboards reload` |

Set a message to `""` to turn it off.
