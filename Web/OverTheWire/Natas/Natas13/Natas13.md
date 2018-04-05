# [Natas 12](http://natas12.natas.labs.overthewire.org/)

![0](https://github.com/GHAFRI/Writeups/blob/master/Web/OverTheWire/Natas/Natas13/0.png)

## Solution

Need to Check [Natas12 Writeup](https://github.com/GHAFRI/Writeups/blob/master/Web/OverTheWire/Natas/Natas12/Natas12.md) for a followup.
Its the same type of `Exploit` but they want it to have the right `file signature`.
If we check `View source` we have:
```
$err=$_FILES['uploadedfile']['error']; 
    if($err){ 
        if($err === 2){ 
            echo "The uploaded file exceeds MAX_FILE_SIZE"; 
        } else{ 
            echo "Something went wrong :/"; 
        } 
    } else if(filesize($_FILES['uploadedfile']['tmp_name']) > 1000) { 
        echo "File is too big"; 
    } else if (! exif_imagetype($_FILES['uploadedfile']['tmp_name'])) { 
        echo "File is not an image"; 
```
Here they are checking the `file size` and making sure that the file is completely a `.jpg`.

To change the `file signature` we just import the same image we used for `Natas12` then we import it to [HxD](https://mh-nexus.de/en/hxd/) hex editor.

![1](https://github.com/GHAFRI/Writeups/blob/master/Web/OverTheWire/Natas/Natas13/1.png)

We see that the file has no file signature for a `.jpg` so to add one we copy our signature `FF D8 FF DB` and then go to `Edit -> Paste Insert` we end up with

![2](https://github.com/GHAFRI/Writeups/blob/master/Web/OverTheWire/Natas/Natas13/2.png)

Since we need the passcode for the next challange, we just change `Natas13` to `Natas14` too.

![3](https://github.com/GHAFRI/Writeups/blob/master/Web/OverTheWire/Natas/Natas13/3.png)

Now we save it and repeat the same uploading steps in `Natas12`, this time we get
```
����Lg96M10TdfaPyVBkJdjymbllQ5L6qdl1 
Lg96M10TdfaPyVBkJdjymbllQ5L6qdl1
```

So, the passcode is `Lg96M10TdfaPyVBkJdjymbllQ5L6qdl1`.


 		
