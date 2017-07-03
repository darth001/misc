# Android Open Source Project


[Android Open Source Project](https://source.android.com/index.html)
[The Android Source Code](https://source.android.com/source/index.html)

Downloading the Source: https://source.android.com/source/downloading.html
Repo Command Reference: https://source.android.com/source/using-repo.html

    $ mkdir ~/bin
    $ export PATH=~/bin:$PATH
    $ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    $ chmod a+x ~/bin/repo

    $ mkdir ~/AOSP
    $ cd ~/AOSP
    $ git config --global user.name "XYZ"
    $ git config --global user.email "XYZ@ABC.COM"
    $ repo init -u https://android.googlesource.com/platform/manifest -b android-6.0.1_r62 --depth=1
    $ repo sync -c


