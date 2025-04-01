# OSPF Route Filtering

## Overview
OSPF does not inherently filter routes like distance-vector protocols do. However, filtering can be applied in specific scenarios using **distribute-lists, prefix-lists, route-maps, and area filtering techniques**.

### Why Filter Routes in OSPF?
- Control which routes are advertised or received.
- Prevent routing loops or suboptimal routing.
- Improve network security and efficiency.

---
## Filtering Order
When applying multiple filtering methods, they are processed in the following order:

**Inbound:**
1. **Route-map in** (if applied)
2. **Distribute-list in** (prefix-list or access-list)

**Outbound:**
1. **Distribute-list out** (prefix-list or access-list)
2. **Route-map out** (if applied)

---

## OSPF Route Filtering Methods
### 1. **Distribute-List Filtering**
Distribute-lists filter routes based on an **access-list** or a **prefix-list** and can be applied in two ways:
- **Inbound**: Filters routes from OSPF before adding them to the routing table.
- **Outbound**: Prevents routes from being advertised to neighbors.

#### Example: Filtering Incoming Routes
```bash
access-list 10 deny 192.168.2.0 0.0.0.255
access-list 10 permit any
!
router ospf 1
 distribute-list 10 in
```
- This denies 192.168.2.0/24 from entering the routing table.

#### Example: Filtering Outgoing Routes
```bash
access-list 20 deny 10.1.1.0 0.0.0.255
access-list 20 permit any
!
router ospf 1
 distribute-list 20 out
```
- This prevents 10.1.1.0/24 from being advertised to OSPF neighbors.

### 2. **Prefix-List Filtering**
A more flexible alternative to access-lists, allowing filtering based on prefix length.

#### Example: Filtering Specific Prefixes
```bash
ip prefix-list FILTER deny 10.1.1.0/24
ip prefix-list FILTER permit 0.0.0.0/0 le 32
!
router ospf 1
 distribute-list prefix FILTER in
```
- Blocks 10.1.1.0/24 from entering the routing table while permitting everything else.

### 3. **Route-Map Filtering**
Allows advanced filtering based on multiple conditions.

#### Example: Filtering Based on a Tag
```bash
route-map BLOCK_OSPF deny 10
 match tag 100

route-map BLOCK_OSPF permit 20
!
router ospf 1
 distribute-list route-map BLOCK_OSPF in
```
- Prevents OSPF routes with **tag 100** from being added to the routing table.

### 4. **LSA Filtering (Preventing LSA Flooding)**
Used to filter inter-area routes by stopping LSAs from propagating into an area.

#### Example: Filtering Routes in a Stub Area
```bash
router ospf 1
 area 1 filter-list prefix FILTER in
 area 1 filter-list prefix FILTER out
!
ip prefix-list FILTER deny 192.168.100.0/24
ip prefix-list FILTER permit 0.0.0.0/0 le 32 
```
- Prevents **192.168.100.0/24** from being advertised into or out of **area 1**.

---

### **5. Summarization and Filtering on ABR**
```bash
router ospf 1
 area 1 range 10.0.0.0 255.255.252.0 not-advertise
```
- Prevents ABR from advertising **10.0.0.0/22** to other areas.

---

These filtering mechanisms help control routing behavior, limit unnecessary route advertisements, and optimize OSPF performance in large networks.


---

