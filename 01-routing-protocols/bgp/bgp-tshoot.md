# **Troubleshooting BGP Neighbor Relationships**  

## **BGP Neighbor Stuck in IDLE**  
### 🔹 **Issue:** The router is not attempting to establish a BGP session.  
🔍 **Possible Causes & Fixes:**  
- **BGP not configured on the neighbor** → Ensure BGP is enabled on both ends.  
- **Neighbor statement missing or incorrect** → Verify with:  
  ```bash
  show run | section bgp
  ```
- **Authentication mismatch (MD5 password set but not matching)** → Check with:  
  ```bash
  show ip bgp neighbors | include password
  ```
- **ACL or firewall blocking BGP (TCP/179)** → Ensure no security policies are filtering BGP.  

---

## **BGP Neighbor Does Not Become ACTIVE**  
### 🔹 **Neighbor is Not Directly Connected**  
📌 **Issue:** The router assumes eBGP peers are directly connected.  
✅ **Solution:** Enable **`ebgp-multihop`** to allow peering over multiple hops.  

```bash
neighbor <IP> ebgp-multihop <hops>
```

---

## **BGP Neighbor Stuck in ACTIVE – Session Not Established**  
### 🔹 **Troubleshooting Steps:**  
✅ **Check for the SYN-ACK Packet** using:  
```bash
debug ip tcp transactions
```
🔍 **Possible Causes & Fixes:**  

1️⃣ **If no TCP SYN-ACK response:**  
- **Neighbor is unreachable** → Verify connectivity with **`ping <neighbor-IP>`**  
- **ACL blocking traffic** → Check firewall rules / ACLs  
- **BGP not fully configured on remote router** → Ensure BGP is enabled  

2️⃣ **If TCP SYN is answered with RST (Reset) packet:**  
- **Incorrect source IP address** → Check **`update-source`** configuration  
- **Remote router rejecting session** → Validate remote BGP configuration  

---

## **BGP Neighbor Flapping Between ACTIVE & IDLE**  
### 🔹 **Issue:** TCP session is established and immediately torn down.  
🔍 **Possible Causes & Fixes:**  
- **AS number mismatch** → Verify neighbor AS with:  
  ```bash
  show ip bgp summary
  ```
- **Flapping link or unstable connection** → Check interface logs:  
  ```bash
  show log | include Interface
  ```
- **BGP timers too aggressive** → Adjust keepalive & hold timers:  
  ```bash
  neighbor <IP> timers 60 180
  ```

---

## **Key Verification Commands**  
💡 Useful commands to check BGP neighbor status:  
```bash
show ip bgp summary                # Check neighbor states  
show ip bgp neighbors               # Detailed neighbor info  
show ip bgp neighbors | include state  # Filter for session state  
show ip route | include BGP         # Verify if routes are received  
show log | include BGP              # Check for errors related to BGP  
```

---
