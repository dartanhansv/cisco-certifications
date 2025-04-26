# ENSLD Exam Topics  

This file contains the official blueprint topics for the Cisco ENSLD (300-420) exam.  

---

### **Important Note**  
- This content is based on the exam topics available as of April 3, 2025.  
- Cisco frequently reviews and updates exam blueprints, so topics may change over time.  
- For the most current version of the exam topics, visit the [Cisco Learning Network ENSLD page](https://learningnetwork.cisco.com/s/ensld-exam-topics).  

---

## 1.0 Advanced Addressing and Routing Solutions (25%)  
- **1.1** Create structured addressing plans for IPv4 and IPv6  
- **1.2** Create stable, secure, and scalable routing designs for IS-IS  
- **1.3** Create stable, secure, and scalable routing designs for EIGRP  
- **1.4** Create stable, secure, and scalable routing designs for OSPF  
- **1.5** Create stable, secure, and scalable routing designs for BGP  
  - **1.5.a** Address families  
  - **1.5.b** Basic route filtering  
  - **1.5.c** Attributes for path preference  
  - **1.5.d** Route reflectors  
  - **1.5.e** Load sharing  
- **1.6** Determine IPv6 migration strategies  
  - **1.6.a** Overlay (tunneling)  
  - **1.6.b** Native (dual-stacking)  
  - **1.6.c** Boundaries (IPv4/IPv6 translations)  

---

## 2.0 Advanced Enterprise Campus Networks (25%)

**2.1 Design campus networks for high availability (FHRP)**
- 2.1.a [First Hop Redundancy Protocols](../00-network-fundamentals/lan/fhrp.md)
- 2.1.b [Platform abstraction techniques](../00-network-fundamentals/lan/platform-abstraction.md)
- 2.1.c [Graceful restart](../00-network-fundamentals/lan/graceful-restart.md)
- 2.1.d [BFD](../00-network-fundamentals/lan/bfd.md)

**2.2 Design campus Layer 2 infrastructures**
- 2.2.a [STP scalability](../00-network-fundamentals/lan/stp-scalability.md)
- 2.2.b [Fast convergence](../00-network-fundamentals/lan/l2-fast-convergence.md)
- 2.2.c Loop-free technologies  
  - ✅ [EtherChannel](../00-network-fundamentals/lan/etherchannel.md)
  - ✅ [Spanning Tree Protocol](../00-network-fundamentals/lan/spanning-tree-protocol.md)
  - ✅ [STP Toolkit](../00-network-fundamentals/lan/stp-toolkit.md)
- 2.2.d PoE and WoL  
  - ✅ [Power over Ethernet](../00-network-fundamentals/lan/power-over-ethernet.md)
  - ✅ [Wake on LAN](../00-network-fundamentals/lan/wol.md)
- 2.2.e Layer 2 security techniques (STP security, port security, VACL)  
  - ✅ [Layer 2 security techniques](../00-network-fundamentals/lan/l2-security.md)
  - ✅ [Port security](../00-network-fundamentals/lan/port-security.md)
  - ✅ [STP Toolkit](../00-network-fundamentals/lan/stp-toolkit.md)

**2.3 Design multicampus Layer 3 infrastructures**
- 2.3.a [Campus Design Models](../00-network-fundamentals/lan/campus-design-models.md)
- 2.3.b [Load sharing](../01-routing-protocols/fundamentals/load-sharing.md)
- 2.3.c Route summarization  
  - ✅ [Redistribution overview](../01-routing-protocols/fundamentals/redistribution-overview.md)
  - ✅ [Redistribution cheatsheet](../01-routing-protocols/fundamentals/redistribution-cheatsheet.md)
  - ✅ [Route redistribution](../01-routing-protocols/fundamentals/route-redistribution.md)
- 2.3.d [Route filtering](../01-routing-protocols/fundamentals/route-filtering.md)
- 2.3.e [VRFs](../01-routing-protocols/fundamentals/vrf.md)
- 2.3.f [Optimal topologies](../00-network-fundamentals/lan/campus-design-models.md)
- 2.3.g Redistribution  
  - ✅ [Redistribution overview](../01-routing-protocols/fundamentals/redistribution-overview.md)
  - ✅ [Redistribution cheatsheet](../01-routing-protocols/fundamentals/redistribution-cheatsheet.md)
  - ✅ [Route redistribution](../01-routing-protocols/fundamentals/route-redistribution.md)

**2.4 Describe SD-Access Architecture**
- ✅ [SD-Access Overview](../07-sd-access/sd-access-overview.md)
- ✅ [SD-Access Architecture](../07-sd-access/sd-access-architecure.md)

**2.5 Describe SD-Access fabric design considerations**
- ✅ [SD-Access Fabric](../07-sd-access/sd-access-fabric.md)
- ✅ [SD-Access Migration](../07-sd-access/sd-access-migration.md)
- ✅ [SD-Access Multicast](../07-sd-access/sd-access-multicast.md)
- ✅ [SD-Access Design](../07-sd-access/sd-access-design.md)


---

## 3.0 WAN for Enterprise Networks (20%)  
- **3.1** Design enterprise WAN architectures  
  - **3.1.a** SD-WAN  
  - **3.1.b** MPLS  
  - **3.1.c** VPN technologies  
- **3.2** Design enterprise WAN resiliency solutions  
  - **3.2.a** Path diversity  
  - **3.2.b** Failover  

---

## 4.0 Network Services (20%)  
- **4.1** Select appropriate QoS strategies to meet customer requirements (DiffServ, IntServ)
- **4.2** Design end-to-end QoS policies 
  - **4.2.a** Classification and marking  
  - **4.2.b** Shaping 
  - **4.2.c** Policing  
  - **4.2.d** Queuing  
    - ✅ [QoS Models & strategies](../02-network-services/qos-models.md)  
    - ✅ [QoS Policies](../02-network-services/qos-policies.md)  
    - ✅ [QoS Trust Boundaries](../02-network-services/qos-trust-boundaries.md)    
- **4.3** Design network management techniques  
  - **4.3.a** In-band vs. out-of-band  
  - **4.3.b** Segmented management networks  
  - **4.3.c** Prioritizing network management traffic  
      - ✅ [Network Management](../02-network-services/network-management.md)    
- **4.4** Describe multicast routing concepts (source trees, shared trees, RPF, rendezvous points)
  - ✅ [Multicast Overview](../01-routing-protocols/multicast/multicast-overview.md)
- **4.5** Design multicast services (SSM, PIM bidirectional, MSDP) 
  - ✅ [PIM](../01-routing-protocols/multicast/pim.md)
---

## 5.0 Automation (10%)

- **5.1** Differentiate between IETF, OpenConfig, and Cisco YANG models  
  - ✅ [YANG Models (IETF, OpenConfig, Cisco)](../03-automation-and-programmability/yang-models.md)

- **5.2** Differentiate between NETCONF and RESTCONF  
  - ✅ [NETCONF](../03-automation-and-programmability/netconf.md)  
  - ✅ [RESTCONF](../03-automation-and-programmability/restconf.md)  
  - ✅ [NETCONF vs RESTCONF](../03-automation-and-programmability/netconf-vs-restconf.md)

- **5.3** Describe the impact of model-driven telemetry on the network  
  - ✅ [Model-Driven Telemetry (Periodic and On-Change)](../03-automation-and-programmability/model-driven-telemetry.md)

- **5.4** Describe GRPC and GNMI  
  - ✅ [gRPC and gNMI](../03-automation-and-programmability/grpc-gnmi.md)

- **5.5** Describe cloud connectivity options such as direct connect, cloud on ramp, MPLS direct connect, and WAN integration  
  - ✅ [Direct Connect and MPLS Direct Connect](../03-automation-and-programmability/direct-connect.md)  
  - ✅ [Cloud On-Ramp](../03-automation-and-programmability/cloud-on-ramp.md)  
  - ✅ [WAN Integration](../03-automation-and-programmability/wan-integration.md)

- **5.6** Describe cloud-based services model in private, public, and hybrid deployments (SaaS, PaaS, IaaS)  
  - ✅ [Cloud Service Models (SaaS, PaaS, IaaS)](../03-automation-and-programmability/cloud-based-services.md)


---

