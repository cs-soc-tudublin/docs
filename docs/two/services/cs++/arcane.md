---
title: Arcane
created: 2026-10-17T22:00:00
modified: 2026-10-17T22:00:00
tags:
  - two
  - services
  - cspp
---

# **Arcane** - Our Docker Management UI

[**REPO**](https://github.com/getarcaneapp/arcane)

Arcane is a web UI for managing Docker hosts. It is intended to replace WatchTower.

Link: arcane.cspp.ie

**Owner:** see the [Ownership Table](../../../ownership/ownership-table.md)

## Features

- View and manage Docker containers, images and volumes
- Manage multiple Docker hosts as separate 'environments'
- Image update checks

Hosted on [Huey](../../vms/huey.md)

## Environments

Arcane manages Docker hosts, not Proxmox containers or VMs. Each Docker host is an 'environment'. Arcane can only see the Docker containers on the hosts that have been added.

Adding an environment gives Arcane control of that host's Docker, so only add a host with the agreement of whoever owns the services on it.

| **Environment** | **Host** | **Added by** |
| --------------- | -------- | ------------ |
| Local Docker    | Huey     | TODO         |
| TODO            | TODO     | TODO         |


