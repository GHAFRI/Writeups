# Easy Message

[Easy Message](http://ec2-35-164-4-176.us-west-2.compute.amazonaws.com/easymessage/)

So we begin by checking `easymessage/robots.txt` if it exits and it shows this
```
User-agent: *
Disallow: /?source
```

So we check `easymessage/?source` and we get
```
<?php

$user = $_POST['user'];
$pass = $_POST['pass'];

include('db.php');

if ($user == base64_decode('Q3liZXItVGFsZW50') && $pass == base64_decode('Q3liZXItVGFsZW50')
    {
        success_login();
    }
    else {
        failed_login();
}

?>
```

After we decode `Q3liZXItVGFsZW50` to `Cyber-Talent` we login and get
```
I Have a Message For You


..-. .-.. .- --. -.--. .. -....- -.- -. ----- .-- -....- -.-- ----- ..- -....- .- .-. ...-- -....- -- ----- .-. ... ...-- -.--.-
```

Its morse code, so we decode that too and we get the flag

`FLAG<KN>I-KN0W-Y0U-AR3-M0RS3)`




