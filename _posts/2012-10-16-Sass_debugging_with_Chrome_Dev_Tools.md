---
layout: post
title: Sass debugging with Chrome Dev Tools
desc: Sass debugging with Chrome Dev Tools
---

Support for Sass landed in Chrome. To enable the new debugging option type in Chrome:

<pre><code>chrome://flags</code></pre>

Turn on the <code>Enable Developer Tools experiments</code> functionality.
Open the Dev Tools <code>SHIFT + CTRL + J</code> or press <code>F12</code> and in <code>settings</code> you will find a new tab called <code>Experiments</code>.
It enables options such as:
<ul>
    <li>Show shadow DOM</li>
    <li>Snippets support</li>
    <li>Native memory profiling</li>
    <li>Live native memory chart</li>
    <li>FileSystem inspection</li>
    <li>Show CPU activity in Timeline</li>
    <li>Override Device Geolocation</li>
    <li>Override Device Orientation</li>
    <li>Support for SASS</li>
</ul>

You have to compile Sass with the <code>--debug-info</code> turned on.

Every CSS rule has additional info which is used by the Dev Tools (or other plug):
<pre><code>
    @media -sass-debug-info{filename{font-family:&lt;SOURCE&gt;}line{font-family:&lt;LINE_NUMBER&gt;}}
</code></pre>






