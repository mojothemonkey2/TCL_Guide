# Intro

My notes on changes I have made to my TCL TV (C645K UK model).

# How-To

## Generic Android

### Enable developer mode

### ADB
#### Connect with ADB
Full guide - https://www.xda-developers.com/install-adb-windows-macos-linux/

Quick guide.. \
You will need a separate computer for this. \
Download the adb client for your platform:
* [Windows](https://dl.google.com/android/repository/platform-tools-latest-windows.zip)
* Ubuntu: `sudo apt-get install android-sdk-platform-tools`

On the TV:
1. [Enable developer mode](#enable-developer-mode)
2. Developer Mode > Enable USB debugging
3. Find the TV's IP: Settings > Network..

From the computer command line: `adb connect <ip of TV>:5555` \
The TV should ask if you wish to allow the USB debugging connection. Choose "Allow".

You should now be connected to your TV. You can verify with: `adb devices` (should list your TV).

#### ADB Shell
Once connected with adb, from the computer command line: `adb shell` \
You should be presented with a prompt like: `BeyondTV4:/ $` \
From this, you will be able to run commands directly on your TV operating system.

## TCL Android



### TV Service menu
TV Settings > Picture > Advanced > Brightness > Contrast \
Enter one of:
* 1950 - General Service Menu (Design Menu)
* 9735 or 6428 - Subsection Factory Menu
* 9705 - Subsection Service Menu
* 6405 - subsection Hotel Menu
* 6425 - TV Running Time and quick access to reset (Reset All and Reset Shop)


# Performance Tweaks

## Generic Android
Disable HW Overlay
Max background tasks = 1

## Uninstall TCL bloat
There are many guides on removing pre-installed TCL apps that come with the TV. \
A lot of these are quite agressive, in trying to remove everything. \
But for me, I was happy to just remove a few of the most obvious apps. \ 
And you need to be careful that you don't remove any of the apps controlling the TV's basic functions, eg the remote.

From [ADB Shell](#adb-shell):
```
pm uninstall --user 0 com.tcl.guard                # security / optimizations. but it a lot of cpu in the background.
pm uninstall --user 0 com.tcl.browser              # tcl browser
pm uninstall --user 0 com.tcl.waterfall.overseas   # the "tcl channel"
pm uninstall --user 0 com.tcl.tv.tclhome_passive   # tcl smarthome
pm uninstall --user 0 com.tcl.dashboard            # tcl smarthome
```

If you later wish to re-install any of these appa, you can do so like: `pm install-existing com.tcl.guard`


# Software Updates
TCL do not seem to be running any updates over the internet, at least in my region (UK). \
Instead, they offer a support service, where you can download firmware updates, and apply these manually via USB stick.

Firmware files will always be .zip, but there are two distinct types:
* OTA - update in place, and keep existing apps.
* IMG - will wipe the device!

First determine your current firmware: \
Setting > Device preference > About > Product Information: Software: V8-R51MT02-LF1V392.021305

The 2nd part of the software id gives you the firmware type, ie platform + variant, eg:
* R51MT02 = Realtek RTD2851M + Android TV.
* R51MT05 = Realtek RTD2851M + Google TV.

You must stick with a firmware that uses the same platform, as this must match the hardware chipset of the TV. \
Different TXX variants can also be for different regions, etc. \

If you stick with the same firmware type, you can use an OTA update. \
If you want to switch to a different variant, eg R51MT02 > R51MT05 (Android TV > Google TV), you must use an IMG update. \
If you need to rollback to an earlier version, then use an IMG firmware for this. \
Note, rollback may require 2 steps to get back to where you were, eg:
1. Flash V344 IMG to get back to an earlier available IMG version.
2. Flash V392 OTA to upgrade this to your original version.

The 3rd part of the software id contains the firmware version, eg: LF1V392 => V392. \
Where the letter indicates:
* V - Production release version (should be the most stable option).
* M - Pre-production version.
* R - Test version.


Firmware files will always be .zip, but there are two distinct types:
* OTA - update in place, and keep existing apps.
  Applied through: Settings > System Update > Local update.
* IMG - will wipe the device!
  Applied through: [Service menu](#tv-service-menu) > 



## Download Firmware


## Update Firmware
Prep a USB stick (with at least 4GB size) by formatting FAT32 (or failing that, can try NTFS).


## Troubleshooting



