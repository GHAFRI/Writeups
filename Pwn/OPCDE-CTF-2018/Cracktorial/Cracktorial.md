# Cracktorial - 400
```
The Cracktorial service generates a random number of factorials with a base between 100,000 and 500,000. Send back the base for each factorial.
Example: 4! = 24. You would receive 24, then send back the base of 4.
The service is at services.opcde-ctf.propervilla.in on port 10000/tcp.
Flag is in format: flag{...}

Hint: Try first connecting manually to the service, e.g:

$ nc -v services.opcde-ctf.propervilla.in 10000
```
## Solution

When we connect to netcat we get
```
DNS fwd/rev mismatch: services.opcde-ctf.propervilla.in != ec2-52-57-139-149.eu-central-1.compute.amazonaws.com
services.opcde-ctf.propervilla.in [52.57.139.149] 10000 (webmin) open
```
After almost 1 min, we get a huge list of values = 2 MB in size.
To solve this algorithm we created a function that takes in the large factorial, and then finds the base of it.
We also used `PwnTools` for this problem to `send` and `recieve` the information from the server.
The problem was that every time we `send` the `base` and recieve the next `factorial` my terminal runs out of memory.

### What I learned

You can utlize other languages like `C` to create faster algorithms to solve the problem.
