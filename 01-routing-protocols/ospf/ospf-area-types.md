# OSPF Area Types

OSPF has different area types to optimize routing efficiency and reduce resource consumption on routers.

## 1. Backbone Area (Area 0)
- The central hub of an OSPF network. All other areas must connect to Area 0.
- Ensures full network visibility by transmitting routing information between non-backbone areas.
- Supports **LSA Types 1, 2, 3, 4, and 5**.
- **Best-fit scenario:**
  - Used as the main transit area for inter-area communication in multi-area OSPF networks.

---

## 2. Standard Area (Non-Backbone)
- Operates like the backbone area but does not function as a transit hub.
- Supports all types of LSAs: **1, 2, 3, 4, and 5**.
- **Best-fit scenario:**
  - When full OSPF routing information is needed without restrictions.

---

## 3. Stub Area
- **Blocks LSA Type 5 (External LSAs)**, which prevents external routes (redistributed from BGP, EIGRP, etc.).
- **Does not support redistribution** of external routes within the area.
- The **ABR injects a default route (`0.0.0.0/0`)** to provide external connectivity.
- Supports **LSA Types 1, 2, and 3**.
- **Best-fit scenario:**
  - When the area does not need external routes but requires inter-area routes (e.g., remote branch offices with no direct internet access).

---

## 4. Totally Stubby Area *(Cisco Proprietary Feature)*
- **Blocks LSA Types 3, 4, and 5**, allowing only an injected default route.
- **Only receives a default route** (`0.0.0.0/0`) from the ABR.
- Supports **LSA Types 1, 2, and 3 (only for the default route)**.
- **Best-fit scenario:**
  - Ideal for low-end routers in remote branches that only need a single route to reach the entire OSPF network.
  - Further reduces routing table size compared to a stub area.

---

## 5. Not So Stubby Area (NSSA)
- Allows redistribution of external routes **but does not accept Type 5 LSAs**.
- Redistributed routes are **converted into Type 7 LSAs**.
- **ABR converts Type 7 LSAs into Type 5 LSAs** for propagation into Area 0.
- **Default routes are not injected automatically**—must be manually configured.
- Supports **LSA Types 1, 2, 3, and 7**.
- **Best-fit scenario:**
  - When an area needs to **redistribute external routes into OSPF** but should **not receive other external LSAs**.

---

## 6. Totally NSSA *(Cisco Proprietary Feature)*
- **Blocks LSA Types 3, 4, and 5**, except for a manually redistributed Type 7 LSA.
- **Automatically injects a default route (`0.0.0.0/0`)**.
- **ABR converts Type 7 LSAs into Type 5 LSAs**.
- Supports **LSA Types 1, 2, 3 (default route only), and 7**.
- **Best-fit scenario:**
  - When an NSSA needs to **redistribute external routes but also minimize inter-area LSA overhead**.
  - Ideal for remote sites that **must advertise external routes but should not store full inter-area information**.

---

## Key Differences & Best Use Cases

| **Area Type**           | **Blocks Type 3** | **Blocks Type 4** | **Blocks Type 5** | **Supports Type 7** | **Best Scenario**                                                    |
| ----------------------- | ----------------- | ----------------- | ----------------- | ------------------- | -------------------------------------------------------------------- |
| **Backbone (0)**        | ❌                 | ❌                 | ❌                 | ❌                   | Core transit area                                                    |
| **Standard Area**       | ❌                 | ❌                 | ❌                 | ❌                   | Full OSPF routing with no restrictions                               |
| **Stub Area**           | ❌                 | ❌                 | ✅                 | ❌                   | Remote sites with no external routes                                 |
| **Totally Stubby Area** | ✅                 | ✅                 | ✅                 | ❌                   | Low-end routers in remote sites needing a default route only         |
| **NSSA**                | ❌                 | ❌                 | ✅                 | ✅                   | Redistribution of external routes without full external LSA flooding |
| **Totally NSSA**        | ✅                 | ✅                 | ✅                 | ✅                   | Redistribution with minimal LSA overhead                             |

---
