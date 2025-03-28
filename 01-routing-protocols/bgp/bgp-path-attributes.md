# BGP Path Attributes  

## Summary  

When a router receives an update containing an optional attribute, it first checks whether it recognizes that attribute. If it does, the router processes it accordingly and decides whether to propagate it.  

If the router **does not recognize** the attribute, it checks the **transitive bit** in the attribute's code. Some attributes, even if not recognized by the router, might still be useful for other routers along the path. These are called **optional transitive attributes**. They are **propagated** even if a router does not understand them.  

When an unknown **optional transitive** attribute is propagated, the router **sets the "partial" bit** in the attribute header. This bit indicates that at least one router in the path did not recognize the attribute but still forwarded it.  

On the other hand, **optional non-transitive attributes** are not forwarded if a router does not recognize them. These attributes are only used locally and **are dropped** if they are unknown to the receiving router.  

---

## Categories of BGP Path Attributes  

### **Well-Known Attributes**  
These attributes **must** be recognized by all BGP implementations.  

#### **Mandatory Well-Known Attributes** (Always present in BGP updates)  
- **Origin** – Indicates the source of the route:  
  - `i` → Learned from an IGP  
  - `e` → Learned from an EGP  
  - `?` → Redistributed from another source  
- **AS-Path** – Lists the sequence of AS numbers the update has passed through.  
- **Next-Hop** – Specifies the IP address of the next-hop router.  

#### **Discretionary Well-Known Attributes** (Not always present)  
- **Local Preference (Local-Pref)** – Used within an AS to influence route selection (higher is preferred).  
- **Atomic Aggregate** – Indicates that a route has been summarized.  

---

### **Optional Attributes**  
These attributes **may or may not** be recognized by BGP implementations.  

#### **Optional Transitive Attributes** (Forwarded even if unrecognized)  
- **Aggregator** – Specifies which AS and router summarized a route.  
- **Community** – Used for tagging and controlling route policies.  

#### **Optional Non-Transitive Attributes** (Dropped if unrecognized)  
- **Multi-Exit Discriminator (MED)** – Influences inbound traffic from external ASes (lower is preferred).  
