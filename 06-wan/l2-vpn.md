# 🖧 Layer 2 VPN (L2VPN)

## 🧠 Introduction
Layer 2 VPNs (L2VPNs) enable geographically dispersed Ethernet devices to communicate as if they were part of the same LAN segment. Service providers deliver Layer 2 connectivity across an IP or MPLS-enabled network, offering customers a seamless extension of their local network.

#### 📚 Sources
- [NetworkLessons - MPLS Layer 2 VPNs](https://notes.networklessons.com/mpls-layer-2-vpns)
- [Cisco XR MPLS Layer 2 VPN Configuration Guide](https://www.cisco.com/en/US/docs/routers/xr12000/software/xr12k_r4.0/lxvpn/configuration/guide/vc40v2.pdf)


### 🚛 How It Works
L2VPN solutions emulate the behavior of a traditional LAN using service provider infrastructure:

- **Function**: Emulates LAN behavior across a WAN.
- **ISP Coordination**: The service provider manages Layer 2 transport, while customers maintain their own routing.
- **Capabilities Required**:
  - Encapsulation of Layer 2 PDUs into Layer 3 packets.
  - Support for various tunneling mechanisms.
  - Maintenance of Layer 2 QoS and process databases.
  - Ease of configuration and management.

### 🛠️ MPLS Layer 2 VPNs

#### 📡 Service Options
- **Layer 2 VPNs**: Provide Layer 2 adjacency (more expensive, useful for specific applications).
- **Layer 3 VPNs**: Provide Layer 3 connectivity (more scalable and cost-effective).

#### 🔗 Connectivity Model
- Enables HQ and branch routers to stay on the same IP subnet.
- Supports dynamic routing protocols like **OSPF** and **EIGRP** across the WAN.

#### 🏗️ Key Concepts

- **MPLS Backbone**: Optimizes speed and traffic shaping.
- **Virtual Private Network (VPN)**: Isolates customer traffic over a shared infrastructure.
- **Layer 2 Extension**: Extends Ethernet, Frame Relay, or ATM traffic over an MPLS network.

### 🧩 Types of MPLS Layer 2 VPNs

- **Point-to-Point (Pseudowire)**: Connects two sites, emulating a leased line.
- **Virtual Private LAN Service (VPLS)**: Provides multipoint-to-multipoint LAN emulation.
- **Hierarchical VPLS (H-VPLS)**: Improves scalability and management for large deployments.

### ⚙️ Operational Mechanisms

- **Label Switching**: MPLS routers use labels instead of IP lookups.
- **Encapsulation**: Layer 2 frames are encapsulated and sent across the MPLS backbone.
- **Traffic Isolation**: Uses separate Label Switched Paths (LSPs) for each customer.

### 🎯 Benefits

- **Flexibility and Scalability**: Supports various Layer 2 protocols across the MPLS network.
- **QoS Enforcement**: Prioritizes critical traffic (e.g., voice, video).
- **Simplified WAN Architecture**: Reduces routing complexity.
- **Efficient Bandwidth Utilization**: Optimizes traffic flow and resource use.

### 📦 Use Cases

- **Business Connectivity**: Seamless branch and data center connectivity.
- **Service Provider Offerings**: Deliver Layer 2 VPN services without dedicated circuits.
- **Disaster Recovery**: Enable fast, reliable backup and replication.

### ⚠️ Considerations

- **Provider Dependence**: Tightly coupled with the provider’s MPLS backbone.
- **Higher Costs**: Generally more expensive than internet-based VPNs.
- **Deployment Complexity**: Requires strong MPLS and Layer 2 expertise.

---

#### 📚 Navigation
- → Next: [WAN Connection Decision Points](wan-connection-decision-points.md)  
- ← Previous: [WAN Overview](wan-overview.md)  
- ↑ Back to: [WAN for Enterprise Networks](./README.md)

---

### 📚 Navigation
- → Next: [MPLS Layer 3 VPN](mpls-l3-vpn.md) 
- ← Previous: [GRE, mGRE, and IPsec Tunnels](gre-mgre-ipsec.md) 
- ↩ Return to: [WAN - Index](../README.md)

