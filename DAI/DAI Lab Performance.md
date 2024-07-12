Things we should check before configuring DAI on VLAN 30:
- DHCP snooping and DHCP binding
- DAI disabled on VLAN 30.
# 1. Make g3/3 of R3 a trusted port

# 2. DAI on VLAN 30

Note:
The DAI process can use the binding table from DHCP snooping but may deny some ARP messages because they're from non-DHCP clients and the switch doesn't know the L3/L2 mappings for those clients



