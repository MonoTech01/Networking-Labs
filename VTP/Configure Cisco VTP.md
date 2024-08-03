# Lab Report

## Goal:

This lab exercise involves configuring VLANs, trunking, and VTP to enable communication between devices on different subnets.

# VLAN and VTP Configuration Instructions:

## Part 1: Trunk Configuration
- Configure Trunks: Configure all connections between switches (SW1, SW2, and SW3) as 802.1Q trunks.
- Verify Trunking: Ensure successful trunk configuration by pinging from PC-10a to the Server at IP address 10.30.0.100. If ping is successful, trunking is working properly.
  
      SW1
      int g0/0
      (config-if)# switchport trunk encap dot1q
      (config-if)# switchport mode trunk
      (config-if)# no shut

      SW2
      int range g0/1-2
      (config-if)# sw tr en d
      (config-if)# sw mode trunk
      (config-if)# no shut

      SW3
      int g0/3
      (config-if)# sw tr en d
      (config-if)# sw mode trunk
      (config-if)# no shut

      Ping successfully!!!!
      
  
## Part 2: VTP Configuration
- Configure VTP Domain: Domain Name: Mono; Password: Mono1; Mode: SW1 - Server, SW3 - Server, SW2 - Client

      SW1, SW2, SW3
      (config)# vtp domain Mono
      (config)# vtp password Mono1
  
      SW1,SW3
      (config)# vtp mode server

      SW2
      (config)# vtp mode client
       
## Part 3: VLAN and SVI Configuration
- Create VLAN 50: On either SW1 or SW3 (VTP servers), and name it "V50".
- Configure SVI for VLAN 50: On each switch (SW1, SW2, SW3), configure an SVI for VLAN 50. Assign an IP address in the 10.5.0.0/24 subnet to each SVI, using the switch number as the last octet (e.g., SW1: 10.5.0.1, SW2: 10.5.0.2, SW3: 10.5.0.3).

SW1





## Part 4: Verification
- Verify VLAN and SVI Configuration: From the command line of any switch, ping the SVI IP addresses of the other two switches on VLAN 50. Successful pings confirm correct VLAN and SVI configuration.
  
# Note: This simple password is for lab purposes only. Use strong and unique passwords in production environments.
