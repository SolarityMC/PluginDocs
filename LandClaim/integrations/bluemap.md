---
id: bluemap
title: BlueMap
sidebar_position: 3
---

With [BlueMap](https://bluemap.bluecolored.de/) installed, LandClaim adds a **Land Claims** layer to
every map. Nothing to set up; it can be turned off with `BlueMap.Enabled: false`.

## What's on the map

Each claim is an outlined, filled area in its tier's colour. Clicking it shows:

- the claim's name and village tag,
- its owners,
- how many players it has,
- its tier.

Only claims (regions marked `land-claim-region`) are drawn. Plots are hidden unless
`BlueMap.ShowPlots` is `true`. Claims in worlds without a BlueMap map are not shown.

## Keeping it current

- Claims made, changed or deleted through LandClaim update the layer right away.
- Every `BlueMap.RefreshMinutes` (default 5) the whole layer is rebuilt, which also picks up changes
  made directly with `/rg`.
- `/lc reload` and a BlueMap reload rebuild it too.

The web map shows changes on its next marker update; no terrain needs re-rendering.

## Settings

```yaml
BlueMap:
  Enabled: true
  RefreshMinutes: 5
  MarkerSetLabel: "Land Claims"   # name of the layer in the map's menu
  ShowPlots: false
  MarkerY: 64                     # height the outlines are drawn at
  Colors:
    Settlement: "#4caf50"
    Village: "#2196f3"
    Town: "#ff9800"
    City: "#e91e63"
```

## Marker height

Markers are flat outlines at `MarkerY`, drawn through the terrain so they are always visible from
above. They don't follow the ground, so in a tilted 3D view an outline can look offset from high
terrain. Set `MarkerY` near your typical surface height for the best fit.
