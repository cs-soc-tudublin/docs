---
title: What is in a Server?
created: 2025-08-01T20:19:04
modified: 2025-08-01T21:19:51
tags:
   - zero
   - hardware
   - server
---

# **WHAT IS IN A SERVER?**

(This page expects some knowledge of PC hardware)

Servers share most parts with other CPUs, but they're usually specialised to Server usecases. Let's talk about the primary differences.

## CPU

Servers regularly have anywhere from 1 to 4 CPUs, though can occasionally go higher (8 or even 16 CPUs). The motherboards in servers with multiple sockets are able to properly direct instructions and data to multiple CPUs.

Server-grade CPUs are normally on-par with consumer-grade CPUs, but make up for it when it comes to Core and Thread count. For example, [`Mallard`](servers/mallard.md) has 2 CPUs, each with 24 cores and 48 threads. That's 96 threads in a single server!

They will usually also have larger caches.

Atop this are other optimisations like multi-threading, better continuous operation, higher RAM limits, etc.

## RAM

The largest difference between consumer RAM and server RAM is the 'Error Correcting Code', or ECC feature.

ECC constantly checks the contents of the RAM for any incorrect bits and fixes them. This comes at the cost of speed and money. But these are acceptable costs when you need to make sure you do not have incorrect memory crashing application, or writing incorrect values to essential databases.

## Storage

Interestingly, server storage is very similar to PC storage. NVMes, HDDs and SSDs are very common. But the *method* of communication is often different.

All consumer drives use SATA (**S**erial **A**dvanced **Technology** **A**ttachment) which can run at a maximum of 6Gb/s.

Servers need drives that can read and write at high speeds, and are reliable, so the main interface for storage is SAS (**S**erial **A**ttached **S**CSI) which can run at a maximum of 22.5Gb/s (Though none of our servers can handle that speed). Even SAS Hard-Disk Drives can operate at SAS-3 (12GB/s) speeds by moving at 15,000RPM.

Servers regularly have significantly more slots for storage, and support 'RAID' (**R**edundant **A**rray of **I**ndependent **D**isks) which allows you to combine disks together to act as a single disk. This allows you to handle drive failures and improve read / write speeds.

## Power Supply Units

Servers almost always have 2 or more PSUs. A single PSU can run the entire server on it's own.

Redundancy is the name of the game when it comes to servers, and it should be able to automatically switch to the other PSU with no downtime.

These PSUs are normally connected to separate sources of power on separate breakers, and usually one or more of the PSUs are connected to a battery backup (UPS).

Data Loss and OS Corruptions would be disastrous for servers, and servers aren't designed to handle sudden power loss events, so battery backups give the servers a few minutes (normally no more than 15 minutes) to finish what it is doing, and gracefully shutdown.

## Network Interface Cards

Everything to do with technology is online now, so servers need to be able to receive lots of data and transmit lots of data.

Servers have NICs (**N**etwork **I**nterface **C**ards) which connect to the local network. There are two types of ports on NICs, [RJ45](https://cdn.taoglas.com/wp-content/uploads/2024/07/what-is-rj45.jpg) (Ethernet) ports, and [SFP](https://www.optcore.net/wp-content/uploads/Acatel-Lucent-SFP-port-700px.jpg) (**S**mall **F**orm-factor **P**luggable) ports. The RJ45 ports rarely exceed 1 - 2.5Gb/s, but the SFP ports regularly exceed 10Gb/s (25, 40, and 100GB/s).

SFP ports allow multiple connectors to be attached, from RJ45 adapters, to Copper and Fibre Optic.

Servers normally have multiple NICs for redundancy, and the multiple ports may be utilised in a way where only one port is connected to the internet, and the other ports are used for faster local-only communications.

## iDRAC / iLO

To allow remote control and monitoring of a server at a hardware level (Including setting fan speeds, installing OSes, rebooting, etc.), all servers have a mini-computer inside of it that can be accessed remotely to complete these tasks.

For Dell, this is called the iDRAC (**I**ntegrated **D**ell **R**emote **A**ccess **C**ontroller), and for HP, iLO (**I**ntegrated **L**ights **O**ut).

These are powered if the server is getting power (Even if the server is off!) and has it's own connection to the network.

## Peripherals

Most servers use old standards for I/O. All of our servers have [VGA](https://upload.wikimedia.org/wikipedia/commons/8/81/Vga-cable.jpg), invented in 1987 for displays, and many older servers use [PS/2](https://upload.wikimedia.org/wikipedia/commons/thumb/5/54/PS2_keyboard_and_mouse_jacks.jpg/330px-PS2_keyboard_and_mouse_jacks.jpg) for Keyboards and Mice, but our servers use USB thankfully.

Some servers still even have [Serial](https://res.cloudinary.com/rsc/image/upload/b_rgb:FFFFFF,c_pad,dpr_2.625,f_auto,h_214,q_auto,w_380/c_pad,h_214,w_380/Y2369145-01?pgw=1).

Modern technologies and ports use more intensive communications standards, so it's better to use simple standards. This also means customers with thousands of servers do not need to spend a lot of money on upgrading all of their connectors when buying new servers.

If it ain't broke, don't fix it!

## *What Next?*

Check out our servers and their specs:

- [Mallard](servers/mallard.md)
- [Ruddy](servers/ruddy.md)
- [Pancakes](servers/pancakes.md)
- [Muscoy](servers/muscovy.md)
Or, [what is a router?](./what-is-a-router.md)
