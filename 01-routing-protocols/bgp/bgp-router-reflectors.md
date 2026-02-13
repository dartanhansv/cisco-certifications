# BGP Router Reflectors

A router reflector (RR) is a BGP node that overrides the iBGP split-horizon rule by advertising ("reflecting") iBGP-learned routes to other iBGP peers.

Once deployed, internal routers form iBGP sessions with the RR instead of forming a full mesh with each other. This solves the iBGP scalability issue but also introduces a potential single point of failure.

For redundancy and resiliency, deploy a cluster of two or more router reflectors.

---

## BGP Advertisement Rules

### Without a Router Reflector

After a route is received:

- An eBGP route can be advertised to any eBGP or iBGP neighbor.
- An iBGP route can be advertised to any eBGP neighbor.
- An iBGP route is not advertised to other iBGP neighbors (split-horizon rule).

---

### With a Router Reflector

The same baseline rules apply, with the following modifications:

1. An eBGP route can be advertised to any eBGP or iBGP neighbor.
2. An iBGP route can be advertised to any eBGP neighbor.
3. An iBGP route is not advertised to other non-client iBGP neighbors (split-horizon rule).

Additional behavior introduced by the RR:

1. Routes learned from non-client iBGP peers can be advertised to RR clients.
2. Routes learned from RR clients can be advertised to:
   - eBGP neighbors
   - Non-client iBGP neighbors
   - Other RR clients

---

## Loop Prevention Mechanisms

Route Reflectors introduce two additional attributes for loop prevention:

- **Cluster ID**
- **Originator ID**

### Cluster ID

- Identifies a Router Reflector cluster.
- Each reflected route carries a **Cluster List** attribute.
- Every RR that reflects the route appends its Cluster ID to the Cluster List.
- An RR rejects a route if its own Cluster ID appears in the Cluster List.

This prevents reflection loops between RRs in the same cluster.

---

### Originator ID

- Represents the Router ID of the iBGP speaker that originally injected the route.
- The first RR that reflects the route sets the Originator ID attribute (optional, non-transitive).
- Any router discards a route if its own Router ID appears as the Originator ID.

This prevents a router from accepting its own route after reflection.

---

## BGP Path Selection with Reflected Routes

Standard BGP best-path selection is performed first:

- Weight
- Local Preference
- AS_PATH length
- Origin
- MED
- eBGP over iBGP

If multiple iBGP paths remain equal, the following RR-specific tie-breakers apply:

1. Non-reflected routes are preferred over reflected routes  
   (Non-reflected routes have no Originator ID attribute.)

2. Between reflected routes, the path with the shorter Cluster List is preferred.

These rules ensure deterministic behavior and reduce suboptimal reflection paths.

---

## Router Reflector Design Guidelines

### RR Clusters

- All redundant RRs in the same cluster must use the same Cluster ID.
- Each cluster must use a unique Cluster ID.
- All RRs in a cluster should maintain iBGP sessions with all clients in that cluster.

This ensures full route visibility and consistent reflection behavior.

---

### Hierarchical Route Reflectors

Used in very large-scale networks:

- Multiple RR clusters are deployed.
- One RR per cluster may act as a top-level RR.
- Top-level RRs form a full-mesh iBGP among themselves.
- Top-level RRs should not maintain additional iBGP sessions outside their role.
- Redundant non-top-level RRs do not require iBGP sessions between themselves.

This design reduces session count while maintaining scalability.

---

### RR Clients

RR clients may:

- Maintain any number of eBGP sessions.
- Establish iBGP sessions only with their configured Route Reflectors.
