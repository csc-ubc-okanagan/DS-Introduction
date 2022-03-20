---
title: "Abandoning the mouse"
---

Why learn to use the command line?

* For many, it will be something you encounter willingly or unwillingly as part of academic life at some point
* It\'s fast for those tasks that are repetitive, like bulk renaming or moving of files.
* You can talk to the person who works for IT at your next party

## Working on a server

There was a time when we couldn\'t point and click. In fact, in many disciplines, it remains imperative that users know how to navigate an operating system without a graphical user interface and a mouse.

Anyone who works with Advanced Research Computing and is asking for server space to deploy a web site or process data will be provided with a an operating system that shares resources with other users. So, there\'s no physical computer, no monitor, no keyboard, no mouse. Not in the way that we\'re used to. Just a bit of space on a server reserved for them that they access from their local machine over a local network or Internet connection.

Additionally, when this operating system using shared resources is spun up, it will likely be a Linux distribution, like RedHat, CentOS, or Ubuntu. So having the skills to move around these systems is important.

## Making this faster

The command line isn\'t just useful for navigating a computer when we don\'t have a graphical, interactive view of what\'s going on. Whenever you find yourself doing something over and over with your mouse and you think \"there must be a faster way of doing this\", odds are there is. If what you\'re doing involves moving files around, joining files together, making the same small edit to a bunch of files etc, Unix and Linux command line tools can save you much time and many headaches.

## The Unix Command line

We (and the good people of the internet) will be throwing around a lot of jargon, so we\'ll start with a few definitions.

### Terminal, Console, Command line, Shell

What\'s the difference?

For all intents and purposes in daily conversation, they\'re synonymous. For the more nuanced participant, however, and so we can sound a bit smarter at that next party where we've found ourselves at the punch bowl with someone in IT, `terminal` refers to the text based environment that sits between you--the user--and your computer--the hardware. It\'s more conceptual than it is real. A `console` is the physical manifestation of a `terminal`. The `command line` simply refers to the space to the right of your command prompt when you\'re in your console; ie the space available for you to type. A `shell` is an application that interprets what you type into your `console's` `command line` and passes this along to the relevant application that will handle what you\'ve typed.

So, you **work** on a `console`, where you **type** on the `command line`, and what you type is **interpreted** by the `shell`

### What is Bash?

Bash stands for Bourne Again Shell. Bash is one `shell` application. There are others. Mac OS defaults to `zsh` the Z shell. They both do the same thing; they interpret what you type in the `command line`. It\'s kind of like choosing Zotero over Mendeley, or LibreOffice over Microsoft Word. Different applications, same basic job. For what we\'re doing today, it won\'t make a difference which one your computer defaults to.

## Summary of commands

We\'ll review using the following commands today...

```bash
pwd # print working directory
ls # list the files in a directory
cd # change directories
mkdir # make a new directory
touch # create a file
mv # move or rename a file
cat # print out the contents of a file
less # paginate through the outputs of cat
curl # access files on the web
open # open a file
```

## Putting it into Practice

Find your console...then

### Basics of navigation

Find out where you are:

```bash
pwd
```

Get ourselves to the same place in our respective operating system

```bash
cd ~/Desktop
```

Note: the `~` returns your home directory. This is generally your user directory by default.

Assuming you have some files sitting on your desktop, list those

```bash
ls
```

Note: all command line applications include `flags`. These provide access to additional options. They are pre-pended with a `-`.

List the files again, but with a bit more information using the `l`--for long format--flag.

```bash
ls -l
```

And just for fun, the `h`--for human readable--flag as well.

```bash
ls -lh
```

### Creating new files

Create a new folder to work in on your Desktop (which is where we should all be at the moment.)

```bash
mkdir 2022_DHSI-Conference
```

Note: Once you create this folder, open it beside your console window and you\'ll be able to see it updated as you work.

Put yourself in that folder

```bash
cd 2022_DHSI-Conference
```

Create a new file that will ultimately become our webpage.

```bash
touch myNewFile.md
```

**File Naming**

Names should be meaningful, they should describe the project and the contents of the file. They should have a system for tracking through time, whether with revision numbers or dates--sometimes dates are more relevant, sometimes revision numbers are more relevant. When dates are used, they should be in the format **yyyymmdd**. They should contain no special characters, this includes spaces. Parts of file name--dates, affiliated project, description--should be joined with underscores `_`, while multiple terms within a part can be in `CamelBack` or separated with dashes `-`.

File naming diatribe done, rename the file we just created to give it a meaningful name

```bash
mv myNewFile.md 20220323_DHSI-Poster_Web-Materials.md
```

Note: `mv` both moves files from one location to another and renames files, which is akin to moving.

Every directory should have a `README` file in it, so let\'s make one of those

```bash
touch README.md
```

### Retrieving remote files

We still need to get our poster template from UBC IT.

```bash
curl https://it.ubc.ca/sites/ubcit.ubc.ca/files/ubc_research_poster_template.ppt -o 20220323_DHSI-Poster.ppt
```

Note: we use the `o`--for output--flag to name the file to put the download into.

We now have the basics lined up; we can move around our computer without a mouse, and we\'ve created some placeholders documents for the content we\'re about to start building out.

## Deeper Dive

### Revisiting Speed

Many things we do on the computer are tedious. Whenever we\'re doing something that is tedious, we should be thinking to ourselves, there\'s got to be a better way of doing this. And there will be. It\'s just a matter of knowing who or what to ask.

### An example

We may well come upon a time when we need to move, delete, or rename a large number of files associated with a project. Let\'s touch down a list of a series of files:

```bash
touch this.tmp that.tmp who.tmp why.tmp where.tmp what.tmp
```
**File Extensions**

File extensions are simply another part of a file name that helps us and our operating system know what application it is that we expect to use to open a file. We can change file extensions and all we change is the file name, we don\'t change anything intrinsic about the file itself. `.tmp` is a common file extension used for plain text files that are temporary in nature and meant to be deleted frequently, or at least not held onto for any length of time.

Now, we might realize that we meant to put these in their own directory. Let\'s make that directory and move everything over, move ourselves over and then investigate things.

```bash
mkdir tmp
mv *.tmp tmp/
cd tmp
ls
```

Note: the `*` is a wildcard and tells `mv`, move anything that ends in `.tmp`

Not a huge time saver, but things get better. We really should have provided these files with a bit more context in their file names, like the project that they\'re affiliated with. We could rename each individually, or harness the power of the command line...

```bash
# for every instance of a file that ends in .tmp;
# do the following: rename that file so that is pre-pended by 'My-Research-Project'
# stop doing things
for i in *.tmp; do mv $i 20220323_DHSI-Poster_$i; done
```

We can also now bulk delete those files

```bash
rm *.tmp
```

And do a final clean up, moving ourselves up one level and deleting our `tmp` folder

```bash
cd ..
rm -R tmp
```

Note: Every folder has in it two place holders, one labeled `.` and the other labeled `..`. `.` refers to the current directory, while `..` refers to the directory one level up in the hierarchy. To see these listed, you can call `ls` with the `a` flag.

Next, we look at Markdown...
