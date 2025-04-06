# IS-IS Overview  

IS-IS is a **link-state routing protocol** that floods link-state information to build a network topology map. Originally designed for OSI **Connectionless Network Protocol (CNLP)**, **Integrated IS-IS** extends its functionality to route IP packets (IPv4/IPv6).  

---

## Key Features  

| Feature                     | Description                                                            |
| --------------------------- | ---------------------------------------------------------------------- |
| **Protocol Type**           | Link-state protocol                                                    |
| **Communication**           | Uses OSI CNLP for router communication                                 |
| **Classless Protocol**      | Supports VLSM and CIDR                                                 |
| **Default Metric**          | Set to 10 for active interfaces                                        |
| **Administrative Distance** | 115                                                                    |
| **Updates**                 | Sends partial route updates only on network changes                    |
| **Authentication**          | Plaintext passwords (MD5 support recommended via RFC draft)            |
| **Interface Types**         | Point-to-point and broadcast                                           |
| **Metric Limitations**      | Single path metric (single link max: 64; path max: 1024)               |
| **IPv4/IPv6 Support**       | Supported as separate topologies                                       |
| **Use Case**                | Common in large ISP networks and attractive compared to OSPF and EIGRP |

---

## Comparison with OSPF  

| Aspect              | IS-IS Features                               | OSPF Features                     |
| ------------------- | -------------------------------------------- | --------------------------------- |
| **Algorithm**       | Dijkstra shortest-path tree (SPT)            | Dijkstra shortest-path tree (SPT) |
| **Update Packets**  | Link-State Packets (LSPs)                    | Link-State Advertisements (LSAs)  |
| **Area Boundaries** | Defined by links                             | Defined by routers                |
| **DR Election**     | No backup DR; highest priority/system ID tie | DR and BDR elected                |

---

## How IS-IS Works  

### Hierarchical Routing  
- **Level 1 (Intra-area routing)**: Communication between intermediate systems (ISs) within the same area.  
- **Level 2 (Inter-area routing)**: Routes between Level 1 areas, forming the inter-area backbone.  

### Area Definition  
- Boundaries are **links**, not routers.  
- IS-IS uses **Network Entity Titles (NETs)** to identify routers.  

---

## IS-IS DR Election  

| Network Type       | Behavior                                                                       |
| ------------------ | ------------------------------------------------------------------------------ |
| **Multiaccess**    | DR selected based on priority (default: 64; range: 0–127). Priority 0 = no DR. |
| **Point-to-point** | No DR elected.                                                                 |

- In multiaccess networks, adjacencies are established between all routers.  

---

## IS-IS Interface Types  

| Type               | Description                            |
| ------------------ | -------------------------------------- |
| **Point-to-point** | Direct connection between two routers. |
| **Broadcast**      | Multiple routers on a single network.  |

---

## IS-IS Authentication  

| Type                      | Description                                                |
| ------------------------- | ---------------------------------------------------------- |
| **Link Authentication**   | Requires common password for routers in the link.          |
| **Area Authentication**   | All routers in the area must have the same password.       |
| **Domain Authentication** | Only for L2 and L1/L2 routers; requires a common password. |

**Recommendation**: Use **MD5 hashing** for authentication (more secure than plaintext).  

---

## IS-IS for IPv6  

- Advertises IPv6 prefixes alongside IPv4 and OSI routes.  
- Identified via **Network Layer Protocol ID (NLPID) 142** (0x8E).  
- Supports **Multi-Topologies (RFC 5120)** for independent IPv4/IPv6 topologies within one domain.  
