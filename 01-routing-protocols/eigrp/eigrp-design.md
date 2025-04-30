# EIGRP Design Considerations

EIGRP does not broadcast its routing table periodically, which minimizes network overhead. It is scalable, efficient, and a suitable choice for large networks — even as a core routing protocol. Its simplicity and performance make it ideal for both LAN and WAN environments. However, as a Cisco-proprietary protocol, it is not interoperable with third-party routers.

EIGRP is preferred over RIP in all enterprise scenarios due to faster convergence, better scalability, and more robust feature support.

---

## 🚀 EIGRP Scaling Techniques

For networks exceeding 100 routers, specific scaling strategies become important to maintain stability and performance:

### 🔁 Hierarchical Topology with Route Summarization

- As network size grows, risks like instability and delayed convergence increase.
- For example, in networks with 500+ routers, EIGRP may degrade without proper hierarchy.
- Use structured designs with summarization to minimize routing overhead.

**Best Practices:**

- Implement hierarchical layers with clear aggregation and distribution boundaries.
- Summarize routes at key aggregation points to reduce query propagation and CPU load.

#### ➕ Multiple EIGRP Autonomous Systems

- Used to segment very large networks.
- Limits query scope to within a specific AS, improving scalability.
- Offers logical separation of network domains.

> ⚠️ Use carefully—EIGRP routes between different ASes are considered *external* (AD 170) and may not be preferred unless explicitly managed.

---

### 🌿 EIGRP Stub Routers

Stub routing is commonly used in hub-and-spoke topologies, especially over WANs.

**Behavior:**

- Stub routers advertise only a limited set of routes (e.g., connected, summary, static) to their upstream (hub).
- They do *not* forward routes learned from other EIGRP neighbors.

**Advantages:**

- Reduces query traffic across slow WAN links.
- Conserves memory and CPU resources.
- Increases network stability in large or complex topologies.

**Disadvantage:**

- Stub routers cannot act as backup paths between hub sites.

---

## 🖥️ EIGRP in the Data Center

Design considerations for EIGRP in data center (DC) environments are similar to those in WAN design but adapted to DC-specific requirements:

### 🔹 Subnet Summarization

- Summarizing subnets at the aggregation layer helps reduce the size of routing tables.
- Improves scalability and simplifies troubleshooting in complex DC networks.

### 🔹 Default Route Advertisement

- Aggregation layer routers can advertise a default route into the access layer.
- Prevents the need to propagate the full routing table throughout the DC.
- Enhances security and simplifies routing logic in access-layer switches or routers.

These techniques help EIGRP remain scalable and efficient in the context of diverse, high-speed, service-rich data center environments.

---

## 📚 Navigation
- → Next: [EIGRP Named Mode](eigrp-named.md)  
- ← Previous: [EIGRP Overview](eigrp-summary.md)  
- ↑ Back to: [Routing Protocols](../readme.md)
