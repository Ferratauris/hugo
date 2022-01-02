---
title: "15 More on data redirection"
date: 2021-12-30T21:34:06+02:00
description: "What other ways can data be redirected?"
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

In the previous article I gave you a command to run.
Here is that code again.

```
echo -e "dir1\ndir2\ndir3\ndir3\ndir5" >> names.txt 
```

I did say that we would get to this type of command in a later article.
Well, It's later now.

Sometimes we would need to redirect data to a file rather than another command.
The above command is a great example of this.
More places where we would use something like this, is to keep records of logs or system performance data.
And there is alot more that we can do using data redirects.

### standards

When you type a command, Your keyboard is seen as standard input
The output on your terminal can be split into 2 groups

* Standard out (1) This displays successful commands
* Standard error (2) This displays errors usually to the terminal as well.
 
### Redirecting output.

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

Redirection is a very powerful tool.
When combined with other commands, we can make alot of work a lot easier.
The pipes and the redirects can be used infinately in a single command to create super compleks commands.
You are starting to program now. How exciting!