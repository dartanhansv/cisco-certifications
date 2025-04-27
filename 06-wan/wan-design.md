# WAN Design for High Availability

Designing a high-availability WAN is a critical task for ensuring continuous business operations and minimizing downtime. High availability (HA) is achieved by eliminating single points of failure in the network, implementing redundancy, and using both software and hardware-based resiliency methods.


### Single-Homed

A single-homed WAN design involves connecting a site to a single service provider. This approach is simpler but may not offer the same level of resilience as a multi-homed design.

#### Advantages
- **Simpler Management**: Only one vendor to manage, reducing complexity.
- **Cost-Efficient**: Typically lower costs for connectivity and equipment.
- **Common QoS Model**: Easier to implement QoS policies across the network.

#### Disadvantages
- **Single Point of Failure**: If the service provider experiences an outage, the entire site loses connectivity.
- **Limited Flexibility**: Difficult to transition to a new provider without significant disruptions.

---

### Multihomed

A multi-homed WAN design involves connecting a site to multiple service providers or different types of connections (e.g., MPLS, Internet). This increases resilience by providing multiple paths for traffic to flow.

#### Advantages
- **Redundancy**: Segmented fault domains and greater failover capabilities.
- **More WAN Options**: Ability to choose from different providers and technologies.
- **Higher Availability**: Better suited for mission-critical applications that require high uptime.

#### Disadvantages
- **Increased Complexity**: More complex routing and management due to the multiple connections.
- **Higher Costs**: More expensive in terms of both initial setup and ongoing maintenance.

---

### Design for High Availability

#### Techniques for High Availability

- **Built-in Techniques**: Some technologies inherently support high availability (e.g., dynamic routing, MPLS).
- **Additional Techniques**: For technologies that lack built-in high availability, other methods can be employed, such as:
  - **Additional WAN Circuits**: Provides backup routes for traffic in case of failure.
  - **Backup Power Supplies**: Ensures continued operation during power outages.

#### Single-Homed Versus Multi-Homed WANs

##### Single-Homed WANs
- **Advantages**: Only one vendor to manage, common QoS model.
- **Disadvantages**: Vulnerable to service provider outages, difficult to switch providers.

##### Multi-Homed WANs
- **Advantages**: Increased fault tolerance, more failover options, and broader choice of providers.
- **Disadvantages**: More complex to configure and maintain, higher costs.

---

### Single-Homed MPLS WANs

- **Design**: Each site connects to a single MPLS VPN from one provider.
- **Routing**: 
  - CE routers peer with the provider using **eBGP**.
  - **iBGP** for CE-to-CE peering.
  - Local prefixes advertised via **BGP**, and BGP routes redistributed into **IGP** (OSPF/EIGRP).

---

### Multi-Homed MPLS WANs

- **Design**: Each site connects to both Provider A and Provider B.
- **Routing**:
  - **CE routers** redistribute local routes from **EIGRP** into **BGP**.
  - BGP routes are redistributed into **EIGRP** as external routes.
  - Filters and tags are applied to prevent routing loops.

---

### Hybrid WANs: Layer 3 VPN with Internet Tunnels

- **Design**: MPLS VPN is used as the primary connection, while an Internet tunnel serves as backup.
- **Routing**: 
  - **eBGP** for peering with the MPLS VPN provider.
  - **EIGRP** for internal routing.
  - BGP routes are preferred over EIGRP routes.
  - **FHRP** (First Hop Redundancy Protocol) is used for failover.
  - Routing protocol metrics are adjusted for path preference.

---

### WAN Integration for Hybrid Solutions

- **Service**: A seamless connection between an on-premises data center and a cloud provider’s data center.
- **Benefits**:
  - **Improved Application Performance**: Optimizes traffic routing.
  - **Cost Reduction**: Reduces the need for dedicated MPLS connections.
  - **Flexibility**: Leverages cloud resources for scalability.

---

### 📚 Navigation
- → Next: [WAN ailover and Backup Connectivity](./wan-backup-connectivity.md)  
- ↑ Back to: [WAN Technologies](./README.md)
