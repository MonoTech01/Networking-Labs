# Suspicious HTTP Requests to /login.php 

The Wireshark capture reveals multiple **HTTP POST** requests to `/login.php`, a sensitive endpoint that typically handles user authentication. These requests appear repeatedly in the following packets:  

- **9,779**, **9,828**, **9,873**, **9,938**, **10,003**, **10,053**, and **10,133**, among others.

### Observations:
- The server responses **only contain text/HTML**, which is unusual for a typical web session. Normally, a web session would include **images, CSS, and JavaScript**.
- The repetitive nature of the requests and responses suggests a **brute-force attack**, where an attacker is systematically trying various login credentials.

### Potential Impact:
If successful, this attack could result in:
- **Compromised accounts**
- **Data breaches**
- **System exploitation**

This pattern indicates malicious activity, warranting further investigation and possible mitigation steps to protect user authentication security.

### Mitigation Strategies:
We should implement a Web Application Firewall (WAF) to detect and block automated login attempts. Additionally, enforcing Multi-Factor Authentication (MFA) significantly reduces the risk of unauthorized access, even if credentials are compromised.
