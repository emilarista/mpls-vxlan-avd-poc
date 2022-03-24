# MPLS_NETWORK

# Table of Contents

- [Fabric Switches and Management IP](#fabric-switches-and-management-ip)
  - [Fabric Switches with inband Management IP](#fabric-switches-with-inband-management-ip)
- [Fabric Topology](#fabric-topology)
- [Fabric IP Allocation](#fabric-ip-allocation)
  - [Fabric Point-To-Point Links](#fabric-point-to-point-links)
  - [Point-To-Point Links Node Allocation](#point-to-point-links-node-allocation)
  - [Loopback Interfaces (BGP EVPN Peering)](#loopback-interfaces-bgp-evpn-peering)
  - [Loopback0 Interfaces Node Allocation](#loopback0-interfaces-node-allocation)
  - [ISIS CLNS interfaces](#isis-clns-interfaces)
  - [VTEP Loopback VXLAN Tunnel Source Interfaces (VTEPs Only)](#vtep-loopback-vxlan-tunnel-source-interfaces-vteps-only)
  - [VTEP Loopback Node allocation](#vtep-loopback-node-allocation)

# Fabric Switches and Management IP

| POD | Type | Node | Management IP | Platform | Provisioned in CloudVision |
| --- | ---- | ---- | ------------- | -------- | -------------------------- |
| MPLS_NETWORK | p | P-1A | 10.30.30.103/24 | - | Provisioned |
| MPLS_NETWORK | p | P-1B | 10.30.30.104/24 | - | Provisioned |
| MPLS_NETWORK | p | P-2A | 10.30.30.106/24 | - | Provisioned |
| MPLS_NETWORK | p | P-2B | 10.30.30.107/24 | - | Provisioned |
| MPLS_NETWORK | p | P-3A | 10.30.30.110/24 | - | Provisioned |
| MPLS_NETWORK | p | P-3B | 10.30.30.111/24 | - | Provisioned |
| MPLS_NETWORK | p | P-4A | 10.30.30.115/24 | - | Provisioned |
| MPLS_NETWORK | p | P-4B | 10.30.30.116/24 | - | Provisioned |
| MPLS_NETWORK | pe | PE-1A | 10.30.30.101/24 | vEOS-LAB | Provisioned |
| MPLS_NETWORK | pe | PE-1B | 10.30.30.102/24 | vEOS-LAB | Provisioned |
| MPLS_NETWORK | pe | PE-2 | 10.30.30.105/24 | vEOS-LAB | Provisioned |
| MPLS_NETWORK | pe | PE-3 | 10.30.30.109/24 | vEOS-LAB | Provisioned |
| MPLS_NETWORK | pe | PE-4A | 10.30.30.113/24 | vEOS-LAB | Provisioned |
| MPLS_NETWORK | pe | PE-4B | 10.30.30.114/24 | vEOS-LAB | Provisioned |

> Provision status is based on Ansible inventory declaration and do not represent real status from CloudVision.

## Fabric Switches with inband Management IP
| POD | Type | Node | Management IP | Inband Interface |
| --- | ---- | ---- | ------------- | ---------------- |

# Fabric Topology

| Type | Node | Node Interface | Peer Type | Peer Node | Peer Interface |
| ---- | ---- | -------------- | --------- | ----------| -------------- |
| p | P-1A | Ethernet2 | pe | PE-1A | Ethernet2 |
| p | P-1A | Ethernet3 | p | P-2A | Ethernet3 |
| p | P-1A | Ethernet6 | p | P-1B | Ethernet6 |
| p | P-1B | Ethernet2 | pe | PE-1B | Ethernet2 |
| p | P-1B | Ethernet3 | p | P-4A | Ethernet3 |
| p | P-1B | Ethernet4 | p | P-3A | Ethernet4 |
| p | P-2A | Ethernet2 | pe | PE-2 | Ethernet4 |
| p | P-2A | Ethernet6 | p | P-2B | Ethernet6 |
| p | P-2B | Ethernet2 | pe | PE-2 | Ethernet5 |
| p | P-2B | Ethernet3 | p | P-3A | Ethernet3 |
| p | P-2B | Ethernet4 | p | P-4A | Ethernet4 |
| p | P-3A | Ethernet2 | pe | PE-3 | Ethernet4 |
| p | P-3A | Ethernet6 | p | P-3B | Ethernet6 |
| p | P-3B | Ethernet2 | pe | PE-3 | Ethernet5 |
| p | P-3B | Ethernet3 | p | P-4B | Ethernet3 |
| p | P-4A | Ethernet2 | pe | PE-4A | Ethernet2 |
| p | P-4A | Ethernet6 | p | P-4B | Ethernet6 |
| p | P-4B | Ethernet2 | pe | PE-4B | Ethernet2 |

# Fabric IP Allocation

## Fabric Point-To-Point Links

| Uplink IPv4 Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ---------------- | ------------------- | ------------------ | ------------------ |

## Point-To-Point Links Node Allocation

| Node | Node Interface | Node IP Address | Peer Node | Peer Interface | Peer IP Address |
| ---- | -------------- | --------------- | --------- | -------------- | --------------- |
| P-1A | Ethernet2 | 100.64.48.0/31 | PE-1A | Ethernet2 | 100.64.48.1/31 |
| P-1A | Ethernet3 | 100.64.48.4/31 | P-2A | Ethernet3 | 100.64.48.5/31 |
| P-1A | Ethernet6 | 100.64.48.2/31 | P-1B | Ethernet6 | 100.64.48.3/31 |
| P-1B | Ethernet2 | 100.64.48.6/31 | PE-1B | Ethernet2 | 100.64.48.7/31 |
| P-1B | Ethernet3 | 100.64.48.10/31 | P-4A | Ethernet3 | 100.64.48.11/31 |
| P-1B | Ethernet4 | 100.64.48.8/31 | P-3A | Ethernet4 | 100.64.48.9/31 |
| P-2A | Ethernet2 | 100.64.48.28/31 | PE-2 | Ethernet4 | 100.64.48.29/31 |
| P-2A | Ethernet6 | 100.64.48.30/31 | P-2B | Ethernet6 | 100.64.48.31/31 |
| P-2B | Ethernet2 | 100.64.48.32/31 | PE-2 | Ethernet5 | 100.64.48.33/31 |
| P-2B | Ethernet3 | 100.64.48.17/31 | P-3A | Ethernet3 | 100.64.48.16/31 |
| P-2B | Ethernet4 | 100.64.48.34/31 | P-4A | Ethernet4 | 100.64.48.35/31 |
| P-3A | Ethernet2 | 100.64.48.12/31 | PE-3 | Ethernet4 | 100.64.48.13/31 |
| P-3A | Ethernet6 | 100.64.48.14/31 | P-3B | Ethernet6 | 100.64.48.15/31 |
| P-3B | Ethernet2 | 100.64.48.18/31 | PE-3 | Ethernet5 | 100.64.48.19/31 |
| P-3B | Ethernet3 | 100.64.48.20/31 | P-4B | Ethernet3 | 100.64.48.21/31 |
| P-4A | Ethernet2 | 100.64.48.36/31 | PE-4A | Ethernet2 | 100.64.48.37/31 |
| P-4A | Ethernet6 | 100.64.48.36/31 | P-4B | Ethernet6 | 100.64.48.37/31 |
| P-4B | Ethernet2 | 100.64.48.36/31 | PE-4B | Ethernet2 | 100.64.48.37/31 |

## Loopback Interfaces (BGP EVPN Peering)

| Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ------------- | ------------------- | ------------------ | ------------------ |
| 100.70.1.0/24 | 256 | 6 | 2.35 % |
| 100.70.3.0/24 | 256 | 8 | 3.13 % |

## Loopback0 Interfaces Node Allocation

| POD | Node | Loopback0 |
| --- | ---- | --------- |
| MPLS_NETWORK | P-1A | 100.70.3.1/32 |
| MPLS_NETWORK | P-1B | 100.70.3.2/32 |
| MPLS_NETWORK | P-2A | 100.70.3.3/32 |
| MPLS_NETWORK | P-2B | 100.70.3.4/32 |
| MPLS_NETWORK | P-3A | 100.70.3.5/32 |
| MPLS_NETWORK | P-3B | 100.70.3.6/32 |
| MPLS_NETWORK | P-4A | 100.70.3.7/32 |
| MPLS_NETWORK | P-4B | 100.70.3.8/32 |
| MPLS_NETWORK | PE-1A | 100.70.1.1/32 |
| MPLS_NETWORK | PE-1B | 100.70.1.2/32 |
| MPLS_NETWORK | PE-2 | 100.70.1.3/32 |
| MPLS_NETWORK | PE-3 | 100.70.1.4/32 |
| MPLS_NETWORK | PE-4A | 100.70.1.5/32 |
| MPLS_NETWORK | PE-4B | 100.70.1.6/32 |

## ISIS CLNS interfaces

| POD | Node | CLNS Address |
| --- | ---- | ------------ |
| MPLS_NETWORK | P-1A | 49.0001.0000.0003.0001.00 |
| MPLS_NETWORK | P-1B | 49.0001.0000.0003.0002.00 |
| MPLS_NETWORK | P-2A | 49.0001.0000.0003.0003.00 |
| MPLS_NETWORK | P-2B | 49.0001.0000.0003.0004.00 |
| MPLS_NETWORK | P-3A | 49.0001.0000.0003.0005.00 |
| MPLS_NETWORK | P-3B | 49.0001.0000.0003.0006.00 |
| MPLS_NETWORK | P-4A | 49.0001.0000.0003.0007.00 |
| MPLS_NETWORK | P-4B | 49.0001.0000.0003.0008.00 |
| MPLS_NETWORK | PE-1A | 49.0001.0000.0001.0001.00 |
| MPLS_NETWORK | PE-1B | 49.0001.0000.0001.0002.00 |
| MPLS_NETWORK | PE-2 | 49.0001.0000.0001.0003.00 |
| MPLS_NETWORK | PE-3 | 49.0001.0000.0001.0004.00 |
| MPLS_NETWORK | PE-4A | 49.0001.0000.0001.0005.00 |
| MPLS_NETWORK | PE-4B | 49.0001.0000.0001.0006.00 |

## VTEP Loopback VXLAN Tunnel Source Interfaces (VTEPs Only)

| VTEP Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| --------------------- | ------------------- | ------------------ | ------------------ |

## VTEP Loopback Node allocation

| POD | Node | Loopback1 |
| --- | ---- | --------- |
