# Debloat Samsung Android via ADB

This repository contains a list of adb commands to aggressively remove bloatware from Samsung Android devices.


Running all commands listed in [commands.txt](./commands.txt) will disable almost all Samsung apps.
This includes the Galaxy App Store, Samsung Themes, Samsung Dex, Samsung Bixby, Facebook, and more.
The end result will be a minimalist Samsung phone.
These commands will not disrupt Samsung Knox or the Google Play Store.
Use at your own risk and read over all commands to make sure you don't take out something you need.
While these commands cannot harm your device, there may be situations where your phone gets into a loop and you must perform a factory reset.


Running these adb commands is equilivent to using [Package Disabler Pro+ (Play Store Link)](https://play.google.com/store/apps/details?id=com.elmklmsamsung.batteryaddon&hl=en_US), except you're running commands manually so you don't need to give an app device admin permission or pay anything.



# ⚠️ WARNING:⚠️
1. After running these commands, you will no longer be able to install Profile Isolation (Work Profile) apps such as [Island](https://play.google.com/store/apps/details?id=com.oasisfeng.island&hl=en_US) or [Shelter](https://play.google.com/store/apps/details?id=net.typeblog.shelter&hl=en_US). **Installing Profile Isolation apps after running these commands will put OneUI into a crash-loop.**
2. Anything to do with the Galaxy Store will not work.
3. The Device Care app will be disabled and will not appear in settings. This includes Samsung's app sleeper and battery monitor. There is [evidence](https://www.virustotal.com/gui/file/048ead2be8d18bbe2b05651380069b3740dd05703e9bd66630da986026518398/details) the Device Care app created by the Chinese company [Qihoo 360](https://en.wikipedia.org/wiki/Qihoo_360) sends data to China domains over HTTP. If you want this functionality, do not disable `com.samsung.android.lool`.
4. Do not disable `com.samsung.android.provider.filterprovider`. **Doing so will cause the stock Samsung camera app to crash**.

> ⚠️ Research each package before running the command to disable it. Some apps have hidden dependencies.

# Instructions
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
- Package Disabler Pro
