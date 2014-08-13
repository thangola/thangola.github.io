---
layout: post
title: "What's the difference between .bash_profile vs .bashrc"
date: 2014-08-13 14:19:15 +0700
comments: true
categories: linux login
---

.bash_profile is executed for login shells, while .bashrc is executed for interactive non-login shells. <br />
**What is a login or non-login shell?** <br />

When you login (type username and password) via console, either sitting at the machine, or remotely via ssh: _.bash_profile_ is executed to configure your shell before the initial command prompt. <br />
But, if you’ve already logged into your machine and open a new terminal window (xterm) inside Gnome or KDE, then _.bashrc_ is executed before the window command prompt. _.bashrc_ is also run when you start a new bash instance by typing _/bin/bash_ in a terminal. <br />


**Why two different files?** <br />

Say, you’d like to print some lengthy diagnostic information about your machine each time you login (load average, memory usage, current users, etc). You only want to see it on login, so you only want to place this in your _.bash_profile_. If you put it in your .bashrc, you’d see it every time you open a new terminal window. <br />


**Recommendation** <br />

Most of the time you don’t want to maintain two separate config files for login and non-login shells — when you set a _PATH_, you want it to apply to both. You can fix this by sourcing _.bashrc_ from your _.bash_profile_ file, then putting _PATH_ and common settings in _.bashrc_. <br />

To do this, add the following lines to _.bash_profile_: 
<pre><code>
if [ -f ~/.bashrc ]; then
   source ~/.bashrc
fi
</code></pre>

Now when you login to your machine from a console _.bashrc_ will be called.
