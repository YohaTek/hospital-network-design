# Hospital Network Design

A documented Cisco network design for a hospital with a **headquarters (HQ)** and a
**branch office**. The design uses a three-tier architecture (Core / Distribution /
Access) and combines HSRP gateway redundancy, OSPF routing, site-to-site IPsec VPN,
VLAN segmentation, DHCP, NAT overload, ACLs, port security, WPA2 wireless, and SSH
management. The topology was built and exercised in **Cisco Packet Tracer**.

This repository holds the design documentation, the subnetting and VLAN plans, the
device configuration excerpts, and the network diagram. There is no build step — the
deliverable is the documentation itself.

## Repository layout

```text
.
├── README.md                      # this file: overview and document index
├── documentation/                 # written design documents (see index below)
│   ├── design_overview.md         # architecture and technology rationale
│   ├── technology_implemented.md  # 16 technologies, purpose and implementation
│   ├── subnetting_plan.md         # HQ /22 and branch /23 address plan
│   ├── vlan_plan.md               # VLAN IDs, names, subnets, trunking
│   ├── acl_rules.md               # standard and extended ACL rules
│   └── dhcp_configuration.md      # DHCP pools, exclusions, verification
├── diagrams/
│   ├── network_diagram.png        # rendered topology (HQ + branch)
│   └── detailed_network_diagram.drawio
└── configs/                       # per-device IOS configuration excerpts
    ├── hq_router_config.txt
    ├── hq_switch_config.txt
    ├── branch_router_config.txt
    ├── branch_switch_config.txt
    └── firewall_config.txt
```

## Design at a glance

| Item | Headquarters | Branch office |
| --- | --- | --- |
| Address block | `192.168.0.0/22` | `192.168.4.0/23` |
| Departments | 10 | 8 |
| Users per department | 60 | 30 |
| Department subnet | `/26` (`255.255.255.192`) | `/27` (`255.255.255.224`) |
| VLAN IDs | 10–100 | 110–180 |
| Gateway redundancy | HSRP on distribution switches | HSRP on distribution switches |
| Routing | OSPF single area + static default route | OSPF single area + static default route |
| Inter-site link | Site-to-site IPsec VPN over the WAN | Site-to-site IPsec VPN over the WAN |

Department-to-VLAN and department-to-subnet mappings are in
[vlan_plan.md](documentation/vlan_plan.md) and
[subnetting_plan.md](documentation/subnetting_plan.md).

## Document index

| Document | Status |
| --- | --- |
| [design_overview.md](documentation/design_overview.md) | Written — architecture, layers, technologies |
| [technology_implemented.md](documentation/technology_implemented.md) | Written — 16 technologies and how each is implemented |
| [subnetting_plan.md](documentation/subnetting_plan.md) | Written — full subnet tables for HQ and branch |
| [vlan_plan.md](documentation/vlan_plan.md) | Written — VLAN assignments, trunking, example trunk config |
| [acl_rules.md](documentation/acl_rules.md) | Written — standard and extended ACL rules, verification |
| [dhcp_configuration.md](documentation/dhcp_configuration.md) | Written — DHCP pools, exclusions, verification |
| [Network diagram](diagrams/network_diagram.png) | Written — rendered topology (4260×2523 PNG) |
| [email_server_configuration.md](documentation/email_server_configuration.md) | **Placeholder** — file is empty |
| [ssh_configuration.md](documentation/ssh_configuration.md) | **Placeholder** — file is empty |
| [wireless_ap_configuration.md](documentation/wireless_ap_configuration.md) | **Placeholder** — file is empty |
| [vpn_configuration.md](documentation/vpn_configuration.md) | **Placeholder** — file is empty |
| [detailed_network_diagram.drawio](diagrams/detailed_network_diagram.drawio) | **Placeholder** — file is empty |
| Per-device `configs/*.txt` | **Placeholder** — files are empty |

Placeholders are reserved names for sections that are still to be written; the
design intent for each is described in
[technology_implemented.md](documentation/technology_implemented.md). Do not treat
an empty file as evidence that a feature was configured.

## Reading order

1. [design_overview.md](documentation/design_overview.md) — why the network looks
   the way it does.
2. [subnetting_plan.md](documentation/subnetting_plan.md) — the address plan.
3. [vlan_plan.md](documentation/vlan_plan.md) — VLANs, trunks, inter-VLAN routing.
4. [acl_rules.md](documentation/acl_rules.md) — traffic filtering between segments.
5. [dhcp_configuration.md](documentation/dhcp_configuration.md) — dynamic addressing.
6. [technology_implemented.md](documentation/technology_implemented.md) — reference
   for every technology and its Packet Tracer implementation.

## Prerequisites

- **Cisco Packet Tracer** (or a compatible simulator) to open and extend the
  topology. Some features are simplified because of Packet Tracer limitations — for
  example route-maps for dual-ISP failover are described in the design but not
  implemented.
- A Markdown viewer (GitHub renders `.md` files directly).
- [draw.io / diagrams.net](https://app.diagrams.net) to edit the
  `diagrams/*.drawio` source, once it exists.

No compiler, package manager, or `make` target is needed.

## Using the repository

```bash
git clone https://github.com/YohaTek/hospital-network-design.git
cd hospital-network-design
```

Then open [documentation/design_overview.md](documentation/design_overview.md) and
follow the reading order above. The configuration snippets in the documents are IOS
CLI excerpts — adapt interface names and addresses to your own lab before pasting
them into a device.

## Roadmap / known gaps

- Fill in the empty placeholder documents: email server, SSH, wireless AP, and VPN
  configuration.
- Add the per-device configuration files under `configs/`.
- Export the editable topology to `diagrams/detailed_network_diagram.drawio`.
- Remove the empty `documentation/network_diagram.png` duplicate; the rendered
  diagram lives in `diagrams/network_diagram.png`.
- Add a `LICENSE` file if the material is meant to be reused.

## Contributing

Small documentation fixes are welcome: keep the subnet and VLAN tables consistent
with each other, and describe Cisco IOS snippets in fenced code blocks so they render
correctly.
