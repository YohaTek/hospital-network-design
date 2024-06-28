# ACL Rules

This document outlines the Access Control List (ACL) rules implemented in the hospital network design to enhance security by controlling traffic flow. Both standard and extended ACLs are used to restrict access and ensure that only authorized traffic is allowed.

## Overview

ACLs are used to:
- Permit or deny traffic based on source and destination IP addresses.
- Control traffic flow into and out of the network.
- Provide an additional layer of security by limiting access to sensitive resources.

## Standard ACL Rules

### Rule 1: Permit Administration Network Access to IT Resources

Allow the administration network (192.168.0.0/26) to access IT department resources (192.168.1.192/26).

#### Configuration

access-list 10 permit 192.168.0.0 0.0.0.63
!
interface Vlan80
 ip access-group 10 in



### Rule 2: Deny Guest Network Access to Sensitive VLANs

Deny the guest network (192.168.2.0/26) access to all other VLANs except for the internet.

####Configuration

access-list 20 deny 192.168.2.0 0.0.0.63
access-list 20 permit any
!
interface Vlan90
 ip access-group 20 in

### Rule 3: Permit HTTP and HTTPS Traffic to the Web Server
Allow HTTP and HTTPS traffic from any source to the web server located in the server VLAN (192.168.2.64/26).

#### Configuration

access-list 100 permit tcp any host 192.168.2.70 eq 80
access-list 100 permit tcp any host 192.168.2.70 eq 443
!
interface Vlan100
 ip access-group 100 in

### Rule 4: Deny All Other Traffic to the Web Server
Deny all other traffic to the web server to ensure it is only accessible via HTTP and HTTPS.

#### Configuration

access-list 101 deny ip any host 192.168.2.70
access-list 101 permit ip any any
!
interface Vlan100
 ip access-group 101 in

### Rule 5: Permit Internal Network Traffic

Allow all internal network traffic between VLANs for standard operations and communications.

#### Configuration

access-list 110 permit ip 192.168.0.0 0.0.3.255 192.168.0.0 0.0.3.255
!
interface Vlan10
 ip access-group 110 in
interface Vlan20
 ip access-group 110 in
interface Vlan30
 ip access-group 110 in
interface Vlan40
 ip access-group 110 in
interface Vlan50
 ip access-group 110 in
interface Vlan60
 ip access-group 110 in
interface Vlan70
 ip access-group 110 in
interface Vlan80
 ip access-group 110 in
interface Vlan90
 ip access-group 110 in
interface Vlan100
 ip access-group 110 in

### Rule 6: Deny All Traffic to Restricted Servers
Deny all traffic from the guest network to the restricted servers in the server VLAN.

#### Configuration

access-list 120 deny ip 192.168.2.0 0.0.0.63 192.168.2.64 0.0.0.63
access-list 120 permit ip any any
!
interface Vlan100
 ip access-group 120 in
Applying ACLs to Interfaces
To apply ACLs to interfaces, use the following commands:


Interface Configurations

interface Vlan10
 ip address 192.168.0.1 255.255.255.192
 ip access-group 10 in
!
interface Vlan90
 ip address 192.168.2.1 255.255.255.192
 ip access-group 20 in
!
interface Vlan100
 ip address 192.168.2.65 255.255.255.192
 ip access-group 100 in
 ip access-group 101 in
 ip access-group 120 in
!
interface Vlan80
 ip address 192.168.1.193 255.255.255.192
 ip access-group 10 in
 ip access-group 110 in
Verifying ACLs
To verify the ACLs, use the following commands:


show access-lists
show running-config | include access-list
show ip interface Vlan10
show ip interface Vlan90
show ip interface Vlan100