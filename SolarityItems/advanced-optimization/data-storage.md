---
id: data-storage
title: Data Storage
sidebar_position: 2
---

SolarityItems keeps very little on disk:

| File | What it holds |
|---|---|
| `config.yml` | Settings and messages |
| `items/*.yml` | One file per item |
| `dome-restores.yml` | Blocks under glass domes that are up right now. Empty when no dome is standing |

Cooldowns are kept in memory only, so they reset when the server restarts.

The ten starter items are written only when the `items/` folder doesn't exist yet. Delete a starter
file to remove that item for good.
