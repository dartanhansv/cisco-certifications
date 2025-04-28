# IPv4 Overview

This document covers essential concepts about IPv4 addressing, including address types, private ranges, NAT translation, subnetting, and route summarization.  
It serves as a foundational review to strengthen IP addressing knowledge, critical for both design and troubleshooting tasks.  


### IPv4 Address Types
| Type      | Description                                                                                           | Example                                                                                                                            |
| --------- | ----------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Unicast   | The IP address of an interface on a single host. It can be a source address or a destination address. | A computer with IP address `192.168.1.10` sends data to another computer with IP address `192.168.1.20`.                           |
| Broadcast | An IP address that reaches all hosts in an address range. It is only a destination address.           | A computer sends a broadcast message to `192.168.1.255` to reach all devices in the `192.168.1.0/24` network.                      |
| Multicast | An IP address that reaches a group of hosts. It is only a destination address.                        | A server sends a multicast stream to the address `224.0.0.1`, which is received by all devices subscribed to that multicast group. |

### IPv4 Address Classes
| Address Class | Network Range                |
| ------------- | ---------------------------- |
| A             | 1.0.0.0 to 126.0.0.0*        |
| B             | 128.0.0.0 to 191.255.0.0     |
| C             | 192.0.0.0 to 223.255.255.0   |
| D             | 224.0.0.1 to 239.255.255.255 |
| E             | 240.0.0.0 to 254.255.255.255 |

> \* Networks 0.0.0.0 and 127.0.0.0 are reserved as special-use addresses.

### IPv4 Private Address Space
| Class Type | Start Address | End Address     |
| ---------- | ------------- | --------------- |
| Class A    | 10.0.0.0      | 10.255.255.255  |
| Class B    | 172.16.0.0    | 172.31.255.255  |
| Class C    | 192.168.0.0   | 192.168.255.255 |

### NAT (Network Address Translation)
| NAT Address Type       | Description                                                                                                                                           | Example                                                                                                                                                   |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Static NAT             | Commonly used to assign a unique public address to a network device with an internal private IP address so that it can be accessed from the Internet. | A web server with internal IP `192.168.1.100` is mapped to a public IP `203.0.113.100`.                                                                   |
| Dynamic NAT            | Dynamically maps an unregistered or private IP address to a registered IP address from a pool (group) of registered addresses.                        | Internal IP `192.168.1.101` is dynamically mapped to a public IP `203.0.113.101` from a pool of public IPs.                                               |
| PAT                    | Maps multiple unregistered or private IP addresses to a single registered IP address by using different ports.                                        | Multiple devices with internal IPs `192.168.1.102`, `192.168.1.103`, etc., are mapped to a single public IP `203.0.113.102` using different port numbers. |
| Inside local address   | The real IP address of a device that resides in the internal network. This address is used in the stub domain.                                        | -                                                                                                                                                         |
| Inside global address  | The translated IP address of the device that resides in the internal network. This address is used in the public network.                             | -                                                                                                                                                         |
| Outside global address | The real IP address of a device that resides on the Internet, outside the stub domain.                                                                | -                                                                                                                                                         |
| Outside local address  | The translated IP address of a device that resides on the Internet. This address is used inside the stub domain.                                      | -                                                                                                                                                         |

### IPv4 Address Subnets
| Class | Binary Mask                         | Dotted-Decimal Mask |
| ----- | ----------------------------------- | ------------------- |
| A     | 11111111 00000000 00000000 00000000 | 255.0.0.0           |
| B     | 11111111 11111111 00000000 00000000 | 255.255.0.0         |
| C     | 11111111 11111111 11111111 00000000 | 255.255.255.0       |

### Common Subnet Masks
| Default Class Mask | Subnet Mask     | Dotted-Decimal Mask |
| ------------------ | --------------- | ------------------- |
| /8                 | 255.0.0.0       | 255.0.0.0           |
| /16                | 255.255.0.0     | 255.255.0.0         |
| /24                | 255.255.255.0   | 255.255.255.0       |
| /10                | 255.192.0.0     | 255.192.0.0         |
| /19                | 255.255.224.0   | 255.255.224.0       |
| /20                | 255.255.240.0   | 255.255.240.0       |
| /25                | 255.255.255.128 | 255.255.255.128     |

<details>
<summary><strong>📚 Subnetting Tutorial (Click to expand)</strong></summary>

#### How to Calculate Subnets
1. **Determine the number of subnets needed**:  
   For example, if you need 4 subnets, you need 2 bits (since \(2^2 = 4\)).

2. **Calculate the new subnet mask**:  
   If the original mask is `/24`, adding 2 bits for subnetting gives `/26`.

3. **Determine the subnet addresses**: 
   - Original network: `192.168.1.0/24`
   - Subnet 1: `192.168.1.0/26`
   - Subnet 2: `192.168.1.64/26`
   - Subnet 3: `192.168.1.128/26`
   - Subnet 4: `192.168.1.192/26`

#### Examples of Subnetting
- **Example 1**: Subnetting `192.168.1.0/24` into 4 subnets:
  - Subnet 1: `192.168.1.0/26`
  - Subnet 2: `192.168.1.64/26`
  - Subnet 3: `192.168.1.128/26`
  - Subnet 4: `192.168.1.192/26`

- **Example 2**: Subnetting `10.0.0.0/8` into 16 subnets:
  - Subnet 1: `10.0.0.0/12`
  - Subnet 2: `10.16.0.0/12`
  - Subnet 3: `10.32.0.0/12`
  - Subnet 4: `10.48.0.0/12`
  - Subnet 5: `10.64.0.0/12`
  - Subnet 6: `10.80.0.0/12`
  - Subnet 7: `10.96.0.0/12`
  - Subnet 8: `10.112.0.0/12`
  - Subnet 9: `10.128.0.0/12`
  - Subnet 10: `10.144.0.0/12`
  - Subnet 11: `10.160.0.0/12`
  - Subnet 12: `10.176.0.0/12`
  - Subnet 13: `10.192.0.0/12`
  - Subnet 14: `10.208.0.0/12`
  - Subnet 15: `10.224.0.0/12`
  - Subnet 16: `10.240.0.0/12`

</details>

---

## Summarization Guidelines
#### Recognize a Block of IPv4 Addresses That Can Be Summarized
- The number of addresses to summarize must be a power of 2.
- The first address in the sequence must be a power of 2.

**Example:**
```
10.0.160.0/24
10.0.163.0/24
10.0.191.0/24
```
- Third octet: 191 - 160 = 31
- Round it to the next power of 2: 32 (2⁵ = 32, 5 bits)
- Summary address is `/24` minus 5 bits = `/19`
- **Summary address: `10.0.160.0/19`**

---

## 🎯 Extra Tip
A great online IP calculator that I use and recommend:  
👉 [Gestiopi Subnet Calculator](http://www.gestioip.net/cgi-bin/subnet_calculator.cgi)

---

### 📚 Navigation
- → Next: [Next Topic Placeholder](next-topic.md)  
- ← Previous: [Previous Topic Placeholder](previous-topic.md)  
- ↑ Back to: [IPv4 Overview](../readme.md)
