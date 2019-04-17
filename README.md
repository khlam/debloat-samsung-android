# Debloat Samsung Android via ADB

This repository contains a list of adb commands to remove bloatware from Samsung Android devices.

The effect of running these adb commands is roughly equilivent to what [Package Disabler Pro+ (Play Store Link)](https://play.google.com/store/apps/details?id=com.elmklmsamsung.batteryaddon&hl=en_US) does, except you're running commands manually so you don't need to give an app device admin permission.

Running all commands listed in [commands.txt](./commands.txt) will **uninstall** all Samsung services, Facebook services, Google apps, Bixby, and most pre-installed bloatware.
These commands will not disrupt Samsung Knox. These commands will **remove** the Galaxy Store (everything including themes) and Samsung Pay.

> IMPORTANT: Research each package before deleting it. Some apps have hidden dependencies.

Ex. removing `com.samsung.android.provider.filterprovider` will cause the stock Samsung camera app to crash. I've tested my list [commands.txt](./commands.txt) and I haven't noticed any issues.

### How?
The following instructions assumes you are familiar with using a command-line interface.
1. Enable Android "Developer Options"
2. Turn on "USB Debugging"
3. Download [Android SDK Platform-Tools](https://developer.android.com/studio/releases/platform-tools) for your OS.
4. Extract [Android SDK Platform-Tools](https://developer.android.com/studio/releases/platform-tools) and start a command-prompt/shell session in the extracted folder's directory.
5. Connect your Samsung Android phone to your computer with USB debugging enabled. Verify that adb sees your device and the daemon is running with the following command
    - `adb devices`
    - You should see the device name listed as a "device".
    
    
    <img src="./img/adb_devices.PNG"/>

6. Enter your device's shell with the following command
    - `adb shell`
7. Once in the device's shell, copy and paste all desired commands from [commands.txt](./commands.txt) to remove the package. 

### Sources
- https://forum.xda-developers.com/showpost.php?p=73894621&postcount=23
