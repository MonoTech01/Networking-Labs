Task:

Login to device R1 and you'll notice that it has a non-default configuration already on it (as evidenced by its host name). Reset this device to a factory default configuration.

Login to every device and configure the following items:

A hostname that matches the device name in the topology diagram

A command that prevents the device from attempting to resolve via DNS mistyped commands

A command that repeats your most recent input/typing to the screen after an interruption by a SYSLOG or other console message.

A password of "INE" to be required whenever anyone attempts to gain access to Privileged EXEC mode. This password should not be visible in plaintext in the output of the configuration file.

Enable every interface shown in the topology diagram and provide a brief interface description such that anyone looking at your configuration will know what that interface connects to.

When you are done with this step, utilize CDP on Switch-2, R5 and R4 to confirm those devices can see (as CDP neighbors) other connected Cisco devices.

Configure devices R1 and R3 to allow inbound Telnet connections. These connections should be authenticated against a preconfigured password of "cisco".

Configure devices R2 and R5 to allow inbound SSH (version-2) connections. These connections should be authenticated against a username of "admin" and a (Privilege Level 15) password of "ine". You may use your own discretion to complete any other required keywords or features required for SSH configuration.

Derive an IP addressing scheme for network segments A through F using the following guidelines:

Your starting network should be 180.50.0.0/16

Your first/largest subnet should be 180.50.0.0 with a new/different subnet mask.

You must use the VLSM method, utilizing the fewest/least host bits in each network as possible per the host requirements shown below:

Network Segment	Required Hosts	Subnet Mask	Prefix
A	99		
B	13		
C	6		
D	11		
E	26		
F	30		
Apply IPv4 addresses to your router interfaces using the following guidelines:

Routers connecting to network segments "A" through "D" should be given the first available host address(s) within each respective subnet.

Don't worry about addressing router R3's Gig0/2 interface yet (for Segments-E and F). That will be accomplished in another lab.

Routers R3(Gig0/0 and Gig0/1), R4 and R5 should be configured using the IPv4 addresses and masks shown in the topology diagram.

Verify your IPv4 addressing configuration by performing the following actions:

Confirm that you can Telnet from R2 to R1

Confirm that you can Telnet from R4 to R3

Confirm that you can SSH from R1 to R2

Confirm that you can SSH from R4 to R5
