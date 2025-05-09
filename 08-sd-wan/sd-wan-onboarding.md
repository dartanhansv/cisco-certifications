# SD-WAN Onboarding

### Onboarding and Provisioning

> 📝 **Source:**  
> [Cisco SD-WAN WAN Edge Onboarding Deployment Guide (Nov 2020)](https://www.cisco.com/c/dam/en/us/td/docs/solutions/CVD/SDWAN/sdwan-wan-edge-onboarding-deploy-guide-2020nov.pdf)


**Onboarding Methods**  
vEdge devices can be onboarded using:

- **Zero Touch Provisioning (ZTP)**
- **Manual Configuration**

---

## Zero Touch Provisioning (ZTP)

### ZTP Steps

- Order SD-WAN devices with PnP licenses via the PnP Connect portal.
- Configure the vBond controller IP address or domain name.
- Define the vBond controller in PnP Connect.
- PnP sends device data to ZTP automatically.
- Upload provisioning file to vManage.

> The ZTP process automates most of the onboarding workflow, but initial setup tasks like uploading provisioning files to vManage are performed manually by the network admin.

### ZTP Considerations

- **Public DNS Servers**: Ensure the edge router can reach public DNS servers (e.g., Google DNS 8.8.8.8 and 8.8.4.4).
- **Reachability**:  The router must be able to resolve and reach `ztp.viptela.com`.
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

Cisco IOS XE SD-WAN is typically deployed on platforms like **CSR1000v** or other supported IOS XE-based routers. These devices are fully managed through **vManage**, just like vEdges.

Once onboarded, IOS XE devices participate in the SD-WAN overlay as full members of the control and data plane. They establish secure connections to vSmart controllers and build IPsec tunnels with other WAN edge routers.
---

### 📚 Navigation
- → Next: [SD-WAN Design](./sd-wan-design.md)
- ← Previous: [SD-WAN Architecture](./sd-wan-architecture.md)  
- ↩ Return to [Cisco SD-WAN](./README.md)

