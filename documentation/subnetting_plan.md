# Subnetting Plan

This document outlines the subnetting plan for the hospital network design, which includes the headquarters (HQ) and the branch office. The subnetting plan is designed to accommodate the specific user requirements for each department and ensure efficient IP address allocation.

## IP Addressing Scheme

### HQ IP Addressing

- **Network Address**: 192.168.0.0/22
- **Total Hosts**: 1024

Each department at HQ requires 60 users. To provide adequate IP addresses and allow for future growth, we use a subnet mask of /26 (255.255.255.192), which provides 64 IP addresses per subnet (62 usable addresses).

#### Departments and Subnets

| Department          | Subnet ID        | Subnet Mask       | IP Range                            | Usable IP Addresses  |
|---------------------|------------------|-------------------|-------------------------------------|----------------------|
| Administration      | 192.168.0.0      | 255.255.255.192   | 192.168.0.1 - 192.168.0.62          | 62                   |
| Emergency           | 192.168.0.64     | 255.255.255.192   | 192.168.0.65 - 192.168.0.126        | 62                   |
| Outpatient          | 192.168.0.128    | 255.255.255.192   | 192.168.0.129 - 192.168.0.190       | 62                   |
| Inpatient           | 192.168.0.192    | 255.255.255.192   | 192.168.0.193 - 192.168.0.254       | 62                   |
| Radiology           | 192.168.1.0      | 255.255.255.192   | 192.168.1.1 - 192.168.1.62          | 62                   |
| Laboratory          | 192.168.1.64     | 255.255.255.192   | 192.168.1.65 - 192.168.1.126        | 62                   |
| Pharmacy            | 192.168.1.128    | 255.255.255.192   | 192.168.1.129 - 192.168.1.190       | 62                   |
| IT Department       | 192.168.1.192    | 255.255.255.192   | 192.168.1.193 - 192.168.1.254       | 62                   |
| Guest Network       | 192.168.2.0      | 255.255.255.192   | 192.168.2.1 - 192.168.2.62          | 62                   |
| Server Room         | 192.168.2.64     | 255.255.255.192   | 192.168.2.65 - 192.168.2.126        | 62                   |

### Branch IP Addressing

- **Network Address**: 192.168.4.0/23
- **Total Hosts**: 512

Each department at the branch requires 30 users. To provide adequate IP addresses and allow for future growth, we use a subnet mask of /27 (255.255.255.224), which provides 32 IP addresses per subnet (30 usable addresses).

#### Departments and Subnets

| Department          | Subnet ID        | Subnet Mask       | IP Range                      | Usable IP Addresses  |
|---------------------|------------------|-------------------|-------------------------------|----------------------|
| Administration      | 192.168.4.0      | 255.255.255.224   | 192.168.4.1 - 192.168.4.30    | 30                   |
| Emergency           | 192.168.4.32     | 255.255.255.224   | 192.168.4.33 - 192.168.4.62   | 30                   |
| Outpatient          | 192.168.4.64     | 255.255.255.224   | 192.168.4.65 - 192.168.4.94   | 30                   |
| Inpatient           | 192.168.4.96     | 255.255.255.224   | 192.168.4.97 - 192.168.4.126  | 30                   |
| Radiology           | 192.168.4.128    | 255.255.255.224   | 192.168.4.129 - 192.168.4.158 | 30                   |
| Laboratory          | 192.168.4.160    | 255.255.255.224   | 192.168.4.161 - 192.168.4.190 | 30                   |
| Pharmacy            | 192.168.4.192    | 255.255.255.224   | 192.168.4.193 - 192.168.4.222 | 30                   |
| IT Department       | 192.168.4.224    | 255.255.255.224   | 192.168.4.225 - 192.168.4.254 | 30                   |

### Summary
- **HQ Network**: 192.168.0.0/22, providing 1024 IP addresses.
- **Branch Network**: 192.168.4.0/23, providing 512 IP addresses.
- **Subnet Mask for HQ Departments**: /26 (255.255.255.192)
- **Subnet Mask for Branch Departments**: /27 (255.255.255.224)

This subnetting plan ensures that each department has enough IP addresses to meet current needs and allows for future expansion. The use of different subnet masks for HQ and the branch optimizes IP address utilization and simplifies network management.
