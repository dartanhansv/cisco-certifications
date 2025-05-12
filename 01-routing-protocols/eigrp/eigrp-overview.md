# Enhanced Interior Gateway Routing Protocol (EIGRP)

**Enhanced Interior Gateway Routing Protocol (EIGRP)** is an advanced distance-vector routing protocol that integrates elements of both **distance-vector** and **link-state** models. It is known for its **rapid convergence**, **efficient bandwidth utilization**, and **scalability**—making it well-suited for large enterprise networks.

EIGRP achieves its fast convergence through the **Diffusing Update Algorithm (DUAL)**, which enables real-time route recalculations without relying on periodic updates. It supports both **IPv4 and IPv6**, offers **multiprotocol capabilities**, and provides flexible **route summarization and traffic engineering** features.

> ⚠️ **Important Note for Certification**  
> Although EIGRP is sometimes referenced as an open-standard protocol, I **personally treat it as Cisco proprietary** in certification exams, based on the following facts:  
> - **Limited RFC Implementation**: The informational RFC released by Cisco in 2013 lacks core technical details, making interoperability with third-party vendors impractical.  
> - **Cisco's Official Cert Guide (OCG)**: The ENSLD OCG explicitly refers to EIGRP as a Cisco-proprietary protocol.  





## ✅ Protocol Overview

| Feature                      | Details                                                         |
| ---------------------------- | --------------------------------------------------------------- |
| Protocol Type                | Hybrid (Distance-vector with link-state characteristics)        |
| IP Protocol Number           | 88                                                              |
| Addressing                   | Multicast: 224.0.0.10 (IPv4), FF02::A (IPv6)                    |
| VLSM Support                 | Yes, classless protocol                                         |
| Default Metric               | Bandwidth and Delay                                             |
| Optional Metrics             | Load and Reliability (enabled via `metric weights`)             |
| Metric Formula               | Composite metric based on K-values                              |
| Load Balancing               | Equal-cost (default); unequal-cost with `variance`              |
| Update Behavior              | Partial updates when topology changes; no periodic full updates |
| Convergence                  | Fast, loop-free via DUAL                                        |
| Authentication               | Supports MD5                                                    |
| Administrative Distance (AD) | 90 (internal), 170 (external), 5 (summary)                      |
| Scalability                  | High; supports large enterprise networks                        |
| Topology Requirements        | No hierarchical topology required                               |



## 🧠 Key Components

- **Protocol-Dependent Modules (PDMs)** handle multiple protocols (e.g., IPX, AppleTalk).
- **Neighbor Discovery** uses Hello packets to establish adjacency and maintain relationships.
- **Reliable Transport Protocol (RTP)** ensures reliable, ordered delivery of routing messages.
- **DUAL Algorithm** selects loop-free best and backup paths using FD, RD, and feasibility condition.



## 📘 Terminology Summary

| Term                   | Description                                   |
| ---------------------- | --------------------------------------------- |
| Successor              | Best next-hop for destination (lowest metric) |
| Feasible Successor     | Backup path; satisfies feasibility condition  |
| Feasible Distance (FD) | Metric from the local router to destination   |
| Reported Distance (RD) | Metric reported by the neighbor router        |
| Feasibility Condition  | RD < FD                                       |



## 🔄 Route States

- **Passive**: Stable state with known successors.
- **Active**: Route being recomputed—query process initiated.
- **Stuck-in-Active (SIA)**: No replies within 3 mins → neighbor reset.



## 📦 EIGRP Packet Types

| Type   | Purpose                                                            |
| ------ | ------------------------------------------------------------------ |
| Hello  | Neighbor discovery; multicast; sent every 5s (or 60s on slow WANs) |
| Ack    | Unicast hello with no data; confirms update receipt                |
| Update | Routing info; multicast or unicast; acknowledged via Ack           |
| Query  | Multicast; asks neighbors for alternate paths                      |
| Reply  | Unicast; response to Query with feasible path info                 |



## ⏱️ Timers

| Link Type            | Hello / Hold Time |
| -------------------- | ----------------- |
| High-speed (LAN)     | 5s / 15s          |
| Low-speed (WAN ≤ T1) | 60s / 180s        |



## 🔒 Authentication

- MD5 authentication supported.
- Must match key ID and key-string across neighbors.



## 📊 Metrics

**Formula**:

```
Metric = {k1 × BW + [(k2 × BW)/(256 − load)] + k3 × delay} × {k5/(reliability + k4)}
```

- BW = Lowest bandwidth along path (kbps)
- Delay = Sum of interface delays (in 10 µs units)
- Reliability and Load = Dynamic values (1 to 255); not used unless enabled via `metric weights`

**Defaults**: `k1 = 1`, `k3 = 1`; all others = 0.

Use:
```bash
router eigrp [ASN]
 metric weights 0 1 1 1 1 1
```



## ⚖️ Variance

| Variance | Metric Threshold | Feasible Successors Included                |
| -------- | ---------------- | ------------------------------------------- |
| 2        | ≤ 2x successor   | Routes with metric ≤ 20 (if successor = 10) |
| 3        | ≤ 3x successor   | Routes with metrics ≤ 30                    |
| 6        | ≤ 6x successor   | Routes with metric ≤ 60                     |

---
## 📚 Navigation
- → Next: [EIGRP Design Considerations](eigrp-design.md)  
- ↑ Back to: [Routing Protocols](../readme.md)
