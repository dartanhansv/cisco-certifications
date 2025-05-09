# SD-WAN Architecture

Cisco SD-WAN architecture is divided into four planes: Orchestration, Management, Control, and Data. Each plane plays a key role in establishing, maintaining, and securing the SD-WAN fabric.

<!-- TIP: Insert a Cisco official architecture diagram image here to help visualize the relationships among vBond, vSmart, vManage, and vEdge. -->

---

## Orchestration Plane

**Controller: vBond**  
The vBond orchestrator is responsible for:

- Performing the initial authentication of vEdge devices.
- Orchestrating connectivity between vSmart controllers and vEdge routers.
  - It tells vEdge routers how to connect with vManage and vSmart controllers.
  - It informs vSmart controllers about newly onboarded vEdge devices.

---

## Management Plane

**Controllers: vManage and vAnalytics Engine**

### vManage
vManage is the centralized Network Management System (NMS) that provides:

- A GUI-based interface for monitoring, configuration, and maintenance of all SD-WAN devices and links (both underlay and overlay).
- Support for Web Console, REST API, CLI, Syslog, SNMP, and NETCONF integrations.

### vAnalytics Engine
Accessed through vManage, vAnalytics provides:

- End-to-end visibility of application and infrastructure performance.
- Real-time failure correlation and application scoring.
- "What-if" scenario modeling for performance forecasting, policy tuning, and QoS optimization.
- Assistance in planning application provisioning, bandwidth expansion, and branch growth.

---

## Control Plane

**Controller: vSmart**

The vSmart controller (the brain of the SD-WAN architecture) is responsible for:

- Managing routing information across the overlay.
- Enforcing network-wide policies, including:
  - Data plane policies (e.g., traffic engineering, SLA-based routing)
  - Network-wide segmentation (VPNs, security zones)

> **Note:** Policies are created and configured in vManage, but enforced by vSmart controllers.

---

## Data Plane

**Component: vEdge Routers**  
vEdge routers, either physical or virtual, are responsible for:

- Establishing the SD-WAN fabric and forwarding user traffic.
- Establishing IPsec and GRE tunnels between SD-WAN sites.
- Exchanging routing information with vSmart over secure control channels.
- Implementing data plane and application-aware routing policies.
- Exporting performance and telemetry statistics.

vEdge routers interface types:

- **Service-Side Interfaces**: Connect to the internal LAN.
- **Transport-Side Interfaces**: Connect to the external WAN (MPLS, Internet, 4G/LTE).

> **Note:** vEdge routers use the Overlay Management Protocol (OMP) to send routing info only to vSmart — never directly to each other.

---

## Summary Table

| **Plane               | **Controller/Component** | **Primary** Function**                                                        |
| :------------------ | :------------------- | :---------------------------------------------------------------------- |
| Orchestration Plane | vBond                | Authenticates and connects control/data components |
| Management Plane    | vManage, vAnalytics  | Device configuration, monitoring, policy creation, network visibility   |
| Control Plane       | vSmart               | Handles routing and enforces policie                   |
| Data Plane          | vEdge Routers        | Forwards traffic, applies policies, and monitors performance   |

---

## Overlay Management Protocol (OMP)

OMP is the protocol that manages the SD-WAN overlay network.  
It operates over TLS or DTLS tunnels between vEdge routers and vSmart controllers and advertises three types of routes:

- **OMP Routes** (vRoutes)
- **TLOC Routes**
- **Service Routes**

---

### OMP Routes (vRoutes)

This represent prefixes learned at local networks (via static routes, OSPF, or BGP). 
Each OMP route contains attributes such as:

- **TLOC**: Transport Location ID (similar to BGP NEXT_HOP), consisting of:
  - System IP address of the OMP speaker
  - Link color (e.g., mpls, internet, metro-ethernet)
  - Encapsulation type (IPsec or GRE)
- **Origin**: Source protocol (BGP, OSPF, connected, static).
- **Originator**: IP address of the device that originated the route.
- **Preference**: Higher preference indicates a more preferred route.
- **Service**: Associated network service (e.g., firewall, WAN optimization).
- **Site ID**: Identifies the site within the SD-WAN domain.
- **Tag**: Optional attribute for routing control and policy decisions.
- **VPN**: VPN or network segment to which the route belongs.

---

### TLOC Routes

TLOC (Transport Location) routes define WAN tunnel endpoints and tell how to reach each SD-WAN site.

Key attributes include:

- **Private Address**: Internal IP address of the TLOC interface.
- **Public Address**: NAT-translated public IP address (if applicable).
- **Carrier**: Identifier for public/private transport.
- **Color**: Link type (e.g., biz-internet, public-internet, mpls).
- **Encapsulation Type**: Tunnel type (IPsec or GRE).
- **Preference**: TLOC selection priority for routing.
- **Site ID**: Site association.
- **Tag**: Optional path control attribute.
- **Weight**: Used to differentiate among multiple TLOCs advertising the same route.

---

### Service Routes

Service routes represent reachability to network services such as:

- Firewalls
- Intrusion Prevention Systems (IPS)
- Application Optimization engines
- VPN labels

These services can be distributed across the SD-WAN overlay and advertised via OMP.

---

### 📚 Navigation
- → Next: [SD-WAN Onboarding](./sd-wan-onboarding.md)  
- ← Previous: [SD-WAN Overview](./sd-wan-overview.md)  
- ↩ Return to [Cisco SD-WAN](./README.md)
