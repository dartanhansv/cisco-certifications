# IPv6 Subnetting

## Understanding IPv6 Addressing
IPv6 addresses are 128-bit long and written in hexadecimal format, divided into **8 hextets** (groups of 4 hex digits):
```
XXXX : XXXX : XXXX : XXXX : XXXX : XXXX : XXXX : XXXX
```
Each **hex digit = 4 bits**, so each **hextet = 16 bits**.

### **Subnet Boundaries**
| Prefix | Bits Used | Hextet Representation      |
| ------ | --------- | -------------------------- |
| `/48`  | 48 bits   | `XXXX:XXXX:XXXX::/48`      |
| `/52`  | 52 bits   | `XXXX:XXXX:XXXX:X000::/52` |
| `/56`  | 56 bits   | `XXXX:XXXX:XXXX:XX00::/56` |
| `/60`  | 60 bits   | `XXXX:XXXX:XXXX:XXX0::/60` |
| `/64`  | 64 bits   | `XXXX:XXXX:XXXX:XXXX::/64` |

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
| Subnet #  | Address                   |
| --------- | ------------------------- |
| 1st `/60` | `2001:db8:5678:0000::/60` |
| 2nd `/60` | `2001:db8:5678:0010::/60` |
| 3rd `/60` | `2001:db8:5678:0020::/60` |
| 4th `/60` | `2001:db8:5678:0030::/60` |

### **Subnetting `/56 → /64`**
A `/64` means we add **8 more bits** (2 hex digits), so we now modify **the last two hex digits**.

| Subnet #  | Address                   |
| --------- | ------------------------- |
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

## **Exam-like exercise: Subnetting a University’s Departments**
### **Scenario:**
A university is expanding and creating two new departments. The network administrator has allocated the IPv6 range `2a01:c30:16:5009::4000/118` for both departments. Each department requires at least 200 hosts.

### **Step 1: Identify the given prefix and subnet mask**
**Given network:** `2a01:c30:16:5009::4000/118`

`/118` means **118 fixed bits**, leaving `(128 - 118) = 10 bits` for host allocation.

`2^10 = 1024` total addresses (including network and reserved ones).

### **Step 2: Determine the subnet size required**
Each department needs **200 hosts**.

- A `/121` subnet has **7 host bits** `(128 - 121 = 7 bits)`, meaning `2^7 = 128 addresses` → **Too small!**
- A `/120` subnet has **8 host bits** `(128 - 120 = 8 bits)`, meaning `2^8 = 256 addresses` → **Enough!**

Thus, the correct subnet size is **/120**.

### **Step 3: Find valid `/120` subnets inside `2a01:c30:16:5009::4000/118`**
`/118` means: `2a01:c30:16:5009::4000 - 2a01:c30:16:5009::43FF`

Breaking it into `/120`:

| Subnet #   | Address                      |
| ---------- | ---------------------------- |
| 1st `/120` | `2a01:c30:16:5009::4000/120` |
| 2nd `/120` | `2a01:c30:16:5009::4100/120` |
| 3rd `/120` | `2a01:c30:16:5009::4200/120` |
| 4th `/120` | `2a01:c30:16:5009::4300/120` |

### **Step 4: Assign subnets**
✅ **Department A:** `2a01:c30:16:5009::4100/120`  
✅ **Department B:** `2a01:c30:16:5009::4200/120`

---

## **Practice Exercises**

### **Example (With Solution)**
**Given:** Subnet `2001:db8:abcd::/48`, divide it into two `/52` subnets.

✅ **Solution:**
1. `/48` means: `2001:db8:abcd::/48`
2. `/52` means we add **4 more bits (1 hex digit)** → `2001:db8:abcd:X000::/52`

| Subnet #  | Address                   |
| --------- | ------------------------- |
| 1st `/52` | `2001:db8:abcd:0000::/52` |
| 2nd `/52` | `2001:db8:abcd:1000::/52` |

### **Now You Try!**
#### **Exercise 1:**
**Given:** Subnet `2001:db8:5678::/56`, divide it into two `/60` subnets.

| Subnet #  | Address |
| --------- | ------- |
| 1st `/60` | ???     |
| 2nd `/60` | ???     |

#### **Exercise 2:**
**Given:** Subnet `2001:db8:aaaa::/48`, divide it into two `/52` subnets.

| Subnet #  | Address |
| --------- | ------- |
| 1st `/52` | ???     |
| 2nd `/52` | ???     |

#### **Exercise 3:**
A hospital is setting up two new departments and allocated `2a01:c30:16:3009::5000/118`. Each department needs 200 hosts. Which two `/120` subnets should they use?

| Subnet #   | Address |
| ---------- | ------- |
| 1st `/120` | ???     |
| 2nd `/120` | ???     |

🚀 **Answer these before moving on!**
