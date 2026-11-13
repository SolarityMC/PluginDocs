---
id: folia-support
title: Folia Support
sidebar_position: 1
---

SolarityMilestones runs natively on Folia (and Canvas) as well as Paper. The startup block says which
one it's on.

- The playtime timer runs on the global scheduler, and each player's time is added on that player's
  own thread.
- PayNow requests run off the game threads. Purchase messages and tier sounds hop to the player's thread.
- Player data is kept in thread-safe maps, so kills and mining count from any region.
