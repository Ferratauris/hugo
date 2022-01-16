---
title: "20 Libraries"
date: 2022-01-16T17:47:07+02:00
description: "What are library files and what are they used for?"
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

Libraries are pieces of code that we can call to do common things.
We don't need to rewrite an entire network stack to communicate over the internet.
Many programs make use of shared libraries to make the jobs of the developers a little easier and more efficient.

To see the libraries that are installed on your system, you can run "ldconfig -v"
This will give you a very large output so it's best to pipe that into less so it can be a little more readable.

This is not particularly useful.
The more useful action to do, is to look at what libraries a certain program uses.
To do this, we run "ldd path to program or command"
For example

```
ldd /usr/bin/ls
```

Let's break that down!

ldd(list daemon dependency, list the libraries needed by the program that will be specified) /usr/bin/ls(the program specified that we want to check the dependencies of)

There is a way for a user to add their own libraries if they would like to use them and not affect the entire system.

Those are usually stored in ".local/lib" in your home folder

## Conclusion

This was a short one.
The important things to know is what a library is and how to find them using the ldd command
Most will never need to create their own libraries or custom add libraries to the system but if you do, you can make use of the custom library folder found in .local/lib in your home directory