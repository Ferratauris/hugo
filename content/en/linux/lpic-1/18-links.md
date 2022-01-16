---
title: "18 Links"
date: 2022-01-07T20:10:06+02:00
description: "How can we reference a location on a filesystem?"
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

## Links

Sometimes we need links.
Links are files that just point to another file or location on your filesystem.
These serve as a good shortcut when a filename is especially long or when a version of a file changes, but we do not want to memorize the full name or path. 
We create a link to make it easier to access a location on a filesystem.

Links come in 2 different variations:

* Hard links: These point to the physical Inode on your filesystem. This means that These can not be used to link to directories or on a device other than where the physical Inode is stored. (The link needs to be on the same storage media volume/partition).
These type of links are more effective.

* Symbolic links/ soft links: These links point to a path. This means that they can point to directories or on locations that are not on the same storage media volume.
They are also less effective.

## Hardlinks

We are going to create a hard link first.
Essentially, when a file is created, the data is written to the hard drive and a hard link is created.
When we interact with a file, we actually interact with the link.
The data will stay on the storage media as long as there is still a hard link connected to it.

Well first, we are going to need something to link to.
So let's first make a file.


```
echo "this is some text" >> ./newfile.txt
```

Let's break that down!

echo(call the echo command which prints input to the output) "this is some text"(The input that we want printed) >>(Redirect and append output to) ./newfile.txt(Location to redirect and append output to)

Use man (Manual) to see other ways echo can be used.

```
man echo
```

Now let's create our first symbolic link!

```
ln newfile.txt newname.txt
```

Let's break that down

ln(Calls the link command which created links to locations) newfile.txt(the file we want to create a link of) newname.txt(The link we are creating)

Use man (Manual) to see other ways ln can be used.

```
man ln
```

As was said previously, the data on the storage media will remain as long as there is a hard link connected to it.

Let's test that

```
rm newfile.txt
```

Let's break that down!

rm (calls the remove command) newfile.txt(The file we want to remove)

Use man (Manual) to see other ways rm can be used.

```
man rm
```
Now let's check the contents of the new linked file!

```
cat newname.txt
```

Let's break that down!

cat(Calls the concatenate command which can be used to display contents of a text file in the standard output) newname.txt(The file we want to concatenate)

Use man (Manual) to see other ways cat can be used.

```
man cat
```
As you can see, The data is still there even though the file was deleted.

### Symbolic/ soft links

Now let's use the new file we created and create a symbolic link.

```
ln -s newname.txt newfile.txt
```

Let's break that down

ln(Calls the link command which created links to locations) -s(softlink toggle) newname.txt(the file we want to create a link of) newfile.txt(The link we are creating)

Use man (Manual) to see other ways ln can be used.

```
man ln
```

Let's test that

```
rm newname.txt
```

Let's break that down!

rm (calls the remove command) newname.txt(The file we want to remove)

Use man (Manual) to see other ways rm can be used.

```
man rm
```
Now let's check the contents of the new linked file!

```
cat newfile.txt
```

Let's break that down!

cat(Calls the concatenate command which can be used to display contents of a text file in the standard output) newname.txt(The file we want to concatenate)

Use man (Manual) to see other ways cat can be used.

```
man cat
```

As you can see, The file is no longer found as the original file was deleted.

## Conclusion

* Hardlinks are links that point to physical data on a storage media volume.
* Softlinks are links that point to a location on your filesystem.
* To create a link, we use the ln command.