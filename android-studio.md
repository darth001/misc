# Android Studio Issues

## No space left on device

Add following bash variable in studio.sh at the start of file:

    export _JAVA_OPTIONS="-Djava.io.tmpdir=/var/tmp"
