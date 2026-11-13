---
id: faq
title: FAQ
sidebar_position: 1
---

## Do I need to migrate anything after updating?

No. Existing owners stay owners and members stay members. Nobody is an officer until someone is
promoted. Settings and messages that are new in an update are added to your `config.yml` and
`lang.yml` on the next start, with their defaults; your own values are kept.

## Can a player be in more than one claim?

Yes, at any rank, in as many claims as they like. The `landclaim.regions.<number>` limit only counts
claims a player **owns**.

## Does an officer count toward the claim's tier?

Yes. Tiers count owners, officers and members alike.

## How do I make an area unclaimable?

Cover it with a WorldGuard region owned by nobody (or by staff). A claim can't overlap a region the
player doesn't own.

## Can I give one player more claims than the rest?

Yes. The highest `landclaim.regions.<number>` a player has wins, so give their group or the player a
bigger number.

## Can claims have a height limit?

No. A claim always covers the full height of the world.

## Do invites survive a restart?

No. Invites, join requests and the request cooldown are kept in memory and cleared on restart.

## Can I use LandClaim without an economy?

Yes. Without Vault and an economy plugin, or with `Economy.Enabled: false`, claiming is free. Only
the City bank needs an economy.

## Can staff edit any claim?

Yes, with `landclaim.edit.others` (part of `landclaim.admin`). Staff act as an owner in every
claim and can add players directly without an invite. Even staff can't remove a claim's last owner.
