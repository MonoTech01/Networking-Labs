# Topology and Addressing table
![CiscoIOS](/Images/CiscoIOSImage-pic0.png)
![CiscoIOS](/Images/CiscoIOSImage-pic1.png)

# Objectives
Part 1: Upgrade an IOS Image on a Cisco Device

Part 2: Backup an IOS Image on a TFTP Server

# Scenario
A TFTP server can help manage the storage of IOS images and revisions to IOS images. For any network, it is good practice to keep a backup copy of the Cisco IOS Software image in case the system image in the router becomes corrupted or accidentally erased. A TFTP server can also be used to store new upgrades to the IOS and then deployed throughout the network where it is needed. In this activity, you will upgrade the IOS images on Cisco devices by using a TFTP server. You will also backup an IOS image with the use of a TFTP server.

# Instructions
## Part 1: Upgrade an IOS Image on a Cisco Device

Step 1: Upgrade an IOS image on a router.

a+b.     Access the TFTP server and enable the TFTP service; Note the IOS image files that are available on the TFTP server.

Open configuration window

c.     From R2, issue the show flash: command and record the available flash memory.

d.     Copy the CISCO1941/K9 IOS version 15.5 image for the 1941 router from the TFTP Server to R2.

Note: In an actual network, if there is more than one interface active on the router, you may need to enter the ip tftp source interface command to specify which interface should be used to contact the TFTP server. This command is not supported in PT 7.2 and older versions and is not necessary to complete this activity.

e.     Verify that the IOS image has been copied to flash.

Question:
How many IOS images are located in flash? 2

f+g,      Use the boot system command to load the version 15.5 IPBase image on the next reload; Save the configuration and reload R2.

R2(config)# boot system flash c1900-universalk9-mz.SPA.155-3.M4a.bin

h.     Use the show version command to verify the upgraded IOS image is loaded after R2 reboots.

R2# show version

Cisco IOS Software, C1900 Software (C1900-UNIVERSALK9-M), Version 15.5(3)M4a, RELEASE SOFTWARE (fc1)

Technical Support: http://www.cisco.com/techsupport

Copyright (c) 1986-2016 by Cisco Systems, Inc.

Compiled Thu 06-Oct-16 13:56 by mnguyen

 

ROM: System Bootstrap, Version 15.0(1r)M9, RELEASE SOFTWARE (fc1)

 

R2 uptime is 21 seconds

System returned to ROM by power-on

System image file is "flash0:c1900-universalk9-mz.SPA.155-3.M4a.bin"

---- output omitted -----

Close configuration window

Step 2: Upgrade an IOS image on a switch.
Open configuration window

a.     Access the TFTP server and copy the c2960-lanbasek9-mz.150-2.SE4.bin image to S1.

S1# copy tftp: flash:

b.     Use the boot system command to configure the switch to load the new IOS image on boot.

c.     Reload S1 and verify the new image has been loaded into memory.

d.     Close the TFTP configuration window if it is still open.

Close configuration window

Part 2: Backup an IOS Image to a TFTP Server
Open configuration window

a.     On R1, display the contents of flash and record the IOS image.

b.     Use the copy command to back up the IOS image in flash memory on R1 to a TFTP server. Note: The isr4300 image is considerably larger than the c1900 image. It will take longer to transmit it to the TFTP server.

- Check the recent version of R1
  
- Copy
  

c.     Access the TFTP server and verify that the IOS image has been copied to the TFTP server.

Note: You may have to start and stop the TFTP service on the server so the file appears in the file listing.
