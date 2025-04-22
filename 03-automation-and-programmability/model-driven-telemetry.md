# Model-Driven Telemetry

## Introduction
Model-driven telemetry (MDT) is a modern approach to network monitoring that leverages standards-based data models (YANG) and streaming protocols to enable real-time access to operational statistics and deeper insights into network behavior.

## Concepts of Model-Driven Telemetry

- **Telemetry**: Automated collection and transmission of data from remote network elements to a monitoring system.
- **Push Model**: Unlike traditional SNMP polling, MDT pushes data from devices to receivers without needing to be queried.
- **YANG Models**: Define the structure and semantics of the data being streamed, supporting consistency and interoperability.
- **Subscription-Based**: Receivers subscribe to specific data elements, enabling targeted and efficient data streaming.

### Publication Types

| Type          | Description                                                                | Common Use Case                                              |
| ------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------ |
| **Periodic**  | Data is streamed at regular, configured intervals (e.g., every 5 seconds). | Monitoring counters or metrics that change frequently.       |
| **On-Change** | Data is streamed only when a change occurs.                                | Events like interface status changes or threshold crossings. |

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
- ← [Back to Automation Overview](./readme.md)
- ← [Previous: NETCONF vs RESTCONF](./netconf-vs-restconf.md)
- → [Next: TBD]
