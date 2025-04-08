# Route Redistribution Cheat Sheet

## Administrative Distance Table (Cisco Default)

| Route Source   | AD Value |
| -------------- | -------- |
| Connected      | 0        |
| Static         | 1        |
| EIGRP Summary  | 5        |
| External BGP   | 20       |
| Internal EIGRP | 90       |
| IGRP           | 100      |
| OSPF           | 110      |
| IS-IS          | 115      |
| RIP            | 120      |
| EGP            | 140      |
| External EIGRP | 170      |
| Internal BGP   | 200      |
| Unknown        | 255      |

> **Note:** AD 255 = Unreachable (route not installed), it is effectively used to **"blackhole"** a route or deny its use.


---

## Redistribution Keywords for OSPF → BGP

| Keyword         | Description               |
| --------------- | ------------------------- |
| `internal`      | Intra + Inter-area routes |
| `external`      | Type 5 (External)         |
| `nssa-external` | Type 7 (NSSA External)    |

---

## Common Loop Prevention Tools

- `route-map` (filter/tag routes)
- `tag` (mark routes during redistribution)
- `prefix-list` (permit/deny specific routes)
- Adjust **AD** (to influence selection)

---
