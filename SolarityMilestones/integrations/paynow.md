---
id: paynow
title: PayNow
sidebar_position: 2
---

Store Support reads completed orders straight from PayNow's Management API. No PayNow plugin is needed
on the server.

## Setting it up

1. In the PayNow dashboard, open your store's **Settings → API Keys** and make a key with order read access.
2. Put the key in `paynow.api-key` and the numeric store id in `paynow.store-id`.
3. Keep `paynow.enabled: true` and run `/solaritymilestones reload`.

The startup block shows `polling every 60s` when it's running, `off` when `enabled` is false, and
`not set up` when the key or store id is missing.

## How spending is counted

- On start and on every reload, the plugin reads the store's whole completed-order history once, then
  checks for new orders every `refresh-seconds`.
- Only orders whose customer has a linked Minecraft account count. Each order is counted once.
- For every player the plugin keeps a baseline: how much it has already added. Only the amount above
  that baseline is added to Store Support, so restarts and reloads never count an order twice.
- A season reset keeps the baselines, so the new season starts at $0 and only new purchases count.
- On a fresh install the baseline starts at zero, so the first sync adds each player's whole PayNow
  history to the current season.
- An online player gets the `purchase-tracked` message when a purchase is added.

If PayNow can't be reached or rejects the key, the console warns once and keeps trying. A `401` or
`403` means the key is wrong or lacks order read access.
