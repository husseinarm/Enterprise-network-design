# Enterprise Network Design & Implementation

A complete enterprise network topology designed and implemented in **Cisco Packet Tracer** — covering VLANs, OSPF, Rapid-PVST, DHCP, DNS, routing, switching, and redundancy.

## 📌 Project Overview

This project simulates a real-world enterprise network with multiple departments, redundant links, and centralized services. It demonstrates hands-on proficiency in Cisco IOS configuration, network design, and troubleshooting.

**Key Technologies:**
- VLANs & 802.1Q Trunking
- Inter-VLAN Routing
- Multi-Area OSPF with Equal-Cost Multi-Path (ECMP)
- Rapid-PVST with Distributed Root Bridges
- DHCP Relay Agent & DNS
- VLSM Subnetting

---

## 🏗️ Network Topology

### Devices
| Device Type | Quantity | Role |
|-------------|----------|------|
| Routers | 4 | WAN routing, OSPF |
| Layer-3 Switches | 3 | Inter-VLAN routing, STP |
| Servers | 2 | DHCP, DNS |
| End Devices | Multiple | PCs, Laptops across VLANs |

### VLANs
| VLAN | Network | Subnet | Gateway |
|------|---------|--------|---------|
| VLAN 10 | 192.168.10.0 | /25 | 192.168.10.1 |
| VLAN 20 | 192.168.20.0 | /26 | 192.168.20.1 |
| VLAN 30 | 192.168.30.0 | /27 | 192.168.30.1 |

### WAN Links
| Link | Network |
|------|---------|
| Router1 ↔ R2 | 172.16.0.4/30 |
| Router1 ↔ R3 | 172.16.0.0/30 |
| R2 ↔ R4 | 172.16.0.60/30 |
| R3 ↔ R4 | 172.16.0.64/30 |

---

## ⚙️ Technologies Implemented

### 1. VLANs & Trunking
- Created VLAN 10, 20, 30 across all switches
- Configured 802.1Q trunk links between switches

### 2. Inter-VLAN Routing
- Configured on Multilayer Switches (MLS1, MLS4, MLS5)
- Verified inter-VLAN communication via ping tests

### 3. OSPF Dynamic Routing
- Configured multi-area OSPF across all routers
- Verified neighbor adjacency (FULL/DR state)
- Achieved Equal-Cost Multi-Path (ECMP) load balancing

### 4. Spanning Tree Protocol (Rapid-PVST)
- Configured MLS4 as Root Bridge for VLAN 20, 30, and Default
- Configured MLS5 as Root Bridge for VLAN 10
- Achieved Root Bridge Load Balancing

### 5. DHCP & DNS
- Deployed centralized DHCP server (1.1.1.1)
- Configured DHCP Relay Agent (ip helper-address)
- Set up DNS records for internal name resolution

---

## ✅ Testing & Validation

### Connectivity Tests (0% Packet Loss)
| Source | Destination | Type | Result |
|--------|-------------|------|--------|
| PC (VLAN 10) | 192.168.10.2 | Same VLAN | ✅ 0% loss |
| PC (VLAN 10) | 192.168.20.2 | Inter-VLAN | ✅ 0% loss |
| PC (VLAN 10) | 192.168.30.2 | Inter-VLAN | ✅ 0% loss |
| PC (VLAN 10) | 1.1.1.1 | Central Server | ✅ 0% loss |
| PC (VLAN 10) | 172.16.0.2 | MLS Gateway | ✅ 0% loss |
| PC (VLAN 10) | 172.16.0.5 | WAN Link | ✅ 0% loss |

### OSPF Verification
