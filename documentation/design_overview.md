# Hospital Network Design Overview

## Introduction
This document provides an overview of the network design for a hospital system, which includes a headquarters (HQ) and a branch office. The design aims to ensure high availability, security, and efficient traffic management through a variety of technologies and configurations.

## Network Architecture
The network architecture is based on a three-tier model comprising the Core, Distribution, and Access layers. This structure provides a scalable and manageable design, facilitating efficient routing and switching while ensuring redundancy and high availability.

### Core Layer
- **Function**: The backbone of the network, responsible for fast and reliable data transfer between the HQ and branch.
- **Devices**: High-performance routers capable of handling large amounts of data and routing between different subnets and VLANs.

### Distribution Layer
- **Function**: Acts as an intermediary between the Core and Access layers, managing routing, VLANs, and redundancy.
- **Devices**: Layer 3 switches configured with HSRP (Hot Standby Router Protocol) to ensure redundancy and load balancing.

### Access Layer
- **Function**: Provides network connectivity to end devices such as computers, printers, and wireless access points.
- **Devices**: Layer 2 switches supporting VLAN segmentation and port security features.

## Key Technologies Implemented
### VLANs and Inter-VLAN Routing
- **Purpose**: Segregate network traffic into different broadcast domains to improve security and performance.
- **Implementation**: VLANs are configured on Access layer switches, with inter-VLAN routing handled by Distribution layer switches using SVI (Switched Virtual Interfaces).

### IP Subnetting
- **Purpose**: Efficient IP address allocation to ensure scalability and manageability.
- **HQ**: Each department has 60 users, with appropriate subnetting to accommodate them.
- **Branch**: Each department has 30 users, with subnetting tailored to their needs.

### Routing Protocols
- **OSPF Single Area**: Used for routing between the HQ and branch to ensure dynamic route updates and efficient path selection.
- **Static Default Routing**: Provides a simple and reliable route to the internet and external networks.

### Redundancy and High Availability
- **HSRP**: Implemented at the Distribution layer to provide gateway redundancy.
- **Dual ISPs**: (Note: Due to packet tracer limitations, route-map for dual ISP implementation is not included, but the concept is explained).

### Security Measures
- **IPsec VPN**: Ensures encrypted communication between the HQ and branch.
- **Access Control Lists (ACLs)**: Standard and extended ACLs are used to control traffic flow and enhance security.
- **Port Security**: Configured on switches in server rooms to prevent unauthorized access.
- **SSH**: Secure remote access to network devices.

### Network Services
- **DHCP**: Centralized DHCP server for dynamic IP address assignment.
- **Email Server**: Configured to handle internal and external email communication.
- **NAT Overload (PAT)**: Allows multiple internal devices to share a single public IP address for internet access.

### Wireless Network
- **Wireless Access Points (WPA2)**: Provide secure wireless connectivity to devices within the
