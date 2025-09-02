---
title: Proxmox
created: 2025-08-04T14:12:57
modified: 2025-09-02T17:08:01
tags:
   - one
   - os
---

# **PROXMOX** - Our Main OS

Proxmox, full name 'Proxmox Virtual Environment' is an open source 'Server Management System' that is designed for using Virtual Machines and 'Linux Containers', as well as being a simple way to have multiple servers work together.

In this model where servers are 'clustered' together, servers are usually referred to as 'nodes'.

Proxmox is widely used by cloud companies like Hetzner or Contabo who offer Virtual Private Servers for rent.

In CS++, we use Proxmox for the following features:

- High Availability
- Migration
- Remote Management
- Scalability
- Ease of Use

## What is *High Availability*?

The concept of High Availability is the process of making it very hard for systems to fail.

CS++'s services are mission critical both for ourselves and other societies, so we want to make sure that any failures are quickly recovered with minimal downtime and no data loss.

In Proxmox, when we configure High Availability, the other nodes can detect if one has gone down and will automatically recover the processes running on that failed node and continue them on another.

We can also manually set one of our nodes to be in maintenance mode, and the services will automatically 'migrate' to other nodes until we take it out of maintenance

## What is *Migration*?

Migration is the act of moving Virtual Machines or Containers from one node to another.

It can migrate VMs with practically zero downtime.

The way it does this is really cool:

When a VM is instructed to migrate, it begins to copy the VM's memory from one node to another, when most of the memory is copied, it quickly pauses the VM to copy the last bit of memory and the CPU instructions & registers to put on the new node. Then it unpauses the container on the new node and the migration has completed.

For example, if you were running a Minecraft server on a VM and migrated it between hosts, the downtime is so short that no clients would be disconnected and they would  experience basically no lag at all!

When it comes to Linux Containers, there is downtime. This is related to the fact that Containers run on the host kernel, as opposed to virtualising their own.

For the trade-off of lower resource requirements and less latency, downtime of up to a few seconds is acceptable when it comes to services that can be offline for a few seconds.

## When to Choose What?

If you have services where uptime is critical (Minecraft Servers, Mail servers, etc.), choose a VM.

If you have services that need to run light, and small seconds of downtime are acceptable (Monitoring, websites, etc.) a Container is totally fine.

## *What Next?*

Find out specifically what a [Virtual Machine](../what-is-a-vm.md) or [Container](../what-is-a-container.md) is.

Maybe you want to learn about the OS we use on our Virtual Machines, [Debian](./debian.md).

Or, to learn how we keep Data Highly Available, learn about [Ceph](../what-is-ceph.md)
