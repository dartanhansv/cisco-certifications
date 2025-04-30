# IPv6 Migration Strategies

Transitioning from IPv4 to IPv6 is essential due to IPv4 address exhaustion and the growing demand for scalable networks. IPv6 migration strategies aim to introduce IPv6 while maintaining interoperability with existing IPv4 infrastructure, ensuring a seamless transition based on business, technical, and operational needs.

---

## 🔀 Core IPv6 Migration Strategies

Organizations adopt one of three primary strategies for IPv6 migration:

- **Dual-stack**: Hosts and networks run IPv4 and IPv6 simultaneously.
- **Tunneling**: IPv6 traffic is encapsulated within IPv4 packets for transport across an IPv4-only infrastructure.
- **Translation**: IPv6 packets are translated into IPv4 and vice versa, enabling communication between native-only hosts.

These strategies help ensure continued connectivity while integrating IPv6.

---

## 🧱 IPv6 Deployment Models

Deployment models define how IPv6 is introduced within networks:

- **Dual-stack model**: IPv4 and IPv6 coexist on hosts and network devices, maintaining separate routing and management.
- **Hybrid model**: Mixes tunneling (e.g., ISATAP, manual tunnels) and dual-stack techniques to extend IPv6 into an IPv4 core.
- **Service block model**: Uses tunneling technologies to provide IPv6 connectivity for a specific module or service block.

> **Note:** The dual-stack model is preferred due to its simplicity and the elimination of tunneling overhead.

---

## 📊 Deployment Model Comparison

| Deployment Model               | Advantages                                                           | Disadvantages                                          |
| ------------------------------ | -------------------------------------------------------------------- | ------------------------------------------------------ |
| **Dual-stack**                 | - No tunneling required<br>- Independent IPv4/IPv6 policies          | - Requires network equipment upgrades                  |
| **Hybrid with ISATAP tunnels** | - Leverages existing infrastructure<br>- No upgrades needed          | - No IPv6 multicast support                            |
| **Hybrid with manual tunnels** | - Maintains independent IPv4 and IPv6 policies                       | - High operational overhead due to many static tunnels |
| **Service block model**        | - Lower impact on existing network<br>- Flexible IPv6 access control | - Requires additional tunneling and equipment          |

### Model Summary

- **Dual-stack model**: Full coexistence of IPv4 and IPv6 on all routers and hosts.
- **Hybrid model**: Tunnels IPv6 traffic over IPv4 while allowing dual-stack clients and servers.
- **Service block model**: Provides IPv6 in isolated sections of the network.

---

## 🌐 Dual-Stack Migration Strategy

Dual-stack (native mode) allows devices to communicate over both IPv4 and IPv6, using the appropriate stack for each connection.

- **DNS Behavior**:
  - AAAA record → IPv6 stack used
  - A record → IPv4 stack used

Since major operating systems prioritize IPv6, this strategy supports a smooth, phased migration.

---

## 🕳️ IPv6 over IPv4 Tunneling Strategy

Tunneling enables IPv6 networks to communicate across an IPv4 backbone by encapsulating IPv6 packets within IPv4 frames.

- **Tunnel endpoints must support both IPv4 and IPv6.**
- **Common use cases**: Border-to-border or border-to-host tunneling.
- **Drawback**: Encapsulation increases overhead, reducing MTU by 20 bytes.

### 🛠️ Manual Tunnels & GRE

- **Manual tunnels** (RFC 4213): Configured with fixed IPv4/IPv6 endpoints.
- **GRE tunnels**: Support IPv6 and other L3 protocols like IS-IS.

---

## 🔄 Automatic Tunnel Mechanisms

### 6to4 (RFC 3056)

- Uses prefix `2002::/16`
- Embeds IPv4 address in IPv6 format
- Border routers forward encapsulated IPv6 packets over IPv4

### 6RD (RFC 5969)

- ISP variant of 6to4 using provider-assigned IPv6 prefixes
- Requires a 6RD Border Relay (BR) router for handling IPv6 traffic

### ISATAP

- Enables intra-site tunneling for IPv6 traffic within IPv4 networks
- Addresses follow format: `prefix:0000:5EFE:IPv4-addr`
- Example: `FE80::5EFE:C0A8:0A0A` (for 192.168.10.10)

---

## 🔁 IPv6/IPv4 Translation Strategy

Translation mechanisms allow IPv6-only hosts to communicate with IPv4-only hosts, eliminating the need for dual-stack.

### 🔧 DNS64 (RFC 6147)

- Synthesizes AAAA records from A records.
- Enables IPv6 clients to connect to IPv4 servers using domain names.
- Works with NAT64 gateways for full translation.

---

### 📚 Navigation
- → Next: [TBD](TBD)  
- ← Previous: [TBD](TBD)  
- ↑ Back to: [TBD](TBD)
