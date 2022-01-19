---
title: "23 Supporting Services In Linux"
date: 2022-01-18T20:02:13+02:00
description: "How is Linux initialized?"
draft: false
enableToc: false
enableTocContent: false
tags:
- Linux
- LPIC1
- Courses
- Linux courses
series:
- LPIC1
categories:
- Linux

libraries:

---

Linux is pretty amazing at multitasking.
When you push the power button, You might be met with a prompt with a blinking cursor.
But in the background many services are running that you can't see
This is all handeled by the Linux kernel.
The most important part and the process that gets started first, is the init system.

The 3 init systems we have are:

* Sysvinit. This is the oldest one developed back in the Unix days that did not support removable hardware
* upstart. Developed by canonical in the 2000s to be able to support removable hardware better
* systemd. Developed by RHEL to speed up boot processes.

The best way to find out what init system you are using is just by going to the vendor website and looking at the documentation.

However, if you do not have the means to do this, you can run

```
ls -1 /sbin | grep init
```

Most systems these days run systemd
there are older systems that still run uostart and sysvinit

upstart and sysvinit will show up as init
The only way to really tell if it is running init or upstart, is to look at the manual page for init

``
man init
```

In this documentation, it will list at the very top if it is init or upstart.
Usually we don't really care whether a system is running upstart or sysvinit.
They are configured and controlled exactly the same way. Infact upstart is just sysvinit with a few automation scripts added.

We only care when the system is running systemd, versus the other two, because then, the way we control the system is very different.

It is recommended to never change your init system. Rather change the system entirely.
Changing init systems is really really hard.