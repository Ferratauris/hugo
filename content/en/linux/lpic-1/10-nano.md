---
title: "10 Nano"
date: 2021-12-21T21:19:06+02:00
description: "Nano is a noob friendly text editor"
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

## Launching nano

Don't let the subtitle scare you off. Nano is noob friendly, yes, but that doesn't mean only noobs use it.
I myself prefer nano as other text editors have a pretty steep learning curve. Nano is much easier.

To launch nano, simply type "nano" in your terminal

```
nano
```

Use man (Manual) to see other ways nano can be used.

```
man nano
```

You can also specify an existing filename to open that file in nano. Or you can specify a new filename to create a file and open it in nano.

```
nano newfile.txt
```
Let's break that down

nano(nano command being called) newfile.txt(newfile.txt gets created and opened in nano)

## Using nano

We can use arrow keys to move around in a text file opened in nano.
Nano also has shortcut keys shown at the bottom to help us to do common tasks.

The "^" stands for ctrl and then the letter or character after.
To save, for example, is "ctrl+O" (Write out)
To access the "help" page, press "ctrl+h"

### Edit shortcuts

Here, more will be explained, like "m" standing for "Alt" 

There are some basics that I could mention

* "Ctrl+x" Close without saving (nano will give you the option to save if you do this anyways)
* "Ctrl+o" Write or save file
* "Ctrl+r" open or insert another file (There will be more options listed if you press this shortcut)
* "Alt+a" mark a region to be cut or copied
* "Alt+Shift+6" Copy text
* "<" and ">" to move between opened files in nano

### Find and replace text

There are instances where we would like to find text and replace it
For this, We use the "Ctrl+w" combo
From there we can use "Alt+w" to continue the same search

To replace text, there are 2 ways. 
One is to press "Ctrl+/"
The other is to use "Alt+r"
The "Alt+r" combo works across more keyboard layouts than the "Ctrl+/" combo

After one of these combos are entered, you will be prompted to enter a piece of text to replace.
Then you will be prompted to enter text to replace with.
You will then be taken to differnt intances of the text to replace and asked if that instance must be replaced.
There is also an option to just go ahead and replace all of the intances in the file.

## Conclusion

You should now be able to open and create files using nano.
And do some advanced tasks as well
You should also be able to open more than one file.
You should also be able to search and replace text.