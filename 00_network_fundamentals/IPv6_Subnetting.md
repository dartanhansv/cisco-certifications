# IPv6 Addressing and Subnetting Summary

## How IPv6 Addressing Works
- IPv6 addresses are **128-bit** long and written in **hexadecimal**.
- They are divided into **eight groups** of four hex digits, separated by colons (`:`), e.g., `2001:0db8:85a3:0000:0000:8a2e:0370:7334`.
- Leading zeros in each group can be omitted (`2001:db8:85a3::8a2e:370:7334`).
- The address is typically split into:
  - **Network Prefix** (first 64 bits) – assigned by ISPs or administrators.
  - **Interface Identifier** (last 64 bits) – often derived from a MAC address.

## Quick IPv6 Subnetting Tips for Exams
1. **/64 is the Standard Subnet Size**
   - Most IPv6 networks use a **/64 prefix**, meaning the first **64 bits** define the network, and the rest are for hosts.

2. **Shortcut for Creating Subnets**
   - Instead of borrowing bits like in IPv4, IPv6 subnets are just different prefix lengths.
   - Example: A `/48` network can be split into **65,536** `/64` subnets.

3. **Quickly Determine Subnet Ranges**
   - Increment the **next hexadecimal digit** after the subnet boundary.
   - Example: If your network is `2001:db8:abcd::/48`, the next subnet would be `2001:db8:abce::/48`.

4. **Memorize Common Prefix Lengths**
   - `/48` → Common for ISPs assigning to organizations.
   - `/56` → Used for smaller site allocations.
   - `/64` → Standard subnet size for local networks.
   - `/128` → A single device (like loopback).

5. **Use Binary for Fine Adjustments**
   - If a subnet needs an unusual prefix (e.g., `/56` to `/60`), convert the last hex digit to binary for clarity.

---

## IPv6 Subnetting Exercises

#### TBD
