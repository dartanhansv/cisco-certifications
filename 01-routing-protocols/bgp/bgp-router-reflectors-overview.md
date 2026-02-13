# BGP Router Reflectors

A router reflector (RR) is a BGP node that overrides the split-horizon rule by advertising ("reflecting") iBGP-learned routes to other iBGP peers.

Once deployed, internal routers form iBGP sessions with the RR instead of forming a full mesh with each other. This solves the iBGP scalability issue but also introduces a potential single point of failure.

For redundancy and resiliency, deploy a cluster of two or more router reflectors.

---

## BGP Rules

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

### Summary

Routes received from:

- eBGP peers → Advertised to eBGP, non-client iBGP, and RR client peers.
- RR clients → Advertised to eBGP, non-client iBGP, and other RR clients.
- Non-client iBGP peers → Advertised to eBGP peers and RR clients only (not to other non-client iBGP peers).
