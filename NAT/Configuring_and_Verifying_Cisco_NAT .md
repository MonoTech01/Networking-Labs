# Topology 
# Task 

Performing most of the configuration on R1 (the Internet-facing router). The Internet is stimulated as the 192.168.1.X network. 
The web server's IP is 192.168.1.100

1. Access R1. Verify the connection between R1 and the web server.
2. Access PC-10 and ping the web server. The ping attempts should fail (since routing 10.16.0.10 directly to the internet would be not accepted).
3. Configure NAT overload on R1 using either a pool of addresses (192.168.1.10-192.168.1.15) OR using the IP address assigned to R1's int 1/0
4. Attempt to ping an open an HTTP web page from PC-10. Both should be successful. Verify cached NAT translations on R1. 

# Performance 
