# Topology and Addressing Table
![ACLs_5.4.12](/Images/PT_5.4.12_1.png)
![ACLs_5.4.12](/Images/PT_5.4.12_2.png)

# Task
Two employees need access to services provided by the server. PC1 only needs FTP access while PC2 only needs web access. Both computers need to be able to ping the server, but not each other.
This means: 
- PC1 needs FTP access to the server.
- PC2 needs web (HTTP) access to the server.
- Both PCs should be able to ping the server.
- PCs should not be able to ping each other.

# Important Notes
Apply ACLs cautiously in production environments to avoid unintended network disruptions.

# Performance
## PC1 needs FTP access to the server.
Configure an ACL to permit FTP and ICMP from PC1 LAN. When configured and applied, this ACL should permit FTP and ICMP. ICMP is listed, but FTP is not. This is because FTP is an application layer protocol that uses TCP at the transport layer.

Rules:
R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 eq ftp

R1(config)# access-list 100 permit icmp 172.22.34.64 0.0.0.31 host 172.22.34.62

![ACLs_5.4.12](/Images/PT_5.4.12_3.png)
![ACLs_5.4.12](/Images/PT_5.4.12_3a.png)

Don't press Enter for all TCP traffic. To limit to FTP only, type 'eq ?' and select 'ftp'.

![ACLs_5.4.12](/Images/PT_5.4.12_4.png)

Extend the current access list with a statement allowing ICMP traffic from PC1 to Server. No need to filter specific ICMP types. Finally, apply the rules on R1's int g0/0. 

Enter interface configuration mode for G0/0 and apply ACL 100 to inbound traffic: R1(config-if)# ip access-group 100 in

![ACLs_5.4.12](/Images/PT_5.4.12_5.png)

### Verify
default username/ password is cisco.

Successfully accessed the server's ftp service = ping from PC1 to the server must be successful.

Ping PC2 from PC1. The ping failed because the ACL doesn't explicitly permit this traffic.

![ACLs_5.4.12](/Images/PT_5.4.12_6.png)


## Part 2: Extended Named ACL
### Configure an ACL to permit HTTP access and ICMP from PC2 LAN.
### Create
Named ACLs start with the "ip" keyword.
A named ACL called 'HTTP_ONLY'

R1(config)# ip access-list extended HTTP_ONLY

Add rules to the ACL:
R1(config-ext-nacl)# permit tcp 172.22.34.96 0.0.0.15 host 172.22.34.62 eq www
R1(config-ext-nacl)# permit icmp 172.22.34.96 0.0.0.15 host 172.22.34.62 

### Apply ACL:

Enter interface configuration mode for G0/1: R1(config)# interface gigabitEthernet 0/1
Apply 'HTTP_ONLY' ACL to inbound traffic: R1(config-if)# ip access-group HTTP_ONLY in

### Verify:

From PC2, ping the server (should succeed).
From PC2, open the server's IP address in a web browser (should succeed).
From PC2, open an FTP connection to the server (should fail).

