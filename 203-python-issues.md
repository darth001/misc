#


##

SSL Warnings

urllib3 will issue several different warnings based on the level of certificate verification support.
These warnings indicate particular situations and can resolved in different ways.

* InsecureRequestWarning

    This happens when an request is made to an HTTPS URL without certificate verification enabled.
    Follow the [certificate verification](https://urllib3.readthedocs.io/en/latest/user-guide.html#ssl) guide to resolve this warning.

* InsecurePlatformWarning

    This happens on Python 2 platforms that have an outdated `ssl` module.
    These older `ssl` modules can cause some insecure requests to succeed where they should fail and secure requests to fail where they should succeed.
    Follow the [pyOpenSSL](https://urllib3.readthedocs.io/en/latest/user-guide.html#ssl-py2) guide to resolve this warning.

* SNIMissingWarning

    This happens on Python 2 versions older than 2.7.9. These older versions lack `SNI` support. This can cause servers to present a certificate that the client thinks is invalid.
    Follow the [pyOpenSSL](https://urllib3.readthedocs.io/en/latest/user-guide.html#ssl-py2) guide to resolve this warning.


##

Certificate verification

It is highly recommended to always use SSL certificate verification. __By default, urllib3 does not verify HTTPS requests.__

In order to enable verification you will need a set of root certificates. The easiest and most reliable method is to use the `certifi` package
which provides Mozilla's root certificate bundle:

    $ sudo pip install certifi

You can also install certifi along with urllib3 by using the `secure` extra:

    $ sudo pip install urllib3[secure]

Once you have certificates, you can create a __PoolManager__ that verifies certificates when making requests:

```
>>> import certifi
>>> import urllib3
>>> http = urllib3.PoolManager(cert_reqs='CERT_REQUIRED', ca_certs=certifi.where())
>>>
```

The __PoolManager__ will automatically handle certificate verification and will raise __SSLError__ if verification fails:

```
>>> http.request('GET', 'https://www.google.com')
(No exception)
>>> http.request('GET', 'https://expired.badssl.com')
urllib3.exceptions.SSLError ...
```

NOTE:
You can use OS-provided certificates if desired. Just specify the full path to the certificate bundle as the `ca_certs` argument instead of `certifi.where()`.
For example, most Linux systems store the certificates at `/etc/ssl/certs/ca-certificates.crt`. Other operating systems can be difficult.


##

Certificate verification in Python 2

Older versions of Python 2 are built with an `ssl` module that lacks `SNI support` and can lag behind security updates. For these reasons it's recommended to use `pyOpenSSL`.

If you install urllib3 with the `secure` extra, all required packages for certificate verification on Python 2 will be installed:

    $ sudo pip install urllib3[secure]

If you want to install the packages manually, you will need `pyOpenSSL`, `cryptography`, `idna`, and `certifi`.

NOTE:
If you are not using macOS or Windows, note that `cryptography` requires additional system packages to compile. See [building cryptography on Linux](https://cryptography.io/en/latest/installation/#building-cryptography-on-linux)
for the list of packages required.

Once installed, you can tell `urllib3` to use `pyOpenSSL` by using `urllib3.contrib.pyopenssl`:

```
>>> import urllib3.contrib.pyopenssl
>>> urllib3.contrib.pyopenssl.inject_into_urllib3()
```

Finally, you can create a `PoolManager` that verifies certificates when performing requests:

```
>>> import urllib3
>>> import certifi
>>> http = urllib3.PoolManager(cert_reqs='CERT_REQUIRED', ca_certs=certifi.where())
```

If you do not wish to use pyOpenSSL, you can simply omit the call to `urllib3.contrib.pyopenssl.inject_into_urllib3()`. urllib3 will fall back to the standard library `ssl` module. You may experience several warnings when doing this.
