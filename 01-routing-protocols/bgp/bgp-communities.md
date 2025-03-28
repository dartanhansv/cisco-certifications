# BGP Communities

## What Are BGP Communities?

You might see a BGP community as a label (tag) attached to the prefixes exchanged between two BGP peers, which can later on be used for traffic engineering. Communities make it easier to apply routing policies without dealing with complex prefix lists or route maps.

They allow network engineers to influence routing decisions, control prefix propagation, and prevent routing loops in a more scalable way.

---

## Well-Known BGP Communities

These communities have predefined meanings and are recognized by all BGP implementations.

### **NO-EXPORT** (`65535:65281`)
- Prevents the prefix from being advertised to **EBGP peers**.
- The route stays within the local AS or sub-AS (in Confederations).
- Useful when you don’t want your prefixes to leave your own AS but still need IBGP routers to see them.

### **NO-ADVERTISE** (`65535:65282`)
- Prevents the prefix from being advertised **to any peer** (IBGP or EBGP).
- The route stays only on the router that received it.
- Useful for routes that should remain completely isolated.

### **Local AS** (`65535:65283`)
- The prefix is advertised **only within the local AS** and not to external peers.
- Used in confederation environments to prevent prefixes from leaving a sub-AS.

### **Internet** (`65535:65284`)
- Explicitly marks a prefix as allowed to be advertised freely across the internet.

---

## Avoiding Route Loops with BGP Communities

BGP communities help prevent loops by controlling how prefixes are propagated. 
- **NO-EXPORT** avoids loops by ensuring routes don’t leave a specific AS.
- **NO-ADVERTISE** prevents a prefix from being sent to any BGP peer, stopping any unintended advertisement.
- **Setting custom communities** can help ensure that routes are accepted or denied at specific AS boundaries.

---

## Preventing an AS from Becoming a Transit Network

BGP communities can prevent an AS from being used as transit by influencing route advertisements:

- **Using NO-EXPORT**: Prevents an AS from advertising prefixes learned from one EBGP neighbor to another EBGP neighbor. For example, if AS 10 receives a prefix from AS 1 and applies NO-EXPORT, it will not advertise that prefix to AS 2.
- **Setting a custom community**: Some ISPs provide communities to control whether prefixes should be advertised globally or restricted.
- **AS-path filtering + Communities**: Combining these ensures fine-grained control over transit routes.

---

## BGP Communities vs. Route Tags

| Feature              | BGP Communities | Route Tags (used in IGPs like OSPF/EIGRP) |
|---------------------|-----------------|--------------------------------|
| **Scope** | BGP (Inter-domain) | IGP (Intra-domain) |
| **Function** | Controls route propagation between ASes | Controls route redistribution within an AS |
| **Flexibility** | More scalable; can modify prefixes dynamically | Requires manual filtering with prefix-lists or route-maps |
| **Standardization** | Well-defined standard communities | No global standard, varies by IGP |
| **Use Case** | Traffic engineering, preventing loops, controlling transit | Avoiding redistribution loops and route preference within IGP |

### **Pros and Cons**

✅ **BGP Communities Pros:**
- Scalable and widely supported.
- Less complex than maintaining long prefix lists.
- Can be used for inter-AS policies.

❌ **BGP Communities Cons:**
- Requires cooperation between ASes to be effective.
- Standard communities are limited; ISPs often define their own custom values.

✅ **Route Tags Pros:**
- Simple for intra-AS route control.
- No dependency on BGP.

❌ **Route Tags Cons:**
- Not useful for inter-AS policies.
- Requires additional filters to take effect.

---

## Summary
- BGP communities are **tags used for traffic engineering, route control, and preventing loops**.
- **NO-EXPORT vs. NO-ADVERTISE**:
  - NO-EXPORT: Stops prefixes from going to EBGP peers.
  - NO-ADVERTISE: Stops prefixes from being advertised anywhere.
- They help **avoid route loops and control AS transit**.
- **Compared to route tags**, BGP communities work at the inter-domain level, while route tags control redistribution inside an AS.


