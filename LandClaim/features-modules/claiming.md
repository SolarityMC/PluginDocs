---
id: claiming
title: Claiming & Resizing
sidebar_position: 1
---

## Making a claim

1. Select two opposite corners with the WorldEdit wand (`/lc wand` gives you one).
2. Run `/lc claim <name>`.
3. Confirm in the menu that opens.

Before the menu opens, LandClaim checks, in this order:

| Check | Fails with |
|---|---|
| You have `landclaim.claimregion` and own fewer claims than your `landclaim.regions.<number>` | "You don't have permission to claim or have claimed too many regions." |
| You have `landclaim.world.<this world>` | "You may not claim regions in this world." |
| The name is a valid WorldGuard region ID: letters, numbers and `_ - , ' + /`, no spaces | "That is not a valid region name." |
| You have a complete wand selection | "You must have two points selected." |
| No region in this world already has that name | "That region already exists." |
| The area doesn't overlap any WorldGuard region you don't own, claims and server regions alike | "This selection overlaps another player's region." |
| The area (length × width) is between `Claims.Regions.MinSize` and `MaxSize` | "This selection is too small/large!" |
| The long side is at most `Claims.Regions.MaxLWRatio` times the short side | "This selection doesn't meet the proportion requirements!" |

Operators skip the first two checks. Confirming charges the claim's price (see
[Economy](economy.md)) and creates the claim with you as its owner.

## What a claim is

A claim is a WorldGuard cuboid region that covers the full height of the world, from Y −64 to the
build limit, whatever heights you selected. LandClaim marks it with the WorldGuard flag
`land-claim-region: region`. Only regions with that marker count as claims for borders,
`/lc nearby`, `/lc requestjoin`, the leaderboard, BlueMap and the developer API.

Every new claim starts with `interact` and `use` set to **deny for non-members**. Players who
aren't in the claim can't open doors, press buttons or open containers, even where `__global__` or
an overlapping region would allow it. Building is already members-only through WorldGuard's normal
rules. Owners can open any of this up in the [Flag Editor](flags.md).

The tier, the village tag and the officer list are kept on the region as well, in the flags
`land-claim-village-tag` and `land-claim-officers`. Back up WorldGuard's region files and you have
backed up your claims.

## Resizing

Select the new area with the wand and run `/lc resize <claim>`. The claim keeps its name, players,
flags and claim spawn; only its corners change.

- Owners can resize their own claims; `landclaim.edit.others` can resize any.
- The new area has to pass the same overlap, size and proportion checks as a new claim.
- Only the blocks you add are charged. Shrinking is free and refunds nothing.

## Deleting

`/lc delete <claim>`, or the **Remove** button in the claim menu, opens a confirmation. Confirming
deletes the WorldGuard region. Owners need `landclaim.delete.own` (part of `landclaim.basic`);
`landclaim.delete.others` deletes any claim with the command, and `landclaim.edit.others` with the button.

## Turning an existing region into a claim

Any WorldGuard region becomes a LandClaim claim once it carries the marker:

```
/rg flag <region> land-claim-region region
```

Add its owner with `/rg addowner <region> <player>`. The default member lock-out is added on the
next restart.

## Plots

A plot is a lot inside a claim with its own owner, for example a town handing out land to its
residents. It is a WorldGuard region like any claim (marker `land-claim-region: plot`), one
priority above the claim it is in, so inside the plot its own owners, members and flags apply.

**Making one.** An owner or officer of a claim selects an area wholly inside it with the wand and
runs `/lc claim <name>`, the same as for a claim. The confirm menu says **Claim Plot**. It needs
`landclaim.claimplot` (part of `landclaim.basic`) and a plot limit, `landclaim.plots.<number>` or
`landclaim.plots.*`. A selection that crosses the claim's edge, or overlaps another plot, is refused.

**Price.** Area × `Claims.Plots.PricePerBlock`, at least `Claims.Plots.BaseCost`, paid by whoever
makes it. The land is already the claim's, so plots never use the free block allowance.

**Handing it over.** The plot's maker owns it at first. Invite a resident from the plot's
**Owners/Members** menu, have them `/lc accept`, then promote them to Owner in **Manage Players**.
Only players who are part of the claim can join one of its plots.

**Who can build in a plot:**

| Player | Inside the plot |
|---|---|
| The plot's owners and members | Yes |
| The claim's owners and officers | Yes, always: they are kept as members of every plot and can't be removed from one |
| Other members of the claim | No |
| Everyone else | No |

**Good to know:**

- Plots run the full height of the world, like claims.
- A plot stays inside its claim when resized, and a claim can't be shrunk past one of its plots.
- Deleting a claim deletes its plots.
- Plots don't have tiers: no tag, claim spawn, bank or town chat of their own. Town chat and the
  claim's tier still work inside them.
- `/lc requestjoin` inside a plot asks to join the plot when you are already part of the claim, and
  the claim itself when you are not.
