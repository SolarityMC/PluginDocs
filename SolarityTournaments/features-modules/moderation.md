---
id: moderation
title: Moderation
sidebar_position: 3
---

Needs `solaritytournaments.moderate` (admins have it). Without `confirm` typed on the end,
`resetplayer` and `disqualify` only show what they would wipe.

## Resetting a player

`/tournaments resetplayer <player> [board|all] confirm` wipes one player's scores for this week, on
every board or just one. What they do afterwards still counts. Switched by `moderation.player-reset`.

## Disqualifying a player

`/tournaments disqualify <player> [reason] confirm` wipes their week and bars them from every tournament
until they are requalified. Nothing they do is counted, and they never appear on a board, in a menu, in
a placeholder, in the week's results, in the prizes or in the Discord post. A prize they won earlier
but haven't collected is held back until they are requalified. The list survives the weekly reset and
restarts.

- `/tournaments requalify <player>` lets them compete again. The scores wiped by the disqualification stay gone.
- `/tournaments disqualified [page]` shows who is barred, why, by whom and when.

`moderation.disqualify: false` ignores the list and everyone counts again. The list is kept, so turning
it back on restores every entry.

## Telling the player

`moderation.notify-player: true` tells the player (when online) that they were reset, disqualified or
requalified. With it off, they only see "Disqualified" in `/tournaments`.

## Fixing a score

Admins can use `/tournaments add|take <board> <player> <amount>`. Money is in dollars. Every moderation
and admin action is logged to the console with who did it.
