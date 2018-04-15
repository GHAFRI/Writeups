# b33ps - 300
```
Remember the good old days when the signal was in the sound? My first modem was 1200 baud, dialing into Bell systems. 
Kids these days don't know what they're missing.
Flag is in format: flag{...}
```

## Solution

As the question says, we needed to look into a `modem` that is `1200 baud` and decode it from there. The only library that does that is [Minimodem](http://www.whence.com/minimodem/). So we downloaded the library and used this command

```
Input: minimodem --rx -f b33ps.flac 1200
Output:
### CARRIER 1200 @ 1200.0 Hz ###
H4sIAAd6cFYAAwvJSMzLLlZIyy9SKMhJrMzMS1dwDnHTU1BwTiwoKS0C8dNyEtOLFTKBikrzFBUUPFKLUkG8yvzSIrCclQKYqk4yNi6ITzIwKIgvzgCRKYnx5SBGLQA4hOrLZAAAAA==
### NOCARRIER ndata=140 confidence=4.847 ampl=1.001 bps=1200.00 (rate perfect) ###
```
Its a Base64 code, so we decode it to a file. The file has a `signiture` of `.<.` so it's basically a `gzip` format. So we add `.gz` and we get
```
Thanks for playing CTF.  Capturing flags is fun!  Here is your flag:  flag{b33p_b00p_sh00p_da_wh00p}
```

So the flag is `flag{b33p_b00p_sh00p_da_wh00p}`

### What I learned

Kali has some really intresting libraries that I should look into, such minimodem that I never heard about before.
