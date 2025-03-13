## ARP Flood Attack Analysis

The Wireshark capture involves a **high volume of ARP requests** within the network. The packets repeatedly query the same IP addresses, indicating a possible **ARP flood attack**.

### Observations:
- The attack starts around **packet 79** and continues throughout the capture.
- The excessive **broadcast traffic** can lead to **network congestion** and **performance degradation**.
- The frequent ARP requests may suggest an attempt to **overwhelm the network**, potentially leading to **network downtime**.

### Potential Impact:
If this is part of an **ARP poisoning attack**, the attacker could:
- **Intercept sensitive traffic**
- **Perform Man-in-the-Middle (MITM) attacks**
- **Manipulate network traffic for malicious purposes**

### Mitigation Strategies:
To counteract this threat, security measures such as **Dynamic ARP Inspection (DAI)**, **static ARP entries**, and **intrusion detection systems (IDS)** should be implemented to prevent unauthorized ARP traffic.
