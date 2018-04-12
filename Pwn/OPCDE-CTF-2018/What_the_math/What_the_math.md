# What The Math? - 200
```
Given a sum N and an array of integers, find two entries in the array whose sum is N. Submit solutions as a space-separated pair, for example:
7638 49278
The service is at services.opcde-ctf.propervilla.in on port 10011/tcp.

Flag is in format: flag{...}

Hint: Try first connecting manually to the service, e.g:

$ nc -v services.opcde-ctf.propervilla.in 10011
```
If we run it on the server we get
```Lunix
nc -v services.opcde-ctf.propervilla.in 10011
DNS fwd/rev mismatch: services.opcde-ctf.propervilla.in != ec2-52-57-139-149.eu-central-1.compute.amazonaws.com
services.opcde-ctf.propervilla.in [52.57.139.149] 10011 (?) open
What The Math?!  Generating sums.
Sum: 3501437660
Array: [874374497, 1177141672, 2734670124, 3321106123, 3148907970, 1207766601, 2168731613, 3235563495, 3677087619, 362458009, 557642715, 3668637605, 970134770, 196404589, 3970550850, 135790669, 2339209263, 2967191303, 1225017450, 2919315105, 4215398585, 60091764, 377123456, 70297931, 1861267997, 807939626, 2211629714, 2809459926, 3831405279, 4218981033, 360650129, 4078517047, 2195160123, 2546556525, 944371513, 108347537, 2528363986, 3426035847, 2579055383, 1637436806, 4265224326, 1080672472, 1663514078, 4011189970, 127178734, 247850352, 3597387598, 240404665, 1233932138, 3318786289, 3661830776, 747062322, 198783222, 418739991, 2465188197, 2263981307, 3693309011, 1424678299, 3477581488, 1921942237, 1661203517, 4277070380, 1640430955, 2130830647, 2778187786, 3431139729]
```

## Solution


The solution we used is
```Python
# Importing Libraries
from pwn import *
import numpy as np

# Connecting to the Server
r = remote('services.opcde-ctf.propervilla.in', 10011)

# Get data from the server
data = []
arr = []
data = r.recvuntil("]").split("\n")
print data
print len(data)
str2 = data[1]
arr2 = str2.split(" ")
total = arr2[1]
print total
str3 = data[2]
arr = str3.split("]")
arr.pop()
str3 = arr[0]
arr = str3.split("[")
str3 = arr[1]
val = str3.split(",")
print val
print len(val)
s = set()
# Function to Compare
for i in range(0,len(val)):
	temp = int(total)-int(val[i])
	if (temp>=0 and temp in s):
   		shit = val[i]
    		shitt = temp
	s.add(int(val[i]))

newshit = shit.split(" ")
shit = newshit[1]
print shit
print shitt
print(type(shit))
print(type(shitt))
ass = str(shitt)

# Send back to the server
r.send(shit + " " + ass )
r.recv()

#Looping the pwn
while True:
	data = r.recvuntil("]").split("\n")
	print data
	print len(data)
	str2 = data[0]
	arr2 = str2.split(" ")
	total = arr2[1]
	print total
	str3 = data[1]
	arr = str3.split("]")
	arr.pop()
	str3 = arr[0]
	arr = str3.split("[")
	str3 = arr[1]
	val = str3.split(",")

	print val
	print len(val)
	s = set()
	for i in range(0,len(val)):
		temp = int(total)-int(val[i])
		if (temp>=0 and temp in s):
	   		shit = val[i]
	    		shitt = temp
		s.add(int(val[i]))
	
	newshit = shit.split(" ")
	shit = newshit[1]
	print shit
	print shitt
	print(type(shit))
	print(type(shitt))
	ass = str(shitt)

	r.send(shit + " " + ass )
	r.recvline()
r.interactive()
```

### What I learned
Nothing
