# 🌐 Direct Internet Access (DIA) and Security in Cisco SD-WAN

Traditional WANs often backhaul Internet traffic through the data center, increasing latency and consuming unnecessary bandwidth.
Cisco SD-WAN enables Direct Internet Access (DIA) at the branch, improving performance, efficiency, and security.
---

## 🚀 Direct Internet Access (DIA)

- **Local Internet Breakout**: Internet-bound traffic is sent directly from branch sites to the Internet, bypassing the data center.
- **Benefits**:
  - Reduces private WAN bandwidth usage.
  - Lowers latency and improves performance for cloud/SaaS apps.
  - Cuts costs by avoiding MPLS backhaul for Internet traffic.
- **Improved User Experience**: Better performance for cloud apps like Office 365, Salesforce, and Webex.
- **NAT Configuration**: NAT is applied on the Internet-facing interface for IP translation.

---

## 🛡️ Security Design in SD-WAN

Cisco SD-WAN offers a broad security framework, with both on-prem and cloud-hosted features.

### 🔒 Key Security Functions
1. **Network Segmentation**: Logical isolation using VPNs.  
2. **Enterprise Firewall**: Stateful inspection at the branch.  
3. **Secure Web Gateway**: Blocks malicious web content.  
4. **DNS-layer Security**: Blocks requests to known malicious domains.

### 🛡️ Additional Features
- **IPsec Encryption**:  Secures data plane tunnels across transports.
- **Intrusion Prevention System (IPS)**: Detects and blocks known threats.  
- **Application Controls**: Enforces application usage policies.
- **Malware Protection**: Scans for and blocks malware.
- **SSL/TLS Decryption**: Inspects encrypted traffic for threats.

> **Note**: vEdge routers include a built-in **stateful firewall** to restrict unauthorized traffic and enable security auditing.

---

## 🧩 VPN Segmentation in SD-WAN

Cisco SD-WAN uses **VPNs** (similar to VRFs) for traffic segmentation.

- **Each VPN** has a separate routing table and policy set.
- **VPN ID Range**: 0 to 65530.
  - `VPN 0`: Transport VPN for WAN links (IPsec tunnels, DTLS/TLS control connections).
  - `VPN 512`: Management VPN for out-of-band device management.
- **Independent Operation**: VPNs do not share routes unless explicitly configured (e.g., service chaining, route leaking).

---

## 🔀 VPN Topology Design

Each VPN can use a different overlay topology based on business needs:

- **Full-mesh**: All sites communicate directly. 
- **Hub-and-spoke**: Branches connect through a central hub (e.g., data center). 
- **Partial-mesh**: Some sites are interconnected, optimizing performance and cost.
- **Point-to-point**: Direct link between two specific sites.

---

## 📜 Access Control Lists (ACLs)

ACLs provide granular control over traffic.

- **Standard ACLs**: Match based on source/destination IP, protocol, ports, DSCP markings.
- **Advanced ACLs**: Match on deeper attributes like TCP flags or packet length.
- **Actions**:
  - **Permit** or **Drop** packets that meet match conditions.
  - **Log** matches for audit and troubleshooting.

> **Important**: Packets that do not match any ACL entry are **dropped by default**.

---

### 📚 Navigation
- → Next: [SD-WAN QoS and Multicast](./sd-wan-qos.md)
- ← Previous: [SD-WAN High Availability](./sd-wan-high-availability.md)
- ↩ Return to [Cisco SD-WAN](./README.md)
