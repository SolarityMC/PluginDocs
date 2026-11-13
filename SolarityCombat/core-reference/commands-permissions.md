---
id: commands-permissions
title: Commands & Permissions
sidebar_position: 1
---

## Commands

### Players

Aliases: `/ct`, `/combat`.

| Command | What it does | Permission |
|---|---|---|
| `/combattag` | Show how long you stay in combat | none |
| `/combattag bypass` | Turn your own combat bypass off or back on, to test as a normal player | `solaritycombat.bypass` |

### Admins

| Command | What it does | Permission |
|---|---|---|
| `/solaritycombat` | Reload `config.yml` and the item caps. The reply shows the caps that loaded. Alias `/scombat` | `solaritycombat.admin` |
| `/killtokens give <player> [amount]` | Give an online player Kill Tokens | `solaritycombat.killtokens.admin` |
| `/killtokens get [amount]` | Give yourself Kill Tokens | `solaritycombat.killtokens.admin` |

`/killtokens` aliases: `/killtoken`, `/ktokens`. The amount defaults to 1 and can be up to 2,304 (a
full inventory of stacks). Whatever doesn't fit is dropped at the player's feet. Bedrock names work
with or without the leading `.`. It works even when `kill-tokens.enabled` is `false`.

## Permissions

| Permission | Default | What it allows |
|---|---|---|
| `solaritycombat.admin` | op | `/solaritycombat`. Includes `solaritycombat.killtokens.admin` |
| `solaritycombat.killtokens.admin` | op | `/killtokens` |
| `solaritycombat.bypass` | op | Never combat tagged, and no combat restrictions apply |
| `solaritycombat.itemcap.bypass` | op | Ignore the item caps |
