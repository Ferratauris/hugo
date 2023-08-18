---
title: "7 Linux Shell"
date: 2021-12-18T16:27:06+02:00
description: "Let's explore the Linux CLI (Command Line Interface)"
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

## Where can we find the terminal?

There are a couple of ways to access the Linux terminal. The first is if you are on a server, it most likely does not have a GUI (Graphical User Interface) installed. The server will boot directly to the terminal.
The second way is to press the shortcut keys. Ctrl+Alt+T 
You can also just launch into a tty (TeleType) ctrl+alt+(F2 to F6). Don't go pressing all of them. Either one of these combinations will work.
To get back to your desktop, press Ctrl+Alt+F7
You can also just open the application menu (Start menu) and then just search for the terminal and launch it.


### It is important to note that the shell runs in a terminal. We interact with the shell.


The font in terminal can be made larger or smaller using the shortcut keys Ctrl+Shift++ or Ctrl+Shift+-

## How does execution work?

When  a program is written for Linux. It is written as a binary that the kernel can understand.
When we type a command in a shell, a program is run from a binary.
The kernel looks at the instruction set in a binary file and executes the instructions.

A command a can be broken into different parts.
* command (The default instruction set)
* argument (Changes to the instruction set)

Examples of these are:

* ls ---> Command. Will list all files/folders that are not hidden in your present working directory
* ls -alh ----> Command + Argument. Will list ALL files including the hidden ones in a LIST format that  shows more information like which permissions the file have, the size of a file, what user and group the file belongs to, when the file was modified and the size and make it HUMAN readable

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

Use man (Manual) to see other ways ls can be used.

```
man ls
```

Below is a short TLDR 

  - List files one per line:
    ls -1

  - List all files, including hidden files:
    ls -a

  - List all files, with trailing `/` added to directory names:
    ls -F

  - Long format list (permissions, ownership, size, and modification date) of all files:
    ls -la

  - Long format list with size displayed using human-readable units (KiB, MiB, GiB):
    ls -lh

  - Long format list sorted by size (descending):
    ls -lS

  - Long format list of all files, sorted by modification date (oldest first):
    ls -ltr

  - Only list directories:
    ls -d */


```
pwd
```
(Print Working Directory) Will output your current location within the file system
For example pwd

Use man (Manual) to see other ways pwd can be used.

```
man pwd
```

Below is a short TLDR

  - Print the current directory:
    pwd

  - Print the current directory, and resolve all symlinks (i.e. show the "physical" path):
    pwd --physical

  - Print the current logical directory:
    pwd --logical


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

Use man (Manual) to see other ways echo can be used.

```
man echo
```

Below is a short TLDR
  - Print a text message. Note: quotes are optional:
    echo "Hello World"

  - Print a message with environment variables:
    echo "My path is $PATH"

  - Print a message without the trailing newline:
    echo -n "Hello World"

  - Append a message to the file:
    echo "Hello World" >> file.txt

  - Enable interpretation of backslash escapes (special characters):
    echo -e "Column 1\tColumn 2"

  - Print the exit status of the last executed command (Note: In Windows Command Prompt and PowerShell the equivalent commands are `echo %errorlevel%` and `$lastexitcode` respectively):
    echo $?



```
touch
```
(Touch) Create a new file
for example: touch newfile.txt 

Use man (Manual) to see other ways touch can be used.

```
man touch
```

Below is a short TLDR
  - Create specific files:
    touch path/to/file1 path/to/file2 ...

  - Set the file [a]ccess or [m]odification times to the current one and don't [c]reate file if it doesn't exist:
    touch -c -a|m path/to/file1 path/to/file2 ...

  - Set the file [t]ime to a specific value and don't [c]reate file if it doesn't exist:
    touch -c -t YYYYMMDDHHMM.SS path/to/file1 path/to/file2 ...

  - Set the file time of a specific file to the time of anothe[r] file and don't [c]reate file if it doesn't exist:
    touch -c -r ~/.emacs path/to/file1 path/to/file2 ...



