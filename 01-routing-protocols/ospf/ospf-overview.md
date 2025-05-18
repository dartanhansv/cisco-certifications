# OSPF Overview

## What is OSPF?
Open Shortest Path First (OSPF) is a **link-state routing protocol** that uses **Dijkstra's Shortest-Path First (SPF) algorithm** to calculate the best paths to destinations. It is widely used in enterprise and service provider networks due to its **scalability, fast convergence, and support for hierarchical design**.

## Why OSPF?
Compared to older protocols like RIP (Routing Information Protocol), OSPF offers significant improvements:
- **Faster convergence**: Quickly adapts to network topology changes.
- **Classless routing**: Supports Variable-Length Subnet Masking (VLSM) for efficient IP allocation.
- **Hierarchical design**: Allows network segmentation into areas to improve scalability.
- **More efficient routing updates**: Uses **Link-State Advertisements (LSAs)** instead of full routing table exchanges.

## OSPF Versions
### OSPFv2
- Designed for **IPv4 networks**.
- Uses **224.0.0.5** (All OSPF Routers) and **224.0.0.6** (All DR/BDR Routers) multicast addresses.

### OSPFv3
- Initially created for **IPv6** but later extended to support **both IPv4 and IPv6**.
- Adds support for:
  - IPv6 addressing.
  - IPv6 as a transport for OSPF messages.
  - Improved authentication and security mechanisms.
  - **Interface-based configuration** instead of network statements, making IPv6 deployments more flexible.


## How OSPF Works
1. **Neighbor Discovery**: OSPF routers discover each other using **Hello packets**.
2. **Adjacency Formation**: After two routers establish bidirectional communication, they form adjacencies.
3. **Database Synchronization**: Routers exchange [Link-State Advertisements (LSAs)](./ospf-lsa-types.md) to build a **Link-State Database (LSDB)**.
4. **SPF Calculation**: Each router independently runs the **SPF algorithm** to determine the best path to each destination.
5. **Routing Table Update**: The best paths are installed in the **Routing Information Base (RIB)**.

## Basic OSPF Configuration
Below is an example of enabling OSPF on a router:

```bash
router ospf 1
 network 192.168.1.0 0.0.0.255 area 0
```

- `1` is the OSPF process ID (locally significant).
- `network 192.168.1.0 0.0.0.255 area 0` associates the network with OSPF **area 0** (Backbone Area).

---
### 📚 Navigation
- → Next: [OSPF Adjacency](./ospf-adjacency.md)
- ↩ Return to [OSPF](./README.md)
