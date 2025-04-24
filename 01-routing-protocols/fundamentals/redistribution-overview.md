# Redistribution Overview

Redistribution enables different routing protocols to exchange routing information, typically at the boundary between administrative domains or during transitional phases such as protocol migrations or network integrations.

---

## 🌉 Use Cases
- **Protocol Migration**: Transitioning from legacy to modern routing protocols.
- **Mixed Protocol Environments**: Connecting networks running different IGPs or BGP.
- **ISP/Enterprise Edge**: Exchanging routes between enterprise networks and ISPs.
- **Mergers & Acquisitions**: Temporarily integrating distinct routing domains.

---

## 🧩 Key Considerations
- **Route Feedback Risk**: Can create loops or inconsistencies without proper filtering.
- **Metric Translation**: Required to ensure path selection works correctly across protocols.
- **Route Control**: Use route maps, distribute lists, and access lists to prevent undesired redistribution.
- **Redistribution Scope**: Limit redistribution to necessary routes only, ideally at specific boundary routers.

---

## 🛠️ Design Guidance
- Prefer **One-Way Redistribution** unless full reachability is required.
- For **Two-Way Redistribution**, implement loop prevention mechanisms.
- Always set **default metrics** explicitly to avoid suboptimal routing.
- **Filter and summarize** to reduce route churn and improve scalability.

For implementation-specific details, examples, and configuration techniques, refer to the [Route Redistribution](./route-redistribution.md) file.

---

### 📚 Navigation
- → Next: [Route Redistribution](./route-redistribution.md)
- ↑ Back to: [Routing Protocols - Fundamentals](../readme.md)

