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
| MPLS_NETWORK | rr | P1-A | 172.16.32.209/24 | vEOS-LAB | Provisioned |
| MPLS_NETWORK | p | P1-B | 172.16.32.203/24 | - | Provisioned |
| MPLS_NETWORK | rr | P2-A | 172.16.32.202/24 | vEOS-LAB | Provisioned |
| MPLS_NETWORK | p | P2-B | 172.16.32.204/24 | - | Provisioned |
| MPLS_NETWORK | p | P3-A | 172.16.32.205/24 | - | Provisioned |
| MPLS_NETWORK | p | P3-B | 172.16.32.207/24 | - | Provisioned |
| MPLS_NETWORK | p | P4-A | 172.16.32.206/24 | - | Provisioned |
| MPLS_NETWORK | p | P4-B | 172.16.32.208/24 | - | Provisioned |
| MPLS_NETWORK | pe | PE-1A | 172.16.32.209/24 | vEOS-LAB | Provisioned |
| MPLS_NETWORK | pe | PE-1B | 172.16.32.210/24 | vEOS-LAB | Provisioned |
| MPLS_NETWORK | pe | PE-2 | 172.16.32.212/24 | vEOS-LAB | Provisioned |
| MPLS_NETWORK | pe | PE-3 | 172.16.32.214/24 | vEOS-LAB | Provisioned |
| MPLS_NETWORK | pe | PE-4A | 172.16.32.216/24 | vEOS-LAB | Provisioned |
| MPLS_NETWORK | pe | PE-4B | 172.16.32.217/24 | vEOS-LAB | Provisioned |

> Provision status is based on Ansible inventory declaration and do not represent real status from CloudVision.

## Fabric Switches with inband Management IP
| POD | Type | Node | Management IP | Inband Interface |
| --- | ---- | ---- | ------------- | ---------------- |

# Fabric Topology

| Type | Node | Node Interface | Peer Type | Peer Node | Peer Interface |
| ---- | ---- | -------------- | --------- | ----------| -------------- |
| rr | P1-A | Ethernet2 | pe | PE-1A | Ethernet2 |
| rr | P1-A | Ethernet3 | rr | P2-A | Ethernet3 |
| rr | P1-A | Ethernet6 | p | P1-B | Ethernet6 |
| p | P1-B | Ethernet2 | pe | PE-1B | Ethernet2 |
| p | P1-B | Ethernet3 | p | P4-A | Ethernet3 |
| p | P1-B | Ethernet4 | p | P3-A | Ethernet4 |
| rr | P2-A | Ethernet2 | pe | PE-2 | Ethernet4 |
| rr | P2-A | Ethernet6 | p | P2-B | Ethernet6 |
| p | P2-B | Ethernet2 | pe | PE-2 | Ethernet5 |
| p | P2-B | Ethernet3 | p | P3-A | Ethernet3 |
| p | P2-B | Ethernet4 | p | P4-A | Ethernet4 |
| p | P3-A | Ethernet2 | pe | PE-3 | Ethernet4 |
| p | P3-A | Ethernet6 | p | P3-B | Ethernet6 |
| p | P3-B | Ethernet2 | pe | PE-3 | Ethernet5 |
| p | P3-B | Ethernet3 | p | P4-B | Ethernet3 |
| p | P4-A | Ethernet2 | pe | PE-4A | Ethernet2 |
| p | P4-A | Ethernet6 | p | P4-B | Ethernet6 |
| p | P4-B | Ethernet2 | pe | PE-4B | Ethernet2 |

# Fabric IP Allocation

## Fabric Point-To-Point Links

| Uplink IPv4 Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ---------------- | ------------------- | ------------------ | ------------------ |

## Point-To-Point Links Node Allocation

