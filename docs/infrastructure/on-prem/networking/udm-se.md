---
title: Ubiquiti Dream Machine - Special Edition
created: 2024-09-06T18:50:38
modified: 2024-09-06T19:01:10
tags: [admin, on-prem, networking, 9]
---

# Ubiquiti Dream Machine - Special Edition

| Name          | Serial Number | IP Address (Internal) | IP Address (External) | Rack Unit # |
| ------------- | ------------- | --------------------- | --------------------- | ----------- |
| CSPP-ShakeDog | ###           | 192.168.1.1           | 147.252.#.#           | 3           |

Our primary router is the [UDM-SE](https://eu.store.ui.com/eu/en/products/udm-se). It is a 'Prosumer' grade router.

All internet traffic is routed through it. Our uplink to [HEANet](https://www.heanet.ie/) is on the 2.5Gb/s Port #9.

# Updates
ShakeDog will not automatically update.
Network stability is critical, and downtime should be scheduled for any network firmware updates.

# Backups
ShakeDog backups are not yet configured.
Here is the ideal backup policy:
- Once per week
- Whenever traffic is lowest on average
- 10 weeks of backups

## Features
- 8x GbE LAN Ports (2x PoE, 6x PoE+)
- 2x 10Gb SPF+ Ports
- 1x 2.5GbE WAN
- 3.5" Drive Bay for Network Video Recording
- Built in Wireguard, OpenVPN, Ubiquiti Teleport, and L2TP VPN Servers
- DHCP
- WAN Failover (Not utilised)
- Application-aware firewall rules
- Threat Detection
- Advanced filtering & routing
- VLAN & Subnet-based traffic segmentation
- Fully Stateful Firewall
- Internal DNS Server