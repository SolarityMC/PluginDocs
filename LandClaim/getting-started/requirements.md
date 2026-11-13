---
id: requirements
title: Requirements
sidebar_position: 3
---

## Server

| | |
|---|---|
| Server software | Paper or Folia 26.2 or 26.3 (Canvas works too) |
| Java | 25 or newer |

## Required plugins

| Plugin | Notes |
|---|---|
| WorldGuard | Stores and protects every claim. Built against 7.0.19, tested on 26.2 with 7.0.19 and on 26.3 with 7.0.21. |
| WorldEdit | Players select claims with its wand. On Folia, use [FastAsyncWorldEdit-Folia](https://github.com/ANO-Development/FastAsyncWorldEdit-Folia), which provides WorldEdit. On 26.3 it must be 26.11.0 or newer: 26.10.3 only supports 26.2 and fails to start on 26.3, and WorldGuard and LandClaim fail with it. |

LandClaim does not enable without both.

## Optional plugins

| Plugin | Adds |
|---|---|
| Vault and an economy plugin | Charging for claimed land and the City bank. Without one, claiming is free. See [Vault](../integrations/vault.md). |
| BlueMap | A Land Claims layer on the web map. See [BlueMap](../integrations/bluemap.md). |
| A permissions plugin (LuckPerms) | Players need permission nodes to claim; see [Commands & Permissions](../core-reference/commands-permissions.md). |
