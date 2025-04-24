## Layer 2 Security 

Cisco offers several Layer 2 security technologies to protect network infrastructure from various attacks. These include:

---

### 1. [STP Security](stp-toolkit.md)

- **BPDU Guard**: Disables ports receiving unauthorized BPDUs.
- **Root Guard**: Prevents unauthorized switches from becoming the root bridge.
- **Loop Guard**: Detects and prevents network loops.

---

### 2. [Port Security](port-security.md)

- **Static MAC Address**: Binds a device's MAC address to a port.
- **Sticky MAC Address**: Dynamically learns and saves a device's MAC address to a port.
- **MAC Address Limit**: Limits the number of MAC addresses per port.
- **Port Security Age Time**: Specifies how long MAC addresses are secured on a port.

---

### 3. VACL Security

- **VLAN Access Lists and Maps**: Filters traffic based on VLANs, providing granular control over traffic and protecting against attacks like:
  - MAC flooding
  - VLAN hopping
  - DHCP spoofing
