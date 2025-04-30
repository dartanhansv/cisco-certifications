## IPv6 Mechanisms
IPv6 introduces a set of mechanisms to ensure reliable operation, efficient communication, and security across networks. These mechanisms include enhanced control messaging, address discovery, dynamic configuration, routing, and integrated security.

### 🌐 ICMPv6
- All IPv6 nodes must implement ICMPv6 to perform network layer functions.
- ICMPv6 performs diagnostics (ping), reports errors, and provides reachability information.
- Although IPv4 ICMP uses IP protocol 1, IPv6 uses a Next Header field number of 58.
- It is used by other IPv6 mechanisms to determine neighbor availability, path MTU, destination link-layer address, or port reachability.

**Informational Messages**:
- Echo request
- Echo reply

**Error Messages**:
- Destination unreachable
- Packet too big
- Time exceeded
- Parameter problem

**Destination-Unreachable Details**:
- No route to destination
- Destination administratively prohibited
- Address unreachable
- Port unreachable

### 🤝 IPv6 Neighbor Discovery Protocol (ND)
- IPv6 does not implement ARP, which is used in IPv4. Instead, IPv6 implements the Neighbor Discovery (ND) protocol.
- ND searches for alternative routers if the primary router fails.
- Hosts use ND to implement:
  - Plug-and-play functions that discover all other nodes in the same link.
  - Check for duplicate addresses.
  - Find routers in the link.

**Functions**:
- Stateless address autoconfiguration
- Duplicate address detection
- Prefix discovery
- Parameter discovery
- Address resolution
- Router discovery
- Next-hop determination
- Neighbor unreachability detection
- Redirect messages

**ICMPv6 Messages Used by ND**:
- Router advertisement (RA): Sent by routers to advertise their presence and link-specific parameters.
- Router solicitation (RS): Sent by hosts to request RA messages from local routers.
- Neighbor solicitation (NS): Sent by hosts to request link-layer addresses of other hosts (also used for duplicate address detection).
- Neighbor advertisement (NA): Sent by hosts in response to NS messages.
- Redirect: Sent to a host to notify it of a better next hop to a destination.

### 🖥️ IPv6 Name Resolution
- IPv4 uses A records for FQDN-to-IPv4 address resolution. DNS adds AAAA records for name-to-IPv6 address resolution.
- **AAAA Record**: Returns an IPv6 address to the requesting host.
- **Dual-Stack Support**: Applications decide which stack to use and request AAAA or A records accordingly.
- **Priority**: Current DNS implementations prioritize A records over AAAA records.

### 📏 Path MTU Discovery
- IPv6 does not allow packet fragmentation by routers; only sending hosts can fragment packets.
- **MTU Requirement**: Every link must have an MTU of 1280 bytes or greater.
- **Discovery Process**: Nodes send ICMPv6 packet-too-big messages to the sending host if the packet exceeds the outgoing interface MTU.

### 🛠️ IPv6 Address-Assignment Strategies

**Manual Configuration**:
- Devices such as routers, switches, servers, and firewalls should have IPv6 addresses configured manually.

**Stateless Address Autoconfiguration (SLAAC) of Link-Local Address**:
- Hosts obtain link-local addresses automatically upon interface initialization.

**Process**:
- Duplicate address detection.
- Joining the all-nodes multicast group.
- Sending neighbor-solicitation messages.
- Receiving neighbor advertisements.
- Using the link-local prefix FE80::/10.

**SLAAC of Globally Unique IPv6 Address**:
- **Process**:
  - Router advertisement (RA) messages.
  - Learning the prefix from RA messages.
  - Creating the client identifier by splitting the local MAC address and adding FF:FE in the middle.
  - Merging the prefix and identifier to form the globally unique address.

### 🛡️ DHCPv6
- Provides stateful address assignment and supports renumbering without routers.
- Offers more control than stateless autoconfiguration.

### ⚡ DHCPv6 Lite
- **SLAAC Simplicity**: Simpler than DHCPv6 but cannot send DNS parameters.
- **Process**:
  - Client performs SLAAC to obtain its IPv6 address.
  - Client sends a DHCP information request to the router.
  - Router responds with the requested information.

### 🔒 IPv6 Security
- IPv6 natively supports IPsec, mandated at the operating system level for all IPsec hosts.

**Extension Headers**:
- Carry IPsec AH and ESP headers.
  - **AH (Authentication Header)**: Provides authentication and integrity (defaults to MD5).
  - **ESP (Encapsulating Security Payload)**: Provides confidentiality by encrypting the payload (defaults to DES-CBC).



---

### 📚 Navigation
- → Next: [IPv6 Routing Protocols](ipv6-routing-protocols.md)  
- ← Previous: [IPv6 Address Design](ipv6-address-design.md)  
- ↑ Back to: [TDB](TBD)
