# 📡 Multicast Routing: PIM, SSM, BIDIR-PIM, and MSDP

## Introduction

Multicast routing allows efficient delivery of data to multiple receivers without sending duplicate streams. Protocol Independent Multicast (PIM), along with protocols like BIDIR-PIM, PIM-SSM, and MSDP, enables scalable multicast designs across enterprise and service provider environments. 

This summary highlights the core concepts and design considerations to support high-level multicast decisions.

---

## 📢 Protocol Independent Multicast (PIM)

PIM operates in two primary modes:
- **Sparse Mode (PIM-SM)**: Uses shared trees and Rendezvous Points (RPs) to reach widely dispersed group members.
- **Dense Mode (PIM-DM)**: Uses source trees and Reverse Path Forwarding (RPF) to efficiently reach relatively close group members by flooding multicast traffic initially, and pruning unused paths later.


---

## 📢 PIM Designated Router (DR)

- In multiaccess segments running PIM, the router with the highest IP address is selected as the DR.
- The DR is responsible for sending join, prune, and register messages to the RP.

---

## 📢 Joining PIM-SM

- DRs receive IGMP membership reports from hosts wanting to join a multicast group.
- If the group is already active on another interface, the router adds the new interface to the forwarding table and periodically sends queries.
- If the group is not yet present, the router adds the interface and sends a **join** message toward the RP requesting the multicast group.

---

## 📢 Pruning PIM-SM

- When there are no more receiving hosts or routers on an interface, a **prune** message is sent toward the RP to remove the interface from the multicast group.

---

## 📢 Auto-RP

- The RP can announce its services to the PIM network through **Auto-RP** (Cisco proprietary).
- **Candidate RPs** send announcements to **RP mapping agents** using multicast address **224.0.1.39**.
- RP mapping agents select an RP based on the highest IP address among candidates and advertise RP-to-group mappings to the rest of the PIM-SM routers.

---

## 📢 Bootstrap Router (BSR)

- **BSR** is a **standards-based** alternative to Auto-RP, defined in [RFC 5059](https://datatracker.ietf.org/doc/html/rfc5059).
- It uses a **Bootstrap Router** to advertise RP information via PIM messages.
- Candidate RPs send their candidacy to the BSR, which then floods RP-set messages across the domain using address **224.0.0.13**.

---

## 📢 PIM-SM Summary

- Relies on an RP to manage multicast traffic.
- Uses a **shared tree (RPT)** for downstream traffic and **source path trees (SPTs)** for upstream traffic.
- The number of SPTs increases with the number of multicast sources, making PIM-SM less scalable for large networks.

---

## 📢 Bidirectional PIM (BIDIR-PIM)

- **BIDIR-PIM** uses a shared tree for both upstream and downstream traffic, eliminating the need for source-based SPTs.
- **Benefits**:
  - Scales efficiently without the overhead of maintaining multiple SPTs.
  - No Reverse Path Forwarding (RPF) checks required.
- **Designated Forwarder (DF)**:
  - Ensures loop-free multicast forwarding.
  - Elected per RP on each network segment based on the best unicast route (administrative distance, metric, IP address).
- **Coexistence**:
  - BIDIR-PIM and traditional PIM-SM can be used together in the same PIM domain using shared RPs.

---

## 📢 PIM Source-Specific Multicast (PIM-SSM)

- Defined in **RFC 3569**, PIM-SSM creates trees directly between receivers and a known source.
- **No RP or shared tree is used**—only (S,G) joins.
  - Trees are created based on group membership reports requesting a particular source.
- **Best for**:
  - Applications with well-known sources.
  - Streaming or Broadcast-like applications within the local PIM domain.

---

## 📢 Multicast Source Discovery Protocol (MSDP)

- Defined in **RFC 3618**.
- **Purpose**: Interconnects multiple PIM-SM domains by enabling RPs to exchange source information.
- Each domain has its own RP.
- When an RP learns of a new sender, it creates a **Source-Active (SA)** message containing:
  - Source IP address
  - Multicast Group address
  - RP IP address
- SA messages are forwarded between MSDP peers via **peer-RPF flooding**, ensuring information moves away from the source RP.

---

# 🗺️ Quick Visual: Multicast Tree Types

```plaintext
+--------------------------+
|    Multicast Tree Types  |
+--------------------------+

1. PIM-SM
   [Source] -> [RP] -> [Receivers]
   (Shared tree initially, switches to Source Trees for optimization)

2. BIDIR-PIM
   [Source] <-> [RP] <-> [Receivers]
   (Always uses a shared tree, no SPT, scalable)

3. PIM-SSM
   [Source] -> [Receivers]
   (Direct, source-specific; no RP involved)
```

---

### 📚 Navigation
- ↑ Back to: [Multicast](./multicast-overview.md)
