# VXLAN_NETWORK

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
| VXLAN_ISLAND2 | l3leaf | GW2 | 10.30.30.105/24 | vEOS-LAB | Provisioned |
| VXLAN_ISLAND3 | l3leaf | GW3 | 10.30.30.105/24 | vEOS-LAB | Provisioned |
| VXLAN_ISLAND2 | l3leaf | LF2 | 10.30.30.103/24 | vEOS-LAB | Provisioned |
| VXLAN_ISLAND3 | l3leaf | LF3 | 10.30.30.103/24 | vEOS-LAB | Provisioned |
| VXLAN_ISLAND2 | spine | SP2 | 10.30.30.102/24 | vEOS-LAB | Provisioned |
| VXLAN_ISLAND3 | spine | SP3 | 10.30.30.102/24 | vEOS-LAB | Provisioned |

> Provision status is based on Ansible inventory declaration and do not represent real status from CloudVision.

## Fabric Switches with inband Management IP
| POD | Type | Node | Management IP | Inband Interface |
| --- | ---- | ---- | ------------- | ---------------- |

# Fabric Topology

| Type | Node | Node Interface | Peer Type | Peer Node | Peer Interface |
| ---- | ---- | -------------- | --------- | ----------| -------------- |
| l3leaf | GW2 | Ethernet2 | spine | SP2 | Ethernet2 |
| l3leaf | GW3 | Ethernet2 | spine | SP3 | Ethernet2 |
| l3leaf | LF2 | Ethernet1 | spine | SP2 | Ethernet1 |
| l3leaf | LF3 | Ethernet1 | spine | SP3 | Ethernet1 |

# Fabric IP Allocation

## Fabric Point-To-Point Links

| Uplink IPv4 Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ---------------- | ------------------- | ------------------ | ------------------ |
| 100.64.22.0/24 | 256 | 4 | 1.57 % |
| 100.64.32.0/24 | 256 | 4 | 1.57 % |

## Point-To-Point Links Node Allocation

| Node | Node Interface | Node IP Address | Peer Node | Peer Interface | Peer IP Address |
| ---- | -------------- | --------------- | --------- | -------------- | --------------- |
| GW2 | Ethernet2 | 100.64.22.7/31 | SP2 | Ethernet2 | 100.64.22.6/31 |
| GW3 | Ethernet2 | 100.64.32.7/31 | SP3 | Ethernet2 | 100.64.32.6/31 |
| LF2 | Ethernet1 | 100.64.22.1/31 | SP2 | Ethernet1 | 100.64.22.0/31 |
| LF3 | Ethernet1 | 100.64.32.1/31 | SP3 | Ethernet1 | 100.64.32.0/31 |

## Loopback Interfaces (BGP EVPN Peering)

| Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ------------- | ------------------- | ------------------ | ------------------ |
| 100.64.20.0/24 | 256 | 3 | 1.18 % |
| 100.64.30.0/24 | 256 | 3 | 1.18 % |

## Loopback0 Interfaces Node Allocation

| POD | Node | Loopback0 |
| --- | ---- | --------- |
| VXLAN_ISLAND2 | GW2 | 100.64.20.12/32 |
| VXLAN_ISLAND3 | GW3 | 100.64.30.12/32 |
| VXLAN_ISLAND2 | LF2 | 100.64.20.11/32 |
| VXLAN_ISLAND3 | LF3 | 100.64.30.11/32 |
| VXLAN_ISLAND2 | SP2 | 100.64.20.1/32 |
| VXLAN_ISLAND3 | SP3 | 100.64.30.1/32 |

## ISIS CLNS interfaces

| POD | Node | CLNS Address |
| --- | ---- | ------------ |
| VXLAN_ISLAND2 | GW2 | 49.0001.0000.0022.0002.00 |
| VXLAN_ISLAND3 | GW3 | 49.0001.0000.0033.0002.00 |
| VXLAN_ISLAND2 | LF2 | 49.0001.0000.0022.0001.00 |
| VXLAN_ISLAND3 | LF3 | 49.0001.0000.0033.0001.00 |
| VXLAN_ISLAND2 | SP2 | 49.0001.0000.0020.0001.00 |
| VXLAN_ISLAND3 | SP3 | 49.0001.0000.0030.0001.00 |

## VTEP Loopback VXLAN Tunnel Source Interfaces (VTEPs Only)

| VTEP Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| --------------------- | ------------------- | ------------------ | ------------------ |
| 100.64.21.0/24 | 256 | 2 | 0.79 % |
| 100.64.31.0/24 | 256 | 2 | 0.79 % |

## VTEP Loopback Node allocation

| POD | Node | Loopback1 |
| --- | ---- | --------- |
| VXLAN_ISLAND2 | GW2 | 100.64.21.12/32 |
| VXLAN_ISLAND3 | GW3 | 100.64.31.12/32 |
| VXLAN_ISLAND2 | LF2 | 100.64.21.11/32 |
| VXLAN_ISLAND3 | LF3 | 100.64.31.11/32 |
