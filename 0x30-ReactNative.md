# ReactNative Issue List

##
[sane] Warning: Lost connection to watchman, reconnecting..
 ERROR  A non-recoverable condition has triggered.  Watchman needs your help!
The triggering condition was at timestamp=1465459414: inotify-add-watch(/home/michael/react/AwesomeProject/node_modules/react-native/ReactAndroid/src/androidTest/java/com/facebook/react) -> The user limit on the total number of inotify watches was reached; increase the fs.inotify.max_user_watches sysctl
All requests will continue to fail with this message until you resolve
the underlying problem.  You will find more information on fixing this at
https://facebook.github.io/watchman/docs/troubleshooting.html#poison-inotify-add-watch

{"watchmanResponse":{"version":"4.5.0","error":"A non-recoverable condition has triggered.  Watchman needs your help!\nThe triggering condition was at timestamp=1465459414: inotify-add-watch(/home/michael/react/AwesomeProject/node_modules/react-native/ReactAndroid/src/androidTest/java/com/facebook/react) -> The user limit on the total number of inotify watches was reached; increase the fs.inotify.max_user_watches sysctl\nAll requests will continue to fail with this message until you resolve\nthe underlying problem.  You will find more information on fixing this at\nhttps://facebook.github.io/watchman/docs/troubleshooting.html#poison-inotify-add-watch\n"}}
Error: A non-recoverable condition has triggered.  Watchman needs your help!
The triggering condition was at timestamp=1465459414: inotify-add-watch(/home/michael/react/AwesomeProject/node_modules/react-native/ReactAndroid/src/androidTest/java/com/facebook/react) -> The user limit on the total number of inotify watches was reached; increase the fs.inotify.max_user_watches sysctl
All requests will continue to fail with this message until you resolve
the underlying problem.  You will find more information on fixing this at
https://facebook.github.io/watchman/docs/troubleshooting.html#poison-inotify-add-watch

    at BunserBuf.<anonymous> (/home/michael/react/AwesomeProject/node_modules/react-native/node_modules/sane/node_modules/fb-watchman/index.js:95:23)
    at emitOne (events.js:77:13)
    at BunserBuf.emit (events.js:169:7)
    at BunserBuf.process (/home/michael/react/AwesomeProject/node_modules/react-native/node_modules/bser/index.js:289:10)
    at /home/michael/react/AwesomeProject/node_modules/react-native/node_modules/bser/index.js:244:12
    at nextTickCallbackWith0Args (node.js:420:9)
    at process._tickCallback (node.js:349:13)

See http://facebook.github.io/react-native/docs/troubleshooting.html
for common problems and solutions.

See [Increasing the amount of inotify watchers](https://github.com/guard/listen/wiki/Increasing-the-amount-of-inotify-watchers) for resolutions.

If you are running Debian, RedHat, or another similar Linux distribution, run the following in a terminal:

    $ echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p

If you are running ArchLinux, run the following command instead (see here for why):

    echo fs.inotify.max_user_watches=524288 | sudo tee /etc/sysctl.d/40-max-user-watches.conf && sudo sysctl --system

##

