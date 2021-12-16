---
title: "Linux as a VM"
date: 2021-11-29T18:00:06+09:00
description: "We are taking a look at the things we need to know when running Linux as a VM"
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

When we run Linux on a VM it is a little different from running Linux on physical hardware. Let's take a look at these differences. Like hardware detection and Drivers (Modules)

## Differences between running Linux on a VM and running Linux on physical hardware

Mostly Linux on a VM and Linux on hardware runs exactly the same.
There are a few small differences

### Hardware names

Hardware on a Linux VM will usually have weird names. 
Hardware in Linux usually has a short name followed by a number to identify the hardware.
The people making Linux have been very forward thinking in giving your virtual hardware a very high number like 33.
The number for a device on a VM will usually be the number following the number of devices that can possibly be connected to your physical PC. This is to avoid any conflict.
Even though the devices have such strange names, they work like any other physical device.

In a VM if you look at (ls /dev), You will see a number of devices that don't actually exist. This is also because the smart people who make these things just made sure that you will be able to emulate most of the devices one can connect to a computer

```
ls /dev
```
## Optimizing Linux in a VM

### Proprietary

This usually depends on what VM software you are running. Are you running an open source VM or a Proprietary VM?

When installing Linux on a Proprietary VM software, Sometimes hardware would not detect correctly.
Most commonly, the network adapter. In this case, the Proprietary VM driver should be installed.
Installing the VM driver will let Linux know that it is installed on a VM and give better performance or better stability. You will be able to interact with the VM a lot better.

Most of the VM's will have a virtual disk you can mount that has the VM modules that need to be installed.
This will allow for better interaction like clipboard sharing between the host and the VM or browsing networks or allowing the input devices to leave the VM to return to the host and come back again without being trapped in the VM.

### Open Source

Most Linux Distros now come packaged with open VM tools.
Open VM tools are generic tools that other VM software can take advantage of.
With these tools, we don't have to install extra tools

### Installing and enabling open VM tools

To install open VM tools run:

On Debian:

```
sudo apt install open-vm-tools
```

On Redhat:

```
sudo dnf install open-vm-tools
```

On Arch:

```
sudo pacman install open-vm-tools
```
Then to enable the package and start the service we run:

```
sudo systemctl enable --now open-vm-tools
```
## Some problems that might come up

Running Linux in a VM rarely presents any problems except for a few small things, the most common one is mentioned now.

Any form of system standby mode usually doesn't work too well. It is best practice to just turn all of these functions off when running Linux in a VM.

## Conclusion

* Linux is basically built to run on a VM. This is why there are rarely any problems.
* Hardware names might not be as you expect them
* Additional modules might need to be installed to optimize performance of a VM
* Standby modes never works well on Linux VM