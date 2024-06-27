# Technology Implemented

This document provides a detailed overview of the technologies implemented in the hospital network design, encompassing both the headquarters (HQ) and the branch office.

## 1. Three-Tier Network Architecture
### Description
The network design follows a three-tier architecture consisting of Core, Distribution, and Access layers. This architecture enhances scalability, performance, and manageability.

### Implementation
- **Core Layer**: High-performance routers for fast data transfer and routing between HQ and the branch.
- **Distribution Layer**: Layer 3 switches configured with HSRP for redundancy.
- **Access Layer**: Layer 2 switches providing connectivity to end devices.

## 2. Network Redundancy
### Description
Redundancy is critical to ensure high availability and minimize downtime in case of device or link failure.

### Implementation
- **HSRP (Hot Standby Router Protocol)**: Configured at the Distribution layer to provide gateway redundancy and load balancing.

## 3. IP Subnetting
### Description
Efficient IP address allocation to support a scalable network.

### Implementation
- **HQ**: Subnetting plan designed to accommodate 60 users per department.
- **Branch**: Subnetting plan designed to accommodate 30 users per department.

## 4. VLAN (Virtual Local Area Network)
### Description
VLANs are used to segment network traffic, improving security and performance by isolating broadcast domains.

### Implementation
- **VLAN Configuration**: VLANs configured on Access layer switches for different departments and functions.
- **Inter-VLAN Trunking**: Trunk links between switches to carry traffic for multiple VLANs.

## 5. Inter-VLAN Trunking (SVI)
### Description
SVI (Switched Virtual Interface) is used for routing traffic between VLANs.

### Implementation
- **Distribution Switches**: SVIs configured on Layer 3 switches to enable inter-VLAN routing.

## 6. HSRP (Hot Standby Router Protocol)
### Description
HSRP provides redundancy for the default gateway, ensuring continuous availability in case of a router failure.

### Implementation
- **Distribution Layer**: HSRP configured on distribution switches for gateway redundancy.

## 7. OSPF Single Area
### Description
OSPF (Open Shortest Path First) is used for dynamic routing within a single area to ensure efficient and automatic route updates.

### Implementation
- **Routing Between HQ and Branch**: OSPF configured to dynamically exchange routing information.

## 8. Static Default Routing
### Description
Static default routes provide a simple and reliable path to external networks.

### Implementation
- **Default Routes**: Configured on routers to direct traffic towards the internet and external networks.

## 9. Site-to-Site IPsec VPN
### Description
IPsec VPN ensures secure and encrypted communication between the HQ and branch office.

### Implementation
- **VPN Configuration**: Site-to-site IPsec VPN configured on routers to encrypt traffic between HQ and branch.

## 10. DHCP Server
### Description
Dynamic Host Configuration Protocol (DHCP) server automatically assigns IP addresses to devices in the network.

### Implementation
- **Centralized DHCP Server**: Configured to manage IP address allocation for HQ and branch.

## 11. Email Server
### Description
An email server is essential for handling internal and external email communication.

### Implementation
- **Email Server Configuration**: Configured to support the hospital's communication needs.

## 12. NAT Overload (PAT)
### Description
Network Address Translation (NAT) overload, or Port Address Translation (PAT), allows multiple internal devices to share a single public IP address.

### Implementation
- **NAT Overload**: Configured on the router to enable internet access for internal devices.

## 13. Access Control Lists (ACL)
### Description
ACLs are used to control network traffic and enhance security by filtering packets based on defined rules.

### Implementation
- **Standard and Extended ACLs**: Configured on routers and switches to restrict access and manage traffic flow.

## 14. Switch Port Security
### Description
Port security prevents unauthorized devices from connecting to the network.

### Implementation
- **Server Room Switch**: Port security configured on switches in critical areas to prevent unauthorized access.

## 15. Wireless Access Points (WPA2)
### Description
Wireless Access Points (APs) provide secure wireless connectivity within the network.

### Implementation
- **WPA2 Security**: Configured on wireless APs to ensure secure wireless communication.

## 16. SSH for Remote Access
### Description
Secure Shell (SSH) is used for secure remote management of network devices.

### Implementation
- **SSH Configuration**: Enabled on routers and switches to allow secure remote access.

This document summarizes the key technologies and their implementation in the hospital network design. Each technology has been carefully selected and configured to meet the requirements of a modern, secure, and reliable network infrastructure.
