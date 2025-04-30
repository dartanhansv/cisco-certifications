# IS-IS Design

IS-IS network design focuses on building scalable and stable Layer 3 topologies by organizing routers into hierarchical levels, enabling route summarization, and controlling flooding domains. A well-designed IS-IS architecture improves convergence, simplifies management, and supports large-scale deployments without relying on a centralized backbone area like OSPF.

## IS-IS Hierarchy
IS-IS uses a **two-level hierarchy** for efficient routing in large networks:
- **Level 1 (L1)**: Intra-area routing, similar to OSPF internal routers in a stubby area.
- **Level 2 (L2)**: Interarea routing, similar to OSPF backbone routers.
- **Level 1/Level 2 (L1/L2)**: Functions like an OSPF area border router (ABR).

## IS-IS Backbone  
Unlike OSPF’s defined backbone area (Area 0), the IS-IS backbone is a **continuous path of adjacencies** among L2 routers.  
- **Rule**: L1 routers should not exist between L2-only or L1/L2 routers in the backbone.

### L1/L2 Router Behavior  
- Maintains **separate link-state databases** for L1 and L2 routes.
- Does not advertise L2 routes to L1 areas.
- **L1 routers** rely on default routes via L1/L2 routers for destinations outside their area, maintaining strict separation between intra-area and interarea routing information.

## IS-IS Area Boundaries  
IS-IS areas are **bounded by links** between L1/L2 and L2 routers, not by the L1/L2 routers themselves.

## IS-IS Topologies  

| **Topology Type** | **Description**                                                                  | **Use Case**                                            |
| ----------------- | -------------------------------------------------------------------------------- | ------------------------------------------------------- |
| **Flat**          | Single area, no hierarchy or summarization; all routers on the same level.       | Small networks.                                         |
| **Hierarchical**  | Multi-area, backbone area via L1/L2 routers; follows three-layer architecture.   | Large networks requiring scalability and summarization. |
| **Hybrid**        | Multi-area without a backbone; allows summarization but less scaling efficiency. | Medium-sized networks.                                  |

### Transition from Flat to Hierarchical  
- **Factors to consider**: Router count, geographical dispersion, link types, and stability.
- **Best Practice**: Start with an L2-only design to simplify future area additions and maintain backbone connectivity.

## Route Leaking  

Route leaking allows selected L2 routes to be shared with L1 areas while preventing loops via an **up/down bit** mechanism.  

| **Up/Down Bit** | **Meaning**                                                     |
| --------------- | --------------------------------------------------------------- |
| `0`             | Route originated in the L1 area.                                |
| `1`             | Route leaked from L2 into L1 (prevents re-advertisement to L2). |

### Benefits of Route Leaking  
- Solves issues with **BGP and MPLS VPNs**, where BGP next-hop addresses must be present in routing tables.
- Avoids suboptimal routing caused by default route reliance.
- **Leaked routes** are marked as `ia` (interarea) in routing tables.

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

## Mesh Groups  

Mesh groups reduce excessive LSP flooding in large NBMA or broadcast multi-access full-mesh networks:
- Group members do not reflood LSPs received from another member within the group.
- Improves **performance and scalability** in networks with extensive mesh configurations.

## Stability and Failover Behavior

A robust IS-IS design supports **fast convergence and stable operations** during link or node failures.

### Link Failure and Recovery
- IS-IS uses periodic LSP refreshes and SPF recalculations to detect and respond to changes.
- Upon a failure, IS-IS rapidly floods new LSPs, triggering SPF recalculation and reconvergence.
- **Route summarization** and **mesh groups** reduce instability propagation, enhancing resilience.

### Best Practices for Stability
- **Limit flooding domains** by designing appropriate area structures.
- **Use summarization** at L1/L2 routers to minimize unnecessary updates.
- **Leverage route leaking selectively** to optimize routing without excessive reliance on default routes.
- **Ensure backbone continuity** by preventing L1-only routers in the core path.

### 📚 Navigation
- ← Previous: [IS-IS IPv6 Deployment](isis-ipv6-deployment.md)  
- ↑ Back to: [IS-IS](./readme.md)
