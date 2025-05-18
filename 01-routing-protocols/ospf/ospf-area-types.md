# OSPF Area Types

OSPF has different area types to optimize routing efficiency and reduce resource consumption on routers.

## 1. Backbone Area (Area 0)

- The central hub in a multi-area OSPF topology.
- All other areas must connect directly (or virtually) to Area 0.
- Supports **LSA Types 1, 2, 3, 4, and 5**.
- Used as the **transit area** for routing between non-backbone areas.
- **Best-fit scenario:**
  - Core of the network, ensuring full route propagation between areas.
- 🧠 **Keep in mind:** Full routing info in and out.


## 2. Standard Area (Non-Backbone, Non-Special)

- A non-backbone area that **does not block any LSA types except Type 7**.
- Supports **LSA Types 1, 2, 3, 4, and 5**.
- **Best-fit scenario:**
  - When an area needs full OSPF information and is not part of the backbone.
- 🧠 **Keep in mind:** Full OSPF routes, just not the backbone.


## 3. Stub Area

- **Blocks LSA Type 5 (external routes)** from being received.
- Cannot contain an ASBR (Autonomous System Boundary Router) - no redistribution.
- Instead of external LSAs, the ABR injects a **default route (`0.0.0.0/0`)**.
- Supports **LSA Types 1, 2, and 3**.
- **Best-fit scenario:**
  - Remote sites that don't need external routes but do need inter-area routes.
- 🧠 **Keep in mind:** No external routes in, just a default route for them.


## 4. Totally Stubby Area *(Cisco Proprietary)*

- Blocks **LSA Types 3, 4, and 5**.
- Receives only a **default route** (`0.0.0.0/0`) from the ABR.
- Further reduces routing table size compared to a stub area.
- Supports **LSA Types 1 and 2 only** (3 only for default route).
- **Best-fit scenario:**
  - Very limited remote branches with low-end routers that need only a single path to the rest of the network.
- 🧠 **Keep in mind:** Only default route in, nothing else.


## 5. Not So Stubby Area (NSSA)

- Allows redistribution of external routes into OSPF.
- The ASBR in the area injects routes as **Type 7 LSAs** (not Type 5).
- ABR converts **Type 7 LSAs to Type 5** LSAs to share with Area 0 and beyond.
- **Does not accept Type 5 LSAs** from other areas.
- **Default route is not injected automatically**, must be configured:
  
    ```
    area <area-id> nssa default-information-originate
    ```

- Supports **LSA Types 1, 2, 3, and 7**.
- **Best-fit scenario:**
  - Remote sites that must **inject external routes** (e.g., from EIGRP) into OSPF but **should not learn external routes** from other areas.
- 🧠 **Keep in mind:** **External routes out**, but **none in**.


## 6. Totally NSSA *(Cisco Proprietary)*

- Further restricts routing information within an NSSA.
- Blocks **LSA Types 3, 4, and 5**, only allowing a **default route** from the ABR.
- Still allows local redistribution as Type 7 LSAs.
- ABR converts **Type 7 LSAs into Type 5 LSAs**.
- **Automatically injects a default route** (`0.0.0.0/0`) — in Cisco IOS, but **may not be the default behavior on all platforms**.
- Supports **LSA Types 1, 2, 3 (default only), and 7**.
- **Best-fit scenario:**
  - Remote sites that **must advertise external routes** but should **only use a default route** to reach the rest of the network.
- 🧠 **Keep in mind:** **External out**, **only default route in**.


## 🔑 Key Differences & Use Cases

| **Area Type**        | **Blocks LSA Types**        | **Allows External LSAs?** | **Default Route Injected?** | **Redistribution Allowed?** | **Best-Fit Scenario**                          |
|----------------------|----------------------------|--------------------------|----------------------------|----------------------------|----------------------------------------------|
| Backbone (Area 0)   | None                        | Yes                      | No                         | Yes                        | Core of the network for full OSPF propagation |
| Standard Area       | None (except Type 7)       | Yes                      | No                         | Yes                        | Non-backbone area requiring full OSPF info |
| Stub Area          | 5                           | No                       | Yes                        | No                         | Remote sites that don't need external routes |
| Totally Stubby Area | 3, 4, 5                     | No                       | Yes                        | No                         | Limited remote branches needing only the default route |
| NSSA               | 5                            | Yes (via Type 7 LSAs)    | No (manual configuration)  | Yes                        | Sites injecting external routes via ASBR (LSA 7 → LSA 5 via ABR) but rejecting external routes from other OSPF areas (LSA 5) |
| Totally NSSA       | 3, 4, 5                     | Yes (via Type 7 LSAs)    | Yes                        | Yes                        | Sites injecting external routes via ASBR (LSA 7 → LSA 5 via ABR) but only using a default route to reach other areas (blocks LSA 3, 4, and 5). |


---
### 📚 Navigation
- → Next: [TDB](TDB)  
- ← Previous: [TDB](TDB)  
- ↩ Return to [OSPF](./README.md)
