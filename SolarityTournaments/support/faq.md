---
id: faq
title: FAQ
sidebar_position: 1
---

### The Blocks Mined or Money Earned board stays at zero

Check the startup warnings. Blocks Mined needs SolarityGens. Money Earned needs SolarityEconomy 1.1.0+
or EssentialsX, and the paying plugin has to be in `boards.money.sources`.

### I changed the schedule but the countdown didn't move

That's on purpose: the week in progress keeps its end time. Run `/tournaments reschedule confirm` to
move it now.

### A winner says they never got their prize

Run `/tournaments payouts`. Prizes for offline winners wait until they join, and a prize for a
disqualified player is held until they are requalified. Delivered prizes are in `payouts.log`.

### Why don't my kills count?

Kills on the same player inside `same-victim-cooldown-seconds`, kills between players on the same IP,
kills in creative or spectator, and kills outside the board's `worlds` don't count.

### Do operators compete?

Yes. Only players with `solaritytournaments.exempt` are left out, and nobody has it by default.

### Can I add another board?

Yes. Add a section under `boards` with one of the three types and a free `slot`, then run
`/tournaments reload`.
