---
title: "17 Locating Binaries"
date: 2022-01-04T20:37:06+02:00
description: "Where are the binaries for commands stored?"
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

When we type a command, the shell takes that command and does something with it.
These commands can either be binaries or it can be built into the shell you are using.

## whereis

The whereis command is used to locate, to locate a file that is in your path.
It will return the location of a file and any manual pages that could be associated with it.
The downside of whereis is that it does not show which binary is run when you type a command.

For example:

```
whereis uname
```

Let's break that down!

whereis(calls the whereis command) uname(file to find)

Use man (Manual) to see other ways whereis can be used.

```
man whereis
```

## Which

The which command is a little more intuative than the whereis command.
Just like whereis, it will also look in your path, but it will always display the first instance of the binary that it finds.

For example:

```
which uname
```

Let's break that down!

which(calls the which command) uname(file to find)

Use man (Manual) to see other ways which can be used.

```
man which
```

## Conclusion

You should now be able to find binaries in your path using which and whereis