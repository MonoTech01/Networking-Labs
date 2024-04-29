# Topology

# Tasks
- Configure Dynamic NAT with Overload 
- Verify Dynamic NAT with Overload Implementation
- Configure PAT using an Interface
- Verify PAT Interface Implementation

# Part 1: Configure Dynamic NAT with Overload
## Step 1: Configure traffic that will be permitted.

## Step 2: Configure a pool of address for NAT.

## Step 3: Associate ACL 1 with the NAT pool and allow addresses to be reused.

## Step 4: Configure the NAT interfaces.

# Part 2: Verify Dynamic NAT with Overload Implementation
## Step 1: Access services across the internet.

### Q & A
Were all connections successful?

## Step 2: View NAT translations.
Notice that all four devices were able to communicate, and they are using just one address out of the pool. PAT will continue to use the same address until it runs out of port numbers to associate with the translation. Once that occurs, the next address in the pool will be used. While the theoretical limit would be 65,536 since the port number field is a 16 bit number, the device would likely run out of memory before that limit would be reached.

# Part 3: Configure PAT using an Interface
## Step 1: Configure traffic that will be permitted.

## Step 2: Associate ACL 2 with the NAT interface and allow addresses to be reused.

## Step 3: Configure the NAT interfaces.

# Part 4: Verify PAT Interface Implementation
## Step 1: Access services across the internet.

### Q & A
Were all connections successful?

## Step 2: View NAT translations.

## Step 3: Compare NAT statistics on R1 and R2.

### Q & A
Why doesn’t R2 list any dynamic mappings?


 
