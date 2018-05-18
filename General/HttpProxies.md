## Http Proxies
1. Follow the instructions of installing and configuring ZAP.
2. Request is intercepted:
![](Img/webgoat_http_proxy.png)
3. Modify the request according to instructions:
![](Img/webgoat_http_proxy_after.png)
* N.B. make sure set message to POST properly:
  * `/WebGoat/HttpProxies/intercept-request?changeMe=Requests%20are%20tampered%20easily HTTP/1.1`
4. Pass the tempered request through using ‘Play’ button.
![](Img/webgoat_proxy_success.png)
