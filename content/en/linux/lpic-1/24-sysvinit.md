---
title: "24 
sysvinit"
date: 2022-01-20T19:22:22+02:00
description: "What exactly is this thing called sysvinit and how can we use it to manage services?"
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

Well we do not need to be absolute kings when it comes to managing services
Usually, when a service is installed, it is as simple as running a simple command to have it run.

### Services at boot and chkconfig

To launch a service at boot, we use chkconfig servicename on
instead of on, we use off to set the service to not run at boot
for example, to have apache run at system boot on centos

```
sudo chkconfig httpd on
```

Let's break that down!

sudo(substitute user do) chkconfig(check configuration) httpd(apache server in centos) on(set to run at boot)

Use man (Manual) to see other ways chkconfig can be used.

```
man chkconfig
```

Other ways we can make use of chkconfig is to check or change the runlevel a service is running at
To check the runlevel of a service, we use chkconfig --list
This command can even be piped into grep

To set a runlevel for a service, we use --level
Below is an example of setting the runlevel of an apache web server to runlevel 3 and 5 on a centos system

```
sudo chkconfig --level 35 httpd on
```

Let's break that down!

sudo(substitute user do) chkconfig(check configuration) --level(runlevel to be set) 3(set runlevel to 3) 5(set runlevel to 5) httpd(apache server in centos) on(set to run at boot on specified runlevel)

Use man (Manual) to see other ways chkconfig can be used.

```
man chkconfig
```

### Services on an already running system

Well when the server is set to launch at system boot, it will launch at system boot.
But what if we do not want to reboot the system to turn on this service?
For that, we use the service command
It has a few toggles one can give it to achieve different results

* status (check if a service is running)
* start (start a service)
* stop (stop a service)
* restart (restart a service)

Below is an example of turning on the apache server on a centos system

```
sudo service httpd on
```

Let's' break that down!

sudo(substitute user do) service(we want a service to do something) httpd(the service we want doing something) on(we want the service to simply turn on immediately)
