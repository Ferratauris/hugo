---
title: "25 Systemd"
date: 2022-01-26T19:57:22+02:00
description: "What exactly is this thing called systemd and how can we use it?"
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

The biggest reason systemd was developed was to better support dynamic hardware.
In this day and age we are used to adding and removing hardware on the fly, like connecting and disconnecting USB devices.

With the older sysvinit, the system booted from scripts in series.
One script ran after another until all of them were done.
This means that if one of the scripts hangs, your entire boot process is halted until that gets sorted out.

Systemd is a binary. it also runs scripts to initialize your system, but it does it in paralel. which means a better and faster boot time. 

To check if your system is running systemd, it is as simple as check in in /usr/sbin
a symlink called init should be there that points to /lib/systemd/systemd
This tells you that systemd is the init system for your system.

Systemd gets it's configurations from 2 places

The first and default one is /lib/systemd
These are configurations that are put there by the distribution itself to get your system up and running.
If we take a look inside this location, we will find targets. The targets are the ones that actually tell your system which services to actually stort and when.

You will also find run levels that are symlinked to different targets to give a little backwards compatibility. For those who still use the old commands.

The second location where systemd configuration files are stored is /etc/systemd/system
In this location, custom overrides get listed.
This is where you would put your custom configurations if you want to change the way your system is initialized.

The runlevels are as follows:

poweroff.target(system is not on)
rescue.target(single user mode. You can use this to repair a malfunctioning machine)
multi-user.target(non graphical multi user environment)
graphical.target(graphical multi user environment)
reboot.target(system is rebooting)

Changing the default target is super simple.
for example if you want to set the default to multi user:

```
sudo systemctl set-default multi-user.target
```

Let's break that down!

sudo(substitute user do) set-default(set default target) multi-user.target(the target we want as a default.)

Use man (Manual) to see other ways systemd can be used.

```
man systemd
```

But you don't have to wait until the next reboot.
You can also change the runlevel on the fly
for example if we want to switch to multiuser mode immediately:

```
sudo systemctl isolate multi-user.target
```

Let's break that down!

sudo(substitute user do) isolate(we want to isolate the system to a specified target) multi-user.target(the target we want to isolate the system to.)

Use man (Manual) to see other ways systemd can be used.

```
man systemd
```

## So how are services managed and installed?

Getting a service to start is pretty easy. Below I will start ssh now and enable it to start at system startup.

```
sudo systemctl enable --now ssh
```

Let's break that down!

sudo(substitute user do) systemctl(system control) enable(enable a specified service at boot) --now(start that service immediately) ssh(secure shell, used to remotely log into a system)

Use man (Manual) to see other ways systemd can be used.

```
man systemd
```

### It should be noted that replacing enable with disable will have the opposite effect.

### removing the --now string will cause the service to not start immediately but be enabled to start at system bootup

Now below, I will show how to check whether a service is running and enabled on boot.

```
systemctl status ssh
```

Let's break that down!

sudo(substitute user do) systemctl(system control) status(Check the status of a specified service) ssh(secure shell, used to remotely log into a system)

Use man (Manual) to see other ways systemd can be used.

```
man systemd
```

Next, let's start a service

```
systemctl status ssh
```

Let's break that down!

sudo(substitute user do) systemctl(system control) start(start a specified service) ssh(secure shell, used to remotely log into a system)

Use man (Manual) to see other ways systemd can be used.

```
man systemd
```

### Please note that stating stop instead of start, the service will stop instead

### To restart a service, simply replace start with restart.
