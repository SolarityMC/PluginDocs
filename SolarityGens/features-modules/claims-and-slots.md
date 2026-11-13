---
id: claims-and-slots
title: Claims & Slots
sidebar_position: 3
---

Claim gens live in claims. SolarityGens owns the season rules (claim sizes, where starter claims go,
prices and gen slots); the claim provider only stores claims and says who belongs to them.

## Claim provider

`claims.provider` in `claimgens.yml` picks where claims come from. It is read at startup, so restart
after changing it.

- **`landclaim`** (the default): claims are [LandClaim](../integrations/landclaim.md) claims.
  LandClaim protects them and keeps their owners, officers and members; SolarityGens creates and
  grows them. Everyone in a claim can place gens in it.
- **`dev`**: square claims kept by SolarityGens itself in `claimgens.db`. They have no protection
  (anyone can build in them) and only decide where gens can go. For testing only.

If `landclaim` is chosen but LandClaim is missing or older than 26.11.0, SolarityGens falls back to
dev claims only when `claims.dev.enabled` is `true`, with a warning. Otherwise it warns that claim gens
can't be placed and `/gens start` won't work until LandClaim is fixed. Switching providers doesn't
move existing claims.

## /gens start

Once per player. It:

1. Creates a starter claim (the first size step, 15x15 by default) in the next free cell of a grid in
   `claims.world`. Cells are `claims.grid.cell-size` blocks apart, `columns` to a row, starting at
   `origin-x` / `origin-z`, so claims can grow to the largest size without touching. A cell that
   overlaps another claim or region (spawn, the warzone) is skipped, up to 20 cells in a row. A player
   who already owns a claim keeps it instead.
2. Unlocks the starter type and gives `starter.amount` starter gens.
3. Teleports the player to the claim (if `starter.teleport` is on): to its LandClaim claim spawn if it
   has one, otherwise to a safe block near the middle.

`/gens home` teleports there again later.

## Gen slots

The `claims.sizes` table sets, for each claim size, how many gens one player may place and how many
gens one claim may hold. The defaults:

| Claim size | Slots | Expansion cost |
|---|---|---|
| 15x15 (start) | 3 | free |
| 21x21 | 4 | $17,000 |
| 27x27 | 5 | $46,000 |
| 33x33 | 6 | $92,000 |
| 39x39 | 7 | $230,000 |
| 45x45 | 8 | $461,000 |

A player's slots come from the largest claim they own (the starter size if they own none). Both
limits apply when placing: a team can't stack every member's gens in one small claim.

## /gens expand

Grows your largest claim to the next size, around its centre. `/gens expand` shows the size, the slots
it gives and the price; `/gens expand confirm` charges and expands. If the claim can't grow (it would
overlap another claim or region) the money is refunded.

## When a claim is deleted or someone leaves

With LandClaim, when a claim is deleted every gen in it is taken out: what it had stored is sold to the
gen's owner, the block and hologram are removed, and the gen goes back to its owner as an item. The
same happens to a player's own gens when they leave a claim or are removed from it. An owner who is
offline is paid straight away and gets the items when they next join, also after a restart. The
gens keep their level.
