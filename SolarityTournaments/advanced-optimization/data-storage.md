---
id: data-storage
title: Data Storage
sidebar_position: 2
---

Everything is in one SQLite file, `plugins/SolarityTournaments/tournaments.db`: the week in progress,
every score, player names, finished weeks and their results, the prize ledger and the disqualified list.

- Scores are counted in memory and written every `storage.flush-seconds` (default 5). A hard crash loses
  at most that many seconds; a normal shutdown saves everything.
- The end of a week is one database transaction, so a crash can't leave it half done.
- Every prize is its own ledger row that can only be delivered once.
- `payouts.log` in the same folder records every delivery.

If `tournaments.db` can't be opened, the plugin logs an error and disables itself, so no score is lost
or overwritten. Back the file up with your worlds.
