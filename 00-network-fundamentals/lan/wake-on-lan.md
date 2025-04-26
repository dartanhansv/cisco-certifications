# Wake on LAN (WoL)

**Wake on LAN (WoL)** is a Layer 2 protocol that enables remote powering-on of devices for maintenance or updates, even if they’re in a sleep or powered-off state—provided the NIC remains active.

---

## 🔧 How It Works

- **NIC Power Retention**: The NIC remains powered even when the computer is off, listening for specific traffic.
- **Magic Packets**: WoL works by sending a specially formatted frame called a *magic packet*—containing the target device’s MAC address repeated several times.
- **Directed Broadcasts**: When sending WoL packets from different subnets, routers must support and permit directed broadcasts to reach the target device.

---

## ✅ Benefits

- **Remote Administration**: Useful for off-hours updates and management without physical access.
- **Energy Savings**: Devices can stay powered off until actually needed.
- **Reduced Downtime**: Enables systems to be quickly brought online for scheduled jobs or remote troubleshooting.

---

## ⚙️ Configuration Tips

### On End Devices:
- Enable WoL in BIOS/UEFI and operating system.
- Configure NIC settings to allow WoL and keep power during sleep/shutdown.

### On Network Infrastructure:
- **Switch**: No special config unless port security or PoE settings interfere with NIC behavior.
- **Router** (if remote WoL):
  - Allow directed broadcasts.
  - Consider security implications of allowing such traffic.
  - Use access control to restrict who can send WoL packets.

> [!NOTE]  
> WoL packets are typically sent over UDP port **9** or **7**, but the protocol itself doesn't require a specific port.
