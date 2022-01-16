---
title: "16 Checksums"
date: 2022-01-03T20:46:06+02:00
description: "how is file integrity determined?"
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

File integrity has always been a problem. From the beginning when files get transferred from one storage device to another to even today when we download files.
We need to be able to ensure that all the parts are there.
Let's find out how.

## Software to use

Linux is a huge community. As such, many have created their own way of checking whether files are correct.
To list a few:

* b2sum
* cksum
* md5sum
* shalsum
* shasum

When choosing a checksum generator, it is always a balance that has to be found between security and usability.

Shasum -a 512 will be the most secure, but it will really be an inconvenience for anyone who needs to check their files using this method.

Usually it is best practice to keep a checksum in more than one place. That way, when a checksum gets compromised, one can still pick up on that using the "backup" checksum

### Create a checksum

It's fairly simple to create a checksum
Just pick a checksum to use and a level of integrity check to pass
For example

```
shasum -a 256 .bashrc
```

Let's break that down!
shasum(call shasum checksum command) -a(algorithm to use will be specified) 256(algorithm to use)

Use man (Manual) to see other ways shasum can be used.

```
man shasum
```

### Verify a file using checksum

To verify a file's integritty, the same checksum and algorithm should be used as the one that was used to create the check.

Usually a developer will release what checksum and algorithm was used

Let's verify that .bashrc is unmodified using the checksum we created earlier

```
shasum -a 256 -c .bashrc
```

Let's break that down!

shasum(call shasum checksum command) -a(algorithm to use will be specified) 256(algorithm to use) -c(check) .bashrc(file to check)

Use man (Manual) to see other ways shasum can be used.

```
man shasum
```

## Conclusion

It is important to know how to check file integrity.
Today there are many hackers and any one of them may be able to corrupt a file.
You should be able to create a checksum so others might double check the integrity of the files you distribute.
