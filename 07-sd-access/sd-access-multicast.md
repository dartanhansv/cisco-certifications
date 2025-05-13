# 🧠 SD-Access Multicast


Multicast is essential for **efficient content distribution**, reducing bandwidth consumption by delivering data **simultaneously** to multiple recipients. In **Cisco SD-Access**, multicast operates within the **overlay**, leveraging **Locator/ID Separation Protocol (LISP)** instead of traditional **underlay multicast routing**.

Unlike legacy multicast architectures that rely on **PIM throughout the network**, SD-Access uses **headend replication** for earlier versions and **overlay multicast routing for newer implementations**. The SD-Access fabric **does not rely on PIM for internal multicast forwarding**, but it **supports PIM at the border** for external multicast integration.



## 📡 Multicast Transport in SD-Access
- **Overlay-Based Multicast**:  
  Multicast traffic flows **within the overlay (EID space)**, covering both **wired and wireless endpoints**.
- **LISP-Based Control Plane**:  
  The fabric uses **LISP replication mechanisms** instead of traditional **PIM-based multicast routing**.
- **No PIM Inside the Fabric**:  
  Unlike conventional network designs, **SD-Access does not run PIM within the fabric**—multicast forwarding is handled **through LISP and internal replication mechanisms**.



## 🔄 Headend Replication vs. Optimized Multicast
- **Earlier SD-Access Versions**:  
  Relied on **headend replication**, where the **border node** duplicated incoming multicast streams for edge switches.
- **Newer SD-Access Versions**:  
  Support **native overlay multicast**, configurable via **manual settings or LAN automation** in **Cisco DNA Center**.  
  - **Optimized multicast replication** reduces processing overhead on border devices.  
  - **Fabric switches actively manage multicast groups**, minimizing unnecessary packet duplication.



## 🌐 Multicast Support and External Sources
- **Internal Multicast Sources**:  
  Both **multicast sources and clients typically reside in the overlay**.
- **External Multicast Sources**:  
  When multicast sources exist **outside the SD-Access fabric**, the **border node** acts as a **gateway**, integrating external multicast streams into SD-Access.
- **PIM at the Border**:  
  - **PIM-SM and PIM-SSM are supported** at the border to interact with external multicast domains.  
  - **A border RP is required** when IP multicast is used externally.
- **MSDP for RP Redundancy**:  
  **Multicast Source Discovery Protocol (MSDP)** enables RP redundancy across multiple domains, ensuring **high availability** for interdomain multicast groups.


---
### 📚 Navigation
- → Next: [SD-Access Design](sd-access-design.md)
- ← Previous: [Migration to Cisco SD-Access](./sd-access-migration.md)
- ↑ Back to: [Cisco SD-Access](README.md)
