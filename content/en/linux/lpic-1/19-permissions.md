---
title: "18 Permissions"
date: 2022-01-11T00:07:07+02:00
description: "Who is allowed to do what on the system?"
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

## Introduction

In the world of operating systems, all files have a permission set tied to it.
This means who is allowed to modify or even see the file.
Usually, the owner has full control over a file.
Even if you specifically change the permission set to deny access to the owner, the owner will have control over the file.
This is to prevent accidental permission mess ups.

## Ownership

We have been seeing permissions and owner information since this whole course supplement started.
To view all the information of a file pertaining to the permission or ownership, ls -l can be used

```
ls -l
```

Let's break that down!

ls(list) -l(longlist)

Use man (Manual) to see other ways ls can be used.

```
man ls
```

So now we have a list of files
You will notice that it starts with some weird characters, then it gives your username twice, then the file size, then the last edit date, then the file name.
The first part with the weird characters are the permissions of a file.

Starting from left to right we have: type,owner(read write execute) group(read write execute) others(read write execute)

Now I would like to create a file real quick that we can do some testing on.

```
echo "this is some text" >> ownfile.txt
```

Let's break that down!

echo(print all input between "" to output) "this is some text"(The text we want printed to output) >>(Redirect output and append to) ownfile.txt(where the output should be redirected to)

Use man (Manual) to see other ways echo can be used.

```
man echo
```

Now let's create a new user to be able to do testing

```
sudo useradd testuser
```

Let's break that down!

sudo(substitute user do) useradd(command to add new user) testuser(name of new user to be created)

Use man (Manual) to see other ways useradd can be used.

```
man useradd
```

First let's check who owns the new file we created!

```
ls -l
```

Let's break that down!

ls(list) -l(longlist)

Use man (Manual) to see other ways ls can be used.

```
man ls
```

Now let's change who owns the file

```
sudo chown testuser ownfile.txt
```

Let's break that down

sudo (substitute user do) chown(change ownership) testuser(new owner to the file) ownfile(file which owner we want to change)

Use man (Manual) to see other ways chown can be used.

```
man chown
```

It is noteworthy that one could use the -R toggle to chown recursively

Another command to take note of is chgrp(changegroup)
As the name suggest, this can be used to change the group a file belong to

This however rarely ever gets used as chown can do exactly the same by adding :groupname after the username.

## Sticky Bit

The sticky bit is simply a way of telling your system that a file created in a certain folder should always belong to a certain user or group.
It's a little harder to explain how to look for it.

When ls-l is run, the file type, then the permissions are shown, usually as read write execute (rwx) for the owner of the group then everyone else.

When an s is shown instead of the x it means that that directory has a sticky bit.
where a sticky bit appears defines what user or group owns the files in a certain folder.

Let's create a folder to become sticky

```
mkdir newdir1
```

Let's break that down!

mkdir(make directory) newdir1(nme of new directory)

Use man (Manual) to see other ways mkdir can be used.

```
man mkdir
```


And then we change the sticky bit for that directory

```
sudo chmod g+s ./newdir1
```

Let's break that down!

chmod(changemode) g(group) +(add attribute) s(Sticky Bit) ./newdir1(directory we want the sticky bit added to)

Use chmod (Manual) to see other ways chown can be used.

```
man chmod
```

Now let's give this folder to the testuser group

```
chown :testuser newdir1
```

Let's break that down!

chown(change ownership) :(define group) testuser(group to give ownership to) newir1(directory which ownership must change)

Use man (Manual) to see other ways chown can be used.

```
man chown
```

You should now see the s attribute when your run ls-l

Now any folder created in this directory will have the testuser group attaches to it.

## File permissions

During the course of reading through all this material, you have probably run ls -l a hundred times.
You probably have seen a hundred times that man can be used to see the manual of a certain command.
You have probably seen the characters in the far left of every file once this command is run.
Those characters start with one of them denominating the type of file.
After that, we get a cluster of read write execute 3 times
rwxrwxrwx
These are the permissions of a file.
The first rwx is the permissions of the owner of a file.
the next rwx is the permissions for the group the file belongs to.
The last rwx is the permissions for everyone else.
If one of these letters does not show up, that means that that particular permission is not set.
Below is an example where everyone has full access to read, write and execute a file

