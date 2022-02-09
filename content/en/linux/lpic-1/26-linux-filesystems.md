---
title: "27 Linux Filesystems"
"
date: 2022-01-26T19:57:22+02:00
description: "What filsystems are there and how do they work?"
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

## Introduction

There are many filesystems in Linux.
Each of them have their own best use cases.

### EXT (Extended Filesystem)

Ext has been around for a long time
There have been many iterations of this filesystem including:

* EXT
* EXT2
* EXT3
* EXT4

The latest version (EXT4) can support:

* volumes of upto 1 Exobyte
* Files upto 16TB
* Unlimited subdirectories
* Journaling (First seen on EXT3)

Journaling needs some explaining.
When a file is written, it does not overwrite an existing file but rather it gets written to a special portion of the storage drive.
Only when the final file is written does the old one get deleted in favour of the new one.
This means that if by chance, your system loses power unexpectedly, the file will be untouched and you won't lose all your work.

### XFS (Extents Filesystem)

XFS was developed by SGI (Silicon Graphics) and it supports

* Volumes upto 8 Exobyte
* Files upto 1 Petabyte
* Extents
* Journaling

Extents need some explaining.
Usually when a large file is created, it can span over many sectors, each of these sectors need a reference to this file.
Throw some fragmentation in there and you have a performance nightmare.
So instead of referencing every single sector, and extent references a range of sectors.

### BTRFS (B-Tree Filesystem)

BTRFS was developed by Sun microsystems and support:

* Volumes upto 8 Exobyte
* Files upto 8 Exobyte
* Snapshots
* Journaling
