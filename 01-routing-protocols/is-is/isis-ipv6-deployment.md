# IS-IS IPv6 Deployment: Single vs. Multi-Topology and the Transition Feature


When deploying IPv6 in an existing IS-IS network, it's critical to choose how IPv6 routes will be handled alongside IPv4. IS-IS offers both **single-topology** and **multi-topology** options, each suited for specific deployment scenarios. Additionally, the **transition feature** allows gradual migration without service disruption.


---

## IS-IS Single vs. Multi-Topology

### **1. Single-Topology IS-IS**
- **IPv4 and IPv6 share the same topology.**
- All IS-IS routers must support both IPv4 and IPv6.
- IPv6 routes follow the same IS-IS paths as IPv4.
- Uses **a single IS-IS Link-State Database (LSDB)**.
- More efficient, but requires **full IPv6 support** on all routers.

#### **When to Use Single-Topology IS-IS**
✅ When all routers in the IS-IS domain support both IPv4 and IPv6.  
✅ When IPv6 is expected to follow the same topology as IPv4.  
✅ When minimizing overhead is a priority.

### **2. Multi-Topology IS-IS**
- **IPv4 and IPv6 have separate IS-IS topologies.**
- Some routers may run only IPv4 or only IPv6.
- IS-IS maintains **separate LSDBs** for IPv4 and IPv6.
- IPv4 and IPv6 routes can follow different paths.
- Requires more resources but allows for flexibility during migration.

#### **When to Use Multi-Topology IS-IS**
✅ When IPv6 deployment is **incomplete**, and some routers do not support IPv6.  
✅ When IPv4 and IPv6 require different **routing policies** or topologies.  
✅ When transitioning from an IPv4-only network to an IPv6-enabled one **without impacting IPv4 routing**.

---

## The Transition Feature in IS-IS

The **transition feature** is used **only in single-topology IS-IS** to ensure a smooth migration from IPv4 to dual-stack (IPv4/IPv6). It helps prevent issues when some routers in the network **do not yet support IPv6**.

### **How the Transition Feature Works**
- Allows IS-IS to **advertise IPv6 reachability** in a single-topology design.
- Prevents routers that **do not support IPv6** from black-holing IPv6 traffic.
- Ensures backward compatibility during incremental IPv6 deployment.
- Once all routers support IPv6, the transition feature is no longer needed.

#### **When to Use the Transition Feature**
✅ When migrating from an **IPv4-only single-topology IS-IS** network to dual-stack.  
✅ When **some routers do not yet support IPv6**, but you want a unified topology.  
✅ To avoid breaking IPv4 routing during IPv6 deployment.  

#### **When NOT to Use the Transition Feature**
❌ If **all routers already support IPv6**—it is unnecessary.  
❌ If using **multi-topology IS-IS**, since IPv4 and IPv6 are already separated.  
❌ If the goal is to move from **single-topology to multi-topology**—this feature is unrelated.

---

## Summary

| Feature             | Single-Topology              | Multi-Topology               |
| ------------------- | ---------------------------- | ---------------------------- |
| LSDB Count          | One                          | Two                          |
| Dual-stack Required | Yes                          | No                           |
| Path Consistency    | Shared between IPv4 and IPv6 | Independent                  |
| Transition Support  | Required during migration    | Not applicable               |
| Use Case            | Homogeneous IPv6 support     | Staged/mixed IPv6 deployment |

---

## Conclusion
- **Single-topology IS-IS** is more efficient but requires all routers to support IPv6.
- **Multi-topology IS-IS** allows independent IPv4 and IPv6 topologies and is useful for incremental deployments.
- **The transition feature** is only relevant in single-topology IS-IS when IPv6 is being gradually introduced and some routers do not yet support it.

### 📚 Navigation
- → Next: [IS-IS Design](isis-design.md)  
- ← Previous: [IS-IS NET Addressing](isis-net-addressing.md)  
- ↑ Back to: [IS-IS](./readme.md)
