# RESTCONF

## Introduction
RESTCONF is a protocol based on HTTP defined in RFC 8040, providing a programmatic interface for managing network devices by exposing data models and operations using RESTful principles.

## Details of RESTCONF

- **Design**: Simpler and more accessible than NETCONF, leveraging REST's statelessness and resource identification.
- **Operations**: Uses HTTP methods for create, retrieve, update, and delete (CRUD) operations on a NETCONF datastore containing YANG data.
- **Data Encoding**: Supports both XML and JSON.
- **Tools**: Compatible with HTTP-based tools and programming libraries.

## RESTCONF Operations

| Operation   | HTTP Method                   | Description                                 |
| ----------- | ----------------------------- | ------------------------------------------- |
| **Create**  | POST, PUT                     | Creates new resources or data elements      |
| **Read**    | GET                           | Retrieves data and metadata from a resource |
| **Update**  | PUT (replace), PATCH (modify) | Updates existing data                       |
| **Delete**  | DELETE                        | Removes resources or data elements          |
| **OPTIONS** | OPTIONS                       | Retrieves supported HTTP methods            |
| **HEAD**    | HEAD                          | Retrieves header metadata without body      |

## Advantages

- **Simplicity**: Easier to learn and use compared to NETCONF.
- **HTTP-Based**: Leverages existing web infrastructure and tools.
- **Statelessness**: Promotes scalability and simpler client development.
- **Resource-Oriented**: Aligns with modern RESTful design practices.
- **Supports XML and JSON**: Flexible for different environments.

## Limitations

- **Less Flexibility**: Compared to NETCONF in certain complex operations.
- **No Locking**: Lacks NETCONF’s mechanism for configuration locking.
- **Security**: Requires careful implementation of authentication and access control.
- **Performance Overhead**: Stateless design can increase overhead in large-scale systems.

## Use Cases

- **Network Automation**: For device provisioning and config updates.
- **Cloud-Based Management**: RESTCONF is ideal in web-scale environments.
- **Third-Party Integration**: Easily integrates with external systems or platforms.
- **API Development**: Basis for RESTful APIs for networking tools.
- **Small/Medium Organizations**: Simpler alternative for less specialized teams.

---
### 📚 Navigation
- → Next: [NETCONF vs RESTCONF](./netconf-vs-restconf.md)
- ← Previous: [NETCONF](./netconf.md)
- ↑ Back to: [Automation and Programmability](./readme.md)


