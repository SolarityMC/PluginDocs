---
id: message-customization
title: Message Customization
sidebar_position: 2
---

Chat messages and most menu text live in `plugins/LandClaim/lang/lang.yml`. Apply changes with
`/lc reload`.

## Format

Messages use [MiniMessage](https://docs.advntr.dev/minimessage/format.html), not `&` colour codes:

```yaml
invites:
  sent: "<gold>Invited</gold> <green>%player%</green> <gold>to</gold> <dark_purple>%regionName%</dark_purple><gold>.</gold>"
```

Gradients, hover text and click actions all work. The invite, join request and leave messages use
`<click:run_command:...>` for their **[Accept]**, **[Approve]** and **[Confirm]** buttons. If you
reword those, keep the commands as they are, including `%claimKey%`.

## Prefix

```yaml
prefix:
  enabled: true
  value: "<gray>[<dark_purple>ANO LandClaim</dark_purple>]:</gray> "
```

Put before every chat message when `enabled` is true.

## Sections

All messages sit under `en-us:`.

| Section | Messages for |
|---|---|
| `general` | No permission, unknown command, reload, wand given |
| `gui` | Main menu, claim list, claim menu, confirmation and removal menus |
| `claims` | Claim removed, `/lc nearby` on/off, `/lc tag` |
| `members` | Rank broadcasts (joined, promoted, demoted, removed, left) and rank errors |
| `invites` | Invites |
| `requests` | Join requests |
| `leave` | `/lc leave` |
| `nearby` | The `/lc nearby` claim list |
| `economy` | Charges and pooled allowance |
| `tiers` | "Requires Village/Town/City" |
| `townchat` | Town chat toggle and message format |
| `bank` | City bank |
| `leaderboard` | `/lc leaderboard` |
| `border` | Entering and leaving action bar |
| `teleport` | Claim spawn |
| `resize` | `/lc resize` |
| `errors` | Everything that can go wrong while claiming |

## Placeholders

| Placeholder | Where | Value |
|---|---|---|
| `%regionName%` | Most messages | The claim's name |
| `%claimKey%` | Invite, request and leave buttons | `world:name`, used in click commands |
| `%player%` | Ranks, invites, requests, bank, town chat | The player the message is about |
| `%actor%` | `members.removed`, `promoted`, `demoted` | The player who made the change |
| `%rank%` | `members.joined`, `promoted`, `demoted` | Owner, Officer or Member |
| `%inviter%`, `%time%` | `invites.sent`, `invites.received` | Who sent the invite; how long it lasts |
| `%seconds%` | `requests.cooldown` | Seconds left |
| `%radius%`, `%distance%`, `%direction%` | `nearby` | Search radius; distance and compass direction to a claim |
| `%amount%`, `%blocks%` | `economy`, `bank` | Money amount; charged blocks |
| `%balance%`, `%type%` | `bank` | Bank balance; DEPOSIT or WITHDRAW |
| `%money_missing%`, `%money_requirement%` | `errors.not-enough-money` | What you are short of; the full price |
| `%message%` | `townchat.format` | The chat message |
| `%rank%`, `%value%` | `leaderboard.entry-*` | Position; area, player count or balance |
| `%max%` | `claims.tag.too-long` | `Tiers.VillageTag.MaxLength` |
| `%command%` | `general.invalid-command` | What the player typed |

## Updating

When an update adds a message, it is added to your `lang.yml` on the next start with its default
text, ready to customise. Messages you have already changed are kept as they are.

## Text that isn't in `lang.yml`

The players, Manage Players, Add Player, Pending Join Requests, teleport and flag editor menus, the
chat prompt questions and countdown, and a few prompt errors are fixed text in this version.
