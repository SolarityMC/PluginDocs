---
id: invites-join-requests
title: Invites, Join Requests & Leaving
sidebar_position: 3
---

Nobody is put into a claim without saying yes. Owners and officers send **invites**, players who want in
send **join requests**, and anyone can **leave** whenever they like.

## Invites

1. Open the claim, then **Players** → **Add Player to Claim** → **Invite Player**.
2. Type the name of an online player in chat.
3. They get: *Alex invited you to join farm.* **[Accept]** **[Deny]**

Clicking **[Accept]** (or typing `/lc accept`) brings them in as a Member and announces it to the
claim. **[Deny]** (or `/lc deny`) tells the inviter they declined.

- An invite lasts `Invites.ExpireSeconds` (default 300, at least 10). Both players are told when it
  runs out.
- Inviting the same player to the same claim again replaces the first invite and restarts its timer.
- A player with invites to several claims must name one: `/lc accept farm`.
- The inviter's rank is checked again when the invite is accepted. If they were demoted or removed in
  the meantime, the invite is no longer valid.
- Only online players can be invited.

## Join requests

A player who wants to join a claim stands inside it and runs `/lc requestjoin`. Inside a plot, the
request goes to the plot if they are already part of the claim around it, and to that claim if
they are not. A plot only takes players who are part of its claim, by invite or by request.

Every owner and officer of that claim who is online gets:
*Steve wants to join farm.* **[Approve]** **[Deny]**

**[Approve]** adds them as a Member; **[Deny]** tells them no. Owners and officers who were offline
find the request under **Players** → **Pending Join Requests**: left-click to approve, right-click to
deny. If nobody who can answer is online, the player is told the request is waiting there.

The typed versions are `/lc approve <player> <claim>` and `/lc reject <player> <claim>`.

- A request lasts `JoinRequests.ExpireMinutes` (default 30, at least 1). The player is told when it expires.
- A player can have one pending request per claim, and must wait `JoinRequests.CooldownSeconds`
  (default 120) between requests to any claim.
- A request that is also covered by an invite is settled when the invite is accepted.
- Everyone can send join requests by default. Remove `landclaim.requestjoin` to stop a group from
  sending them.

## Leaving

`/lc leave <claim>` asks *Leave farm? You will need a new invite to rejoin.* with a **[Confirm]**
button. The **Leave Claim** button in the players menu does the same. Confirming removes you and
tells the rest of the claim.

Any rank can leave, except a claim's only owner. See [The last owner](ranks.md#the-last-owner).

## After a restart

Invites, join requests and the request cooldown are kept in memory only. A restart clears them;
players simply send them again.
