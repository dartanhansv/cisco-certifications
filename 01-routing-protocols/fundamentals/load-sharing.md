# Load Sharing in Layer 3 Designs

**Load Balancing** is a key aspect of scalable and resilient Layer 3 designs. Here are the primary considerations:

## IP Routing Protocols and Load Balancing

- **Equal-Cost Load Balancing**:
  - Most IP routing protocols support balancing across multiple equal-cost paths.
  - The `maximum-paths` command adjusts how many equal-cost paths are used (default is 4, max is typically 6).

- **Bandwidth Consistency**:
  - Equal bandwidth among parallel links is crucial for creating equal-cost paths.
  - **EIGRP** can balance across unequal-cost paths using the **variance** command.

## Unequal Bandwidth Paths and Hop-Based Protocols

- **Hop-Based Routing Protocols** (e.g., RIP):
  - Load balance across paths with the same hop count, regardless of actual bandwidth.
  - Can cause **pinhole congestion** when lower-bandwidth links are overused while high-bandwidth links remain underutilized.
  - Best practice: design with equal bandwidth or use bandwidth-aware routing protocols.

## Cisco Router Load Balancing Behavior

Load balancing depends on the **switching method** used:

- **Process Switching**:
  - Balances traffic on a **per-packet** basis.

- **Fast, Autonomous, Silicon, Optimum, Distributed, NetFlow Switching**:
  - Balances traffic on a **per-destination** basis using cached information.

---

### 📚 Navigation
- [➡️ Next: README](./readme.md)
- [🏠 Back to Main: Routing Protocols](../README.md)
- [⬅️ Previous: N/A](#)
