# WAN Design for High Availability

Designing a high-availability WAN is all about making sure your network stays up and running, even when parts of it fail. That means adding redundancy, planning backup paths, and using smart routing to avoid downtime.


### 🧱 Single-Homed WAN

This is the simplest setup: each site connects to just one service provider.


#### ✅ Pros
- **Easy to manage**: Only one provider to deal with.
- **Lower cost**: Less hardware, fewer circuits.
- **Common QoS Model**: Simple policy application.

#### ❌ Cons
- **Single point of failure**: If the provider goes down, so does your site.
- **Limited Flexibility**: Switching providers can be disruptive.

### 🌐 Multi-Homed WAN

A multi-homed WAN connects each site to two (or more) providers. It’s more complex, but way more resilient.


#### ✅ Pros
- **Redundancy**: Failover if one link goes down.
- **More flexibility**: Ability to choose from different providers and technologies.
- **Higher Availability**: Better suited for mission-critical applications that require high uptime.


#### ❌ Cons
- **More complexity**: More complex routing and management due to the multiple connections.
- **Higher cost**: More expensive in terms of both initial setup and ongoing maintenance.


### ⚙️ Techniques for High Availability

Some technologies come with HA built-in. Others need a little help.

#### Built-In HA Examples
- **MPLS VPNs**
- **Dynamic Routing Protocols** (like OSPF and BGP)

#### Add-On HA Tools
- **Extra WAN circuits**: Backup links for when primary fails.
- **Power redundancy**: UPS and backup generators.
- **Route filtering and tuning**: Control failover behavior.


#### Single-Homed Versus Multi-Homed WANs

##### Single-Homed WANs
- **Advantages**: Only one vendor to manage, common QoS model.
- **Disadvantages**: Vulnerable to service provider outages, difficult to switch providers.

##### Multi-Homed WANs
- **Advantages**: Increased fault tolerance, more failover options, and broader choice of providers.
- **Disadvantages**: More complex to configure and maintain, higher costs.


### 🔌 Single-Homed MPLS WANs

A site connects to one MPLS VPN provider.

- **Routing**:
  - **CE to PE** typically runs **eBGP**.
  - Some designs use **iBGP** between CEs.
  - BGP routes may be redistributed into the IGP (OSPF or EIGRP) for internal reachability.


### 🌐 Multi-Homed MPLS WANs

Each site connects to two MPLS providers (or the same provider via different POPs).

- **Routing**:
  - **CE routers** redistribute local routes from **EIGRP** into **BGP**.
  - BGP routes are redistributed into **EIGRP** as external routes.
  - Use filters and tags to prevent routing loops.


### 🧵 MPLS VPN with Backup Dark Fiber

Sometimes, branches connected via MPLS also have a direct link between them, like a dark fiber connection. Ideally, **MPLS should be the primary path**, with the **direct link acting only as a backup**. 
To make sure this works as expected, OSPF metrics and path selection need some adjusting.

- If you're using OSPF for CE-PE routing, the **MPLS VPN backbone** usually handles traffic between branches.
- But **OSPF tends to prefer intra-area routes** over inter-area or external ones, which can accidentally make it favor the direct link instead.

To fix this, you’ll need **a sham link**:

- A **sham link** is an OSPF virtual interface set up between CEs through the MPLS provider's cloud.
- It tricks OSPF into treating the VPN route as an intra-area path, ensuring MPLS remains the preferred route instead of the direct link.

> 🧠 **Heads up**: In MPLS VPN setups, **OSPF typically relies on MP-BGP**, which redistributes routes as **inter-area or external**. If a direct connection is intra-area, OSPF will prioritize it. That’s where the sham link comes in—it keeps the VPN route classified as intra-area, making sure MPLS stays on top.


### 🔁 Hybrid WANs: Layer 3 VPN with Internet Tunnels

You can use MPLS as your main path and the internet as a fallback using VPN tunnels.

- **Design**: 
  - MPLS = primary path.
  - IPsec tunnel over internet = backup path.

- **Routing**: 
  - **eBGP** for peering with the MPLS VPN provider.
  - **EIGRP or OSPF** internally.
  - BGP routes are preferred over EIGRP routes.
  - Routing protocol metrics are adjusted for path preference.
  - **FHRP** (First Hop Redundancy Protocol) is used for failover.
  

### ☁️ WAN Integration for Hybrid Solutions

Sites need to connect to cloud providers like AWS, Azure, or GCP (Google Cloud Platform).

- **Service**: Direct connect between on-premises data center and a cloud provider’s data center.
- **Benefits**:
  - **Improved Application Performance**: Optimizes traffic routing.
  - **Cost Reduction**: Reduces the need for dedicated MPLS connections.
  - **Flexibility**: Leverages cloud resources for scalability.

---

### 📚 Navigation
- → Next: [WAN Backup Connectivity](./wan-backup-connectivity.md) 
- ← Previous: [Enterprise Managed VPNs](enterprise-managed-vpns.md) 
- ↩ Return to: [WAN - Index](../README.md)



