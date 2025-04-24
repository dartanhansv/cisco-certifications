# Route Filtering

## 🔍 Filtering Overview

**Definition**: Filtering involves controlling which routes are allowed into or out of a routing domain, or at redistribution points, to influence traffic flow and avoid routing issues.

### ✅ Benefits of Filtering at Redistribution Points
- Prevents routing loops.
- Reduces suboptimal routing.
- Enhances policy enforcement (e.g., security, compliance).
- Limits visibility of certain routes.

---

## 🚫 Avoiding Transit Traffic

### 🔸 OSPF
- OSPF does **not support LSA filtering within an area**.
- Intra-area traffic flows cannot be filtered directly.
- Area 0 (backbone) is often used as transit for other discontiguous areas.

### 🔸 EIGRP
- Use **stub routers** to avoid making remote sites act as transit points.
- EIGRP stubs:
  - Limit route advertisement.
  - Reduce query propagation.
  - Improve convergence.
- Filtering can help define which networks are reachable or advertised.

### 🔸 BGP
- **Outbound filtering**:
  - Control which prefixes are advertised to ISPs or peers.
  - Apply route maps, prefix lists, or communities.
- **Inbound filtering**:
  - Limit accepted prefixes to prevent bloated routing tables.
  - Ensure only expected networks are learned.

---

## 🛡️ Preventing BGP Transit AS Situations

| Method              | Description                                               |
| ------------------- | --------------------------------------------------------- |
| **Filter-List**     | Match AS paths using regex (e.g., block via AS path ACLs) |
| **No-Export**       | BGP community attribute to limit route propagation        |
| **Prefix-List**     | Match prefixes for inbound/outbound filtering             |
| **Distribute-List** | Control redistribution based on access/control lists      |

> 💡 Use these tools to prevent your network from becoming a transit AS unintentionally.

---

## 🧭 Design Recommendations

- Use **access-lists**, **route-maps**, and **prefix-lists** to:
  - Define which routes should or should not be redistributed.
  - Apply specific metrics during redistribution.
  - Control directionality of route advertisement.

- For **transit traffic optimization**:
  - Avoid making non-core areas or sites transit points.
  - Plan summarization and filtering carefully.
  - Ensure BGP policies reflect business routing intentions.

---



