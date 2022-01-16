---
title: "13 Managing files"
date: 2021-12-28T22:12:06+02:00
description: "How exactly are files managed in a Linux environment"
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

## What tools are available for everyday tasks?

There is a list of tools one can use. One of them happens to be list (ls)

### List contents of a directory

To list the contents of a directory, simply type ls

```
ls
```

Use man (Manual) to see other ways ls can be used.

```
man ls
```

It is also possible to list the contents of a directory you are not currently in.
Let's list the contents of /etc

```
ls /etc
```

Let's break that down!

ls(call list command) /etc(which directory to list)

Ok. So now we can see a list of content in a directory. But what if we need more information?
Well, we can add arguments to the command. 

Let's list the content of a directory that is not hidden. But let's also see who may read, write, and execute a file. We would also like to see the owner of the file and when the file was created.
To do this, we type ls -l. Let's run this on /etc

```
ls -l /etc
```

Let's break that down!

ls(list) -l(longlist) /etc(patch to directory that needs to be listed)

Ok. Can anyone tell me how much is 4096 bytes? The long list function only showed us the file sizes in bytes. This is not very user friendly. 
To remedy this, we can add the -h toggle.
To do this, we type ls -lh or ls -hl.
The order doesn't matter. As long as all the toggles are there

```
ls -lh /etc
```

Let's break that down!

ls(list) -l(longlist) h(human readable) /etc(patch to directory that needs to be listed)

That's all good and well. But I know there are more files than what showed up. What gives?
The files that did not show up are hidden.
To view hidden files, we use the -a toggle.
Once again, the order doesn't matter.

```
ls -alh /etc
```

Let's break that down!

ls(list) a(all) l(longlist) h(human readable) /etc(path to directory that needs to be listed)


### View contents of a file

It is fairly simple to view the contents of a file.
Let's take a look at what is inside .bashrc
This file can be found in your home directory.

The oldest and easiest way is to use the concatenate "cat" command

```
cat .bashrc
```

Let's break that down!

cat(call cat command) .bashrc(on .bashrc)

Use man (Manual) to see other ways cat can be used.

```
man cat
```

Ok so this is a pretty lengthy file and the command just dumped all of the content in my terminal. Is there a way to do the same thing, but slower?
Yes we can!
More is a command that does the same thing, only it will pause after each page and wait for user input.

```
more .bashrc
```

Let's break that down!

more(call the more command) .bashrc(on the .bashrc file)

Use man (Manual) to see other ways more can be used.

```
man more
```

Ok, that is, again, all good and well. But we can only move forward in a file.
What if we would like to move back as well?
Linux has got you covered.
The command we use for that, is less.
With less, we can use the arrow keys to move text up and down.
Or we can use the page up and page down keys to page forward and backward in a text file.

```
less .bashrc
```

Let's break that down!

less(call the less command) .bashrc(on the .bashrc file)

Use man (Manual) to see other ways less can be used.

```
man less
```

The nice thing about less, is that it also supports vim syntax.
This means that you can even search for a word within less using the same command we would use in vim.

The next pair of commands we will look at are head and tails.
Head will by default give you the first 10 lines in a file.
Tail will give you the last 10 lines.

```
head .bashrc
```

Let's break that down!

head(call the head command) .bashrc(on the .bashrc file)

Use man (Manual) to see other ways head can be used.

```
man head
```

This pair of commands also accepts a -n argument.
For example, we can add "-n 20" to one of these commands to show the first or last 20 lines of a file.

```
tail -n 20
```

Let's break that down!

tail(call the tail command) -n(number of lines) 20(is 20) 

Use man (Manual) to see other ways tail can be used.

```
man tail
```

Tail also has a neat little feature that will keep a file open and display any changes.
we activate this by using the -f toggle. Let's put it all together now.

```
tail -n 30 -f .bashrc
```

Let's break that down

tail(call the tail command) -n(number of lines will be specified) 30(number of lines specified) -f(follow or keep the file open)

### Relocating or rename files files

To move files or to rename files, we use the mv command.
I will not be showcasing this, as all systems are different and I will not be able to know what file(s) can be safely moved or renamed on your system.

The command will be constructed as follows for moving a file

"mv (location-of-file)/(filename) (desired location of the (file)/(filename)"

The rename is exactly the same. However, we keep the same locations and give them a new name.

"mv (location-of-file)/(filename) (location of the file)/(new-filename)

One can also specify more than one file to perform the action on. Even wildcards are accepted.
One can also change the location and the name of a file at the same time.

Use man (Manual) to see other ways mv can be used.

```
man mv
```

### Make a new directory

This will be short and sweet.
The command to create a new directory is mkdir. 
Let's create a directory called test

```
mkdir test
```

Let's break that down!

mkdir(make directory) test(directory name)

Use man (Manual) to see other ways mkdir can be used.

```
man mkdir
```

Simple enough

### Copy files or directories

cp is the command we use for this.
This is much safer, so I will be able to showcase this command.
Let's copy .bashrc into the new test directory we have just created.

```
cp .bashrc test/
```

Let's break that down!

cp(copy) .bashrc(file to copy) test/(destination of the copied file)

Use man (Manual) to see other ways cp can be used.

```
man cp
```

### Remove

To remove a file, rm is used. And to remove a directory, rmdir is used.
When a directory has contents, rmdir will not run on it.
To bypass this, we use the -r (recursive) toggle

Let's remove the test directory

```
rm -r test
```

Let's break that down!

rm(remove) -r(recursive) test(file/directory to remove)

Use man (Manual) to see other ways rm can be used.

```
man rm
```

It is pretty handy to note that one could use "." to represent the current directory and ".." to represent the parent directory (The directory the current directory is in)

The next command will copy test.txt from your documents directory, to your home directory.
but first, we need to create that file.

```
cd Documents
```

Let's break that down!

cd(change directory) Documents(directory to change to)

```
touch test.txt
```

Let's break that down!

touch(create new file) test.txt(name of file to be created)

Use man (Manual) to see other ways touch can be used.

```
man touch
```

```
cp test.txt ../
```

Let's break that down!

cp(copy) test.txt(file to copy) ../(a directory up)

Let's remove that file and do the command again. Only this time, we will use the shortcut for home, which is "~"

```
rm ../test.txt
```

Let's break that down!

rm(remove) ../(one directory up) test (file to remove)

```
cp test.txt ~
```

cp(copy) test.txt(file to copy) ~(home directory)

And there you go. Simple, isn't it?

## Conclusion

There are many commands one can use to manage files in Linux.
All of these are to give you all the power.

Use this power wisely.

### NEVER RUN rm -rm WITHOUT TYPING THE FULL LOCATION AND NAME OF A FILE. RUNNING THIS COMMAND ON THE WRONG THING CAN AND WILL DESTROY YOUR SYSTEM!!!