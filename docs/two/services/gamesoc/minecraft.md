---
title: Minecraft Server
created: 2025-10-16T15:16:59
modified: 2025-10-24T19:44:34
tags:
  - two
  - gamesoc
  - services
---

# **Minecraft Server**

[**REPO**](https://github.com/itzg/docker-minecraft-server)

This is a server at mc.gamesoc.ie

The server is also joinable through bedrock clients using port 19132

The map is hosted at [map.gamesoc.ie](https://map.gamesoc.ie)

**Plugins** - These files are hosted locally at [files.int.cspp](../cs++/zipline.md). They are downloaded through the docker compose at a static link. You only need to update the hosted files url, when updating. Adding/removing plugins requires an edit of the docker-compose

- Bluemap
- CoreProtect
- DiscordSRV
- EssentialsX
- EssentialsXChat
- EssentialsXProtect
- EssentialsXSpawn
- Floodgate
- Geyser
- LibertyBans
- LuckPerms
- MiniMOTD
- ProtocolLib
- Tectonic
- ToolStats
- Vault
- ViaBackwards
- ViaVersion
- WorldEdit
- Worldguard

Hosted on [Dewey](../../vms/dewey.md)
