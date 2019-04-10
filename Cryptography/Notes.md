# Tips and Tricks for cryptography:
## RSA CTF Tool (flag and pub key)
If a problem is given with the above, then your most likely gonna use [rsactftool](https://github.com/Ganapati/RsaCtfTool)  
We first obtain the RSA Private key from the provided `key.pub`  
There are 2 methods:
### #1
```sh
cd RsaCtfTool
python2.7 RsaCtfTool.py --publickey key.pub  --private
```
We store the RSA Private key in a `private.pem`
If the flag file is in `base64` we convert it to binary file using:
```sh
echo "base64_data" | base64 -d > flag
```
Find we decrypt the private key with the flag file to get the flag:
```sh
openssl rsautl -decrypt -inkey private.pem -in flag -out flag.txt
```
### #2
With a single line from `rsactftool`:  
```sh
cd RsaCtfTool
python2.7 RsaCtfTool.py --publickey key.pub --uncipherfile flag --verbose --private
```
Notice: Flag file should be in binary format.

## RSA CTF Tool (p= q= e= c=)
If a problem is given with the above, then your most likely gonna use [rsactftool](https://github.com/Ganapati/RsaCtfTool)
To activate:  
```sh
cd RsaCtfTool
virtualenv --python=/usr/bin/python2.7 .
source bin/activate
python2.7 RsaCtfTool.py
```

## OTP or Many Time Pad Attack
This method can be explained here: [Many Time Pad Attack](https://crypto.stackexchange.com/questions/59/taking-advantage-of-one-time-pad-key-reuse)  
There are few methods I used to solve this problem:
### #1
Use `cribdrag.py` to find the key using manual analysis.
### #2
Use `featherduster` with `multi_byte_xor` module.

## Messy Text:
if you come across messy text such as this  
`A7]^gF*(u(BkVO)1MV#U/oPWADf.4LBQ&)IE+j2TD.GLe2e4XS@q%-(3+b!&3+=g#AMcDXAMuMZ@:V/M2e4jY`  
use a good source software such as `cyberchef` to decode it, and the method to do so is using `Base85`  

## Useful python code:
### Extract only Upper case from a text file
```py
data = ''.join([c for c in data_file if c.isupper()])
```
### Read from a file and store as a string:  
```py
with open('bin.txt','r') as f:
	data = f.read()
```
### Replacing data in a string:
```py
data = data.replace("ZERO","0").replace("ONE","1")
```
