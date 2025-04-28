# 🌐 Direct Internet Access (DIA) and Security in Cisco SD-WAN

In a traditional WAN, Internet traffic is typically backhauled to a central data center, causing delays and wasting bandwidth.  
Cisco SD-WAN enables local Internet breakout (DIA), improving efficiency, performance, and security at remote sites.

---

## 🚀 Direct Internet Access (DIA)

- **Routing**: Internet-bound or public cloud traffic from branch sites is routed directly to the Internet, bypassing the data center.
- **Benefits**:
  - Reduced private WAN bandwidth consumption.
  - Lower latency and faster access to Internet-based resources.
  - Cost savings by offloading Internet traffic from MPLS circuits.
- **Improved User Experience**:
  - Branch employees experience better connectivity to SaaS applications like Office 365, Salesforce, and Webex.
- **IP NAT**:
  - NAT is configured on the Internet-facing interface for private-to-public IP translation.

---

## 🛡️ Security Design in SD-WAN

Cisco SD-WAN offers multiple security services across on-premises and cloud-hosted options:

### 🔒 Core Security Categories
1. **Network Segmentation**: Traffic isolation using VPNs.
2. **Enterprise Firewall**: Stateful firewall policies applied at the branch.
3. **Secure Web Gateway**: Filters malicious web content.
4. **DNS-layer Security**: Blocks requests to known malicious domains.

### 🛡️ Security Features
- **IPsec Encryption**: Secures data plane tunnels across transports.
- **Intrusion Prevention System (IPS)**: Detects and blocks threats.
- **Application Controls**: Enforces application usage policies.
- **Malware Protection**: Scans for and blocks malware.
- **SSL/TLS Decryption**: Inspects encrypted traffic for threats.

> **Note**: vEdge routers come with a built-in **stateful firewall** to restrict unauthorized traffic and enable security auditing.

---

## 🧩 VPN Segmentation in SD-WAN

In Cisco SD-WAN, **VPNs** provide logical traffic separation similar to VRFs:

- **Each VPN** has a separate routing table and policy set.
- **VPN ID Range**: 0 to 65530.
  - `VPN 0`: Transport VPN for WAN links (IPsec tunnels, DTLS/TLS control connections).
  - `VPN 512`: Management VPN for out-of-band device management.
- **Independent Operation**:
  - VPNs do not share routes unless explicitly configured (e.g., service chaining).

---

## 🔀 VPN Topology Design

Depending on business needs, each VPN can have a different overlay topology:

- **Full-mesh**: Every site communicates directly with others.
- **Hub-and-spoke**: Branch sites communicate through a central hub (e.g., a data center).
- **Partial-mesh**: Some sites are interconnected, optimizing performance and cost.
- **Point-to-point**: Direct link between two specific sites.

---

## 📜 Access Control Lists (ACLs)

ACLs are used to define fine-grained security and traffic control:

- **Standard ACLs**:
  - Match based on source/destination IP, protocol, ports, DSCP markings.
- **Advanced ACLs**:
  - Match using deeper packet attributes like packet length, TCP flags, etc.
- **Actions**:
  - **Permit** or **Drop** packets based on match conditions.
  - **Log** matches for audit and troubleshooting.

> **Important**: Unmatched packets are **dropped** by default.

---

# 📚 Navigation
- → Next: [TD](TD)  
- ← Previous: [TD](TD)  
- ↑ Back to: [TD](TD)
