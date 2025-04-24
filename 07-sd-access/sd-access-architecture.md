### SD-Access Architecture

Cisco SD-Access is architected in layers to support a modular and scalable enterprise access network, enabling policy enforcement, segmentation, automation, and assurance.

---

#### 🧱 Architectural Layers

- **Physical Layer**: Consists of hardware infrastructure such as routers, switches, wireless APs/controllers, physical/virtual links, and server appliances.
- **Network Layer**: Composed of the underlay (IP connectivity) and overlay (VXLAN/LISP-based fabric) including the control, data, and policy planes.
- **Controller Layer**: Includes orchestration systems (like Cisco DNA Center and ISE) that automate deployment, enforce policies, and provide analytics.
- **Management Layer**: Provides interfaces for user interaction (GUI, APIs, CLI) to manage and operate the SD-Access environment.
- **Partner Ecosystem**: Integrates Cisco and third-party solutions that consume or augment SD-Access services.

---

#### 🧠 Control Plane Functions

Built on **LISP (Locator/ID Separation Protocol)**, the control plane handles endpoint tracking and forwarding decisions.

- **Host Tracking Database (HTDB)**: Centralized repository for Endpoint Identifier (EID) to fabric edge bindings.
- **Map Server**: Receives endpoint registration messages from edge nodes and updates the HTDB.
- **Map Resolver**: Answers LISP mapping queries from edge nodes, returning RLOCs (Routing Locators) for EID destinations.

---

#### 🌐 Fabric Node Roles

##### ➤ Edge Node

- Registers endpoints into the fabric
- Maps users to Virtual Networks (VN)
- Acts as an Anycast Gateway for Layer 3
- Handles LISP encapsulation/decapsulation
- Forwards traffic using VXLAN

##### ➤ Border Node

Manages communication between the fabric and external networks:

- **Internal Border Node**: Connects to known internal resources; advertises internal IP pools and imports routes.
- **External Border Node**: Connects to external destinations; advertises internal IPs but does *not* import unknown routes.
- **Internal + External Border Node**: Bridges known internal and transit networks.

**Key Border Node Functions**:
- Advertises EID subnets outside the fabric
- Acts as the exit point from the fabric domain
- Maps LISP instances to VRFs
- Applies policy translations as needed

---

### 📚 Navigation
- [➡️ 2.5 Campus Fabric Design Considerations](./campus-fabric-design.md)
- [🏠 Back to Section 02 - Campus Design](../readme.md)
- [⬅️ 2.4 SD-Access Overview](./sd-access-overview.md)

### 📚 Navigation
- → Next: [TBD](./TBD)
- ← Previous: [SD-Access Overview](./sd-access-overview.md)
- ↑ Back to: [SD-Access Index](../readme.md)

