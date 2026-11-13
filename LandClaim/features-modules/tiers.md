---
id: tiers
title: Tiers
sidebar_position: 4
---

A claim's tier comes from how many players it has: owners plus officers plus members. It is worked
out live every time, so it always matches the claim's current players and goes down again when
players leave.

| Tier | Players (default) | Unlocks |
|---|---|---|
| I · Settlement | 1–3 | Claiming, ranks, flags |
| II · Village | 4–6 | Village tag, claim spawn |
| III · Town | 7–10 | Town chat |
| IV · City | 11+ | City bank, free expansion |

Each tier keeps everything from the tiers below it. The ranges are set under `Tiers` in
`config.yml`; see [Main Configuration](../configuration/main-configuration.md#tiers).

## Village tag (Village)

`/lc tag <claim> <text>` gives the claim a tag, shown next to its name on [BlueMap](../integrations/bluemap.md).
Spaces are fine; the length limit is `Tiers.VillageTag.MaxLength` (default 24). Anyone in the claim
can set it.

## Claim spawn (Village)

Owners set a teleport point from the claim's **Teleport** menu while standing inside the claim.
Players then use `/lc teleport <claim>` or the menu's ender pearl to go there. Below Village the
menu shows **Claim Spawn Locked**.

## Town chat (Town)

`/lc townchat` toggles town chat for you. While it is on and you stand inside a Town-tier (or higher)
claim you belong to, your chat messages go only to the players standing inside that claim, and to
the console. Step outside the claim and your messages go to public chat again.

The toggle lasts until you turn it off or the server restarts. The format is `townchat.format` in
`lang.yml`.

## City bank (City)

City claims get a shared bank that uses the server's Vault economy.

```
/lc bank deposit <claim> <amount>
/lc bank withdraw <claim> <amount>
/lc bank log <claim>
```

- Anyone in the claim can deposit, withdraw and read the log, given the matching
  `landclaim.bank.*` permission. Grant only `landclaim.bank.deposit` and `landclaim.bank.log` if you
  want withdrawals limited to staff.
- Every deposit and withdrawal is logged with the player's name.
- Balances are stored in `plugins/LandClaim/citybanks/<world>_<claim>.yml`. A claim that drops below
  City keeps its balance and gets access again when it grows back.
- Deleting a claim closes its bank. What is left goes to the player who deletes it, if they own
  it; when an admin deletes someone else's claim, the balance is split between its owners. The file
  moves to `citybanks/deleted/` with its log, so a new claim with the same name starts empty.

## Free expansion (City)

Resizing a City claim is always free. See [Economy](economy.md).

## Leaderboard

`/lc leaderboard size|members|bank` shows the top 5 claims by area, player count or City bank
balance. The ranking is refreshed in the background every `Leaderboard.RefreshMinutes` (default 5),
so a change can take that long to appear.
