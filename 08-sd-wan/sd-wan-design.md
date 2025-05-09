# 🛠️ SD-WAN Design Considerations

When deploying SD-WAN components, an enterprise designer should consider scalability, high availability, security, and QoS.

---

## 🧠 Control Plane Design Options

SD-WAN vManage, vSmart, and vBond can be deployed using three cloud-delivered control methods, based on the company's IT policies:

- **On-premises**:  
  The enterprise IT team deploys and manages vManage, vSmart, and vBond components, along with vEdge routers and overlay policy.

- **Managed SP**:  
  A service provider deploys and manages the vManage, vSmart, and vBond components in the SP's cloud infrastructure.

- **Cisco Cloud Deployment**:  
  Cisco deploys and manages the vManage, vSmart, and vBond components in its cloud infrastructure.

---

## 📈 Scalability

To enhance the availability and growth of SD-WAN orchestration, management, and control planes, consider implementing horizontal scaling:

- **Add vBond orchestrators**:  
  Increase vEdge bring-up capacity and achieve redundancy by mapping all IP addresses to a single DNS name.

- **Create a vManage cluster**:  
  To support more vEdge routers (up to ~5,000 devices depending on software version).

- **Add vSmart controllers**:  
  Increase the capacity of the control plane (each vSmart can typically support ~2,000 devices).

---

## 🧩 SD-WAN Deployment Design Considerations 

### Multitenant

- vManage and vBond can be shared between tenants.
- vSmart must be dedicated to a tenant and **cannot** be multitenant.
  This ensures complete separation of routing and policy information per tenant.

### Control Connections
SD-WAN establishes secure control plane communications using specific protocols based on the component:

- Control plane tunnels to vBond orchestrators **always** use Datagram Layer Security (DTLS), because these connections must be handled by UDP.
- Connections to vSmart and vManage **use DTLS by default**, but can be configured to use TLS instead.

---

## ♻️ High Availability

High availability is achieved by deploying redundant vBond, vSmart, and vManage controllers—often in geographically diverse data centers. Edge devices can be configured with dual transport interfaces and participate in clustering or stateful failover, depending on the platform (e.g., IOS XE supports device-level HA).

---

## 🚦 Quality of Service (QoS)

SD-WAN allows traffic classification and prioritization through centralized policies. QoS is implemented at the edge, applying queuing, shaping, and policing rules across transport interfaces to preserve application performance and meet SLAs. App-aware routing can also steer traffic based on performance metrics such as latency, loss, and jitter.

---

### 📚 Navigation
- → Next: [SD-WAN LAN Design](./sd-wan-lan.md)
- ← Previous: [SD-WAN Onboarding ](./sd-wan-onboarding.md)  
- ↩ Return to [Cisco SD-WAN](./README.md)

