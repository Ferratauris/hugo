---
title: "24 Introduction to sysvinit"
date: 2022-01-20T19:22:22+02:00
description: "What exactly is this thing called sysvinit?"
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

Sysvinit itself is a very simple binary that calls on a bunch of configuration scripts to get your system up and running.
This is one of the reasons so many Unix users still like to use it, configuring the initialize system is as simple as changing a few text files.
The most important scripts that sysvinit launched are rc.local and rc.sysinit found in /etc/rc.d
Another place it can sometimes be found is /etc
It is recommended that if you want to modify your init system, to never touch rc.sysinit and instead modify rc.local
sysvinit is also responsible for keeping track of what state your system is in.

There are 7 states your system can be in:

0 off. Your system is not turned on
1 single user mode. Only 1 user can be logged in. Good for doing maintenance
2 multi user mode without networking.
3 full multiuser mode
4 custom. You can customize this one to your liking
5 Multi user mode with a graphical user interface
6 reboot. System is not on or off

The runlevels configuration files are stored in /etc/rc.d/
Each folder in here rc0.d through rc6.d are the different folders containing scripts to be used at each runlevel.

To see your current system runlevel run 

```
runlevel
```

or

```
who -r
```

Remember that these commands will not work on a systemd system

To change your runlevel, simply run the command init followed by the runlevel you want to switch to.