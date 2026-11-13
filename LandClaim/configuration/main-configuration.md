---
id: main-configuration
title: Main Configuration
sidebar_position: 1
---

Everything lives in `plugins/LandClaim/config.yml`. Apply changes with `/lc reload`. Any setting
missing from your file uses the default shown here, so a `config.yml` from an older version keeps
working; add a key only when you want a different value.

## Claims

```yaml
Claims:
  Regions:
    MinSize: 25
    MaxSize: 999999999
    MaxLWRatio: 4
    NearbyParticleRadius: 50
    NearbyReportRadius: 500
  Border:
    Enabled: true
    Material: OCHRE_FROGLIGHT
    Mode: GROUND
    DurationTicks: 60
```

| Key | Default | Meaning |
|---|---|---|
| `Regions.MinSize` | `25` | Smallest claim area, in blocks (length × width) |
| `Regions.MaxSize` | `999999999` | Largest claim area, in blocks |
| `Regions.MaxLWRatio` | `4` | How many times longer the long side may be than the short side. 4 allows 400 × 100 but not 401 × 100. |
| `Regions.NearbyParticleRadius` | `50` | `/lc nearby` shows the borders of claims within this many blocks |
| `Regions.NearbyReportRadius` | `500` | `/lc nearby` lists claims within this many blocks |
| `Border.Enabled` | `true` | Border and action bar when a player walks into a claim |
| `Border.Material` | `OCHRE_FROGLIGHT` | Block used for borders. Any [block material](https://jd.papermc.io/paper/org/bukkit/Material.html). |
| `Border.Mode` | `GROUND` | `GROUND` draws on the surface; `PLAYER_FEET` at the player's feet, so flying players see it |
| `Border.DurationTicks` | `60` | How long the entry border stays, in ticks (20 = 1 second) |

The size and proportion limits apply to new claims and to resizes. `Plots.PricePerBlock` (default
`0.1`) and `Plots.BaseCost` (default `1`) price [plots](../features-modules/claiming.md#plots): area ×
price per block, at least the base cost. `Regions.PricePerBlock` is left over from older versions and
isn't used; claim prices are under `Economy`.

## Prompts, invites and join requests

```yaml
Prompts:
  TimeoutSeconds: 120

Invites:
  ExpireSeconds: 300

JoinRequests:
  ExpireMinutes: 30
  CooldownSeconds: 120
```

| Key | Default | Meaning |
|---|---|---|
| `Prompts.TimeoutSeconds` | `120` | Time to answer a [chat prompt](../features-modules/chat-prompts.md). `0` = no time limit. |
| `Invites.ExpireSeconds` | `300` | How long an invite stays open. Minimum 10. |
| `JoinRequests.ExpireMinutes` | `30` | How long a join request waits for an answer. Minimum 1. |
| `JoinRequests.CooldownSeconds` | `120` | Time a player must wait between join requests. `0` = none. |

## Economy

```yaml
Economy:
  Enabled: true
  FreeBlocksPerPlayer: 500
  PricePerBlock: 0.75
  MemberDiscountPerMember: 0.10
  MaxDiscount: 0.90
```

| Key | Default | Meaning |
|---|---|---|
| `Enabled` | `true` | `false` makes claiming free |
| `FreeBlocksPerPlayer` | `500` | Blocks each player can claim for free, across all their claims |
| `PricePerBlock` | `0.75` | Price of each block beyond the free allowance |
| `MemberDiscountPerMember` | `0.10` | Discount per member or officer of the claim (0.10 = 10%) |
| `MaxDiscount` | `0.90` | Highest total discount |

See [Economy](../features-modules/economy.md) for how a price is worked out.

## Tiers

```yaml
Tiers:
  Settlement: { Min: 1, Max: 3 }
  Village: { Min: 4, Max: 6 }
  Town: { Min: 7, Max: 10 }
  City: { Min: 11, Max: -1 }
  VillageTag:
    MaxLength: 24
```

`Min` and `Max` are player counts (owners + officers + members). `Max: -1` means no upper limit.
Tiers are checked from City down to Village, and a claim that fits none of them is a Settlement.
Keep the ranges from overlapping. `VillageTag.MaxLength` caps `/lc tag`.

## Leaderboard

```yaml
Leaderboard:
  RefreshMinutes: 5
```

How often `/lc leaderboard` rankings are rebuilt in the background. Minimum 1.

## BlueMap

```yaml
BlueMap:
  Enabled: true
  RefreshMinutes: 5
  MarkerSetLabel: "Land Claims"
  ShowPlots: false
  MarkerY: 64
  Colors:
    Settlement: "#4caf50"
    Village: "#2196f3"
    Town: "#ff9800"
    City: "#e91e63"
```

See [BlueMap](../integrations/bluemap.md).

## ClearLaggEnhanced

```yaml
ClearLaggEnhanced:
  ProtectClaimMobs: true
```

Stops ClearLaggEnhanced removing peaceful mobs inside claims and plots. See [ClearLaggEnhanced](../integrations/clearlaggenhanced.md).

## Developer API

```yaml
Api:
  Worlds: []
```

Worlds where other plugins may create and change claims through `LandClaimApiV2`. An empty list
allows every world. Ending a temporary flag always works, whatever this says. See
[Developer API](../integrations/developer-api.md).
