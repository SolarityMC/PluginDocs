---
id: common-issues
title: Common Issues
sidebar_position: 2
---

## "That player is not online. Invites can only be sent to online players."

Invites go to online players only. The player can send `/lc requestjoin` from inside the claim
later instead, and you can answer it from **Pending Join Requests**.

## "Your rank in this claim does not allow that."

Officers can only add and remove plain members; promotions, demotions and removing officers or
owners are for owners. See [Ranks](../features-modules/ranks.md).

## "A claim must keep at least one owner."

The player is the claim's only owner. Promote someone else to Owner first, then demote, remove or
leave.

## "That player is already part of this claim."

Invites and direct adds only bring in players who aren't in the claim yet. To change a rank, use
**Manage Players**.

## "You have more than one invite."

Name the claim: `/lc accept farm`, or click the **[Accept]** button in the invite message.

## "Stand inside a claim to request to join it."

`/lc requestjoin` asks to join the claim you are standing in. It has to be a LandClaim claim, not a
plain WorldGuard region.

## "Wait 120s before sending another join request."

There is a cooldown between join requests, set by `JoinRequests.CooldownSeconds`.

## "This feature requires Tier II (Village) or higher."

The claim needs more players. See [Tiers](../features-modules/tiers.md).

## "There is no teleport set for this claim."

An owner has to set the claim spawn first, from the claim's **Teleport** menu while standing inside it.

## "Prompt expired."

The chat prompt timed out before an answer was sent. Open the editor and try again, or raise
`Prompts.TimeoutSeconds` (`0` removes the limit).
