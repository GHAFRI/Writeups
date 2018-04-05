# [Forgotten](https://shellterlabs.com/en/questions/carnaval-hacking-2017/crnvl-forgotten/)

```
Dev people are always forgetting things. 
Let's take advantage on that and find the creds.
```

## Solution

The `source code` has nothing of intrest so we tried some `SQL Injection`. 
After few fails, we attempted a `directory search` using [dirsearch](https://github.com/maurosoria/dirsearch).
With a full scan, we found only one intresting directory `/checklogin.php`. 
If we insert that into the URL we get nothing. If we look back at the question `Dev people are always forgetting things` we tried using `/checklogin.php.bkp`
and we got
```
<?php
   session_start();
   
   if($_SERVER["REQUEST_METHOD"] == "POST") {
      // username and password sent from form 
      
      $username = $_POST['username'];
      $password = $_POST['password']; 
      
      // If result matched $myusername and $mypassword, table row must be 1 row
			if($username == "dogbert" && $password == "shellter{n3v3r_f0r637_70_r3v13w_7h3_f1l35_0f_y0ur_pr0j3c7}"){
         $_SESSION['login_user'] = $username;
         header("location:welcome.php");
      }else {
         echo "Your Login Name or Password is invalid";
      }
   }

?>
```
The flag is `shellter{n3v3r_f0r637_70_r3v13w_7h3_f1l35_0f_y0ur_pr0j3c7}`
