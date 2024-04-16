# The Lab Settings
![DNS](/Images/DNS3.png)
![DNS](/Images/DNS1.png)
![DNS](/Images/DNS2.png)

# Performance
## Assess the PC
![DNS](/Images/DNS5.png)

## Capture Ethernet0
![DNS](/Images/DNS6.png)

## Explore DNS Query Traffic
### Filter UDP port
![DNS](/Images/DNS7.png)

![DNS](/Images/DNS9.png)

![DNS](/Images/DNS10.png)

![DNS](/Images/DNS11.png)

![DNS](/Images/DNS12.png)

### What are the source and destination MAC addresses? Which network interfaces are these MAC
addresses associated with?

Destination 6c:03:09:3c:cc:30 
Source 00:50:56:99:35:ac
Ethernet 0

### What are the source and destination IP addresses? Which network interfaces are these IP addresses
associated with?

Source 192.168.1.10 (PC)
Destination 192.168.1.1 (Router)
Ethernet 0

### What are the source and destination ports? What is the default DNS port number?
source 55292
destination 53
default 53


## Explore DNS Response Traffic
![DNS](/Images/DNS8.png)

![DNS](/Images/DNS15.png)

![DNS](/Images/DNS13.png)

![DNS](/Images/DNS14.png)

### What are the source and destination MAC and IP addresses and port numbers? How do they compare to
the addresses in the DNS query packets?

Destination 192.168.1.10 (PC) - port 53
Source 192.168.1.1 (Router) - port 55292
The router acts as an intermediary. PC sends a DNS query to the router, which forwards it to a DNS server, receives the IP address in a response, and then relays this information back to PC.

### Can the DNS server do recursive queries?
Yes!

### Observe the CNAME and A records in the answers details. How do the results compare to nslookup results?
They are the same.

# Reflection Question
### From the Wireshark results, what else can you learn about the network when you remove the filter?
Without a filter, Wireshark shows me all network traffic, revealing other protocols in use, devices communicating, broadcast messages, etc.

### How can an attacker use Wireshark to compromise your network security?
An attacker could use Wireshark to sniff sensitive data (especially if it is not encrypted) and analyze your network for vulnerabilities.
