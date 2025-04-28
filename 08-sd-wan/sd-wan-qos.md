# QoS in SD-WAN

Cisco’s SD-WAN solution includes several QoS features for advanced traffic prioritization and network policies:

- **Bidirectional Forwarding Detection (BFD)**
- **Application-aware Routing**
- **Interface Queuing with Low-Latency Queueing (LLQ)**

## Bidirectional Forwarding Detection (BFD)

WAN edge routers use BFD to probe and measure transport link performance, providing information on latency, jitter, and loss. This helps determine the best paths and gathers data on interface status and IPsec tunnel MTU. BFD detects transport link failures in subseconds and measures path liveliness and quality on all WAN edge routers.

**Characteristics of BFD in SD-WAN**:
- Runs inside IPsec tunnels
- Operates in echo mode
- Automatically invoked during IPsec tunnel establishment
- Cannot be disabled

# Multicast over SD-WAN

- **PIM-SM Support**: Cisco SD-WAN supports only Protocol Independent Multicast - Sparse Mode (PIM-SM).
- **Optimized Packet Distribution**: Eliminates packet replication on the ingress router, which is connected to the multicast source.
- **Replicator vEdge**: The ingress router forwards multicast streams to a vEdge router configured as a replicator.

## How It Works

- **Replicator vEdge**: Forwards streams to multicast receivers.
- **PIM Rendezvous Point (RP)**: Not an SD-WAN device; vEdge routers do not support RP functionality.
- **Auto-RP**: Supported for distributing RP-to-group mapping information to local-site PIM routers.
- **IGMP Version 2**: vEdge routers support IGMP v2 to process receiver membership reports for hosts in a particular VPN to determine if traffic should be forwarded.

---

### 📚 Navigation
- → Next: [TD](TD)  
- ← Previous: [TD](TD)  
- ↑ Back to: [TD](TD)
