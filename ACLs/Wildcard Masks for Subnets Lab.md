# Objective [Block multiple networks]
Block all traffic from the network address 10.16.0.0/21 on R1. 

# Topology
Note: I've used Packet Tracer to replicate the necessary parts of the original network for this task.
![ACLs](/Images/ACL17a.png)

# What is the network address 10.16.0.0/21?
Let me subnet it!

The subnet mask is 255.255.248.0

The network/21 (affected the third octet) increases by 8, so the next network is 10.16.8.0/21

The broadcast address is 10.16.7.255

The last usable address is 10.16.7.254

The first usable address is 10.16.0.1

# What to expect before creating an ACL on R1?
![ACL](/Images/ACL13.png)

# Assess the network
Similar to the other ACL labs, I checked that there was no ACL configuration on R1.
![ACL](/Images/ACL18.png)
![ACL](/Images/ACL19.png)
![ACL](/Images/ACL19a.png)
![ACL](/Images/ACL20.png)
![ACL](/Images/ACL20a.png)

# Create an ACL on R1
![ACL](/Images/ACL21.png)

# Apply the ACL on R1's int g0/0
Because I blocked many networks including vlan 10, vlan 20, vlan 30, vlan 40, I am "destroying" the routing protocol :imp:.
![ACL](/Images/ACL22.png)

# Expected Result

They've been blacklisted and they're feeling blue...bye /21!!!

![ACL](/Images/ACL23.png)








