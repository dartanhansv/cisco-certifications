# 🛣️ SD-WAN Migration Strategy

Migrating from a traditional WAN to Cisco SD-WAN can be seamless and minimally disruptive if planned carefully.  
A successful migration strategy focuses on maintaining service continuity, leveraging existing investments, and gradually adopting the benefits of SD-WAN.

---

## 🔄 Common Migration Phases

1. **Parallel Installation**
   - Deploy the SD-WAN overlay network alongside the existing WAN infrastructure.
   - Existing MPLS or Internet links can initially carry both legacy and SD-WAN traffic.
   - Devices like vEdge or cEdge routers are deployed without immediately replacing the legacy WAN routers.

2. **Hybrid Transport Leverage**
   - **MPLS links** are kept intact while the SD-WAN fabric uses both MPLS and Internet transports.
   - Tunnels (IPSec over MPLS and Internet) are established between SD-WAN edge devices.
   - This phase enables validation of routing, policy enforcement, and performance while still relying on the legacy WAN for critical services.
   - **Application-aware routing** and **traffic engineering** can be introduced through centralized policies.


3. **Full Transition**
   - Gradual phasing out of legacy MPLS routers as confidence in SD-WAN grows.
   - SD-WAN fabric eventually handles all transport needs, replacing traditional WAN architectures.
   - At this point, transport independence becomes a key benefit—Internet, MPLS, LTE, or any IP transport can be used.
   - Redundancy for both **transport (dual links)** and **headend (multiple hubs)** should be in place.
---

## 🧠 Key Design Considerations

- **Minimal Disruption**: Migrations often start with pilot sites before scaling network-wide.
- **Staging and Testing**: Carefully test routing, failover, and policy enforcement before cutting over production traffic.
- **Security Readiness**: Ensure security policies (e.g., segmentation, encryption) are ready from Day 1.
- **Coexistence Planning**: In some large enterprises, SD-WAN and legacy WAN may permanently coexist.

---

### 📚 Navigation
- → Next: [SD-WAN High Availability](./sd-wan-high-availability.md)
- ← Previous: [SD-WAN LAN Design](./sd-wan-lan.md)
- ↩ Return to [Cisco SD-WAN](./README.md)
