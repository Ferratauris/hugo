---
title: "14 Redirecting data"
date: 2021-12-29T20:51:06+02:00
description: "What is Piping? How does it work?"
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

## Why do we Redirect data?

Normally when a command is run, the output is sent to standard out which is the terminal.
This output can then be redirected in many differnt ways.

### Piping

the firt way to redirect output we are going to look at, is piping
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

### piping with xargs

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
Run the following command to create this file.

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

In the previous article I gave you a command to run.
Here is that code again.

## Redirecting using >

Sometimes we would need to redirect data to a file rather than another command.
The above command is a great example of this.
More places where we would use something like this, is to keep records of logs or system performance data.
And there is alot more that we can do using data redirects.

### standards

When you type a command, Your keyboard is seen as standard input
The output on your terminal can be split into 2 groups

* Standard out (1) This displays successful commands
* Standard error (2) This displays errors usually to the terminal as well.
 
### Redirecting output to a file.

To redirect output to a file or device, we use the ">" symbol
Let's create a file that contains a list of all the files in our present working directory.

```
ls -lh > list.txt
```

Let's break that down!

ls(list) -l(longlist) h(human readable) >(redirect output into) list.txt(where output needs to be redirected)

Let's see that list

```
cat list.txt
```

Let's break that down

cat(concatenate) list.txt(file to concatenate)

Now that was cool.
It is important to note that when you use a single ">"
The system interperets this as write.
Redirecting anything else into the same file will overwrite all the data in the file.

But what if we already have data in a file?
I can use the redirect to keep a record of logs or system performance.
But if it all keeps getting erased, that is not very useful.

Ok don't panic. We can append to a file by using ">>"
Lets give that a try

```
ls -alh ../ >> list.txt
```

Let's break that down!

ls(list) -a(all) l(longlist) h(human readable) ../(one directory up) ..(append output to file) list.txt(file to append output to)

Now we should have a file that lists the contents of the present working directory and then the parent directory.

```
cat list.txt
```

Let's break that down!

cat(concatenate) list.txt(file to concatenate)

### /dev/null

Now let's find any mp3 files on the system starting from root

```
find / -name *.mp3
```

Let's break that down!

find(call the find command) /(directory file to execute the find command on) -name(name will be specified) *(anything) .mp3(with the .mp3 extension)

Use man (Manual) to see other ways find can be used.

```
man find
```

Wow! That was a lot of errors. Now you could go ahead and sif through all that output and try to find the mp3 files on the system. But there is an easier way.

Let's just redirect the errors. 
Ok. But do we really need a text file that contains all the errors from this command?
No! We will redirect it to /dev/null
This is a virtual device on your system where data goes to die.

```
find / -name *.mp3 2> /dev/null
```

Let's break that down!

find(call the find command) /(directory to call the find command on) -name(name will be specified) *(anything) .mp3(with the .mp3 extension) 2>(redirect all errors to) /dev/null(virtual dump device)

Nice! Now we only saw the output that was needed!

### tee

The last thing I want to mention is the tee command.
This can be used to output to the terminal as well as a file.
Perhaps we would like to see the data now, but also save it for later use.

Let's find the jpg files on the system and save the results for later use

```
find / -name *.jpg 2> /dev/null | tee list.txt
```

Let's break that down!

find(call find command) /(directory path to call find on) -name(name will be specified) *(anything) .jpg(with the .jpg extension) 2>(redirect errors) /dev/null(where to redirect errors to, in this case a virtual text dump device) |(pipe output into) tee(read from standard input and write to standard output and files) list.txt(file to write output into)

## Conclusion

We have learned how piping can be very useful and how to essentially swap commands in a pipe.
Usually mkdir is run and then a list of names are given.
Using xargs, we can give a list of names and then run mkdir, swapping the command around.
Redirection is a very powerful tool.
When combined with other commands, we can make alot of work a lot easier.
The pipes and the redirects can be used infinately in a single command to create super compleks commands.
You are starting to program now. How exciting!