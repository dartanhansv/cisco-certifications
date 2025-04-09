# VLAN Design Models

VLANs (Virtual LANs) allow network segmentation at Layer 2, enabling logical groupings of users and devices regardless of physical location. Good VLAN design improves manageability, scalability, and security.

---

## End-to-End VLAN Design

- **Same VLAN spans multiple switches across the campus.**
- Users remain in the same VLAN regardless of their location.
- Traffic between users in the same VLAN remains at Layer 2.
- Requires trunk links across the access and distribution layers.

### Pros:
- Simplifies resource access for roaming users.
- Centralized VLAN management.
- May reduce need for Layer 3 routing.

### Cons:
- Large failure domain (spanning-tree, broadcast storms).
- Harder to implement security and QoS policies.
- Sub-optimal traffic paths ("traffic tromboning").
- Poor scalability.

> [!NOTE]
> Cisco recommends avoiding end-to-end VLANs in most modern campus designs.

---

## Local VLAN Design

- **VLANs are local to access/distribution blocks.**
- Routing is required for inter-VLAN communication.
- Traffic stays localized and routed at the distribution layer.
- Does **not** require VLANs to be trunked across the entire campus.

### Pros:
- Improved scalability and fault isolation.
- Easier to implement security and QoS.
- Reduces Layer 2 loop domains and STP complexity.
- Optimal routing paths (traffic stays local).

### Cons:
- Slightly more complex to manage routing.
- Roaming users may need readdressing or additional mobility services.

> [!TIP]
> This is the **recommended design** for most enterprise networks today.

#### [TBD](diagram-path): Diagram showing End-to-End vs Local VLAN topology
---

## Voice and Data VLANs

It is common to configure **two VLANs per access port** when connecting IP phones:

- **Voice VLAN**: Dedicated VLAN for voice traffic.
- **Data VLAN**: Used by the workstation or computer connected through the phone.

This ensures:
- Proper traffic separation
- Easier QoS classification (e.g., marking voice traffic for priority treatment)

Example config:
```bash
interface FastEthernet0/1
  switchport mode access
  switchport access vlan 10
  switchport voice vlan 20
```

---

## General VLAN Design Best Practices

- Use **local VLANs** per access block whenever possible.
- Avoid spanning VLANs across distribution blocks.
- Keep VLANs confined to small areas to reduce STP scope.
- Assign meaningful VLAN IDs and names.
- Document VLAN usage and IP addressing schemes.
- Use dynamic VLAN assignment (e.g., with 802.1X) when needed.

---



