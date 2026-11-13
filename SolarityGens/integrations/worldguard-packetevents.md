---
id: worldguard-packetevents
title: WorldGuard & PacketEvents
sidebar_position: 4
---

## WorldGuard

LandClaim needs WorldGuard for its claims (see [LandClaim](landclaim.md)). SolarityGens itself uses
it for click-to-mine gens and the utility menus:

- **Mine through players** only works inside the regions in `settings.mine-through-regions`.
- **`interact-blocks.regions`** limits right-clicking anvils and enchanting tables to regions.

Region names are matched as typed and in lower case. Without WorldGuard both features are simply off.
All WorldGuard code is kept in one class, so SolarityGens loads fine without it.

## PacketEvents

Optional, for mine-through. Hiding a drilled-through player normally also removes them from your tab
list; with PacketEvents, SolarityGens strips them out of that packet, so they stay in tab with their
real rank. Without it mine-through works the same, and the player briefly drops from tab.
