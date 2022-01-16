---
title: "11 Vim"
date: 2021-12-22T22:34:06+02:00
description: "Vim is probably the most powerful text editor you will ever learn"
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

## Intro to vim

vim is a super powerful text editor. It is a significantly difficult text editor for noobies to use.
The learning curve is much steeper than nano.
Most Linux veterans use vim as it supports a lot of powerful features like macros.
vim is also designed to only utilize a keyboard even if the entire right side of the keyboard is missing, like if the arrow keys are not there.
vim allows for programming, code review, syntax highlighting, debugging and testing.

## Start using vim

To open vim, simply type vim in your terminal.

```
vim
```

Use man (Manual) to see other ways vim can be used.

```
man vim
```

You can also specify an existing filename to open that file in nano. Or you can specify a new filename to create a file and open it in vim.

```
vim newfile.txt
```
let's break that down

vim(call vim command) newfile.txt (open or create and open newfile.txt)

## Modes of operation

vim has 3 modes of operation.

* Command mode (Issue commands like copy, paste, delete)
* Insert mode (For typing)
* Visual mode (Look at a file)

## Commands

Press : to enter command mode

* h (Move the cursor left)
* j (Move the cursor down)
* k (Move the cursor up)
* l (Move the cursor right)
* i (Insert mode)
* w (Write)
* q (Quit)
* Esc (exit insert mode and enter visual mode)
* ! (Do a command without safety checks)
* any number (Jump to that line)
* Set number (Show line numbers)
* d (Delete a line. When you are in visual mode, dd will achieve the same result. This can also be used   with line number for example ":1,5d" will delete lines one through 5)
* y (Copy a line to clipboard. When you are in visual mode you can use yy for the same result)
* p (paste a line. Also works in visual mode)
* help (show vim documentation)
* e! (Throw away all changes and reopen the file)

You can also use ZZ in visual mode as a shortcut to save and quit

## Searching and replacing text

### Search

To search in vim, While vim is in the visual mode, type "/(word)" to search for a word.

You can also search for a word before opening vim. In your terminal, type "vim +/(word) (textfile). to open vim directly at the word you want to search for.

To repeat a search just press "/" and enter

You can also use "n" to repeat the search forward and "N" to search  backwards.

### Replace

To replace a word use ":" to go to command mode. Then  "s/" and a word to search for "/" Word to replace with. ":s/(searchword)/(replaceword)

You can also start the command with "line number,line number" to search and replace across a bunch of line numbers "(line number),(linenumber)s/"searchword"/"replaceword"

This is a case sensitive search



## Conclusion

You should now be ready for basic vim usage