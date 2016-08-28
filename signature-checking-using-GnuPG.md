# Checking GPG signature


GnumPG(GNUM Privacy Guard) is an Open Source alternative to the well-knnown Pretty Good Privacy(PGP) by Phil Zimmermann. See http://www.gnupg.org/ for more information about GnuPG.


##

To verify the signature for a specific package, you first need to obtain a copy of the package's public GPG key. You can

* Download from https://gpg.mit.edu/ with the public key name via web browser, e.g., Google Chrome/Firefox, then store it in some file, e.g., package-public-key.asc
* Download from the public key using the public key id via command, e.g., gpg --recv-keys public-key-id, which also import the public key
* Cut and paste the public key directly from some text file, e.g., https://example.com/package-public-key.asc, then store it in some file, e.g., package-public-key.asc

To import the public key into your personal public GPG keyring, using `gpg --import`, e.g.,

    $ gpg --import package-public-key.asc

For RPM installation, you can also import the public key directly:

    $ rpm --import package-public-key.asc


##

After you have downloaded and imported the public key, download your desired package and the corresponding signature from the package's download page.
The signature file should have the same name as the package file with an .asc extension, e.g.,
```
package-version.tar.gz
package-version.tar.gz.asc
```

Make sure both files are stored in the same directory, and then run the following command to verify the signature for the package file:

    $ gpg --verify package-version.tar.gz.asc

If the downloaded package is valid, you will see a "Good signature", otherwise you may need download the package again, better with a different mirrow.
