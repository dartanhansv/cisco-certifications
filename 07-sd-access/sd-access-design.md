# 🏗️ SD-Access Design

SD-Access provides a **software-defined networking architecture** for enterprises, enabling **automation, segmentation, and centralized policy enforcement**. This document outlines key design recommendations for **fabric sites, control and border plane configuration, segmentation strategies, and wireless integration**.


## 🧠 Design Recommendations
- **Redundancy** – Implement redundant paths to prevent single points of failure and ensure quick recovery.
- **Load Balancing** – Utilize techniques to distribute traffic evenly across multiple paths.
- **Convergence** – Design for fast convergence times to minimize downtime.
- **Hierarchical Structure** – Use a hierarchical network design with **core, distribution, and access layers**.
- **Segmentation** – Apply **macrosegmentation and microsegmentation** strategies to **enhance security and optimize traffic flow**.


## 🎯 Practical Goals
- **Larger Fabric Sites** – Prefer larger fabric sites over multiple smaller ones unless business constraints dictate otherwise.
- **Layer 3 Routed Access** – Design edge nodes using a **Layer 3 routed access model** for efficient routing.


## 🕸️ Overlay Design
- **Overlay Network** – Transports user traffic via **VXLAN encapsulation**, embedding **SGTs for segmentation**.
- **IP Subnet Management** – Favor **larger subnets** to minimize broadcast traffic; avoid **overlapping subnets** when shared services require **inter-VN communication**.


## 🧵 Fabric Design
- **Fabric Site Components** – Dedicated **control, border, and edge nodes**.
- **Layer 2/3 Mobility** – Mobility and **anycast gateways** operate **within a single fabric site**.
- **Isolation** – Each fabric site operates **independently** from external networks.


## 🧠 Control Plane Design
- **Endpoint ID Management** – Control plane nodes maintain **endpoint database**; local cache used if CP nodes fail.
- **High Availability Strategy** – Deploy **two control plane nodes** for redundancy.
- **Colocation Considerations** – Control plane roles can exist on **border nodes**, provided they meet **scale requirements**.
- **Capacity** – Up to **six control plane nodes**; **wireless controllers (WLCs) support connectivity with up to four CP nodes**.


## 🌐 Border Design
- **External Routing** – Use **fusion routers/firewalls** for inter-VRF routing.
- **Shared Services**:
  - **Global Routing Table (GRT)** –  
    - eBGP connectivity between **border** and **fusion routers** for VN route exchange.  
  - **Separate VRF Instances** –  
    - Each VN requires **individual BGP adjacencies**.  
    - Possible issues: **SGT loss, manual configuration complexities, traffic hairpinning**.


## 🏙️ Cisco SD-Access Distributed Campus Considerations

### 🔗 SD-Access Transit
- Connects **fabric sites** via **Metro Ethernet or direct/leased fiber**.
- **Not part of the data forwarding path**.
- Always **deployed in pairs for HA**.

### 🧠 Transit Control Plane Nodes
- Must be **IP-reachable via IGP**.
- **Cannot be collocated** with other fabric roles.


## 🔐 Segmentation

SD-Access segmentation improves **security**, **policy enforcement**, and **network isolation** through two approaches: **macrosegmentation** and **microsegmentation**.

### 🏛️ Macrosegmentation (VN-Based Segmentation)
Macrosegmentation groups **similar devices and users** into **Virtual Networks (VNs)**, offering **path isolation across control and data planes**.

#### **Characteristics**
- Uses **VRFs** to create **separate network segments**, preventing **cross-VN communication**.
- Requires **fusion routers or firewalls** for **inter-VN traffic exchange**.
- **Ideal for broad segmentation**, such as isolating **guest networks, IoT devices, and corporate traffic**.

#### **Key Considerations**
- **Inter-VN Communication Requires External Devices**
  - Traffic between VNs must pass through **firewalls or fusion routers** for security enforcement.  
- **Avoid Overlapping IP Subnets**
  - While multiple VNs allow **overlapping subnets**, shared services often require **inter-VN communication**, making subnet uniqueness preferable.


### 🧩 Microsegmentation (SGT-Based Segmentation)
Microsegmentation enables **fine-grained access control within a VN**, using **Scalable Group Tags (SGTs)** to enforce **policy-based isolation** at the **data plane level**.

#### **Characteristics**
- **SGT-based segmentation** allows **policy enforcement within a VN**, eliminating dependency on **external routing devices**.
- **Larger IP subnets are viable**, since **broadcast flooding issues** common in large Layer 2 networks are **mitigated** via SGT-based isolation.  
- **Simplifies IP addressing**, reducing **DHCP scopes** and minimizing **manual subnet planning**.  

#### **Key Benefits**
- **Policy enforcement without VRFs** – Traffic segmentation is handled **locally within the VN** instead of requiring **external devices**.
- **Reduced IP complexity** – Microsegmentation **allows larger subnets**, simplifying **IP address management** for SD-Access.
- **More flexible segmentation** – Security policies can be **dynamically assigned** to endpoints **without changing network topology**.


## 🏆 Segmentation Design Recommendations
- **Macrosegmentation** should be used for **broad isolation** between distinct **network types** (e.g., guest vs. enterprise traffic).
- **Microsegmentation** should be used for **granular policy control** within a VN, limiting **endpoint communication based on security roles**.
- **Avoid Overlapping Subnets**
  - While **VNs support overlapping IP subnets**, this should be **minimized** to ensure **shared service accessibility across VNs**.


## 🌍 Virtual Networks (VNs)
- **Isolation** – Each VN operates as a **separate VRF**.
- **Assignment** – VN **assigned via LISP** for endpoint mobility.
- **Traffic Forwarding** – VXLAN encapsulation with **VNIs (Virtual Network Identifiers)**; **supports up to 16 million segments**.
- **Default VN** – Used when **no specific VN is assigned**.


## 📶 Over-the-Top (OTT) Wireless
- **Legacy Option** – Traditional **local mode wireless deployment**.
- **Traffic Transport** – CAPWAP tunneling between APs and WLC.
- **Location Strategy** – WLC placement **near data center or service block**.


## 📡 Fabric Wireless
- **Best Practice** – Full wireless integration with **SD-Access fabric**.
- **Security** – **SGT-based policy enforcement** for consistent **wired/wireless segmentation**.
- **Placement Strategy** – **Local WLC** per fabric site.
- **Redundancy** – Use **StackWise** for **resilient AP uplinks**.
- **Infrastructure VRF (INFRA)** – Provides **GRT-based reachability** for APs.

---
### 📚 Navigation
- → Next: [SD-Access Security](./sd-access-security.md)  
- ← Previous: [SD-Access Multicast](sd-access-multicast.md)
- ↩ Return to: [SD-Access - Index](README.md)
