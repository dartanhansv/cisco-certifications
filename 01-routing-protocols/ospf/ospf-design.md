# OSPF Design Considerations

## Hub-and-Spoke Design  
- **Keep Area 0 at the hub side**:  
  - Branch routers only calculate SPF within their own area.  
  - Reduces **LSA flooding** over WAN links.  

## Area Design for Remote Branches  
- **Define one OSPF area per branch**:  
  - Grouping all branches in a single area doesn't scale well.  
  - Separate areas for each branch limit **LSA flooding** and minimize **SPF recalculations**.  
<br>
<br>
## Additional Design Considerations  

### Summarization and Route Optimization  
- Use **ABRs** to summarize routes between areas:  
  - Reduces the size of routing tables and improves performance.  
  - Simplifies the topology by limiting the scope of LSAs.  

### OSPF over WAN Links  
- **Point-to-Point on Frame Relay**:  
  - Prevent DR/BDR elections by treating WAN links as point-to-point connections.  
  - Note: Frame Relay might still appear in exams but is less common in modern deployments.  
- **DMVPN**:  
  - Use DMVPN to avoid DR/BDR elections and simplify OSPF routing on dynamic WAN topologies.  

### LSA Control and Filtering  
- Use **ABR and ASBR filtering** to block unnecessary advertisements:  
  - Prevent flooding LSAs that aren't needed across the network.  
  - Control external route redistribution into OSPF areas for better traffic optimization.  

### Multi-Area OSPF  
- Minimize inter-area routing dependencies to keep most traffic within local areas.  
- Reduce reliance on **ABRs** for routing decisions.

### Stub Areas  
- Apply **stub areas** where appropriate to limit LSA types and shrink routing tables.  
- Particularly useful for remote branches with predictable routing needs.  

### Link Redundancy  
- Design redundant links to **Area 0** whenever possible to prevent routing failures.  

### Authentication  
- Enable OSPF authentication for secure routing:  
  - Consider MD5 or SHA encryption for safe OSPF communication.  

### Cost Optimization  
- Adjust **interface costs** to prioritize high-bandwidth links.  

---
