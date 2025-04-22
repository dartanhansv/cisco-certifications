# YANG Data Models: IETF, OpenConfig, and Cisco

## Introduction
IETF, OpenConfig, and Cisco YANG models represent different approaches to modeling network device data using the YANG language. Each model serves distinct purposes and offers unique features tailored to various network environments and requirements.

## Comparison of YANG Models

| Model                 | Purpose                                                   | Scope                                  | Features                                                        | Example                                                |
| --------------------- | --------------------------------------------------------- | -------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------ |
| **IETF YANG Models**  | Developed by the Internet Engineering Task Force (IETF)   | Wide range of network functions        | Standardized, interoperable, limited feature coverage           | Common YANG modules for interfaces, QoS, and datatypes |
| **OpenConfig Models** | Network operator-led initiative for vendor-neutral models | Common network protocols and services  | Vendor-neutral, operationally complete, consistent and cohesive | Configuration and telemetry data in a single structure |
| **Cisco YANG Models** | Vendor-specific models developed by Cisco                 | Broad range of Cisco-specific features | Comprehensive, vendor-specific, native models                   | YANG models published on GitHub for Cisco platforms    |

> [!TIP]  
> OpenConfig is often preferred in multi-vendor environments due to its consistency and neutral approach.

> [!NOTE]  
> Cisco YANG models are often required when accessing device-specific capabilities not yet standardized.

---

### 📚 Navigation
- ← [Back to Automation Overview](../readme.md)
- → [Next: NETCONF and RESTCONF](./netconf-restconf.md)
