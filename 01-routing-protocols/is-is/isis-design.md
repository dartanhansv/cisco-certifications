# IS-IS Design  

IS-IS uses a **two-level hierarchy** for efficient routing in large networks. Routers are configured as:  
- **Level 1 (L1)**: Intra-area routing, similar to OSPF internal routers in a totally stubby area.  
- **Level 2 (L2)**: Interarea routing, similar to OSPF backbone routers.  
- **Level 1/Level 2 (L1/L2)**: Functions like an OSPF area border router (ABR).  

---

## IS-IS Backbone  
Unlike OSPF’s defined backbone area (Area 0), the IS-IS backbone is a **continuous path of adjacencies** among L2 routers.  
- **Rule**: L1 routers should not exist between L2-only or L1/L2 routers in the backbone.

### L1/L2 Router Behavior  
- Maintains **separate link-state databases** for L1 and L2 routes.  
- Does not advertise L2 routes to L1 areas.  
  - **L1 routers** rely on default routes via L1/L2 routers for destinations outside their area.  

---

## IS-IS Area Boundaries  
- IS-IS areas are **bounded by links** between L1/L2 and L2 routers, not by the L1/L2 routers themselves.  

---

## IS-IS Topologies  

| **Topology Type** | **Description**                                                                  | **Use Case**                                            |
| ----------------- | -------------------------------------------------------------------------------- | ------------------------------------------------------- |
| **Flat**          | Single area, no hierarchy or summarization; all routers on the same level.       | Small networks.                                         |
| **Hierarchical**  | Multi-area, backbone area via L1/L2 routers; follows three-layer architecture.   | Large networks requiring scalability and summarization. |
| **Hybrid**        | Multi-area without a backbone; allows summarization but less scaling efficiency. | Medium-sized networks.                                  |

### Transition from Flat to Hierarchical  
- **Factors to consider**: Router count, geographical dispersion, link types, and stability.  
- **Best Practice**: Start with an L2-only design to simplify future area additions and maintain backbone connectivity.  

---

## Route Leaking  

Route leaking allows selected L2 routes to be shared with L1 areas while preventing loops via an **up/down bit** mechanism.  

| **Up/Down Bit** | **Meaning**                                                     |
| --------------- | --------------------------------------------------------------- |
| `0`             | Route originated in the L1 area.                                |
| `1`             | Route leaked from L2 into L1 (prevents re-advertisement to L2). |

### Benefits of Route Leaking  
- Solves issues with protocols like **BGP and MPLS VPNs**, where BGP next-hop addresses must be present in routing tables.  
- Avoids suboptimal routing caused by default route reliance.  

### Key Points  
- Without route leaking, L1 routers rely on default routes for destinations outside their area.  
- Leaked routes are marked as `ia` (interarea) in routing tables.  

---

## Summarization in IS-IS  

Summarization hides detailed topology information, reduces update propagation, and isolates instability.  

### Guidelines for Summarization  
- Configure summarization on **L1/L2 routers injecting L1 routes into L2**.  
- Ensure all L1/L2 routers in an area summarize into the backbone to prevent uneven traffic distribution.  
- Internal routes cannot be summarized at L1 but can be summarized at L2.  

| **Direction**             | **Summarization Scope**          |
| ------------------------- | -------------------------------- |
| **Core → Distribution**   | Default route (`0.0.0.0/0`).     |
| **Distribution → Access** | Aggregate access network routes. |

---

## Mesh Groups  

Mesh groups reduce excessive flooding in large NBMA full-mesh networks by controlling Link-State Packet (LSP) propagation:  
- Group members do not reflood LSPs received from another member within the group.  
- Helps manage **performance and scalability** in networks with extensive mesh configurations.  

---

## Design Considerations  

- **NBMA Networks**: IS-IS does not directly support NBMA. Use a broadcast or point-to-point model depending on network characteristics.  
- **Flat vs. Hierarchical Design**:  
  - Flat designs are simpler but less scalable.  
  - A hierarchical approach ensures better scalability, making it the recommended choice for large networks.  

---

## Summary Table of Key IS-IS Design Features  

| Feature             | Details                                                                 |
| ------------------- | ----------------------------------------------------------------------- |
| **Backbone**        | Continuous path of adjacencies among L2 routers (not Area 0 like OSPF). |
| **Route Leaking**   | Allows selected L2 routes into L1 with up/down bit for loop prevention. |
| **Area Boundaries** | Defined by links between L1/L2 and L2 routers, not L1/L2 routers.       |
| **Summarization**   | Configured on L1/L2 routers; isolates instability and reduces traffic.  |
| **Mesh Groups**     | Reduces LSP flooding in full-mesh networks.                             |

---
