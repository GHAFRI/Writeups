# Memes
```
The owner of this website is addicted to memes, he decided to create a system to view the memes, but I think it did not work ... (watch out for the trolls)
```
## Solution

The site has a picture and music playing in the background.
If we check `/robots.txt` we get 
```
User-agent: *
Disallow: /memesviewer/
Disallow: /tafacil.txt
```

Now, when we check `/memesviewer/tafacil.txt` we get an error page, but if we check onle `/memesviewer` we get the `index` page.
Inside `flag.txt` we have the flag `shellter{3u_s0u_muit0_r4p1d0}`

