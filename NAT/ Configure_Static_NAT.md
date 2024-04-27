# Scenario
In IPv4 configured networks, clients and servers use private addressing. Before packets with private addressing can cross the internet, they need to be translated to public addressing. Servers that are accessed from outside the organization are usually assigned both a public and a private static IP address. 
# Task
Configure static NAT so that outside devices can access an inside server at its public address.

# Topology and Addressing Table
![StaticNAT](/Images/StaticNAT-0.png)

# Access the network
## Connectivity 
PC1 and L1 do not successfully access Server 1
PC1 and L1 can ping R1
## Check R1's routing table and running-config 
## Configure static NAT
### NAT Statement
### Apply to R1's interfaces: inside and outside


