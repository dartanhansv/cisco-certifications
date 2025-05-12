# Service Provider-Managed VPNs

## WAN Connection Decision Points

When choosing a WAN solution, consider service availability, financial factors, technical aspects, and security requirements.

### Key Factors:

#### **Service Availability**

- Reliability and uptime of the WAN service.
- Redundancy options to ensure high availability.

#### **Financial Decision Points**

- **Total VPN solution cost**: Subscription fees, infrastructure costs, and maintenance.
- **Vendor Lock-in**: Dependency on a single provider may limit flexibility.

#### **Technical Aspects**

- **Convergence**:
  - Layer 3 VPNs rely on the service provider for routing and convergence.
  - Layer 2 VPNs require customer-managed routing.
- **Scalability**:
  - Layer 2 VPNs may face challenges in full-mesh topologies due to numerous adjacencies.
  - Layer 3 VPNs are more scalable since CE devices connect only to the PE device.
- **Quality of Service (QoS)**: Ensures application prioritization.
- **Service Level Agreements (SLA)**: Defines performance guarantees.
- **Supported Traffic Types**: Voice, video, and data compatibility.
- **MTU Size Considerations**: Avoids fragmentation issues.

#### **Security Considerations**

- Some WAN solutions provide encryption (e.g., MPLS does not inherently encrypt traffic).
- Importance of security measures when using internet-based VPNs.
- IPSec or other encryption mechanisms may be required for data confidentiality.

#### **Redundancy & High Availability**

- Dual-homed connections for failover.
- Using multiple providers to ensure continuity.
- Backup solutions like LTE or satellite for emergency failover.

#### **Performance Factors**

- Latency, jitter, and packet loss considerations.
- Impact of different WAN technologies (MPLS vs. Internet VPN vs. Dedicated Circuits).
- How QoS policies affect real-time applications.



---

### 📚 Navigation
- → Next: [WAN Technologies (Metro Ethernet, DWDM, 4G/5G, and more)](wan-technologies.md)  
- ← Previous: [WAN Overview](./wan-overview.md)
- ↩ Return to: [WAN - Index](../README.md)

