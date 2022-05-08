---
title: "26 Supporting storage devices"
date: 2022-01-26T19:57:22+02:00
description: "What do we do when we want to create a partition on the hard drive?"
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

## What tools can be used to create and manage partitions in Linux?

The two most prominent ones are fdisk for MBR(Master Boot Record) and gdisk for GPT(Guid Partition Table)

These days, partitions aren't needed so much anymore.
We have really really big storage drives.
Partitions can still be useful however.

One might decide to put /var on it's own partition. This way if someone tries to make a million print jobs in an attempt to slow down your system, it will only affect that one partition and nothing else.

Another idea is to separate the home folders on different partitions.
This way, no matter what happens to the user folder, the system remains unaffected and vice versa
I was able to fully reinstall my OS and keep all my files and settings because my home folder was not only on a different partition but on a different storage drive.
You might also create a partition specifically for swap to ensure that a swap space is always available for your system.

## There are 2 types of partitions. Primary and extended or logical partitions

A primary partition will usually be where your boot data is stored.
Your system must be able to access these partitions quickly.
This is only true for mbr(master boot record)

There is however a new kid on the block

## GPT(Guid Partition Table)

Instead of partitions, we have volumes on a GPT drive.
you can have as many volumes as you like.

### CAUTION! RUNNING THE COMMANDS SHOWN IN THIS PAGE WITHOUT PRIOR KNOWLEDGE AND INTENT MAY CAUSE IRREVERSIBLE DATA LOSS! PLEASE DO NOT JUST RUN THE COMMANDS UNLESS YOU KNOW IT REALLY IS WHAT YOU NEED TO BE DOING!

## fdisk

Okay, we are just about to get started formatting and partitioning drives.
But before we can do that, we need to know the name of the drive we want to modify.

To do this, we run lsblk(list block devices)

```
lsblk
```

Let's break that down!

lsblk(List block devices)

Use man (Manual) to see other ways lsblk can be used.

```
man lsblk
```

For the next part, I will assume the drive is empty with no partitions

So let's then start modifying a disk.
To do this, we type fdisk followed by the drive path that we want to modify.

```
sudo fdisk /dev/sdd
```

Let's break that down!

sudo(substitute user do) fdisk(manipulate disk partition table) /dev/sdd(The path to the drive we want to modify, in this case, sdd)

Use man (Manual) to see other ways fdisk can be used.

```
man fdisk
```

The key functionality that gets used most on fdisk is p(print, Shows the partitions already there) n(New partition) w(write new partition table)

after we have run fdisk /dev/sdd you will be in the fdisk utility and the system will wait for your nest input
Press n to create a new partition
The system will ask if it's a primary or extended partition
For the purposes of this article, I will choose primary

The system will then ask for a partition number.
Usually the first available number should be used.

Then comes the size.
First we will need to give a starting sector.
The first empty sector should be used here.
on most empty and new disks, this is 2048

Now we need to define the size.
Long ago, we would've needed to calculate sector sizes and junk
If you read the screen, you will notice that the system is telling you that you may use +size(abbreviation) The abbreviations it supports are k(kilobyte) M(Megabyte) G(Gigabyte) T(Terabyte) P(Petabyte) 

So to wrap that all up, we would probably type +20M to create a 20 megabyte partition

Now finally just type W to write the changes to the disk.

## gdisk

This is quite similar

So let's then start modifying a disk.
To do this, we type gdisk followed by the drive path that we want to modify.

```
sudo gdisk /dev/sdd
```

Let's break that down!

sudo(substitute user do) gdisk(Interactive GUID partition table (GPT) manipulator) /dev/sdd(The path to the drive we want to modify, in this case, sdd)

Use man (Manual) to see other ways fdisk can be used.

```
man gdisk
```

The key functionality that gets used most on gdisk is p(print, Shows the partitions already there) n(New partition, create new partition) w(write new partition table)

after we have run gdisk /dev/sdd you will be in the fdisk utility and the system will wait for your next input
Press n to create a new partition

The system will  ask for a partition number.
Usually the first available number should be used.

Then comes the size.
First we will need to give a starting sector.
The first empty sector should be used here.
on most empty and new disks, this is 2048

Now we need to define the size.
Long ago, we would've needed to calculate sector sizes and junk
If you read the screen, you will notice that the system is telling you that you may use +size(abbreviation) The abbreviations it supports are k(kilobyte) M(Megabyte) G(Gigabyte) T(Terabyte) P(Petabyte) 

So to wrap that all up, we would probably type +20M to create a 20 megabyte partition

Now finally just type W to write the changes to the disk.

## Conclusion

Fdisk is used to create partitions on a MBR disk
Gdisk is used to create partitions on a GPT disk