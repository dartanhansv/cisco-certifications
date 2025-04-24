# Hierarchical Network Model

The **Cisco Hierarchical Network Model** is a well-established framework for designing enterprise LANs in a scalable, modular, and manageable way.

The model is divided into three layers:

## Core Layer
- Designed for **high-speed, reliable transport** of data across the backbone.
- Optimized for **performance and availability**.
- Avoids complex services (e.g., ACLs, NAT, QoS marking) to minimize latency and improve convergence time.
- Redundancy and load balancing are critical.

## Distribution Layer
- Serves as an **aggregation point** for access switches.
- Performs **policy enforcement**, **routing between VLANs**, **QoS**, and **security**.
  - e.g., forward traffic out to different interfaces based on the policy rather than the routing table.
- Redundancy and load balancing are often implemented here.
- Connects to other distribution blocks, data centers, or WAN edges.
- Handles media translations (e.g., Ethernet to Token Ring).
- Performs redistribution between routing domains (e.g., different routing protocols).
- Acts as a **demarcation point** between:
  - Layer 2 and Layer 3 segments
  - Static and dynamic routing protocols
- Enables address or area aggregation/summarization:
  - **Summarization of end-user networks toward the core layer to reduce routing table size and isolate network issues**
  - **Advertisement of default or service routes toward the access layer (e.g., internet-bound traffic)**

## Access Layer
- Provides **endpoint connectivity** for users and devices.
- Focused on **port security**, **user authentication**, and **basic Layer 2 forwarding**.
- Switches here often connect to phones, printers, and user workstations.
- Implements **network access control** (e.g., 802.1X).
- Supports features like **voice VLANs**, **PoE**, and **port-based ACLs**.
- **Spanning Tree Protocol (STP)** and enhancements (e.g., **PortFast**, **BPDU Guard**) are typically configured here to prevent loops and improve convergence.


---

## Characteristics Summary

| Layer        | Key Function               | Typical Devices              |
| ------------ | -------------------------- | ---------------------------- |
| Core         | High-speed forwarding      | Core switches (e.g. C9500)   |
| Distribution | Policy, routing, filtering | Layer 3 switches             |
| Access       | Endpoint connectivity      | Access switches (e.g. C9300) |

---

## Design Principles

- Use **redundancy** in the core and distribution layers.
- Implement **layered modularity** for easier troubleshooting and scaling.
- Prefer **Layer 3 routing** between distribution and core layers.
- Keep the core layer **simple and fast**.

---

## Benefits

- **Scalability**: Easily expand the network by adding new access switches.
- **Performance**: Traffic is segmented and optimized.
- **Resilience**: Redundancy and modularity help with fault isolation.
- **Manageability**: Clear separation of responsibilities among layers.

---

## Related Concepts

- The **Three-Tier Campus Network** is the physical implementation of this model.
- In **smaller environments**, the **Collapsed Core** design may merge core and distribution layers into a single layer.

---

**Reference:**
- CCNP Enterprise Design ENSLD 300-420 Official Cert Guide, Chapter 6
