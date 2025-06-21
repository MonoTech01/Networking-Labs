
# Cisco Lab 1

## 1. Factory Resetting R1

First, access the device's console. To erase the existing, non-default configuration on router R1 and restore it to its factory settings, execute the following commands from privileged EXEC mode:

    en  
    erase startup-config
    
    reload
    
OR: write erase

Upon reloading, the device will be in its factory default state.

## 2. Device Configuration (All Devices)
- Assign a Hostname
- Disable DNS Lookup for Mistyped Commands
- Ensure Uninterrupted Command Entry
- Secure Privileged EXEC Mode
- Activate Interfaces

R1

    en
    config t
    host R1
    no ip domain-lookup
    line con 0
    logging synchronous
    ena secret ultracat
    int range g0/0-2
    no shut

R2

    en
    config t
    host R2
    no ip domain-lookup
    line con 0
    logging synchronous
    ena secret ultracat
    int range g0/0-3
    no shut

R3
    
    en
    config t
    host R3
    no ip domain-lookup
    line con 0
    logging synchronous
    ena secret ultracat
    int range g0/0-2
    no shut

R4

    en
    config t
    host R4
    no ip domain-lookup
    line con 0
    logging synchronous
    ena secret ultracat
    int range g0/0-1
    no shut

R5

    en
    config t
    host R5
    no ip domain-lookup
    line con 0
    logging synchronous
    ena secret ultracat
    int range g0/0-2
    no shut

S1

    en
    config t
    host S1
    no ip domain-lookup
    line con 0
    logging synchronous
    ena secret ultracat
    int range g0/0,g0/2-3
    no shut

S2

    en
    config t
    host S2
    no ip domain-lookup
    line con 0
    logging synchronous
    ena secret ultracat
    int range g0/0-3
    no shut

S3

    en
    config t
    host S3
    no ip domain-lookup
    line con 0
    logging synchronous
    ena secret ultracat
    int range g0/0-3,g1/0,g3/0
    no shut

S4

    en
    config t
    host S4
    no ip domain-lookup
    line con 0
    logging synchronous
    ena secret ultracat
    int range g0/0-2,g1/0,g3/0
    no shut

-  Verifying Connectivity with CDP
Once the initial configurations are complete on all relevant devices, use the Cisco Discovery Protocol (CDP) to confirm direct network adjacencies. Execute the following command on Switch-2, R5, and R4 from privileged EXEC mode:

    show cdp nei


## 3. Configuring Telnet on R1 and R3 (to allow inbound Telnet connections on routers R1 and R3, authenticated by the password "cisco")

R1 and R3

    en
    config t
    line vty 0 924
    transport input telnet
    password cisco
    login
 
> **Note:** Telnet is **unsecured** (clear text). Generally, use SSH if security is a concern. Complex passwords are required in the real enviroment!!!

## 4. Configuring SSH (Version 2) on R2 and R5

R2 and R5

    en
    config t
    ip domain-name ultracat.com
    crypto key generate rsa modulus 2048
    ip ssh version 2
    username admin privilege 15 secret ultracat
    line vty 0 924
    transport input ssh
    login local

Brief explation:
- **Hostname & Domain Name** are often required (especially on older IOS) to generate RSA keys.
- **RSA Key** creation allows SSH encryption.
- **Local User** with privilege 15 provides administrative access via SSH.
- **VTY Line** restricted to SSH and local login ensures secure remote access.

## 5. VLSM IP Addressing Scheme and Applying IP Addresses on Router Interfaces

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
- **Router Interfaces**: Typically use the **first usable** IP in each subnet (from A to D).

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


R1
    
    config t
    int g0/2
    ip add 180.50.0.1 255.255.255.128

    int g0/0
    ip add 180.50.0.194 255.255.255.240
    
    intg0/1
    ip add 180.50.0.210 255.255.255.240

R2

    config t
    int g0/3
    ip add 180.50.0.2 255.255.255.128
    
    int g0/0
    ip add 180.50.0.193 255.255.255.240
    
    int g0/1
    ip add 180.50.0.225 255.255.255.248

    int g0/2
    ip add 180.50.0.209 255.255.255.240

- **R3, R4, R5**: Use the IP addresses and masks in the diagram.
- **R3 Gig0/2** (Segments E & F): Not addressed yet in this lab per instructions.

## 8. Verification Tests

1. **Telnet** from R2 to R1:

    ```
    R2# telnet 180.50.0.194
    ```

2. **Telnet** from R4 to R3:

    ```
    R4# telnet 20.1.34.3
    ```

3. **SSH** from R1 to R2:

    ```
    R1# ssh -l admin 180.50.0.193
    ```

4. **SSH** from R4 to R5:

    ```
    R4# ssh -l admin 20.1.45.5
    ```

Each test confirms both **IP connectivity** and **remote access** configurations (Telnet/SSH). All worked!
