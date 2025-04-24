---

# 🔄 Graceful Restart (GR)

Graceful Restart (GR) is a high availability mechanism used by routing protocols to minimize disruption during control plane failures, such as routing process restarts or supervisor failovers. It allows routers to preserve forwarding state while re-establishing control plane adjacencies.

---

## 🎯 Purpose and Benefits

- **Minimize traffic disruption**: Maintains forwarding entries during a restart.
- **Fast reconvergence**: Allows routing peers to maintain the session and forward traffic.
- **Non-Stop Forwarding (NSF)**: Often used in tandem with GR to preserve data plane operations.

---

## 🔍 How It Works

1. **GR-Capable Router**: Notifies neighbors during the restart that it is performing a graceful restart.
2. **GR-Aware Neighbors**:
   - Retain the forwarding state.
   - Maintain the session during a predefined grace period.
3. **Recovery Phase**:
   - The restarting router re-learns topology information.
   - Routing tables are re-synchronized without dropping the session.

⏱️ **Grace Period**: Timer during which the restarting router must re-establish adjacencies, typically configured per protocol.

---

## 🤝 Protocol Support

| Protocol | GR Support          | NSF Integration |
| -------- | ------------------- | --------------- |
| OSPF     | ✅ RFC 3623          | Yes             |
| BGP      | ✅ RFC 4724          | Yes             |
| IS-IS    | ✅ RFC 5306          | Yes             |
| EIGRP    | ✅ Cisco proprietary | Yes             |

> NSF and GR work together: NSF maintains data plane; GR maintains control plane peering.

---

## 🧠 Considerations

- **Symmetric Support**: GR requires support on both peers.
- **Timer Configuration**: Grace periods must be consistent across devices.
- **State Refresh**: Peers must support state refresh mechanisms.
- **Failure Handling**: If GR fails, full reconvergence occurs.

---

## 🚫 Limitations

- **No topology change awareness** during GR — stale routes may exist until reconvergence.
- **Interoperability**: Must be verified between vendors or different IOS versions.
- **Not a replacement for true high availability** (e.g., ISSU or clustering).

---

### 📚 Navigation
- [➡️ Coming Soon](../lan/readme.md)
- [🏠 Return to Folder](../lan/readme.md)
- [⬅️ Platform Abstraction (2.1.b)](platform-abstraction.md)
