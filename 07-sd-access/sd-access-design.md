# 🏗️ SD-Access Design

This summary outlines SD-Access design recommendations, including overlay and fabric components, control and border plane design, segmentation strategies, and wireless integration options.

---

### 🧠 Design Recommendations
- **Redundancy**: Implement redundant paths to prevent single points of failure and ensure quick recovery.
- **Load Balancing**: Utilize techniques to distribute traffic evenly across multiple paths.
- **Convergence**: Design for fast convergence times to minimize downtime.
- **Hierarchical Structure**: Use a hierarchical network design with core, distribution, and access layers.
- **Segmentation**: Segment the network to isolate different types of traffic, improving security and performance.

---

### 🎯 Practical Goal
- **Larger Fabric Sites**: Prefer larger fabric sites over multiple smaller ones unless business constraints dictate otherwise.
- **Layer 3 Routed Access**: Design edge nodes using a Layer 3 routed access model.

---

### 🕸️ Overlay Design
- **Overlay Network**: Transports all user traffic via VXLAN encapsulation; SGTs embedded for segmentation.
- **Macrosegmentation**: Group similar devices/users into Virtual Networks (VNs). Requires external devices for inter-VN routing.
- **Microsegmentation**: Uses SGTs to apply policies within a VN.
- **IP Subnet Management**: Favor larger subnets to minimize broadcast traffic; avoid overlapping subnets for services across VNs.

---

### 🧵 Fabric Design
- **Fabric Site Components**: Dedicated control, border, and edge nodes.
- **Scope**: Layer 2/3 mobility and anycast gateways are restricted to a single fabric site.
- **Isolation**: Each site operates independently from other external fabrics.

---

### 🧠 Control Plane Design
- **Endpoint ID**: Maintained by control plane nodes; local database used if CP node is down.
- **HA Strategy**: Deploy two control plane nodes for redundancy.
- **Colocation**: CP roles can exist on border nodes if they meet scale requirements.
- **Capacity**: Up to 6 control plane nodes; WLCs support communication with up to 4 CP nodes.

---

### 🌐 Border Design
- **External Routing**: Use fusion router/firewall for inter-VRF routing.
- **Shared Services**:
  - **GRT**:
    - eBGP used between border and fusion routers.
    - Routes exchanged for all VNs.
  - **Separate VRF Instances**:
    - Each VN requires separate BGP adjacencies.
    - Potential issues: SGT loss, manual configs, traffic hairpinning.

---

### 🧩 Cisco SD-Access Distributed Campus Considerations

#### 🔗 SD-Access Transit
- Connects fabric sites via Metro Ethernet or direct/leased fiber.
- Not part of the data forwarding path.
- Always deployed in pairs for HA.

#### 🧠 Transit Control Plane Nodes
- IP-reachable via IGP.
- Cannot be collocated with other fabric roles.

---

### 🔐 Segmentation
- **Unified Policy**: Enables consistent policy across wired and wireless.
- **VRF/VN Segmentation**: Extends VN info across distributed sites.
- **SGT Segmentation**: Tags endpoints for SGACL policy enforcement via ISE.

---

### 🌍 Virtual Networks (VNs)
- **Isolation**: Each VN is a separate VRF.
- **Assignment**: VN assigned via LISP.
- **Traffic**: VXLAN with VNIs; 16 million segments supported.
- **Default VN**: Used when no specific VN assigned.

---

### 📶 Over-the-Top (OTT) Wireless
- **Legacy Option**: Traditional local mode wireless deployment.
- **Traffic**: CAPWAP between APs and WLC.
- **Location**: WLC near data center or service block.

---

### 📡 Fabric Wireless
- **Best Practice**: Full integration with SD-Access fabric.
- **Security**: SGT-based policy enforcement.
- **Placement**: Local WLC per fabric site.
- **Redundancy**: Use StackWise for resilient AP uplinks.
- **INFRA VRF**: Provides GRT-based reachability for APs.

---

### 📚 Navigation
- → Next: [Cisco SD-WAN](../08-sd-wan/README.md)  
- ← Previous: [SD-Access Multicast](sd-access-multicast.md)
- ↑ Back to: [Cisco SD-Access](README.md)
