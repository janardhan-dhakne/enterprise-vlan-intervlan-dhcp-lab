# Enterprise VLAN, Inter-VLAN Routing & DHCP Lab

## 📌 Project Overview

Designed and implemented an enterprise network topology using Cisco IOS and EVE-NG.

The lab demonstrates VLAN-based network segmentation, 802.1Q trunking, Router-on-a-Stick, Inter-VLAN routing and centralized DHCP services.

## 🖥️ Lab Environment

- EVE-NG
- Cisco IOS
- Cisco Routers
- Cisco Switches
- VPCS

## 🏗️ Network Topology

<img width="1920" height="1080" alt="Enterprise VLAN-Intervlan Lab Topology" src="https://github.com/user-attachments/assets/bb587718-53d9-4a9e-8f71-feb80a063843" />


## 🌐 VLAN & IP Addressing

| Department | VLAN | Network | Default Gateway |
|------------|------|---------|-----------------|
| HR | 10 | 192.168.10.0/24 | 192.168.10.1 |
| IT | 20 | 192.168.20.0/24 | 192.168.20.1 |
| Finance | 30 | 192.168.30.0/24 | 192.168.30.1 |
| Management | 40 | 192.168.40.0/24 | 192.168.40.1 |

## 🔧 Technologies & Concepts

- VLAN
- VLAN Segmentation
- 802.1Q Trunking
- Router-on-a-Stick
- Inter-VLAN Routing
- DHCP
- Default Gateway
- Cisco IOS
- Layer 2 Switching
- Layer 3 Routing
- Network Troubleshooting

## ⚙️ Network Design

### R1

R1 performs:

- Router-on-a-Stick
- Inter-VLAN Routing
- DHCP Server

Subinterfaces:

| Interface | VLAN | IP Address |
|-----------|------|------------|
| e0/0.10 | 10 | 192.168.10.1 |
| e0/0.20 | 20 | 192.168.20.1 |
| e0/0.30 | 30 | 192.168.30.1 |
| e0/0.40 | 40 | 192.168.40.1 |

### SW1

SW1 acts as the central/distribution switch.

Connections:

- R1 → SW1: Trunk
- SW1 → SW2: Trunk
- SW1 → SW3: Trunk
- SW1 → SW4: Trunk
- SW1 → SW5: Trunk

### Access Switches

- SW2 → VLAN 10 → HR
- SW3 → VLAN 20 → IT
- SW4 → VLAN 30 → Finance
- SW5 → VLAN 40 → Management

## 📡 DHCP

R1 provides DHCP services for all four VLANs.

DHCP pools:

- VLAN 10 → 192.168.10.0/24
- VLAN 20 → 192.168.20.0/24
- VLAN 30 → 192.168.30.0/24
- VLAN 40 → 192.168.40.0/24

## 🧪 Verification

The following commands were used to verify the configuration:

```text
show vlan brief
show interfaces trunk
show ip interface brief
show ip dhcp binding
show ip dhcp pool
show running-config
