# Topology
![NAT](/Images/PAT-1.png)

# Tasks
- Configure Dynamic NAT with Overload 
- Verify Dynamic NAT with Overload Implementation
- Configure PAT using an Interface
- Verify PAT Interface Implementation

# Part 1: Configure Dynamic NAT with Overload

## Step 1: Configure traffic that will be permitted.

On R1, configure one statement for ACL 1 to permit any address belonging to 172.16.0.0/16.

![NAT](/Images/PAT-2.png)


## Step 2: Configure a pool of address for NAT.
Configure R1 with a NAT pool that uses the two useable addresses in the 209.165.200.232/30 address space.
![NAT](/Images/PAT-3.png)

## Step 3: Associate ACL 1 with the NAT pool and allow addresses to be reused.

![NAT](/Images/PAT-4.png)

## Step 4: Configure the NAT interfaces.

Configure R1 interfaces with the appropriate inside and outside NAT commands.

![NAT](/Images/PAT-5.png)


# Part 2: Verify Dynamic NAT with Overload Implementation

## Step 1: Access services across the internet.
![NAT](/Images/PAT-6.png)
![NAT](/Images/PAT-7.png)
![NAT](/Images/PAT-8.png)
![NAT](/Images/PAT-9.png) 

### Q & A
Were all connections successful? YES!

## Step 2: View NAT translations.
![NAT](/Images/PAT-10.png)

Notice that all four devices were able to communicate, and they are using just one address out of the pool. PAT will continue to use the same address until it runs out of port numbers to associate with the translation. Once that occurs, the next address in the pool will be used. While the theoretical limit would be 65,536 since the port number field is a 16 bit number, the device would likely run out of memory before that limit would be reached.



# Part 3: Configure PAT using an Interface

## Step 1 + 2: Configure traffic that will be permitted + Associate ACL 2 with the NAT interface and allow addresses to be reused.
![NAT](/Images/PAT-11.png)

## Step 3: Configure the NAT interfaces.
![NAT](/Images/PAT-12.png)

# Part 4: Verify PAT Interface Implementation
## Step 1: Access services across the internet

PC3, L3, PC4, L4 successfully ping 209.165.201.5 

### Q & A
Were all connections successful? Yes!

## Step 2: View NAT translations.

![NAT](/Images/PAT-13.png)

# Compare NAT statistics on R1 and R2.

### Q & A
Why doesn’t R2 list any dynamic mappings?


 
