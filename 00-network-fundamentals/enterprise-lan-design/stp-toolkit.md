# STP Toolkit and UDLD

This file covers important enhancements and complementary features to the Spanning Tree Protocol (STP), which help prevent loops, improve convergence, and detect unidirectional link failures in switched networks.

---

## PortFast

- Enables ports to transition directly to the forwarding state, bypassing STP's listening and learning states.
- Ideal for access ports connected to end devices (e.g., PCs, printers).

```bash
switch(config-if)# spanning-tree portfast
```

>[!TIP]
Enable `PortFast` only on ports connected to end devices. Never use it on trunk links or switch uplinks.

---

## BPDU Guard

- Protects the network by err-disabling a PortFast-enabled interface if a BPDU is received.
- Prevents rogue switches from being plugged into the network.

```bash
switch(config-if)# spanning-tree bpduguard enable
```

>[!NOTE]
Use BPDU Guard in combination with PortFast for better access layer protection.

---

## Root Guard

- Prevents a designated port from becoming a root port, even if it receives superior BPDUs.
- Helps enforce the intended STP topology.

```bash
switch(config-if)# spanning-tree guard root
```

>[!TIP]
Apply Root Guard on access or downstream ports to protect the root bridge election.

---

## Loop Guard

- Prevents a port from transitioning to the forwarding state if BPDUs stop being received (unlike STP which might assume the link is blocked).
- Protects against unidirectional failures or misconfigurations that may lead to loops.

```bash
switch(config-if)# spanning-tree guard loop
```

>[!NOTE]
Loop Guard is most useful on non-designated ports like root ports or alternate ports.

---

## UDLD (Unidirectional Link Detection)

- Detects unidirectional links caused by miswiring, fiber issues, or faulty transceivers.
- Shuts down affected ports to prevent loops.

### UDLD Modes

| Mode       | Description                                                                 |
| ---------- | --------------------------------------------------------------------------- |
| Normal     | Detects unidirectional links but does not shut down the port automatically. |
| Aggressive | Sends multiple UDLD messages; if no reply, it disables the port.            |

```bash
switch(config)# udld enable
switch(config)# udld aggressive
switch(config-if)# udld port aggressive
```

>[!IMPORTANT]
Aggressive mode is recommended for critical links (e.g., switch uplinks) to prevent loops caused by silent failures.

---

## Loop Guard vs UDLD

| Feature       | Loop Guard                                       | UDLD                                                   |
| ------------- | ------------------------------------------------ | ------------------------------------------------------ |
| Scope         | Layer 2 (STP-based)                              | Physical (Layer 1 and Layer 2)                         |
| Operation     | Works by monitoring BPDUs                        | Uses its own protocol to detect bidirectional failures |
| Configuration | Per-interface                                    | Global or per-interface                                |
| Port Effect   | Keeps port in loop-inconsistent (blocking) state | Disables the port                                      |
| Typical Use   | STP-enabled links                                | Fiber/copper uplinks between switches                  |

>[!TIP]
Use both tools together for maximum protection in enterprise switch environments.

---

## Troubleshooting Tip: Err-disabled Ports

If a port is err-disabled (due to BPDU Guard, UDLD, etc.):
1. Fix the underlying cause (e.g., remove rogue switch, fix cabling).
2. Re-enable the port manually:

```bash
switch(config-if)# shutdown
switch(config-if)# no shutdown
```

>[!CAUTION]
Always verify the root cause before re-enabling the port to prevent further disruptions.
