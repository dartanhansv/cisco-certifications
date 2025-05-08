# 🎯 IPv6 Address Design

IPv6 addressing design focuses on efficient subnetting, hierarchical allocations, and scalability to accommodate the vast address space provided by 128-bit addresses. By properly planning IPv6 address distribution across LANs and WANs, organizations can simplify route summarization, support future growth, and ensure address independence from service providers when necessary.


---

## 🧩 Planning for Addressing with IPv6
When designing LAN subnets with IPv6, using a `/64` subnet is recommended. This is similar to a `/24` in IPv4, providing:
- Ample addresses for devices.
- Room for future growth.
- Simplified subnet aggregation.
- Reduced renumbering effort.

> ⚡ **Tip:** Always design with `/64` for standard subnets to enable Stateless Address Autoconfiguration (SLAAC).

If you receive IPv6 addresses from an ISP, you may need to renumber if you switch providers.  
To avoid this:
- Obtain an IPv6 block directly from a **Regional Internet Registry (RIR)**.

**Global unicast addresses** are allocated from the `2000::/3` block.

**The five RIRs are:**
- **AfriNIC**: Africa
- **APNIC**: Asia Pacific
- **ARIN**: Canada, United States, Caribbean
- **LACNIC**: Latin America, Caribbean
- **RIPE NCC**: Europe, Middle East, Central Asia

---

## 🧩 IPv6 Address Allocation Strategies

### 🏗️ Partly Linked IPv4 Address into IPv6
- Match IPv6 `/64` subnets with existing IPv4 `/24` subnets.
- Align VLAN numbers and simplify migration.

> ⚡ **Caution:** Does not work well for point-to-point links (e.g., `/30`).

### 🏗️ Whole IPv4 Address Linked into IPv6
- Embed the entire IPv4 address into the IPv6 least significant bits.
- Example: IPv4 `172.16.0.1` → inserted into IPv6.

> ⚡ **Drawback:** Address relationships are not human-readable.

### 🏗️ Allocation Based on Location and/or Type
- Reserve bits to classify:
  - **Location** (e.g., data center, branch, edge).
  - **Device type** (e.g., router, switch, server).
- Remaining bits identify VLANs or subnets within the site.

---

## 🧩 Design Recommendations

### 🚀 Route Summarization
- Plan address blocks to allow summarization.
- **Benefits:**
  - Reduces route table size.
  - Decreases CPU processing for route computation.
  - Enables scalable network growth.

### 🚀 IPv6 Private Addressing
- Private addresses are **Unique Local Addresses (ULAs)**, using `FC00::/7`.
- Avoid NAT (Network Address Translation) unless absolutely necessary.

> ⚡ **Important:**  
> The IETF does not recommend NAT66 for IPv6. Use ULAs only when truly required.

---

## 🧩 IPv6 Addressing for the Enterprise

IPv6 address assignment is hierarchical:
- **IANA → RIRs → LIRs (ISPs) → Enterprises/Consumers**

**Typical address block sizes:**
- ISPs: `/32`
- Large enterprises: `/40`
- Small companies: `/56`
- Home users: `/64`

> Example:  
> A `/48` block (`2001:db8:abcd::/48`) provides **65,536** `/64` subnets.

---

## 🧩 IPv6 vs IPv4: Key Comparisons

| Characteristic          | IPv6                                 | IPv4                           |
| :---------------------- | :----------------------------------- | :----------------------------- |
| Address Length          | 128 bits                             | 32 bits                        |
| Address Representation  | Hexadecimal                          | Dotted decimal                 |
| Header Length           | Fixed (40 bytes)                     | Variable                       |
| Upper-Layer Protocols   | Next Header field                    | Protocol Type field            |
| Link Address Resolution | ND (Neighbor Discovery)              | ARP                            |
| Address Configuration   | SLAAC or Stateful DHCP               | Stateful DHCP                  |
| DNS Record Type         | AAAA                                 | A                              |
| Routing Protocols       | EIGRPv6, OSPFv3, RIPng, IS-IS (IPv6) | EIGRP, OSPFv2, RIPv2, IS-IS    |
| QoS Fields              | Traffic Class, Flow Label, DSCP      | IP Precedence, TOS field, DSCP |
| Private Addresses       | ULAs (FC00::/7)                      | RFC 1918                       |
| Fragmentation           | Sending host only                    | Sending host and routers       |
| Loopback Address        | `::1`                                | `127.0.0.1`                    |
| Scope Types             | Unicast, Anycast, Multicast          | Unicast, Broadcast, Multicast  |

---

### 📚 Navigation
- → Next: [IPv6 Routing Protocols](./ipv6-routing-protocols.md)  
- ← Previous: [IPv6 Subnetting](./ipv6-subnetting.md)  
- ↑ Back to: [IPv6](./README.md)
