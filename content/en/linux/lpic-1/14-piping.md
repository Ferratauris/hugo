---
title: "14 Redirecting data"
date: 2021-12-29T20:51:06+02:00
description: "What is Piping? How does it work?"
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

## Why do we pipe?

Normally when a command is run, the output is sent to standard out which is the terminal.
A pipe allows us to use the output of one command as input for another command.
To do this, we use the pipe command "|"

lets run ps -aux again.

```
ps -aux
```

Let's break that down!

ps(command being called) -a(all)u(users)x(system)

Use man (Manual) to see other ways ps can be used.

```
man ps
```

That is a lot of information.
What if we were looking for a certain process?
Let's try that again. Only this time, we will pipe the output of ps -aux into another command called grep.
Grep let's us search for a word in a set of words.
Let's look for the display manager

```
ps -aux | grep bash
```

Let's break that down!

ps(process show) -a(all) u(user) x(system) |(pipe output into) grep(search utility) bash(term to search for) 

Now that's a lot more useful. We can now see who is running bash, and what the process ID is.

Another common way to use the pipe is to pipe dmesg into the less command.
dmesg is the system log for all hardware. The dmesg command itself will just dump a bunch of text onto your screen. To make it easier to read, we could run "dmesg | les"
And as we know, the less command supports vim commands as well. This means we could search for an entry asell.

```
dmesg | less
```

Let's break that down!

dmesg(hardware log) |(pipe into) less(call the less command)

Use man (Manual) to see other ways more can be used.

```
man more
```

## xargs

There will be instances where a command can not be piped to.
This happens when a command expects a certain input and this input can not be matched.
For instance, lets create a few directories

```
mkdir dir1 dir2 dir3
```

Let's break that down!

mkdir(Make directory) dir1(name of the first new directory) dir2(Name of the 2nd new directory) dir3(name of the 3rd new directory)

That was simple enough. We created 3 folders. So where does piping and xarg fit into this?
Well. The problem comes when we want to use a file with a list of names to create a bunch of folders.
Let's say you have 100 new employees.
All of them need their own directory on the server.

xargs takes the full command that we give it and breaks it up into pieces that will then be fed to mkdir one by one as a series of commands. This means that mkdir will be run separately for each of the names in a file.

First, we will need to create a text file for xarg to work with.
Run the following command to create this file. (It will echo dir1 dir2 dir3 dir4 and so on, on a new line each and redirect the output of the echo command into a text file called names.txt. We will learn more about this in a later article)

```
echo -e "dir1\ndir2\ndir3\ndir3\ndir5" >> names.txt 
```

Let's break that down!

echo(call the echo command) -e(enable interpretation of backslash escapes) "dir1\ndir2\ndir3\ndir3\ndir5"(text to echo, new lines are indicated as /n) >>(append output to) names.txt(name of file to append to) 

Ok now we can cat the content of names.txt and pipe this into mkdir soo mkdir can create all the directories listed in the file. But to make this command work, we will need to use xargs

```
cat names.txt | xargs mkdir
```

Let's break that down!

cat(call concatenate command) names.txt(name of file to call the cat command on) |(pipe) xargs(build and execute command lines from standard input) mkdir(call make directory command)

Use man (Manual) to see other ways more can be used.

```
man more
```

And there you have it. All the directories have been created and it took almost no effort from us.
Isn't Linux just the best?

One last thing. When you want to create a directory with a space in the name. For instance, Your name and your surname "name surname" 
Putting the two names next to each other will be read as 2 different directories to be created. Remember that to most command lines, a space indicates a new argument or command and not something that is part of the previous command.

To put a space there, we use "\" 
Example: ferra\ tor
That will tell the command line that "ferra tor" is one name

## Conclusion

We have learned how piping can be very useful and how to essentially swap commands in a pipe.
Usually mkdir is run and then a list of names are given.
Using xargs, we can give a list of names and then run mkdir, swapping the command around.