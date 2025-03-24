# Intro

My notes on changes I have made to my TCL TV (C645K UK model).

# How-To

## Generic Android

### Enable developer mode

### ADB
#### Connect with ADB
Full guide - https://www.xda-developers.com/install-adb-windows-macos-linux/

Quick guide..
You will need a separate computer for this.
Download the adb client for your platform:
* [Windows](https://dl.google.com/android/repository/platform-tools-latest-windows.zip)
* Ubuntu: `sudo apt-get install android-sdk-platform-tools`

On the TV:
1. [Enable developer mode](#enable-developer-mode)
2. Developer Mode > Enable USB debugging
3. Find the TV's IP: Settings > Network..

From the computer command line: `adb connect <ip of TV>:5555`
The TV should ask if you wish to allow the USB debugging connection. Choose "Allow".

You should now be connected to your TV. You can verify with: `adb devices` (should list your TV).

#### ADB Shell
Once connected with adb, from the computer command line: `adb shell`
You should be presented with a prompt like: `BeyondTV4:/ $`
From this, you will be able to run commands directly on your TV operating system.

## TCL Android



### TV service menu
TV Settings > Picture > Advanced > Brightness > Contrast
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
There are many guides on removing pre-installed TCL apps that come with the TV.
A lot of these are quite agressive, in trying to remove everything. 
But for me, I was happy to just remove a few of the most obvious apps. 
And you need to be careful that you don't remove any of the apps controlling the TV's basic functions, eg the remote.

From [ADB Shell](#adb-shell):
```

```

If you later wish to re-install an app, from the shell: ``


# Software Updates
TCL do not seem to be running any updates over the internet, at least in my region (UK).
Instead, they offer a support service, where you can download firmware updates, and apply these manually via USB stick.

Firmware files will always be .zip, but there are two types:
* OTA - eas


## Download Firmware




