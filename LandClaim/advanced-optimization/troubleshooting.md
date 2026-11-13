---
id: troubleshooting
title: Troubleshooting
sidebar_position: 2
---

## LandClaim doesn't enable

It needs WorldGuard and WorldEdit. Check the console at startup for either one failing to load. On
Folia, plain WorldEdit isn't Folia-supported; install FastAsyncWorldEdit-Folia.

## "You don't have permission to claim or have claimed too many regions."

The player is missing `landclaim.claimregion`, or has no `landclaim.regions.<number>` node, or already
owns that many claims. `landclaim.basic` doesn't include a claim limit. Grant one:

```
/lp group default permission set landclaim.regions.3 true
```

## "You may not claim regions in this world."

The player needs `landclaim.world.<world name>` for the world they stand in, or `landclaim.world.*`.

## "This selection overlaps another player's region."

Claims run from bedrock to build height, so a selection overlaps any region above or below it as
well, including spawn or other server regions. Stand somewhere else, or check what is there with
`/rg list` and `/rg info`.

## The claim was made, but visitors can still use doors and chests

Check the claim's `interact` and `use` flags in the Flag Editor, or with `/rg info <claim>`. New
claims deny both to non-members. If an owner set `interact` to Allow, `use` follows it. A
higher-priority region overlapping the claim can also allow it.

## Borders don't show

- `Claims.Border.Enabled` must be `true`.
- The player may have turned them off with `/lc nearby off`; `/lc nearby on` brings them back.
- Only claims marked `land-claim-region: region` get borders; plain WorldGuard regions don't.
- `Claims.Border.Material` must be a block. An unknown name falls back to ochre froglight.

## Players can't find the Add Player, Flag Editor or Remove button

- **Add Player to Claim:** owners and officers with `landclaim.addplayer`.
- **Flag Editor:** owners with `landclaim.flageditor`. Officers and members don't get it.
- **Remove:** owners with `landclaim.delete.own`, the same node as `/lc delete`.

## Claiming is free even though `Economy.Enabled` is true

No Vault economy was found. Check that Vault and an economy plugin are installed and loaded. On
Folia, the economy plugin must also be Folia-supported.

## A message shows "An error occured finding lang section …"

That message key is missing from both your `lang.yml` and the jar. Check the spelling and indentation
of the keys you edited.

## The leaderboard is behind

It rebuilds every `Leaderboard.RefreshMinutes` (default 5), not on every change.
