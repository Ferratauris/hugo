---
title: "22 Managing software in RHEL"
date: 2022-01-18T20:02:13+02:00
description: "How can we manage software in RHEL (Red Hat Enterprise Linux)?"
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

Previously, I mentioned that the LPIC exam only focuses Ubuntu and RHEL (Red Hat Enterprise Linux)

First, like with Ubuntu, we need to understand that there are in fact 3 package managers for RHEL based distros:

* yum (yellowdog update manager)
* dnf (dandified yum)
* rpm (redhat package manager)

The original one was rpm. It was created to be able to install or uninstall packages. But it did not track dependencies. Linux packages can sometimes rely on other packages, kernel modules and libraries to work correctly.
How this one works is, you get a zipped package that contains instructions to install the package and only the package and nothing else.

After a while yum was designed. Not only did it search and install software, but it also tracked and installed dependencies.
The problem however is. As you install more and more packages, it has more and more dependencies to keep track of. This is not ideal as yum would slow down over time because of this.

Then dnf was designed.
dnf just does a better job of tracking those all important dependencies. It was designed to be aware of dependencies that other software may rely on if you uninstall a piece of software and it's dependencies.
Not only does it remove the software, but also all of its dependencies unless another installed package depends on it too.

When the package manager is asked to install a package in the command line, it reaches out to the mirrors listed in the configuration file, finds the package, and installs it.

### But where are the mirrors defined?

The mirrors are listed in the following location:

* /etc/yum/repos.d

## How is dnf used?

dnf can be used a few different ways. 
The first way we look at. The way everyone knows.
Installing packages

```
sudo dnf install mc
```

Let's break that down!

sudo(substitute user do, in this case the substitute user is root) dnf(call dandified yellowdog update manager) install(install package name defined) mc(the package we want installed, in this case, midnight commander)

Use man (Manual) to see other ways dnf can be used.

```
man dnf
```

We can also search to see if a package actually exists in the repository

```
sudo dnf search mc
```

Let's break that down!

sudo(substitute user do, in this case the substitute user is root) dnf(call dandified yellowdog update manager) search(search for a package name defined) mc(the package we want searched, in this case, midnight commander)

Use man (Manual) to see other ways dnf can be used.

```
man dnf
```

We can find out more about a package too

```
sudo dnf list mc
```

Let's break that down!

sudo(substitute user do, in this case the substitute user is root) dnf(call dandified yellowdog update manager) list(list information about a package name defined) mc(the package we want information listed of, in this case, midnight commander)

Use man (Manual) to see other ways dnf can be used.

```
man dnf
```

With dnf, we can actually do a little more to get more info. 
For this, we can run dnf info packagename

```
sudo dnf info mc
```

Let's break that down!

sudo(substitute user do, in this case the substitute user is root) dnf(call dandified yellowdog update manager) info(give more information about a package name defined) mc(the package we want information listed of, in this case, midnight commander)

Use man (Manual) to see other ways dnf can be used.

```
man dnf
```

To refresh the database of software available in the repositories you make use of, and upgrade your system. Unlike with Ubuntu. We run a single command: rpm updade

```
sudo rpm update
```

Let's break that down!

sudo(substitute user do, in this case the substitute user is root) rpm(call the dandified yellowdog update manager) update(update the database of available packages)

Use man (Manual) to see other ways rpm can be used.

```
man rpm
```

The last thing we need to know is how to remove packages

```
sudo dnf autoremove mc
```

Let's break that down!

sudo(substitute user do, in this case the substitute user is root) dnf(call the dandified yellowdog update manager) autoremove(autoremove package name defined) mc(the package we want removed, in this case, midnight commander)

Use man (Manual) to see other ways apt can be used.

```
man apt
```

One last thing I need to mention is that one can also point dnf to a local file on your storage to have it installed. Or add your own user defined repositories. The instructions are usually listed by the maintainer

For example. the webmin packages are not in the official repository of ubuntu.
We can add the repository by following the steps listed here:

https://www.webmin.com/deb.html

## Conclusion

Although there are many different ways to manage packages on RHEL, the recommended way is using rpm