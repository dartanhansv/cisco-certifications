# NETCONF vs RESTCONF

## Introduction
NETCONF and RESTCONF are protocols designed to interact with YANG-based data models for network device configuration and management. While they serve similar purposes, they differ in transport protocols, encoding, operational behavior, and suitability for specific use cases.

## Comparison of NETCONF and RESTCONF

| Feature                | NETCONF                                                 | RESTCONF                                              |
| ---------------------- | ------------------------------------------------------- | ----------------------------------------------------- |
| **Protocol**           | SSH-based, RPC over XML                                 | HTTP-based, RESTful API                               |
| **Data Encoding**      | XML only                                                | XML and JSON                                          |
| **Architecture**       | Stateful, session-based                                 | Stateless                                             |
| **Operations**         | RPC operations (`<get>`, `<edit-config>`, etc.)         | Standard HTTP verbs (`GET`, `POST`, `PUT`, `DELETE`)  |
| **Datastores**         | Supports running, startup, and candidate stores         | Maps to NETCONF datastores, handled implicitly        |
| **Locking Support**    | Yes, supports configuration locking                     | No native locking mechanism                           |
| **Tool Compatibility** | Specialized tools like `ncclient`, `yangcli`            | Any HTTP client (e.g., `curl`, Postman, REST APIs)    |
| **Learning Curve**     | Higher: requires understanding XML and YANG deeply      | Lower: familiar HTTP/REST model, especially with JSON |
| **Best Suited For**    | Large, complex networks requiring transaction integrity | Lightweight environments and web app integrations     |

---

### 📚 Navigation
- ← [Back to Automation Overview](./readme.md)
- ← [Previous: NETCONF](./netconf.md)
- → [Next: TBD]
