# Note
Standard ACLs filter traffic based on the source IP address only. A typical best practice for standard ACLs is to configure and apply the ACL as close to the destination as possible. 
# Topology and Addressing Table

![ACLs_5.2.7](/Images/5.2.7_1.png)
![ACLs_5.2.7](/Images/5.2.7_2.png)



# Task 1
For the first access list in this activity, create a standard numbered ACL that allows traffic from all hosts on the 192.168.10.0/24 network and all hosts on the 192.168.20.0/24 network to access all hosts on the 192.168.30.0/24 network. The security policy also states that an explicit deny any access control entry (ACE), also referred to as an ACL statement, should be present at the end of all ACLs.

![ACLs_5.2.7](/Images/5.2.7_3.png)
![ACLs_5.2.7](/Images/5.2.7_4.png)
![ACLs_5.2.7](/Images/5.2.7_5.png)

## Verify
![ACLs_5.2.7](/Images/5.2.7_6.png)
![ACLs_5.2.7](/Images/5.2.7_7.png)
![ACLs_5.2.7](/Images/5.2.7_8.png)

# Task 2
- Create a named standard ACL that conforms to the following policy: allow traffic from all hosts on the 192.168.40.0/24 network access to all hosts on the 192.168.10.0/24 network. Also, only allow host PC-C access to the 192.168.10.0/24 network. The name of this access list should be called BRANCH-OFFICE-POLICY. 
- Problem: Security policies changed, and now an Access Control List (ACL) needs updating to match new rules. Currently, a PC can't reach an internet server because the ACL is blocking return traffic. New Rules:
Allow traffic from a specific internet network (209.165.200.224/27) to access a local network (192.168.10.0/24).
All ACLs should end with a "deny any" rule for better consistency.
=> What to do: Update the "BRANCH-OFFICE-POLICY" ACL to reflect these changes.
### Note: Instead of deleting and recreating the whole ACL, you can directly modify the ACL by adding/removing specific lines for efficiency and accuracy.

![ACLs_5.2.7](/Images/5.2.7_9.png)
![ACLs_5.2.7](/Images/5.2.7_10.png)
![ACLs_5.2.7](/Images/5.2.7_11.png)

## Verify
![ACLs_5.2.7](/Images/5.2.7_12.png)


# Report - 100% Completion
![ACLs_5.2.7](/Images/5.2.7_13.png)
