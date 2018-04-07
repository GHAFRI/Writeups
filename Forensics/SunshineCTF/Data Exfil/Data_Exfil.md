# Data Exfil
```
We think a critical document has been stolen out of our network, luckily our next gen IDS managed to capture the traffic during the attack. 
Can you tell us what they took?
Author: Medic-
```
## Solution

We have a folder that contains a `pcap` file and some `.log` files.
If we check the pcap file we wont find anything intresting so we switch to one of the `log` files starting with `dns.log`.
We see that some `proto count` have IP `8.8.8.8` and some have IP of `54.175.216.124`.
Then when we look to the right, we see some `hex` code.
```
504b030414000000000030be774c973a10791e0000001e0000000a000000.cozybear.group
7365637265742e74787473756e7b7730775f495f646e735f7333335f7930.cozybear.group
755f316e5f683372337d504b0102140014000000000030be774c973a1079.cozybear.group
1e0000001e0000000a000000000000000100200000000000000073656372.cozybear.group
```
If we take that `hex` code to any hex editor we can see
```
PK........0¾wL—:.y............secret.txtsun{w0w_I_dns_s33_y0u_1n_h3r3}PK..........0¾wL—:.y.................. .......secr
```

So the flag is: sun{w0w_I_dns_s33_y0u_1n_h3r3}

