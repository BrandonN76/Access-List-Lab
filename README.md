<h1>Cisco Packet Tracer Network Lab</h1>
<b>Lab Purpose:</b>
The goal of the lab is to simulate a small business network with multiple VLANs and implement an access control lists to manage traffic between the VLANs.
<h2>Lab Setup</h2>
<img src="https://i.imgur.com/ldyuXJo.png">

## Network Devices and port connections

### Router: Company Router
- **FastEthernet 0/0 (Switch 1)**
  - IP Address: 192.168.1.1
  - Subnet Mask: 255.255.255.0

- **FastEthernet 0/0.10 (VLAN 10 - Switch 1)**
  - IP Address: 192.168.10.1
  - Subnet Mask: 255.255.255.0
  - Default gateway: 192.168.10.1

- **FastEthernet 0/0.20 (VLAN 20 - Switch 1)**
  - IP Address: 192.168.20.1
  - Subnet Mask: 255.255.255.0
  - Default gateway: 192.168.20.1

- **FastEthernet 0/0.30 (VLAN 30 - Switch 1)**
  - IP Address: 192.168.30.1
  - Subnet Mask: 255.255.255.0
  - Default gateway: 192.168.30.1

- **FastEthernet 0/1 (Switch 2)**
  - IP Address: 192.168.1.2
  - Subnet Mask: 255.255.255.0

- **FastEthernet 0/1.40 (VLAN 40 - Switch 2)**
  - IP Address: 192.168.40.1
  - Subnet Mask: 255.255.255.0
  - Default gateway: 192.168.40.1

- **FastEthernet 0/1.50 (VLAN 50 - Switch 2)**
  - IP Address: 192.168.50.1
  - Subnet Mask: 255.255.255.0
  - Default gateway: 192.168.50.1

- **FastEthernet 0/1.60 (VLAN 60 - Switch 2)**
  - IP Address: 192.168.60.1
  - Subnet Mask: 255.255.255.0
  - Default gateway: 192.168.60.1

### Switch 1

- **FastEthernet 0/3-6 (VLAN 10)**
  - IP Address: 192.168.10.0/24

- **FastEthernet 0/7-10 (VLAN 20)**
  - IP Address: 192.168.20.0/24

- **FastEthernet 0/11-12 (VLAN 30)**
  - IP Address: 192.168.30.0/24

### Switch 2

- **FastEthernet 0/3-6 (VLAN 40)**
  - IP Address: 192.168.40.0/24

- **FastEthernet 0/7-10 (VLAN 50)**
  - IP Address: 192.168.50.0/24

- **FastEthernet 0/11-12 (VLAN 60)**
  - IP Address: 192.168.60.0/24

## VLANs

- **VLAN 10 (HR):** PC 1-4
- **VLAN 20 (Finance):** PC 5-8
- **VLAN 30 (IoT_1):** Printer 1-2
- **VLAN 40 (Staff):** PC 9-12
- **VLAN 50 (IT):** PC 13-16
- **VLAN 60 (IoT_2):** Printer 3-4

## Access Control List

**Access List for Network Filtering**
- Allow traffic from:
  - 10 192.168.10.0/24 to any
  - 20 192.168.20.0/24 to any
  - 30 192.168.30.0/24 to any
- Allow specific traffic from:
  - 40 192.168.40.0/24 to 192.168.50.0/24
  - 50 192.168.40.0/24 to 192.168.60.0/24
- Allow traffic from:
  - 60 192.168.50.0/24 to any
- Deny traffic from 192.168.40.0/24 to:
  - 70 192.168.10.0/24
  - 80 192.168.20.0/24
  - 90 192.168.30.0/24
- Deny traffic from:
  - 100 192.169.10.0/24 to 192.168.40.

(Attempting to ping Staff from HR on the first command and then pinging IT from HR on the second command)
<img src="https://i.imgur.com/sQVU43Q.png">

**Overview**
In this lab, I simulated a small business network featuring a single router, two switches, each connected to eight computers, and two printers. The network was segmented into six VLANs to organize departments efficiently. To enhance security and control communication between departments, I implemented an Access Control List (ACL). Notably, I configured the ACL to restrict communication for VLAN 40 (Staff) — the only department unable to freely communicate with others.A noteworthy aspect of the lab involved fine-tuning the ACL to specifically allow Staff computers to communicate solely with VLAN 50 (IT) and VLAN 60 (Printers), showcasing the efficacy of the access control measures. This deliberate restriction exemplifies how ACLs can be tailored to enforce communication policies within a network, contributing to a more secure and organized business environment.
