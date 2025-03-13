## URG-PSH-FIN Flood Attack Analysis

The Wireshark capture is an **URG-PSH-FIN flood attack**, a type of **Denial-of-Service (DoS) attack** where an attacker sends a high volume of **TCP packets** with unusual flag combinations (**URG, PSH, and FIN**).

### Observations:
- The attack is observed in packets **210-293**.
- The affected server **responds with RST+ACK packets**, indicating an attempt to reset the connections.
- The attacker **continuously switches source ports**, making it difficult to filter out the attack effectively.

### Potential Impact:
This attack pattern, observed throughout the capture, suggests an attempt to:
- **Exhaust the server’s resources**
- **Disrupt legitimate traffic**
- **Bypass security mechanisms**

The persistent nature of the attack requires immediate mitigation strategies, such as **intrusion prevention systems (IPS)**, **rate limiting**, and **firewall rules** to minimize the impact.

### Mitigation Strategies:
We should deploy an Intrusion Prevention System (IPS) capable of identifying and blocking abnormal TCP flag combinations, thus mitigating resource exhaustion. Moreover, configuring firewall-based rate limiting and enabling TCP SYN cookies further protects against DoS attacks by ensuring only legitimate connection requests consume server resources.
