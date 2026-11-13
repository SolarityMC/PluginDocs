---
id: boards
title: Boards
sidebar_position: 1
---

Every board is a key under `boards` in `config.yml`. Each one has a `type`:

| Type | What counts |
|---|---|
| `PLAYER_KILLS` | A player killed by another player |
| `GENERATORS_MINED` | A SolarityGens click-to-mine generator block mined, nothing else |
| `MONEY_EARNED` | Money paid by a plugin listed in the board's `sources` |

The default config has one of each: `kills`, `blocks` and `money`. Set `enabled: false` on a board to
turn it off.

## Rules for every board

- Creative and spectator never count (`fair-play.ignore-creative`).
- Players with `solaritytournaments.exempt` never count.
- `worlds` limits a board to some worlds; empty means everywhere.
- `min-score` is the least a player needs to win a prize (money: dollars).
- Disqualified players are left off every board.

## Player Kills

- `same-victim-cooldown-seconds` (default 300): killing the same player again inside this window does
  not count, so two friends can't trade kills. `0` turns it off.
- `ignore-same-ip` (default true): a kill between two players on the same IP address does not count.

## Blocks Mined

- `generators`: the SolarityGens generator ids that count. Empty means every generator.

## Money Earned

- Only money the server pays counts. `/pay`, `/eco`, auctions, coinflips, KOTH, crates and anything
  from a plugin not in `sources` never counts. See [Economy](../integrations/economy.md).
- `money-format`: how the score is shown. `%amount%` is the number, with cents shown under $1,000.

## Looks

`name`, `color`, `icon`, `slot` (its place in `/tournaments`), `unit` and `unit-one` ("24 kills",
"1 kill"), `description`, `counts`, `not-counted` and `discord-emoji`. A board can have its own
`prizes:` section; otherwise it pays the shared one. See
[The Weekly Cycle & Prizes](weekly-cycle.md).
