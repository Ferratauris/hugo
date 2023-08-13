---
title: "5 The Linux Booting process"
date: 2021-12-16T20:14:06+02:00
description: "We take a look at how Linux Boots"
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

## The BIOS (Basic Input/Output System)

When the power button of a computer is pressed, The first thing that happens is the BIOS chip turns on.
The BIOS chip initializes the different hardware components like CPU and RAM.
Bios then finds the correct hard drive to boot from.
It will look for the MBR (Master Boot Record) or GPT (Guid Partition table) on the Storage device that it was set to boot from first and then look for a bootloader.

## Bootloader

The next thing that will happen, is the system will look for a bootloader stored in a MBR (Master boot Record).
The bootloader is usually written to the first part of the Storage device.

## Grub

Grub is the most common bootloader on Linux. This launches the actual Kernel.
Grub will be explained in detail in a later article.

## intird

initrd is what loads the actual kernel.
initrd is found in /boot. This gets loaded into RAM and is the bare minimum a system needs to be able to function. It is essentially the smallest working version of Linux
The Kernel will Initialize the system.
The kernel can be found in /boot and has the name vmlinuz

## Initialization process (systemd)

The next part is the system gets initialized. Systemd is responsible for this
Systemd will start all the background services that are needed  for Linux to function.
Systemd is the very first program that gets run on your PC and always have a process ID of 1

### It is important to note that before systemd, there was another initialization service called sysvinit.

## Conclusion

You should now be able to identify the boot process.
* To list them again:
** BIOS/UEFI
** MBR/GPT
** GRUB
** initrd/Kernel
** Systemd

* System firmware can be either a BIOS or a UEFI

* Firmware is responsible for initializing the hardware and executing the bootloader

* A boot menu will give you the option to configure the boot order

* The MBR data is stored on the first sector of the hard drive

* GPT maintains multiple copies of the boot data

* GRUB is an open source bootloader.
It features support for multiple architectures, graphical menus, and recue mode.
It's menu entries point to operating systems on the disk and kernels.

* The linux kernel is loaded from /boot/vmlinuz followed by the version.
it is copressed with gzip so it will be decompressed and loaded into RAM.

* Initrd or initramfs initializs the RAM and conataines the basic root file system loaded from /boot/initrd-version or /bot/initramfs-version

*  The kernel launches either sysVinit or systemd