# Toppology
![VPN](/Images/VPN-0.png)
# Addressing Table + Phase 1 & 2 Policy Parameters + Passwords
![VPN](/Images/VPN-1.png)
![VPN](/Images/VPN-2.png)
# Part 1: Configure IPsec Parameters on R1

## Step 1: Test connectivity.

Ping from PC-A to PC-C.

### Check PC-C's IP address
![VPN](/Images/VPN-3.png)

### Ping -> Worked!
![VPN](/Images/VPN-4.png)

## Step 2: Enable the Security Technology package.

### a.     On R1, issue the show version command to view the Security Technology package license information.
security      disable       None          None => It's not enabled yet!

![VPN](/Images/VPN-5.png)


### b,c   If the Security Technology package has not been enabled, use the following command to enable the package

R1(config)# license boot module c1900 technology-package securityk9
![VPN](/Images/VPN-6.png)

Check:

![VPN](/Images/VPN-7.png)

d.     Save the running-config and reload the router to enable the security license.

![VPN](/Images/VPN-8.png)


e.     Verify that the Security Technology package has been enabled by using the show version command.

Check the package after the reload!

![VPN](/Images/VPN-9.png)

## Step 3: Identify interesting traffic on R1.

Configure ACL 110 to identify the traffic from the LAN on R1 to the LAN on R3 as interesting. This interesting traffic will trigger the IPsec VPN to be implemented when there is traffic between the R1 to R3 LANs. All other traffic sourced from the LANs will not be encrypted. Because of the implicit deny all, there is no need to configure a deny ip any any statement.

![VPN](/Images/VPN-10.png)

## Step 4: Configure the IKE Phase 1 ISAKMP policy on R1.

Configure the crypto ISAKMP policy 10 properties on R1 along with the shared crypto key vpnpa55. Refer to the ISAKMP Phase 1 table for the specific parameters to configure. Default values do not have to be configured. Therefore, only the encryption method, key exchange method, and DH method must be configured.

Note: The highest DH group currently supported by Packet Tracer is group 5. In a production network, you would configure at least DH 14.

![VPN](/Images/VPN-11.png)

## Step 5: Configure the IKE Phase 2 IPsec policy on R1.

a.     Create the transform-set VPN-SET to use esp-aes and esp-sha-hmac.

R1(config)# crypto ipsec transform-set VPN-SET esp-aes esp-sha-hmac

![VPN](/Images/VPN-12.png)

b.     Create the crypto map VPN-MAP that binds all of the Phase 2 parameters together. Use sequence number 10 and identify it as an ipsec-isakmp map.

![VPN](/Images/VPN-13.png)

I added my configuration the IKE in step 5a. 

![VPN](/Images/VPN-14.png)


Step 6: Configure the crypto map on the outgoing interface.

Bind the VPN-MAP crypto map to the outgoing Serial 0/0/0 interface.

![VPN](/Images/VPN-15.png)


# Part 2: Configure IPsec Parameters on R3

## Step 1: Enable the Security Technology package.

a.     On R3, issue the show version command to verify that the Security Technology package license information has been enabled.

b.     If the Security Technology package has not been enabled, enable the package and reload R3.

## Step 2: Configure router R3 to support a site-to-site VPN with R1.

Configure reciprocating parameters on R3. Configure ACL 110 identifying the traffic from the LAN on R3 to the LAN on R1 as interesting.

![VPN](/Images/VPN-19.png)


## Step 3: Configure the IKE Phase 1 ISAKMP properties on R3.

I forgot to screenshoot for this step, but I listed my commands below:

R3(config)# crypto isakmp policy 10

R3(config-isakmp)# encryption aes 256

R3(config-isakmp)# authentication pre-share

R3(config-isakmp)# group 5

R3(config-isakmp)# exit

R3(config)# crypto isakmp key vpnpa55 address 10.1.1.2

## Step 4: Configure the IKE Phase 2 IPsec policy on R3.

a.     Create the transform-set VPN-SET to use esp-aes and esp-sha-hmac.

I forgot to screenshoot for this step, but I listed my commands below:

R3(config)# crypto ipsec transform-set VPN-SET esp-aes esp-sha-hmac

b.     Create the crypto map VPN-MAP that binds all of the Phase 2 parameters together. Use sequence number 10 and identify it as an ipsec-isakmp map.

![VPN](/Images/VPN-17.png)

## Step 5: Configure the crypto map on the outgoing interface.

Bind the VPN-MAP crypto map to the outgoing Serial 0/0/1 interface. 

![VPN](/Images/VPN-18.png)


# Part 3: Verify the IPsec VPN

## Step 1: Verify the tunnel prior to interesting traffic.

Issue the show crypto ipsec sa command on R1. Notice that the number of packets encapsulated, encrypted, decapsulated, and decrypted are all set to 0.

## Step 2: Create interesting traffic.

Ping PC-C from PC-A.

![VPN](/Images/VPN-21.png)
![VPN](/Images/VPN-22.png)

## Step 3: Verify the tunnel after interesting traffic.

On R1, re-issue the show crypto ipsec sa command. Notice that the number of packets is more than 0, which indicates that the IPsec VPN tunnel is working.

## Step 4: Create uninteresting traffic.
 Ping PC-B from PC-A.  Note: Issuing a ping from router R1 to PC-C or R3 to PC-A is not interesting traffic.


## Step 5: Verify the tunnel.

On R1, re-issue the show crypto ipsec sa command. Notice that the number of packets has not changed, which verifies that uninteresting traffic is not encrypted.

![VPN](/Images/VPN-23.png)


# Completion
![VPN](/Images/VPN-24.png)
