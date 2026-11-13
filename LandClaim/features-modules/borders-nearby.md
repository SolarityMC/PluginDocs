---
id: borders-nearby
title: Borders & Nearby Claims
sidebar_position: 6
---

## Borders when you enter a claim

Walking into a claim briefly outlines its edge with glowing blocks (ochre froglight by default) and
shows *Entering claim: farm* in the action bar. Walking out shows *Leaving claim: farm*.

The border blocks are sent to that one player's client only. Nothing changes in the world, nobody
else sees them, and they disappear after `Claims.Border.DurationTicks` (default 60, 3 seconds).

```yaml
Claims:
  Border:
    Enabled: true            # false turns the entry border and action bar off for everyone
    Material: OCHRE_FROGLIGHT
    Mode: GROUND             # GROUND: on the surface. PLAYER_FEET: at your feet, for flying players
    DurationTicks: 60
```

Players who don't want it run `/lc nearby off`. That choice is saved on the player and survives
relogs and restarts; `/lc nearby on` turns it back on.

## `/lc nearby`

Running `/lc nearby` without `on` or `off` does two things:

1. Lists every claim within `Claims.Regions.NearbyReportRadius` blocks (default 500), nearest first,
   with its distance and compass direction: *farm (42 blocks NE)*. The claim you are standing in is
   left out.
2. Shows the borders of every claim within `Claims.Regions.NearbyParticleRadius` blocks (default 50)
   for 15 seconds.

Running it again while the borders are up hides them. While `/lc nearby` borders are showing,
walking into a claim doesn't interrupt them.

Only claims count (regions marked `land-claim-region: region`). Spawn and other server regions are
never listed or outlined.
