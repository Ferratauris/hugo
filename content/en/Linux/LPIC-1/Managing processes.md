---
title: "Managing Processes"
date: 2021-12-18T16:27:06+02:00
description: "How are Processes managed in Linux?"
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

## The ps Command

When a Linux system gets booted up, many processes get run even before we get to interact with the system.

To see the Processes, the ps(Process Show) command is used

```
ps
```

Below is an example:

```
░▒▓    ~/b/w/hugo    master  ps                      ✔  21:36:44  ▓▒░
    PID TTY          TIME CMD
  32645 pts/0    00:00:01 zsh
  32684 pts/0    00:00:00 zsh
  32704 pts/0    00:00:00 zsh
  32705 pts/0    00:00:00 zsh
  32707 pts/0    00:00:00 gitstatusd-linu
  40980 pts/0    00:00:00 ps

░▒▓    ~/b/w/hugo    master ?1                       ✔  21:42:39  ▓▒░

```

As you can see, This is not very useful at all. This command without any arguments, will show all the processes currently running in that specific shell. Which is not alot.
This is why we would give the ps command alot more to work with.

The first we look at, is ps-a(Shows all of the current user's processes)

```
░▒▓    ~/b/w/hugo    master ?1  ps -a                ✔  21:47:04  ▓▒░
    PID TTY          TIME CMD
  32684 pts/0    00:00:00 zsh
  32704 pts/0    00:00:00 zsh
  32705 pts/0    00:00:00 zsh
  32707 pts/0    00:00:00 gitstatusd-linu
  41172 pts/0    00:00:00 ps

░▒▓    ~/b/w/hugo    master ?1                       ✔  21:47:08  ▓▒░

```

Mine is not giving alot of information. Mileage may vary on this one

The variant of the command that gets used the most is: ps -aux (Shows all processes across the entire system with the usernames that are running them)

Running ps this way, will give a huge output. I won't post it here as it is a giant mess.
Go ahead, try it for yourself.


### Finding a process

Ok now as you can see, that is a giant mess. Noone will ever be able to work with that.
So to make this command a little more useful, we can use a search program called grep.
pgrep(search for a process)


Looking for the zsh process
```
pgrep zsh
```

```
░▒▓    ~/b/w/hugo    master ?1  pgrep zsh            ✔  21:51:01  ▓▒░
32645
32684
32704
32705

░▒▓    ~/b/w/hugo    master ?1                       ✔  22:03:26  ▓▒░
```

As you can see, I have a few zsh programs running. 

## top

Now, sofar we have been looking at some useful commands.
None of them are as useful as top when we are looking at processes
Running the top command will give you great information to work with. Like the processes using the most of the resources the system has available. It will show the:

* ID of a process
* User running the process
* Process Priority (Measured in niceness)
And many more

```
top
```

Once again, I urge you to try it.

## Conclusion

Although ps can be used to see alot of good information, as it stands now, top is way more useful.
* ps (Shows processes)
* top (Shows all information on the process that is using the most of your processing power.)

### We will learn more useful commands around this later. but for now. I urge you to practice just these commands.