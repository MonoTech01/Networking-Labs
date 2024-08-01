# Topology

    Sw1                                          Sw2
    
    g0/0                                         g0/3
    
    g0/1                                         g0/2
    
    g0/2                                         g0/1
    
    g0/3                                         g0/0

    VLAN 10 - PC10a 10.10.0.51/24               PC10b 10.10.0.52/24
  
    VLAN 20 - PC20a 10.20.0.51/24               PC20b 10.20.0.52/24

# Task
## Configure Etherchannel Sw1 - Sw2
- LACP Sw1 active, Sw2 passive
- Encapsulation dot1q
- Mode trunk
  
# Performance

