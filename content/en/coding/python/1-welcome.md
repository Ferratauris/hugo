---
title: "1 Welcome"
date: 2021-12-14T22:04:06+02:00
description: "What can be expected from the Python series"
draft: false
enableToc: false
enableTocContent: false
tags:
- Coding
- Python
- Courses
series:
- Python
categories:
- Python

libraries:

---


## Welcome to Python

Python is a beloved coding language that is very easy to learn.
Yes I can go into detail about how NASA or Google uses python as it can be used for programming or AI learning.
Python is very flexible. We will be learning how to  code using this tremendously popular language.

There are awesome websites out there that can help you code better. Even Youtube videos or courses. I have compiled a bunch of them and will be using these to give a comprehensive understanding.

So Let's stop wasting time and jump in!

We are going to need to have something to code on.

There are many coding platforms we can make use of.  I will be making use of VSCODE.  It is very simple and easy to use.

First, Let's install it.

## VSCODE on Linux

This is the easiest way to use Hugo.

Just open your terminal and type (Package-manager)(install) vscode 

### On Debian derivatives

'''
sudo apt install vscode 
'''

### On Red hat derivatives

'''
sudo yum install vscode 
'''

### On Arch derivatives

'''
sudo pacman -S  vscode 
'''

### On Suse derivatives

'''
sudo zypper install vscode 
'''

It really couldn't be easier. You just tell your computer what to do and it does it.

## VSCODE on Mac OS

For you apple fans out there! Open a terminal by pressing (Cmd+Shift+P) and run one of these commands

'''
brew install visual-studio-code
'''

or

'''
port install visual-studio-code
'''

Vscode can also be downloaded from their website for Mac. Follow the link below for more information



## VSCODE on Windows

Windows has a powerful powershell. Let's put it to good use.
But WAIT! we can't just start using it. First it needs to be set up.
Windows uses Chocolatey or winget to install from powershell
Winget is the official package manager and choco is a community powered package manager
First Chocolatey needs to be set up

### Install Chocolatey

We need to ensure Get-ExecutionPolicy is not restricted

* open powershell as administrator
* Run Get-ExecutionPolicy

```
Get-ExecutionPolicy
```

If it returns:

```
Restricted
```

Run

'''
Set-ExecutionPolicy AllSigned 
'''

Then run the following command:

'''
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
'''

Once this is done, We can start with the fun stuffs: using a nix like package manager in Windows

Run

```
choco install vscode
```
Now the software needed should be installed. Wasn't that quick and painless?

We can also make use of wizards and gui package managers. But To me, this is  the most efficient way.

Now stay in your CLI and create a new folder where your coding learning and projects will live

'''
mkdir python
'''

It is important to make little use of spaces and uppercase characters when naming a file or folder as this will just be easier to  work with in the future.

Now we relocate to that folder.

'''
cd python
'''

We make our first program

'''
code print.py
'''

This will open vscode

Simply type:

'''
print('Hello World!')
'''

save!

Run the code!

You are now a coding master! Soon we  will hack the entire internet!

The above is a simple program to print  the text "hello world!" in the terminal.
It should be noted that either single or double quotes.  it is encouraged to use single as much as possible as this will just make code easier to read.

Let's make another one!

'''
print('hi')
'''

Now let's try another!

'''
print('Hello world!')
Print('My name is')
print('John Doe')
'''

Each print statement will output a whole new line.

You are now a coding machine!
You have just coded 3 different simple text printing software.

Next do it without my help

Write a  program that will output: Do you like green eggs and ham?

GOODLUCK!