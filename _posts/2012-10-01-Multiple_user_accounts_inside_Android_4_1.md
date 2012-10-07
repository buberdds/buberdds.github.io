---
layout: post
title: Multiple user accounts inside Android 4.1
desc: Multiple user accounts inside Android 4.1
---

After rooting Android Jelly Bean device you will gain access to hidden OS functionality: user profiles.
It's hidden because it's unfinished. Some apps may not work, like Google Chrome for instance. It's always crashing,
while running by secondary user. You cannot hide apps for a guest account etc. Visually you can not determine what user is currently active and
notifications and recent apps do not clear while switching between users.
Jelly Bean’s user profiles are far away from perfect, but still they are usefull.

To manage user accounts you will need
<a href="https://play.google.com/store/apps/details?id=jackpal.androidterm" target="_blank">Terminal Emulator</a>.
First of all, switch to the root account using <code>su</code> command.
You can check your user and group typing: <code>id</code>.

Now you can create a new user typing:
<pre>
<code>
    pm create-user USER_NAME
</code>
</pre>
Apps and some system settings are in /data/user/USER_ID.
The new profile is limited compared to the original. Limitations can be seen in the settings menu.

You can switch between users via command line:
<pre>
<code>
    am switch-user 1
</code>
</pre>

As you can see, you have to type the user id. You can also switch using graphic interface. Just press and hold Power button.

To get list of all users on current device, type:
<pre>
<code>
    pm list-users
</code>
</pre>

To delete user pass the user id (integer) to <code>pm remove-user</code> command.