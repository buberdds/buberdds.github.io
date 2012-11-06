---
layout: post
title: Remote Debugging for Mobile Web
desc: Remote Debugging for Mobile Web
---

<h2>Chrome for Android</h2>
Inspecting remote devices with the desktop Chrome Dev Tools is the best option so far.  The only disadvantage is of course
limitation to Android 4+ devices, older versions are left behind. Now, all you need is to have Android SDK on your desktop and
Chrome on your mobile device. As usual you communicate via ADB so connect your device using USB wire.
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

Navigate to localhost:9222 and you'll be able to inspect all the pages opened on a mobile device.
All the tabs of Chrome Dev tools are fully usable.

<p>
<img class="articlePhoto" src="/images/Remote_Debugging_for_Mobile_Web/Remote_Debugging_for_Mobile_Web_photo2.png" alt="Remote Debugging for Mobile Web" />
</p>

<p>
<img class="articlePhoto" src="/images/Remote_Debugging_for_Mobile_Web/Remote_Debugging_for_Mobile_Web_photo3.png" alt="Remote Debugging for Mobile Web" />
</p>

<h2>Weinre</h2>
Weinre uses the user interface code from the Web Inspector project at WebKit, so it runs only on WebKit-based browsers.
It fills a gap for remote debugging tools for Android 2.2+ native browser and iOS 4.2+ Mobile Safari.
You can install Weinre using a <a href="http://nodejs.org/download/" target="_blank">node</a> package manager:

<pre><code>
    npm install weinre
</code></pre>

Weinre server takes a few arguments. Most usefull are <code>httpPort</code> and <code>boundHost</code>. boundHost enables
access to the server from any other machine, because its default value is <code>localhost</code>, it's useful to change it.
To list all of the options type <code>weinre --help</code>. So to start remote debugging choose a free port and type in your ip address/hostname.
<pre><code>
    weinre --httpPort [portNumber] --boundHost [hostname | ip address]
</code></pre>

In your browser navigate to the weinre server. You'll find a link to the script, which you can inject into your site, while you are in development environment:
<pre><code>
    &lt;script src="http://&lt;ADDRESS&gt;/target/target-script-min.js#anonymous"&gt;&lt;/script&gt;
</code></pre>

There is also bookmarklet, which allows you to inspect any web page you are viewing.
On your mobile device, open Android Default Browser and navigate to the weinre server. Under the Target Bookmarklet section
tap and hold link <code>weinre target debug</code> and choose copy link URL option. Now add new bookmark by pressing star icon.
Type in label <code>weinre</code> and in location address paste javascript code from your clipboard. Press OK to save the bookmark.

<p>
    <img class="articlePhoto" src="/images/Remote_Debugging_for_Mobile_Web/weinre_photo1.png" alt="Remote Debugging for Mobile Web" />
</p>

On your desktop computer choose the link from <code>Access Points</code> section of weinre server <code>debug client user interface</code>.
On mobile device navigate to any site, click a bookmarklet icon and choose a newly added <code>weinre</code>.
On your desktop computer you will see a new client connected to weinre server:

<p>
<img class="articlePhoto" src="/images/Remote_Debugging_for_Mobile_Web/weinre_photo2.png" alt="Remote Debugging for Mobile Web" />
</p>

You can click on it, if you have multiple clients connected you can switch between them just clicking on their name.
In the Elements Tab you will find the markup of debugging website, and CSS.

The <code>Resource</code> tab is limited to Session Storage, Local Storage and Databases.
The <code>Network</code> tab is limited to XHR request only.

Weinre's inspector is very limited. It doesn’t work on all webkit browsers, but it is the best options for older Android/iOS devices.

<h2>Adobe Edge Inspect</h2>
Adobe released its own inspector. They use a hosted weinre server on Adobe.com.
Don't know why I should use it while I can run a local weinre server anywhere, on any OS.
The main advantage is the synchronized browsing and refreshing on all connected devices, but usually you’ll be searching
for a bug on a specific device. Moreover, this option is <strong>not for free</strong>. You have to buy Creative Cloud plan or pay monthly for upgraded version of Edge Inspect.

<h2>Opera Dragonfly</h2>

Debugging Opera Mobile is available only on Android devices. This is the most user friendly debugging option.
On your desktop Opera open Dragonfly <code>Ctrl + Shift + I</code> and choose the <code>Remote Debug Configuration</code> icon.

<p>
<img class="articlePhoto" src="/images/Remote_Debugging_for_Mobile_Web/dragonfly1.jpg" alt="Remote Debugging for Mobile Web" />
</p>

The only one configuration step is to set a port number.

In Opera Mobile navigate to:

<pre><code>opera:debug</code></pre>

In the debug window fill in IP address of your desktop computer and the chosen port number, tap <code>connect</code> button.
You'll be able to debug any opened website in Mobile Opera via the desktop Dragonfly.


<h2>Firefox</h2>

You can debug Android devices using Firefox too. Connect your mobile device via the USB to a host machine and forward the TCP connection using adb (yes, you need Android SDK):

<pre><code>adb forward tcp:[portNumber] tcp:[portNumber]</code></pre>

On your desktop computer navigate to <code>about:config</code> and set the <code>devtools.debugger.remote-enabled</code> property to <code>true</code>.
After restarting, Firefox will reveal a new option in the menu bar (tools -> web developer): <code>Remote Debugger</code>.

You have to enable the same property in Firefox for Android. When you navigate to the <code>about:config</code> type in a search box <code>devtools</code>.
You will see a list of devtools properties, set the <code>devtools.debugger.remote-enabled</code> to <code>true</code> and the <code>debugger.force-local</code> to <code>false</code>.

To start a remote connection, you have to know the IP address of your mobile device (Settings -> Wi-Fi -> tap a name of your active connection).
On your desktop choose the <code>Remote debugger</code> and fill in IP address of your mobile device and a forwarded via adb port number.
You will see a connection prompt and you have 3 seconds to press OK.

In the Firefox 16 the remote debugger is limited to Javascript only and you might be disappointed.

The web console will be available in the version 19. Debugger will support CSS/Network etc., better late than never.




