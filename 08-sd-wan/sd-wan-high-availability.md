# 🔄 High Availability and Redundancy

Cisco SD-WAN offers several solutions to ensure high availability and redundancy, categorized into:

- Site Redundancy
- Transport Redundancy
- Network/Headend Redundancy
- Controller Redundancy

---

## 🏠 Site Redundancy

Site redundancy ensures continued operation if a vEdge router fails at a site. This can be achieved through:

- **VRRP (Virtual Router Redundancy Protocol)**:  
  Provides failover at the switched infrastructure level.

- **Layer 3 Routing**:  
  Uses Layer 3 switches or routers for failover.

**How does it work?**  
Imagine you have two vEdge routers at a site.  
If the first vEdge router fails, VRRP will automatically redirect traffic to the second vEdge router.  
Similarly, if OSPF or BGP is running between the vEdge devices and the router, routing protocols will reroute traffic to the second vEdge router if the first one fails.

---

## 🌐 Transport Redundancy

Transport redundancy ensures that if your primary WAN transport fails, traffic is redirected to a secondary transport.

**How does it work?**  
Imagine you have two types of WAN transport: MPLS and Internet.  
If the MPLS circuit fails, transport redundancy automatically diverts traffic to the Internet transport.  
This ensures continuous connectivity and minimizes disruptions.

---

## 🏢 Network/Headend Redundancy

Network/headend redundancy ensures that if the primary network headend vEdge router at the data center loses connectivity, the vEdge router at a branch site can connect to a redundant headend vEdge router.

**Example Explanation**  
Imagine you have two headend vEdge routers at your data center.  
If the primary headend vEdge router loses connectivity, the branch site’s vEdge router will automatically switch to the secondary, redundant headend vEdge router.  
This setup ensures that the branch site maintains connectivity to the data center, minimizing downtime.

---

## 🧠 Controller Redundancy

As previously discussed, you can **increase the number of vSmart controllers** to enhance the scalability and redundancy of the control plane.

---

# 📚 Navigation
- → Next: [TD](TD)  
- ← Previous: [TD](TD)  
- ↑ Back to: [TD](TD)
