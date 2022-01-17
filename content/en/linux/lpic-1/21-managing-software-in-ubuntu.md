---
title: "20 managing software in Ubuntu"
date: 2022-01-17T21:13:13+02:00
description: "How can we manage software in Ubuntu?"
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

Well from my previous blog post you will know that I really like Arch Linux. 
However, the LPIC-1 exam only cares about Ubuntu and RHEL.
So we will be focusing on ubuntu in this article

First we need to understand that there are in fact 3 package managers for Debian based distros and by extension, Ubuntu:

* apt (aptitude)
* apt-get (aptitude get)
* dpkg (debian package manager)

The original one was dpkg. It was created to be able to install or uninstall packages. But it did not track dependencies. Linux packages can sometimes rely on other packages, kernel modules and libraries to work correctly.
How this one works is, you get a zipped package that contains instructions to install the package and only the package and nothing else.

After a while apt-get was designed. Not only did it search and install software, but it also tracked and installed dependencies.
The problem however is. As you install more and more packages, it has more and more dependencies to keep track of. This is not ideal as apt-get would slow down over time because of this.

Then apt was designed (I know. Why the same shorter name? that makes it a little confusing even to me. I honestly thought that apt was designed before apt-get)
apt just does a better job of tracking those all important dependencies. It was designed to be aware of dependencies that other software may rely on if you uninstall a piece of software and it's dependencies.
Not only does it remove the software, but also all of its dependencies unless another installed package depends on it too.

When the package manager is asked to install a package in the command line, it reaches out to the mirrors listed in the configuration file, finds the package, and installs it.

### But where are the mirrors defined?

The mirrors are listed in 2 locations

* /etc/apt/sources.list
* /etc/apt/sourced.list.d

## How is apt used?

apt can be used a few different ways. 
The first way we look at. The way everyone knows.
Installing packages

```
sudo apt install mc
```

Let's break that down!

sudo(substitute user do, in this case the substitute user is root) apt(call aptitude, the package manager) install(install package name defined) mc(the package we want installed, in this case, midnight commander)

Use man (Manual) to see other ways apt can be used.

```
man apt
```

We can also search to see if a package actually exists in the repository

```
sudo search install mc
```

Let's break that down!

sudo(substitute user do, in this case the substitute user is root) apt(call aptitude, the package manager) search(search for a package name defined) mc(the package we want searched, in this case, midnight commander)

Use man (Manual) to see other ways apt can be used.

```
man apt
```

We can find out more about a package too

```
sudo apt list mc
```

Let's break that down!

sudo(substitute user do, in this case the substitute user is root) apt(call aptitude, the package manager) list(list information about a package name defined) mc(the package we want information listed of, in this case, midnight commander)

Use man (Manual) to see other ways apt can be used.

```
man apt
```

To refresh the database of software available in the repositories you make use of, we run apt updade

```
sudo apt update
```

Let's break that down!

sudo(substitute user do, in this case the substitute user is root) apt(call aptitude, the package manager) update(update the database of available packages)

Use man (Manual) to see other ways apt can be used.

```
man apt
```

To update the actual packages that are installed, we run apt upgrade

```
sudo apt upgrade
```

Let's break that down!

sudo(substitute user do, in this case the substitute user is root) apt(call aptitude, the package manager) upgrade(upgrade installed packages)

Use man (Manual) to see other ways apt can be used.

```
man apt
```

One more thing we need to know for ubuntu is upgrading ubuntu itself

```
sudo apt dist-upgrade
```

Let's break that down!

sudo(substitute user do, in this case the substitute user is root) apt(call aptitude, the package manager) dist-upgrade(upgrade ubuntu itself)

Use man (Manual) to see other ways apt can be used.

```
man apt
```

The last thing we need to know is how to remove packages

```
sudo apt autoremove mc
```

Let's break that down!

sudo(substitute user do, in this case the substitute user is root) apt(call aptitude, the package manager) autoremove(autoremove package name defined) mc(the package we want removed, in this case, midnight commander)

Use man (Manual) to see other ways apt can be used.

```
man apt
```

One last thing I need to mention is that one can also point atp to a local file on your storage to have it installed. Or add your own user defined repositories. The instructions are usually listed by the maintainer

For example. the webmin packages are not in the official repository of ubuntu.
We can add the repository by following the steps listed here:

https://www.webmin.com/deb.html

## Conclusion

Although there are many different ways to manage packages on Ubuntu, the recommended way is using apt