# 📡 Multicast in Cisco SD-WAN

Multicast plays a critical role in **efficient content distribution** over SD-WAN networks, enabling optimized **video streaming, software distribution**, and other **one-to-many transmissions**. Cisco SD-WAN supports multicast forwarding through **Protocol Independent Multicast - Sparse Mode (PIM-SM)** while leveraging **WAN replication techniques** to minimize bandwidth consumption.



## 🔗 Multicast Support in SD-WAN
Cisco SD-WAN enables multicast traffic forwarding using **PIM-SM** to distribute content across multiple sites efficiently.

### **How Multicast Works in SD-WAN**
- **The ingress router** (connected to the multicast source) forwards streams to a **replicator vEdge**.
- The replicator **distributes copies** of multicast traffic **to all interested receivers**.
- **WAN Edge routers support IGMPv2**, tracking receiver memberships within **specific VPNs**.

> **Important Note:** The **PIM Rendezvous Point (RP) function is not supported on vEdge devices**. Instead, RP must reside on **local-site PIM routers**. Auto-RP can be used for RP-to-group mapping.



## 🔁 Multicast Replicator Optimization

### **Why It Matters**
Multicast replication in SD-WAN **saves bandwidth** by reducing **redundant multicast streams** over WAN links.

### **How It Works**
- When multiple **WAN Edge routers** in the same **VPN** need access to the same **multicast group**, instead of each router **individually pulling** the stream from an external source, **one router is elected as the multicast replicator**.
- The **multicast replicator** receives **multicast traffic** and **locally forwards copies** to other WAN Edge routers in the VPN via **internal tunnels**.
- This mechanism **eliminates duplicate multicast flows**, conserving bandwidth and reducing **unnecessary WAN overhead**.

### **Key Benefits**
- **Efficient Bandwidth Utilization** – Reduces duplicate multicast streams over expensive WAN links.
- **Optimized Traffic Forwarding** – Ensures multicast packets reach multiple recipients **without increasing WAN usage**.
- **Scalability** – Enables seamless multicast replication for **large-scale SD-WAN deployments**.

---
### 📚 Navigation
- ← Previous: [QoS in Cisco SD-WAN](./sd-wan-qos.md)
- ↩ Return to [Cisco SD-WAN](./README.md)
