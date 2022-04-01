
# Validate State Report

**Table of Contents:**

- [Validate State Report](validate-state-report)
  - [Test Results Summary](#test-results-summary)
  - [Failed Test Results Summary](#failed-test-results-summary)
  - [All Test Results](#all-test-results)

## Test Results Summary

### Summary Totals

| Total Tests | Total Tests Passed | Total Tests Failed |
| ----------- | ------------------ | ------------------ |
| 82 | 32 | 50 |

### Summary Totals Devices Under Tests

| DUT | Total Tests | Tests Passed | Tests Failed | Categories Failed |
| --- | ----------- | ------------ | ------------ | ----------------- |
| GW2 |  20 | 8 | 12 | Interface State, LLDP Topology, IP Reachability, Routing Table, Loopback0 Reachability |
| GW3 |  20 | 8 | 12 | Interface State, LLDP Topology, IP Reachability, Routing Table, Loopback0 Reachability |
| SPE5 |  21 | 8 | 13 | Interface State, LLDP Topology, IP Reachability, BGP, Routing Table, Loopback0 Reachability |
| SPE6 |  21 | 8 | 13 | Interface State, LLDP Topology, IP Reachability, BGP, Routing Table, Loopback0 Reachability |

### Summary Totals Per Category

| Test Category | Total Tests | Tests Passed | Tests Failed |
| ------------- | ----------- | ------------ | ------------ |
| NTP |  4 | 4 | 0 |
| Interface State |  16 | 12 | 4 |
| LLDP Topology |  4 | 0 | 4 |
| IP Reachability |  4 | 0 | 4 |
| BGP |  6 | 4 | 2 |
| Routing Table |  32 | 8 | 24 |
| Loopback0 Reachability |  16 | 4 | 12 |

## Failed Test Results Summary

| Test ID | Node | Test Category | Test Description | Test | Test Result | Failure Reason |
| ------- | ---- | ------------- | ---------------- | ---- | ----------- | -------------- |
| 9 | GW2 | Interface State | Vxlan Interface Status & Line Protocol == "up" | Vxlan1 | FAIL | interface status: down - line protocol status: down |
| 10 | GW3 | Interface State | Vxlan Interface Status & Line Protocol == "up" | Vxlan1 | FAIL | interface status: down - line protocol status: down |
| 11 | SPE5 | Interface State | Vxlan Interface Status & Line Protocol == "up" | Vxlan1 | FAIL | interface status: down - line protocol status: down |
| 12 | SPE6 | Interface State | Vxlan Interface Status & Line Protocol == "up" | Vxlan1 | FAIL | interface status: down - line protocol status: down |
| 21 | GW2 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet1 - remote: SPE6_Ethernet1 | FAIL | P2-A.clearshark.net - Ethernet5 |
| 22 | GW3 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet1 - remote: SPE5_Ethernet1 | FAIL | P3-B.clearshark.net - Ethernet5 |
| 23 | SPE5 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet1 - remote: GW3_Ethernet1 | FAIL | GW3.clearshark.net - Ethernet2 |
| 24 | SPE6 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet1 - remote: GW2_Ethernet1 | FAIL | GW2.clearshark.net - Ethernet2 |
| 25 | GW2 | IP Reachability | ip reachability test p2p links | Source: GW2_Ethernet1 - Destination: SPE6_Ethernet1 | FAIL | 100% packet loss |
| 26 | GW3 | IP Reachability | ip reachability test p2p links | Source: GW3_Ethernet1 - Destination: SPE5_Ethernet1 | FAIL | 100% packet loss |
| 27 | SPE5 | IP Reachability | ip reachability test p2p links | Source: SPE5_Ethernet1 - Destination: GW3_Ethernet1 | FAIL | 100% packet loss |
| 28 | SPE6 | IP Reachability | ip reachability test p2p links | Source: SPE6_Ethernet1 - Destination: GW2_Ethernet1 | FAIL | 100% packet loss |
| 33 | SPE5 | BGP | bgp evpn peer state established (evpn) | bgp_neighbor: 100.64.30.11 | FAIL | Session state "Active" |
| 34 | SPE6 | BGP | bgp evpn peer state established (evpn) | bgp_neighbor: 100.64.20.11 | FAIL | Session state "Active" |
| 36 | GW2 | Routing Table | Remote VTEP address | 100.64.31.11 | FAIL | VTEP 100.64.31.11 is not in the routing table |
| 37 | GW2 | Routing Table | Remote VTEP address | 100.64.31.12 | FAIL | VTEP 100.64.31.12 is not in the routing table |
| 38 | GW2 | Routing Table | Remote VTEP address | 100.64.21.12 | FAIL | VTEP 100.64.21.12 is not in the routing table |
| 39 | GW3 | Routing Table | Remote VTEP address | 100.64.21.11 | FAIL | VTEP 100.64.21.11 is not in the routing table |
| 41 | GW3 | Routing Table | Remote VTEP address | 100.64.31.12 | FAIL | VTEP 100.64.31.12 is not in the routing table |
| 42 | GW3 | Routing Table | Remote VTEP address | 100.64.21.12 | FAIL | VTEP 100.64.21.12 is not in the routing table |
| 43 | SPE5 | Routing Table | Remote VTEP address | 100.64.21.11 | FAIL | VTEP 100.64.21.11 is not in the routing table |
| 44 | SPE5 | Routing Table | Remote VTEP address | 100.64.31.11 | FAIL | VTEP 100.64.31.11 is not in the routing table |
| 46 | SPE5 | Routing Table | Remote VTEP address | 100.64.21.12 | FAIL | VTEP 100.64.21.12 is not in the routing table |
| 47 | SPE6 | Routing Table | Remote VTEP address | 100.64.21.11 | FAIL | VTEP 100.64.21.11 is not in the routing table |
| 48 | SPE6 | Routing Table | Remote VTEP address | 100.64.31.11 | FAIL | VTEP 100.64.31.11 is not in the routing table |
| 49 | SPE6 | Routing Table | Remote VTEP address | 100.64.31.12 | FAIL | VTEP 100.64.31.12 is not in the routing table |
| 52 | GW2 | Routing Table | Remote Lo0 address | 100.64.30.11 | FAIL | Lo0 100.64.30.11 is not in the routing table |
| 53 | GW2 | Routing Table | Remote Lo0 address | 100.64.30.12 | FAIL | Lo0 100.64.30.12 is not in the routing table |
| 54 | GW2 | Routing Table | Remote Lo0 address | 100.64.20.12 | FAIL | Lo0 100.64.20.12 is not in the routing table |
| 55 | GW3 | Routing Table | Remote Lo0 address | 100.64.20.11 | FAIL | Lo0 100.64.20.11 is not in the routing table |
| 57 | GW3 | Routing Table | Remote Lo0 address | 100.64.30.12 | FAIL | Lo0 100.64.30.12 is not in the routing table |
| 58 | GW3 | Routing Table | Remote Lo0 address | 100.64.20.12 | FAIL | Lo0 100.64.20.12 is not in the routing table |
| 59 | SPE5 | Routing Table | Remote Lo0 address | 100.64.20.11 | FAIL | Lo0 100.64.20.11 is not in the routing table |
| 60 | SPE5 | Routing Table | Remote Lo0 address | 100.64.30.11 | FAIL | Lo0 100.64.30.11 is not in the routing table |
| 62 | SPE5 | Routing Table | Remote Lo0 address | 100.64.20.12 | FAIL | Lo0 100.64.20.12 is not in the routing table |
| 63 | SPE6 | Routing Table | Remote Lo0 address | 100.64.20.11 | FAIL | Lo0 100.64.20.11 is not in the routing table |
| 64 | SPE6 | Routing Table | Remote Lo0 address | 100.64.30.11 | FAIL | Lo0 100.64.30.11 is not in the routing table |
| 65 | SPE6 | Routing Table | Remote Lo0 address | 100.64.30.12 | FAIL | Lo0 100.64.30.12 is not in the routing table |
| 68 | GW2 | Loopback0 Reachability | Loopback0 Reachability | Source: GW2 - 100.64.20.11 Destination: 100.64.30.11 | FAIL | 100% packet loss |
| 69 | GW2 | Loopback0 Reachability | Loopback0 Reachability | Source: GW2 - 100.64.20.11 Destination: 100.64.30.12 | FAIL | 100% packet loss |
| 70 | GW2 | Loopback0 Reachability | Loopback0 Reachability | Source: GW2 - 100.64.20.11 Destination: 100.64.20.12 | FAIL | 100% packet loss |
| 71 | GW3 | Loopback0 Reachability | Loopback0 Reachability | Source: GW3 - 100.64.30.11 Destination: 100.64.20.11 | FAIL | 100% packet loss |
| 73 | GW3 | Loopback0 Reachability | Loopback0 Reachability | Source: GW3 - 100.64.30.11 Destination: 100.64.30.12 | FAIL | 100% packet loss |
| 74 | GW3 | Loopback0 Reachability | Loopback0 Reachability | Source: GW3 - 100.64.30.11 Destination: 100.64.20.12 | FAIL | 100% packet loss |
| 75 | SPE5 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE5 - 100.64.30.12 Destination: 100.64.20.11 | FAIL | 100% packet loss |
| 76 | SPE5 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE5 - 100.64.30.12 Destination: 100.64.30.11 | FAIL | 100% packet loss |
| 78 | SPE5 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE5 - 100.64.30.12 Destination: 100.64.20.12 | FAIL | 100% packet loss |
| 79 | SPE6 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE6 - 100.64.20.12 Destination: 100.64.20.11 | FAIL | 100% packet loss |
| 80 | SPE6 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE6 - 100.64.20.12 Destination: 100.64.30.11 | FAIL | 100% packet loss |
| 81 | SPE6 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE6 - 100.64.20.12 Destination: 100.64.30.12 | FAIL | 100% packet loss |

## All Test Results

| Test ID | Node | Test Category | Test Description | Test | Test Result | Failure Reason |
| ------- | ---- | ------------- | ---------------- | ---- | ----------- | -------------- |
| 1 | GW2 | NTP | Synchronised with NTP server | NTP | PASS | - |
| 2 | GW3 | NTP | Synchronised with NTP server | NTP | PASS | - |
| 3 | SPE5 | NTP | Synchronised with NTP server | NTP | PASS | - |
| 4 | SPE6 | NTP | Synchronised with NTP server | NTP | PASS | - |
| 5 | GW2 | Interface State | Ethernet Interface Status & Line Protocol == "up" | Ethernet1 - P2P_LINK_TO_SPE6_Ethernet1 | PASS | - |
| 6 | GW3 | Interface State | Ethernet Interface Status & Line Protocol == "up" | Ethernet1 - P2P_LINK_TO_SPE5_Ethernet1 | PASS | - |
| 7 | SPE5 | Interface State | Ethernet Interface Status & Line Protocol == "up" | Ethernet1 - P2P_LINK_TO_GW3_Ethernet1 | PASS | - |
| 8 | SPE6 | Interface State | Ethernet Interface Status & Line Protocol == "up" | Ethernet1 - P2P_LINK_TO_GW2_Ethernet1 | PASS | - |
| 9 | GW2 | Interface State | Vxlan Interface Status & Line Protocol == "up" | Vxlan1 | FAIL | interface status: down - line protocol status: down |
| 10 | GW3 | Interface State | Vxlan Interface Status & Line Protocol == "up" | Vxlan1 | FAIL | interface status: down - line protocol status: down |
| 11 | SPE5 | Interface State | Vxlan Interface Status & Line Protocol == "up" | Vxlan1 | FAIL | interface status: down - line protocol status: down |
| 12 | SPE6 | Interface State | Vxlan Interface Status & Line Protocol == "up" | Vxlan1 | FAIL | interface status: down - line protocol status: down |
| 13 | GW2 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback0 - EVPN_Overlay_Peering | PASS | - |
| 14 | GW2 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback1 - VTEP_VXLAN_Tunnel_Source | PASS | - |
| 15 | GW3 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback0 - EVPN_Overlay_Peering | PASS | - |
| 16 | GW3 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback1 - VTEP_VXLAN_Tunnel_Source | PASS | - |
| 17 | SPE5 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback0 - EVPN_Overlay_Peering | PASS | - |
| 18 | SPE5 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback1 - VTEP_VXLAN_Tunnel_Source | PASS | - |
| 19 | SPE6 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback0 - EVPN_Overlay_Peering | PASS | - |
| 20 | SPE6 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback1 - VTEP_VXLAN_Tunnel_Source | PASS | - |
| 21 | GW2 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet1 - remote: SPE6_Ethernet1 | FAIL | P2-A.clearshark.net - Ethernet5 |
| 22 | GW3 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet1 - remote: SPE5_Ethernet1 | FAIL | P3-B.clearshark.net - Ethernet5 |
| 23 | SPE5 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet1 - remote: GW3_Ethernet1 | FAIL | GW3.clearshark.net - Ethernet2 |
| 24 | SPE6 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet1 - remote: GW2_Ethernet1 | FAIL | GW2.clearshark.net - Ethernet2 |
| 25 | GW2 | IP Reachability | ip reachability test p2p links | Source: GW2_Ethernet1 - Destination: SPE6_Ethernet1 | FAIL | 100% packet loss |
| 26 | GW3 | IP Reachability | ip reachability test p2p links | Source: GW3_Ethernet1 - Destination: SPE5_Ethernet1 | FAIL | 100% packet loss |
| 27 | SPE5 | IP Reachability | ip reachability test p2p links | Source: SPE5_Ethernet1 - Destination: GW3_Ethernet1 | FAIL | 100% packet loss |
| 28 | SPE6 | IP Reachability | ip reachability test p2p links | Source: SPE6_Ethernet1 - Destination: GW2_Ethernet1 | FAIL | 100% packet loss |
| 29 | GW2 | BGP | ArBGP is configured and operating | ArBGP | PASS | - |
| 30 | GW3 | BGP | ArBGP is configured and operating | ArBGP | PASS | - |
| 31 | SPE5 | BGP | ArBGP is configured and operating | ArBGP | PASS | - |
| 32 | SPE6 | BGP | ArBGP is configured and operating | ArBGP | PASS | - |
| 33 | SPE5 | BGP | bgp evpn peer state established (evpn) | bgp_neighbor: 100.64.30.11 | FAIL | Session state "Active" |
| 34 | SPE6 | BGP | bgp evpn peer state established (evpn) | bgp_neighbor: 100.64.20.11 | FAIL | Session state "Active" |
| 35 | GW2 | Routing Table | Remote VTEP address | 100.64.21.11 | PASS | - |
| 36 | GW2 | Routing Table | Remote VTEP address | 100.64.31.11 | FAIL | VTEP 100.64.31.11 is not in the routing table |
| 37 | GW2 | Routing Table | Remote VTEP address | 100.64.31.12 | FAIL | VTEP 100.64.31.12 is not in the routing table |
| 38 | GW2 | Routing Table | Remote VTEP address | 100.64.21.12 | FAIL | VTEP 100.64.21.12 is not in the routing table |
| 39 | GW3 | Routing Table | Remote VTEP address | 100.64.21.11 | FAIL | VTEP 100.64.21.11 is not in the routing table |
| 40 | GW3 | Routing Table | Remote VTEP address | 100.64.31.11 | PASS | - |
| 41 | GW3 | Routing Table | Remote VTEP address | 100.64.31.12 | FAIL | VTEP 100.64.31.12 is not in the routing table |
| 42 | GW3 | Routing Table | Remote VTEP address | 100.64.21.12 | FAIL | VTEP 100.64.21.12 is not in the routing table |
| 43 | SPE5 | Routing Table | Remote VTEP address | 100.64.21.11 | FAIL | VTEP 100.64.21.11 is not in the routing table |
| 44 | SPE5 | Routing Table | Remote VTEP address | 100.64.31.11 | FAIL | VTEP 100.64.31.11 is not in the routing table |
| 45 | SPE5 | Routing Table | Remote VTEP address | 100.64.31.12 | PASS | - |
| 46 | SPE5 | Routing Table | Remote VTEP address | 100.64.21.12 | FAIL | VTEP 100.64.21.12 is not in the routing table |
| 47 | SPE6 | Routing Table | Remote VTEP address | 100.64.21.11 | FAIL | VTEP 100.64.21.11 is not in the routing table |
| 48 | SPE6 | Routing Table | Remote VTEP address | 100.64.31.11 | FAIL | VTEP 100.64.31.11 is not in the routing table |
| 49 | SPE6 | Routing Table | Remote VTEP address | 100.64.31.12 | FAIL | VTEP 100.64.31.12 is not in the routing table |
| 50 | SPE6 | Routing Table | Remote VTEP address | 100.64.21.12 | PASS | - |
| 51 | GW2 | Routing Table | Remote Lo0 address | 100.64.20.11 | PASS | - |
| 52 | GW2 | Routing Table | Remote Lo0 address | 100.64.30.11 | FAIL | Lo0 100.64.30.11 is not in the routing table |
| 53 | GW2 | Routing Table | Remote Lo0 address | 100.64.30.12 | FAIL | Lo0 100.64.30.12 is not in the routing table |
| 54 | GW2 | Routing Table | Remote Lo0 address | 100.64.20.12 | FAIL | Lo0 100.64.20.12 is not in the routing table |
| 55 | GW3 | Routing Table | Remote Lo0 address | 100.64.20.11 | FAIL | Lo0 100.64.20.11 is not in the routing table |
| 56 | GW3 | Routing Table | Remote Lo0 address | 100.64.30.11 | PASS | - |
| 57 | GW3 | Routing Table | Remote Lo0 address | 100.64.30.12 | FAIL | Lo0 100.64.30.12 is not in the routing table |
| 58 | GW3 | Routing Table | Remote Lo0 address | 100.64.20.12 | FAIL | Lo0 100.64.20.12 is not in the routing table |
| 59 | SPE5 | Routing Table | Remote Lo0 address | 100.64.20.11 | FAIL | Lo0 100.64.20.11 is not in the routing table |
| 60 | SPE5 | Routing Table | Remote Lo0 address | 100.64.30.11 | FAIL | Lo0 100.64.30.11 is not in the routing table |
| 61 | SPE5 | Routing Table | Remote Lo0 address | 100.64.30.12 | PASS | - |
| 62 | SPE5 | Routing Table | Remote Lo0 address | 100.64.20.12 | FAIL | Lo0 100.64.20.12 is not in the routing table |
| 63 | SPE6 | Routing Table | Remote Lo0 address | 100.64.20.11 | FAIL | Lo0 100.64.20.11 is not in the routing table |
| 64 | SPE6 | Routing Table | Remote Lo0 address | 100.64.30.11 | FAIL | Lo0 100.64.30.11 is not in the routing table |
| 65 | SPE6 | Routing Table | Remote Lo0 address | 100.64.30.12 | FAIL | Lo0 100.64.30.12 is not in the routing table |
| 66 | SPE6 | Routing Table | Remote Lo0 address | 100.64.20.12 | PASS | - |
| 67 | GW2 | Loopback0 Reachability | Loopback0 Reachability | Source: GW2 - 100.64.20.11 Destination: 100.64.20.11 | PASS | - |
| 68 | GW2 | Loopback0 Reachability | Loopback0 Reachability | Source: GW2 - 100.64.20.11 Destination: 100.64.30.11 | FAIL | 100% packet loss |
| 69 | GW2 | Loopback0 Reachability | Loopback0 Reachability | Source: GW2 - 100.64.20.11 Destination: 100.64.30.12 | FAIL | 100% packet loss |
| 70 | GW2 | Loopback0 Reachability | Loopback0 Reachability | Source: GW2 - 100.64.20.11 Destination: 100.64.20.12 | FAIL | 100% packet loss |
| 71 | GW3 | Loopback0 Reachability | Loopback0 Reachability | Source: GW3 - 100.64.30.11 Destination: 100.64.20.11 | FAIL | 100% packet loss |
| 72 | GW3 | Loopback0 Reachability | Loopback0 Reachability | Source: GW3 - 100.64.30.11 Destination: 100.64.30.11 | PASS | - |
| 73 | GW3 | Loopback0 Reachability | Loopback0 Reachability | Source: GW3 - 100.64.30.11 Destination: 100.64.30.12 | FAIL | 100% packet loss |
| 74 | GW3 | Loopback0 Reachability | Loopback0 Reachability | Source: GW3 - 100.64.30.11 Destination: 100.64.20.12 | FAIL | 100% packet loss |
| 75 | SPE5 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE5 - 100.64.30.12 Destination: 100.64.20.11 | FAIL | 100% packet loss |
| 76 | SPE5 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE5 - 100.64.30.12 Destination: 100.64.30.11 | FAIL | 100% packet loss |
| 77 | SPE5 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE5 - 100.64.30.12 Destination: 100.64.30.12 | PASS | - |
| 78 | SPE5 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE5 - 100.64.30.12 Destination: 100.64.20.12 | FAIL | 100% packet loss |
| 79 | SPE6 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE6 - 100.64.20.12 Destination: 100.64.20.11 | FAIL | 100% packet loss |
| 80 | SPE6 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE6 - 100.64.20.12 Destination: 100.64.30.11 | FAIL | 100% packet loss |
| 81 | SPE6 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE6 - 100.64.20.12 Destination: 100.64.30.12 | FAIL | 100% packet loss |
| 82 | SPE6 | Loopback0 Reachability | Loopback0 Reachability | Source: SPE6 - 100.64.20.12 Destination: 100.64.20.12 | PASS | - |
