---
title: "17 Locating files or binaries"
date: 2022-01-05T20:48:06+02:00
description: "How do we search for things in the linux command line?"
draft: false
enableToc: false
enableTocContent: false
tags:
  - Linux
  - LPIC1
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

## Find

Find is the end all be all of trying to locate a file or binary.
Find is case sensitive.
It is however important to note that the syntax of find is a little different to what one is used to.

### Search by name

For example:

```
find / -name bashrc 2> /dev/null
```

Let's break that down.

find(call the find command) /(location we want to search through, in this case, the root of the file system) -name(the name of the file will be specified) bashrc(the name of the file we are trying to find) 2(Errors) >(redirect output) /dev/null(A location that doesn't physically exist)

Use man (Manual) to see other ways find can be used.

```
man find
```

Notice how the syntax is -name. In normal unix syntax, each of those letters would have been a toggle.
With find, the entire word is the toggle.
Make a note of this!

### Search by file size

Finding files according to their size is also very useful

Below is an example:

```
find / -size 20M 2> /dev/null
```

Let's break that down.

find(call the find command) /(location we want to search through, in this case, the root of the file system) -size(The size of the file will be specified) 20(The numeric value of the size of the file) M(Megabytes) 2(Errors) >(redirect output) /dev/null(A location that doesn't physically exist)

Use man (Manual) to see other ways find can be used.

```
man find
```

To find files that are bigger than a certain size, the + is used.
For smaller than a certain size, the - is used.
Bytes ares depicted as c
kilobytes are depicted as k
Megabytes are depicted as M (Notice the M is capitol)

Below is an example of finding a file that is bigger than a certain amount of kilobytes.
The same syntax can be used for different file sizes higher or lower.

```
find / -size +2000k 2> /dev/null
```

Let's break that down.

find(call the find command) /(location we want to search through, in this case, the root of the file system) -size(The size of the file will be specified) +(bigger than) 2000(The numeric value of the size of the file) k(kilobytes) 2(Errors) >(redirect output) /dev/null(A location that doesn't physically exist)

Use man (Manual) to see other ways find can be used.

```
man find
```

## Grep

Grep is a command that instead of searching the name of a file, it searches the content of a file.
In this instance, we will be looking at grep -r to recursively search the contents of a file.
By default, grep is case sensitive, however, one can change that behavior.
Another useful way to use grep, is to only show the filenames. 
Grep by default shows the line in the file where a word was found.


Here is an example

```
grep -ril "alias" ~/
```

Let's break that down!

grep(call the grep search command) -r(recursive) i(case insensitive) l(list filenames only) "alias"(what to search for) ~/(Home directory)

Use man (Manual) to see other ways grep can be used.

```
man grep
```

## Conclusion

You should now be able to find binaries in your path using which and whereis.
You should also be able to find files using the file command.
Please go check the manual. There are use cases I haven't mentioned for find.
Like searching according to permissions.
grep can be used to search the contents of files. we can add toggles like r and i to have the search  run case insensitively or recursively