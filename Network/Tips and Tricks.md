# Here is the list of tips I used for networking:
## TTH Hashsum File
If you `binwalk` pcap file you might come across a file that looks like this:
```xml
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<FileListing Version="1" CID="AH3KWVYA5DAWJA7HAVHXC6BCLPNG34PVQVMPXPY" Base="/" Generator="EiskaltDC++ 2.2.9">
<Directory Name="dcpp">
	<File Name="text" Size="9" TTH="CA4CMF34SHRUQIBG6MNRDAI5BVT7HQQRTGC7TBA"/>
</Directory>
</FileListing>
```
This means that the flag is in a `flag.txt` file that has a `TTH hashsum` that is `9` bytes.  
To solve this we use a `bruteforcer.py` script that uses the OS library to excute shell of [rhash](https://github.com/rhash/RHash) and uses a python library [brute](https://github.com/rdegges/brute) (its python2):  
```py
import os
from brute import brute

flag = "CA4CMF34SHRUQIBG6MNRDAI5BVT7HQQRTGC7TBA".lower()
print("[+] Brute Forcing TTH Hash")
for b in brute(length=4, letters=True, numbers=True, symbols=False):
	p = os.popen('printf "CTF{'+b+'}\n" | rhash --tth -')
	s = p.read()
	s = s[:s.find(" ")]
	if s == flag:
		print("[+] FLAG FOUND")
		print("Flag is: "+b)
		break
```
Notice: This will take few seconds for 2 bytes, minutes for 3 bytes and maybe hours for 4 bytes.

## Kindle SP01
If you spot a header in a pcap file under the word `SP01` that means you need to use [This](https://github.com/NiLuJe/KindleTool):
```
kindletool dm file.pcap out
```
Then we just `binwalk` it to find what we need.

## SSL:

If an SSL `key` file exists in the `pcap` file, add it to the `Edit->Preferences->Protocols->SSL` key list and specify a certain `IP`, `port` and `protocol` to decrypt the SSL.
