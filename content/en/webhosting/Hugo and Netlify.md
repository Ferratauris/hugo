---
title: "Hugo and Netlify"
date: 2021-11-29T18:00:06+09:00
description: "For those who find just coding things easier."
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

This is by far my favorite way. The website you are viewing right now is made by using this method.

Once again, Your website will haveto be registered to be accessible from the public, but that will then be all. No paying Google or Amazon, only the domain name.

So let’s start.

We will need a few things.

* Hugo
* git
* vscode (or a text editor like vim or emacs or notepad++ just pick one you are most comforatble with)
* A github account
* A netlify account
* Some knowledge of how all of this fits together (I will attempt to help with this)

You can do all of this using a terminal, but if you want ease of use, get VS Code or Git desktop. This will make your life a little easier.

Most of the content laid out here is also available on the Hugo website. Please go have a look.

First, we need to install Hugo.

This can be different depending on your system
Having Linux or Mac OS would make this alot easier for you

## Hugo on Linux

This is the easiest way to use Hugo.

Just open your terminal and type (Package-manager)(install) hugo vscode git

### On Debian derivitaves

    sudo apt install hugo vscode git

### On Red hat derivatives

    sudo yum install hugo vscode git

### On Arch derivitaves

    sudo pacman -S hugo vscode git

### On Suse derivatives

    sudo zypper install hugo vscode git

It really could't be esier. You just tell your computer what to do and it does it.

## Hugo on Mac OS

For you apple fans out there! Open a terminal by pressing (Cmd+Shift+P) and run one of these commands

    brew install hugo visual-studio-code git

or

    port install hugo visual-studio-code git

Vscode can also be downloaded from their website for Mac. Follow the link below for more information



## Hugo on Windows

Windows has a powerful powershell. Let's put it to good use.
But WAIT! we can't just start using it. first it needs to be set up.
Windows uses Chocolatey or winget to install from powershell
Winget is the official package manager and choco is a cummunity powered package manager
First Chocolatey needs to be set up

### Install Chocolatey

We need to ensure Get-ExecutionPolicy is not restricted

* open powershell as administrator
* Run Get-ExecutionPolicy

    Get-ExecutionPolicy

If it returns

```
Restricted
```

Run

    Set-ExecutionPolicy AllSigned 

Then run the following command:


    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))