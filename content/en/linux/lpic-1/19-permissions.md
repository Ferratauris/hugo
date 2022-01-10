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
man nkdir
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

## Conclusion

* chown is used to change ownership of a file.
* chgrp can be used to change the group a file belongs to.
* chmod can be used to modify file permissions.
* The sticky bit permanently changes the attributes of a directory