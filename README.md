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
3. Samsung Dex / Samsung Phone integration with Windows 10 will be disabled. 
4. The Device Care app will be disabled and will not appear in settings. This includes Samsung's app sleeper and battery monitor. There is [evidence](https://www.virustotal.com/gui/file/048ead2be8d18bbe2b05651380069b3740dd05703e9bd66630da986026518398/details) the Device Care app created by the Chinese company [Qihoo 360](https://en.wikipedia.org/wiki/Qihoo_360) sends data to China domains over HTTP. If you want this functionality do not disable `com.samsung.android.lool`.
5. Do not disable `com.samsung.android.provider.filterprovider` or `com.samsung.android.app.smartcapture`. **Doing so will cause the stock Samsung camera app to crash**.

> ⚠️ Research each package before running the command to disable it. Some apps have hidden dependencies.

# Instructions
The following instructions assumes you are familiar with using a command-line interface.
1. (Recommended for stability) Backup, update, and factory reset your phone.
2. On your phone, enable Android's "Developer Options"
3. In "Developer Options", turn on "USB Debugging"
4. On your computer, download [Android SDK Platform-Tools](https://developer.android.com/studio/releases/platform-tools) for your OS.
5. Extract [Android SDK Platform-Tools](https://developer.android.com/studio/releases/platform-tools) and start a command-prompt/shell session in the extracted folder's directory.
6. Connect your Samsung Android phone to your computer with USB debugging enabled. Verify that adb sees your device and the daemon is running with the following command
    - `adb devices`
    - You should see the device name listed as a "device".
    - At this point your device should prompt you to accept USB debugging from your computer. Tap "Allow". 
    
    <img src="./img/adb_devices.PNG"/>

7. Enter your device's shell with the following command
    - `adb shell`
8. Once in the device's shell, copy and paste all desired commands from [commands.txt](./commands.txt) to remove the package.

9. To remove all apps in the list type the following command
    - Rename command.txt to command.sh
    - Push the file to sdcard by
        `adb push /path/to/command.sh /sdcard
    - Run the following command in adb shell
        `cd /sdcard/`
        `chmod +x command.sh`
        `/system/bin/sh command.sh`

# Other
Once in your device's shell, you can use the following command to list installed packages by name.
 - `pm list package | grep '<package name>'`

For example, to list all installed packages with Facebook in their name, you'd type,
 - `pm list package | grep 'facebook'`

### Sources
- https://www.xda-developers.com/disable-system-app-bloatware-android/
- https://forum.xda-developers.com/showpost.php?p=73894621&postcount=23
- Package Disabler Pro
