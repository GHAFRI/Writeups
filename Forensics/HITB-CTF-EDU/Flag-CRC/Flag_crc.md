# Flag CRC - N/A
```
N/A 
However the hint was: CRC32
```
## Solution

We were given a zip file that is encrypted with a password. We first run
```
unzip -v flag.zip
```
to check for file information, and we recieve

![1](https://github.com/GHAFRI/Writeups/blob/master/Forensics/HITB-CTF-EDU/Flag-CRC/1.png)

We can see we have a `CRC32` in the given file. After googling CRC cracker, we obtain a `cracker.py` code to run to extract the hidden text from the `CRC32` format.

![2](https://github.com/GHAFRI/Writeups/blob/master/Forensics/HITB-CTF-EDU/Flag-CRC/2.png)

Ordering it based from flag0 to flag3 and we get `flag{easy_crc32_crack}`

### What I learned

You can extract data from CRC32 of a zip file.