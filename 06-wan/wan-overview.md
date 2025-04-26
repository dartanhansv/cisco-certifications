# WAN Overview

## Introduction
Wide Area Networks (WANs) connect geographically distributed sites, enabling organizations to share resources, applications, and services efficiently. WAN design must consider multiple factors, including cost, performance, scalability, and security.

## WAN Transport Technologies
Different transport technologies are used to establish WAN connectivity, each with its own characteristics and use cases:

- **MPLS (Multiprotocol Label Switching)**
  - Service provider-managed WAN solution.
  - Offers traffic engineering, QoS, and VPN services.
  - Provides predictable performance and SLAs.
  - For a deep dive, see [MPLS Layer 3 VPN](./mpls-l3-vpn.md).

- **Internet-Based WAN (Broadband, LTE, 5G, etc.)**
  - Cost-effective and widely available.
  - No inherent QoS or SLAs (except for business-grade circuits).
  - Typically secured using VPNs (e.g., IPsec, DMVPN, or SD-WAN).
  - See [Enterprise-Managed VPNs](./enterprise-managed-vpns.md) for VPN options.

- **Leased Lines (Dedicated Circuits, Metro Ethernet, Dark Fiber, etc.)**
  - High-performance, private, and dedicated bandwidth.
  - Expensive and less flexible than other options.
  - Often used for data center interconnects.

## WAN Design Considerations

### **1. QoS (Quality of Service)**
- Prioritizes critical traffic (e.g., voice, video, business apps).
- Reduces latency, jitter, and packet loss.
- For details on implementing QoS in WANs, refer to [WAN Connection Decision Points](./wan-connection-decision-points.md).

### **2. Scalability**
- MPLS scales well due to provider-managed routing.
- Internet-based solutions may face performance challenges as the network grows.

### **3. Resiliency & Redundancy**
- WAN designs should include failover mechanisms (e.g., dual ISP, redundant MPLS links, SD-WAN).
- Dynamic routing protocols (BGP, EIGRP, OSPF) help maintain connectivity.
- Learn more about routing protocols at [PE-CE Routing Protocols](./mpls-layer3-vpn.md).

### **4. Security**
- Internet-based WANs require encryption (IPsec, SSL, or TLS-based VPNs).
- MPLS is inherently private but may still need encryption for compliance.
- See [GRE, mGRE, and IPsec](./gre-mgre-ipsec.md) for secure tunneling methods.

### **5. Cost Considerations**
- MPLS is more expensive but provides SLAs.
- Internet-based solutions are cost-effective but may require additional security and QoS mechanisms.

## Related Topics
- [WAN Connection Decision Points](./wan-connection-decision-points.md)
- [Enterprise-Managed VPNs](./enterprise-managed-vpns.md)
- [MPLS Layer 3 VPN](./mpls-layer3-vpn.md)
- [GRE, mGRE, and IPsec](./gre-mgre-ipsec.md)
- [IPsec, VTI, and DMVPN](./ipsec-vti-dmvpn.md)

