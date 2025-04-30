# IS-IS NET Addressing  

The **Network Entity Title (NET)** is the OSI address used by IS-IS for communication between routers using OSI Protocol Data Units (PDUs). While IS-IS can be configured to route IP packets, its internal operations rely on OSI standards.  

A NET is a **hexadecimal string** ranging from **8 to 20 bytes in length** and consists of the following parts:  

| Component                                 | Description                                                                                             |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **AFI (Authority and Format Identifier)** | Identifies the authority governing the address format. Commonly, AFI `49` is used for private networks. |
| **Area ID**                               | Defines the IS-IS area. Routers with the same Area ID belong to the same IS-IS area.                    |
| **System ID**                             | Identifies the router uniquely within an IS-IS area. Typically 6 bytes long.                            |
| **SEL (Selector)**                        | Used to specify an entity or service within a device. Default value is `00` for routing purposes.       |

---

## Example of a NET Address  
Let’s break down the NET address `49.0002.1921.6800.4501.00` into its components:  

| Component     | Value            | Description                    |
| ------------- | ---------------- | ------------------------------ |
| **AFI**       | `49`             | Private addressing scheme      |
| **Area ID**   | `0002`           | Defines the IS-IS area         |
| **System ID** | `1921.6800.4501` | Uniquely identifies the router |
| **SEL**       | `00`             | Selector for routing (default) |

---

## Detailed Breakdown of NET Components  

### 1. **Authority and Format Identifier (AFI)**  
The AFI identifies the addressing authority and address format.  
- **Common Value**: `49` is used for private networks.  
- **Public Networks**: Other AFIs may be used in public or globally unique OSI networks.

### 2. **Area ID**  
The Area ID groups routers into the same IS-IS area. Routers within the same area exchange Level 1 information only.  
- Typical Length: Variable, commonly **2–13 bytes** depending on the network design.  
- **Examples**:  
  - `0001`: A small local area.  
  - `01.23`: A more complex hierarchical structure.  

### 3. **System ID**  
The System ID uniquely identifies each router within an IS-IS area.  
- **Length**: Exactly 6 bytes (12 hexadecimal characters).  
- **Recommendation**: Derive the System ID from an IPv4 loopback address to simplify management. For example:  
  - Loopback IP: `192.168.0.1` → System ID: `1921.6800.0001`.  
- **Uniqueness**: It must be unique within the IS-IS domain to avoid routing conflicts.  

### 4. **Selector (SEL)**  
The SEL is typically used to identify a specific service within the router.  
- Default Value: `00` (indicates the NET is used for routing).  

---

## Additional Examples  

| NET Address                   | Breakdown                                                          |
| ----------------------------- | ------------------------------------------------------------------ |
| **49.0001.1111.2222.3333.00** | AFI: `49`, Area ID: `0001`, System ID: `1111.2222.3333`, SEL: `00` |
| **49.0003.1987.6543.2101.00** | AFI: `49`, Area ID: `0003`, System ID: `1987.6543.2101`, SEL: `00` |
| **49.01.1234.5678.9ABC.00**   | AFI: `49`, Area ID: `01`, System ID: `1234.5678.9ABC`, SEL: `00`   |

---

## Key Points  

1. **System ID Design**:  
   - Align System IDs with loopback IPs for easier management.  
   - Example: `10.1.1.1` → System ID: `1001.0101.0001`.  

2. **NET Length**:  
   - Must be between **8 and 20 bytes**.  
   - Shorter NETs are easier to configure but may limit scalability.  

3. **Best Practices**:  
   - Keep Area IDs consistent within each IS-IS area.  
   - Use `00` for SEL to adhere to routing conventions.  

---


### 📚 Navigation
- → Next: [IS-IS IPv6 Deployment](isis-ipv6-deployment.md)  
- ← Previous: [IS-IS Overview](isis-overview.md)  
- ↑ Back to: [IS-IS](./readme.md)