```
cp
```
(Copy) Copy a file
For example: cp newfile.txt newfile1.txt

Use man (Manual) to see other ways cp can be used.

```
man cp
```

Below is a short TLDR
  - Copy a file to another location:
    cp path/to/source_file.ext path/to/target_file.ext

  - Copy a file into another directory, keeping the filename:
    cp path/to/source_file.ext path/to/target_parent_directory

  - Recursively copy a directory's contents to another location (if the destination exists, the directory is copied inside it):
    cp -r path/to/source_directory path/to/target_directory

  - Copy a directory recursively, in verbose mode (shows files as they are copied):
    cp -vr path/to/source_directory path/to/target_directory

  - Copy multiple files at once to a directory:
    cp -t path/to/destination_directory path/to/file1 path/to/file2 ...

  - Copy text files to another location, in interactive mode (prompts user before overwriting):
    cp -i *.txt path/to/target_directory

  - Follow symbolic links before copying:
    cp -L link path/to/target_directory

  - Use the full path of source files, creating any missing intermediate directories when copying:
    cp --parents source/path/to/file path/to/target_file



```
cat
```
(Concatenate) Merge text files together in a single output. (Can be used to few the contents of a file when only one filename is given)
For example: cat newfile.txt

Use man (Manual) to see other ways cat can be used.

```
man cat
```

Below is a short TLDR

  - Print the contents of a file to `stdout`:
    cat path/to/file

  - Concatenate several files into an output file:
    cat path/to/file1 path/to/file2 ... > path/to/output_file

  - Append several files to an output file:
    cat path/to/file1 path/to/file2 ... >> path/to/output_file

  - Copy the contents of a file into an output file in [u]nbuffered mode:
    cat -u /dev/tty12 > /dev/tty13

  - Write `stdin` to a file:
    cat - > path/to/file

  - [n]umber all output lines:
    cat -n path/to/file

  - Display non-printable and whitespace characters (with `M-` prefix if non-ASCII):
    cat -v -t -e path/to/file


```
less
```
(Less) Show content of a file one line at a time
For example: less newfile.txt

Use man (Manual) to see other ways less can be used.

```
man less
```

Below is a short TLDR
  - Open a file:
    less source_file

  - Page down/up:
    <Space> (down), b (up)

  - Go to end/start of file:
    G (end), g (start)

  - Forward search for a string (press `n`/`N` to go to next/previous match):
    /something

  - Backward search for a string (press `n`/`N` to go to next/previous match):
    ?something

  - Follow the output of the currently opened file:
    F

  - Open the current file in an editor:
    v

  - Exit:
    q




```
more
```
(More) Show content of a file one page at a time
For example: more newfile.txt

Use man (Manual) to see other ways more can be used.

```
man more
```

Below is a short TLDR
  - Open a file:
    more path/to/file

  - Open a file displaying from a specific line:
    more +line_number path/to/file

  - Display help:
    more --help

  - Go to the next page:
    <Space>

  - Search for a string (press `n` to go to the next match):
    /something

  - Exit:
    q

  - Display help about interactive commands:
    h


Most shells have a tab autocomplete function. When typing a command, tab can be pressed to let the system guess what the rest of the command is and then autocomplete the command. This is very useful for being more productive.

## Conclusion

* You should know how to boot directly to console
* The different terminal software include but are not limited to xterm, konsole, gnome terminal.
* The default shell for linux is found at /bin/sh
* Redhat uses bash which is found at /bin/bash
* ubuntu ises dash which can be found at /bin/dash
* You should know some commands like ls or history
* You should know that some commands allows for arguments to be passe aswell.
* You can use tab to autocomplete commands.

* Some of the commands you should master are:
- ls
- mkdir
- cd
- pwd
- echo
- touch
- cp
- cat
- more
- less
- vim
- nano
- gedit

* Vim nano and gedit are used to edit files