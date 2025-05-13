# 🎯 QoS in Cisco SD-WAN

Cisco’s SD-WAN solution includes several **QoS features** designed for **traffic prioritization, real-time path selection**, and optimized **network performance**.



## ⚙️ QoS Features in SD-WAN
- **Bidirectional Forwarding Detection (BFD)**
- **Application-aware Routing**
- **Interface Queuing with Low-Latency Queueing (LLQ)**


## 🛰️ Bidirectional Forwarding Detection (BFD)

WAN edge routers use **BFD** to probe and measure transport link performance. It provides real-time metrics such as:

- **Latency**
- **Jitter**
- **Loss**

BFD runs inside **IPsec tunnels** and operates in **echo mode**. It is automatically enabled when tunnels are established and **cannot be disabled**.


#### **Key Functions**
- Subsecond failure detection on transport links  
- Helps determine **path liveliness and quality**  
- Gathers data on **interface status and IPsec MTU**  


## 📡 Application-Aware Routing

**Application-aware routing** selects the best path for traffic based on:
- **Application identification**  
- **Real-time SLA metrics** from BFD  
- **Policy-based rules and thresholds**  

When SLA thresholds (**latency, jitter, loss**) are exceeded, traffic is **automatically rerouted** to an alternative path that meets performance expectations.


## 🧃 Interface Queuing with LLQ

QoS policies on **vEdge interfaces** support:
- **Class-based queuing** to prioritize traffic types
- **Low-Latency Queuing (LLQ)** for real-time applications like **voice and video**
- **Traffic shaping and policing mechanisms**
- **DSCP remarking** to ensure consistent QoS enforcement across the WAN


---
### 📚 Navigation
- → Next: [SD-WAN Multicast](./sd-wan-multicast.mdd)
- ← Previous: [Direct Internet Access and Security](./sd-wan-dia-security.md)
- ↩ Return to [Cisco SD-WAN](./README.md)