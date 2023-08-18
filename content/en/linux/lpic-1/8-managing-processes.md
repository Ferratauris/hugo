---
title: "8 Managing Processes"
date: 2021-12-19T22:34:06+02:00
description: "How are Processes managed in Linux?"
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

## The ps Command

When a Linux system gets booted up, many processes get run even before we get to interact with the system.

To see the Processes, the ps(Process Show) command is used

```
ps
```

Use man (Manual) to see other ways ps can be used.

```
man ps
```

Below is a short TLDR 
  - List all running processes:
    ps aux

  - List all running processes including the full command string:
    ps auxww

  - Search for a process that matches a string:
    ps aux | grep string

  - List all processes of the current user in extra full format:
    ps --user $(id -u) -F

  - List all processes of the current user as a tree:
    ps --user $(id -u) f

  - Get the parent PID of a process:
    ps -o ppid= -p pid

  - Sort processes by memory consumption:
    ps --sort size


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

First we look at, is ps-a(Shows all of the current user's processes)

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

Use man (Manual) to see other ways pgrep can be used.

```
man pgrep
```

Below is a short TLDR
  - Return PIDs of any running processes with a matching command string:
    pgrep process_name

  - Search for processes including their command-line options:
    pgrep --full "process_name parameter"

  - Search for processes run by a specific user:
    pgrep --euid root process_name



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

So far we have been looking at some useful commands.
None of them are as useful as top when we are looking at processes
Running the top command will give you great information to work with. Like the processes using the most of the resources the system has available. It will show the:

* ID of a process
* User running the process
* Process Priority (Measured in niceness)
And many more

```
top
```

Use man (Manual) to see other ways top can be used.

```
man top
```

Below is a short TLDR
  - Start `top`:
    top

  - Do not show any idle or zombie processes:
    top -i

  - Show only processes owned by given user:
    top -u username

  - Sort processes by a field:
    top -o field_name

  - Show the individual threads of a given process:
    top -Hp process_id

  - Show only the processes with the given PID(s), passed as a comma-separated list. (Normally you wouldn't know PIDs off hand. This example picks the PIDs from the process name):
    top -p $(pgrep -d ',' process_name)

  - Get help about interactive commands:
    ?



Once again, I urge you to try it.

## Conclusion

Although ps can be used to see a lot of good information, as it stands now, top is way more useful.
* ps (Shows processes)
* top (Shows all information on the process that is using the most of your processing power.)

### We will learn more useful commands around this later. but for now. I urge you to practice just these commands.