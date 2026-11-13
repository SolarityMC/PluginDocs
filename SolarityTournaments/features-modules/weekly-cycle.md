---
id: weekly-cycle
title: The Weekly Cycle & Prizes
sidebar_position: 2
---

## When a week ends

The week ends on `schedule.day` at `schedule.time` in `schedule.timezone`. A real IANA zone follows
daylight saving, so noon stays noon.

The end of the week in progress is saved as an exact moment. Editing the schedule never moves a week
players are already counting down: the change applies from the next week, or straight away with
`/tournaments reschedule confirm`.

If the server was off when the week should have ended, `schedule.catch-up-missed` decides:

- `true`: the week is finished (and paid) 10 seconds after the server starts.
- `false`: the week is closed with no prizes.

## What happens at the end

1. The top 10 of every board are saved for the history menus.
2. Every prize is written down as its own entry, in the same database transaction.
3. The winners are announced in chat and with a title card (`announce.chat`, `announce.title`).
4. The results are posted to Discord if it's set up.
5. The scores reset and the next week starts.

`/tournaments end confirm` does this right away. `/tournaments reset confirm` wipes the week with no prizes.

## Prizes

`prizes.1`, `prizes.2` and `prizes.3` each have a `display` (what menus, chat and Discord show) and
`commands` (what actually pays, run from the console). Places run from 1 to 10. Tokens: `%player%`,
`%uuid%`, `%board%`, `%place%`, `%score%`, `%week%`.

Crate keys can only be given to someone online, so a prize waits for its winner:

- Online when the week ends: delivered straight away.
- Offline: delivered `prizes.delivery-delay-seconds` (default 5) after they next join.
- `prizes.deliver-offline: true` runs the commands for offline winners too. Only turn it on if every
  prize command works on offline players.

Each prize is handed out exactly once, even across restarts. `/tournaments payouts` lists anything
still waiting, and every delivery is logged to `payouts.log` in the plugin folder.

## Pausing

`enabled: false` stops all counting and the weekly reset. `/tournaments` still opens so players can
look back at past weeks.
