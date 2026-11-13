---
id: folia-support
title: Folia Support
sidebar_position: 1
---

SolarityCombat runs natively on Folia (and Canvas) as well as Paper. The startup block says which one
it's on.

- Combat tags are kept in thread-safe maps, so hits tag players in any region. The countdown runs on
  the global scheduler.
- Kill Tokens are given on the killer's own thread, even when the killer is in another region (a bow
  shot or a knock into lava).
- `/killtokens` hands tokens out on the target player's thread.
- Item cap checks and reminders run on each player's own thread.
- Vehicles held out of a safezone are moved back with an async teleport, keeping the rider seated.
