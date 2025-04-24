### SD-Access Fabric Design

**Fabric Models**: SD-Access fabric design revolves around scaling the architecture to fit various deployment sizes, from **Fabric-in-a-Box (FiaB)** sites to **large enterprise campuses**. The design must ensure flexibility, resilience, and scalability to support wired and wireless access.

#### Reference Model Templates

- **Fabric in a Box (FiaB) Site**:
  - **Coverage**: Single fabric site.
  - **Capacity**: <200 endpoints, 5 VNs, 40 APs.
  - **Design**: All fabric functions (border, control plane, edge, and wireless) colocated on a single redundant platform (e.g., StackWise Virtual).
  - **Wireless**: SD-Access Embedded Wireless for site-local WLC functionality.
  - **Considerations**:
    - High availability via StackWise-480 or StackWise Virtual.
    - Site-local services for resiliency (e.g., DHCP, DNS, WLCs, ISE).

- **Very Small Site**:
  - **Coverage**: Single office or building.
  - **Capacity**: <2,000 endpoints, 8 VNs, 100 APs.
  - **Design**: Border colocated with control plane on 1-2 devices, embedded wireless or hardware WLCs.
  - **Considerations**:
    - Two-tier collapsed core/distribution with access layer servicing several wiring closets.
    - Dedicated edge node devices.

- **Small Site**:
  - **Coverage**: Single office or building.
  - **Capacity**: <10,000 endpoints, 32 VNs, 200 APs.
  - **Design**: Border colocated with control plane, separate wireless controller.
  - **Considerations**:
    - Two-tier design, high availability with colocated core switches.
    - Dedicated WLC required.

- **Medium Site**:
  - **Coverage**: Building with multiple wiring closets or multiple buildings.
  - **Capacity**: <25,000 endpoints, 50 VNs, 1,000 APs.
  - **Design**: Distributed border from control plane using redundant devices, separate WLCs.
  - **Considerations**:
    - Three-tier design.
    - Dedicated devices for border and control plane nodes.
    - At least 2 dedicated WLCs.

- **Large Site**:
  - **Coverage**: Large building with multiple wiring closets or multiple buildings.
  - **Capacity**: <50,000 endpoints, 64 VNs, 2,000 APs.
  - **Design**: Multiple border exits, distributed control plane on redundant devices, separate wireless controller.
  - **Considerations**:
    - Typically used for headquarters or large multi-fabric sites.
    - Redundant pairs for control plane and border nodes.

---

### 📚 Navigation
- → Next: [SD-Access Design](./sd-access-design.md)
- ← Previous: [SD-Access Architecture](./sd-access-architecture.md)
- ↑ Back to: [SD-Access Overview](./sd-access-overview.md)
