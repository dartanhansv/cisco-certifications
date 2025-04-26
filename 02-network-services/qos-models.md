# QoS Models

Quality of Service (QoS) is essential for managing network resources and providing better application experiences. Cisco supports three main models for QoS service differentiation: Best-Effort (BE), Differentiated Services (DiffServ), and Integrated Services (IntServ).

## 🚀 Best-Effort QoS
- **Default Model**: No QoS behaviors to prioritize traffic.
- **Usage**: Not suitable for real-time applications like voice or video; used after prioritizing other important traffic classes.

## 🚀 Integrated Services (IntServ)
- **Real-Time Applications**: Designed for video, multimedia conferencing, and virtual reality.
- **Resource Reservation**: Uses RSVP to request QoS along the end-to-end path.
- **Functions**: Admission control, classification, policing, queuing, and scheduling.
- **Guarantees**: Provides hard QoS guarantees like bandwidth, delay, and packet loss rates end-to-end.

## 🚀 Differentiated Services (DiffServ)
- **Traffic Classes**: Separates traffic into multiple classes to meet varying QoS requirements.
- **Packet Marking**: Uses DSCP values to classify and prioritize traffic.
- **Scalability**: Designed to overcome IntServ limitations, providing cost-effective and scalable QoS.
- **Per-Hop Behavior (PHB)**: Defined by DSCP settings or ACLs, ensuring proper treatment across the network.

### 📊 DSCP Mapping Table

| Application             | DSCP    | Decimal Value |
| ----------------------- | ------- | ------------- |
| Network control         | CS7     | 56            |
| Internetwork control    | CS6     | 48            |
| VoIP                    | EF      | 46            |
| Broadcast video         | CS5     | 40            |
| Multimedia conferencing | AF4     | 34–38         |
| Real-time interaction   | CS4     | 32            |
| Multimedia streaming    | AF3     | 26–30         |
| Signaling               | CS3     | 24            |
| Transactional           | AF2     | 18–22         |
| Network management      | CS2     | 16            |
| Bulk                    | AF1     | 10–14         |
| Scavenger               | CS1     | 8             |
| Best-effort             | default | 0             |

---

### 📚 Navigation
- ↑ Back to: [Network Services](../readme.md)
