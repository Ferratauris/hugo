---
title: "9 Process Priorities"
date: 2021-12-20T22:21:06+02:00
description: "How are processes prioritized?"
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

## How does process priorities work?

Linux is really good at multitasking. Many processes can run at the same time. But it is important to note that a processor can only handle one process at a time per core. This happens extremely fast as processors can do millions of calculations per second.


### But why then do we need to get involved with process priorities?

To the Linux kernel, all processes are seen as equal. No one process is more important than another.
This can be a little counterintuitive especially when we need to for example a backup or encode a video. Usually we'd want the processor to spend more time doing that than some other menial task. Or maybe the reverse is true. We would want to be able to give more processor time to one process over another.

## Managing processes

### Nice!

To manage process priorities, Linux assigns a niceness value to processes. The "nicer" a process is, the less priority it will have to run on your system. (It is nice, waiting and letting others do their work first). Nice values are between -20 and +19. A lower value would mean that the process has a higher priority.

To run a command with a nice value, we would put nice -n (+-){priority number from -20 to +19}

example:

```
sudo nice -n -15 vivaldi
```
This will run vivaldi at a higher priority. Now nothing can stand in my way of binging netflix

### Seeing niceness value

The easiest way o see a niceness value of a process is to run top

```
top
```
The niceness value will appear in the NI column


### Renice

Ok. So now we can run a process with a higher or lower priority. But what if we need to change the priority.
You had a backup running while you were binging netflix, but now this backup needs to finish. There is a power outage scheduled soon. So how will we then give the backup a higher priority and vivaldi a lower priority?
So from running top earlier, we saw the process I for Vivaldi

For that, we use renice (sudo renice {new niceness value}{process ID})

For example
```
renice 10 5095
```

## Killing a process

Sometimes, it may happen that a process is stuck and occupying your processor. 
We would like to stop it completely as soon as possible

There are a few different arguments one can give the kill command.

* kill -1 (This will force a process to reload and try again)
* kill -15 (This will ask a program to write to the hard drive and then terminate)
* kill -9 (This is brutal. The first 2 commands is a signal to the process. This one signals the processor to just drop the process altogether, Do not write to the hard drive and do not restart.)

Below is an example of killing off a random process. DO NOT RUN THIS COMMAND ON YOUR OWN SYSTEM! IT MIGHT BREAK SOMETHING!

```
kill -9 5095
```


## Conclusion

We should now be able to identify process priorities, change process priorities and terminate processes