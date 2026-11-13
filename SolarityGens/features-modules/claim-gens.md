---
id: claim-gens
title: Claim Gens
sidebar_position: 1
---

Claim gens are owned generators placed inside a claim. They are the main income on GenSMP.

## How production works

A claim gen never ticks. It remembers how much it holds and when it was last brought up to date,
and works out what it has made since then whenever someone looks at it, collects, upgrades or
picks it up:

- Each level has an interval and an amount per cycle (level 1: one item every 10 seconds).
- A part-finished cycle carries over: nothing is lost by collecting at an odd moment.
- Production stops at the level's storage cap, and the clock restarts when the gen is full, so
  nothing builds up while it is capped. The default caps hold 30 minutes of output.
- Offline time counts the same way, up to the cap.
- An upgrade first settles what the gen made at the old level, then switches to the new one.

Because of this, the number of gens has no cost per tick, however many are placed.

## Levels

Every type shares one level table (`levels` in [`claimgens.yml`](../configuration/claim-gens-configuration.md)).
The defaults:

| Level | Interval | Storage | Sell multiplier | Upgrade cost |
|---|---|---|---|---|
| 1 | 10s | 180 | x1.00 | |
| 2 | 8s | 225 | x1.00 | 250 x the type's sell price |
| 3 | 6s | 300 | x1.20 | 450 x the type's sell price |
| 4 | 4.5s | 400 | x1.35 | 800 x the type's sell price |
| 5 | 3.5s | 515 | x1.50 | 1400 x the type's sell price |

Upgrade costs scale with the type, so a coal gen ($2 an item) costs $500 to reach level 2.

## Placing

A claim gen item places like a normal block, with these checks:

- It must go inside a claim you own or are a member of.
- You must have a free [gen slot](claims-and-slots.md), and the claim must have room for another gen.
- The item must belong to a gen the server knows and that isn't already placed. A copied or forged
  item is refused, not used up, and the attempt is written to the audit log.

Whoever places a gen owns it. Only the owner can collect, sell, upgrade or pick it up; other claim
members see whose it is.

## Selling

**Collect and Sell** in the [gen menu](../core-reference/menus.md#gen-menu) sells everything stored:

```
money = items x type sell price x level multiplier x server booster
```

The gen is emptied and the money paid in one step under the gen's own lock, so two clicks (or two
players) can never sell the same output twice. If the economy refuses the payment, the items go back
into the gen. Claim gens use their own prices from `claimgens.yml`, never ShopGUIPlus, and only the
[server booster](boosters.md#server-booster) applies to them.

## Picking up

**Pick Up** sells what is stored, removes the block and gives the gen back as an item. The item keeps
the same gen (its id and level), so placing it again brings the gen back exactly as it was.

## Protection

Claim gens can't be broken by hand (players are told to use Pick Up), and are protected from
explosions, pistons, fire (log gens burn), endermen and other mobs changing blocks, and flowing
liquids. Right-clicking one never strips a log or uses an item on it.

## Holograms

Each placed gen has floating text above it (a Text Display) with its name, level and stored amount.
It updates when the gen is used and every `hologram.update-seconds` (30 by default), never every
tick. Holograms are not saved with the chunk: they come back when the chunk loads, so a crash can't
leave stray copies. They carry the tag `solaritygens:hologram`, so entity clearers can be set to skip
them.
