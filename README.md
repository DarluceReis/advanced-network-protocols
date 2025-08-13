# 🌐 Network Configuration Project

This repository contains the configuration files and a detailed explanation of the **network topology** I designed and implemented in **Cisco Packet Tracer**.  
The project demonstrates my skills in **network administration**, including:

- **VLSM subnetting**
- **Dynamic routing** (RIP)
- **Redundancy protocols** (HSRP)
- **Advanced security features**

---

## Project Overview

The network is composed of **three main sites**:

1. **Production Site — Vila Real**  
2. **Central Office — Porto**  
3. **Datacenter — Lisbon**  

The goal was to establish robust, secure, and redundant communication between all locations.

---

## 1. Production Site — Vila Real

 **Subnets configured with VLSM** starting from 183.16.0.0/16 to optimize address space usage:

| Subnet         | Supported Hosts | Interface | Mask |
|----------------|-----------------|-----------|------|
| **VILAREAL 1** | 1021            | g0/0      | /22  |
| **VILAREAL 2** | 800             | g0/1      | /21  |

**DHCP Service**  
A dedicated DHCP server (**Server-PT Server1**) was configured to dynamically assign IP addresses to all hosts in Vila Real.

---

## 2. Datacenter — Lisbon

A key location, hosting the **central DNS server** for the entire network.

- **DNS Server:** Server-PT DNS SERVER
- **Static IP:** configured manually
- **Domain Name:** cesae.local
- **Function:** Resolves hostnames for all network devices.

---

## 3. Central Office — Porto

### VLANs & VTP
- **VLAN 10 — FINANCEIRO:** 192.168.10.0/25  
- **VLAN 20 — STAFF:** 192.168.20.0/26  
- **VTP (Virtual Trunking Protocol)** configured for automatic VLAN management.

### HSRP (Hot Standby Router Protocol)
- **HSRP-ACTIVE** router acts as the primary gateway.
- **HSRP-STANDBY** router remains ready to take over in case of failure.

### Inter-VLAN Routing
- Implemented using the **Router-on-a-Stick** method for VLAN communication.

---

## 4. Routing

- **Protocol Used:** RIP (Routing Information Protocol) for dynamic routing between the three sites.

---

## 5. Security & Hardening

- **Port-Security:**  
  - **VLAN 10 (Financeiro):** Shutdown mode, 1 dynamic MAC per port.  
  - **VLAN 20 (Staff):** Restrict mode, 1 static MAC per port.  

- **DHCP Snooping:** Prevents rogue DHCP server attacks.  
- **ARP Inspection:** Protects against ARP spoofing attacks.  
- **STP Hardening:** PortFast & BPDU Guard on all access ports for stability.

---

## Network Topology Diagram

![Network Topology](images/network-topology.PNG)


---

**Skills Demonstrated:**  
VLSM | RIP | HSRP | VLAN & VTP | DHCP | DNS | Port-Security | DHCP Snooping | ARP Inspection | STP Hardening
