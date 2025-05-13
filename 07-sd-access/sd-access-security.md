# 🔐 SD-Access Security

Security in SD-Access is built around **centralized policy enforcement**, **identity-based access control**, and **network segmentation**. Cisco **Identity Services Engine (ISE)** plays a critical role in managing identity and security policies, integrating seamlessly with **Cisco DNA Center** to simplify **policy orchestration** across the fabric.



## 🛡️ Cisco ISE in SD-Access

### **Identity and Policy Management**
Cisco **ISE** provides **identity-based network access control**, enabling **user and device visibility** while enforcing **group-based policies** dynamically within the SD-Access fabric. It allows endpoints to be classified into **Scalable Groups (SGTs)**, simplifying **security enforcement** across the network.

### **Integration with Cisco DNA Center**
Cisco ISE works alongside **Cisco DNA Center**, leveraging:
- **pxGRID services** for trust establishment.  
- **External RESTful Services (ERS)** to exchange **policy and contract data** between systems.  
- **REST APIs** to dynamically manage **SGTs**, ensuring consistency in enforcement.

### **Deployment Models**
ISE can be deployed as:
- A **standalone appliance** managing security across a single fabric.  
- A **distributed deployment** using multiple appliances to scale policy enforcement across multiple fabric sites.



## 🔗 TrustSec and Scalable Group Tags (SGTs)

Cisco **TrustSec** enhances security by eliminating the need for **traditional access control lists (ACLs)** on each network device. Instead, it assigns **SGTs** to users or devices **at ingress**, enforcing **policy at egress** within the infrastructure.

### **Scalable Group Tags (SGTs)**
- **SGTs are 16-bit security identifiers**, embedded in **VXLAN headers** for SD-Access segmentation.
- Cisco **ISE manages SGTs** across the fabric, ensuring consistent **policy-based traffic control**.
- Unlike traditional ACL-based enforcement, SGTs allow **dynamic policy adaptation** without manual intervention.

### **TrustSec Policy Enforcement**
Each TrustSec-enabled design must implement:
1. **SGT Classification**  
   - Cisco **ISE classifies endpoints** based on **authentication and authorization policies**.
2. **SGT Propagation**  
   - **Inline tagging** or via **SGT Exchange Protocol (SXP)** ensures SGT values remain intact across network devices.

---
### 📚 Navigation
- ← Previous: [SD-Access Design](./sd-access-design.md)
- ↩ Return to: [SD-Access - Index](./README.md)
