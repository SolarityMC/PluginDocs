---
id: installation
title: Installation
sidebar_position: 2
---

1. Download the latest release.
2. Drop `SolarityMilestones-<version>.jar` into your `plugins` folder.
3. Restart the server.

The first start writes `config.yml` to `plugins/SolarityMilestones/` and creates the `playerdata`
folder. The startup block in the console shows the categories that loaded, whether Blocks Mined is
reading from SolarityGens, the PayNow state and which plugins were hooked.

## Upgrading from 1.x or 2.0.0

Remove the old `SolarityMilestones.jar` and drop in the new one. The plugin name and data folder are
the same, so your `config.yml`, every player's progress and claims, and the PayNow and blocks
baselines carry over untouched.
