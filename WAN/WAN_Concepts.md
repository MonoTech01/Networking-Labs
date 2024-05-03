# Objectives
Investigating various types of WANs by exploring a topology that uses diverse connectivity technologies by describing different WAN connectivity options.

# Scenario
Explore WAN technologies that are used to connect business and home users to data services.

# Topology
![WAN](/Images/WANconcepts-0.png)

# Part 1: Investigate Consumer WAN Technologies for Home and Mobile Devices

## Step 1: Explore Consumer WAN Technologies
In this step, you will explore three consumer WAN technologies and home networks.

### a. Look at the two home networks.

What are the WAN technologies in use?
- Consumer WAN Technologies: Cellular Network, Home DSL Network, Home Cable Network.  

### b.     Examine the connections used in the network topology by selecting the Connections icon (the orange lightning bolt) in the PT devices menu. Hover over the media icons to display their names in the white box at the bottom of the PT window.

What media is used to connect the two home networks to the ISP? What devices in the home networks are directly connected to the ISP?
- From ISP to DSL Modem: phone cable.
- From ISP to Coaxial Splitter: coaxial cable.
- From ISP to CellTower0: coaxial cable.
### c.     Click the DSL modem and open the Physical tab.

What ports are available on the device and what is connected to them?
- Line 0 (ISP-DSL Modem) and Fast ethernet 0 (DSL Modem - Wireless Router2)
![WAN](/Images/WANconcepts-1.png)

What is the purpose of the DSL modem?
- A DSL modem essentially converts the signal from the telephone network (analog) into a format usable by your home network (digital). It acts as a translator between these two worlds.

What is the type of connection between the ISP/Telco/Cable Company network and the Home Cable Network? Why is the splitter necessary?
- The type of connection between the ISP/Cable Company network and the Home Cable Network is a coaxial cable. This cable is the same type used for delivering cable TV signals.The splitter is necessary because a single coaxial cable carries both the internet data signal and the cable TV signal. This prevents interference and ensures smooth operation of both services.
Note: A TV signal is a complex electronic signal that carries the information needed to display a picture and sound on your television.

### d.     Look at the ports on the cable modem.

Questions:
What does the cable modem do? What connections does it have?
- The cable modem takes the high-speed data signal from the cable company delivered through a coaxial cable and converts that signal into a digital format your home network devices can understand (like computers, phones). It has coaxial and fast ethernet 0 connections

![WAN](/Images/WANconcepts-2.png)

Which port does the cable from the cable modem connect to on the home wireless router? Where did the interface IP address come from?
- The internet port - Blue one in the picture!
- It comes from the ISP.
  
![WAN](/Images/WANconcepts-3.png)

### e.     Look at the Smartphone.

What is its IP address? Where did the IP address come from?
- 198.51.100.100
![WAN](/Images/WANconcepts-4.png)
- ISP
  
What data service is the cellphone currently using (cellular data or Wi-Fi)?
- Cellular

## Step 2: Explore the Business WAN
In this step you will explore the business WAN. The business is a retail tire store. It has a local headquarters where most of the business functions occur, and three stores that are connected to the business WAN.

### a.     Look at the Connections menu.
What different types of connections do you see in use in the Business network?
- From ISP to Bussiness Headquarters Router (Serial).
- From StoreNet to others Store Switch (Serial).
- The others are used copper cables.

### b.     Open the physical view for the StoreNet switch.
What types of interfaces are present?

![WAN](/Images/WANconcepts-5.png)

Which interfaces and media are used to connect the store networks to the Business Headquarters network? Why was this done?
- Copper cable.
- I think because it is close to each other! 

What type of WAN service is used to connect the Business Headquarters router to the ISP?
- Business WAN and Serial cable

# Part 2: Explore Connectivity
Questions:
Ping devices within the Business WAN and the Consumer WAN networks. Also ping between the networks and the between the networks and the web server. Can all hosts ping each other and the web server?
- Store 1-1, Store 2-1, Laptop 2 could ping the Web Server
![WAN](/Images/WANconcepts-6.png)
![WAN](/Images/WANconcepts-7.png)
![WAN](/Images/WANconcepts-8.png)

- IP address of PC Store 1-1 is 192.168.10.4. Laptop 2 could not ping PC Store 1-1.
![WAN](/Images/WANconcepts-9.png)

- Similar to the above situation, Laptop 2 could not ping PC Store 2-2.
![WAN](/Images/WANconcepts-10.png)

Is this a good situation? Yes, It is good for security reasons. The business network must not be reached from other normal home networks. 
