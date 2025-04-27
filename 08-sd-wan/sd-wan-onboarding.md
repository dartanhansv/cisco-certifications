# SD-WAN Onboarding

### Onboarding and Provisioning

Onboarding Methods  
vEdge devices can be onboarded using:

- **Zero Touch Provisioning (ZTP)**
- **Manual Configuration**

---

## Zero Touch Provisioning (ZTP)

### ZTP Steps

- Order SD-WAN devices with PnP licenses via the PnP Connect portal.
- Configure the vBond controller IP address or domain name.
- Define the vBond controller in PnP Connect.
- PnP sends data to ZTP automatically.
- Upload provisioning file to vManage.

### ZTP Considerations

- **Public DNS Servers**: Ensure the edge router can reach public DNS servers (e.g., Google DNS 8.8.8.8 and 8.8.4.4).
- **Reachability**: The router must reach `ztp.viptela.com`.
- **Network Cable**: Connect the appropriate interface (e.g., `ge0/0` for vEdge 1000).

### Onboarding Steps

- Build configuration template on vManage.
- Cable and power on the vEdge routers.
- Authenticate devices via the vBond server.
- Load configuration from vManage onto vEdge routers.
- Build secure channels to the vSmart controller.
- Set up OMP peering with vSmart controllers.
- Establish IPsec tunnels to form the SD-WAN overlay network.

> This process ensures that vEdge devices are properly configured and integrated into the SD-WAN network.

---

## Manual Configuration

In manual onboarding:

- A site network administrator manually configures essential details to connect vEdge devices with the vBond orchestrator.
- The required information includes:
  - IP address and gateway IP address (or use DHCP)
  - vBond IP address or hostname (if available in DNS)
  - DNS server IP address
  - Organization name
  - System IP address
  - Site ID

---

## Onboarding Cisco IOS XE Devices

Cisco IOS XE devices can be onboarded using three methods:

- **PnP Connect**: Automatically discovers, installs, and provisions the device to the SD-WAN overlay network.
- **Bootstrap**: A configuration file is created with vManage and loaded onto a USB key, which is then inserted into the device.
- **Manual Configuration**: A network administrator manually configures parameters via the console port.

---

# 📚 Navigation
- → Next: [TD](TD)  
- ← Previous: [TD](TD)  
- ↑ Back to: [TD](TD)
