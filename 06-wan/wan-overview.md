# WAN Overview

## Introduction
Wide Area Networks (WANs) connect geographically distributed sites, enabling organizations to share resources, applications, and services efficiently. WAN design must consider multiple factors, including cost, performance, scalability, and security.

## WAN Transport Technologies
Different transport technologies are used to establish WAN connectivity, each with its own characteristics and use cases:

- **MPLS (Multiprotocol Label Switching)**  
  🏷️ Service provider-managed WAN solution.  
  🏷️ Offers traffic engineering, QoS, and VPN services.  
  🏷️ Provides predictable performance and SLAs.  
  📚 For a deep dive, see [MPLS Layer 3 VPN](./mpls-l3-vpn.md).

- **Internet-Based WAN (Broadband, LTE, 5G, etc.)**  
  🌐 Cost-effective and widely available.  
  🌐 No inherent QoS or SLAs (except for business-grade circuits).  
  🌐 Typically secured using VPNs (e.g., IPsec, DMVPN, or SD-WAN).  
  📚 See [Enterprise-Managed VPNs](./enterprise-managed-vpns.md) for VPN options.

- **Leased Lines (Dedicated Circuits, Metro Ethernet, Dark Fiber, etc.)**  
  🔗 High-performance, private, and dedicated bandwidth.  
  🔗 Expensive and less flexible than other options.  
  🔗 Often used for data center interconnects.

## WAN Connectivity Options

### On-Premises
- **Leased Lines**: Dedicated, reliable, high-speed connectivity such as T1/E1, T3/E3, and OCx circuits.
- **Wireless**: 
  - **LTE Advanced**: Download rates up to 600 Mbps, upload rates up to 100 Mbps.
  - **LTE Advanced Pro**: Download rates up to 1.1 Gbps, upload rates up to 200 Mbps.
  - **5G**: Download peak rates up to 20 Gbps, upload peak rates up to 10 Gbps.
- **MPLS**: Layer 3 VPN technology providing secure, reliable connectivity with QoS and CoS features.
- **Ethernet WAN**: Layer 2 VPN technology offering high-speed connectivity over copper, fiber, or wireless media.

### Cloud
- **Cloud Connect**: Direct connectivity to cloud service providers (AWS, Azure, Google Cloud), offering private, secure connections and improved application performance.
- **Cloud On-Ramp**: SD-WAN service providing seamless connectivity to cloud providers, optimizing traffic routing, reducing latency, and improving application performance.

### Hybrid
- **SD-WAN**: Cloud-enabled WAN technology offering secure, reliable connectivity using multiple transport options (broadband, MPLS, LTE). Optimizes application performance, controls routing, reduces costs, and simplifies management.

## WAN Design Considerations

### **1. QoS (Quality of Service)**
- Prioritizes critical traffic (e.g., voice, video, business apps).
- Reduces latency, jitter, and packet loss.
- 📚 For details on implementing QoS in WANs, refer to [WAN Connection Decision Points](./wan-connection-decision-points.md).

### **2. Scalability**
- MPLS scales well due to provider-managed routing.
- Internet-based solutions may face performance challenges as the network grows.

### **3. Resiliency & Redundancy**
- WAN designs should include failover mechanisms (e.g., dual ISP, redundant MPLS links, SD-WAN).
- Dynamic routing protocols (BGP, EIGRP, OSPF) help maintain connectivity.
- 📚 Learn more about routing protocols at [PE-CE Routing Protocols](./mpls-layer3-vpn.md).

### **4. Security**
- Internet-based WANs require encryption (IPsec, SSL, or TLS-based VPNs).
- MPLS is inherently private but may still need encryption for compliance.
- 📚 See [GRE, mGRE, and IPsec](./gre-mgre-ipsec.md) for secure tunneling methods.

### **5. Cost Considerations**
- MPLS is more expensive but provides SLAs.
- Internet-based solutions are cost-effective but may require additional security and QoS mechanisms.

---

### 📚 Navigation
- → Next: [WAN Connection Decision Points](./wan-connection-decision-points.md)  
- ↑ Back to: [WAN Technologies](../README.md)
