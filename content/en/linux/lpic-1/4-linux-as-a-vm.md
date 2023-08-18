---
title: "4 Linux as a VM"
date: 2021-12-16T18:10:06+02:00
description: "We are taking a look at the things we need to know when running Linux as a VM"
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

Let's break this down.
ls(list) /dev(the directory whose contents we want to list).

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

Let's break this down.
sudo (substitute user do) apt(aptitude, the package manager for debian based distros) install(install a program) open-vm-tools(the program to be installed).

Use man (Manual) to see other ways sudo can be used.

```
man sudo
```
Below is a short TLDR

  - Run a command as the superuser:
    sudo less /var/log/syslog

  - Edit a file as the superuser with your default editor:
    sudo --edit /etc/fstab

  - Run a command as another user and/or group:
    sudo --user=user --group=group id -a

  - Repeat the last command prefixed with `sudo` (only in `bash`, `zsh`, etc.):
    sudo !!

  - Launch the default shell with superuser privileges and run login-specific files (`.profile`, `.bash_profile`, etc.):
    sudo --login

  - Launch the default shell with superuser privileges without changing the environment:
    sudo --shell

  - Launch the default shell as the specified user, loading the user's environment and reading login-specific files (`.profile`, `.bash_profile`, etc.):
    sudo --login --user=user

  - List the allowed (and forbidden) commands for the invoking user:
    sudo --list


Use man (Manual) to see other ways apt can be used.

```
man apt
```
Below is a short TLDR

  - Search for a given package:
    apt search package

  - Show information for a package:
    apt show package

  - Install a package, or update it to the latest available version:
    sudo apt install package

  - Remove a package (using `purge` instead also removes its configuration files):
    sudo apt remove package

  - Upgrade all installed packages to their newest available versions:
    sudo apt upgrade

  - List all packages:
    apt list

  - List installed packages:
    apt list --installed


On Redhat:

```
sudo dnf install open-vm-tools
```

Let's break this down.
sudo (substitute user do) dnf(dandified ).

Use man (Manual) to see other ways dnf can be used.

```
man dnf
```
below is a shoert TLDR

  - Upgrade installed packages to the newest available versions:
    sudo dnf upgrade

  - Search packages via keywords:
    dnf search keyword1 keyword2 ...

  - Display details about a package:
    dnf info package

  - Install a new package (use `-y` to confirm all prompts automatically):
    sudo dnf install package1 package2 ...

  - Remove a package:
    sudo dnf remove package1 package2 ...

  - List installed packages:
    dnf list --installed

  - Find which packages provide a given command:
    dnf provides command

  - View all past operations:
    dnf history


On Arch:

```
sudo pacman install open-vm-tools
```

Use man (Manual) to see other ways pacman can be used.

```
man pacman
```

Below is a short TLDR

  - Synchronize and update all packages:
    sudo pacman -Syu

  - Install a new package:
    sudo pacman -S package_name

  - Remove a package and its dependencies:
    sudo pacman -Rs package_name

  - Search the database for packages containing a specific file:
    pacman -F "file_name"

  - List installed packages and versions:
    pacman -Q

  - List only the explicitly installed packages and versions:
    pacman -Qe

  - List orphan packages (installed as dependencies but not actually required by any package):
    pacman -Qtdq

  - Empty the entire pacman cache:
    sudo pacman -Scc


Let's break there commands down now.
First we call sudo (Substitute User Do).
This allows us to do actions as a system administrator.
Then we call in the package manager.
Then we tell the package manager to install a package.
Then we give the package name.

### Enable Open VM Tools

Then to enable the package and start the service we run:

```
sudo systemctl enable --now open-vm-tools
```
Let's break this down.
Sudo(substitute user do) systemctl (system control) enable (enable) --now (immediately) open-vm-tools (the service we want to start).

Use man (Manual) to see other ways systemctl can be used.

```
man systemctl
```

Below is a short TLDR

  - Show all running services:
    systemctl status

  - List failed units:
    systemctl --failed

  - Start/Stop/Restart/Reload a service:
    systemctl start|stop|restart|reload unit

  - Show the status of a unit:
    systemctl status unit

  - Enable/Disable a unit to be started on bootup:
    systemctl enable|disable unit

  - Mask/Unmask a unit to prevent enablement and manual activation:
    systemctl mask|unmask unit

  - Reload systemd, scanning for new or changed units:
    systemctl daemon-reload

  - Check if a unit is enabled:
    systemctl is-enabled unit


## Some problems that might come up

Running Linux in a VM rarely presents any problems except for a few small things, the most common one is mentioned now.

Any form of system standby mode usually doesn't work too well. It is best practice to just turn all of these functions off when running Linux in a VM.

## Conclusion

* Linux is basically built to run on a VM. This is why there are rarely any problems.
* Hardware names might not be as you expect them
* Additional modules might need to be installed to optimize performance of a VM
* Standby modes never works well on Linux VM