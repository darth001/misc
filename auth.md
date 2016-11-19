#


##

https://blog.risingstack.com/web-authentication-methods-explained/

https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)
https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)


If you have to support a web application only, either cookies or tokens are fine - for cookies think about XSRF, for jwt take care of XSS.
If you have to support both a web application and a mobile client, go with an API that supports token-based authentication.
If you are building APIs that communicate with each other, go with request signing.


##
