---
id: installation
title: Installation
sidebar_position: 2
---

1. Download the latest release.
2. Drop `SolarityTournaments-<version>.jar` into your `plugins` folder.
3. Restart the server.

The first start writes `config.yml` and `messages.yml` to `plugins/SolarityTournaments/`, creates
`tournaments.db`, and starts the first week. The startup block in the console shows the week, when it
ends, how many boards are running and which plugins were hooked.

## Upgrading from 1.x or 2.0.0

Remove the old `SolarityTournaments.jar` and drop in the new one. The plugin name and data folder are
the same, so your `config.yml`, `messages.yml`, `tournaments.db` and the week in progress carry over
untouched.
