# WAN Design for High Availability

## Introduction

Designing a high-availability WAN is a critical task for ensuring continuous business operations and minimizing downtime. High availability (HA) is achieved by eliminating single points of failure in the network, implementing redundancy, and using both software and hardware-based resiliency methods. In modern enterprise environments, a well-designed WAN must accommodate not only on-premises infrastructure but also hybrid and cloud-based solutions, all while maintaining performance, security, and scalability.

This document focuses on strategies and design considerations for creating a high-availability WAN, exploring single-homed and multi-homed approaches, the integration of MPLS and Internet VPNs, and hybrid solutions to enhance redundancy and reliability.

## Design for High Availability

High availability is essential for businesses, especially for critical applications. The goal is to eliminate single points of failure in the network design using software features or hardware-based resiliency. Redundancy is crucial for achieving high levels of availability.

### Techniques for High Availability
- **Built-in Techniques**: Some technologies have inherent high availability features.
- **Additional Techniques**: For technologies lacking high availability, other methods can be employed, such as additional WAN circuits or backup power supplies.

## Single-Homed Versus Multi-Homed WANs

### Single-Homed WANs
- **Advantages**: Only one vendor to manage, common QoS model.
- **Disadvantages**: Catastrophic if the carrier has an outage, difficult to transition to a new carrier.

### Multi-Homed WANs
- **Advantages**: Segmented fault domains, more WAN offerings, greater failover capabilities.
- **Disadvantages**: More complex to manage, higher recurring WAN costs.

## Single-Homed MPLS WANs
- **Design**: Each site connects to a single MPLS VPN from one provider.
- **Routing**: CE routers peer with the provider using eBGP, iBGP for CE-to-CE peering, local prefixes advertised with BGP, learned BGP routes redistributed into IGP (OSPF/EIGRP).

## Multi-Homed MPLS WANs
- **Design**: Each site connects to both provider A and provider B.
- **Routing**: CE routers redistribute local routes from EIGRP into BGP, BGP routes redistributed into EIGRP as external routes, filtering/tagging to prevent routing loops.

## Hybrid WANs: Layer 3 VPN with Internet Tunnels
- **Design**: MPLS VPN for primary connection, Internet tunnel for backup.
- **Routing**: eBGP for peering with MPLS VPN provider, EIGRP for internal routing, BGP routes preferred over EIGRP routes, FHRP for failover, routing protocol metrics modification for path preference.

## WAN Integration
- **Service**: Seamless connectivity between on-premises data center and cloud provider's data center.
- **Benefits**: Improved application performance, optimized traffic routing, reduced costs compared to dedicated MPLS connections.

---

### 📚 Navigation
- → Next: [Direct Connect and MPLS Direct Connect](direct-connect.md)  
- ← Previous: [WAN Design (Single-homed, Multihomed, Failover)](wan-design.md) 
- ↩ Return to: [WAN - Index](../README.md)

