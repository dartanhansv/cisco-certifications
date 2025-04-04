# Multicast Review  

Multicast packets are sent to a **multicast group** identified by an **IP multicast address**.  

---

## Summary of Protocols  

| Protocol      | Description                                                                                       |
| ------------- | ------------------------------------------------------------------------------------------------- |
| **IGMP**      | Hosts send IGMP query messages to routers, and switches add the host to multicast group.              |
| **PIM-SM**    | Assumes no hosts want multicast traffic unless specifically requested; uses shared trees via RPs. |
| **BIDIR-PIM** | Builds bidirectional shared trees; never creates shortest-path trees.                             |
| **PIM-SSM**   | Eliminates RPs and shared trees; builds shortest-path trees (SPTs).                               |
| **MSDP**      | Interconnects multiple PIM-SM domains; RPs exchange source information.                           |

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

---

## Protocol Independent Multicast (PIM)  

### Sparse Mode (PIM-SM)  
- Uses shared trees and RPs.  
- Receivers join groups via IGMP; RP coordinates multicast group membership.  

### Dense Mode (PIM-DM)  
- Uses source trees and **Reverse Path Forwarding (RPF)**.  
- DR forwards multicast traffic and manages prune/join messages.  

### Bidirectional PIM (BIDIR-PIM)  
- Builds bidirectional shared trees; scales well for many-to-many models.  

### PIM Source-Specific Multicast (PIM-SSM)  
- Builds SPTs for known sources; recommended for broadcast applications.  

---

## Multicast Source Discovery Protocol (MSDP)  
- Connects multiple PIM-SM domains.  
- RPs exchange source information without dependency on external domains.  

---
