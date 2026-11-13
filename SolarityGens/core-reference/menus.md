---
id: menus
title: Menus
sidebar_position: 3
---

Nothing can be taken out of or put into these menus. Clicks closer together than
`menu.click-cooldown-ms` (300 ms by default, in `claimgens.yml`) are ignored, which stops
spam-click macros.

## Gen menu

Right-click one of your claim gens. Someone else's gen only tells you whose it is.

| Button | Does |
|---|---|
| **Info** (the gen's block, middle) | Level, output per hour, stored and storage cap, sell price per item, and the server booster if one is running |
| **Collect and Sell** (left) | Sells everything stored and pays you at once. Shows what it is worth right now |
| **Upgrade** (right) | Moves the gen to the next level. Shows the new speed, storage, sell price and the cost. Turns into **Max level** at the top |
| **Pick Up** (bottom) | Sells what is stored, removes the gen and gives it back as an item that keeps its level |

The menu redraws after every click, so the numbers are always current.

## Generator shop

`/gens` opens the shop. The top shows your balance and your gen slots. Each gen type shows its
category, tier and sell price, and one of:

- **Unlocked**: click to buy another gen of this type (if the type has a `buy-price`).
- **Locked**, requirement met: the unlock price; click to unlock. Unlocking gives one gen.
- **Locked**, requirement not met: a grey pane with the gen and level you need first.

Unlocking never replaces a gen you already have. See [Unlock Shop](../features-modules/unlock-shop.md).
