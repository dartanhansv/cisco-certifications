# IS-IS Overview  

Intermediate System to Intermediate System (IS-IS) is a **link-state routing protocol** that floods link-state information to build a network topology map. Originally designed for OSI **Connectionless Network Protocol (CNLP)**, **Integrated IS-IS** extends its functionality to route IP packets (IPv4/IPv6).  

IS-IS  plays a key role in large service provider and carrier networks due to its flexibility, support for IPv4 and IPv6 via multi-topology extensions, and simplified area design compared to OSPF.

---

## 🔍 Key Features

| Feature                     | Description                                                |
| --------------------------- | ---------------------------------------------------------- |
| **Protocol Type**           | Link-state                                                 |
| **Communication**           | Uses OSI CNLP for router communication                     |
| **Classless Protocol**      | Supports VLSM and CIDR                                     |
| **Default Metric**          | 10 (on active interfaces)                                  |
| **Administrative Distance** | 115                                                        |
| **Updates**                 | Partial updates only on topology changes                   |
| **Authentication**          | Plaintext (MD5 recommended via RFC draft)                  |
| **Interface Types**         | Point-to-point and broadcast                               |
| **Metric Limitations**      | Single path metric (per-link max: 64; per-path max: 1024)  |
| **IPv4/IPv6 Support**       | Supported using separate topologies (Multi-Topology IS-IS) |
| **Use Case**                | Common in large ISP networks                               |

---

## 🔁 IS-IS vs OSPF

| Aspect              | IS-IS                                       | OSPF                             |
| ------------------- | ------------------------------------------- | -------------------------------- |
| **Algorithm**       | Dijkstra (SPT)                              | Dijkstra (SPT)                   |
| **Update Packets**  | Link-State Packets (LSPs)                   | Link-State Advertisements (LSAs) |
| **Area Boundaries** | Defined by links                            | Defined by routers               |
| **DR Election**     | No BDR; based on highest priority/system ID | DR and BDR elected               |

---

## 🛠 How IS-IS Works
### IS-IS Packet Types

- **Hello Packets**: Used to form adjacencies between routers.
- **Link-State Packets (LSPs)**: Advertise routing information and include both intra-area and inter-area routes.
- **CSNP (Complete Sequence Number PDU)**: Used to confirm receipt of LSPs.
- **PSNP (Partial Sequence Number PDU)**: Used to request specific LSPs or acknowledge received ones.


### Hierarchical Routing

- **Level 1 (Intra-area)**: Routing within an area.
- **Level 2 (Inter-area)**: Routing between areas; forms the backbone.

### Area Definition

- Boundaries are based on **links**, not routers.
- Routers are identified using **Network Entity Titles (NETs)**.

---

## 👑 Designated Router (DR) Election

| Network Type       | DR Election Behavior                                                             |
| ------------------ | -------------------------------------------------------------------------------- |
| **Multiaccess**    | DR selected based on priority (0–127; default: 64). Priority 0 disables DR role. |
| **Point-to-point** | No DR election.                                                                  |

- All routers on a multiaccess network form full adjacencies with each other.

---

## 🔌 Interface Types

| Type               | Description                            |
| ------------------ | -------------------------------------- |
| **Point-to-point** | Direct connection between two routers. |
| **Broadcast**      | Shared network with multiple routers.  |

---

## 🔐 Authentication Methods

| Scope                     | Description                                                     |
| ------------------------- | --------------------------------------------------------------- |
| **Link Authentication**   | Same password required on each side of the link.                |
| **Area Authentication**   | All routers in the same area must share the same password.      |
| **Domain Authentication** | Used by Level 2 or Level 1/2 routers across the routing domain. |

> 🔒 **Best practice**: Use **MD5 hashing** for stronger security over plaintext.

---

## 🌐 IS-IS for IPv6

- Supports IPv6 routing alongside IPv4 and OSI.
- IPv6 traffic is identified by **NLPID 142 (0x8E)**.
- Implements **Multi-Topology IS-IS (MT-ISIS)** as per **RFC 5120**, allowing separate IPv4 and IPv6 topologies.

---

### 📚 Navigation
- → Next: [IS-IS NET Addressing](isis-net-addressing.md)
- ↑ Back to: [IS-IS](../readme.md)
