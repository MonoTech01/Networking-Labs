# Objective [Block multiple networks]
Block all traffic from the network address 10.16.0.0/21 on R1. 

# Topology
Note: I've used Packet Tracer to replicate the necessary parts of the original network for this task.
![ACLs](/Images/ACL17.png)

# What is the network address 10.16.0.0/21?
Let me subnet it!
The subnet mask is 255.255.248.0
The network/21 (affected the third octet) increases by 8, so the next network is 10.16.8.0/21
The broadcast address is 10.16.7.255
The last usable address is 10.16.7.254
The first usable address is 10.16.0.1

