# IPv4 Addressing and Subnetting Analysis

### Given the following IPv4 address and subnet mask:
- **IPv4 Address**: 192.168.27.7
- **Subnet Mask**: 255.255.224.0

### Questions:
- **A.** How many total hosts per network?
- **B.** How many usable hosts per network?
- **C.** What is the network address or subnet ID that this IPv4 address belongs to?
- **D.** What is the broadcast address that this IPv4 address belongs to?
- **E.** What is the network address for the next subnet?
- **F.** How many networks can you have?

---

## Step-by-Step Solution

### Step 1: Binary Conversion Table
Write out your binary conversion table with the **Most Significant Bit (MSB)** to the left and **Least Significant Bit (LSB)** on the right. If you do it the other way, remember to flip your bits when checking with a calculator.

#### Binary Conversion Table:

| Most Significant Bit | Least Significant Bit |
|----------------------|------------------------|
| 7 6 5 4              | 3 2 1 0                |
| 2^ 2^ 2^ 2^          | 2^ 2^ 2^ 2^            |
| =====================|========================|
| 128 64 32 16         | 8 4 2 1                |
| =====================|========================|

---

### Step 2: Write out the IP Address and Subnet Mask in Binary

- **IPv4 Address**:
    - Decimal: 192.168.27.7
    - Binary: 1100 0000 . 1010 1000 . 0001 1011 . 0000 0111

- **Subnet Mask**:
    - Decimal: 255.255.224.0
    - Binary: 1111 1111 . 1111 1111 . 1110 0000 . 0000 0000

---

### Step 3: Count Network and Host Bits
Using the subnet mask in binary, count the bits available for networks and hosts.

- **Mask in Decimal**: 255.255.224.0
- **Mask in Binary**: 1111 1111 . 1111 1111 . 1110 0000 . 0000 0000

The number of network bits is 19, and the number of host bits is 13.

- **Network Bits**: 19
- **Host Bits**: 13

> **Note**: IPv4 masks are 32 bits long. Verify that the sum of network bits and host bits equals 32 to avoid mistakes.

---

### Step 4: CIDR Notation
From the host bits, we see that the CIDR notation is **/19** (i.e., 192.168.27.7 / 19).

---

### Step 5: Total Hosts per Network
Calculate the total number of hosts per network by evaluating \(2^{13}\):

- **Total Hosts per Network (A)**:  
  \(2^{13} = 8192\)

---

### Step 6: Usable Hosts per Network
Calculate the usable hosts per network by subtracting 2 from the total number of hosts:

- **Usable Hosts per Network (B)**:  
  \(8192 - 2 = 8190\)

---

### Step 7: Range for Address Blocks
To accommodate 8192 total hosts, calculate the range of address blocks: \( \frac{8192}{256} = 32 \).

---

### Step 8: Network Address Calculation
Perform a bitwise AND between the IPv4 address and the subnet mask:

- **IPv4 Address in Binary**: 1100 0000 . 1010 1000 . 0001 1011 . 0000 0111
- **Mask in Binary**: 1111 1111 . 1111 1111 . 1110 0000 . 0000 0000

**Bitwise AND** results in:

- **Network Address in Binary**: 1100 0000 . 1010 1000 . 0000 0000 . 0000 0000
- **Network Address in Decimal (C)**: 192.168.0.0

---

### Step 9: Define Address Blocks
Write out the first block of addresses and define them:

| **Network Address** | **First Usable Host** | **Last Usable Host** | **Broadcast Address** |
|---------------------|-----------------------|----------------------|-----------------------|
| 192.168.0.0         | 192.168.0.1           | 192.168.31.254       | 192.168.31.255 (D)    |

---

### Step 10: Next Block (or Subsequent Blocks)
The next network block:

| **Network Address** | **First Usable Host** | **Last Usable Host** | **Broadcast Address** |
|---------------------|-----------------------|----------------------|-----------------------|
| 192.168.32.0 (E)    | 192.168.32.1          | 192.168.63.254       | 192.168.63.255        |

---

### Step 11: Range of IPv4 Addresses
If no specific range is given, assume the entire private block for `192.168.x.x` (from `192.168.0.0` to `192.168.255.255`). This results in 8 subnets, each with 8192 total hosts.

- **Total Networks (F)**: 8 networks, each with 8192 hosts.

---

### All Network Blocks Using 255.255.224.0 Mask (/19)

| **#** | **Network Address** | **Usable Host Range**       | **Broadcast Address** |
|-------|---------------------|-----------------------------|-----------------------|
| 1     | 192.168.0.0         | 192.168.0.1 - 192.168.31.254| 192.168.31.255        |
| 2     | 192.168.32.0        | 192.168.32.1 - 192.168.63.254| 192.168.63.255        |
| 3     | 192.168.64.0        | 192.168.64.1 - 192.168.95.254| 192.168.95.255        |
| 4     | 192.168.96.0        | 192.168.96.1 - 192.168.127.254| 192.168.127.255       |
| 5     | 192.168.128.0       | 192.168.128.1 - 192.168.159.254| 192.168.159.255      |
| 6     | 192.168.160.0       | 192.168.160.1 - 192.168.191.254| 192.168.191.255      |
| 7     | 192.168.192.0       | 192.168.192.1 - 192.168.223.254| 192.168.223.255      |
| 8     | 192.168.224.0       | 192.168.224.1 - 192.168.255.254| 192.168.255.255      |

---