| Node | Node Interface | Node IP Address | Peer Node | Peer Interface | Peer IP Address |
| ---- | -------------- | --------------- | --------- | -------------- | --------------- |
| P1-A | Ethernet2 | 100.64.48.0/31 | PE-1A | Ethernet2 | 100.64.48.1/31 |
| P1-A | Ethernet3 | 100.64.48.4/31 | P2-A | Ethernet3 | 100.64.48.5/31 |
| P1-A | Ethernet6 | 100.64.48.2/31 | P1-B | Ethernet6 | 100.64.48.3/31 |
| P1-B | Ethernet2 | 100.64.48.6/31 | PE-1B | Ethernet2 | 100.64.48.7/31 |
| P1-B | Ethernet3 | 100.64.48.10/31 | P4-A | Ethernet3 | 100.64.48.11/31 |
| P1-B | Ethernet4 | 100.64.48.8/31 | P3-A | Ethernet4 | 100.64.48.9/31 |
| P2-A | Ethernet2 | 100.64.48.28/31 | PE-2 | Ethernet4 | 100.64.48.29/31 |
| P2-A | Ethernet6 | 100.64.48.30/31 | P2-B | Ethernet6 | 100.64.48.31/31 |
| P2-B | Ethernet2 | 100.64.48.32/31 | PE-2 | Ethernet5 | 100.64.48.33/31 |
| P2-B | Ethernet3 | 100.64.48.17/31 | P3-A | Ethernet3 | 100.64.48.16/31 |
| P2-B | Ethernet4 | 100.64.48.34/31 | P4-A | Ethernet4 | 100.64.48.35/31 |
| P3-A | Ethernet2 | 100.64.48.12/31 | PE-3 | Ethernet4 | 100.64.48.13/31 |
| P3-A | Ethernet6 | 100.64.48.14/31 | P3-B | Ethernet6 | 100.64.48.15/31 |
| P3-B | Ethernet2 | 100.64.48.18/31 | PE-3 | Ethernet5 | 100.64.48.19/31 |
| P3-B | Ethernet3 | 100.64.48.20/31 | P4-B | Ethernet3 | 100.64.48.21/31 |
| P4-A | Ethernet2 | 100.64.48.36/31 | PE-4A | Ethernet2 | 100.64.48.37/31 |
| P4-A | Ethernet6 | 100.64.48.38/31 | P4-B | Ethernet6 | 100.64.48.39/31 |
| P4-B | Ethernet2 | 100.64.48.40/31 | PE-4B | Ethernet2 | 100.64.48.41/31 |

## Loopback Interfaces (BGP EVPN Peering)

| Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ------------- | ------------------- | ------------------ | ------------------ |
| 100.70.1.0/24 | 256 | 6 | 2.35 % |
| 100.70.2.0/24 | 256 | 2 | 0.79 % |
| 100.70.3.0/24 | 256 | 6 | 2.35 % |

## Loopback0 Interfaces Node Allocation

| POD | Node | Loopback0 |
| --- | ---- | --------- |
| MPLS_NETWORK | P1-A | 100.70.2.1/32 |
| MPLS_NETWORK | P1-B | 100.70.3.32/32 |
| MPLS_NETWORK | P2-A | 100.70.2.2/32 |
| MPLS_NETWORK | P2-B | 100.70.3.34/32 |
| MPLS_NETWORK | P3-A | 100.70.3.35/32 |
| MPLS_NETWORK | P3-B | 100.70.3.36/32 |
| MPLS_NETWORK | P4-A | 100.70.3.37/32 |
| MPLS_NETWORK | P4-B | 100.70.3.38/32 |
| MPLS_NETWORK | PE-1A | 100.70.1.11/32 |
| MPLS_NETWORK | PE-1B | 100.70.1.12/32 |
| MPLS_NETWORK | PE-2 | 100.70.1.13/32 |
| MPLS_NETWORK | PE-3 | 100.70.1.14/32 |
| MPLS_NETWORK | PE-4A | 100.70.1.15/32 |
| MPLS_NETWORK | PE-4B | 100.70.1.16/32 |

## ISIS CLNS interfaces

| POD | Node | CLNS Address |
| --- | ---- | ------------ |
| MPLS_NETWORK | P1-A | 49.0001.0000.0002.0001.00 |
| MPLS_NETWORK | P1-B | 49.0001.0000.0003.0002.00 |
| MPLS_NETWORK | P2-A | 49.0001.0000.0002.0002.00 |
| MPLS_NETWORK | P2-B | 49.0001.0000.0003.0004.00 |
| MPLS_NETWORK | P3-A | 49.0001.0000.0003.0005.00 |
| MPLS_NETWORK | P3-B | 49.0001.0000.0003.0006.00 |
| MPLS_NETWORK | P4-A | 49.0001.0000.0003.0007.00 |
| MPLS_NETWORK | P4-B | 49.0001.0000.0003.0008.00 |
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
