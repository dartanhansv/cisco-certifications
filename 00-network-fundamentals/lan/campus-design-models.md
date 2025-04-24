# Campus Design Models

This document outlines design models used in enterprise campus networks, with focus on modularity, scalability, and fault isolation.

## Three-Tier Model

The **Three-Tier Model** is the traditional [hierarchical network model](hierarchical-network-model.md) consisting of:

- **Core Layer**: High-speed backbone, routing between distribution blocks.
- **Distribution Layer**: Policy enforcement, inter-VLAN routing, redundancy.
- **Access Layer**: User/device access, Layer 2 forwarding, security.

This model supports scalability by segmenting the network into modular distribution blocks.

## Two-Tier (Collapsed Core) Model

Used in smaller networks where **core and distribution layers are combined** into a single layer:

- Reduces cost and complexity.
- Suitable for environments with limited scalability needs.
- Simplifies troubleshooting but limits scalability.

## Routed Access Design

In this model, **Layer 3 routing extends to the access layer**:

- Each access switch is a Layer 3 device with its own IP subnet.
- **No need for STP across uplinks**, reducing convergence issues.
- Redundancy and load balancing are handled via routing protocols instead of FHRP.
- Typically used with **RIP, EIGRP, OSPF**, or **HSRP with routed ports**.

This design enhances convergence speed, fault isolation, and scalability but requires more configuration and capable hardware at the access layer.

**Diagram:** [Routed Access Design](TBD)

---

## Design Considerations

- Align network design with **business requirements**.
- Apply **redundancy** and **fast convergence mechanisms**.
- Keep traffic **local within distribution blocks** when possible.
- Use **Layer 3 Access layer** when possible.

---

## Routing Convergence in Multi-Campus Designs

### Core Design: Building Triangles and Redundant Links
- **Building Triangles**: Cisco recommends using redundant triangles instead of squares to leverage equal-cost redundant paths for deterministic convergence.
- **Redundant Links**: Triangular designs with redundant links enable equal-cost path routing, allowing each switch to have two routes and two Cisco Express Forwarding adjacency entries, ensuring fast traffic restoration without waiting for routing protocol convergence.

### Routing Convergence
- **Factors Affecting Convergence Time**:
  - **Detection Time**: Time to detect the loss of a valid forwarding path.
  - **Path Determination Time**: Time to determine an ideal new path, influenced by the number of routers involved.
  - **Update Time**: Time to update software and Cisco Express Forwarding hardware forwarding tables with new routing information.

- **Equal-Cost Paths**: If switches have redundant equal-cost paths, convergence events are handled locally within the switch. Without equal-cost paths, EIGRP or OSPF must determine a new route, impacting convergence times.

- **EIGRP Convergence**: Time varies based on the number of EIGRP queries and the response time for each query. Design must limit the number and range of queries to reduce convergence time.

- **OSPF Convergence**: Time required to flood and receive LSAs and run the Dijkstra SPF computation to determine the SPT. Network recovery optimization involves tuning the design to reduce the time and resources needed for these events.

---
