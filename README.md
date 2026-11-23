# 🌐 Company Network Infrastructure Lab

## 📌 Overview

A simulated enterprise network infrastructure designed and implemented using **Cisco Packet Tracer**. This project demonstrates practical networking skills, including network segmentation, routing, network services, security configuration, remote device management, and troubleshooting.

## 🏗️ Network Architecture

The network consists of the following components:

- Cisco 2911 routers
- Cisco 2960 switches
- Administration Department (VLAN 10)
- Technical Support Department (VLAN 20)
- Servers Network (VLAN 30)
- Simulated ISP connection and external server

## 🛠️ Implemented Technologies

- VLAN creation and configuration
- IEEE 802.1Q trunking
- Inter-VLAN Routing (Router-on-a-Stick)
- DHCP configuration and DHCP Relay
- DNS configuration and hostname resolution
- Extended Access Control Lists (ACLs)
- SSH v2 remote device management
- Switch Port Security
- WAN connectivity and NAT Overload (PAT)
- Network monitoring and troubleshooting using Cisco IOS commands

---

## 🗺️ Network Topology

![Network Topology](screenshots/01-network-topology.png)

## 📋 IP Addressing Scheme

| Device / Segment | Interface / VLAN | IP Address / Subnet | Notes |
| :--- | :--- | :--- | :--- |
| **ADMIN** | `VLAN 10` | `192.168.10.0/24` (GW `192.168.10.1`) | Restricted from `SUPPORT` via ACL `110` |
| **SUPPORT** | `VLAN 20` | `192.168.20.0/24` (GW `192.168.20.1`) | Workstation segment |
| **SERVERS** | `VLAN 30` | `192.168.30.0/24` (GW `192.168.30.1`) | Internal server (`192.168.30.10`) and switch management |
| **R1 WAN / ISP-R1** | `Gi0/1` → `ISP-R1` | `203.0.133.2` → `203.0.133.1` | WAN connection and NAT outside interface |
| **INTERNET-SERVER** | Simulated WAN | `198.51.100.10` | External connectivity testing |

---

## 1. 🔀 VLAN Configuration

VLANs are used to logically segment the network into separate broadcast domains, isolating administrative workstations, technical support workstations, and servers. Communication between VLANs is handled by inter-VLAN routing configured on router R1 using the Router-on-a-Stick architecture.

**Administration VLAN configuration:**

![Administration VLAN](screenshots/02-admin-vlan.png)

**Technical Support VLAN configuration:**

![Technical Support VLAN](screenshots/02-support-vlan.png)

**Servers VLAN configuration:**

![Servers VLAN](screenshots/02-server-vlan.png)

---

## 2. 📡 DHCP Configuration

DHCP automatically assigns IPv4 addresses, subnet masks, default gateways, and DNS server settings to client devices in **ADMIN** (`VLAN 10`) and **SUPPORT** (`VLAN 20`). Separate DHCP pools are configured for each VLAN to ensure clients receive the correct network configuration without requiring manual setup.

**DHCP server configuration:**

![DHCP Configuration](screenshots/03-dhcp-configuration.png)

---

## 3. 🌍 DNS Configuration

The internal DNS service resolves hostnames to IP addresses, allowing devices to access local network services using domain names instead of numeric IP addresses. An `A` record is configured to map `company.local` to `192.168.30.10`.

**DNS server configuration:**

![DNS Configuration](screenshots/04-DNS-config-server.png)

**Testing hostname resolution using the configured DNS record:**

![DNS Testing](screenshots/04-testing-DNS.png)

---

## 4. 🔒 Network Security (ACL)

Extended ACL `110` is configured on router R1 to control traffic between VLANs. A deny rule blocks traffic originating from the ADMIN network (`192.168.10.0/24`) and destined for the SUPPORT network (`192.168.20.0/24`). Connectivity tests verify that the configured access restrictions are enforced.

**ACL configuration:**

![Network Security ACL](screenshots/05-ACCESS-LIST.png)

**Testing inter-VLAN access restrictions:**

![ACL Testing](screenshots/05-testing-ACL.png)

---

## 5. 🔑 SSH Remote Management

SSH version 2 is configured to provide encrypted remote access to network devices. Local user authentication is enabled, and Telnet access is disabled on the VTY lines. Remote management is tested by establishing SSH connections from a workstation to the router and switches.

**Testing SSH access to the router:**

![SSH Router Connection](screenshots/06-ssh-router-connecting.png)

**Testing SSH access to the switch:**

![SSH Switch Connection](screenshots/06-ssh-switch-connecting.png)

---

## 6. 🔄 NAT Configuration

NAT Overload (PAT) is configured on router R1 to translate private internal IP addresses from the ADMIN, SUPPORT, and SERVERS networks into the router's outside WAN address (`203.0.133.2`). This allows internal devices to communicate with external networks through the simulated ISP connection. NAT translations are verified using Cisco IOS show commands.

**NAT configuration on R1:**

![NAT Configuration](screenshots/07-NAT-config-router.png)

**Verifying NAT translations and connectivity to the simulated Internet server:**

![NAT Verification](screenshots/07-NAT-config.png)

---

## 7. 🧪 Connectivity and Troubleshooting

Connectivity tests are performed to verify communication between network devices and validate the implemented routing and security policies.

The following tests are conducted:

- ✅ Successful connectivity to the default gateway.
- ✅ Successful communication with the internal server in VLAN 30.
- ✅ Successful connectivity to the simulated Internet server (`198.51.100.10`).
- 🚫 Blocked ping from ADMIN to SUPPORT, verifying ACL enforcement.

These tests demonstrate the functionality of inter-VLAN routing, internal network services, NAT/PAT, and access control policies.

**Connectivity and troubleshooting test results:**

![Connectivity Testing](screenshots/08-Connectivity-and-troubleshooting.png)

![Additional Connectivity Testing](screenshots/08-Connectivity-and-troubleshooting2.png)

---

## 📁 Project Files

- `Georgian_AirLink_Network_Lab.pkt` — Cisco Packet Tracer project file.
- `screenshots/` — Network topology and configuration screenshots.
