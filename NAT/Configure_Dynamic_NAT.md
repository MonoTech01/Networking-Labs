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
![NAT](/Images/DynamicNAT-7.png)
![NAT](/Images/DynamicNAT-8.png)
![NAT](/Images/DynamicNAT-9.png)

## View NAT translations.

![NAT](/Images/DynamicNAT-10.png)

# Q & A
Q: What will happen if more than 2 devices attempt to access the internet?

A: If more than two devices from the 172.16.0.0/16 network attempt to access the internet, only two devices will be able to receive a translated public IP address from the pool. This is because the pool only has two addresses. Subsequent devices will be unable to initiate outbound connections until an address in the pool becomes available (due to a device stopping its internet activity).

# Report - 100% Completion

![NAT](/Images/DynamicNAT-6.png)


