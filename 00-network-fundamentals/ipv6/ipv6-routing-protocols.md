## IPv6 Routing Protocols

IPv6 routing protocols enable dynamic exchange of IPv6 network reachability information between routers. They have been adapted or redesigned to support IPv6 addressing, multicast updates, and the operational differences compared to IPv4 routing.

### 🔄 RIPng (Routing Information Protocol next generation)
- Retains core RIP mechanisms like a 15-hop limit and split horizon with poison reverse.
- Supports IPv6 addresses and prefixes.
- Uses UDP port 521 instead of 520.
- Exchanges updates via multicast group FF02::9 for RIP routers.

### 🚀 EIGRP for IPv6
- Retains EIGRP core mechanisms: neighbor discovery, DUAL algorithm, modular design.
- Supports IPv6 prefixes and operates independently from IPv4 EIGRP.
- Does not use network statements for activation.
- Exchanges updates via multicast group FF02::A for EIGRP routers.

### 🧭 OSPFv3 (Open Shortest Path First version 3)
- Retains OSPF core mechanisms: flooding, SPF calculation, DR/BDR election, and areas.
- Designed for IPv6 transport, carrying IPv6 addresses and prefixes.
- Exchanges information via multicast groups FF02::5 (all OSPF routers) and FF02::6 (all DRs).

### 🧩 IS-IS for IPv6
- Supports IPv6 through additional TLV (Type-Length-Value) structures:
  - New reachability TLVs and interface address TLVs.
- Enables multi-topology IS-IS:
  - IPv4 and IPv6 can operate independently within the same IS-IS domain.
- IPv4, IPv6, or both can be configured per interface for Level 1, Level 2, or Level 1/2.
- If IPv4 and IPv6 share the same topologies and levels, multi-topology extensions are not required.

### 🌍 BGP4 Multiprotocol Extensions (MP-BGP) for IPv6
- Defined in RFC 2545 to carry IPv6 route information.
- Introduces new attributes:
  - **MP_REACH_NLRI**: Describes reachable IPv6 destinations (with next-hop and prefix information).
  - **MP_UNREACH_NLRI**: Communicates withdrawn IPv6 routes.
- Cisco IOS supports BGP multiprotocol attributes to handle IPv6 routing.

---

### 📚 Navigation
- → Next: [IPv6 Transition Mechanisms](ipv6-transition-mechanisms.md)  
- ← Previous: [IPv6 Mechanisms](ipv6-mechanisms.md)  
- ↑ Back to: [IPv6](../readme.md)
