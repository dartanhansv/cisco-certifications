# OSPF Adjacency and Neighbor States

## OSPF Hello Protocol
OSPF routers use **Hello packets** to discover and maintain neighbor relationships. These packets are sent periodically and contain essential parameters that must match for routers to become neighbors.

### Hello Packet Key Fields
- **Router ID**: Unique identifier for each OSPF router.
- **Area ID**: Must match between neighbors.
- **Authentication Password**: If authentication is enabled, passwords must match.
- **Hello and Dead Intervals**: Must be identical between neighbors.
- **Stub Area Flag**: Must match if an area is configured as a stub.
- **MTU Size**: Mismatched MTU settings can prevent adjacency formation.

### OSPF Hello Timer Defaults
- **10 seconds** for **point-to-point** and **broadcast** networks.
- **30 seconds** for **NBMA (Non-Broadcast Multi-Access)** networks.

## OSPF Neighbor States
OSPF routers go through the following states before achieving full adjacency:

### **1. Down**
- No Hello packets have been received from the neighbor.

### **2. Init**
- A Hello packet has been received, but the sending router’s **Router ID** is not listed in it.
- Indicates that the neighbor has not yet acknowledged our presence.

### **3. 2-Way**
- The router sees its own **Router ID** in the received Hello packet.
- A bidirectional communication is established.
- **DR (Designated Router) and BDR (Backup Designated Router) election occurs in multi-access networks**.
- Routers remain in **2-Way** with non-DR/BDR routers.

### **4. Exstart**
- The Master-Slave relationship is determined between routers.
- The router with the **higher Router ID** becomes the Master.
- Database exchange preparation begins.

### **5. Exchange**
- Routers exchange **Database Description (DBD) packets**.
- Each router compares received DBDs with its own **Link-State Database (LSDB)**.

### **6. Loading**
- Routers send **Link-State Request (LSR) packets** for missing or outdated LSAs.
- Link-State Updates (LSUs) are sent in response to LSRs.

### **7. Full**
- The routers have fully synchronized their databases.
- The adjacency is complete, and the routers can now forward traffic based on the learned OSPF topology.

## DR/BDR Election
On multi-access networks (e.g., Ethernet), OSPF elects a **Designated Router (DR)** and a **Backup Designated Router (BDR)** to reduce flooding:
- The router with the **highest priority** is elected as DR.
- The router with the **second highest priority** is elected as BDR.
- If priorities are equal, the router with the **highest Router ID** is elected.
- DR/BDR elections do not occur in point-to-point networks.

### Example: Configuring OSPF Priorities
```bash
interface GigabitEthernet0/0
 ip ospf priority 200  # Higher priority increases chance of becoming DR
```

---
