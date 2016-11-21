#


##

https://en.wikipedia.org/wiki/Transport_Layer_Security
http://www.akadia.com/services/ssh_test_certificate.html

[man](openssl, req, rsa, x509)


##

* Generate a private key

The first step is to create your RSA private key.

    $ openssl genrsa -des3 -out server.key.orig 2048

NOTE: pass phrase required.

* Generate a CSR(Certificate Signing Request)

Once the private key is generated a Certificate Signing Request can be generated.
The CSR is then used in one of two ways. Ideally, the CSR will be sent to a Certificate Authority, 
such as Verisign who will verify the identity of the requestor and issue a signed certificate. The
second option is to self-sign the CSR.

    $ openssl req -new -key server.key.orig -out server.csr

During the generation of the CSR, you will be prompted for several pieces of information.
These are the X.509 attributes of the certificate. One of the prompts will be for "Common Name(e.g., YOUR name)".
It is important that this field be filled in with the fully qualified domain name of the server to be protected by SSL.

* Remove PassPhrase from key

Apache will ask for the pass-phrase each time the web server is started. It is possible to remove the Triple-DES encryption from the key.

    $ openssl rsa -in server.key.org -out server.key

* Generate a Self-Signed Certificate

To generate a temporary certificate which is good for 365 days:

    $ openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt

* Install the private key and certificate

When Apache with mod_ssl is installed, it creates several directories in the Apache config directory.
The location of this directory will differ depending on how Apache was compiled.

    $ sudo cp server.crt /etc/apache2/
    $ sudo cp server.key /etc/apache2/

* Configure SSL-enabled virtual hosts

```
SSLEngine on
SSLCertificateFile /etc/apache2/server.crt
SSLCertificateKeyFile /etc/apache2/server.key
SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown
CustomLog logs/ssl_request.log "%t %h %{SSL_PROTOCOL}x %{SSK_CIPHER}x \"%r\" %b"
```

* Restart Apache

Restart Apache to take effect

    $ sudo service apache2 restart


##

One-shot command:

    $ openssl req -x509 -newkey rsa:2048 -days 365 -keyout server.key.orig -out server.crt
    $ openssl rsa -in server.key.orig -out server.key
    $ sudo cp server.key server.crt /etc/nginx/ssl/
