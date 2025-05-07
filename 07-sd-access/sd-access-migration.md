# 🧬 Migration to Cisco SD-Access

Cisco Software-Defined Access (SD-Access) transforms traditional campus networks by abstracting control, management, and data planes into a fabric-based model. Migrating to this architecture introduces operational efficiency, enhanced segmentation, and centralized policy enforcement. However, due to the complexity and diversity of existing infrastructure, migration must be strategically planned to balance innovation with stability.

## 📘 Pre-Migration Terminology

Understanding the deployment context is essential for selecting an appropriate migration strategy:

- **Greenfield**: Refers to a completely new deployment with no legacy infrastructure. It offers the cleanest integration path for SD-Access but is less common in enterprise environments.
- **Brownfield**: Refers to an existing traditional network that needs to be integrated or gradually transitioned into the SD-Access fabric. Brownfield deployments often include older switches, mixed protocols, and complex operational requirements.

## 🚀 Approaches

### 1. 🔁 Parallel
- Build a Cisco SD-Access network next to an existing brownfield network.
- Physically patch cables to move switches from the brownfield network to the Cisco SD-Access network.
- Simplifies change management and rollback.
- Requires additional rack space, power, and cabling infrastructure.

### 2. 🧩 Incremental
- Convert traditional switches from the brownfield network to Cisco SD-Access fabric edge nodes.
- Use **Layer 2 Border handoff** for incremental migration.
- Suitable for networks with existing equipment capable of supporting Cisco SD-Access or with environmental constraints like lack of space and power.

### 3. ⚙️ Hybrid
- Combine **parallel** and **incremental** approaches.
- Example: Configure new core switches as border nodes, add and configure control plane nodes, and incrementally convert brownfield access switches to Cisco SD-Access fabric edge nodes.

## 🌐 Layer 2 Border Handoff

- Provides an **overlay service** between Cisco SD-Access and traditional networks, allowing Layer 2 communication between hosts.
- 🔒 **Dedicated Role**: Border node with Layer 2 handoff should be dedicated and not colocated with other functions.
- 🫥 **Transparent Mode**: Device must operate in transparent mode for VLAN Trunking Protocol (VTP) to avoid unintended VLAN modifications.
- 🚫 **VLAN Restrictions**:
  - Traditional network can use any VLAN **except**:
    - `1`
    - `1002–1005`
    - `2045–2047`
    - `3000–3500`
  - These are reserved in Cisco DNA Center or used for special functions in Cisco software.

---

### 📚 Navigation
- → Next: [SD-Access Multicast](sd-access-multicast.md)  
- ← Previous: [SD-Access Fabric](sd-access-fabric.md)  
- ↑ Back to: [Cisco SD-Access](README.md)
