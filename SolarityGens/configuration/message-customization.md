---
id: message-customization
title: Messages
sidebar_position: 3
---

Every chat message has a default built into the plugin. To change one, add its key under
`messages:` in `config.yml` and run `/gens reload`. A key you don't set keeps its default, and an empty
value (`""`) turns that message off.

Colours: legacy `&` codes, hex `&#RRGGBB` or `<#RRGGBB>`, `<gradient:#a:#b>` and `<rainbow>`.

## Prefixes

| Key | Used for |
|---|---|
| `prefix` | Put in front of every message to a player |
| `prefix-broadcast` | Put in front of server booster announcements |

## Claim gens

| Key | Placeholders | When |
|---|---|---|
| `claimgen-placed` | `%name%`, `%used%`, `%max%` | A gen was placed |
| `claimgen-place-no-claim` | | Placed outside any claim |
| `claimgen-place-not-member` | | Placed in a claim you don't belong to |
| `claimgen-place-slots` | `%max%` | All your gen slots are used |
| `claimgen-place-claim-full` | `%max%` | The claim holds as many gens as its size allows |
| `claimgen-place-duplicate` | | The item's gen is already placed (a copied item) |
| `claimgen-place-unknown` | | The item's gen isn't known (a forged item) |
| `claimgen-place-unknown-type` | | The gen's type was removed from config |
| `claimgen-break` | | Someone tried to break a gen |
| `claimgen-info-other` | `%name%`, `%owner%`, `%level%` | Right-clicked someone else's gen |
| `claimgen-not-owner` | `%owner%` | Used someone else's gen |
| `claimgen-sold` | `%amount%`, `%name%`, `%money%`, `%booster%` | Collect and Sell |
| `claimgen-nothing` | | Nothing stored yet |
| `claimgen-sell-failed` | | The economy refused the payout |
| `claimgen-upgraded` | `%level%`, `%money%` | Upgrade |
| `claimgen-max-level` | | Already at the top level |
| `claimgen-no-money` | `%money%` | Can't afford something |
| `claimgen-picked-up` | `%name%`, `%sold%` | Pick Up |
| `claimgen-returned` | `%amount%` | Gens from a deleted or left claim were handed back |
| `claimgen-unlocked`, `claimgen-bought` | `%name%` | Shop purchases |
| `claimgen-requirement` | `%name%`, `%level%` | Unlock requirement not met |
| `claimgen-locked`, `claimgen-not-for-sale`, `claimgen-already-unlocked` | `%name%` | Shop refusals |
| `start-done` | `%size%` | `/gens start` worked |
| `start-already`, `start-failed` (`%reason%`) | | `/gens start` refused |
| `expand-cost` | `%size%`, `%slots%`, `%money%` | `/gens expand` without confirm |
| `expand-done` | `%size%`, `%slots%` | Expanded |
| `expand-none`, `expand-max`, `expand-failed` (`%reason%`), `home-failed` | | Claim refusals |
| `claims-unavailable` | | Claim gens are off (database problem) |
| `global-booster-started`, `global-booster-ended` | `%by%`, `%multiplier%`, `%time%` | Server booster announcements |
| `global-booster-queued` | `%queue%` | A server booster was queued |

Admin messages: `admin-given`, `admin-unlocked`, `admin-setlevel`, `admin-reset-confirm`,
`admin-reset-done`, `not-looking-at-claimgen`, `claimgen-type-not-found`.

## Click-to-mine gens and general

`no-permission`, `player-only`, `usage`, `reloaded` (`%claim%`, `%count%`), `gen-not-found`, `given`,
`player-not-found`, `cannot-break`, `picked-up`, `not-looking-at-gen`, `removed`, `orphan-gen` (`%id%`),
`list-header`, `list-entry`, `list-empty`, `pickup-armed`, `pickup-disarmed`, `pickup-not-required`,
`resetstats-confirm`, `resetstats-done`, `toggle-on`, `toggle-off` (`%feature%`), `inventory-full`,
`feature-disabled`, `anvil-opened`, `enchanting-opened`, and the booster messages `booster-block-name`,
`booster-sell-name`, `booster-usage`, `booster-bad-type`, `booster-bad-block-mult`, `booster-bad-sell-mult`,
`booster-bad-duration`, `booster-given`, `booster-received`, `booster-activated`, `booster-expired`.
