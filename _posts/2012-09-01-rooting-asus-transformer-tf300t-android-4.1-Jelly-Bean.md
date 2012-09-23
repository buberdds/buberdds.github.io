---
layout: post
title: Rooting Asus Transformer TF300T on Android 4.1 Jelly Bean
desc: Rooting Asus Transformer TF300T on Android 4.1 Jelly Bean
---

<h4>Download Unlock device app</h4>

Download official <abbr>Unlock app</abbr> from <a href="http://support.asus.com.tw/download/" target="_blank">Asus website</a>.
You will find apk under <abbr>Utilities</abbr> category. Unlocker for Ice Cream Sandwich work on Jelly Bean too. BTW you will no longer be covered under the warranty and your tablet and can no longer receive ASUS software updates.

<h4>Download Superuser</h4>

You can find it on <a href="http://androidsu.com/superuser/" target="_blank">AndroidSU.com</a>.<br /> You have to get 3.2 version: Superuser-3.2-RC3-arm-signed.zip.

<h4>Download TWRP</h4>

On the <a href="http://teamw.in/project/twrp2" target="_blank">Team Win Recovery Project</a> select TF300T device and download:<br/><abbr>openrecovery-twrp-2.2.2.0-tf300t-JB.blob</abbr>, rename file to twrp.blob.

<h4>Android Debug Bridge (adb)</h4>

If you don't have Android SDK already installed on your computer you can download it from <a href="http://developer.android.com/sdk/index.html" target="_blank">here</a>.
Commands: adb and fastoot are located in platform-tools sdk's subfolder. Place all files:
<pre>
<code>
    UnLock_Device_App_V7.apk
    Superuser-3.2-RC3-arm-signed.zip
    twrp.blob
</code>
</pre>
in that folder (or add to platform-tools to PATH).

<h4>Pushing files</h4>
Connect to your tablet using adb and push unlock app and superuser.

<pre>
<code>
    adb devices
    adb push UnLock_Device_App_V7.apk /sdcard/
    adb push Superuser-3.2-RC3-arm-signed.zip /sdcard/
</code>
</pre>

It's time to run unlock app on your Transformer. After unlocking you have to use fastboot command and install TWRP.

Turn off your device and boot to fastboot (power on while holding volume down, then select the usb icon and hit volume up to confirm). The device will now be in fastboot mode. Plug the device into your computer and type:

<pre>
<code>
    fastboot -i 0x0B05 flash recovery twrp.blob
</code>
</pre>

When the progress bar will get filled up, press and hold the Volume Up + Power buttons together to reboot.

<h4>Boot into TWRP recovery.</h4>

Shutdown tablet and run it pressing pressing and hold Volume Down + Power. Choose RCK to run TWRP - just press the Volume Up.
Select Install option and choose Superuser-3.2-RC3-arm-signed.zip from sdcard. Select zip, install and reboot system.

<h4>Finall hit</h4>

Install <a href="https://play.google.com/store/apps/details?id=eu.chainfire.supersu" target="_blank">SuperSU</a> app on your tablet.






