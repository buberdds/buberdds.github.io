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

<p>
    <img class="articlePhoto" src="/images/Remote_Debugging_for_Mobile_Web/Remote_Debugging_for_Mobile_Web_photo1.png" alt="Remote Debugging for Mobile Web" />
</p>

On your desktop computer enter the <code>platform-tools</code> SDK's subfolder and type:
<pre>
<code>
    adb devices
    adb forward tcp:9222 localabstract:chrome_devtools_remote
</code>
</pre>

Navigate to localhost:9222 and you'll be able to inspect all pages opened on mobile device.
All tabs of Chrome Dev tools are fully usable.

<p>
<img class="articlePhoto" src="/images/Remote_Debugging_for_Mobile_Web/Remote_Debugging_for_Mobile_Web_photo2.png" alt="Remote Debugging for Mobile Web" />
</p>

<p>
<img class="articlePhoto" src="/images/Remote_Debugging_for_Mobile_Web/Remote_Debugging_for_Mobile_Web_photo3.png" alt="Remote Debugging for Mobile Web" />
</p>

<h2>Weinre</h2>
Weinre uses the user interface code from the Web Inspector project at WebKit, so it runs only on WebKit-based browsers.
It fills gap for remote debugging tools for Android 2.2+ native browser and iOS 4.2+ Mobile Safari.
You can install Weinre using <a href="http://nodejs.org/download/" target="_blank">node</a> package manager:

<pre><code>
    npm install weinre
</code></pre>

Weinre server takes, a few arguments. Most usefull are <code>httpPort</code> and <code>boundHost</code>. boundHost enable
access to the server from any other machine, because it's default value is <code>localhost</code>, it's usefull to change it.
To list all of available options type <code>weinre --help</code>. So to start remote debugging choose a free port and type in your ip address/hostname.
<pre><code>
    weinre --httpPort [portNumber] --boundHost [hostname | ip address]
</code></pre>

In your browser navigate to weinre server. You'll find link to script, which you can inject into your site
<pre><code>
    &lt;script src="http://<ADDRESS>:<PORT>/target/target-script-min.js#anonymous"></script&gt;
</code></pre>

There is also bookmarklet, which allow you to inspect any web page you are viewing.
On your mobile device, open Android Default Browser and navigate to weinre server. Under Target Bookmarklet section
tap and hold link <code>weinre target debug</code> and choose copy link URL option. Now add new bookmark by pressing star icon.
Type in label <code>weinre</code> and in location address paste javascript code from your clipboard. Press OK to save bookmark.

<p>
    <img class="articlePhoto" src="/images/Remote_Debugging_for_Mobile_Web/weinre_photo1.png" alt="Remote Debugging for Mobile Web" />
</p>

On your desktop computer choose the link from <code>Access Points</code> section of weinre server <code>debug client user interface</code>.
On mobile debice navigate to any site, click bookmarklet icon and choose newly added <code>weinre</code>.
On your desktop computer you will see a new client connected to weinre server:

<p>
<img class="articlePhoto" src="/images/Remote_Debugging_for_Mobile_Web/weinre_photo2.png" alt="Remote Debugging for Mobile Web" />
</p>

You can click on it, if you have multiple clients connected you can switch between them just clicking on their name.
In the Elements Tab you will find the markup of debugging website, and CSS.

The <code>Resource</code> is limited to Session Storage, Local Storage and Databases.
The <code>Network</code> tab is limited to XHR request only.

Weinre is very limited. It's not working on all webkit browser, but it is the best options for older Android/iOS devices.

<h2>Adobe Edge Inspect</h2>
Adobe released own inspector. They use a hosted weinre server on Adobe.com.
Don't know why should I use it while I can run local weinre server anywhere, on any OS.
The main advantage is synchronized browsing and refreshing on all connected devices, but usually your gonna searching
for a bug on a specific device. Moreover, this option is <strong>not for free</strong>. You have to buy Creative Cloud plan or pay monthly for upgraded version of Edge Inspect.
