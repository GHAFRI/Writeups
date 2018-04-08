# Dird - 300
```
Dirds are birds with dog heads. I don't think they have thumbs, though.
Flag is in format: flag{...}
```
## Solution

We were given a doge bird image to look for the flag. We tried looking through `binwalk`, `exif` and even `Stegsovl` for an hidden things with no clue. Then we looked into using online sites even though we don't work that way, but we thought maybe a site can show us more like `http://exif.regex.info`. So we hooked that up and we got

![1](https://github.com/GHAFRI/Writeups/edit/tree/Forensics/OPCDE-CTF-2018/Dird/1.png)

So, the flag is `flag{Tider Dirden}`

### What I learned

Check the thumbnails too.
