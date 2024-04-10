# Topology
![ACLs](/Images/ACL00.png)

VLAN 10's network address: 10.16.0.0/24

Note: I've used Packet Tracer to replicate the necessary parts of the original network for this task.

# Objective
Block all traffic from the source IP address of PC10 10.16.0.10 on R1.

# Performance

## Assess the network
### PC10
PC10's IP address is 10.16.0.10, and the default gateway is 10.16.0.1.
![ACLs](/Images/ACL9.png)
### R1
Router R1's interface g0/0 IP address is 10.16.6.5, and no access list was configured.
![ACLs](/Images/ACL2.png)

## Create an access list
### Deny
![ACLs](/Images/ACL4.png)
![ACLs](/Images/ACL5.png)

### Permit
ACLs automatically block traffic that doesn't match a 'permit' rule (implicit 'deny any'). That was why 'permit any' rule was added in my configuration to allow unmatched traffic.
![ACLs](/Images/ACL12.png)

##  Apply the access list on R1 to filter inbound traffic.
![ACLs](/Images/ACL7.png)
The inbound access list is 1 now!
![ACLs](/Images/ACL8.png)

## Test
The result was expected. The traffic went from PC10 to R1 and was block at R1's int g0/0.
![ACLs](/Images/ACL11.png)

The access-list 1 on R1 showed how many IP addresses matched for deny rule and permit rule.
![ACLs](/Images/ACL10.png)










## 

