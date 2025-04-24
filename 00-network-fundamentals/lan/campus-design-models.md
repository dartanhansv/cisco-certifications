# 🏗️ Campus Design Models

This document outlines design models used in enterprise campus networks, focusing on modularity, scalability, fault isolation, and optimal topology principles.

## 🧱 Three-Tier Model

The **Three-Tier Model** is the traditional [hierarchical network model](hierarchical-network-model.md) consisting of:

- **Core Layer**: High-speed backbone, routing between distribution blocks.
- **Distribution Layer**: Policy enforcement, inter-VLAN routing, redundancy.
- **Access Layer**: User/device access, Layer 2 forwarding, security.

This model supports scalability by segmenting the network into modular distribution blocks.

### Design Guidelines (Three-Tier Model)

#### Access Layer
- Limit routing neighbor relationships to avoid unnecessary CPU overhead.
- Restrict VLANs to a single wiring closet.
- Use **RPVST+** for rapid Spanning Tree convergence.
- Prune unused VLANs on trunks and disable trunking on host ports.
- Use **VTP Transparent** mode.
- Apply the `switchport host` command on end-user ports.
- Leverage Cisco STP Toolkit:
  - PortFast
  - Loop Guard
  - Root Guard
  - BPDU Guard
- Consider Layer 3 access to enable faster convergence and load balancing.

#### Distribution Layer
- Implement FHRPs (HSRP, VRRP, or GLBP) between access and distribution layers.
- Use Layer 3 routing protocols between distribution and core.
- Peer only on links intended for transit.
- Favor Layer 3 triangles over squares.
- Connect VLANs across access switches via distribution layer.
- Summarize routes towards the core to optimize convergence.
- Consider **VSS** to eliminate STP and FHRP in some cases.

#### Core Layer
- Use redundant triangle connections.
- Design a loop-free Layer 3 topology.
- Use equal-cost paths to all destination networks.
- Prefer Layer 3 switches in the core for intelligent services.

## 🧩 Two-Tier (Collapsed Core) Model

Used in smaller networks where **core and distribution layers are combined** into a single layer:

- Reduces cost and complexity.
- Suitable for environments with limited scalability needs.
- Simplifies troubleshooting but limits scalability.

## 🚦 Routed Access Design

In this model, **Layer 3 routing extends to the access layer**:

- Each access switch operates at Layer 3 with its own IP subnet.
- No STP across uplinks — improves convergence.
- Load balancing and redundancy handled via routing.
- Often used with **RIP, EIGRP, OSPF**, or **HSRP with routed ports**.

This design improves convergence speed, fault isolation, and scalability, but requires more capable hardware at the access layer.

**Diagram:** [Routed Access Design](TBD)

## 🧠 Routing Convergence in Multi-Campus Designs

### Core Design: Building Triangles and Redundant Links
- Cisco recommends **redundant triangles** instead of squares to enable deterministic convergence.
- Equal-cost paths provide fast failover using Cisco Express Forwarding.

### Convergence Factors
- **Detection Time**: Time to detect a failed path.
- **Path Determination**: Time to compute a new path (depends on network size).
- **Update Time**: Time to update software and hardware forwarding tables.

#### Protocol-Specific Convergence
- **EIGRP**: Depends on query scope and response time.
- **OSPF**: Depends on LSA flooding and SPF computation.

Network design must minimize these factors to optimize recovery.

## 📐 Optimal Topology Principles

These guidelines apply across all hierarchical layers:

- Ensure **high availability, scalability, and efficient routing**.
- Design for **redundancy** using multiple links and devices.
- Use **load balancing** to distribute traffic across multiple paths.
- Optimize for **fast convergence** to minimize downtime.
- Follow a **hierarchical structure** (core, distribution, access).
- **Segment** the network to improve performance and security.

---

