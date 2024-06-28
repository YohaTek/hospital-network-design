# DHCP Configuration

This document outlines the configuration of the DHCP (Dynamic Host Configuration Protocol) server for the hospital network design. DHCP is used to automatically assign IP addresses and other network configuration parameters to devices on the network, facilitating easier management and connectivity.

## Overview

The DHCP server will be configured to provide dynamic IP address assignment for both the headquarters (HQ) and branch office networks. Each VLAN will have its own DHCP scope to ensure proper IP address allocation within each subnet.

## DHCP Configuration for Headquarters (HQ)

### DHCP Configuration on Router

#### Step 1: Define DHCP Pools for Each VLAN

1. **Administration VLAN (VLAN 10)**
    ```bash
    ip dhcp pool VLAN10_ADMIN
     network 192.168.0.0 255.255.255.192
     default-router 192.168.0.1
     dns-server 8.8.8.8 8.8.4.4
     domain-name hq.example.com
    ```

2. **Emergency VLAN (VLAN 20)**
    ```bash
    ip dhcp pool VLAN20_EMERGENCY
     network 192.168.0.64 255.255.255.192
     default-router 192.168.0.65
     dns-server 8.8.8.8 8.8.4.4
     domain-name hq.example.com
    ```

3. **Outpatient VLAN (VLAN 30)**
    ```bash
    ip dhcp pool VLAN30_OUTPATIENT
     network 192.168.0.128 255.255.255.192
     default-router 192.168.0.129
     dns-server 8.8.8.8 8.8.4.4
     domain-name hq.example.com
    ```

4. **Inpatient VLAN (VLAN 40)**
    ```bash
    ip dhcp pool VLAN40_INPATIENT
     network 192.168.0.192 255.255.255.192
     default-router 192.168.0.193
     dns-server 8.8.8.8 8.8.4.4
     domain-name hq.example.com
    ```

5. **Radiology VLAN (VLAN 50)**
    ```bash
    ip dhcp pool VLAN50_RADIOLOGY
     network 192.168.1.0 255.255.255.192
     default-router 192.168.1.1
     dns-server 8.8.8.8 8.8.4.4
     domain-name hq.example.com
    ```

6. **Laboratory VLAN (VLAN 60)**
    ```bash
    ip dhcp pool VLAN60_LAB
     network 192.168.1.64 255.255.255.192
     default-router 192.168.1.65
     dns-server 8.8.8.8 8.8.4.4
     domain-name hq.example.com
    ```

7. **Pharmacy VLAN (VLAN 70)**
    ```bash
    ip dhcp pool VLAN70_PHARMACY
     network 192.168.1.128 255.255.255.192
     default-router 192.168.1.129
     dns-server 8.8.8.8 8.8.4.4
     domain-name hq.example.com
    ```

8. **IT Department VLAN (VLAN 80)**
    ```bash
    ip dhcp pool VLAN80_IT
     network 192.168.1.192 255.255.255.192
     default-router 192.168.1.193
     dns-server 8.8.8.8 8.8.4.4
     domain-name hq.example.com
    ```

9. **Guest Network VLAN (VLAN 90)**
    ```bash
    ip dhcp pool VLAN90_GUEST
     network 192.168.2.0 255.255.255.192
     default-router 192.168.2.1
     dns-server 8.8.8.8 8.8.4.4
     domain-name guest.example.com
    ```

10. **Server Room VLAN (VLAN 100)**
    ```bash
    ip dhcp pool VLAN100_SERVER
     network 192.168.2.64 255.255.255.192
     default-router 192.168.2.65
     dns-server 8.8.8.8 8.8.4.4
     domain-name hq.example.com
    ```

#### Step 2: Exclude Static IP Addresses

Exclude IP addresses that will be assigned statically to network devices such as servers, routers, and switches.

