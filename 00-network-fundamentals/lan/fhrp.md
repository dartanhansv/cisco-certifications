# First Hop Redundancy Protocols (FHRPs)

FHRPs ensure network communication continues seamlessly when the primary default gateway fails. They allow multiple routers to share a virtual IP address, with one active and others on standby for failover.

---

### 🧠 Key Concepts
- **Redundancy**: Ensures a backup router is available if the primary fails.
- **Virtual IP Address**: Shared among routers and used by hosts as the default gateway.
- **Failover**: A standby router automatically takes over when the active fails.
- **Transparency**: End-users typically remain unaware of gateway changes.

---

### 🔁 Protocol Comparison

| Feature              | HSRP                   | VRRP                     | GLBP                   |
| -------------------- | ---------------------- | ------------------------ | ---------------------- |
| **Type**             | Cisco proprietary      | Open standard (RFC 3768) | Cisco proprietary      |
| **Redundancy**       | ✅                      | ✅                        | ✅                      |
| **Load Balancing**   | ❌                      | ❌                        | ✅ (via multiple AVFs)  |
| **Default Timers**   | Hello: 3s<br>Hold: 10s | Hello: 1s<br>Hold: 3s    | Hello: 3s<br>Hold: 10s |
| **Preemption**       | Supported (default: ❌) | Supported (default: ✅)   | ✅                      |
| **Authentication**   | ✅                      | ❌                        | ✅                      |
| **Tracking Support** | ✅ Built-in             | ❌ External required      | ✅                      |

---

### 🧩 Protocol Overviews

#### 🛡️ HSRP (Hot Standby Router Protocol)
- Creates a virtual router with shared IP & MAC.
- One router is active, others are on standby.
- Supports 4095 groups (HSRPv2).
- Built-in interface tracking.
- Use preemption to optimize STP alignment.

```bash
standby 10 track Ethernet0/0 20
```

#### 🌐 VRRP (Virtual Router Redundancy Protocol)
- Similar operation to HSRP.
- Open standard (RFC 3768).
- Preemption enabled by default.
- No built-in interface tracking.

#### ⚖️ GLBP (Gateway Load Balancing Protocol)
- All routers in a group can forward traffic.
- Elects one Active Virtual Gateway (AVG) and multiple Active Virtual Forwarders (AVFs).
- Provides automatic load sharing.

---

### 🧭 Deployment Considerations

- **Layer 2 Access Layer**:
  - Distribution switches act as default gateways.
  - FHRPs are required (HSRP, VRRP, or GLBP).

- **Layer 3 Routed Access**:
  - Access switches act as gateways.
  - FHRPs not needed.

- **VSS/StackWise Virtual**:
  - Eliminates need for FHRPs.
  - Default gateway redundancy is built into the platform.

---

### ⚙️ Preemption & Failover
- Ensure preemption delay is longer than switch boot time.
- Avoid preemption before full routing connectivity to the core is restored.
- Misconfigured preemption timing may lead to dropped client traffic.

---

### 📚 Navigation
- [Next: Platform Abstraction Techniques](platform-abstraction-techniques.md)  
- [Back to Folder Overview](../../02-enterprise-campus/readme.md)  
- [Previous: —]
