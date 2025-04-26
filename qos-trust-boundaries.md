# 🚀 Trust States and Boundaries

Traffic marking integrity is critical to ensure that network resources are properly allocated to priority applications. In a QoS deployment, defining where to trust traffic markings — the **trust boundary** — is a major design decision.

> ⚡ **Best Practice**: Always place the **trust boundary as close as possible to the traffic source** to prevent untrusted devices from improperly marking packets.

---

## 🎯 Port Trust States

### ❌ Untrusted
- **Behavior**: Discards any Layer 2 (CoS) or Layer 3 (DSCP) markings.
- **Action**: Sets internal DSCP value to **0**.

### 🏷️ Trust CoS
- **Behavior**: Accepts **Class of Service (CoS)** marking.
- **Action**: Calculates internal DSCP based on a **CoS-to-DSCP mapping** (default or customized).

### 🏷️ Trust DSCP
- **Behavior**: Accepts **DSCP** marking.
- **Action**: Sets internal DSCP to **match** the received value.

---

## 📦 Traffic Shaping vs Policing (Quick Review)

| Feature         | Traffic Shaping                      | Traffic Policing                               |
| --------------- | ------------------------------------ | ---------------------------------------------- |
| Main Goal       | Smooth traffic bursts to steady flow | Enforce rate limits by dropping excess traffic |
| Method          | Buffers excess packets               | Drops or remarks packets immediately           |
| Effect on Delay | Introduces delay                     | No delay for conforming traffic                |
| Risk            | Increased latency                    | Potential TCP retransmissions                  |

- **Traffic Shaping**: Buffers excess traffic to keep transmission within allowed rates, smoothing bursts and preventing congestion.
- **Traffic Policing**: Drops excess traffic immediately, enforcing strict limits but risking retransmissions due to packet loss.

---

# 📚 Navigation
- ↑ Back to: [Network Services](../readme.md)
