---
title: "Linux Shell"
date: 2021-12-16T18:10:06+02:00
description: "Let's explore the Linux CLI (Command Line Interface)"
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

## Where can we find the terminal?

The are a couple of ways to acces the Linux terminal. The first is if you are on a server, it most likely does not have a GUI (Graphical User Interface) installed. The server will boot directly to teminal.
The second way is to press the shortcut keys. Ctrl+Alt+T 
You can also just launch into a tty (TeleType) ctrl+alt+(F2 to F6). Don't go pressing all of them. Either one of these combinations will work.
To get back to your desktop, press Ctrl+Alt+F7
You can also just open the aplication menu (Start menu) and then just search for terminal and launch it.


### It is important to note that shell runs in a terminal. We interact with the shell.


The font in terminal can be made larger or smaller using the shortcut keys Ctrl+Shift++ or Ctrl+Shift+-

## How does execution work?

When  a program is written for Linux. It is written as a binary that the kernel can understand.
When we type a command in shell, a program is run from a binary.
The kernel looks at the instruction set in a binary file and executes the instructions.

A command acan be broken into differnt parts.
* command (The default instruction set)
* arguement (Changes to the instruction set)

Examples of these are:

* ls ---> Command. Will list all files/folders that are not hidden in your presend working directory
* ls -alh ----> Command + Arguement. Will list ALL files including the hidden ones in a LIST format that  shows more information like which permitions the file have, the size of a file, what user and group the file belongs to, when the file was modified and the size and make it HUMAN readable

Below is an example

```
░▒▓    ~/b/w/hugo    master ?1  ls                   ✔  15:54:06  ▓▒░
archetypes  config  content  public  resources  themes

░▒▓    ~/b/w/hugo    master ?1                       ✔  15:54:11  ▓▒░

```

```
░▒▓    ~/b/w/hugo    master ?1  ls -alh              ✔  15:54:11  ▓▒░
total 40K
drwxr-xr-x  9 ferret ferret 4.0K Dec  1 22:20 .
drwxr-xr-x  5 ferret ferret 4.0K Dec 12 17:30 ..
drwxr-xr-x  8 ferret ferret 4.0K Dec 18 15:54 .git
-rw-r--r--  1 ferret ferret  306 Dec  1 22:20 .gitmodules
-rw-r--r--  1 ferret ferret    0 Dec  1 22:20 .hugo_build.lock
drwxr-xr-x  2 ferret ferret 4.0K Dec  1 22:20 archetypes
drwxr-xr-x  3 ferret ferret 4.0K Dec  1 22:20 config
drwxr-xr-x  3 ferret ferret 4.0K Dec  1 22:20 content
drwxr-xr-x 10 ferret ferret 4.0K Dec  1 22:20 public
drwxr-xr-x  3 ferret ferret 4.0K Dec  1 22:20 resources
drwxr-xr-x  5 ferret ferret 4.0K Dec  1 22:20 themes

░▒▓    ~/b/w/hugo    master ?1                       ✔  15:55:05  ▓▒░

```

## Command examples

```
ls

```
(List) Will list content of the present working directory
For example ls

```
pwd

```
(Print Working Directory) Will output your current location within the file system
For example pwd

```
cd

```
(Change Directory) Change the directory you are currently located at in the file system
For example: cd /home

```
echo

```
(echo) Output your input directly to a specified location (Default location is terminal)
For example: echo hello

```
touch

```
(Touch) Create a new file
for example: touch newfile.txt 

```
cp

```
(Copy) Copy a file
For example: cp newfile.txt newfile1.txt

```
cat

```
(Concatonate) Merge text files together in a single ouput. (Can be used to few the contents of a file when only one filename is given)
For example: cat newfile.txt

```
less

```
(Less) Show content of a file one line at a time
For example: less newfile.txt

```
more

```
(More) Show content of a file one page at a time
For example: more newfile.txt

Most shells have a tab autocomplete function. When typing a command, tab can be pressed to let the system gues what the rest of the command os and then autocomplet the command. This is very useful for being more productive.

## Conclusion

Get familiar with the terminal. In Linux, it is your best friend. It is there to empower you and it is one of the main reasons users leave windows in favor of Linux.
Practice the commands. Use them in different ways and explore them.
The command given here are the basic building blocks.