# Adobe Flash Player Plugin

https://get.adobe.com/flashplayer/

Browse to the above official download page, select plugin version to download, e.g., YUM for Linux, then download and install the rpm package,

    $ sudo rpm -ivh adobe-release-x86_64-1.0-1.noarch.rpm

After installing the repo package, we can now install the flash player plugin now,

    $ sudo dnf install flash-plugin

Now that we've installed Adobe Flash Player, the plugin should be added to Firefox plugins directory,

    $ ln -s /usr/lib64/flash-plugin/libflashplayer.so ~/.mozilla/plugins/libflashplayer.so

Refer flash-plugin's readme.ext for more details.

OK, done.
