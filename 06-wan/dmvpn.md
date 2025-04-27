# DMVPN (Dynamic Multipoint VPN)

## Purpose
Cisco IOS solution for building IPsec over GRE VPNs dynamically and scalably.

## Key Technologies
- **Next Hop Resolution Protocol (NHRP)**  
  - Creates a mapping database for all spoke tunnels to real public addresses.
- **Multipoint GRE (mGRE)**  
  - Single GRE interface supporting multiple GRE and IPsec tunnels, reducing complexity and configuration size.

## Features
- **Hub Router Configuration Reduction**: 
  - Single mGRE interface and IPsec profile to manage all spoke routers.
- **Automatic IPsec Initiation**:
  -  Auto-creation of GRE tunnels without IPsec peering configuration.
- **Support for IP Unicast, IP Multicast, and Dynamic Routing Protocols**:
  -  No need for a service provider.
- **Remote Spoke Routers**: 
  - Supports dynamic IP addressing and NAT configurations.
- **Dynamic Spoke-to-Spoke Tunnels**: 
  - Enables partial scaling or fully meshed VPNs.
- **GRE Tunnel Benefits**: 
  - Includes QoS, deterministic routing, and redundancy scenarios.

## Connectivity
- **P2P GRE Tunnel Interface**: 
  - Each remote site connects to a single mGRE headend interface, which dynamically accepts new tunnel connections.
- **Redundancy**: 
  - Achieved by configuring spokes to terminate to multiple headends at one or more hub locations.
- **IPsec Tunnel Protection**: 
  - Maps cryptographic attributes to the tunnel originated by the remote peer.
- **Dead Peer Detection (DPD)**: 
  - Detects loss of peer IPsec connection.
- **NHRP Configuration**: 
  - Required on both headend and spoke routers for using mGRE interfaces.

---

### 📚 Navigation
- → Next: [FlexVPN](flexvpn.md)  
- ← Previous: [WAN Connection Decision Points](wan-connection-decision-points.md)  
- ↑ Back to: [WAN Technologies](../readme.md)
