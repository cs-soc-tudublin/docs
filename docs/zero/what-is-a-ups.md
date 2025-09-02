---
title: What is a UPS?
created: 2025-08-03T17:09:24
modified: 2025-09-02T17:08:01
tags:
   - zero
   - hardware
   - power
---

# What is a UPS?

It should be abundantly clear by now that redundancy is at the core of servers and networking.

This extends to power, too. Without power, these servers can do nothing.

An unexpected power loss event can be catastrophic for servers, servers and Server OSes are not designed for unexpected power loss. This can cause OS corruption, data loss and much more. A tripped breaker can cause days or weeks of downtime!

This is why servers and networking hardware have two power supplies.

The best way to power your rack is as follows:

- One PSU is connected to a primary PDU (Power Distribution Unit)
- The second PSU is connected to a second PDU
- These PDUs source their power from different circuits (Preventing a tripped breaker from bringing everything down)
- At least one PDU is connected to a UPS (Uninterruptible Power Supply)

So, with all of this precursor knowledge, let's answer the question

## **OKAY** - What is a UPS?

A UPS or Uninterruptible Power Supply is a basically a smart battery. It is connected to the mains and outputs power to be used by the rack.

If that mains connection fails for whatever reason, the UPS instantly switches to the internal battery backup to supply the load required by the servers.

UPSes usually have a network connection both to allow remote monitoring and control, but also to be able to transmit to the network that mains power has been lost and to begin shutting down.

## **SHUTDOWN!** - Graceful Exits and Specing a UPS

The size of a UPS is measured in VA, volt amps (also known as watts!). So a UPS with 2,000VA would be able to output 2,000W for one hour before being empty.

When you spec a UPS, you take the maximum draw of all of your equipment that will be connected to it, and how long it would need to take to safely stop all of the services and shut them all down. This graceful shutdown prevents data loss AND hardware damage!

For example, let's say you have 4x servers which have a total draw of 1,000W each. Then you have networking hardware which draws an extra 1,000W combined.

That's a total of 5,000W.

In your testing, you have found that it takes about 10 minutes to safely shut everything down. But you want to add extra time as more services and hardware will appear over the lifetime of the UPS. I tend to round up to the nearest 15/20 minutes.

You will need a UPS which can output 5,000W for 15 minutes. So, that's 5,000W/4 (As watts are the measurement of power over the time of 1 hour, don't think about it too hard.)

Your minimum UPS size is 1,250VA

## SUPERPOWERS - UPS Configurations

UPSes can be configured to wait a set time after mains power is lost *before* sending the shutdown signal. This is because a lot of power outages are only a few minutes. Then, if the power isn't restored at the timeout, it'll send the shutdown signal.

UPSes can also be configured to send a 'Wake on LAN' signal when mains power is restored and stabilised, to automatically restart all the hardware. This is a bit of a double-edged sword, as grid stabilisation after a blackout is more of an art than a science, and successive blackouts can occur.

Finally, UPSes can also 'clean' the power. Alternating Current needs to be at a stable frequency, but the frequency after a blackout is often [dirty](https://www.emfanalysis.com/wp-content/uploads/2015/08/What-is-Dirty-Electricity.jpg) and not a clean waveform. This can cause damage to hardware.

## *What next?*

Learn about our own UPS, [Minecraft](other/minecraft.md)

Or learn about the Ubiquiti RPS, [Bunsen](networking/bunsen.md)

This is the end of the **WHAT IS?** section of Layer Zero. You can go on to check [Layer Zero Procedures](./procedures/index.md) for regularly maintenance and tasks you do at a hardware level. Or take the next step into [**LAYER ONE** - Operating Systems and Storage](../one/index.md)!
