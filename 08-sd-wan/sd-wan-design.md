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
  Support more vEdge routers.

- **Add vSmart controllers**:  
  Increase the capacity of the control plane.

---

## 🧩 SD-WAN Deployment Design Considerations 

### Multitenant

- vManage and vBond can be shared between tenants.
- vSmart must be dedicated to a tenant and **cannot** be multitenant.

### Control Connections

- Control plane tunnels to vBond orchestrators **always** use Datagram Layer Security (DTLS), because these connections must be handled by UDP.
- Connections to vSmart and vManage **use DTLS by default**, but can be configured to use TLS instead.

---

# 📚 Navigation
- → Next: [TD](TD)  
- ← Previous: [TD](TD)  
- ↑ Back to: [TD](TD)

