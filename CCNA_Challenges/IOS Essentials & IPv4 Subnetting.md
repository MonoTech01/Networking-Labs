
# Cisco IOS Essentials & IP Subnetting

## 1. Reset R1 to Factory Defaults

1. From privileged EXEC mode (e.g., `R1#`), erase the current startup configuration:

    ```
    en
    #write erase

    OR

    #erase startup-config
    ```

2. **Reload** the device to load default settings from ROM:

    ```
    #reload
    ```

**Result:**  
R1 should return to a factory-default state (basic prompt, no saved config).

---

## 2. Basic Device Configuration (All Devices)

1. **Set Hostname** (e.g., `R1`, `S2`, etc.):

    ```
    en
    #config t
    (config)# hostname R1
    ```

2. **Disable DNS Lookup** so the device does not attempt to resolve unknown commands:

    ```
    (config)# no ip domain-lookup
    ```

3. **Enable Logging Synchronous** to avoid console messages interrupting your typing:

    ```
    (config)# line con 0
    (config-line)# logging synchronous
    ```

4. **Set an Enable Secret Password** (“Mono”) to protect privileged EXEC mode (hashed):

    ```
    (config)# enable secret Mono
    ```

---

## 3. Interface Configuration & CDP Verification

1. **Enable Interfaces & Add Descriptions**:

   ```
    #config t
    (config)# interface range gigabitEthernet[numberoftheints]
    (config-if-range)# description Link to R2
    (config-if-range)# no shutdown
    ```

3. **Verify CDP Neighbors**:

    ```
    #show cdp neighbors
    ```

This ensures each device sees its directly connected Cisco neighbors.

---

## 4. Telnet Configuration (R1 & R3)

Allow inbound Telnet connections with a simple password (`cisco`), then require login:

      ```
      (config)# line vty 0 
      (config-line)# transport input telnet 
      (config-line)# password cisco
      (config-line)# login
 
> **Note:** Telnet is **unsecured** (clear text). Generally, use SSH if security is a concern. Complex passwords are required in the real enviroment!!!

---

## 5. SSH Configuration (R2 & R5)

Devices R2 and R5 should allow **secure** (encrypted) SSH connections:

    ```
    en
    #config t
    (config)# hostname R2          ! Or R5, depending on device
    (config)# ip domain-name mono.com
    (config)# crypto key generate rsa modulus 2048
    (config)# ip ssh version 2
    (config)# username admin privilege 15 secret mono
    
    (config)# line vty 0
    (config-line)# transport input ssh
    (config-line)# login local


1. **Hostname & Domain Name** are often required (especially on older IOS) to generate RSA keys.  
2. **RSA Key** creation allows SSH encryption.  
3. **Local User** with privilege 15 provides administrative access via SSH.  
4. **VTY Line** restricted to SSH and local login ensures secure remote access.

---

## 6. VLSM IP Addressing Scheme

### Requirements

- **Base Network**: `180.50.0.0/16`
- **Subnets (Segments A–F)** must accommodate:

  | Segment | Required Hosts |
  |---------|---------------|
  | A       | 99            |
  | B       | 13            |
  | C       | 6             |
  | D       | 11            |
  | E       | 26            |
  | F       | 30            |

- **VLSM**: Use the minimal number of host bits for each subnet to conserve address space.
- **Router Interfaces**: Typically use the **first usable** IP in each subnet.

### Example: Allocating Subnets (Largest-First)

**Why Largest-First?**  
- Helps avoid fragmentation and ensures large subnets have enough contiguous address space.

| Segment | Required Hosts | Chosen Prefix | Subnet              | Usable Range                   | Broadcast       |
|---------|---------------|---------------|---------------------|--------------------------------|-----------------|
| **A**   | 99            | `/25`         | 180.50.0.0/25       | 180.50.0.1 – 180.50.0.126      | 180.50.0.127    |
| **F**   | 30            | `/27`         | 180.50.0.128/27     | 180.50.0.129 – 180.50.0.158    | 180.50.0.159    |
| **E**   | 26            | `/27`         | 180.50.0.160/27     | 180.50.0.161 – 180.50.0.190    | 180.50.0.191    |
| **B**   | 13            | `/28`         | 180.50.0.192/28     | 180.50.0.193 – 180.50.0.206    | 180.50.0.207    |
| **D**   | 11            | `/28`         | 180.50.0.208/28     | 180.50.0.209 – 180.50.0.222    | 180.50.0.223    |
| **C**   | 6             | `/29`         | 180.50.0.224/29     | 180.50.0.225 – 180.50.0.230    | 180.50.0.231    |

