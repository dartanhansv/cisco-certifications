# SD-WAN Overview

Software-Defined Wide Area Network (SD-WAN) revolutionizes WAN deployments by abstracting transport networks and centralizing control, offering agility, security, and scalability for enterprises.

---

## Why SD-WAN?

- **Application Optimization**: Enables dynamic path selection and application-aware routing for better performance.
- **Cost Efficiency**: Reduces reliance on expensive MPLS circuits by enabling broadband or LTE/5G usage.
- **Security at Scale**: Integrates with cloud-delivered security services and enforces policy-based segmentation.
- **Operational Simplicity**: Centralized configuration and monitoring reduce provisioning and troubleshooting time.

---

## Cisco SD-WAN

Cisco SD-WAN is built on **Software-Defined Networking (SDN)** principles, which centralize control and abstract the underlying transport infrastructure from the application layer.

- Enterprise-class WAN architecture overlay integrating routing, security, orchestration, and centralized policy.
- Transport independent: Supports MPLS, 4G/5G, and low-cost Internet links.
- Extends seamlessly to data centers, branch offices, and public cloud providers.
- **Cloud Integration**: Cisco SD-WAN integrates with Megaport for on-demand branch connectivity to AWS, Azure, and Google Cloud.

---

## Core SD-WAN Capabilities
Cisco SD-WAN offers several core capabilities that differentiate it from traditional WAN architectures:

- Application-aware routing
- Zero-touch provisioning (ZTP)
- Centralized policy and template management
- End-to-end segmentation
- Integrated security features (firewall, IPS, URL filtering)

---

## Underlay vs Overlay

### **Underlay Network**
- **Transport Links**: MPLS, broadband Internet, LTE/5G, and other connection types.
- **Physical Devices**: Routers, switches, and access points that manage traffic forwarding and site connectivity.
- **Routing and IP Connectivity**: Conventional routing protocols like OSPF, BGP, and static routes to handle data forwarding.
- **Essential Services**: DNS, DHCP, and time synchronization are typical services in the underlay.

The underlay network must be operational to support the virtual SD-WAN overlay network on top of it

### **Overlay Network**  
The **overlay network** is the virtual SD-WAN network built on top of the underlay. It provides advanced features like secure, application-aware routing and centralized policy control. The overlay includes:

- **Tunnels**: IPsec-encrypted virtual links (TLOCs) established between SD-WAN edge devices across the underlay.
- **Centralized Control**: Policies, routing decisions, and segmentation pushed by controllers (vSmart) and orchestrated through the management plane.
- **Transport Abstraction**: Normalizes behavior across different link types (e.g., MPLS vs. Internet) to simplify policy application.
- **Segmentation**: Enables traffic separation using VPNs and VRFs for user, voice, or guest services.

The overlay network adds **flexibility, scalability, and security**, transforming the underlying physical WAN into a dynamic, application-optimized fabric.


---


## SD-WAN Planes

| **Plane**                | **Description**                               |
|--------------------------|-----------------------------------------------|
| **Control Plane**        | Manages and distributes routing information.  |
| **Data Plane**           | Forwards user data packets between locations. |
| **Orchestration Plane**  | Coordinates network elements and resources.   |
| **Management Plane**     | Handles configuration, monitoring, and troubleshooting. |

---

## Customer Edge Platform Options

- **Physical Devices**: Branch services routers (ISR/ASR) or vEdge hardware appliances.
- **Software Devices**: vEdge cloud instances tailored for:
  - Data centers
  - Campus networks
  - Branch offices
  - Home offices
- Various models offer different speed capabilities and WAN transport compatibility.

---

### 📚 Navigation
- → Next: [SD-WAN Architecture](./sd-wan-architecture.md) 
- ↩ Return to [Cisco SD-WAN](./README.md)
