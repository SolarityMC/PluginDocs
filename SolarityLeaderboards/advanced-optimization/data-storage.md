---
id: data-storage
title: Data Storage
sidebar_position: 2
---

Everything the plugin counts itself is in `plugins/SolarityLeaderboards/stats.yml`, one section per
player UUID:

```yaml
00000000-0000-4000-8000-00000000000a:
  name: Steve
  kills: 7
  deaths: 2
  blocks: 1500
  playtime: 3000      # minutes
  balance: 12345.67   # last balance read through Vault, if baltop uses Vault
```

It is the 2.0.0 format plus `balance`. Gens mined and gens sold aren't stored here: they are read
from SolarityGens every refresh.

## Saving

- Every `save-seconds` (120) when something changed, off the game threads, and once more on shutdown.
- Each save is written to `stats.yml.tmp` and then moved over `stats.yml`, so a crash mid-save leaves
  the previous file intact.

## A broken stats.yml

If `stats.yml` can't be read (a bad hand edit, say), it is copied to
`stats.yml.broken-<date>-<time>` before anything else happens, and the console says so. Fix the copy
and put it back while the server is stopped. If even the copy fails (a full disk, say), the console
says to back the file up by hand, because the next save will overwrite it.

## Resetting

There is no reset command. To wipe the boards, stop the server and delete `stats.yml`.
