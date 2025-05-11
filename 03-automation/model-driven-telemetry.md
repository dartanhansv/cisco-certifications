# Model-Driven Telemetry

## Introduction
Model-driven telemetry (MDT) is a modern approach to network monitoring that leverages standards-based data models (YANG) and streaming protocols to enable real-time access to operational statistics and deeper insights into network behavior.

## Concepts of Model-Driven Telemetry

- **Telemetry**: Automated collection and transmission of data from remote network elements to a monitoring system.
- **Push Model**: Unlike traditional SNMP polling, MDT pushes data from devices to receivers without needing to be queried.
- **YANG Models**: Define the structure and semantics of the data being streamed, supporting consistency and interoperability.
- **Subscription-Based**: Receivers subscribe to specific data elements, enabling targeted and efficient data streaming.

### 📡 Publication Types

| Type          | Description                                                                | Common Use Case                                              | Performance Impact                  |
| ------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------ | ----------------------------------- |
| **Periodic**  | Data is streamed at regular, configured intervals (e.g., every 5 seconds). | Monitoring counters or metrics that change frequently.       | Higher — sends data continuously    |
| **On-Change** | Data is streamed only when a change occurs.                                | Events like interface status changes or threshold crossings. | Lower — sends data only when needed |



## Telemetry Modes: Dial-In vs Dial-Out

Model-driven telemetry supports two main modes of operation based on how subscriptions and sessions are established:

| Characteristic                     | **Dial-In**                                                   | **Dial-Out**                                                 |
| --------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| **Who initiates the session**     | Collector → Device                                             | Device → Collector                                            |
| **Session type**                  | Dynamic                                                        | Static or Configured                                          |
| **Persistence**                   | Tied to the session; lost on reload                            | Persistent; survives reloads                                  |
| **Subscription location**         | In memory only                                                 | Stored in running configuration                               |
| **Subscription ID**               | Dynamically generated                                          | Manually configured                                           |
| **Transport support**             | gRPC only                                                      | TCP, UDP, or gRPC                                             |
| **Connection direction**          | Requires device to accept inbound connection                   | Device initiates outbound connection                          |
| **After device reload**           | Subscription must be reinitiated                               | Automatically resumes                                         |
| **Load balancing**                | Not applicable                                                 | Supports anycast and load-balanced collectors                 |
| **Security implications**         | Inbound ports must be open                                     | No need for inbound access; more firewall-friendly            |
| **Data & config channel**         | Same session used for both config and telemetry                | Separate sessions possible                                    |

> Source: [xrdocs.io – Model-Driven Telemetry: Dial-In or Dial-Out?](https://xrdocs.io/telemetry/blogs/2017-01-20-model-driven-telemetry-dial-in-or-dial-out/)

## Impact of Model-Driven Telemetry on Networks

MDT brings significant improvements to network operations by enabling real-time, scalable, and efficient monitoring and automation.

### Benefits

- **Real-Time Monitoring**: Delivers near-instant visibility into network conditions.
- **Granular Visibility**: Captures detailed operational metrics for devices and services.
- **Faster Troubleshooting**: Reduces mean time to detect and resolve issues.
- **Lower Bandwidth Overhead**: Push-based design reduces repeated queries.
- **Scalability**: Designed for large-scale, distributed environments.

### How It Works

1. **Data Collection**: Devices gather data as defined by YANG models.
2. **Streaming**: Data is pushed to receivers using transport protocols (e.g., gRPC, HTTP/HTTPS).
3. **Subscription**: Monitoring systems subscribe to specific telemetry paths.
4. **Processing & Analysis**: The telemetry stream is analyzed for insights, alerting, automation, or visualization.

---

### 📚 Navigation
- → Next: [gRPC and gNMI](./grpc-gnmi.md)  
- ← Previous: [NETCONF vs RESTCONF](./netconf-vs-restconf.md)  
- ↩ Return to: [Automation and Programmability](./README.md)
