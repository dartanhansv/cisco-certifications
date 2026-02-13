# BGP Confederations

## Summary

BGP Confederations split a single AS into smaller sub-ASes.

### Why

- They are often implemented in large networks to allow the use of different routing policies.

### How It Works

- Within a member AS:
  - Full mesh (follows classic iBGP rules)
  - BGP attributes are not modified

- Intra-confederation eBGP sessions behave **almost** like iBGP:
  - Only the AS-PATH attribute is modified:
    - The intra-confederation AS is prepended to the AS-PATH

- External eBGP sessions (to peers outside the confederation):
  - All intra-confederation ASNs are removed, and the real AS is prepended to the AS-PATH

---

## Configuration

### Identifying an Intra-Confederation eBGP Session

Run `show bgp neighbor x.x.x.x` and look for:

- `external link` – indicates eBGP
- `neighbor under common administration` – indicates a BGP confederation session

---

## Design Guidelines

- Prefer route reflectors for scaling iBGP.
- Whenever possible, avoid using different routing policies within the same AS.
  - If you must use different routing policies, implement BGP confederations.
  - Align intra-confederation ASNs with the physical topology.
- Use private ASNs.

---

> [!WARNING]
> Implementing BGP confederations requires reconfiguring BGP on every router in the AS.
