# 🚀 Designing End-to-End QoS Policies

Cisco has developed various QoS mechanisms to manage and prioritize network traffic, ensuring proper functionality for delay-sensitive applications like VoIP.

---

## 🎯 Traffic Classification and Marking
- **Classification**: Identifies the type of traffic.
- **Marking**: Sets a value in the IP header based on classification.

**Technologies Supporting Classification**:
- **Network-based Application Recognition (NBAR)**: Uses deep packet inspection to identify applications, even those not using standard ports.
- **Committed Access Rate (CAR)**: Uses rate limits to set precedence, customizable by user, IP address, and application type.

---

## 📦 Traffic Shaping and Policing

### 📥 Shaping
- **Traffic Shaping**: Slows down packet transmission rate using a token bucket technique.
- **Purpose**: Smooths traffic to prevent drops at provider networks.

### 📤 Policing
- **Policing**: Tags or drops traffic based on match criteria.
- **Mechanism**: Uses a "leaky bucket" model to limit ingress traffic.

**Comparison**:
| Feature     | Shaping                       | Policing                 |
| ----------- | ----------------------------- | ------------------------ |
| Action      | Buffers packets               | Drops or remarks packets |
| Propagation | Does **not** propagate bursts | **Propagates** bursts    |

---

## 🎛️ Queuing Strategies

When packets arrive faster than they can be transmitted, they are queued. Different queuing techniques manage how packets are selected for transmission:

### 🛡️ Low-Latency Queuing (LLQ)

- **LLQ (Queue 0)**: Strict priority queue used for control and BFD traffic.
- **DSCP Marking**: 48 decimal.
- **Behavior**: Traffic in LLQ is transmitted first.

**Congestion Handling**:
- Uses **Tail Drop**: Drops packets when the queue is full.

---

### ⚙️ Weighted Round Robin (WRR)

- **Queues 1-7**: Scheduled using WRR.
- **Queue 2**: Default queue for user traffic.

---

### 📈 Packet Flow on vEdge Routers
1. Local policy and configuration checks (policer, classification)
2. Application-aware routing policy (SLA-based)
3. Centralized data policy enforcement
4. Routing and forwarding
5. Scheduling and queuing (LLQ, WRR, RED)
6. Local shaping and ACLs

---

## 🎯 QoS Effectiveness

QoS **manages existing bandwidth**, prioritizing critical traffic during congestion, but **does not add bandwidth**.

**Popular Technique**:
- Traffic classification based on protocol type or ACL.
- Identified classes get specific policy treatments.
- Remaining traffic is treated as best effort.

---

# 🚀 QoS Options Overview

Cisco offers a variety of congestion management strategies depending on the router queue type:

### 📥 Priority Queuing (PQ)
- **Four Queues**: High, medium, default, and low.
- **Downside**: Risk of starvation for lower-priority traffic.

### 📦 Custom Queuing (CQ)
- **Up to 16 Queues**: Byte limits per queue.
- **Fairness**: Allows bandwidth sharing, but considered legacy.

### 🎯 Weighted Fair Queuing (WFQ)
- **Traffic Separation**: Grouped into high- and low-bandwidth flows.
- **Priority**: Low-bandwidth prioritized over high-bandwidth.

---

# 📚 Evolution to Modular QoS

Newer methods modularized queuing into classes and priorities:

### 📈 Class-Based Weighted Fair Queuing (CBWFQ)
- **Modular Classes**: Based on ACLs, protocols, interfaces.
- **Flexibility**: Create many traffic classes.

### 🔥 Low-Latency Queuing (LLQ) + CBWFQ
- **Strict Priority Queue**: Handles delay-sensitive traffic like VoIP.
- **Starvation Prevention**: Maximum thresholds applied.

---

## 🔧 Link Efficiency Techniques

Cisco IOS supports:
- **LFI (Link Fragmentation and Interleaving)**
- **Multilink PPP (MLP)**
- **RTP header compression**

These optimize bandwidth usage on slower links.

---

## 🎯 TCP Window Size

- **Definition**: Upper limit of frames transmitted without ACK.
- **Tuning**: Improves performance under high delay or loss conditions.

---

# 📚 Navigation
- ↑ Back to: [Network Services](../readme.md)
