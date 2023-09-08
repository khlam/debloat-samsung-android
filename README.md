# Debloat Samsung Android Phones with Android Debug Bridge (ADB)

This repository contains a list of [Android Debug Bridge (ADB)](https://developer.android.com/studio/command-line/adb) commands to aggressively disable apps/bloatware from Samsung Android devices that don't normally display an option to remove them.

Running all commands listed in [debloat.txt](./debloat.txt) will disable almost all Samsung apps.
This includes the Galaxy App Store, Samsung Themes, Samsung Dex, Samsung Bixby, Facebook, and more.
The end result will be a minimalist Samsung phone.
These commands SHOULD NOT disrupt Google Play Store. (if so, just revert with [revert_debloat.txt](./revert_debloat.txt))
Use at your own risk and read over all commands to make sure you don't take out something you need.
While these commands cannot harm your device, there may be situations where:
 a. Something important stops working, try [revert_debloat.txt](./revert_debloat.txt) to re-add all the removed packages
 a. Your phone gets into a crash-loop and the easiest fix is to boot the device into "Recovery Mode" and perform a factory reset research the procedure to boot into recovery mode for your Samsung phone, it can differ between models

## ⚠️ WARNING:⚠️
After running these commands, you will no longer be able to: 
1. install Profile Isolation (Work Profile) apps such as [Island](https://play.google.com/store/apps/details?id=com.oasisfeng.island&hl=en_US) or [Shelter](https://play.google.com/store/apps/details?id=net.typeblog.shelter&hl=en_US). **Installing Profile Isolation apps after running these commands will put OneUI into a crash-loop.**
2. Use anything that needs Galaxy Store to work.
3. Use Samsung Dex/Samsung Phone integration with Windows 10.
4. There is a list of apps that are known to cause issues [do_not_remove.txt](./do_not_remove.txt) DO NOT remove them.

> ⚠️ Research each package before running the command to disable it. Some apps have hidden dependencies.

## Instructions (to debloat, and to revert debloat)
The following instructions assumes you are familiar with using a command-line interface.
Further reading on ADB can be found here: https://developer.android.com/studio/command-line/adb#Enabling.

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

8. Once in the device's shell: 

9. a. copy and paste all desired packages to remove from [debloat.txt](./debloat.txt)
 
If anything goes south, revert all changes running:
 
9. b. copy and paste all desired packages to re-add from [revert_debloat.txt](./revert_debloat.txt)

 

## Contributing:
There is alist of apps that are known to cause issues, those will not be added to the list and can be found at [do_not_remove.txt](./do_not_remove.txt)

Once in your device's shell, you can use the following command to list installed packages by name.
 - `pm list package | grep '<package name>'`

For example, to list all installed packages with Facebook in their name, you'd type,
 - `pm list package | grep 'facebook'`

If there is any package missing from the removal list, feel free to open a issue or creating a PR

## Sources

- forked from: https://github.com/khlam/debloat-samsung-android
- https://developer.android.com/studio/command-line/adb
- https://www.xda-developers.com/disable-system-app-bloatware-android/
- https://forum.xda-developers.com/showpost.php?p=73894621&postcount=23
- Package Disabler Pro
