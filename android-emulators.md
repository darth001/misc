# AVD 

## launching emulator manually failed

Problem:

[michael@localhost ~]$ emulator -list-avds
Nexus_5X_API_23
[michael@localhost ~]$ emulator -avd Nexus_5X_API_23
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct null not valid
Aborted (core dumped)

Solvtion:

???


## launching emulator via Android Studio succeded

/home/michael/Android/Sdk/tools/emulator -netdelay none -netspeed full -avd Nexus_5X_API_22
Creating filesystem with parameters:
    Size: 69206016
    Block size: 4096
    Blocks per group: 32768
    Inodes per group: 4224
    Inode size: 256
    Journal blocks: 1024
    Label: 
    Blocks: 16896
    Block groups: 1
    Reserved block group size: 7
Created filesystem with 11/4224 inodes and 1302/16896 blocks
console on port 5554, ADB on port 5555
Your emulator is out of date, please update by launching Android Studio:
 - Start Android Studio
 - Select menu "Tools > Android > SDK Manager"
 - Click "SDK Tools" tab
 - Check "Android SDK Tools" checkbox
 - Click "OK"

07/21 09:43:52: Launching app
$ adb push /home/michael/AndroidStudioProjects/EasyManager/app/build/outputs/apk/app-debug.apk /data/local/tmp/com.easymanager.easymanager
$ adb shell pm install -r "/data/local/tmp/com.easymanager.easymanager"
	pkg: /data/local/tmp/com.easymanager.easymanager
Success


$ adb shell am start -n "com.easymanager.easymanager/com.easymanager.easymanager.MainActivity" -a android.intent.action.MAIN -c android.intent.category.LAUNCHER
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]
Connected to process 3090 on device Nexus_5X_API_22 [emulator-5554]

