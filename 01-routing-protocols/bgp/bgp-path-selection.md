# BGP Best Path Selection

## Selection Process
BGP uses a series of attributes to determine the best path to a destination. The decision-making process follows this order:

1. **Highest Weight** (Cisco-specific)
2. **Highest Local Preference**
3. **Locally Originated Routes**
4. **Shortest AS_PATH**
5. **Lowest Origin Type**
6. **Lowest MED**
7. **Prefer eBGP over iBGP Paths**
8. **Lowest IGP Metric to Next-Hop**
9. **Oldest Path** (to maintain stability)
10. **Lowest Router ID**
11. **Lowest Neighbor IP Address**

## Key Attributes & Use Cases

### **Weight (Cisco-Specific)**
- First parameter analyzed in the path selection process.
- Configured locally and is not propagated to other routers.
- Higher value is preferred 
  - Range: 0 - 65535
  - Default: 32768 for locally originated routes, 0 otherwise.

**Use Case:**
- Used when a router has multiple exit points from its AS.
- Helps control outbound traffic flow.

---
### **Local Preference (Local-Pref)**
- Second parameter analyzed.
- Propagated to **iBGP neighbors only** within the AS.
- Higher value is preferred 
  - Range: 0 - 4294967295 
  - Default: 100

**Use Case:**
- Influences outbound traffic when multiple exit points exist.
- Ensures consistency in exit point selection across the AS.

**Choosing Between Weight and Local-Pref:**
- **Weight:** Affects only the local router.
- **Local-Pref:** Applies to all routers in the AS.
- **Use Weight when fine-tuning a single router’s decision.**
- **Use Local-Pref when enforcing a policy across the AS.**

---
### **Locally Originated Routes**
- Third parameter analyzed.
- Routes originated by the local router (via `network` statement or redistribution) are preferred over those learned from others.

**Use Case:**
- Prioritizes locally injected routes.

---
### **AS-Path**
- Fourth parameter analyzed.
- Represents the list of ASes a route traverses.
- Can be manipulated using **AS-Path Prepending** to make a path less attractive.
- **Shorter AS-Path is preferred.**

**Use Case:**
- Controls inbound traffic by influencing how external ASes select routes to your AS.
- Useful in multi-homed environments.

---
### **Origin Type**
- Fifth parameter analyzed.
- Indicates how a prefix was learned:
  - **IGP (i)** - Most preferred
  - **EGP (E)** - Less preferred
  - **Incomplete (?)** - Least preferred (e.g., static routes, redistributions)

**Use Case:**
- Helps differentiate between different sources of a route.
- Less commonly used for direct traffic manipulation.

---
### **Multi-Exit Discriminator (MED)**
- Sixth parameter analyzed.
- Used to influence **inbound** traffic into an AS when multiple entry points exist.
- **Lower MED is preferred** (Default: 0).
- Propagated to iBGP neighbors but **not beyond the receiving AS**.

**Use Case:**
- Ensures optimal inbound traffic flow in multi-homed setups.
- Often used by ISPs to guide incoming traffic across multiple connections.

---
### **eBGP vs iBGP Preference**
- Seventh parameter analyzed.
- eBGP-learned routes are **always** preferred over iBGP-learned routes (unless explicitly changed).

**Use Case:**
- Ensures external routes are prioritized over internal ones.

---
### **IGP Metric to Next-Hop**
- Eighth parameter analyzed.
- **Lower IGP metric is preferred.**
- Ensures the shortest internal path is used to reach the BGP next-hop.
- Crucial for iBGP, as next-hop reachability is required for route selection.

**Use Case:**
- Helps optimize internal routing decisions when multiple BGP paths exist.
- Ensures that next-hop addresses are reachable within the AS.

---
### **Oldest Path (Stability Factor)**
- Ninth parameter analyzed.
- If all else is equal, the oldest route is preferred to maintain stability.

**Use Case:**
- Prevents frequent route flapping.

---
### **Router ID & Neighbor IP (Final Tie-Breakers)**
- If all other attributes are equal, the route from the lowest **Router ID** is preferred.
- If Router IDs are the same, the route from the lowest **neighbor IP address** is selected.

**Use Case:**
- Acts as the ultimate tiebreaker when all else is equal.

---

## **Real-World Applications** 
📌 ***Must-Know for cert exams***
### **Scenario 1: Choosing the Best Exit Point for Outbound Traffic**
- Use **Local Preference** to influence which external link traffic exits from within an AS.
- Example: Data centers using multiple ISPs may set higher **Local Pref** for a preferred ISP.

### **Scenario 2: Influencing Inbound Traffic**
- Use **AS-Path Prepending** to make one path look longer (less preferred).
- Use **MED** to signal preferred entry points into the AS (only if the upstream ISP honors it).

### **Scenario 3: Preventing Suboptimal Routing**
- **Weight** can be used on a single router to enforce a preferred outbound path without affecting the entire AS.
- Ensuring **Next-Hop Reachability** is crucial in iBGP environments, requiring redistribution into an IGP.

---

