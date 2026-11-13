---
id: message-customization
title: Message Customization
sidebar_position: 2
---

Every word players see is in `plugins/SolarityTournaments/messages.yml`. Apply changes with
`/tournaments reload`.

- Colours: `&` codes and `&#RRGGBB` hex.
- `%prefix%` is the `prefix` line at the top.
- Blank a message (`""`) to send nothing.
- A line that is exactly a token like `%podium%` or `%prizes%` is swapped for a whole block of lines,
  so leave it on its own line.
- Menu titles stay black (`&0`) so the resource pack can draw the menu art behind them.

## Sections

| Section | What it holds |
|---|---|
| top level | Chat replies, confirmations and moderation messages |
| `help`, `moderation-help`, `admin-help` | The command list for each permission level |
| `prize-delivered` | What a winner sees when their prize arrives |
| `announce` | The end-of-week chat announcement and title card |
| `discord` | The text of the Discord post |
| `format` | How weeks, dates and times are written |
| `place-colours`, `place-colour-other` | Gold, silver and bronze, then every other place |
| `placeholder` | What placeholders show for an empty place or a disqualified player |
| `menu` | Every menu title, item name and lore line |
