# 🔄 Graceful Restart (GR), NSF, and NSR

Graceful Restart (GR) is a **high-availability mechanism** that allows routing peers to **maintain forwarding state** during control plane disruptions, such as **routing process restarts or supervisor failovers**. By preserving existing routes, GR ensures **traffic continuity** while control plane adjacencies are re-established.

NSF (Non-Stop Forwarding) and NSR (Non-Stop Routing) complement GR by **preserving data and control plane operations**, reducing reconvergence delays.


## 🎯 Purpose and Benefits

- **Minimizes traffic disruption** – Forwarding continues while the router reboots.  
- **Speeds up reconvergence** – Routing peers maintain sessions without losing learned topology.  
- **Enhances reliability** – Often deployed alongside **NSF** or **NSR** to provide comprehensive high availability.  


## 🔍 How Graceful Restart Works

1. **GR-Capable Router Signals a Restart** – Neighboring routers are informed that the device is undergoing **a graceful restart**.  
2. **GR-Aware Neighbors Retain Forwarding State** –  
   - Maintain routing adjacencies **without resetting sessions**.  
   - Keep forwarding traffic based on **previously known routes**.  
3. **Recovery Phase Begins** –  
   - The restarting router **re-learns routing topology** from peers.  
   - Adjacencies are **re-synchronized** without impacting active traffic.  

⏱️ **Grace Period**: A configurable timer defining **how long neighbors maintain forwarding state** while waiting for the restarting router to recover.  
- If the **grace period expires before reconvergence**, routing sessions may be **reset**, leading to **full topology recalculation**.


## 🚨 Failure Handling Mechanism

When GR fails, routers **must detect failure and trigger full reconvergence**:
- **Missed adjacencies** – If neighbors fail to reestablish adjacencies within the grace period, all stale routes are **purged**.  
- **Fallback to standard reconvergence** – Routing protocols perform **full path recalculations** based on fresh updates.  
- **Traffic impact** – Data forwarding **may temporarily drop** if GR-dependent reconvergence is delayed.  


## 🤝 Protocol Support

| Protocol | GR Support          | NSF Integration |
| -------- | ------------------- | --------------- |
| OSPF     | ✅ RFC 3623          | Yes             |
| BGP      | ✅ RFC 4724          | Yes             |
| IS-IS    | ✅ RFC 5306          | Yes             |
| EIGRP    | ✅ Cisco proprietary | Yes             |

> **NSF and GR complement each other** – GR maintains control plane adjacencies, while **NSF ensures uninterrupted data forwarding**.


## 🔄 NSF and NSR Overview

### **Non-Stop Forwarding (NSF)**
NSF ensures **data plane continuity** during control plane failures, allowing routers to **continue forwarding packets** even while routing processes are restarted.  
- **Requires neighbor support** for graceful restart.  
- **Does not preserve routing adjacencies**—routing tables must be rebuilt post-recovery.  
- Works in tandem with **Graceful Restart (GR)** to minimize service disruption.

### **Non-Stop Routing (NSR)**
NSR provides **control plane redundancy** by synchronizing routing states between **active and standby route processors**.  
- **No dependency on neighbors**—adjacencies remain **fully intact** during failovers.  
- **More reliable than NSF**, as it maintains full routing information internally.  
- Frequently used in **IOS XR and other high-availability platforms**.

> **Key Difference**: NSF relies on **peer cooperation** to preserve traffic forwarding, while NSR maintains **internal routing state** without neighbor dependency.


## 🔄 NSR vs. NSF Comparison

| Feature                         | **NSF (Non-Stop Forwarding)**                                 | **NSR (Non-Stop Routing)**                                      |
|----------------------------------|------------------------------------------------------------------|------------------------------------------------------------------|
| **Neighbor Support Needed?**     | Yes (must support graceful restart)                             | No (self-contained, no peer dependency)                          |
| **Control Plane Dependency**     | Restarted and rebuilt during SSO (with help from neighbor)     | Continuously maintained via sync between active/standby RPs      |
| **Data Plane Disruption**        | Minimal (forwarding continues during RP failover)              | Minimal (like NSF)                                               |
| **Routing Protocol Impact**      | Peers must assist in reestablishing adjacencies                | Adjacencies are preserved internally                             |
| **IS-IS Support**                | Supported, but needs graceful restart support on neighbor      | Supported natively, no neighbor dependency                       |
| **OSPF Support**                 | Supported (RFC 3623), needs neighbor cooperation               | Supported, no neighbor dependency                                |
| **BGP Support**                  | Supported (RFC 4724), needs peer cooperation                   | Supported, often in platforms like IOS XR                        |
| **Use Case**                     | Multivendor environments where graceful restart is supported   | Environments where peer support is not guaranteed                |
| **Config Complexity**            | Moderate (requires checking peer support, timers, capabilities)| Lower (mostly internal setup)                                    |
| **Best Fit for This Scenario**   | Not ideal (upstream doesn’t support GR)                        | Best choice (solves the issue internally)                        |


## 🧠 Design Considerations

- **Both peers must support GR** – Symmetric implementation is required for successful operation.  
- **Grace period consistency** – Timers should be **uniform across devices** to prevent premature session drops.  
- **State refresh mechanisms** – Routers must support **topology updates** after control plane recovery.  
- **Interoperability concerns** – GR support **varies across different vendors**, requiring careful validation.  


## 🚫 Limitations

- **No awareness of topology changes during restart** – Stale routes may persist until full routing updates occur.  
- **Not a substitute for true high availability** – GR ensures short-term continuity but **does not replace ISSU or clustering**.  
- **May delay reconvergence in unstable networks** – If too many routers depend on GR, topology recovery can **slow down**.  

