# gRPC and gNMI

## Introduction

**gRPC** (Google Remote Procedure Call) is a high-performance, open-source RPC framework developed by Google that uses HTTP/2 for transport and Protocol Buffers (protobuf) for data serialization.

**gNMI** (gRPC Network Management Interface) is a network management protocol built on top of gRPC, providing mechanisms to **install, change, delete**, and **retrieve configuration and operational state** data from network devices.

---

## gRPC Overview

- **Transport Layer**: Based on HTTP/2, enabling features like multiplexing, flow control, and TLS.
- **Bi-directional Streaming**: Supports streaming in both directions, ideal for telemetry and configuration updates.
- **Efficiency**: Uses Protocol Buffers (binary format), ensuring compact, fast, and efficient data exchange.
- **Interface Definition Language (IDL)**: APIs are defined using `.proto` files and compiled to generate client/server code.
- **Cross-Platform**: Works across multiple languages and platforms.
- **Integration**: Often used as the foundation for gNMI and other telemetry or management services.

### Common gRPC Operations (Cisco IOS XR)

| Operation             | Description                             |
| --------------------- | --------------------------------------- |
| **GetConfig**         | Retrieve device configuration           |
| **MergeConfig**       | Merge (add/update) configuration data   |
| **DeleteConfig**      | Remove configuration entries            |
| **ReplaceConfig**     | Overwrite configuration sections        |
| **GetOper**           | Retrieve operational state data         |
| **ShowCmdTextOutput** | Execute show commands and return output |

---

## gNMI Overview

- **Purpose**: gNMI is used to manage and monitor network devices in a model-driven manner.
- **Built on gRPC**: Inherits all performance and transport benefits of gRPC.
- **Data Modeling**: Uses YANG models to define the structure of configuration and state data.
- **Secure Communication**: Supports TLS encryption for secure communication between collector and network device.

### gNMI Capabilities

| Function         | Description                                         |
| ---------------- | --------------------------------------------------- |
| **Capabilities** | Query supported models and versions on the device   |
| **Get**          | Retrieve configuration or operational state         |
| **Set**          | Modify configuration (update, replace, delete)      |
| **Subscribe**    | Create a telemetry subscription (streaming updates) |

### gNMI State Handling Example

- **Failure Detection**: If the gNMI Broker (GNMIB) goes down, it signals an operational state change to *down* and sends a `service unavailable` response.
- **Recovery**: Upon recovery, it signals an *up* state and resumes normal RPC message handling.

---

## Summary

| Feature        | gRPC                                | gNMI                                          |
| -------------- | ----------------------------------- | --------------------------------------------- |
| **Use Case**   | Generic RPC communication framework | Model-driven device configuration & telemetry |
| **Transport**  | HTTP/2 (TLS supported)              | HTTP/2 via gRPC (inherits gRPC capabilities)  |
| **Encoding**   | Protocol Buffers                    | Protocol Buffers                              |
| **Operations** | Generic (Get, Merge, Delete, etc.)  | Capabilities, Get, Set, Subscribe             |
| **Modeling**   | Not model-driven                    | YANG-based                                    |
| **Streaming**  | Supported                           | Supported (via Subscribe)                     |

---
### 📚 Navigation
- → Next: [Model-Driven Telemetry](./model-driven-telemetry.md)
- ← Previous: [NETCONF vs RESTCONF](./netconf-vs-restconf.md)
- ↑ Back to: [Automation and Programmability](./readme.md)
