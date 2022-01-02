---
title: "16 More on Filtering output"
date: 2021-12-30T21:34:06+02:00
description: "So how else can we filter output?"
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

## grep (globally search a regular expression and print)

grep is used to search for a word or regular expression in either text or a command that we pipe to it.
Remember that grep is case sensitive.
For example. If I want the df command to only show the physical storage driver on my computer, I can pipe it into grep and filter the output to only show the lines that contain sd.

```
df | grep sd
```

Let's break that down!

df(call the df command which reports file system usage) |(pipe output into) grep(call grep, a command that searches for word) sd(word to search for)

Use man (Manual) to see other ways grep can be used.

```
man grep
```

Use man (Manual) to see other ways df can be used.

```
man df
```

## grep with regular expressions

## Search for one or another expression

Grep can search for more than one word.
To do this, we need to first warn grep that we are about to use a regular expression.
To do this, we use grep -E also known as egrep.
The pipe symbol then becomes "or" when used in grep.

Let's look at an example

```
df -h | grep -E "sda|sdb"
```

Let's break that down

df(call the df command which reports file system usage) -h(human readable) |(pipe output into) grep(call grep, a command that searches for word) -e(specifies that a regular expression will be used) sda(word to search for) |(the regular expression "or") sdb(another word to search for)

Let's do the same but with egrep

```
df -h | egrep "sda|sdb"
```

Let's break that down

df(call the df command which reports file system usage) -h(human readable) |(pipe output into) egrep(call the grep command with the -E flag already activated to specify that a regular expression will be used) sda(word to search for) |(the regular expression "or") sdb(another word to search for)

### Search for a range of items

grep can also be used to search for a range of items
Below is an example

```
df -h | egrep "sda[1,5]"
```

Let's break that down

df(call the df command which reports file system usage) -h(human readable) |(pipe output into) egrep(call the grep command with the -E flag already activated to specify that a regular expression will be used) sda(word to search for) "[1,5]"(The brackets are a regular expression indicating a range. the 1 and 5 are the ranges we want to display)

## Conclusion

This is not a very long article
The thing we need to remember is that grep is used to search for string values.
grep has a -e toggle which can also be expressed as egrep, which will allow usage of regular expressions


### I ENCOURAGE YOU TO READ THE MANUAL PAGE FOR REGULAR EXPRESSIONS BELOW IS HOW TO FIND IT

```
man 7 regex
```
