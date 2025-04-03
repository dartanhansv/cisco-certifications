# OSPFv3 Overview 


OSPFv3 was initially designed to support **IPv6 networks**, with **IPv4 support** later added through **Address Families**. It uses **IPv6 for transport** regardless of the IP version being routed, making it more versatile than OSPFv2.

Additionally, OSPFv3 integrates **IPsec for authentication and security**, replacing the native authentication methods of OSPFv2.  

---

## Changes from OSPFv2 to OSPFv3  
- **IPv6 for transport**:  
  OSPFv3 uses IPv6 as the transport layer, even when routing IPv4 prefixes.  
- **IPv6 addressing support**:  
  New LSAs handle IPv6 prefixes and addressing.  
- **Per-link processing**:  
  - OSPFv3 processes per link instead of per subnet like OSPFv2.  
  - Routers on the same link can belong to multiple subnets.  
- **No native authentication**:  
  OSPFv3 uses **IPsec** for authentication and security.  
- **Router ID-based neighbors**:  
  - Neighbors are identified by **Router ID**, even in point-to-point and broadcast networks.  
  - Note: Router IDs, Area IDs, and LSA IDs remain 32 bits long in OSPFv3.  

---

## What Remains the Same  
Core OSPF concepts and mechanisms are unchanged:  
- SPF calculations (using **Dijkstra's Algorithm**)  
- Router types (Backbone, Internal, ABR, ASBR)  
- DR/BDR elections  
- Areas and topology structure  
- Link-State Database  

---

## OSPFv3 Areas  
- Areas are the same as in OSPFv2. Refer to [ospf-area-types.md](ospf-area-types.md).  

---

## OSPFv3 Router Types  
- **Backbone Router**:  
  - Has at least one interface in **Area 0**.  
- **Internal Router**:  
  - All interfaces are connected to a single area.  
  - Maintains one Link-State Database.  
- **ABR** (Area Border Router):  
  - Connected to multiple areas, including **Area 0**.  
  - Maintains a separate Link-State Database for each area.  
  - Generates **Summary LSAs**.  
- **ASBR** (Autonomous System Boundary Router):  
  - Redistributes external routes (static or from other protocols like EIGRP, RIP, or BGP).  

---

## OSPFv3 LSAs  
Two new LSAs added:  
- **Link LSA**:  
  - Advertises link-local addresses and IPv6 prefixes associated with the link.  
- **Intra-Area Prefix LSA**:  
  - Specifies prefixes for routers, stub networks, or transit network segments.  

---

## Important Notes  
- SPF calculation still uses **Dijkstra’s Algorithm**.  
- Administrative distance: **110**.  
- Multicast addresses:  
  - **FF02::5** (ALLSPFRouters).  
  - **FF02::6** (ALLDRouters).  

---
