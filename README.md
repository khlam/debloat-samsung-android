# Debloat Samsung Android Phones
Tested and working on Galaxy S9.

### What?
This repository contains a list of adb commands to remove bloatware from Samsung Android devices.
It removes all Samsung-related apps, Facebook services, Google apps, etc.
You can still re-install any app you need.
I've only tested this on my personal Samsung Galaxy S9.

### How?
1. Enable Android "Developer Options"
2. Turn on "USB Debugging"
3. Download and start [ADB - XDA Forums](https://www.xda-developers.com/google-releases-separate-adb-and-fastboot-binary-downloads/) for your OS.
4. Connect your Samsung Android phone to your computer. Verify that adb sees your device and the daemon is running with the following command
    - `adb devices`
5. Enter shell with the following command
    - `adb shell`
6. Once in the device's shell, simply copy and paste all desired commands from [commands.txt](./commands.txt) to remove the package. I encourage researching each package to make sure you don't need it.

### Sources
- https://forum.xda-developers.com/showpost.php?p=73894621&postcount=23