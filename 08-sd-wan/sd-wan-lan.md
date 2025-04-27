# 🏢 LAN Design

Site LAN designs can vary significantly based on size and requirements.  
They can range from a simple Layer 2 access switch setup to a large hierarchical network with multiple distribution and access switches and a Layer 3 core network.

Cisco SD-WAN can manage separate LAN networks as **VPNs**, allowing distinct policies for different types of traffic (e.g., corporate, PCI, guest wireless).

---

## 🔗 Layer 2 Design Options

1. **Layer 2 with a single vEdge router**
2. **Layer 2 with VRRP for dual vEdge routers**
3. **Layer 2 with a single vEdge router and multiple VPNs**
4. **Layer 2 with VRRP for dual vEdge routers and multiple VPNs**

---

## 🌐 Layer 2 Access Switch Connected to a Single vEdge Router

- Common setup for small branch sites.
- For redundancy, **dual vEdge routers** are implemented with **VRRP** as the first-hop gateway protocol.
- **VRRP** dynamically assigns responsibility for a virtual master router to one of the VRRP routers on a LAN.
- If the master fails, the virtual router backup automatically takes over.

---

## 🔀 Layer 2 Design with Multiple VPNs

- Separate LAN networks (IP subnets) placed in separate VPNs.
- When using two vEdge routers, separate VRRP instances support each VPN.

---

## 🛣️ Layer 3 LAN Design for SD-WAN

- **Static routes**, **OSPF**, or **BGP** can be used to exchange routes between vEdge routers and Layer 3 switches.
- A **single static route** might suffice for a branch site.
- **Larger sites** might use OSPF.
- **Data centers** would likely use BGP.

---

## 🧩 Layer 3 LAN Design with Multiple VPNs

- **Routes between VPNs are not exchanged.**  
  (This preserves traffic segmentation between different business units or functions.)

---

## 📜 vEdge DHCP Server

- **DHCP Server Functionality**:  
  vEdge routers can assign IP addresses directly to hosts at a customer site via the service side interface.

- **DHCP Relay (IP Helper)**:  
  vEdge routers can forward DHCP requests from the service side network to a DHCP server located in a different subnet.

---

# 📚 Navigation
- → Next: [TD](TD)  
- ← Previous: [TD](TD)  
- ↑ Back to: [TD](TD)

