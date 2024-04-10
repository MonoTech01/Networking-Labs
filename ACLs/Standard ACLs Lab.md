# Topology
![ACLs](/Images/ACL3.png)

VLAN 10's network address: 10.16.0.0/24

PC10's IP address: 10.16.0.10
PC10's default gateway: 10.16.0.1
![ACLs](/Images/ACL9.png)

Router R1's interface g0/0 IP address: 10.16.6.5

# Objective
Block all traffic from the source IP address 10.16.0.10 on router R1.

# Performance
## Change router R1 name from R1-AZ to R1-ML.
![ACLs](/Images/ACL1.png)

## Create an access list
### Deny
![ACLs](/Images/ACL4.png)
![ACLs](/Images/ACL5.png)

### Permit
![ACLs](/Images/ACL12.png)
### Note: ACLs automatically block traffic that doesn't match a 'permit' rule (implicit 'deny any'). That was why 'permit any' rule was added in my configuration to allow unmatched traffic.

##  Apply the access list on the router R1-ML to filter inbound traffic.
![ACLs](/Images/ACL7.png)

### Check
The inbound access list is 1 now!
![ACLs](/Images/ACL8.png)

### Test
The result was expected. The traffic went from PC10 to R1 and was block at R1's int g0/0
![ACLs](/Images/ACL11.png)









## 

