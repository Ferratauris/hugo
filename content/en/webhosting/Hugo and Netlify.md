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
* vscode (or a text editor like vim or emacs or notepad++ just pick one you are most comfortable with)
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

### On Debian derivatives

    sudo apt install hugo vscode git

### On Red hat derivatives

    sudo yum install hugo vscode git

### On Arch derivatives

    sudo pacman -S hugo vscode git

### On Suse derivatives

    sudo zypper install hugo vscode git

It really couldn't be easier. You just tell your computer what to do and it does it.

## Hugo on Mac OS

For you apple fans out there! Open a terminal by pressing (Cmd+Shift+P) and run one of these commands

    brew install hugo visual-studio-code git

or

    port install hugo visual-studio-code git

Vscode can also be downloaded from their website for Mac. Follow the link below for more information



## Hugo on Windows

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

    Set-ExecutionPolicy AllSigned 

Then run the following command:


    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

Once this is done, We can start with the fun stuffs: using a nix like package manager in Windows

Run

```
choco install hugo git vscode
```
Now the software needed should be installed. Wasn't that quick and painless?

## Netlify

Ok. Now you do need a Netlify account. So follow the link below

https://www.netlify.com

You need to sign in or create a Netlify account.
If you don't have a Netlify account, click on signup, enter your email and choose a password atleast 10 characters long
Then go to your inbox, click on Verify.
Now you will be asked to introduce yourself to Netlify.
You do you on this page. Fill it as you see fit.

The next page will ask you to deploy your first project. We will get to this soon. But first...

## Github

You need to set up a Github account. So follow the link below

https://github.com

Sign in. Or if you do not have an existing account, Sign up:
Enter your email and click on Sign up for Github. Enter a password and click continue
Then enter a username and click continue
then type y if you want to receive product updates via email. Otherwise type n and click continue
Then do an account verification
When that is done, click on create account
Then go to your email and find the otp sent to you and enter it.
Fill the welcome page as you see fit.
Next, pick free. 

Finally, we can start building a website

## Domain Name

Ok. We need a Domain name so people will be able to access the glorious website we have been setting up.
You may use any registrar you choose. but I will be explaining namecheap.
Follow the link below to get to namecheap

https://www.namecheap.com

Here, type in a website URL that you would like for example ferratauris
Then Namecheap will generate a few name suggestions
Before you pick a name, Go to the Namecheap coupon website below

https://couponfollow.com/site/namecheap.com

Get a coupon code before continuing

Back to Namecheap

Add the name that you would like to cart and proceed to checkout.
Enter and confirm coupon code and confirm order.
Sign up or login and pay now.
Now we have a Domain name

## Time to create a new website

In your terminal of choice, navigate to a directory/folder that you want to contain your new website

Now type: hugo new site <name of your new website> then press enter. (Or for a quickstart. Copy the code below and run it)

```
hugo new site quickstart
```
### Add a theme

type: cd <name of your new website> Then press enter. (Or for quickstart. Copy the code below)

```
cd quickstart
```

Then initialize git

```
git init
```
And get the theme

```
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
```
Follow the link below for more themes

https://themes.gohugo.io

Finally we can type:

```
code .
```
This will open VSCode right in the current folder/Directory

To make things easier on yourself, navigate to the website folder in your file explorer and copy the content from
 /(website-name)/(themes)/(theme-name)/exampleSite to
 /(website-name)

 Then back in the terminal, type "hugo serve"

 ```
hugo serve
```

To have a look at it. Click on the localhost link that appears in your terminal.
If all is done correctly, You should now see a fully functioning website.

### All of the themes function differently. Please take a look at the readme for your theme to learn how to configure it.

That was easy enough. But now we need all our friends to access this website aswell

## Create a Github Repository

Go to github as before and click on "New" next to "Repositories"
Give your repository a name then scroll down and click on create.
Then copy the line on this the next page starting with: "git remote add origin https://github.com/" into your terminal and press enter

### Link vscode to github.

In Github go to settings. By clicking your profile pic in the top left corner and then settings.
Go to Developer settings/ Personal access tokens
Then create a new token. Give it all access since it will be you yourself connecting to the repository.
and set the token to not expire.

Back to vscode.

Install the GitHub Pull Requests and Issues Plugin
Sign in by entering your GitHub Username
Then your personal access token

## Netlify time

Click on Import from Git. Select GitHub, then the website you have created.
Then click on deploy site. Wait for Netlify to deploy your website. Once it is done
Click on Set up custom domain.
Give your website a domain that you created in namecheap. 
Yes, add domain

Then under domain management, across from primary domain.
Click on options and select Set up Netlify DNS from the dropdown menu
Click on Verify. Then add domain. Then Continue

See the links? We are going to copy them over to namecheap

In your namecheap dashboard. Go to domain list. Click on manage.
Set Nameservers to custom
click on add a nameserver and paste the link from netlify in there.
Do so for all the links.

And you are done.

## NOW GO WILD AND DO WHAT YOU'D LOVE TO DO ON YOUR NEW WEBSITE.