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
Configure an ACL to permit FTP and ICMP from PC1 LAN

![ACLs_5.4.12](/Images/PT_5.4.12_3.png)
![ACLs_5.4.12](/Images/PT_5.4.12_3a.png)
![ACLs_5.4.12](/Images/PT_5.4.12_4.png)
![ACLs_5.4.12](/Images/PT_5.4.12_5.png)
![ACLs_5.4.12](/Images/PT_5.4.12_6.png)


### Create: 

R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 eq ftp

R1(config)# access-list 100 permit icmp 172.22.34.64 0.0.0.31 host 172.22.34.62

### Apply: 

Enter interface configuration mode for G0/0: R1(config)# interface gigabitEthernet 0/0
Apply ACL 100 to inbound traffic: R1(config-if)# ip access-group 100 in

### Verify:

From PC1, ping the server (should succeed).
From PC1, open an FTP connection to the server (should succeed).
From PC1, ping PC2 (should fail).

## Part 2: Extended Named ACL
### Create
a named ACL called 'HTTP_ONLY'

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

