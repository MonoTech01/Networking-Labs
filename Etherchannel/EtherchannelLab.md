# Lab Report

## Mission
Create a etherchannel bundle for a trunk link between Sw1 and Sw2

## Topology

    Sw1                                          Sw2
    
    g0/0                                         g0/3
    
    g0/1                                         g0/2
    
    g0/2                                         g0/1
    
    g0/3                                         g0/0

    VLAN 10 - PC10a 10.10.0.51/24               PC10b 10.10.0.52/24
  
    VLAN 20 - PC20a 10.20.0.51/24               PC20b 10.20.0.52/24

## Task
Configure Etherchannel Sw1 - Sw2
- LACP Sw1 active, Sw2 passive
- Encapsulation dot1q
- Mode trunk
  
## Performance
        Sw1
        en
        config t
        int range g0/0-3
        sw trunk encap dot1q
        sw mode trunk
        channel-group 1 mode active
        no shut

        Sw2
        en
        config t
        int range g0/0-3
        sw trunk encap dot1q
        sw mode trunk
        channel-group 1 mode passive
        no shut

        Verify for both switches
        show int status
        show LACP neighbors
        show etherchannel sum
        
