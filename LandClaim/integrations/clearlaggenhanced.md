---
id: clearlaggenhanced
title: ClearLaggEnhanced
sidebar_position: 4
---

With ClearLaggEnhanced 26.10.1 or newer installed, its entity clears leave
peaceful mobs inside claims alone. Nothing to set up; it can be turned off with
`ClearLaggEnhanced.ProtectClaimMobs: false`.

## What's kept

A mob is kept when it is peaceful and stands inside a claim or a plot (any region marked
`land-claim-region`):

- farm animals, pets and horses,
- villagers and wandering traders,
- iron and snow golems,
- fish, squid, bats and allays.

Hostile mobs and dropped items inside claims are still cleared, so mob farms don't pile up.
Everything outside claims follows ClearLaggEnhanced's own settings.

Kept mobs are skipped by ClearLaggEnhanced's entity clearing and misc entity limiter, but still
count towards its mob limiter, so breeding and spawning in claims stay capped like everywhere else.
With ClearLaggEnhanced 26.10.1 itself they don't count, so claims there have no mob cap; use a newer
version.

## Settings

```yaml
ClearLaggEnhanced:
  ProtectClaimMobs: true
```

`/lc reload` applies a change straight away.

## Older ClearLaggEnhanced versions

Versions before 26.10.1 have no API for this. LandClaim logs one warning at startup and
ClearLaggEnhanced keeps clearing as it did before.
