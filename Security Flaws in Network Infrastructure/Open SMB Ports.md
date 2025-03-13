 ## Open SMB Ports Vulnerability  
The **SMB service** is running on **open ports 139 and 445**, making it susceptible to **CVE-2017-0144 (EternalBlue)**. This vulnerability allows attackers to:
- **Execute arbitrary code remotely**.
- **Spread malware across the network**, including ransomware attacks like **WannaCry**.

## Mitigation Strategies for SMB Vulnerability  

To mitigate this vulnerability, the following security measures should be implemented:  

### 1. **Disable SMBv1 Completely**  
- SMBv1 is outdated and contains **multiple security vulnerabilities**.  
- Disabling SMBv1 eliminates exposure to known exploits like **EternalBlue (CVE-2017-0144)**.  

### 2. **Enforce SMBv3 with Encryption**  
- **SMBv3 encryption** protects against **eavesdropping and unauthorized data access**.  
- This ensures secure data transmission across the network.  

### 3. **Deploy Network Security Applications**  
- Implement a **Next-Generation Firewall (NGFW)** to inspect and detect malicious SMB traffic.  
- **Intrusion Detection/Prevention Systems (IDS/IPS)** can identify and block SMB-based attacks. 

### 4. **Proactive Threat Mitigation**  
- **Monitor SMB traffic** for abnormal patterns that indicate exploitation attempts.  
- **Apply strict access controls** to limit SMB access to only necessary systems.  
- **Regularly update security patches** to prevent newly discovered vulnerabilities.  

By implementing these measures, SMB-based attacks can be **immediately mitigated or stopped**, reducing the risk of system compromise.
