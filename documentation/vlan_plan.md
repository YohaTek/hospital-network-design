# VLAN Plan

This document outlines the VLAN (Virtual Local Area Network) configuration for the hospital network design, including both the headquarters (HQ) and the branch office. VLANs are implemented to segment network traffic, enhance security, and improve performance.

## VLAN Configuration Overview

### VLAN Benefits
- **Security**: VLANs isolate sensitive traffic, reducing the risk of unauthorized access.
- **Performance**: Segregating traffic into VLANs reduces broadcast domains, improving overall network performance.
- **Manageability**: VLANs make it easier to manage and troubleshoot network segments.

### VLAN Implementation
- **VLANs are configured on Access layer switches.**
- **Inter-VLAN routing is handled by Distribution layer switches using SVIs (Switched Virtual Interfaces).**

## VLAN Assignments

### HQ VLANs

| VLAN ID | VLAN Name        | Department          | Subnet              | Description                     |
|---------|------------------|---------------------|---------------------|---------------------------------|
| 10      | VLAN_ADMIN       | Administration      | 192.168.0.0/26      | Administrative staff& resources |
| 20      | VLAN_EMERGENCY   | Emergency           | 192.168.0.64/26     | Emergency department            |
| 30      | VLAN_OUTPATIENT  | Outpatient          | 192.168.0.128/26    | Outpatient services             |
| 40      | VLAN_INPATIENT   | Inpatient           | 192.168.0.192/26    | Inpatient services              |
| 50      | VLAN_RADIOLOGY   | Radiology           | 192.168.1.0/26      | Radiology department            |
| 60      | VLAN_LAB         | Laboratory          | 192.168.1.64/26     | Laboratory department           |
| 70      | VLAN_PHARMACY    | Pharmacy            | 192.168.1.128/26    | Pharmacy department             |
| 80      | VLAN_IT          | IT Department       | 192.168.1.192/26    | IT department and resources     |
| 90      | VLAN_GUEST       | Guest Network       | 192.168.2.0/26      | Guest Wi-Fi network             |
| 100     | VLAN_SERVER      | Server Room         | 192.168.2.64/26     | Server room devices             |

### Branch VLANs

| VLAN ID | VLAN Name        | Department          | Subnet              | Description                     |
|---------|------------------|---------------------|---------------------|---------------------------------|
| 110     | VLAN_ADMIN_B     | Administration      | 192.168.4.0/27      | Administrative staff &resources |
| 120     | VLAN_EMERGENCY_B | Emergency           | 192.168.4.32/27     | Emergency department            |
| 130     | VLAN_OUTPATIENT_B| Outpatient          | 192.168.4.64/27     | Outpatient services             |
| 140     | VLAN_INPATIENT_B | Inpatient           | 192.168.4.96/27     | Inpatient services              |
| 150     | VLAN_RADIOLOGY_B | Radiology           | 192.168.4.128/27    | Radiology department            |
| 160     | VLAN_LAB_B       | Laboratory          | 192.168.4.160/27    | Laboratory department           |
| 170     | VLAN_PHARMACY_B  | Pharmacy            | 192.168.4.192/27    | Pharmacy department             |
| 180     | VLAN_IT_B        | IT Department       | 192.168.4.224/27    | IT department and resources     |

## VLAN Trunking

### Trunk Links
- **Trunk links are configured between Access layer switches and Distribution layer switches.**
- **Trunk ports are set to carry multiple VLANs, allowing inter-VLAN communication.**

### Example Trunk Configuration
```bash
interface GigabitEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100
