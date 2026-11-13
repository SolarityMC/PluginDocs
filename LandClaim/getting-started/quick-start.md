---
id: quick-start
title: Quick Start
sidebar_position: 1
---

Get players claiming land in about five minutes.

## 1. Install

Put LandClaim, WorldGuard and WorldEdit (FastAsyncWorldEdit-Folia on Folia) in `plugins/` and start
the server. See [Installation](installation.md) for the details.

## 2. Give players permission to claim

`landclaim.basic` gives players every normal command and menu, but claiming also needs two
permissions that say **how many** claims a player may own and **where**:

```
/lp group default permission set landclaim.basic true
/lp group default permission set landclaim.regions.3 true
/lp group default permission set landclaim.world.world true
```

- `landclaim.regions.<number>`: how many claims a player may own. The highest number they have wins;
  `landclaim.regions.*` removes the limit.
- `landclaim.world.<world name>`: a world they may claim in, one node per world. `landclaim.world.*`
  allows every world.

Operators skip both checks.

## 3. Make a claim

1. Run `/lc wand` (or click the wooden axe in `/lc`) to get the WorldEdit wand.
2. **Left-click** one corner of the area and **right-click** the opposite corner.
3. Run `/lc claim <name>`, for example `/lc claim farm`.
4. Click the green block in the confirmation menu.

The claim covers the whole column from bedrock to build height, whatever heights you clicked. You
are its owner, and players who aren't in the claim can't build or use doors, buttons and containers in it.

## 4. Bring friends in

Open `/lc list`, click the claim, then **Players** → **Add Player to Claim** → **Invite Player**, and
type a name. They get a chat message with **[Accept]** and **[Deny]** buttons. A player can also stand
in your claim and run `/lc requestjoin`; you get **[Approve]** and **[Deny]** buttons.

Promote a member to Officer from **Players** → **Manage Players** so they can invite people too. See
[Ranks](../features-modules/ranks.md).

## 5. Grow

At 4 players the claim becomes a Village and can set a tag and a claim spawn; at 7 a Town with its
own chat; at 11 a City with a shared bank and free expansion. See [Tiers](../features-modules/tiers.md).

## Useful commands

```
/lc                     # main menu
/lc list                # your claims
/lc nearby              # claims around you, with their borders shown
/lc resize <claim>      # move the claim to your current wand selection
/lc teleport <claim>    # go to the claim spawn
/lc leave <claim>       # leave a claim you are part of
```

The full list is in [Commands & Permissions](../core-reference/commands-permissions.md).