---

## 7. Applying IP Addresses on Router Interfaces

- **Routers connecting segments A–D**: Assign first usable IP (e.g., `180.50.0.1`) with the correct mask:

    ```
    R1(config)# interface gig0/0
    R1(config-if)# ip address 180.50.0.1 255.255.255.128
    R1(config-if)# no shutdown
    ```

- **R3, R4, R5**: Use the IP addresses and masks per the diagram or VLSM plan above.  
- **R3 Gig0/2** (Segments E & F): Not addressed yet in this lab per instructions.

---

## 8. Verification Tests

1. **Telnet** from R2 to R1:

    ```
    R2# telnet 180.50.X.X
    ```

2. **Telnet** from R4 to R3:

    ```
    R4# telnet 180.50.Y.Y
    ```

3. **SSH** from R1 to R2:

    ```
    R1# ssh -l admin 180.50.Z.Z
    ```

4. **SSH** from R4 to R5:

    ```
    R4# ssh -l admin 180.50.W.W
    ```

Each test confirms both **IP connectivity** and **remote access** configurations (Telnet/SSH).

---

## 9. FAQ: Subnet Reordering

### 9.1 Why Allocate from Largest to Smallest?

- **Less Fragmentation**: Ensures the largest subnet has enough contiguous space.
- **Avoid Address Exhaustion**: Placing a large subnet later might not fit if you’ve already consumed blocks with smaller subnets.
- **Easier Future Growth**: Large subnets often need more headroom.

### 9.2 Is It Compulsory?

- **Not strictly.** You can allocate in any order if you have plenty of space.
- **Largest-first** is a best practice to prevent potential design pitfalls in more constrained networks.

---

## 10. Example: Alphabetical Order (A–F) Without Reordering

If you choose to allocate subnets strictly in alphabetical order (Segments A, B, C, D, E, F), a possible layout might be:

| Segment | Required Hosts | Subnet             | Mask                | Range                            | Broadcast        |
|---------|---------------|---------------------|---------------------|----------------------------------|------------------|
| **A**   | 99            | 180.50.0.0/25      | 255.255.255.128     | 180.50.0.1 – 180.50.0.126        | 180.50.0.127     |
| **B**   | 13            | 180.50.0.128/28    | 255.255.255.240     | 180.50.0.129 – 180.50.0.142      | 180.50.0.143     |
| **C**   | 6             | 180.50.0.144/29    | 255.255.255.248     | 180.50.0.145 – 180.50.0.150      | 180.50.0.151     |
| **D**   | 11            | 180.50.0.152/28    | 255.255.255.240     | 180.50.0.153 – 180.50.0.166      | 180.50.0.167     |
| **E**   | 26            | 180.50.0.168/27    | 255.255.255.224     | 180.50.0.169 – 180.50.0.198      | 180.50.0.199     |
| **F**   | 30            | 180.50.0.200/27    | 255.255.255.224     | 180.50.0.201 – 180.50.0.230      | 180.50.0.231     |

This works fine if you have enough space. The **largest-first** approach simply helps when address space might become tight.

---

## Conclusion

1. **Factory-Default & Basic Setup**: Ensures consistent starting points and good practices (e.g., no DNS lookup, logging synchronous).  
2. **Telnet & SSH Configuration**: Demonstrates both unsecure (Telnet) and secure (SSH) remote management setups.  
3. **VLSM**: Shows how to optimize subnetting by assigning the fewest host bits necessary.  
4. **Subnet Allocation Order**: Largest-first vs. alphabetical—both valid, with largest-first recommended to avoid fragmentation.  
5. **Verification**: Telnet/SSH tests confirm IP addressing and authentication configurations.

By following these steps, you establish a solid understanding of **Cisco IOS fundamentals** and **VLSM subnetting** techniques.