ip dhcp excluded-address 192.168.0.1 192.168.0.10
ip dhcp excluded-address 192.168.0.65 192.168.0.75
ip dhcp excluded-address 192.168.0.129 192.168.0.139
ip dhcp excluded-address 192.168.0.193 192.168.0.203
ip dhcp excluded-address 192.168.1.1 192.168.1.10
ip dhcp excluded-address 192.168.1.65 192.168.1.75
ip dhcp excluded-address 192.168.1.129 192.168.1.139
ip dhcp excluded-address 192.168.1.193 192.168.1.203
ip dhcp excluded-address 192.168.2.1 192.168.2.10
ip dhcp excluded-address 192.168.2.65 192.168.2.75


DHCP Configuration for Branch Office
DHCP Configuration on Router
Step 1: Define DHCP Pools for Each VLAN
Administration VLAN (VLAN 110)

ip dhcp pool VLAN110_ADMIN_B
 network 192.168.4.0 255.255.255.224
 default-router 192.168.4.1
 dns-server 8.8.8.8 8.8.4.4
 domain-name branch.example.com
Emergency VLAN (VLAN 120)

ip dhcp pool VLAN120_EMERGENCY_B
 network 192.168.4.32 255.255.255.224
 default-router 192.168.4.33
 dns-server 8.8.8.8 8.8.4.4
 domain-name branch.example.com
Outpatient VLAN (VLAN 130)

ip dhcp pool VLAN130_OUTPATIENT_B
 network 192.168.4.64 255.255.255.224
 default-router 192.168.4.65
 dns-server 8.8.8.8 8.8.4.4
 domain-name branch.example.com
Inpatient VLAN (VLAN 140)

ip dhcp pool VLAN140_INPATIENT_B
 network 192.168.4.96 255.255.255.224
 default-router 192.168.4.97
 dns-server 8.8.8.8 8.8.4.4
 domain-name branch.example.com
Radiology VLAN (VLAN 150)

ip dhcp pool VLAN150_RADIOLOGY_B
 network 192.168.4.128 255.255.255.224
 default-router 192.168.4.129
 dns-server 8.8.8.8 8.8.4.4
 domain-name branch.example.com
Laboratory VLAN (VLAN 160)

ip dhcp pool VLAN160_LAB_B
 network 192.168.4.160 255.255.255.224
 default-router 192.168.4.161
 dns-server 8.8.8.8 8.8.4.4
 domain-name branch.example.com
Pharmacy VLAN (VLAN 170)

ip dhcp pool VLAN170_PHARMACY_B
 network 192.168.4.192 255.255.255.224
 default-router 192.168.4.193
 dns-server 8.8.8.8 8.8.4.4
 domain-name branch.example.com
IT Department VLAN (VLAN 180)

ip dhcp pool VLAN180_IT_B
 network 192.168.4.224 255.255.255.224
 default-router 192.168.4.225
 dns-server 8.8.8.8 8.8.4.4
 domain-name branch.example.com
Step 2: Exclude Static IP Addresses
Exclude IP addresses that will be assigned statically to network devices such as servers, routers, and switches.


ip dhcp excluded-address 192.168.4.1 192.168.4.10
ip dhcp excluded-address 192.168.4.33 192.168.4.43
ip dhcp excluded-address 192.168.4.65 192.168.4.75
ip dhcp excluded-address 192.168.4.97 192.168.4.107
ip dhcp excluded-address 192.168.4.129 192.168.4.139
ip dhcp excluded-address 192.168.4.161 192.168.4.171
ip dhcp excluded-address 192.168.4.193 192.168.4.203
ip dhcp excluded-address 192.168.4.225 192.168.4.235
Verification
To verify the DHCP configuration and ensure it is functioning correctly, use the following commands:

Show DHCP Leases

show ip dhcp binding
Show DHCP Pool Statistics

show ip dhcp pool
Show DHCP Server Statistics

show ip dhcp server statistics

By following these configurations, the DHCP server will dynamically allocate IP addresses to devices within each VLAN, ensuring efficient IP address management and network connectivity.

This document provides a detailed overview and configuration steps for setting up DHCP on your net