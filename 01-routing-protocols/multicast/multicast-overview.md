# Multicast Review

Multicast packets are sent to a **multicast group** identified by an **IP multicast address**.

---

## Summary of Protocols

| Protocol      | Description                                                                                       |
| ------------- | ------------------------------------------------------------------------------------------------- |
| **IGMP**      | Hosts send IGMP query messages to routers, and switches add the host to multicast group.          |
| **PIM-SM**    | Assumes no hosts want multicast traffic unless specifically requested; uses shared trees via RPs. |
| **BIDIR-PIM** | Builds bidirectional shared trees; never creates shortest-path trees.                             |
| **PIM-SSM**   | Eliminates RPs and shared trees; builds shortest-path trees (SPTs).                               |
| **MSDP**      | Interconnects multiple PIM-SM domains; RPs exchange source information.                           |

---

## Multicast

### IGMP
**Internet Group Management Protocol**  
- IGMP is a protocol that helps devices and routers manage multicast groups.
- Hosts use IGMP to tell routers which multicast groups they belong to.
- IGMP operates only within the local subnet; IGMP messages are not routed between networks.
- There are three versions:
  - **IGMPv1** (RFC 1112): Basic membership queries and reports.
  - **IGMPv2** (RFC 2236): Faster leave mechanisms and group-specific queries.
  - **IGMPv3** (RFC 3376): Adds Source-Specific Multicast (SSM) capabilities.

---

## Multicast Addresses

### IPv4 Multicast
| Address Range    | Description                 |
| ---------------- | --------------------------- |
| **224.0.0.0/24** | Local network control block |
| **224.0.0.1**    | All hosts on the subnet     |
| **224.0.0.2**    | All multicast routers       |
| **224.0.0.5**    | All OSPF routers            |
| **224.0.0.6**    | All OSPF DR routers         |
| **224.0.0.10**   | EIGRP routers               |

### IPv6 Multicast
| Address     | Description              |
| ----------- | ------------------------ |
| **FF01::1** | All nodes (node-local)   |
| **FF02::1** | All nodes (link-local)   |
| **FF02::2** | All routers (link-local) |
| **FF02::5** | OSPFv3 routers           |
| **FF02::A** | EIGRP routers            |

**Note**: These protocol summaries and multicast addresses form the essential knowledge required for exams covering multicast.

---

## Layer 3 to Layer 2 Mapping

Multicast MAC addresses map to the reserved IEEE **0100.5e00** range.
- Lower 23 bits of the MAC address correspond to lower 23 bits of the IP address.
- Example: IP `224.0.0.2` maps to MAC `0100.5e00.0002`.

---

## IGMP Versions

| Version    | Key Features                                                                | Compatibility       |
| ---------- | --------------------------------------------------------------------------- | ------------------- |
| **IGMPv1** | Membership query and report. Slow group termination due to query intervals. | Legacy systems      |
| **IGMPv2** | Faster group termination with leave messages.                               | Backward-compatible |
| **IGMPv3** | Supports Source-Specific Multicast (SSM). Backward-compatible with v1/v2.   | Modern networks     |

---

## Sparse vs Dense Mode

| Mode       | Characteristics                                     |
| ---------- | --------------------------------------------------- |
| **Sparse** | Widely dispersed receivers; bandwidth limited.      |
| **Dense**  | Densely distributed receivers; bandwidth plentiful. |

---

## Multicast Distribution Trees

| Type            | Key Features                                                           |
| --------------- | ---------------------------------------------------------------------- |
| **Source Tree** | Roots at source; creates shortest-path trees (SPTs); memory intensive. |
| **Shared Tree** | Roots at RP; reduces memory load; paths may be suboptimal initially.   |

### Source Trees
- Rooted at the source of the multicast group, expanding directly through the network to destination hosts.
- Also known as **Shortest-Path Trees (SPTs)**.
- Drawback: Routers must consume memory resources to maintain a list of all multicast groups.

### Shared Trees
- Rooted at a **Rendezvous Point (RP)** located between the sources and receivers.
- Advantage: Reduces memory requirements for routers by centralizing traffic through an RP.
- Drawback: Initial multicast traffic may take suboptimal paths until the network optimizes them.

---

# Reverse Path Forwarding (RPF)

**Reverse Path Forwarding (RPF)** ensures that multicast traffic follows the optimal path back toward the source, preventing loops and maintaining efficient delivery.

When a multicast router receives a multicast packet, it performs an **RPF check**, verifying whether the packet arrived on the interface the router would use to send unicast traffic back to the source of the multicast stream.

- If the check **passes**, the router forwards the packet.  
- If the check **fails**, the router drops the packet to prevent routing loops.  

Additionally, if no group members are present on any attached or downstream subnets, the router sends a **prune message upstream** to stop receiving the multicast stream. This mechanism ensures **loop-free multicast forwarding trees** and optimizes bandwidth usage.


---

## Rendezvous Points (RPs)

- **Role**:  
  RPs act as central points in multicast networks where multicast sources initially send their packets. These packets are then forwarded to multicast group members.
- **Shared Trees**:  
  RPs are used to create shared trees that optimize resource usage by centralizing multicast traffic.
- **Auto-RP**:  
  - Candidate RPs announce their availability through Auto-RP.
  - RP mapping agents select one RP, often based on the highest IP address among candidates.
- **Optimization**:  
  Although multicast packets initially may not take optimal paths, the network dynamically optimizes paths over time to improve efficiency.

---

## Protocol Independent Multicast (PIM)

### Sparse Mode (PIM-SM)
- Uses shared trees rooted at RPs.
- Receivers join multicast groups via IGMP; RP coordinates group membership and traffic distribution.

### Dense Mode (PIM-DM)
- Uses source-based trees and **Reverse Path Forwarding (RPF)** checks.
- DRs (Designated Routers) forward multicast traffic and manage prune/join signaling.

### Bidirectional PIM (BIDIR-PIM)
- Builds bidirectional shared trees.
- Scales well for environments with many multicast sources and many receivers.

### PIM Source-Specific Multicast (PIM-SSM)
- Builds shortest-path trees (SPTs) directly from receivers to known sources.
- Eliminates the need for RPs.
- Ideal for applications like broadcast video where the source is known.

---

## Multicast Source Discovery Protocol (MSDP)

- Connects multiple PIM-SM domains.
- Allows RPs in different domains to exchange multicast source information without depending on external systems.

---
### 📚 Navigation
- → Next: [Multicast PIM](pim.md)  
- ↑ Back to: [Routing Protocols](../readme.md)
