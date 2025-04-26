# 🛠️ Network Management Design

Effective network management ensures visibility, control, and security across all network elements. The ISO FCAPS model provides a framework to understand the key processes involved in network management.

---

## 🧩 Network Management Components

| Element                             | Description                                                       |
| ----------------------------------- | ----------------------------------------------------------------- |
| **Network Management System (NMS)** | Central system running management applications.                   |
| **Protocols and Standards**         | SNMP, MIB, RMON used to exchange management information.          |
| **Managed Devices**                 | Devices monitored and controlled by the NMS.                      |
| **Management Agents**               | Software inside managed devices (e.g., SNMP agents, RMON agents). |

---

## 🔎 Network Management Processes (FCAPS)

| Process                      | Purpose                                               |
| ---------------------------- | ----------------------------------------------------- |
| **Fault Management**         | Detects, isolates, and corrects faults.               |
| **Configuration Management** | Tracks, baselines, and manages device configurations. |
| **Accounting Management**    | Measures usage for billing or analysis.               |
| **Performance Management**   | Monitors efficiency and packet delivery.              |
| **Security Management**      | Manages authentication, authorization, and auditing.  |

---

## 🌐 In-Band vs. Out-of-Band Management

| Approach              | Characteristics                                                                                                                                      |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| **In-Band**           | - Uses production IP subnets.<br>- Typically accessed via loopback addresses.<br>- Shares infrastructure with user traffic.                          |
| **Out-of-Band (OOB)** | - Uses a dedicated, physically separate network.<br>- Access via management ports.<br>- Isolated credentials and infrastructure for higher security. |

---

## 🚦 Traffic Prioritization

- Network management traffic should be prioritized to ensure timely control and monitoring.
- **Classification Recommendations**:
  - **Layer 3 (IP)**: DSCP **CS1** (value 16).
  - **Layer 2 (Ethernet CoS)**: CoS **2**.

---

# 📚 Navigation
- ↑ Back to: [Network Services](../readme.md)
