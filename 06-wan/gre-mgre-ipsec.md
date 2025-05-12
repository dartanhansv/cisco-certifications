
# GRE, mGRE, and IPsec

## Generic Routing Encapsulation (GRE)

GRE is a tunneling protocol used to encapsulate various network layer protocols over an IP network.

### **Key Features**:

- Supports unicast and multicast traffic.
- Enables any Interior Gateway Protocol (IGP) over a GRE tunnel.
- Virtual point-to-point connection between two routers.
- Uses protocol number **47**.

### **Disadvantages**:

- No built-in encryption; typically combined with IPsec.
- No native keepalive mechanism (Cisco provides a proprietary solution).
- Adds **24 bytes** of overhead, leading to potential fragmentation issues.

### **Advantages**:

- Supports multicast traffic, enabling routing protocols.
- Allows deployment of any IGP over a GRE tunnel.

### **Recursive Routing Loops**:

- Occur when the tunnel destination is routed through the tunnel itself.
- Avoid using **route filtering** or **different routing protocols** for the transport network and GRE tunnel.


# Multipoint GRE (mGRE)

## Overview

mGRE enables a single GRE interface to support multiple GRE tunnels, reducing configuration complexity.

### **Key Features**:

- Uses a single GRE interface for multiple tunnels.
- Supports unicast, multicast, and broadcast.
- Relies on **Next Hop Resolution Protocol (NHRP)** for dynamic peer discovery.

## Next Hop Resolution Protocol (NHRP)

- Maps tunnel IP addresses to physical IP addresses.
- Allows dynamic learning of peers, unlike static GRE tunnels.


# GRE Over IPsec

## Why Combine GRE and IPsec?

- IPsec ensures **encryption** but does not support multicast or broadcast.
- GRE supports **multicast and broadcast** but lacks encryption.
- Combining both allows for **secure** transport of routing protocols.

### **Implementation Methods**:

1. **Cryptographic Maps**:
   - Packets are encapsulated with GRE and then encrypted with an IPsec cryptographic map.
   - More complex but useful for non-Cisco environments.
2. **Tunnel Protection Mechanism** (**Recommended Approach**):
   - GRE encapsulation occurs first, followed by encryption via IPsec.
   - Simpler configuration and better performance.


---
### 📚 Navigation
- → Next: [Layer 2 VPN](l2-vpn.md) 
- ← Previous: [IPSec Virtual Tunnel Interface (IPSec VTI)](ipsec-vti.md)  
- ↩ Return to: [WAN - Index](../README.md)

