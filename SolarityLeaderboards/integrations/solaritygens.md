---
id: solaritygens
title: SolarityGens
sidebar_position: 1
---

With SolarityGens 26.11.0 or newer installed, two boards read from it through its `GensStatsAPI`:

- **Blocks Mined** adds each player's click-to-mine gens mined to the blocks they broke.
- **Gens Sold** is each player's lifetime money from selling claim gen output, in whole dollars.

Nothing needs setting up: the console's `Hooks` line lists `SolarityGens` when it is found.

Without SolarityGens, or with an older one (the old DytchsGens API at `gg.dytch.gens.api` isn't
read), Blocks Mined counts ordinary blocks only and Gens Sold stays empty. Turn it off with
`boards.sold.enabled: false` if the server doesn't run SolarityGens.
