# NETCONF

## Introduction
Network Configuration Protocol (NETCONF) is a network management protocol defined by the IETF in RFC 6241. It enables automated configuration and management of network devices, facilitating large-scale network deployments and dynamic network reconfiguration.

## NETCONF Details

### Protocol

- **Connection**: Operates over TCP.
- **Client/Server**: The NETCONF manager is the client; the NETCONF-enabled device is the server.
- **Encryption**: All communication is encrypted via SSH, using XML for message encoding.
- **Operations**: Structured as remote procedure calls (RPCs), formatted in XML.
- **Data Stores**: Supports multiple configuration data stores (running, candidate, startup).
- **Capabilities**: Advertised and exchanged when the session is established.
- **Transaction Support**: Ensures reliable, consistent operations.

### NETCONF Data Stores

- **Running, Startup, and Candidate**: Can hold complete configuration sets and be targets of operations.
- **Device Support**: Only the *running* datastore is required; support for others is optional.
- **Writeability**: Varies depending on device and datastore support.

### NETCONF Operations

| Operation         | Description                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `<get-config>`    | Retrieves specific or full configuration from a specified datastore      |
| `<edit-config>`   | Modifies a configuration (create, merge, replace, delete)                |
| `<get>`           | Retrieves device operational state and optionally configuration data     |
| `<get-schema>`    | Retrieves the YANG schema from the device                                |
| `<lock>`          | Locks a configuration datastore (e.g., candidate) to prevent other edits |
| `<unlock>`        | Unlocks the configuration datastore                                      |
| `<close-session>` | Gracefully ends the NETCONF session                                      |

### Advantages

- **Automation & Orchestration**: Ideal for managing large-scale or dynamic networks.
- **Standardization**: Uses YANG for consistent configuration across devices and vendors.
- **Security**: Communicates over secure channels like SSH or TLS.
- **Scalability**: Well-suited for enterprise and service provider environments.
- **Auditing & Compliance**: Supports configuration history and regulatory audits.
- **Service Provisioning**: Plays a critical role in orchestrating services.

### Limitations

- **Complexity**: Requires familiarity with XML and YANG.
- **Bandwidth Use**: XML verbosity may increase message size.
- **Vendor-Specific Extensions**: Can reduce interoperability in mixed environments.
- **Device Load**: Processing XML may demand higher CPU/memory resources.

### Use Cases

- **Data Center Automation**: Efficiently configures multiple switches, routers, and firewalls.
- **Software-Defined Networks (SDN)**: Automates configuration and provisioning in SDN environments.
- **Compliance Checking**: Automates audit processes and compliance verifications.
- **Firmware Upgrades**: Manages updates across devices at scale.
- **Service Orchestration**: Enables automatic setup of complex, multi-device services.

---

### 📚 Navigation
- ← [Back to Automation Overview](./readme.md)
- ← [Previous: RESTCONF](./restconf.md)
- → [Next: NETCONF vs RESTCONF](./netconf-vs-restconf.md)
