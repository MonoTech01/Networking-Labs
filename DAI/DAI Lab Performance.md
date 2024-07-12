Things we should check before configuring DAI on VLAN 30:
- DHCP snooping and DHCP binding
- DAI disabled on VLAN 30.

![DAI](/DAI/Images/DAI0.png)

# 1. Make g3/3 of R3 a trusted port

![DAI](/DAI/Images/DAI1.png)

![DAI](/DAI/Images/DAI2.png)

# 2. DAI on VLAN 30
![DAI](/DAI/Images/DAI3.png)

A broadcast of a different network from g0/0 is blocked

# 3. Verify
![DAI](/DAI/Images/DAI4.png)

Note:
The DAI process can use the binding table from DHCP snooping but may deny some ARP messages because they're from non-DHCP clients and the switch doesn't know the L3/L2 mappings for those clients



