# Objectives
R2: The 192.168.11.0/24 network is not allowed access to the WebServer on the 192.168.20.0/24 network. All other access is permitted.

R3: The 192.168.10.0/24 network is not allowed to communicate with the 192.168.30.0/24 network. All other access is permitted.



# Topology & Addressing Table
![ACL_PT](/Images/PT_5.1.8_2.png)

![ACL_PT](/Images/PT_5.1.8_1.png)

# Access the networks and devices
## R2
![ACL_PT](/Images/PT_5.1.8_3.png)
## R3
![ACL_PT](/Images/PT_5.1.8_7.png)

# Plan, Implement, Apply, Check
## R2
![ACL_PT](/Images/PT_5.1.8_4.png)
![ACL_PT](/Images/PT_5.1.8_5.png)
![ACL_PT](/Images/PT_5.1.8_6.png)

## R3
![ACL_PT](/Images/PT_5.1.8_8.png)
![ACL_PT](/Images/PT_5.1.8_9.png)
![ACL_PT](/Images/PT_5.1.8_10.png)

# Verify












### Step 3: Verify ACL configuration and functionality.
a.     Enter the show run or show ip interface gigabitethernet 0/0 command to verify the ACL placements.

b.     With the two ACLs in place, network traffic is restricted according to the policies detailed in Part 1. Use the following tests to verify the ACL implementations:

·         A ping from 192.168.10.10 to 192.168.11.10 succeeds.

·         A ping from 192.168.10.10 to 192.168.20.254 succeeds.

·         A ping from 192.168.11.10 to 192.168.20.254 fails.

·         A ping from 192.168.10.10 to 192.168.30.10 fails.

·         A ping from 192.168.11.10 to 192.168.30.10 succeeds.

·         A ping from 192.168.30.10 to 192.168.20.254 succeeds.

c.     Issue the show access-lists command again on routers R2 and R3. You should see output that indicates the number of packets that have matched each line of the access list. Note: The number of matches shown for your routers may be different, due to the number of pings that are sent and received.

R2# show access-lists

Standard IP access list 1

10 deny 192.168.11.0 0.0.0.255 (4 match(es))

20 permit any (8 match(es))

 

R3# show access-lists

Standard IP access list 1

10 deny 192.168.10.0 0.0.0.255 (4 match(es))

20 permit any (8 match(es))
