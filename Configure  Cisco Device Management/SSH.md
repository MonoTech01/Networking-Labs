## Tasks
Configure Router R1:
- Set domain name of "mono.com".
- Generate 2048-bit RSA key pair.
- Enable SSHv2 only.
- Create user "admin" with password "monohye" (privilege level 15).
- Secure vty lines 0-15 for SSH-only access.

## Performance

    R1
    
    (config) # ip domain-name mono.com
    
    (config) # username admin privilege 15 secret monohye
    
    (config) # crypto key generate rsa modulus 2048
    
    (config) # ip ssh version 2
    
    (config) # line vty 0 15
    (config-line)# transport input ssh
    (config-line)# login local

    Verify
    R2#ssh -l admin 192.168.10.1
    Password:

    R1#

    
    


