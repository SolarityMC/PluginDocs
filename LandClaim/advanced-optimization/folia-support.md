---
id: folia-support
title: Folia Support
sidebar_position: 1
---

LandClaim is marked `folia-supported` and runs natively on Folia 26.2 and 26.3. Nothing needs configuring.

## How it handles regions

- Claim edits made from chat (prompt answers, invites, admin adds) move to the player's own region
  thread before they touch the claim. Player name lookups that might need Mojang run off-thread first.
- Teleports to a claim spawn use asynchronous teleporting from the player's region thread.
- Borders are sent to the client only, never placed in the world. A player who changes world or
  logs out simply drops their border; nothing is sent to restore blocks in another region.
- Border block and height lookups only read chunks owned by the player's current region.
- Invite and join request timers, the leaderboard refresh and BlueMap updates run on the async
  scheduler and never block a region.

## Plugins to pair it with

- **WorldEdit:** use [FastAsyncWorldEdit-Folia](https://github.com/ANO-Development/FastAsyncWorldEdit-Folia).
- **WorldGuard:** 7.0.19 is Folia-supported.
- Folia skips plugins that aren't marked `folia-supported`. If your economy plugin is one of them,
  Vault has no economy and claiming is free; see [Vault](../integrations/vault.md).

## Developer API

`checkCapture` must be called on the thread that owns both the player and the location. On Folia,
anything else returns `UNAVAILABLE`.

`LandClaimApiV2` reads can be called from any thread. Its changes run on the region thread that owns
the claim's center chunk, fire their events there, and hand the region save to WorldGuard's writer
off the game thread. Temporary flags are timed off-thread and put back on the claim's region thread;
a sweep every 30 seconds catches any that are overdue. See [Developer API](../integrations/developer-api.md).
