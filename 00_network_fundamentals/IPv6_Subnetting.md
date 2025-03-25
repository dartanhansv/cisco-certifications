# IPv6 Subnetting

## Understanding IPv6 Addressing
IPv6 addresses are 128-bit long and written in hexadecimal format, divided into **8 hextets** (groups of 4 hex digits):
```
XXXX : XXXX : XXXX : XXXX : XXXX : XXXX : XXXX : XXXX
```
Each **hex digit = 4 bits**, so each **hextet = 16 bits**.

### **Subnet Boundaries**
| Prefix  | Bits Used | Hextet Representation |
|---------|----------|----------------------|
| `/48`   | 48 bits  | `XXXX:XXXX:XXXX::/48` |
| `/52`   | 52 bits  | `XXXX:XXXX:XXXX:X000::/52` |
| `/56`   | 56 bits  | `XXXX:XXXX:XXXX:XX00::/56` |
| `/60`   | 60 bits  | `XXXX:XXXX:XXXX:XXX0::/60` |
| `/64`   | 64 bits  | `XXXX:XXXX:XXXX:XXXX::/64` |

Notice how each step **adds exactly 4 bits** (1 hex digit)? That's why we modify **one more hex digit each time**.

## Subnetting IPv6 - Example Breakdown

### **Subnetting `/56 → /60`**

#### **Given:** `2001:db8:5678::/56`
We know `/56` means:
✅ **`2001:db8:5678:XX00::/56`** (14 hex digits are fixed)

A `/60` means we need **4 more bits** (1 hex digit), so we go to:
✅ **`2001:db8:5678:XXX0::/60`**

Thus, the **correct way to increment is the 3rd hex digit of the 4th hextet**.

### **4 Subnets of `/60`**
| Subnet # | Address |
|----------|----------------------------|
| 1st `/60` | `2001:db8:5678:0000::/60` |
| 2nd `/60` | `2001:db8:5678:0010::/60` |
| 3rd `/60` | `2001:db8:5678:0020::/60` |
| 4th `/60` | `2001:db8:5678:0030::/60` |

### **Subnetting `/56 → /64`**
A `/64` means we add **8 more bits** (2 hex digits), so we now modify **the last two hex digits**.

| Subnet # | Address |
|----------|----------------------------|
| 1st `/64` | `2001:db8:5678:0000::/64` |
| 2nd `/64` | `2001:db8:5678:0001::/64` |
| 3rd `/64` | `2001:db8:5678:0002::/64` |
| 4th `/64` | `2001:db8:5678:0003::/64` |

## **Shortcut for Quick Calculations**
1. Identify how many extra bits are needed to reach the new prefix.
2. Each **hex digit = 4 bits**, so divide the extra bits by 4 to find how many hex digits to modify.
3. Increment the correct hex digit (left to right, within the hextet).
4. Stick to **nibble boundaries (multiples of 4 bits)** for easy calculations.

With this approach, you can quickly determine the next subnet in an exam or real-world scenario!

---

## **Practice Exercises**

### **Example (With Solution)**
**Given:** Subnet `2001:db8:abcd::/48`, divide it into two `/52` subnets.

✅ **Solution:**
1. `/48` means: `2001:db8:abcd::/48`
2. `/52` means we add **4 more bits (1 hex digit)** → `2001:db8:abcd:X000::/52`

| Subnet # | Address |
|----------|----------------------------|
| 1st `/52` | `2001:db8:abcd:0000::/52` |
| 2nd `/52` | `2001:db8:abcd:1000::/52` |

### **Now You Try!**
#### **Exercise 1:**
**Given:** Subnet `2001:db8:5678::/56`, divide it into two `/60` subnets.

| Subnet # | Address |
|----------|----------------------------|
| 1st `/60` | ??? |
| 2nd `/60` | ??? |

#### **Exercise 2:**
**Given:** Subnet `2001:db8:aaaa::/48`, divide it into two `/52` subnets.

| Subnet # | Address |
|----------|----------------------------|
| 1st `/52` | ??? |
| 2nd `/52` | ??? |

🚀 **Answer these before moving on!**
