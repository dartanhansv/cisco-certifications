# Route Redistribution

### 🔁 What is Route Redistribution?
Route redistribution is the process of exchanging routes between different routing protocols on a router, typically at the service provider edge or at the boundary of autonomous systems. It's commonly used in:

- Migrations from legacy to modern routing protocols.
- Environments with multiple vendors using different protocols.
- Enterprises with separate administrative domains.
- Mergers and acquisitions where initial integration requires communication across different routing systems.

---

### 📥 Route Sources
Routes redistributed may originate from:

- **Static Routes**: Often used when not peering with AS external routers.
- **Different Routing Protocols**: For example, one domain using EIGRP and another using OSPF.
- **ISP Peering**: Enterprise running OSPF while the ISP uses BGP.

---

### ⚠️ Route Feedback
Route feedback occurs when a routing protocol learns a route via redistribution and inadvertently announces it back to the protocol it came from. This can result in routing loops and instability if not controlled.

---

### 🔄 Redistribution Methods

#### Two-Way Redistribution
- Routing information is exchanged between two protocols without relying on static routes.
- Route filters (like distribute-lists, prefix-lists, and route-maps) are essential to prevent loops.

#### One-Way Redistribution
- Routes are redistributed in one direction only (e.g., from EIGRP into OSPF).
- Often used at the network edge with static or default routes injected into the routing domain.

---

### 🧮 Metrics and Configuration
Different routing protocols use different metrics. When redistributing, you must configure appropriate seed metrics:

- Use the `default-metric` command to assign a metric to redistributed routes.
- Without a metric, some protocols (like EIGRP) will not accept redistributed routes.

#### OSPF-Specific Considerations
- Use the `subnets` keyword to allow redistribution of subnetted routes.
- Redistributed routes are external Type 2 (E2) by default.
- Use the `metric-type` keyword to change to external Type 1 (E1) if desired.

---

### 🚫 Non-Transitive Redistribution
Redistribution is not inherently transitive. For example:

- OSPF routes redistributed into EIGRP.
- EIGRP routes redistributed into BGP.
- OSPF routes are *not* automatically passed into BGP through EIGRP.

Each redistribution step is isolated and must be explicitly configured.

---

### 🧠 Design Recommendations
- Use **access-lists**, **distribution-lists**, and **route-maps** to:
  - Filter incoming/outgoing routes.
  - Set metrics and route tags.
  - Prevent routing loops.

- For **two-way redistribution**, always include route filters and tag routes to prevent re-entry.
- Configure **default metrics** using protocol-specific commands.
- In OSPF, use appropriate `metric-type` and `subnets` options.
- Consider **summarization** and **loop prevention strategies** in multi-protocol environments.

---

### 📚 Navigation
- → Next: [Back to Redistribution CheetSheet](./redistribution-cheatsheet.md)
- ← Previous: [Redistribution Overview](./redistribution-overview.md)
- ↑ Back to: [Routing Protocols - Fundamentals](../readme.md)
