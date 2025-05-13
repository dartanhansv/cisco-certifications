# ENSLD Exam Topics  

This file contains the official blueprint topics for the Cisco ENSLD (300-420) exam.  

---

### **Important Note**  
- This content is based on the exam topics available as of April 3, 2025.  
- Cisco frequently reviews and updates exam blueprints, so topics may change over time.  
- For the most current version of the exam topics, visit the [Cisco Learning Network ENSLD page](https://learningnetwork.cisco.com/s/ensld-exam-topics).  

## 1.0 Advanced Addressing and Routing Solutions (25%)

- **1.1** Create structured addressing plans for IPv4 and IPv6  
  - ✅ [IPv4 Overview](../00-network-fundamentals/ipv4/ipv4-overview.md) _(IPv4 basics, addressing strategies, and subnetting techniques)_  
  - ✅ [IPv6 Overview](../00-network-fundamentals/ipv4/ipv4-overview.md) _(IPv6 fundamentals, advantages over IPv4, and basic addressing)_  
  - ✅ [IPv6 Address Design](../00-network-fundamentals/ipv6/ipv6-address-design.md) _(IPv6 address allocation techniques: SLAAC, DHCPv6, and manual assignment)_  
  - ✅ [IPv6 Mechanisms](../00-network-fundamentals/ipv6/ipv6-mechanisms.md) _(Key IPv6 transition mechanisms like NAT64, 6RD, and tunneling)_

- **1.2** Create stable, secure, and scalable routing designs for IS-IS  
  - ✅ [IS-IS Overview](../01-routing-protocols/is-is/isis-overview.md) _(IS-IS protocol fundamentals and deployment scenarios)_  
  - ✅ [IS-IS NET Addressing](../01-routing-protocols/is-is/isis-net-addressing.md) _(Hierarchical IS-IS addressing for scalability)_  
  - ✅ [IS-IS IPv6 Deployment](../01-routing-protocols/is-is/isis-ipv6-deployment.md) _(Best practices for implementing IPv6 with IS-IS)_  
  - ✅ [IS-IS Design](../01-routing-protocols/is-is/isis-design.md) _(IS-IS scalability, convergence considerations, and security features)_

- **1.3** Create stable, secure, and scalable routing designs for EIGRP  
  - ✅ [EIGRP Overview](../01-routing-protocols/eigrp/eigrp-overview.md) _(Fundamental concepts of EIGRP, including neighbor relationships and metrics)_  
  - ✅ [EIGRP Design](../01-routing-protocols/eigrp/eigrp-design.md) _(EIGRP scalability, convergence time, and redundancy strategies)_

- **1.4** Create stable, secure, and scalable routing designs for OSPF  
  - ✅ [OSPF Overview](../01-routing-protocols/ospf/ospf-overview.md) _(OSPF basics, LSAs, and area hierarchy)_  
  - ✅ [OSPF Adjacency](../01-routing-protocols/ospf/ospf-adjacency.md) _(How OSPF neighbors establish adjacencies and exchange LSAs)_  
  - ✅ [OSPF Route Types](../01-routing-protocols/ospf/ospf-route-types.md) _(Explanation of intra-area, inter-area, and external OSPF routes)_  
  - ✅ [OSPF Virtual Link](../01-routing-protocols/ospf/ospf-virtual-link.md) _(Connecting discontiguous areas using virtual links)_  
  - ✅ [OSPF Route Filtering](../01-routing-protocols/ospf/ospf-route-filtering.md) _(Techniques for controlling which routes are advertised in OSPF)_  
  - ✅ [OSPF Design](../01-routing-protocols/ospf/ospf-design.md) _(Scalability, redundancy, and tuning strategies for OSPF networks)_  
  - ✅ [OSPFv3 Overview](../01-routing-protocols/ospf/ospfv3-overview.md) _(OSPFv3 enhancements for IPv6 routing)_

- **1.5** Create stable, secure, and scalable routing designs for BGP  
  - **Address families** _(IPv4, IPv6, and MP-BGP support)_  
  - **Basic route filtering** _(Techniques for prefix-based BGP filtering)_  
  - **Attributes for path preference** _(Weight, local preference, AS path, MED, and communities)_  
  - **Route reflectors** _(Scaling BGP networks through route reflection)_  
  - **Load sharing** _(Achieving traffic distribution across multiple BGP paths)_  
    - ✅ [BGP Overview](../01-routing-protocols/bgp/bgp-overview.md) _(Fundamentals of BGP operations and use cases)_  
    - ✅ [BGP Path Attributes](../01-routing-protocols/bgp/bgp-path-attributes.md) _(How BGP path attributes influence routing decisions)_  
    - ✅ [BGP Path Selection](../01-routing-protocols/bgp/bgp-path-selection.md) _(Understanding the BGP best path selection process)_  
    - ✅ [BGP Communities](../01-routing-protocols/bgp/bgp-communities.md) _(Grouping and controlling routes using BGP communities)_  
    - ✅ [BGP Troubleshooting](../01-routing-protocols/bgp/bgp-tshoot.md) _(Common issues and diagnostic techniques for BGP)_

- **1.6** Determine IPv6 migration strategies  
  - **Overlay (tunneling)** _(GRE, 6to4, ISATAP, and Teredo tunnels)_  
  - **Native (dual-stacking)** _(Running IPv4 and IPv6 together for seamless migration)_  
  - **Boundaries (IPv4/IPv6 translations)** _(NAT64, NAT-PT, and 6PE techniques)_  
    - ✅ [IPv6 Migration](../00-network-fundamentals/ipv6/ipv6-migration.md) _(Strategies for transitioning enterprise networks to IPv6)_


## 2.0 Advanced Enterprise Campus Networks (25%)

- **2.1** Design campus networks for high availability (FHRP)  
  - ✅ [First Hop Redundancy Protocols](../00-network-fundamentals/lan/fhrp.md) _(HSRP, VRRP, and GLBP redundancy techniques for gateway availability)_  
  - ✅ [Platform abstraction techniques](../00-network-fundamentals/lan/platform-abstraction.md) _(Decoupling hardware dependencies through abstraction layers)_  
  - ✅ [Graceful restart](../00-network-fundamentals/lan/graceful-restart.md) _(Minimizing routing disruptions during process failures)_  
  - ✅ [BFD](../00-network-fundamentals/lan/bfd.md) _(Fast failure detection mechanism for dynamic routing protocols)_

- **2.2** Design campus Layer 2 infrastructures  
  - ✅ [STP scalability](../00-network-fundamentals/lan/stp-scalability.md) _(Optimizing Spanning Tree Protocol (STP) to handle large-scale Layer 2 networks)_  
  - ✅ [Fast convergence](../00-network-fundamentals/lan/l2-fast-convergence.md) _(Techniques to reduce STP recovery time and minimize downtime)_  
  - **Loop-free technologies**  
    - ✅ [EtherChannel](../00-network-fundamentals/lan/etherchannel.md) _(Bundling multiple links for redundancy and increased bandwidth)_  
    - ✅ [Spanning Tree Protocol](../00-network-fundamentals/lan/spanning-tree-protocol.md) _(Preventing Layer 2 loops with protocol-based redundancy)_  
    - ✅ [STP Toolkit](../00-network-fundamentals/lan/stp-toolkit.md) _(Enhancements like BPDU Guard, Root Guard, and Loop Guard for better STP security)_  
  - **PoE and WoL**  
    - ✅ [Power over Ethernet](../00-network-fundamentals/lan/power-over-ethernet.md) _(Delivering electrical power via network cables to devices)_  
    - ✅ [Wake on LAN](../00-network-fundamentals/lan/wake-on-lan.md) _(Remotely waking up network devices when needed)_  
  - **Layer 2 security techniques (STP security, port security, VACL)**  
    - ✅ [Layer 2 security techniques](../00-network-fundamentals/lan/l2-security.md) _(Security strategies including MAC filtering and VLAN-based access control)_  
    - ✅ [Port security](../00-network-fundamentals/lan/port-security.md) _(Restricting unauthorized devices from connecting to switch ports)_  

- **2.3** Design multicampus Layer 3 infrastructures  
  - ✅ [Campus Design Models](../00-network-fundamentals/lan/campus-design-models.md) _(Hierarchical network design and enterprise scalability models)_  
  - ✅ [Load sharing](../01-routing-protocols/fundamentals/load-sharing.md) _(Distributing traffic across multiple paths for efficiency)_  
  - **Route summarization**  
    - ✅ [Redistribution overview](../01-routing-protocols/fundamentals/redistribution-overview.md) _(Key principles of route redistribution between protocols)_  
    - ✅ [Redistribution cheatsheet](../01-routing-protocols/fundamentals/redistribution-cheatsheet.md) _(Quick reference for configuring route redistribution)_  
    - ✅ [Route redistribution](../01-routing-protocols/fundamentals/route-redistribution.md) _(Interconnecting multiple routing protocols to share routes)_  
  - ✅ [Route filtering](../01-routing-protocols/fundamentals/route-filtering.md) _(Selective advertisement and blocking of routes in large networks)_  
  - ✅ [VRFs](../01-routing-protocols/fundamentals/vrf.md) _(Using Virtual Routing and Forwarding for logical separation of networks)_  
  - ✅ [Optimal topologies](../00-network-fundamentals/lan/campus-design-models.md) _(Best practices for redundant and scalable campus design)_

- **2.4** Describe SD-Access Architecture  
  - ✅ [SD-Access Overview](../07-sd-access/sd-access-overview.md) _(Cisco SD-Access fundamentals and intent-based networking)_  
  - ✅ [SD-Access Architecture](../07-sd-access/sd-access-architecture.md) _(Infrastructure and components of SD-Access fabric)_

- **2.5** Describe SD-Access fabric design considerations  
  - ✅ [SD-Access Fabric](../07-sd-access/sd-access-fabric.md) _(Explains control, data, and policy planes of SD-Access)_  
  - ✅ [SD-Access Migration](../07-sd-access/sd-access-migration.md) _(Best practices for transitioning from legacy network designs)_  
  - ✅ [SD-Access Multicast](../07-sd-access/sd-access-multicast.md) _(Handling multicast traffic efficiently within an SD-Access fabric)_  
  - ✅ [SD-Access Design](../07-sd-access/sd-access-design.md) _(Strategies for scalability, segmentation, and user policy enforcement)_


## 3.0 WAN for Enterprise Networks (20%)

- **3.1** Describe WAN connectivity options for on-premises, hybrid, and cloud solutions  
  - ✅ [WAN Overview](../06-wan/wan-overview.md) _(Introduction to WAN connectivity models, including hybrid and cloud integration)_  
  - ✅ **3.1.a** [Layer 2 VPN](../06-wan/l2-vpn.md) _(Tunneling Layer 2 traffic across WANs using technologies like VPLS)_  
  - ✅ **3.1.b** [MPLS Layer 3 VPN](../06-wan/mpls-l3-vpn.md) _(Using MPLS to create isolated customer routing domains over provider networks)_  
  - ✅ **3.1.c / 3.1.d / 3.1.e** [Metro Ethernet, DWDM, 4G/5G](../06-wan/wan-technologies.md) _(Overview of various WAN technologies used for enterprise connectivity)_  
  - ✅ **3.1.f** [SD-WAN Customer Edge](../08-sd-wan/sd-wan-overview.md) _(How SD-WAN enhances performance for cloud-based applications)_

- **3.2** Design site-to-site VPN for on-premises, hybrid, and cloud solutions  
  - ✅ **3.2.a** [Dynamic Multipoint VPN (DMVPN)](../06-wan/dmvpn.md) _(On-demand multipoint tunnels without static configurations)_  
  - ✅ **3.2.b** [Layer 2 VPN](../06-wan/l2-vpn.md) _(Extending Layer 2 domains across WAN for seamless service continuity)_  
  - ✅ **3.2.c** [MPLS Layer 3 VPN](../06-wan/mpls-l3-vpn.md) _(Scalable routing virtualization across a provider MPLS backbone)_  
  - ✅ **3.2.d / 3.2.f** [IPsec and GETVPN](../06-wan/ipsec-vti.md) _(Secure transport encryption with group-based keying mechanisms)_  
  - ✅ **3.2.e** [GRE, mGRE, and IPsec](../06-wan/gre-mgre-ipsec.md) _(Tunneling solutions for encapsulating traffic across WANs)_

- **3.3** Design high availability for enterprise WAN for on-premises, hybrid, and cloud solutions  
  - ✅ [WAN Design and Backup Connectivity](../06-wan/wan-design.md) _(Strategies for redundant WAN paths and failover configurations)_

- **3.4** Describe Cisco SD-WAN architecture (orchestration plane, management plane, control plane, data plane, onboarding and provisioning, security)  
  - ✅ [SD-WAN Architecture](../08-sd-wan/sd-wan-architecture.md) _(Breakdown of control, management, orchestration, and data planes)_  
  - ✅ [SD-WAN Onboarding](../08-sd-wan/sd-wan-onboarding.md) _(Steps for provisioning and configuring SD-WAN edge devices)_

- **3.5** Describe Cisco SD-WAN design considerations (control plane design, overlay design, LAN design, high availability, redundancy, scalability, security design, QoS and multicast over SD-WAN fabric)  
  - ✅ [SD-WAN Design](../08-sd-wan/sd-wan-design.md) _(Comprehensive design strategies for scalable SD-WAN deployments)_  
  - ✅ [SD-WAN High Availability](../08-sd-wan/sd-wan-high-availability.md) _(Redundancy techniques for maintaining SD-WAN uptime)_  
  - ✅ [SD-WAN LAN Design](../08-sd-wan/sd-wan-lan.md) _(Integration of SD-WAN edge devices with existing LAN infrastructure)_  
  - ✅ [SD-WAN Migration](../08-sd-wan/sd-wan-migration.md) _(Transition strategies from traditional WAN to SD-WAN)_  
  - ✅ [SD-WAN Direct Internet Access and Security](../08-sd-wan/sd-wan-dia-security.md) _(Security policies for internet-bound SD-WAN traffic)_  
  - ✅ [SD-WAN QoS](../08-sd-wan/sd-wan-qos.md) _(Optimizing traffic prioritization and ensuring application performance)_  
  - ✅ [SD-WAN Multicast](../08-sd-wan/sd-wan-multicast.md) _(Efficient multicast distribution and WAN bandwidth optimization techniques)_



## 4.0 Network Services (20%)

- **4.1** Select appropriate QoS strategies to meet customer requirements (DiffServ, IntServ)  
  - ✅ **DiffServ vs. IntServ** _(Comparing Differentiated Services (DiffServ) and Integrated Services (IntServ) for traffic management)_

- **4.2** Design end-to-end QoS policies  
  - ✅ [QoS Models & Strategies](../02-network-services/qos-models.md) _(Traffic prioritization techniques such as LLQ, CBWFQ, and WRED)_  
  - ✅ [QoS Policies](../02-network-services/qos-policies.md) _(Methods for applying QoS at different network layers)_  
  - ✅ [QoS Trust Boundaries](../02-network-services/qos-trust-boundaries.md) _(Defining where QoS classifications should be enforced in a network)_

- **4.3** Design network management techniques  
  - ✅ [Network Management](../02-network-services/network-management.md) _(Strategies for monitoring and maintaining network health using SNMP, NetFlow, and telemetry)_

- **4.4** Describe multicast routing concepts (source trees, shared trees, RPF, rendezvous points)  
  - ✅ [Multicast Overview](../01-routing-protocols/multicast/multicast-overview.md) _(Multicast forwarding models: source trees, shared trees, and Reverse Path Forwarding (RPF))_

- **4.5** Design multicast services (SSM, PIM bidirectional, MSDP)  
  - ✅ [PIM](../01-routing-protocols/multicast/pim.md) _(Protocol Independent Multicast (PIM) variations: Sparse Mode, Dense Mode, Bi-Directional PIM, and SSM)_

---

## 5.0 Automation (10%)

- **5.1** Differentiate between IETF, OpenConfig, and Cisco YANG models  
  - ✅ [YANG Models (IETF, OpenConfig, Cisco)](../03-automation/yang-models.md) _(Structure and usage of different YANG models in network automation)_

- **5.2** Differentiate between NETCONF and RESTCONF  
  - ✅ [NETCONF](../03-automation/netconf.md) _(XML-based protocol for managing configuration changes on network devices)_  
  - ✅ [RESTCONF](../03-automation/restconf.md) _(RESTful API alternative for simplifying network automation)_  
  - ✅ [NETCONF vs RESTCONF](../03-automation/netconf-vs-restconf.md) _(Comparison of capabilities and use cases for NETCONF vs RESTCONF)_

- **5.3** Describe the impact of model-driven telemetry on the network  
  - ✅ [Model-Driven Telemetry (Periodic and On-Change)](../03-automation/model-driven-telemetry.md) _(Enabling real-time data collection for proactive network monitoring)_

- **5.4** Describe GRPC and GNMI  
  - ✅ [gRPC and gNMI](../03-automation/grpc-gnmi.md) _(How gRPC and gNMI improve efficiency in network telemetry and device configuration)_

- **5.5** Describe cloud connectivity options such as direct connect, cloud on ramp, MPLS direct connect, and WAN integration  
  - ✅ [Direct Connect and MPLS Direct Connect](../06-wan/direct-connect.md) _(Dedicated private links for cloud connectivity via MPLS and Direct Connect)_  
  - ✅ [Cloud On-Ramp](../08-sd-wan/sd-wan-cloud-on-ramp.md) _(Optimizing cloud service access from enterprise networks)_  
  - ✅ [WAN Integration](../06-wan/wan-integration.md) _(Techniques for integrating WAN solutions with cloud infrastructure)_

- **5.6** Describe cloud-based services model in private, public, and hybrid deployments (SaaS, PaaS, IaaS)  
  - ✅ [Cloud Service Models (SaaS, PaaS, IaaS)](../08-sd-wan/sd-wan-cloud-models.md) _(Key characteristics and differences between SaaS, PaaS, and IaaS)_


---

