Part 1 - Initial setup
1. Configure the appropriate hostname on each router/switch.

       en
       config t
       host [name]

3. Configure the enable secret jeremysitlab on each router/switch. Use type 9 hashing if available; otherwise, use type 5.

        Router#config t
        Enter configuration commands, one per line.  End with CNTL/Z.
        Router(config)#host R1
        R1(config)#enable secret ?
          0      Specifies an UNENCRYPTED password will follow
          5      Specifies an ENCRYPTED secret will follow
          LINE   The UNENCRYPTED (cleartext) 'enable' secret
          level  Set exec level password
        R1(config)#enable secret 5 ?
          LINE  The ENCRYPTED 'enable' secret string
        R1(config)#enable secret 5 jeremyitlab



5. Configure the user account cisco with secret ccna on each router/switch. Use type 9 hashing if available; otherwise, use type 5.
6. Configure the console line to require login with a local user account. Set a 30-minute inactivity timeout. Enable synchronous logging.
