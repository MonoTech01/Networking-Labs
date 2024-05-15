# Topology & Addressing Table
![CDP](/Images/CDP-pic0.png)

![CDP](/Images/CDP-pic1.png)


# Part 1: Use SSH to Remotely Access Network Devices
In Part 1, use the Admin-PC to remotely access the Edge1 gateway router. Next, from the Edge1 router you will SSH into the Remote Branch Office.

a.     On the Admin-PC, open a command prompt.

b.     SSH into the gateway router at 192.168.1.1 using the username admin01 and the password S3cre7P@55.

PC> ssh –l admin01 192.168.1.1

Open

Password:

Edge1#

Note: Notice that you are placed directly into privileged EXEC mode. This is because the admin01 user account is set to privilege level 15.

c.     Use the show ip interface brief and show interfaces commands to document the Edge1 router’s physical interfaces, IP addresses, and subnet masks in the Addressing Table.

d.     From Edge1, use SSH to access the Remote Branch Office at 209.165.200.10 with the username branchadmin and the same password as above:

Edge1# ssh –l branchadmin 209.165.200.10

Open

Password:

Branch-Edge#

Q: After connecting to the Remote Branch Office what piece of previously missing information can now be added to the Addressing Table above?
A: 

# Part 2: Use CDP to Discover Neighboring Devices
You are now remotely connected to the Branch-Edge router. Using CDP, begin looking for connected network devices.

a.     Issue the show ip interface brief and show interfaces commands to document the Branch-Edge router’s network interfaces, IP addresses, and subnet masks. Add the missing information to the Addressing Table to map the network:

Branch-Edge# show ip interface brief

Branch-Edge# show interfaces

b.     Security best practice recommends only running CDP when needed, so CDP may need to be turned on. Use the show cdp command to display its status.

Branch-Edge# show cdp

% CDP is not enabled

c.     You need to turn on CDP, but it is a good idea to only broadcast CDP information to internal network devices and not to external networks. To do this, turn on the CDP protocol and then disable CDP on the S0/0/1 interface.

Branch-Edge# configure terminal

Branch-Edge(config)# cdp run

Branch-Edge(config)# interface s0/0/1

Branch-Edge(config-if)# no cdp enable

Branch-Edge(config-if)# exit

d.     Issue a show cdp neighbors command to find any neighboring network devices.

Note: CDP will only show connected Cisco devices that are also running CDP.

Branch-Edge# show cdp neighbors

Q: Is there a neighboring network device? What type of device is it? What is its name? On what interface is it connected? Is the device’s IP address listed? Record the information in the Addressing Table.
A: 

## Note: It may take some time for CDP updates to be received. If you see no output from the command, press the Fast Forward Time button several times.

e.     To find the IP address of the neighboring device use the show cdp neighbors detail command and record the ip address:

Branch-Edge# show cdp neighbors detail

Q: Aside from the neighboring device’s IP address, what other piece of potentially sensitive information is listed?
A: 

f.      Now that you know the IP address of the neighbor device, connect to it with SSH in order to discover other devices that may be its neighbors.

## Note: To connect with SSH use the same Remote Branch Office username and password.

Branch-Edge# ssh –l branchadmin <the ip address of the neighbor device>

Q: After successfully connecting with SSH, what does the command prompt show?
A: 

g.     You are remotely connected to the next neighbor. Use the show cdp neighbors command, and the show cdp neighbors detail command, to discover other connected neighbor devices.

Question:
What types of network devices neighbor this device? Record any newly discovered devices in the Addressing Table. Include their hostname, interfaces, and IP addresses.

h.     Continue discovering new network devices using SSH and the show CDP commands. Eventually, you will reach the end of the network and there will be no more devices to discover.

Question:
What is the name of the switch that does not have an IP address on the network?

i.      Draw a topology of the Remote Branch Office network using the information you have gathered using CDP.