rwxrwxrwx

Now let's take a look at how that would look if the owner has read write and execute permissions. The group has read, write and execute permissions and everyone else has no permissions to read or write but may execute a file.

rwxrwx--x

These are the Posix compliant permissions.
In the posix world, owners of a file are represented by u
The group a file belongs to is represented by g
Everyone else is represented by o

### Old style permissions.

In the Unix world before modern Linux, we used to use bits to set permissions.
This is a little harder for some people to do and you definitely do not need to know any of this.
I would just like to inform you since I find it easier to do it this way and someone reading this might feel the same.

When the permission bits are set, it is important to remember that each permission has a bit value and they are added up to add or remove permissions.

Below are the values of the different permissions:

* stickybit - 1
* setgid - 2
* setuid - 4
* execute - 1
* write - 1
* read - 4

To have a bit set to read and write, we add 4 and 1 to get 5
When setting permissions in this way, the first bit will be for the owner, the second for the group and the third for everyone else.

To give the owner only permission to read and no permissions to anyone else, it will be represented as 400.

Below is an awesome website where you can calculate these values

http://permissions-calculator.org

I will quote from http://permissions-calculator.org/info/ to explain what some of the terms above mean.

setuid:
Binary executables with the setuid bit (chmod u+s path) can be executed with the privileges of the file's owner. Due to it's nature it should be used with care.

In octal, the setuid bit is set with 4000 e.g: "chmod 4755 path".

setuid has no effect if the user does not have execute permissions.

setuid is represented with a lower-case "s" in the output of ls. In cases where it has no effect it is represented with an upper-case "S".

setgid:
Binary executables with the setgid bit (chmod g+s path) can be executed with the privileges of the file's group.

A useful property is to set the setgid bit on a directory so that all files and directories newly created within it inherit the group from that directory.

In octal, the setgid bit is represented by 2000 e.g: "chmod 2755 path".

setgid has no effect if the group does not have execute permissions.

setgid is represented with a lower-case "s" in the output of ls. In cases where it has no effect it is represented with an upper-case "S".

Sticky bit:
The sticky bit (chmod +t path) was introduced for use with executables as a way of telling an operating system to keep the text segment of the program in swap space after the process had terminated. This was a performance feature designed to make subsequent execution of the program faster.

The sticky bit is more commonly used on directories where it allows the files or directories within to only be moved or deleted by that object's owner, the directory owner, or the super-user.

In octal, the sticky bit is set with 1000 e.g: "chmod 1755 path".

The sticky bit has no effect if others do not have execute permissions.

The sticky bit is represented with a lower-case "t" in the output of ls. In cases where it has no effect it is represented with an upper-case "T".

That was a handful

All of this information as said before is really not all that necessary.
I only provide it just in case someone out there exists that thinks like me.

## New style permissions

The new way is easier for most people to read. you just remember the previous mentions of owner(u), group(g) and other(o). And read(r), write(w) and execute(x)

To add a permission, we use + to remove a permission, we use - and to overwrite a permission we use =

We are also allowed to add more than one together. specifying ugo will set permissions for the owner group and others.
Specifying rwx will work with read, write and execute.
one could even use a comma to separate the different permissions out.

If I wanted to remove the group and other the read permission, I could write it as g-r,o-r
Or if I want to give read and write to group, I could write it as g+rw
If I want everyone to have only read and write I can write it as ugo=rw

Below is an example where I will remove the read permission of both group and other.
But first let's create a file to play with

```
echo "This is some text" >> newfile.txt
```

Use man (Manual) to see other ways echo can be used.

```
man echo
```

Let's break that down!

echo(sent input text to output) "This is some text"(The input we want sent to the output) >>(redirect and append output to) newfile.txt(Where we want the output redirected and to)

```
chmod g-r,o-r newfile.txt
```

Let's break that down!

chmod(change mode of a file) g(group) -(remove) (read permission) ,(more to come) o(other) -(remove) r(read permission) newfile.txt(the file we are changing the mode on)

Use man (Manual) to see other ways chmod can be used.

```
man chmod
```


## Conclusion

* chown is used to change ownership of a file.
* chgrp can be used to change the group a file belongs to.
* chmod can be used to modify file permissions.
* The sticky bit permanently changes the attributes of a directory