# IPv6 Overview

IPv6 is the latest version of the Internet Protocol, designed to overcome IPv4 limitations by offering a vastly larger address space, simplified packet headers, improved support for extensions and security, and enhanced capabilities like autoconfiguration and mobility.


#### Introduction
IPv6 offers several enhancements over IPv4, including:
- **Larger Address Space**: Uses 128-bit addresses, supporting more hierarchy levels and simpler autoconfiguration.
- **Globally Unique IP Addresses**: Eliminates the need for NAT.
- **Header Format Efficiency**: Fixed header length reduces processing time.
- **Improved Option Mechanism**: Options are in separate extension headers.
- **Address Autoconfiguration**: Supports dynamic assignment with or without DHCP.
- **Flow Labeling Capability**: Labels packets for special handling (e.g., QoS).
- **Security Capabilities**: Includes IPsec for authentication and privacy.
- **MTU Path Discovery**: Eliminates the need for packet fragmentation.
- **Site Multihoming**: Supports multiple addresses and prefixes for hosts and networks.
- **Support for Mobility**: Allows nodes to maintain connections while changing locations.
- **Eliminates Broadcasts**: Uses multicasts instead of broadcasts.

#### IPv6 Address Representation
- **128-bit Length**: Represented as eight groups of four hexadecimal digits, separated by colons.
- **Hexadecimal Notation**: Each group is written as four hexadecimal digits (0-9, a-f).
- **Colons as Separators**: Groups are separated by colons (:).
- **Leading Zero Compression**: Leading zeros within a group can be omitted.
- **Double Colon (::) for Zero Groups**: Consecutive groups of all zeros can be compressed to a double colon (::), but only once in an address.
- **Example**: `2001:0db8:85a3::8a2e:0370:7334` is a shortened version of `2001:0db8:85a3:0000:0000:8a2e:0370:7334`.

#### IPv4-Mapped IPv6 Addresses
- **Purpose**: Represent IPv4 addresses within the IPv6 address space for compatibility in dual-stack environments.
- **Format**: `::FFFF:IPv4_address` (e.g., `::FFFF:192.0.2.128`).
- **Usage**: Primarily used internally within applications, APIs, and operating systems, not for routing.
- **Deprecated Format**: The previous format `::IPv4_address` (e.g., `::192.0.2.128`) is now deprecated.

#### IPv6 Address Types
- **Unicast**: Identifies a single interface; can be a source or destination address.
- **Anycast**: Routes traffic to the closest interface within a group; can only be a destination address.
- **Multicast**: Reaches a group of hosts; can only be a destination address.

| Unicast Address Type       | Description                                                             |
| -------------------------- | ----------------------------------------------------------------------- |
| Global Unicast             | Used for communication across the internet; globally unique.            |
| Unique Local Address (ULA) | Used for internal networks; not routable on the internet.               |
| Link-Local                 | Used for communication on a single link; not routable beyond that link. |

#### Global Aggregatable IPv6 Address
- **Purpose**: Allows aggregation of routing prefixes to reduce the number of routes in the global routing table.
- **Prefix**: Identified by a fixed prefix of `2000::/3`.
- **Format**: Global Routing Prefix, Subnet ID, and 64-bit Interface ID (usually the device MAC address).

#### Well-Known IPv6 Multicast Addresses
| Multicast Address | Multicast Group                                                |
| ----------------- | -------------------------------------------------------------- |
| FF01::1           | All nodes (interface-local)                                    |
| FF02::1           | All nodes (link-local)                                         |
| FF01::2           | All routers (interface-local)                                  |
| FF02::2           | All routers (link-local)                                       |
| FF02::5           | OSPFv3                                                         |
| FF02::6           | OSPFv3 designated routers                                      |
| FF02::9           | RIPng                                                          |
| FF02::A           | EIGRP routers                                                  |
| FF02::B           | Mobile agents                                                  |
| FF02::C           | DHCP servers/relay agents                                      |
| FF02::D           | All PIM routers                                                |
| FF05::1           | All nodes in the local network site                            |
| FF0x::FB          | Multicast DNS                                                  |
| FF02::1:2         | All DHCP and relay agents on the local network site (RFC 3313) |
| FF05::1:3         | All DHCP servers on the local network site (RFC 3313)          |

#### IPv6 Prefix Allocation
- **Format Prefix (FP)**: Leading bits of an IPv6 address define the address type or other reservations.

| Hexadecimal/Prefix | Allocation                                                                             |
| ------------------ | -------------------------------------------------------------------------------------- |
| 0100::/8           | Reserved, 0100::/64 reserved for discard-only address block                            |
| 2000::/3           | Global unicast address; IANA unicast address assignments are limited within this range |
| 8000::/3           | Reserved for geographic-based unicast addresses                                        |
| FC00::/7           | Unique local unicast                                                                   |
| FE80::/10          | Link-local unicast addresses                                                           |
| FF00::/8           | Multicast addresses                                                                    |

#### Special IPv6 Addresses
- **Unspecified Address**: `0:0:0:0:0:0:0:0` (not forwarded by an IPv6 router).
- **Loopback Address**: `0:0:0:0:0:0:0:1` (similar to IPv4 loopback address `127.0.0.1`).

---

### 📚 Navigation
- → Next: [IPv6 Address Types and Assignment](ipv6-address-types.md)  
- ← Previous: [IPv4 Address Design](ipv4-address-design.md)  
- ↑ Back to: [Network Fundamentals](../readme.md)
