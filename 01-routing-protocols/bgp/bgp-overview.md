# BGP Overview

## Introduction to BGP
Border Gateway Protocol (BGP) is the protocol that holds the internet together. It is an **exterior gateway protocol (EGP)** used to exchange routing information between **autonomous systems (ASes)**. Unlike interior routing protocols (OSPF, EIGRP, etc.), which find the shortest path, BGP focuses on **policy-based routing** to control traffic flow.

### Why is BGP the Internet Protocol?
- BGP allows **scalability** by handling millions of routes.
- Uses **path vector** logic instead of link-state or distance-vector.
- Provides **policy control** over inbound and outbound routing decisions.
- Ensures **redundancy and resiliency** in multi-homed networks.
---
## How BGP Works
BGP establishes **peer relationships** with other routers (neighbors) using **TCP (port 179)**. Once a session is established, BGP exchanges routing information using **NLRI (Network Layer Reachability Information)**.

### BGP Message Types
- **Open** – Establishes the session between BGP peers.
- **Keepalive** – Ensures the peer relationship remains active.
- **Update** – Advertises new routes or withdraws old ones.
- **Notification** – Sent when an error occurs, causing session termination.

## Basic BGP Configuration
BGP is manually configured using the **AS number** and **neighbor relationships**.

### Example: eBGP Configuration
```sh
router bgp 65001
  neighbor 192.168.1.2 remote-as 65002
  network 203.0.113.0 mask 255.255.255.0
```

### Example: iBGP Configuration
```sh
router bgp 65001
  neighbor 192.168.1.2 remote-as 65001
  neighbor 192.168.1.3 remote-as 65001
```
- **eBGP** is used between different ASes.
- **iBGP** is used within the same AS and requires **full mesh** (or route reflectors).

---
## BGP Route Filtering
Route filtering is used in BGP to control which routes are accepted and advertised. Filtering can be applied using:
- **Prefix lists**: Filters based on network prefixes.
- **AS-path filters**: Filters based on the AS-PATH attribute.
- **Route-maps**: More granular filtering with multiple conditions.

### **Filtering Order**
**Inbound Routes:**
1. Route-map (in)
2. AS-path filter (Filter-list in)
3. Prefix-list (in)

**Outbound Routes:**
1. Prefix-list (out)
2. AS-path filter (Filter-list out)
3. Route-map (out)

### **Example - Inbound Filtering**
```bash
ip prefix-list DENY-PREFIXES deny 10.0.0.0/8 le 32
ip prefix-list ALLOW-OTHERS permit 0.0.0.0/0 le 32

route-map FILTER-INBOUND deny 10
 match ip address prefix-list DENY-PREFIXES

route-map FILTER-INBOUND permit 20
 match ip address prefix-list ALLOW-OTHERS

router bgp 65001
 neighbor 192.168.1.2 remote-as 65002
 neighbor 192.168.1.2 route-map FILTER-INBOUND in
```

### **Example - Outbound Filtering**
```bash
ip as-path access-list 1 permit ^65001$

route-map FILTER-OUT permit 10
 match as-path 1

router bgp 65001
 neighbor 192.168.1.2 remote-as 65002
 neighbor 192.168.1.2 route-map FILTER-OUT out
```
---
## BGP Peers
BGP peer relationships are established using the `neighbor` command. By default, eBGP peers must be directly connected unless `ebgp-multihop` is configured.

## BGP Peer Groups

BGP **peer groups** allow multiple neighbors to share the same configuration, improving efficiency.
- Outgoing updates are prepared for the **peer group** and replicated to other group members.
- Individual neighbor configurations override peer group settings only for **incoming updates**.

### Example: Configuring Peer Groups
```sh
router bgp 65001
  neighbor PEER-GROUP peer-group
  neighbor PEER-GROUP remote-as 65002
  neighbor 192.168.1.2 peer-group PEER-GROUP
  neighbor 192.168.1.3 peer-group PEER-GROUP
```

## Policy-Based Routing (PBR)
PBR allows traffic to be forwarded based on policies rather than the routing table.

### **Set IP Default Next-Hop**
Used when the destination IP is **not** in the Routing Information Base (RIB).

**Use Case:**
- Redirect traffic to a specific ISP if a route is missing in the main routing table.

**Example:**
```bash
route-map PBR-DEFAULT-NH permit 10
 match ip address ACL-PBR
 set ip default next-hop 192.168.1.1

interface GigabitEthernet0/1
 ip policy route-map PBR-DEFAULT-NH
```

### **Set IP Next-Hop**
Used when the destination IP **is** in the RIB, ensuring normal routing is preferred.

**Use Case:**
- Force certain traffic to take a different path even when it exists in the routing table.

**Example:**
```bash
route-map PBR-NH permit 10
 match ip address ACL-PBR
 set ip next-hop 192.168.2.1

interface GigabitEthernet0/1
 ip policy route-map PBR-NH
```

## Additional BGP Concepts
- **BGP Route Reflectors** – Reduce the need for full-mesh iBGP by allowing selected routers to reflect routes.
- **BGP Confederations** – Divide large ASes into smaller sub-ASes to improve scalability.
- **Multiprotocol BGP (MP-BGP)** – Supports IPv6, VPNs, and multicast routing.

---
