# Topology
![NAT](/Images/DynamicNAT-1.png)

# Tasks
Configure Dynamic NAT + Verify NAT Implementation

# Task 1: Configure Dynamic NAT
## Configure traffic that will be permitted.

On R2, configure one statement for ACL 1 to permit any address belonging to the 172.16.0.0/16 network.

![NAT](/Images/DynamicNAT-2.png)

## Configure a pool of address for NAT.

Configure R2 with a NAT pool that uses two addresses in the 209.165.200.228/30 address space.

![NAT](/Images/DynamicNAT-3.png)


## Associate ACL 1 with the NAT pool.
Enter the command that associates ACL 1 with the NAT pool that you just created.

![NAT](/Images/DynamicNAT-4.png)


## Configure the NAT interfaces.

Configure R2 interfaces with the appropriate inside and outside NAT commands.

![NAT](/Images/DynamicNAT-5.png)

## Access services across the internet.
From the web browser of L1, PC1, or PC2, access the web page for Server1.

## View NAT translations.
View the NAT translations on R2. Identify the internal source address of the PC and the translated address from the NAT pool in the command output.

R2# show ip nat translations

# Report - 100% Completion

![NAT](/Images/DynamicNAT-6.png)


