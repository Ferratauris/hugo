---
title: "6 GRUB configuration"
date: 2021-12-17T22:46:06+02:00
description: "What is GRUB and how can it be modified?"
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

## What is GRUB

Grub (Grand Unified Boot Loader) is a bootloader. It contains the location of the OS on the storage drive.
Grub works for any operating system.
It can determine what hardware to load and what software or modules to load.

## Configuring GRUB

When configuring GRUB, there are 2 places one has to look.

### Default GRUB configurations

The first one is located at /etc/default/grub
There are many ways to edit it. I am particularly partial to VSCode.
For me, I would run this command in shell

```
sudo code /etc/default/grub
```
Let's break that down.
sudo (substitute user do) code (program to be used) /etc/default/grub (path to file we want to open in the program)

But if you are working on a server with no fancy GUI installed and you need to stay in a terminal to edit settings, you will need to run sudoedit /etc/deafault/grub

```
sudoedit /etc/default/grub
```

Let's break that down
sudoedit (substitute user do edit) /etc/default/grub (path to file) 
An editor will open with some settings that can be changed.

When this file is changed, it will not take immediate effect. 
The Bootloader is read only and we are not allowed to make changes.

To make changes from the previous file take effect, we need to run the following command.

```
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```
Let's break that down
sudo (Substitute User Do) grub2-mkconfig (configure grub) -o (Output to a file) /boot/grub2/grub.cfg (file to sent the output to)

In Ubuntu, this is a little easier. Just run

```
sudo update-grub2
```
Let's break that down

sudo (super user do) update-grub2 (update grub-2)

### GRUB service

To get to the location of the GRUB service we need to run this in terminal as root (Administrator)

```
cd /etc/grub.d
```
Let's break that down

cd (change directory) /etc/grub.d (directory to change to)

Below is a listing of the files that can be found at this location

```
░▒▓    ~  sudo ls -alh /etc/grub.d                      ✔  22:39:45  ▓▒░
[sudo] password for ferret: 
total 88K
drwxr-xr-x   5 root root 4.0K Nov 14 22:56 .
drwxr-xr-x 104 root root 4.0K Dec 17 20:49 ..
-rw-r--r--   1 root root  181 Nov 14 22:56 .script_sources.txt
-rwxr-xr-x   1 root root 8.7K Sep  7 17:44 00_header
-rwxr-xr-x   1 root root  270 Apr  5  2021 01_grub-customizer_menu_color_helper
-rwxr-xr-x   1 root root  982 Nov 14 22:56 10_linux_proxy
-rwxr-xr-x   1 root root  14K Sep  7 17:44 20_linux_xen
-rwxr-xr-x   1 root root  12K Sep  7 17:44 30_os-prober
-rwxr-xr-x   1 root root 1.4K Sep  7 17:44 31_uefi-firmware
-rwxr-xr-x   1 root root  214 Sep  7 17:44 40_custom
-rwxr-xr-x   1 root root  215 Sep  7 17:44 41_custom
-rw-r--r--   1 root root  483 Sep  7 17:44 README
drwxr-xr-x   4 root root 4.0K Oct 31 14:50 backup
drwxr-xr-x   2 root root 4.0K Oct 31 14:50 bin
drwxr-xr-x   2 root root 4.0K Nov 14 22:56 proxifiedScripts

░▒▓    ~                                                ✔  22:40:16  ▓▒░

```

Normally we would only configure the 40_custom file to add more  menu entries
(More Operating Systems that can be found on your system)

## Conclusion

* Grub allows one to pick between boot options and is also responsible for finding Operating Systems and the boot process.
* Grub stands for Grand Unified Bootloader.
* Grub is an own source bootloader

* Grub supports Multiple architectures
* Grub supports graphical menus
* Grub offers a rescue mode
* Grub allows us to configure modules

* The menu entries of grub points to operating systems on the disk and also points to kernels

* Grub is automatically configured once Linux is installed
* Grub allows for dual boot configurations 

* A manual configuration is needed once a new operating system is added or once a kernel is updated. This is usually handled by the kernel update package.

* To modify grub paramiters, we run

sudoedit /etc/default/grub

* To configure Grub we edit the following

## On Ubuntu 

/boot/grub/grub.cfg

## On RHEL

/boot/grub2/grub.cfg

To compile the change you have made run:

### On Ubuntu

sudo update-grub2

### On RedHat

sudo grub2-mkconfig -o /boot/grub2/grub.cfg

* To add an OS to grub or make a new menu entry we run

sudoedit /etc/grub.d/40_custom