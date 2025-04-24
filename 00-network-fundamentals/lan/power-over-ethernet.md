# Power over Ethernet (PoE)

**Power over Ethernet (PoE)** allows network cables to carry electrical power, simplifying deployments of devices such as IP phones, wireless access points (APs), and cameras.

---

## PoE Standards

| Standard     | IEEE    | Max Power to Device             | Voltage  | Max Cable Distance |
| ------------ | ------- | ------------------------------- | -------- | ------------------ |
| PoE          | 802.3af | 15.4 W                          | ~48 V    | 100 m              |
| PoE+         | 802.3at | 25.5 W                          | ~50-57 V | 100 m              |
| UPoE (Cisco) | -       | 60 W                            | ~50-57 V | 100 m              |
| PoE++        | 802.3bt | 60 W (Type 3)<br>100 W (Type 4) | ~50-57 V | 100 m              |

> *Note: Actual delivered power may be slightly less due to cable loss.*

---

## PoE Operation

- A device providing power is called a **Power Sourcing Equipment (PSE)**.
- A device receiving power is called a **Powered Device (PD)**.

### PoE Detection and Negotiation

PSE detects PD using:
- **Passive Detection**: Sends a small voltage to check for a valid signature resistor.
- **Active Negotiation (PoE+/PoE++)**:
  - **LLDP** (Link Layer Discovery Protocol) used for power negotiation.
  - Allows dynamic adjustment of power based on PD requirements.

---

## PoE Power Management

- PoE is managed per **interface**, **class**, or **device**.
- Power classes (0-8) define max power levels:

| Class | Max Power (W) |
| ----- | ------------- |
| 0     | 15.4          |
| 1     | 4.0           |
| 2     | 7.0           |
| 3     | 15.4          |
| 4     | 30.0          |
| 5     | 45.0          |
| 6     | 60.0          |
| 7     | 75.0          |
| 8     | 90.0          |

---

## Power Policing

- Prevents devices from drawing more power than negotiated.
- Actions include: **log**, **err-disable**, or **power cut-off**.

```bash
Switch(config-if)# power inline police
```

---

## PoE Troubleshooting Tips

- Verify power availability:
  ```bash
  show power inline
  ```
- Check for power policing status:
  ```bash
  show power inline police
  ```
- If an interface is in **err-disabled** due to power, fix the issue and:
  ```bash
  interface X
  shutdown
  no shutdown
  ```

---

