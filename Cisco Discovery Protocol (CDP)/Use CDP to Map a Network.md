# Topology & Addressing Table
![CDP](/Images/CDP-pic0.png)

![CDP](/Images/CDP-pic1.png)

# Scenario
A senior network administrator requires you to map the Remote Branch Office network and discover the name of a recently installed switch that still needs an IP address to be configured. Your task is to create a map of the branch office network. You must record all of the network device names, IP addresses and subnet masks, and physical interfaces interconnecting the network devices, as well as the name of the switch that does not have an IP address.

To map the network, you will use SSH for remote access and the Cisco Discovery Protocol (CDP) to discover information about neighboring network devices. Because CDP is a Layer 2 protocol, it can be used to discover information about devices that do not have IP addresses. You will record the gathered information to complete the Addressing Table and provide a topology diagram of the Remote Branch Office network.

The local and remote administrative usernames and passwords are:

Local Network

Username: admin01

Password: S3cre7P@55

Branch Office Network

Username: branchadmin

Password: S3cre7P@55


# Part 1: Use SSH to Remotely Access Network Devices
In Part 1, use the Admin-PC to remotely access the Edge1 gateway router. Next, from the Edge1 router you will SSH into the Remote Branch Office.

a.     On the Admin-PC, open a command prompt.

b.     SSH into the gateway router at 192.168.1.1 using the username admin01 and the password S3cre7P@55.

![CDP](/Images/CDP-pic2.png)

Note: Notice that you are placed directly into privileged EXEC mode. This is because the admin01 user account is set to privilege level 15.

c.     Use the show ip interface brief and show interfaces commands to document the Edge1 router’s physical interfaces, IP addresses, and subnet masks in the Addressing Table.

![CDP](/Images/CDP-pic3.png)

![CDP](/Images/CDP-pic4.png)

d.     From Edge1, use SSH to access the Remote Branch Office at 209.165.200.10 with the username branchadmin and the same password as above:

![CDP](/Images/CDP-pic5.png)

![CDP](/Images/CDP-pic6.png)

# Part 2: Use CDP to Discover Neighboring Devices
You are now remotely connected to the Branch-Edge router. Using CDP, begin looking for connected network devices.

a.     Issue the show ip interface brief and show interfaces commands to document the Branch-Edge router’s network interfaces, IP addresses, and subnet masks. Add the missing information to the Addressing Table to map the network:

Branch-Edge# show ip interface brief

Branch-Edge# show interfaces

b.     Security best practice recommends only running CDP when needed, so CDP may need to be turned on. Use the show cdp command to display its status.

![CDP](/Images/CDP-pic7.png)

c.     You need to turn on CDP, but it is a good idea to only broadcast CDP information to internal network devices and not to external networks. To do this, turn on the CDP protocol and then disable CDP on the S0/0/1 interface.

![CDP](/Images/CDP-pic8.png)


d.     Issue a show cdp neighbors command to find any neighboring network devices.

Note: CDP will only show connected Cisco devices that are also running CDP.

![CDP](/Images/CDP-pic9.png)

## Note: It may take some time for CDP updates to be received. If you see no output from the command, press the Fast Forward Time button several times.

e.     To find the IP address of the neighboring device use the show cdp neighbors detail command and record the ip address:

![CDP](/Images/CDP-pic10.png)

f.      Now that you know the IP address of the neighbor device, connect to it with SSH in order to discover other devices that may be its neighbors.

## Note: To connect with SSH use the same Remote Branch Office username and password.

Branch-Edge# ssh –l branchadmin <the ip address of the neighbor device>

![CDP](/Images/CDP-pic11.png)

g.     You are remotely connected to the next neighbor. Use the show cdp neighbors command, and the show cdp neighbors detail command, to discover other connected neighbor devices.

![CDP](/Images/CDP-pic12.png)

![CDP](/Images/CDP-pic13.png)

h.     Continue discovering new network devices using SSH and the show CDP commands. Eventually, you will reach the end of the network and there will be no more devices to discover.

i.      Draw a topology of the Remote Branch Office network using the information you have gathered using CDP.
