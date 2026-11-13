---
id: requirements
title: Requirements
sidebar_position: 1
---

## Server

- Minecraft 26.3 or newer
- Paper or Folia (Canvas works too)
- Java 25 or newer

## Optional plugins

None of these are needed to load. Without them the categories they feed stay at zero.

| Plugin | What it adds |
|---|---|
| SolarityGens | Feeds the Blocks Mined category |
| PlaceholderAPI | The `%solaritymilestones_...%` placeholders |

Store Support needs a PayNow store and a Management API key, set in `config.yml` (see
[PayNow](../integrations/paynow.md)). The reward commands in the default config use `money` and
`coin`, so they need whatever plugins provide those commands on your server.
