---
id: ranks
title: Ranks
sidebar_position: 2
---

Everyone in a claim has one of three ranks: **Owner**, **Officer** or **Member**.

## What each rank can do

| | Owner | Officer | Member |
|---|:-:|:-:|:-:|
| Build and use the claim (WorldGuard member access) | ✓ | ✓ | ✓ |
| Invite players, answer join requests | ✓ | ✓ | |
| Remove members | ✓ | ✓ | |
| Remove officers and owners | ✓ | | |
| Promote and demote | ✓ | | |
| Flag Editor | ✓ | | |
| Set or remove the claim spawn | ✓ | | |
| Resize and delete the claim | ✓ | | |
| Set the village tag | ✓ | ✓ | ✓ |
| Use the City bank | ✓ | ✓ | ✓ |
| Leave the claim | ✓ | ✓ | ✓ |

Owners can promote anyone up to Owner and demote anyone, including other owners. Officers only ever
deal with plain members: they can bring members in and take them out, but can't change anyone's
rank. Invites and join requests always bring a player in as a Member; higher ranks come from a
promotion.

Admins with `landclaim.edit.others` can do everything an owner can in every claim, and can add
owners and members directly without an invite.

## Promoting and demoting

Open the claim, then **Players** → **Manage Players**, and click the player. **Promote** moves them
up one rank and **Demote** down one rank; **Remove from claim** asks for confirmation first. A
player moved between ranks never has to be removed and added again.

## The last owner

A claim always keeps at least one owner. Its only owner can't be demoted or removed, not even by an
admin, and can't leave. Promote someone else to Owner first; then either of you can step down.

## Broadcasts

Every change is announced to everyone in the claim who is online, plus the player who made it:

- *Steve joined farm as Member.*
- *Steve was promoted to Officer in farm by Alex.*
- *Steve was demoted to Member in farm by Alex.*
- *Steve was removed from farm by Alex.*
- *Steve left farm.*

A player who was just removed still gets the message. The wording is in the `members` section of
`lang.yml`; see [Message Customization](../configuration/message-customization.md).

## How ranks are stored

Owners and members are WorldGuard's own owners and members of the region. Officers are WorldGuard
members whose UUID is also listed in the region's `land-claim-officers` flag. To WorldGuard an
officer is simply a member, so officers have exactly the same access to the land as members; the
extra rank only matters inside LandClaim.

Each player holds exactly one rank. Older claims sometimes list a player as both owner and member;
LandClaim shows them once, as Owner, and drops the extra entry the next time their rank changes.

Officers count toward the claim's [tier](tiers.md) like everyone else.
