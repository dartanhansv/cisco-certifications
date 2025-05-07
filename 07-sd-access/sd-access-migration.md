# 🧠 SD-Access Multicast

[Multicast](../../01-routing-protocols/multicast/multicast-overview.md) in Cisco SD-Access enables efficient distribution of data streams such as video, telemetry, or voice traffic within the fabric. Instead of relying on traditional replication mechanisms, **SD-Access integrates multicast natively into the overlay** using control-plane separation and fabric roles. This ensures scalable, policy-driven multicast delivery across virtualized segments and between legacy and fabric networks.


---

## 📡 Headend Replication

- **Earlier Versions**: Headend replication of multicast packets into the fabric was standard, requiring the border to receive and replicate all multicast packets from edge switches.
- **Recent Versions**: Multicast features can be configured manually within fabric switches or through LAN automation, reducing headend replication overhead on border switches.

## 🌐 Multicast Support

- **Sources**: Multicast sources can exist both inside and outside the SD-Access fabric.
- **PIM Implementations**:
  - [PIM](../../01-routing-protocols/multicast/pim.md) Sparse Mode (PIM-SM) and PIM Source-Specific Multicast (PIM-SSM) are supported.
  - A **Rendezvous Point (RP)** is required for PIM-SM.
  - **PIM-SSM does not use an RP**, relying instead on direct (S,G) joins.
- **Overlay Requirement**: When multicast is enabled in the fabric overlay, an RP is required (only for PIM-SM).
- **RP Redundancy**: Multicast Source Discovery Protocol (MSDP) can be used to support RP redundancy across borders.
- **Configuration**: Multicast routing and RP settings can be deployed manually or automated via Cisco DNA Center.

---

### 📚 Navigation
- → Next: [SD-Access Design](sd-access-design.md)  
- ← Previous: [Migration to Cisco SD-Access](./sd-access-migration.md)  
- ↑ Back to: [Cisco SD-Access](README.md)
