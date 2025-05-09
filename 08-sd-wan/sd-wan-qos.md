# 🎯 QoS and Multicast in Cisco SD-WAN

Cisco’s SD-WAN solution includes several QoS features for advanced traffic prioritization and real-time path selection, along with limited multicast support for efficient content distribution.

## ⚙️ QoS Features in SD-WAN
- **Bidirectional Forwarding Detection (BFD)**
- **Application-aware Routing**
- **Interface Queuing with Low-Latency Queueing (LLQ)**

### 🛰️ Bidirectional Forwarding Detection (BFD)

WAN edge routers use **BFD** to probe and measure transport link performance. It provides real-time metrics such as:

- **Latency**
- **Jitter**
- **Loss**

BFD runs inside IPsec tunnels and operates in echo mode. It is automatically enabled when tunnels are established and cannot be disabled.

**Key Functions:**

- Subsecond failure detection on transport links  
- Helps determine path liveliness and quality  
- Gathers data on interface status and IPsec MTU  

---
### 📡 Application-Aware Routing

**Application-aware routing** selects the best path for traffic based on:

- Application identification  
- Real-time SLA metrics from BFD  
- Policy-based rules and thresholds

When SLA thresholds (like latency, jitter, or loss) are exceeded, traffic is automatically redirected to an alternate path that meets performance expectations.

---

### 🧃 Interface Queuing with LLQ

QoS policies on vEdge interfaces support:

- **Class-based queuing** to prioritize traffic types
- **Low-Latency Queuing (LLQ)** for real-time applications like voice and video
- Traffic shaping and policing mechanisms
- DSCP remarking to ensure consistent treatment across the WAN

---

## 📡 Multicast over SD-WAN
Cisco SD-WAN supports **Protocol Independent Multicast - Sparse Mode (PIM-SM)** for delivering one-to-many content like video or software updates.

### 🔁 How It Works

- The **ingress router** (connected to the multicast source) forwards streams to a **replicator vEdge**.
- The replicator vEdge then sends copies of the multicast traffic to all interested receivers.
- **vEdge routers support IGMPv2** to track receiver memberships within specific VPNs.

> **Note**: The PIM Rendezvous Point (RP) function is **not supported** on vEdge devices. Instead, RP must reside on local-site PIM routers. Auto-RP is supported for RP-to-group mapping.

> **Note**: The PIM Rendezvous Point (RP) function is **not supported** on vEdge devices. Instead, RP must reside on local-site PIM routers. Auto-RP is supported for RP-to-group mapping.
---

### 📚 Navigation
- ← Previous: [Direct Internet Access and Security](./sd-wan-dia-security.md)
- ↩ Return to [Cisco SD-WAN](./README.md)