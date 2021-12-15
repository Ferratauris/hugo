---
title: "Installing Linux"
date: 2021-11-29T18:00:06+09:00
description: "How exactly is Linux Installed?"
draft: false
enableToc: false
enableTocContent: false
tags:
-
series:
-
categories:

libraries:

---

## Getting to know Linux

In this article we are going to talk about the fundamentals of installing Linux.

* How and where to get a Linux distribution (Distro)
* How to build an installation media
* How to install Linux onto a system

First We will need to ensure that we have a system that can actually run Linux.
Research will need to be done.
Next we will need to decide which Distro to use.
There are a whole slew of available Distros.
Most of which are based on root Distros and then built from there
The root Distros include but are not limited to:

### Linux Distro tree in a nutshell

* Slackware (one of the oldest Distros). Distros based on Slackware include:
 S.U.S.E

 * Debian (One of the most supported Distros). Distros based on Linux include:
 Sparky Linux
 Linux Mint Debian Edition
 sparky Linux
 SteamOs (The old one)
 Lindows
 Backtrack
 kali
 Raspberry Pi OS
 Tails
 Ubuntu

 Ubuntu also has a whole slew of distros based on it which include:
 Kununtu
 Deepin
 Backtrack
 Zorin OS

 * Red Hat (An enterprise version of Linux) Distros based on Red Hat include:
 ClearOS
 Oracle Linux
 CentOS
 Qubes OS
 Mandrake
 Open Mandriva

* Jurix which include: 
Open SUSE

Enoch Which include:
Gentoo
Chromium OS

* Arch Linux Which includes:
Manjaro
BlackArch
Archie

* Linux From Scratch (LFS)

* Android OS

* AOSP Which includes: 
LineageOS

The full tree can be explored in the link below

https://upload.wikimedia.org/wikipedia/commons/b/b5/Linux_Distribution_Timeline_21_10_2021.svg

As you can clearly see, Linux runs your world. It would be to your benefit to understand is

## Finding a Distro

For LPIC-1 We will focus on Ubuntu and CentOS

### The first thing I need you to understand is that Linux is Linux. Everything that works for one will most likely work for all of them.

A Distro is just Linux with a few handy programs installed. You are free to mix and match
You don't need to have Kali Linux to be able to do penetration testing. You only need to install the programs on the Distro of your choice. Everything in Linux is cusomisable

Please also take note that the biggest difference between Distro families are the way software is installed. Apt does not work on Arch and Zypper will not work in Ubuntu.
This is the only major difference between Distro families

### Ubuntu

To get Ubuntu we need to go to the Ubuntu website. The link is below

https://ubuntu.com

click on Download. 

On the download page, we can pick between different versions of Ubuntu. They are all essentially the same thing, but they have different packages pre-installed to make your life easier.

On the Ubuntu website, there is a full guide to creating a bootable USB to install operating systems.
Follow the link below

https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview

### CentOS

To get CentOS follow the link below

centos.org

Click on Download

Once again, we will have more than one version aimed at the different use cases

(The fedora website has a media writer that will create a bootable USB for you. It has a windoes and a Mac version)

Follow the link below to get the Fedora Media Writer

https://getfedora.org/en/workstation/download/

A bootable USB is needed to install Linux on barebones. 
An ISO will do just fine if you are planning on running a Virtual Machine (VM)

## ALWAYS BACKUP YOUR DATA. THIS CAN NOT BE STRESSED ENOUGH.

If you are installing Linux on an existing system, please be aware that like any other OS install, your data will be destroyed to change the format of the storage media in preparation for a new OS install. Please do not attempt a dualboot. They are notoriously easy to set up and notorious for breaking your system and creating a situation where no OS works anymore.

Remember to set up your BIOS to boot from your new USB key if you are planning on going the bare Bones route

## Install Linux

### First Boot

Insert your USB key and set your BIOS to boot from it
We are going to use Ubuntu as an example as most installs are very much the same
Your Ubuntu install will allow you to either try Ubuntu or Install Ubuntu
Try will boot up into a desktop envirnoment with software ready to go. It is essentially a fully functioning OS from your USB. (I say fully functional but remember, this is running from a USB so no drivers will be installed and your system might not work to it's full potential)

The install is pretty standard. A few settings will be presented like
* Keyboard layout. (Do you use qwerty or dvorak? is this a US or a UK layout)
* Updates and other software (Here options like what apps you want, what drivers you want and how you want your updates are set)
* Installation Type. ( Here you can either erase the entire disk to install Linux or customize your partition layout. IGNORE DUALBOOT)
* You will be warned before the install starts that you are about to lose all the data on your storage device
* Where are you? (Linux is not tracking you. It would just like to set up your timezone correctly)
* Who are you(Here you can create your username and password)

Ubuntu should now be installed and your PC can be restarted to boot off of the hard drive where Ubuntu is now installed

After installing an OS, it is wise to run updated as USBs go out if date fairly quickly
Then identify any hardware that was not detected and installed automatically by the system and find and install the necessary drivers.

## Conclusion

You should now have a fully installed Linux OS of your choice. Updated and ready to go
This is a simple and straightforward task just like instaling windows.
Just remember to always read what the screen is saying to avoid any headaches