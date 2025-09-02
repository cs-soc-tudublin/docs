---
title: Ubiquiti RPS
created: 2025-08-03T17:53:59
modified: 2025-09-02T17:08:01
tags:
   - zero
   - hardware
   - networking
---

# **BUNSEN** - Redundant Power Supply

Ubiquiti is a lovely company that would never create a proprietary cable for the second PSU in it's networking gear… right?

[**WRONG**](https://cdn.cs.1worldsync.com/75/c6/75c6d384-a293-4373-bf9a-f3c815bfda08.jpg).

So, if you didn't have the RPS and the SmartPower(TM) cables, and no battery backup. One loss to the mains, [and the whole system goes down](https://youtube.com/clip/UgkxzUXwBSKLf1GXb9rvOGX-Kv_0kjg3YdPT?si=RcCI-9N_-LU52xuH).

Bunsen is connected to the power supply, which is attached to the UPS. If the mains go offline, the primary power cables (C13s) to the networking gear stops delivering power, but the RPS continues to deliver power through the SmartPower cables to each bit of networking gear.

Without the RPS, if the power went out, our whole network would go off. The servers might still be powered, but they won't receive the shutdown signal from the UPS, and won't be able to communicate with any network attached storage, or eachother.

| **Item**         | **Spec**                    |
| ---------------- | --------------------------- |
| Max Power Output | 950W                        |
| SmartPower Ports | 6x SmartPower               |
| Networking       | 1x 1Gb/s RJ45 (for control) |
