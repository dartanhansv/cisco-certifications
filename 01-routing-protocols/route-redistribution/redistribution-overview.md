# Route Redistribution Overview

## Administrative Distance

Administrative Distance (AD) is used by routers to select the best route when multiple routing protocols provide information about the same destination. Lower AD = higher trust.

| Route Source   | Default AD |
| -------------- | ---------- |
| Connected      | 0          |
| Static         | 1          |
| EIGRP Summary  | 5          |
| External BGP   | 20         |
| Internal EIGRP | 90         |
| IGRP           | 100        |
| OSPF           | 110        |
| IS-IS          | 115        |
| RIP            | 120        |
| EGP            | 140        |
| External EIGRP | 170        |
| Internal BGP   | 200        |
| Unknown        | 255        |

> Routes with AD of 255 are not installed in the routing table.

---

## Route Redistribution

Redistribution allows routes learned by one routing protocol to be advertised into another. It is common in networks with protocol migrations or multiple domains.

### Key Concepts
- **Seed Metric:** Some protocols require a manual seed metric when redistributing (e.g., EIGRP, RIP).
- **Route Tagging:** Helps to prevent routing loops by marking routes.
- **Filtering:** Use route-maps, prefix-lists, or tags to control which routes are redistributed.

---

## Redistributing OSPF into BGP

### Behavior:
- By default, only OSPF internal routes (Intra- and Inter-area) are redistributed.
- To redistribute external or NSSA routes, explicit keywords are required.

### Keywords:
- `internal`: Intra-area + Inter-area
- `external`: External Type 5 routes
- `nssa-external`: NSSA Type 7 routes

### Example:
```bash
router bgp 65001
 redistribute ospf 1 match external
```

---

## Redistributing EIGRP into OSPF

### Behavior:
- Requires a metric to redistribute into EIGRP.
- OSPF uses Type 2 (E2) external routes by default.

### Example:
```bash
router ospf 1
 redistribute eigrp 100 metric-type 2
```

---

## Loop Prevention Techniques

Loop prevention is critical during redistribution.

### Methods:
- **Route Maps:** Filter or tag specific routes
- **Administrative Distance:** Adjust to prefer the right protocol
- **Prefix Lists:** Limit accepted or advertised routes
- **Tags:** Prevent re-advertising of routes back to the original protocol

---

## References
- [Cisco - Administrative Distance](https://www.cisco.com/c/en/us/support/docs/ip/border-gateway-protocol-bgp/15986-admin-distance.html)
- [Cisco - Redistributing OSPF into BGP](https://www.cisco.com/c/en/us/support/docs/ip/border-gateway-protocol-bgp/5242-bgp-ospf-redis.html)
- [Cisco - Adjusting AD of Received Routes](https://www.cisco.com/c/en/us/support/docs/switches/nexus-9000-series-switches/220166-configure-administrative-distance-of-spe.html)
- [NetworkStraining - Redistribution Example](https://www.networkstraining.com/redistribution-between-cisco-eigrp-ospf/)

