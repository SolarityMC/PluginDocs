---
id: boosters
title: Boosters
sidebar_position: 4
---

There are two kinds of booster, and each applies to one kind of gen.

## Server booster

For claim gens. One player buys it (the store runs a console command) and everyone on the server
gets it:

```
/gens admin globalbooster <multiplier> <duration> [activated by]
```

- It multiplies the money from claim gen sales only. It never speeds up production or raises storage.
- It is capped at `global-booster.max-multiplier` (2.0 by default); a bigger multiplier is lowered to
  the cap.
- One runs at a time. Another one waits in a queue and starts when the current one ends.
- Starting and ending are announced to the whole server.
- The running booster and the queue are saved, so a restart doesn't lose them.
- `/gens admin globalbooster stop` ends the running one early.

Players see it in `/boosters`, and `%solaritygens_booster%` / `%solaritygens_booster_time%` show it
on scoreboards.

## Booster vouchers

For click-to-mine gens. Items given with:

```
/gens booster give <player> <block|sell> <multiplier> <duration> [amount]
```

- **Block** vouchers multiply how many items a click-to-mine gen drops (whole numbers: 2x, 3x).
- **Sell** vouchers multiply money from `/autosell` and from manual ShopGUIPlus sells (decimals: 1.25x).

A player right-clicks a voucher to start it (permission `solaritygens.booster.use`). One block and one
sell booster can run at a time; the same multiplier adds time, a different one replaces it. They keep
running while the player is offline and survive restarts. Vouchers never affect claim gens.

Voucher looks and the `/boosters` panel are set under `boosters:` in [`config.yml`](../configuration/main-configuration.md#boosters).
