---
title: How to Spec a Server
created: 2025-08-01T23:02:01
modified: 2025-08-01T23:41:24
tags:
  - zero
  - hardware
  - server
---

# HOW DO WE SPEC A SERVER?

Servers are usually bought to fulfil a specific purpose. The purpose informs the components install (Called the 'Specification' or 'specs').

Components can be replaced and updated, but some components are easier to change than others, so usually they are spec'd to remain as-is for a long time (Sometimes the complete service life of the server).

## Why Don't We just Buy the Best Hardware out There?

The simple answer is **COST**! Servers are significantly more expensive than Consumer hardware as it's designed to last much longer than a PC.

Also, since buying a server isn't a subscription, manufacturers will charge a higher cost so they can survive without every company buying thousands of new servers each year.

## How Do We Pick the Specs?

To talk about how we approach specing a server, we're going to consider 3 examples of what a server would do:

- Versatile High-Performance Compute
- AI, Video & Simulation Workloads
- Data Storage

As a note, assume that all of these examples include room for expansion.

### 1. Versatile High-Performance Compute

These servers are designed simply to be able to handle lots of requests, run lots of applications and be an all-rounder.

**CPU:**

The first focus would be on the CPUs. You'd want modern, high-speed and high-core / thread CPUs that allow multi-threading and parallel processing. Larger cache sizes would mean more data can be stored closer to the CPU so it has to wait less.

**RAM:**

Your next focus would be the RAM. RAM is the next step in the [Memory Hierarchy](https://media.geeksforgeeks.org/wp-content/uploads/20250111112435920586/Memory-Hierarchy-Design.webp). Having more RAM means more of the application / data is ready to be processed by the CPU. ECC ram is a MUST for servers to make sure no invalid data is read or written.

RAM speeds are also important, you'll want something that isn't too slow, or else your CPUs waste clock cycles waiting for data to be read off disk.

**Storage:**

Compute servers don't need that much storage. Their storage needs include:

- Space for the OS
- Space for all the applications running
- Space for just the essential data it's storing to do it's job

All the additional storage needs are usually fulfilled by a Storage Server that it talks to through the network.

The focus here would normally be data redundancy and access speed.

You don't need super redundancy, and you don't need exceptionally fast disk access, but you don't want to go outdated.

A common approach is SSDs for the OS and applications, and HDDs for the data. Remember, with SAS you can get 6Gb/s of data transfer from spinning disks!

**Networking:**

When deciding on networking, you should have a pretty good expectation of what the server will be doing on the network. How many requests per second will it be getting? What are the size of the responses it will be replying with?

We do not need the fastest speeds out there. Remember, we are bottlenecked by the networking hardware we attach to.

If our switches and routers can only handle 1Gb/s, then it makes no sense to get faster hardware unless you specifically plan to upgrade your networking hardware early into the service life of this server.

Redundancy is the aim of the game, so you'd want at least 2x RJ45 or SFP ports.

Having multiple ports also allows you to connect to multiple networks! You could have a 10Gb/s connection to your Storage Server network and other servers, but only a 1Gb/s link to the internet if it fits your use-case.

### 2. AI, Video and Simulation Workloads

If you're building a Video Rendering server, Physics Simulating or AI server, your primary focus will be your GPU. GPUs are primarily for graphical processing, but are exponentially faster at Vector mathematics and Parallel Processing when compared to CPUs.

 GPUs really shine in AI, Video and Simulation workloads (Among other things), so some servers have a GPU installed to fulfil this purpose.

**GPU:**

Workloads which require a GPU have gotten incredibly resource heavy in the last few years, so normally when specing a GPU server, your GPU(s) will be your most expensive part(s) by far, as being close to the bleeding edge is important to not having to upgrade / retire the hardware early.

**CPU:**

You will still need a powerful CPU as networking and Disk operations are handled by the CPU, but since the majority of the requirements go to the GPU, you can relax the requirements here.

**RAM:**

All of these workloads usually have very large datasets to go with it, so a significant amount of RAM is recommended. GPUs have their own VRAM (Video RAM), but the standard RAM will usually be used when downloading and uploading the data to and from the server.

**Storage:**

As stated above, datasets for these workloads tend to be quite large. So large amounts of high-speed onboard storage is a must-have.

This storage does not have to be bleeding edge, but should be quite roomy.

**Networking:**

Like the High-Performance Compute example above, you'll want speeds that match your network speeds, and especially your internet speed. If any upgrades in these areas are expected, you'll want to overspec on the server as the later upgrade will match the server's hardware.

### 3. Data Storage

Running a single (or a few) Network Attached Storage (NAS) Servers for archival, backup and block storage reasons is very common when specing out a multi-server system. These servers are usually much more powerful than you may think!

**CPUs:**

You will want fast CPUs, not as much as the High-Performance Compute server. But the CPU in this system will be spending most of it's time reading and writing to disk, as well as doing parity calculations, array rebuilds, (de)compression, encryption, etc.

**RAM:**

RAM should be one of your biggest focuses here. The more RAM you have, the more data you can copy into memory to respond to requests faster.

High speeds will also be vital!

**Storage:**

It's a storage server. Load this up with as much storage as you possibly can!

**DO NOT FORGET:** Data loss here can be catastrophic! Data Storage server will regularly use RAID to allow for the loss of one or more drives without incurring data loss. Some may even configure 'hot spares', which are drives that do nothing until another drive dies and it jumps in to store the data while the failed drive is replaced.

Depending on how you want to use this server (Archival or just block storage) will tell you whether to focus on Drive speeds or drive capacity. Some requirements may require self-encrypting drives.

**Networking:**

You need a networking hardware that *RIPS*!

You need to be able to pull data down and throw data off as fast as possible!

It would be really bad if the network connection for this server gets saturated and it's unable to keep up with demand, as this means servers will be wasting precious clock cycles waiting for it's data.

## *What Next?*

Take a look at the specs for our 4 servers, and our laptop!

- [Mallard](./servers/mallard.md)
- [Ruddy](./servers/ruddy.md)
- [Pancakes](./servers/pancakes.md)
- [Muscovy](./servers/muscovy.md)
- [Runner (Laptop)](./other/runner.md)

Or get started on networking by asking [what is a Router?](./what-is-a-router.md)
