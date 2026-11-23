# Company Network Infrastructure Lab

## Overview
A simulated company network infrastructure built using Cisco Packet Tracer. The project demonstrates network configuration, segmentation, routing, network services, security and troubleshooting.

## Network Architecture
- Cisco 2911 routers
- Cisco 2960 switches
- Administration VLAN (VLAN 10)
- Technical Support VLAN (VLAN 20)
- Servers VLAN (VLAN 30)
- Simulated ISP and Internet server

## Implemented Technologies
- VLAN configuration and trunking
- Inter-VLAN Routing (Router-on-a-Stick)
- DHCP and DHCP Relay
- DNS configuration
- Access Control Lists (ACL)
- SSH remote device management
- Switch Port Security
- WAN configuration and NAT Overload
- Network troubleshooting using Cisco IOS commands

## Network Addressing

| Network | Subnet | Gateway |
|---|---|---|
| ADMIN | 192.168.10.0/24 | 192.168.10.1 |
| SUPPORT | 192.168.20.0/24 | 192.168.20.1 |
| SERVERS | 192.168.30.0/24 | 192.168.30.1 |

## Troubleshooting
Used commands such as:
- `ping`
- `ipconfig`
- `show ip interface brief`
- `show ip route`
- `show vlan brief`
- `show interfaces trunk`
- `show ip nat translations`

## Files
- `Georgian_AirLink_Network_Lab.pkt` — Cisco Packet Tracer project file.
- `screenshots/` — Network topology and configuration screenshots.

# Cisco Packet Tracer Enterprise Lab (VLANs, Routing, ACLs, NAT & SSH)

![Network Topology](screenshots/network-topology.png)

## Addressing Overview

| Device / Segment | Interface / VLAN | IP Address / Subnet | Notes |
| :--- | :--- | :--- | :--- |
| **ADMIN** | `VLAN 10` | `192.168.10.0/24` (GW `192.168.10.1`) | Restricted from `SUPPORT` via ACL `110` |
| **SUPPORT** | `VLAN 20` | `192.168.20.0/24` (GW `192.168.20.1`) | Workstation segment |
| **SERVERS** | `VLAN 30` | `192.168.30.0/24` (GW `192.168.30.1`) | Internal server (`192.168.30.10`) and switch management |
| **R1 WAN / ISP-R1** | `Gi0/1` -> `ISP-R1` | `203.0.133.2` -> `203.0.133.1` | Default route and NAT overload (`PAT`) outside |
| **INTERNET-SERVER** | Simulated WAN | `198.51.100.10` | External reachability and NAT target |

