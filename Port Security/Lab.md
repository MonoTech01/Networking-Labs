# 1
## f0/1 - f0/3
***
    SW1>en
    SW1#config t
    Enter configuration commands, one per line.  End with CNTL/Z.
    SW1(config)#int range f0/1-f0/3
    SW1(config-if-range)#sw port-security
    Command rejected: FastEthernet0/1 is a dynamic port.
    Command rejected: FastEthernet0/2 is a dynamic port.
    Command rejected: FastEthernet0/3 is a dynamic port.

### Note: 
- Port Security only enable on a trunk or access port.
- By default: Violation mode is shutdown and Sticky learning is disable! So, We don't need to config them in this case!
***
    SW1(config-if-range)#sw mode access
    SW1(config-if-range)#sw port-security

    SW1(config-if-range)#sw port-security aging ?
      time  Port-security aging time	
    SW1(config-if-range)#sw port-security aging time ?
      <1-1440>  Aging time in minutes. Enter a value between 1 and 1440
    SW1(config-if-range)#sw port-security aging time 60

    SW1(config-if-range)#sw port-security maximum ?
    <1-132>  Maximum addresses
    SW1(config-if-range)#sw port-security maximum 1
    SW1(config-if-range)#

# 2

