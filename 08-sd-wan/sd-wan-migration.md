# 🛣️ SD-WAN Migration Strategy

Migrating from a traditional WAN to Cisco SD-WAN can be seamless and minimally disruptive if planned carefully.  
A successful migration strategy focuses on maintaining service continuity, leveraging existing investments, and gradually adopting the benefits of SD-WAN.

---

## 🔄 Common Migration Phases

1. **Parallel Installation**
   - Deploy the SD-WAN overlay network alongside the existing WAN infrastructure.
   - Existing MPLS or Internet links can initially carry both legacy and SD-WAN traffic.
   - Devices like vEdge or cEdge routers are added without immediately replacing the legacy WAN.

2. **Hybrid Transport Leverage**
   - **MPLS links** are kept intact while the SD-WAN fabric uses both MPLS and Internet transports.
   - Tunnels (IPSec over MPLS and Internet) are established between SD-WAN edge devices.
   - This hybrid approach allows validation and optimization of SD-WAN policies while retaining the old WAN for critical traffic.

3. **Full Transition**
   - Gradual phasing out of legacy MPLS routers as confidence in SD-WAN grows.
   - SD-WAN fabric eventually handles all transport needs, replacing traditional WAN architectures.
   - At this stage, transport redundancy (dual Internet/MPLS links) and headend redundancy (multiple hubs) should be fully operational.

---

## 🧠 Key Design Considerations

- **Minimal Disruption**: Migrations often start with pilot sites before scaling network-wide.
- **Staging and Testing**: Carefully test routing, failover, and policy enforcement before cutting over production traffic.
- **Security Readiness**: Ensure security policies (e.g., segmentation, encryption) are ready from Day 1.
- **Coexistence Planning**: Sometimes legacy WAN and SD-WAN coexist permanently in large enterprises.

---

# 📚 Navigation
- → Next: [TD](TD)  
- ← Previous: [TD](TD)  
- ↑ Back to: [TD](TD)
