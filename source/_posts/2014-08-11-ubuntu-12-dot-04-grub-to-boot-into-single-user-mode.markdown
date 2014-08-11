---
layout: post
title: "Ubuntu 12.04 Grub to boot into single user mode"
date: 2014-08-11 18:04:58 +0700
comments: true
categories: 
---
Hi,

Steps to boot in single user mode in Ubuntu 12.04:

Step 1: When you start your system, press "shift" key continuously to get the grub loader screen.

Step 2: In Grub 2 menu, select the menu with Linux 3.2.0.23-generic-pae highlighted.

Step3: Press 'e' to edit the grub2 menu.

Step 4:  Move the cursor to the line that starts with "linux /boot/vmlinuz-3.2.0-23-generice-pae".

Step 5: Change the content "ro quiet spalsh $vt_handoff" To "rw init=/bin/bash".

Step 6: Press "Ctrl+x" to continue boot to in single user mode.

Step 7: Now you will get prompt of the root user.

Step 8: Change root user password,
# passwd root

Step 9: Now sync and reboot the system i.e.
# sync
# reboot -f

I hope, above steps are helpful to change the root user password in single user mode.
