# Meadowlark Dental Group – Network Design & Implementation

## 📌 Project Overview

This project presents the **design and implementation of a multi-site healthcare network** for **Meadowlark Dental Group** using **Cisco Packet Tracer**.

The network connects three locations:

- 🏢 **Headquarters (HQ)**
- 🏥 **Practice-North**
- 🏥 **Practice-South**

The HQ contains four departments: **Patient Records, Orthodontic Imaging, IT & Billing, and Front Desk**. VLANs are used to logically separate these departments, while WAN connections provide communication between the three locations. Jaikishan_Suthar_Network_Docume…

---

## 🎯 Objectives

- Design a scalable multi-site network
- Connect HQ, North and South locations
- Separate HQ departments using VLANs
- Configure **802.1Q trunking**
- Implement **Router-on-a-Stick**
- Configure serial WAN connections
- Implement static routing
- Apply VLSM-based IPv4 addressing
- Configure default gateways
- Test end-to-end connectivity
- Troubleshoot network connectivity problems Jaikishan_Suthar_Network_Docume…

---

## 🏗️ Network Architecture

### Locations

```text
                    NORTH
                  NORTH-R1
                      |
                  Serial WAN
                      |
                      |
                    HQ-R1
                   /     \
                  /       \
             HQ-SW1      Serial WAN
               |             \
          HQ Departments   SOUTH-R1
                            |
                         SOUTH-SW1
```

HQ acts as the **central location**, with serial WAN connections to North and South. The HQ switch carries the departmental VLANs through a trunk connection to HQ-R1. Jaikishan_Suthar_Network_Docume…

---

## 🖥️ Devices Used

| Device | Name | Purpose |
|---|---|---|
| Router | HQ-R1 | Inter-VLAN routing and WAN connectivity |
| Router | NORTH-R1 | North LAN and WAN connectivity |
| Router | SOUTH-R1 | South LAN and WAN connectivity |
| Switch | HQ-SW1 | HQ VLANs and end devices |
| Switch | NORTH-SW1 | North PCs |
| Switch | SOUTH-SW1 | South PCs |

The project uses representative PCs at each location for testing. Jaikishan_Suthar_Network_Docume…

---

## 🌐 VLAN Configuration

| VLAN ID | VLAN Name | Department/Site |
|---:|---|---|
| 10 | PATIENT_RECORDS | HQ Patient Records |
| 20 | ORTHODONTIC_IMAGING | HQ Orthodontic Imaging |
| 30 | IT_BILLING | HQ IT & Billing |
| 40 | FRONT_DESK | HQ Front Desk |
| 50 | NORTH_LAN | North |
| 60 | SOUTH_LAN | South |

HQ-SW1 uses **Gi0/1 as an 802.1Q trunk** toward HQ-R1. Jaikishan_Suthar_Network_Docume…

---

## 📡 IP Addressing

The project uses **192.168.60.0/22** with VLSM-style subnet allocation.

| Network | Subnet | Gateway | Mask |
|---|---|---|---|
| Patient Records | 192.168.60.0/26 | 192.168.60.1 | 255.255.255.192 |
| Orthodontic Imaging | 192.168.60.64/28 | 192.168.60.65 | 255.255.255.240 |
| IT & Billing | 192.168.60.80/28 | 192.168.60.81 | 255.255.255.240 |
| Front Desk | 192.168.60.96/29 | 192.168.60.97 | 255.255.255.248 |
| North LAN | 192.168.60.104/29 | 192.168.60.105 | 255.255.255.248 |
| South LAN | 192.168.60.112/29 | 192.168.60.113 | 255.255.255.248 |
| HQ-North WAN | 192.168.60.120/30 | — | 255.255.255.252 |
| HQ-South WAN | 192.168.60.124/30 | — | 255.255.255.252 |

Jaikishan_Suthar_Network_Docume…

---

## 🔀 Routing

The project uses **static routing** between HQ, North and South.

HQ-R1 uses:

- `G0/0.10`
- `G0/0.20`
- `G0/0.30`
- `G0/0.40`

for the four HQ VLAN gateways.

The routers use serial interfaces for WAN connectivity. Jaikishan_Suthar_Network_Docume…

---

## 🔗 WAN Connections

```text
HQ-R1 S0/0/0  ↔  NORTH-R1 S0/0/0
HQ-R1 S0/0/1  ↔  SOUTH-R1 S0/0/0
```

### WAN Networks

- HQ-North: `192.168.60.120/30`
- HQ-South: `192.168.60.124/30`

Serial interfaces were configured as required, including DCE clocking. Jaikishan_Suthar_Network_Docume…

---

## 🔄 How the Network Works

A typical communication flow is:

```text
End Device
    ↓
Switch
    ↓
VLAN
    ↓
802.1Q Trunk
    ↓
Router-on-a-Stick
    ↓
Static Routing
    ↓
Serial WAN
    ↓
Remote Router
    ↓
Remote Switch
    ↓
Destination Device
```

This allows devices in different departments and different locations to communicate.

---

## 🧪 Network Testing

Connectivity was tested using **ping** between:

- PCs and their gateways
- North and South
- South and HQ
- HQ and North
- Different HQ departments

The final successful tests achieved **0% packet loss**. Jaikishan_Suthar_Network_Docume…

---

## 🛠️ Troubleshooting

During implementation, the following issues were identified and resolved:

- Static routing issue between South and North
- Overlapping serial IP address
- Initial first-packet ping failures during ARP/path learning
- VLAN assignment verification
- Trunk configuration verification

Commands used for verification included:

```bash
show vlan brief
show interfaces trunk
ping
copy running-config startup-config
```

Jaikishan_Suthar_Network_Docume…

---

## 📚 Main Networking Concepts Used

- Network Topology
- LAN
- WAN
- IPv4 Addressing
- VLSM
- Subnetting
- VLAN
- 802.1Q Trunking
- Router-on-a-Stick
- Inter-VLAN Routing
- Static Routing
- Serial WAN
- DCE/DTE
- Default Gateway
- ARP
- ICMP
- Ping
- Network Troubleshooting
- Cisco Packet Tracer

---

## ✅ Final Result

The Meadowlark Dental Group network was successfully designed and implemented in **Cisco Packet Tracer**. HQ departments are separated using VLANs, inter-VLAN communication is provided through Router-on-a-Stick, and HQ is connected to the North and South practices using serial WAN links. Static routing enables communication across the complete network. Jaikishan_Suthar_Network_Docume…

---

## 👨‍💻 Project Information

**Student:** Jaikishan Suthar  
**Roll Number:** 150096752152  
**Course:** Computer Networking / Networking Case Study  
**Project:** Meadowlark Dental Group – Network Design and Implementation  
**Tool:** Cisco Packet Tracer
