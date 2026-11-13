---
id: discord
title: Discord
sidebar_position: 4
---

When a week ends, the results can be posted to a Discord channel through a webhook.

1. In Discord: Edit Channel > Integrations > Webhooks > New Webhook, and copy its URL.
2. Put it in `discord.webhook-url` and set `discord.enabled: true`.
3. Run `/tournaments reload`.

Treat the URL like a password: anyone holding it can post to that channel.

| Key | Default | What it does |
|---|---|---|
| `enabled` | `false` | Post the results |
| `webhook-url` | `""` | The webhook URL |
| `username` | `SolarityMC` | The name the post shows |
| `avatar-url` | `""` | The avatar the post shows |
| `color` | `#55E0FF` | The embed's side colour |
| `mention` | `""` | A role to ping, e.g. `<@&123456789012345678>`. Only this role can be pinged |
| `places` | `3` | How many places to list per board |

`/tournaments preview` prints the post for the live standings to the console, and
`/tournaments post confirm` sends it now. The post's text is in the `discord` section of `messages.yml`.
