---
id: faq
title: FAQ
sidebar_position: 1
---

### Blocks Mined stays at zero

Check the startup block. It should say `blocks (SolarityGens)`. If it says `(no SolarityGens)`,
SolarityGens isn't installed or didn't enable; if there's a warning about the stats API, update
SolarityGens.

### Store Support stays at zero

Check the PayNow row in the startup block and any PayNow warning after it. The buyer also needs a
linked Minecraft account on PayNow; orders without one can't be matched to a player.

### Why don't my kills count?

Kills on the same player inside `same-victim-cooldown-seconds`, kills between players on the same IP,
and self-kills don't count.

### A player reached a tier but got nothing

Rewards aren't given automatically. They're claimed by clicking the tier in `/milestones`.

### Can I change the menu titles?

Not from the config. Category names come from `display` and tier names from `name`; the rest of the
menu text is built in.

### Can I add a fifth category?

It will load, but only `kills`, `blocks`, `playtime` and `spent` have something counting them, and the
main menu has room for four.

### How do I test a reward without spending money?

`/solaritymilestones addspent <player> <cents>` adds test spending to Store Support, then claim the tier
from `/milestones`.
