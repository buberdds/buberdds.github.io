---
layout: post
title: Multiple user accounts inside Android 4.1
desc: Multiple user accounts inside Android 4.1
---

After rooting Android Jelly Bean device you will gain access to a hidden OS functionality: user profiles.
It's hidden because it's unfinished. Some apps may not work, like Google Chrome for instance. It's always crashing,
while running by a secondary user. You cannot hide apps for a guest account etc. Visually you cannot determine what user is currently active,
notifications and recent apps do not clear while switching between users.
Jelly Bean’s user profiles are far away from perfect, but still they are useful.

To manage user accounts you will need
<a href="https://play.google.com/store/apps/details?id=jackpal.androidterm" target="_blank">Terminal Emulator</a>.
First of all, switch to the root account using the <code>su</code> command.
You can check your user and group typing: <code>id</code>.
<p>
<img class="articlePhoto" src="/images/Multiple_user_accounts_inside_Android_4_1/Multiple_user_accounts_photo1.jpg" alt="Android multiple user accounts" />
</p>
Now you can create a new user:
<pre>
<code>
    pm create-user USER_NAME
</code>
</pre>
Apps and some system settings are in /data/user/USER_ID.
The new profile is limited compared to the original. Limitations can be seen in the settings menu.

You can switch between users via the command line:
<pre>
<code>
    am switch-user USER_ID
</code>
</pre>

As you can see, you have to type the user id. You can also switch using graphic interface. Just press and hold the Power button.

<p>
<img class="articlePhoto" src="/images/Multiple_user_accounts_inside_Android_4_1/Multiple_user_accounts_photo2.jpg" alt="Android multiple user accounts" />
</p>

To get the list of all users on a current device, type:
<pre>
<code>
    pm list-users
</code>
</pre>

To delete a user pass the user id to the <code>pm remove-user</code> command.
<pre>
<code>
    pm remove-user USER_ID
</code>
</pre>