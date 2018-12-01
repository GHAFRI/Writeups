# Flag CRC - N/A
```
N/A 
However the hint was: CRC32
```
[CTF File](https://github.com/GHAFRI/Writeups/blob/master/Forensics/HITB-CTF-EDU/Flag-CRC/flag_0cdc286d10e7ba95570b27e2ead3fc31.zip)
## Solution

We were given a zip file that is encrypted with a password. We first run
```
unzip -v flag.zip
```
to check for file information, and we recieve

![1](https://github.com/GHAFRI/Writeups/blob/master/Forensics/HITB-CTF-EDU/Flag-CRC/1.png)

We can see we have a `CRC32` in the given file. After googling CRC cracker, we obtain a `cracker.py` from [Zip CRC Cracker](https://github.com/kmyk/zip-crc-cracker) code to extract the hidden text from the `CRC32` format.

![2](https://github.com/GHAFRI/Writeups/blob/master/Forensics/HITB-CTF-EDU/Flag-CRC/2.png)

Ordering it based from flag0 to flag3 and we get `flag{easy_crc32_crack}`

### What I learned

You can extract data from CRC32 of a zip file.
