# EtherChannel

EtherChannel is a Layer 2 or Layer 3 link aggregation technology that allows multiple physical links to be combined into one logical link, providing increased bandwidth and redundancy.

## Benefits
- **Increased bandwidth** by aggregating links.
- **Redundancy**: if one link fails, the others stay active.
- **Faster convergence** than STP reacting to individual link failures.
- **STP treats all links in the EtherChannel as a single logical link**, avoiding loops without blocking individual member links.

---

## Protocols

### PAgP (Port Aggregation Protocol)
- **Cisco proprietary**.
- Negotiates the EtherChannel.
- Modes:
  - **Desirable**: Actively attempts to form a channel.
  - **Auto**: Passively waits to be asked.

### LACP (Link Aggregation Control Protocol)
- **IEEE 802.3ad standard**.
- Interoperable with other vendors.
- Modes:
  - **Active**: Actively tries to form an EtherChannel.
  - **Passive**: Waits for the other side.

---

## EtherChannel Mode Combinations

| Side A    | Side B      | Result       |
| --------- | ----------- | ------------ |
| on        | on          | EtherChannel |
| on        | (any other) | Failure      |
| auto      | auto        | Failure      |
| desirable | desirable   | EtherChannel |
| auto      | desirable   | EtherChannel |
| active    | active      | EtherChannel |
| passive   | passive     | Failure      |
| active    | passive     | EtherChannel |

---

## Configuration Examples

### PAgP
```bash
interface range g1/0/1 - 2
 channel-group 1 mode desirable
```

### LACP
```bash
interface range g1/0/3 - 4
 channel-group 1 mode active
```

---

## Load Balancing
EtherChannel distributes traffic based on a hashing algorithm that can use:
- Source or destination MAC address
- Source or destination IP address
- TCP/UDP ports (if Layer 4)

### Configuration
```bash
port-channel load-balance <hash>
```

### Available <hash> options:
- `dst-ip` – Destination IP address
- `src-ip` – Source IP address
- `src-dst-ip` – Source XOR Destination IP address
- `dst-mac` – Destination MAC address
- `src-mac` – Source MAC address
- `src-dst-mac` – Source XOR Destination MAC address
- `dst-port` – Destination Layer 4 port
- `src-port` – Source Layer 4 port
- `src-dst-port` – Source XOR Destination Layer 4 port
- Others depending on platform

### Load Distribution with Odd Number of Links
Cisco’s proprietary hash algorithm balances traffic across EtherChannel members based on a modulo operation. For odd numbers of member links, the distribution might not be perfectly even:

| Number of Members | Load Balancing Between Ports |
| ----------------- | ---------------------------- |
| 8                 | 1:1:1:1:1:1:1:1              |
| 7                 | 2:1:1:1:1:1:1                |
| 6                 | 2:2:1:1:1:1                  |
| 5                 | 2:2:2:1:1                    |
| 4                 | 2:2:2:2                      |
| 3                 | 3:3:2                        |
| 2                 | 4:4                          |

---

## Troubleshooting Tips
- Ensure both sides use the same EtherChannel mode.
- Interface settings (speed, duplex, VLAN, trunking) must match.
- Use `show etherchannel summary` and `show interfaces port-channel <id>` to verify status.
- EtherChannel mismatch can cause **err-disabled** state:
  - Fix the configuration
  - Then recover the interface with:
    ```bash
    shutdown
    no shutdown
    ```

---

## Related Concepts
- Commonly used in **campus designs** to aggregate uplinks between access and distribution layers. See: [campus-design-models.md](campus-design-models.md)
- EtherChannel can be configured on **Layer 2** (switching) or **Layer 3** (routing) interfaces.

---

