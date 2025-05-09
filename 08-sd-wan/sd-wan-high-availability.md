# 🔄 High Availability and Redundancy

Cisco SD-WAN offers several solutions to ensure high availability and redundancy, categorized into:

- Site Redundancy
- Transport Redundancy
- Network/Headend Redundancy
- Controller Redundancy

---

## 🏠 Site Redundancy

Ensures continued operation at the branch site if a vEdge (or cEdge) router fails.

- **VRRP (Virtual Router Redundancy Protocol)**:  
  Common in Layer 2 LANs. Provides failover by dynamically shifting the default gateway to a backup router.

- **Layer 3 Routing**:  
  Used in Layer 3 LAN designs - Layer 3 switches or routers.
  Redundancy is achieved through routing protocol convergence when a router failure occurs.

**Example**  
At a branch with two vEdge routers, if the primary fails:
- In a Layer 2 LAN, VRRP shifts the default gateway to the standby router.
- In a Layer 3 LAN, routing protocols like OSPF or BGP reroute traffic to the working router.

---

## 🌐 Transport Redundancy

Protects against WAN link failures by switching traffic to a backup transport.

**Example**  
A site connected via both MPLS and Internet:
- If the MPLS link fails, SD-WAN automatically reroutes traffic over the Internet.
- Traffic engineering policies can prioritize certain applications during the failover.

This ensures uninterrupted connectivity.

---

## 🏢 Network/Headend Redundancy

Maintains connectivity between branch sites and data center hubs or regional headends.

**Example**  
If the primary headend vEdge router at the data center becomes unreachable:
- Branch vEdge routers automatically reconnect to the secondary headend router.
- This seamless handover prevents service disruption at the branch.
---

## 🧠 Controller Redundancy

Redundancy at the control plane level ensures centralized functions remain operational even if a component fails.

- **vSmart**: Multiple vSmart controllers ensure policy and routing updates continue.
- **vBond**: Redundant vBond orchestrators help new edge devices join the network.
- **vManage**: Clustering or backup of vManage ensures GUI/API-based management remains available.

---

<!-- Add diagrams for dual vEdge site, dual transport, and headend redundancy. -->

---

### 📚 Navigation
- → Next: [SD-WAN QoS and Multicast](./sd-wan-qos.md)
- ← Previous: [SD-WAN Migration](./sd-wan-migration.md)
- ↩ Return to [Cisco SD-WAN](./README.md)