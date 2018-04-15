# NSA Math Test - 300
```
Public key crypto is built on the inability to factor large relative primes quickly. Given a relative prime N, find the two prime numbers whose product is N. Submit solutions as a space-separated pair, for example:
9001 9187
The service is at services.opcde-ctf.propervilla.in on port 10010/tcp.
Flag is in format: flag{...}
Hint: Try first connecting manually to the service, e.g:
$ nc -v services.opcde-ctf.propervilla.in 10010
```
We connect to the server we get
```Lunix
DNS fwd/rev mismatch: services.opcde-ctf.propervilla.in != ec2-52-57-139-149.eu-central-1.compute.amazonaws.com
services.opcde-ctf.propervilla.in [52.57.139.149] 10010 (?) open
Welcome to NSA Math Test!  Generating relative primes.
Which two primes give you the product: 64706487147923
```

## Solution

Just like the question asked we need to find `two prime numbers whose product is N` which is given to us from the server.

```Python
# Importing Libraries
from pwn import *
import numpy as np
import math

# Function to compare factors with their product
def factors(number):
	return [[x, number / x] for x in range(int(math.sqrt(number)))[2:] if not number %x]

# connect to netcat server
r = remote('services.opcde-ctf.propervilla.in', 10010)
# Retrieve data from the server
data = []
arr = []
#while r.can_recv():
data = r.recvline("\n")
data = r.recvuntil("\n").split("\n")
print data
print len(data)

str2 = data[0]
arr2 = str2.split(": ")
total = arr2[1]
print total
man = int(total)
animal = factors(man)
print animal
str1 = str(animal[0])
arr1 = str1.split(",")
print arr1
str2 = arr1[0]
arr2 = str2.split("[")
one = arr2[1]
print one
str3 = arr1[1]
arr3 = str3.split("]")
t =  arr3[0]
t = t.split(" ")
t = t[1]
two = t
print two

one = str(one)
two = str(two)

# Send data to the server
r.send(one + " " + two )

# Loop the requests
while True:
	data = r.recvuntil("\n").split("\n")
	print data
	print len(data)
	str2 = data[0]
	arr2 = str2.split(": ")
	total = arr2[1]
	print total
	man = int(total)
	animal = factors(man)
	print animal
	str1 = str(animal[0])
	arr1 = str1.split(",")
	print arr1
	str2 = arr1[0]
	arr2 = str2.split("[")
	one = arr2[1]
	print one
	str3 = arr1[1]
	arr3 = str3.split("]")
	t =  arr3[0]
	t = t.split(" ")
	t = t[1]
	two = t
	print two

	one = str(one)
	two = str(two)

	r.send(one + " " + two )
# To output the flag  
r.interactive
```

### What I learned

- [x] More into pwntools.

