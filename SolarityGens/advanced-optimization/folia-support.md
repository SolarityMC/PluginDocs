---
id: folia-support
title: Folia Support
sidebar_position: 1
---

SolarityGens runs natively on Folia (and Canvas) as well as Paper. The same jar works on both.

## How it stays on the right thread

- **Claim gens do no work per tick.** Output is worked out from the clock when a gen is used, so dense
  claims cost nothing between clicks. The only timer is the hologram refresh (every 30 seconds by
  default), and each refresh runs on that gen's own region.
- **Blocks and holograms** are only touched on the region that owns them: placing and breaking run in
  the block's events, and pick up and admin reset hop to the gen's region to remove the block.
- **Players** are only touched on their own thread: console and store gives, the starter gen, item
  returns and `/gens home` teleports (`teleportAsync`).
- **Disk work never runs on a game thread.** Claim gen data is written by one background database
  thread, in order. `gens.yml`, `players.yml` and `boosters.yml` are written in the background through
  a temp file and a move, so a crash mid-write leaves the previous file.
- **Shared state** is in concurrent maps, and each gen has its own lock for collect, upgrade and pick up.
- **Reloads** build the new config aside and swap it in whole, so a region thread never sees a
  half-loaded config.
- **Mine-through** only checks players in worlds that hold one of its regions, each on their own thread.

## Spreading gens out

Each claim gen is cheap, but a region with hundreds of players is still one thread. The starter claim
grid leaves a gap between claims; keep claims spread across the world rather than packed in one hub.
LandClaim's reads work from any thread, and its claim changes run on the claim's own region thread.
