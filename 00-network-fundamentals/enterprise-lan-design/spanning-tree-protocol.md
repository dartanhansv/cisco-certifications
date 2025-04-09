# Spanning Tree Protocol (STP)

The **Spanning Tree Protocol (STP)** prevents **Layer 2 loops** in a switched network by creating a loop-free logical topology. It elects a **root bridge** and selectively blocks redundant paths.

---

## STP Operation Overview

1. **Bridge ID (BID)**: Composed of priority (default: 32768) + MAC address.
2. **Root Bridge Election**:
   - Switch with the **lowest BID** becomes the **Root Bridge**.
3. **Path Cost Calculation**:
   - Each switch calculates cost to reach the Root Bridge.
   - Cost is based on link speed (e.g., 100 Mbps = 19, 1 Gbps = 4).
4. **Port Roles**:
   - **Root Port (RP)**: Best path toward the Root Bridge.
   - **Designated Port (DP)**: Best forwarding port on a segment.
   - **Blocked Port**: Alternate path to prevent loops.

---

## STP Timers

| Timer         | Default Value | Purpose                           |
| ------------- | ------------- | --------------------------------- |
| Hello Time    | 2 seconds     | Interval between BPDUs from root  |
| Forward Delay | 15 seconds    | Listening/Learning state duration |
| Max Age       | 20 seconds    | Time before removing stale BPDUs  |

---

## STP States

1. **Blocking**: Receives BPDUs, does not forward.
2. **Listening**: Participates in BPDU exchanges.
3. **Learning**: Learns MAC addresses, no forwarding.
4. **Forwarding**: Sends and receives user data.
5. **Disabled**: Administratively shut down.

---

## STP Types

| Type            | Description                                                                 |
| --------------- | --------------------------------------------------------------------------- |
| **STP**         | Original IEEE 802.1D. Slow convergence (30-50 seconds).                     |
| **RSTP**        | IEEE 802.1w. Faster convergence (~5 seconds). Backward-compatible with STP. |
| **MST**         | IEEE 802.1s. Multiple VLANs mapped to a single STP instance.                |
| **PVST+**       | Cisco proprietary. One STP instance per VLAN.                               |
| **Rapid PVST+** | Cisco proprietary. Combines RSTP fast convergence with per-VLAN logic.      |

> [!NOTE] 
Cisco exams may refer to both IEEE and Cisco-proprietary versions.

---

## Convergence and Topology Changes

- Triggered by link failures, switch reboots, or path changes.
- When a topology change occurs:
  - **TCN BPDU** is sent upstream to the root bridge.
  - Root bridge sets the **TC flag** in Hello BPDUs for 35 seconds.
  - All switches age out CAM table entries after **Forward Delay** (15s).

>[!TIP]
RSTP uses rapid transition to immediately put edge ports into forwarding state (e.g., using PortFast).

---

## Loop Prevention vs Loop Recovery

| Feature         | Purpose         | Mechanism                      |
| --------------- | --------------- | ------------------------------ |
| STP             | Loop Prevention | Blocks redundant paths         |
| Flex Links, REP | Loop Recovery   | Enables alternate active paths |

---

## Related Concepts

- [STP Toolkit and UDLD](stp-toolkit-and-udld.md)
- [EtherChannel](etherchannel.md): STP sees an EtherChannel as a single logical link
- [VLAN Design](vlan-design.md): PVST+ creates a tree per VLAN

---

[TBD – STP diagram showing Root Bridge, Root/Designated/Blocked Ports]
