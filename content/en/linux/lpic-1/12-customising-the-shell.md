---
title: "11 Customizing the shell"
date: 2021-12-22T22:34:06+02:00
description: "We are going to customize the shell to work better for us"
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

### Introduction

When a shell is launched, it has a set of default configurations.
These configurations can come from many different places.
When you launch into a shell, it will get it's configurations for a specific user from the .profile file.
These configurations can carry over between different shells.
The second location is the rc file of the shell. For bash, it is the .bashrc file and for zsh, it is the .zshrc file. This file is specific to a shell.
All shells will also have a .history file that just stores all of the commands you have previously run.
They also have a .logout file which can run a certain script whenever you log out of the shell.
These 2 files are specific to the shell it was configured for.

In the /etc directory, you can also find the global configurations for a shell.
Once again there is a .rc file and a profile.d file. These configurations are in use when there is no user specific configuration set.

## .rc

All the different shells have a .rc file.
I will be using bash as it is the most common shell used in the Linux world.
Bash will use the .bashrc file found in your home folder.
The best way to configure a shell will be to use this file as the profiles configuration doesn't always work.

Now let's dig into the .bashrc file.

From your home folder, type nano .bashrc or if you are a vim user, type vim .bashrc

```
nano .bashrc
```

The first things we'll see, is:

### History

HISTSIZE=1000
HISTFILESIZE=2000

These are used to configure how many commands get stored in your history file and how large that file is allowed to be.

### Prompt text

The text you get when in a prompt. By default it will be your hostname/username/location-in-the-file-system.

This configuration is found in the .rc file just a bit further on.
By default, on Ubuntu it would be 'PS1="[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a]$PS!"'

IT WAS PREVIOUSLY STATED THAT UBUNTU WILL MOSTLY BE USED AS IT IS ONE OF THE MORE POPULAR DISTROS

### Path

IT IS IMPORTANT TO NOTE THAT THIS MIGHT BE FOUND IN THE .profiles CONFIGURATION FILE.

Deeper into the .rc file, we will find where the shell is looking for a command when issued
It would look something like 'PATH="$HOME/bin:$PATH"'
This is a useful path if that directory has been created by you. Chances are, you did not.

A common thing to do here is to add 'PATH=".:$PATH"' -----> This will allow a script to be run from the directory it is stored, without specifying that the shell should look in the current directory.

```
PATH=".:$PATH"
```

To see the path Linux is currently using, type "echo $PATH" in your terminal.

```
echo $ PATH
```

### Aliases

The most useful setting in a shell configy=uration is aliases. run ls again.
Do you see that it is colorised?
This is't usually how la works. This is actually an alias in your .rc file.
It looks like this: "alias ls='ls --color=auto'"
This actually means that when you run ls, the actual command that is run is ls --color=auto

## Functions

Functions are essentially commands that you yourself can write and uncorporate them into the shell.

Below is an example:

cheat() { curl "https://cheat.sh/$1"; }

What this function does, is to show the content of https://cheat.sh/{anything you type into the terminal}

If  you then run "cheat tar" it will return the contents of https://cheat.sh/tar

## Conclusion

This was a hefty article. There was alot to learn and a lot to try to remember
The most important things to learn here are:

* Where the configuration files for the shell are
* How variables, aliases and functions are used.
