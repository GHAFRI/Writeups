# Under Pressure - 100
```
I have been asked to explain the difference between encoding and compression in a job interview. 
I guess people confuse the two?

Flag is in format: flag{...}
```

## Solution

As simple as this problem is, we are given a `Txt` file with a `Base64` text
```
TmljZSB3b3JrIGRlY29kaW5nIHRoaXMuIFRoaW5ncyBzdGlsbCBmZWVsIGEgbGl0dGxlIGNvbXByZXNzZWQuCh+LCAi3Dt1YAANjb21wcmVzc2VkAEvLSUyvds7PLSgyLi7ONMiLT8xziXfNSzZIycxzj08MSo1PyXRzMy4yziuJL8nI9Es3reUCABG/Ca00AAAA
```
We convert it ASCII and we get
```
Nice work decoding this. Things still feel a little compressed.
XcompressedKILv-(2..4ȋOswK6HsOJOts3.2+/K7	4
```
It seems like a `file code`, so we take `decode` it again, but this time into a `.bin` file and we open it in to `HxD` we get
```
.‹..·.ÝX..compressed.KËIL¯vÎÏ-(2..Î4È‹OÌs‰wÍK6HÉÌs.O.J.OÉts3.2Î+‰/ÉÈôK7.å...¿..4...
```
`.<.` is a file signature for a `gzip` compression, so we change `.bin` to `.gz` and we open it.
We find a file and in that file we get the flag
```
Thanks for playing CTF.  
Capturing flags is fun!  Here is your flag:  flag{b33p_b00p_sh00p_da_wh00p}
```

### What I learned 

Never copy file formats from a decoder directly to a hex editor.
Let that decoder convert directly to a file for you so you dont lose important variables such as `<` which could correupt your files.
