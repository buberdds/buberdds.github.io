---
layout: post
title: Remote Debugging for Mobile Web
desc: Remote Debugging for Mobile Web
---

<h2>Chrome for Android</h2>
Inspecting remote devices with the desktop Chrome Dev Tools is the best option so far. The only one disadvantage is of course
limitation to Android 4+ devices, older versions are left behind. Now, all you need is to have Android SDK on your desktop and
Chrome on your mobile device. As useally you communicate via ADB so connect your device using USB wire.
Launch Chrome and enable debugging <code>Settings > Advanced > Developer tools > Enable USB Web debugging</code>.
On your desktop computer enter the <code>platform-tools</code> SDK's subfolder and type:
<pre>
<code>
    adb devices
    adb forward tcp:9222 localabstract:chrome_devtools_remote
</code>
</pre>

Navigate to localhost:9222 and you'll be able to inspect all pages opened on mobile device.
All tabs of Chrome Dev tools are fully usable.


<h2>Weinre</h2>
comming soon

<h2>Adobe Edge Inspect</h2>
Adobe released own inspector. They use a hosted weinre server on Adobe.com.
Don't know why should I use it while I can run local weinre server anywhere, on any OS.
The main advantage is synchronized browsing and refreshing on all connected devices, but usually your gonna searching
for a bug on a specific device. Maybe I'm missing something or I'm just not the target of this product.

<h2>Firefox for Android</h2>
comming soon

<h2>Opera Dragonfly</h2>
comming soon

