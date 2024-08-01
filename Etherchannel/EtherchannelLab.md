# Lab Report

## Source
Performed the lab using the Adept-CBT platform.

## Mission
Create an EtherChannel bundle between switches Sw1 and Sw2 to function as a trunk link.

## Topology

    Sw1                                          Sw2
    
    g0/0                                         g0/3
    
    g0/1                                         g0/2
    
    g0/2                                         g0/1
    
    g0/3                                         g0/0

    VLAN 10 - PC10a 10.10.0.51/24               PC10b 10.10.0.52/24
  
    VLAN 20 - PC20a 10.20.0.51/24               PC20b 10.20.0.52/24

## Task
- Configure EtherChannel between switches Sw1 and Sw2.

- Requirements
    - Protocol: LACP (Link Aggregation Control Protocol)
    - Sw1: Active LACP negotiation
    - Sw2: Passive LACP negotiation
    - Trunking: 802.1Q encapsulation
  
## Performance
        Sw1
        en
        config t
        int range g0/0-3
        shut
        sw trunk encap dot1q
        sw mode trunk
        channel-group 1 mode active
        no shut

        Sw2
        en
        config t
        int range g0/0-3
        shut
        sw trunk encap dot1q
        sw mode trunk
        channel-group 1 mode passive
        no shut

        Verify for both switches
        show int status
        show etherchannel sum
        show etherchannel
        show lacp neighbor
        show etherchannel detail
        
        ping PCs to each other

        More commands to verify
        show etherchannel protocol
        show etherchannel load-balance
        show interfaces trunk
        show interface po1
        show run int po1
        show int po1 switchport

        
