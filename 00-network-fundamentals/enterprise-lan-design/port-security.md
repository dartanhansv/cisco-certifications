# Port Security

**Port Security** is a Layer 2 security feature that restricts input to an interface by limiting and identifying MAC addresses of the workstations allowed to access the port.

It's primarily configured on **access ports** to prevent unauthorized devices from connecting to the network.

---

## Key Concepts

- **Static secure MAC address**: Manually configured and stored in the running config.
- **Dynamic secure MAC address**: Learned dynamically and lost on reboot.
- **Sticky secure MAC address**: Learned dynamically and saved in the running config (can be saved to startup config).

---

## Configuration Example

```bash
interface FastEthernet0/1
 switchport mode access
 switchport port-security
 switchport port-security maximum 2
 switchport port-security violation restrict
 switchport port-security mac-address sticky
```

- `maximum 2`: Only 2 MAC addresses are allowed.
- `violation restrict`: Packets from unknown MACs are dropped and a log is generated.
- `mac-address sticky`: Allows the switch to dynamically learn MAC addresses and add them to the running configuration.

---

## Violation Modes

| Mode         | Action                                                            |
| ------------ | ----------------------------------------------------------------- |
| **Protect**  | Discards offending traffic silently.                              |
| **Restrict** | Discards traffic and generates log/SNMP traps.                    |
| **Shutdown** | Puts the port into err-disabled state and sends an SNMP trap/log. |

> **Note**: `shutdown` is the default violation mode.

---

## Show Commands

```bash
show port-security interface Fa0/1
show port-security address
```

---

## Recovery from Violation

If the port goes into **err-disabled** state due to a violation (e.g., `shutdown` mode):

```bash
interface FastEthernet0/1
 shutdown
 no shutdown
```

> Optionally, configure **errdisable recovery** globally:

```bash
errdisable recovery cause psecure-violation
errdisable recovery interval 300
```

---

## Best Practices

- Use sticky MACs for ease of configuration with a touch of persistence.
- Always monitor violation counts and logs.
- Use with other Layer 2 security features like DHCP Snooping, DAI, etc.

---

