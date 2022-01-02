---
title: "16 Filtering output"
date: 2022-01-02T21:26:06+02:00
description: "So how can we filter output?"
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

## Sort

Sort, as is implied, allows us to sort output in a way that we want.
Usually when we list the content of a directory, it will be sorted alphabetically.
Running sort on it's own will sort output alphabetically.
But if we run "sort -r" we can reverse that order.

```
ls /bin | sort -r
```

Let's break that down!

ls(call list command) /bin(directory to call the list command on) |(pipe output into) sort(call the sort command) -r(reverse)

Use man (Manual) to see other ways sort can be used.

```
man sort
```

## Translate (tr)

The problem is that sort is not very sophisticated.
Sort will look from the start of the output and count spaces as characters aswell.
This would mean that if we do a long list, the output will not be sorted in a way that actually makes sense.

Give it a try.

```
ls -alh / | sort
```

Let's break that down!

ls(call list command) -a(all) l(longlist) -h(human readable) /(directory to call the list command on) |(pipe output into) sort(call the sort command)

To make the output easier for sort to work with, we will have to call on another command caller "tr" (Translate)

Let's make the output a little easier for the computer to interperet.

```
ls -lh / | tr -s " " ","
```

Let's break that down!

ls(call list command) -l(longlist) h(human readable) /(directory to call the list command on) |(pipe output into) tr(translate) -(squeeze repeats of) " "(what repeats of to squeeze) ","(what to replace the squeezed characters with)

Use man (Manual) to see other ways tr can be used.

```
man tr
```

This might look like a mess to us humans, but the computer likes it this way.
The next code block will not do much if you try to copy it into a terminal.
To insert a tab, we need to escape a tab. To do this, we press "Ctr+v"
The command will look something like this:

```
ls -lh  / | tr -s " " "(ctrl+v)(tab)"
```

Let's break that down!

ls(call list command) -l(longlist) -h(human readable) /(what directory to call list command on) |(pipe output into) tr(call the translate command) -S(squeeze into) " "(What to squeeze into) "(ctrl+v)(tab)"(what to replace the squeezed characters with)

Do not copy that. 
Physically press the keys that are in brackets

Doing this will make the output nice for the computer to read and nice for humans too.
Kind of a nice middle ground.

Now we can pipe this into sort and have an output that is not incorrectly sorted.

```
ls -lh  / | tr -s " " "(ctrl+v)(tab) | sort -t "(ctrl+v)(tab)" -k 9
```

Let's break that down!

ls(call list command) -l(longlist) h(human readable) /(root directory) |(pipe output into) tr(call translate command) -S(squeeze into) " "-S(squeeze into) " "(What to squeeze into) "(ctrl+v)(tab)"(what to replace the squeezed characters with) |(pipe output into) sort(call the sort command) -t(indicate fields separator) "(ctrl+v)(tab)"(the field separator we have indicated) -k(sort via column) 9(column number to sort to)

## cut

Ok but what if we don't want to see all the output, but only one part?
We use cut to only show certain data and leave the rest out.

Let's only look at the file sizes of this output.

```
ls -lh / | tr -s " " "(ctrl+v)(tab)" | sort -r -t "(ctrl+v)(tab)" -k 9 | cut -d "(ctrl+v)(tab)" -f 5,9
```

Let's break that down!

ls(call list command) -l(longlist) h(human readable) /(root directory) |(pipe output into) tr(call translate command) -S(squeeze into) " "-S(squeeze into) " "(What to squeeze into) "(ctrl+v)(tab)"(what to replace the squeezed characters with) |(pipe output into) sort(call the sort command) -t(indicate fields separator) "(ctrl+v)(tab)"(the field separator we have indicated) -k(sort via column) 9(column number to sort to) |(pipe output into) cut(call the cut command) -d(delimiter for separation of information is to be set to) "(ctrl+v)(tab)"(what the delimiter needs to be set to) -f(fields to be selected for viewing is to be specified) 5,9(fields to view specified)

Use man (Manual) to see other ways cut can be used.

```
man cut
```

## Conclusion

Ok. This was a little bit advanced.
But if you followed the steps correctly, you just made a small program.
Congratulations! You are now officially a programmer.

We learned that we can use sort to sort output, translate to translate output to make it easier for a computer to work with and cut to only see the output that we need.