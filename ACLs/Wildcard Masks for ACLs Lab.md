# Objective [Block 1 Network]
Block all traffic from the network address 10.16.0.0/24 on R1.

# Topology
![ACLs](/Images/ACL00.png)

VLAN 10's network address: 10.16.0.0/24

Note: I've used Packet Tracer to replicate the necessary parts of the original network for this task.
## Note 
This lab uses the same network setup as the "Standard ACLs Lab". I'll repeat some of the steps, providing a summarized version below. Please check "Standard ACLs Lab" as needed. 
### The similar steps
Access the network: PC10's IP address is 10.16.0.10, and the default gateway is 10.16.0.1; Router R1's interface g0/0 IP address is 10.16.6.5, and no access list was configured.

## What to expect before configuring an ACL to block the network address on R1?
![ACL](/Images/ACL13.png)
## Configuring the ACL and apply it on R1's int g0/0
![ACL](/Images/ACL14.png)
## Always check the configuration
![ACL](/Images/ACL16.png)
## Expected Result
![ACL](/Images/ACL15.png)

## Tip
If you configure an ACL but do not see any logs or expected results, you might forget to apply it on a router's int.


 



