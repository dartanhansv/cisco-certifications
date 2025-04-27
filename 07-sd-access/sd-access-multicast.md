# 🧠 SD-Access Multicast

This summary outlines multicast support within Cisco SD-Access, focusing on headend replication, multicast routing protocols, and design considerations for both internal and external multicast sources.

### 📡 Headend Replication
- **Earlier Versions**: Headend replication of multicast packets into the fabric was standard, requiring the border to receive and replicate all multicast packets from edge switches.
- **Recent Versions**: Multicast features can be configured manually within fabric switches or through LAN automation, reducing headend replication overhead on border switches.

### 🌐 Multicast Support
- **Sources**: Multicast sources can be supported both inside and outside the SD-Access fabric.
- **PIM Implementations**: A rendezvous point (RP) is used on the border for all multicast clients in the overlay. Multicast protocol configurations can be done within Cisco DNA Center.
- **Protocols**: Both PIM Source-Specific Multicast (SSM) and PIM–Sparse Mode are supported with SD-Access.
- **RP Requirement**: When IP multicast is used in the overlay, an RP is required.
- **MSDP for RP Redundancy**: Multicast Source Discovery Protocol (MSDP) can be used for RP redundancy if desired.

---

### 📚 Navigation
- → Next: [SD-Access Design](sd-access-design.md)
- ← Previous: [Migration to Cisco SD-Access](./sd-access-migration.md)
- ↑ Back to: [Cisco SD-Access](README.md)
