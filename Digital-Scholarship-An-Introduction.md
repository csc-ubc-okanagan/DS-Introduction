# Digital Scholarship: An Introduction

## Outline

This 2 hour workshop will introduce you to 3 popular tools and some conceptual approaches to digital scholarship. The end product will be a static webpage, a place that you can use to communicate and disseminate your scholarly outputs.

We will not be programming and we will not be writing html. But we will use the command line and publish a web page. This is a low barrier workshop ideal for those who are interested in digital workflows that will stand the test of time, reflect best practices in document structure, and leverage version control for both recovery and transparency, but are not sure where to start.

We will start by seeing what it's like to go mouse free, using the command line interface to navigate our computer and create new files. We will then learn the basics of markdown, an alternative to using Microsoft Word to build beautiful looking documents that are grounded in plain text. Lastly, we will publish our markdown document to the web using GitHub and GitHub Pages.

This work shop will set the stage for further exploration into navigating and exploring the files on your computer, authoring documents in flexible, persistent formats, and sharing your outputs wether for an academic CV, conference poster session, or just for fun. 

**What you will need**

* A computer. Neither a tablet nor cell phone will suffice. Don't have a laptop? Grab one from the library.

That's it. We'll set you up with everything else during the workshop.

## Before We Begin

*15 Minutes*

* Install [Typora](https://typora.io/)
* Install [Pandoc](https://pandoc.org/installing.html)
* Set up Windows 10 for linux command line tools

[Originally posted on StackOverflow](https://stackoverflow.com/questions/36352627/how-to-enable-bash-in-windows-10-developer-preview/36465000#36465000)

1. Click the Start button , click Control Panel, click Programs, and then click Turn Windows features on or off
2. Enable Windows Subsystem for Linux
3. To get Bash installed, open Command Prompt (Click Start, enter cmd) and type \"bash\"

* Set up a [GitHub account](https://github.com/)

## Overview

### Command line

* Describe the terminal, shell and bash / zsh

**Tasks**

* Windows, enable bash (https://stackoverflow.com/questions/36352627/how-to-enable-bash-in-windows-10-developer-preview/36465000#36465000)

**Commands**

Find out where you are

* pwd

List the files in your current diretory

* ls

Move to a new location. We'll move to our Desktop.

* cd

Create a new file.

* touch

Talk about file naming

* Names should be meaningful, they should describe the project and the contents of the file. They should have a system for tracking through time, whether with revision numbers or dates - sometimes dates are more relevant, sometimes revision numbers are more relevant.

Rename the file to give it a meaningful name

* mv

Copy the file to give it a revision number

* cp

Delete the original

* rm

### markdown

* Describe markdown and the process of migration from plain text to html, pdf, docx

**The Ethos of Markdown**

There are a couple of things that make markdown stand out as a tool for authoring documents. The first is that it is plain text. The second is that separates document structure from document styling.

Plain Text

Plain text files are files that contain only text characters, that is, only readable characters with no additional information encoded in them, no formatting, no images etc. This in effect means that any a plain text file can be opened by any text editing program on any computer on any operating system. This also means that plain text files are very future proof; a plain text file written in the 1980s can still be opened on your computer and will still be able to be opened in another 10 or 20 years.

This is quite different from say a document written in Microsoft Word, which only renders perfectly in Word and only in versions of Word that support that particular document's formatting. This kind of rot, or inability to access content, has plagued authors for decades, especially when there was a lot more competition among word processors.

If we were to try and open a Word document in a text editor, this is what we'd see:

**Image** 

Structure vs Styling

When an authoring environment separates out structure from styling, it allows us to focus on each independently of the other, encouraging the writer to focus first and foremost on what they want to say and then subsequently on how this will be formatted.

Editors like Microsoft Word of LibreOffice, for example, wed these together so that styling - fonts, colours, spacing around elements, page breaks etc - are part of the writing process.

Markdown encourages the writer to think only about document structure and prose while writing - that is, should this be a heading, subheading, list, table etc - and to look at how these elements are formatted once writing is complete - 1st level headers should 16pt Helvetica bold, tables should span the full width of the page, list items should be preceded by bullets not dashes etc.

**How Markdown Works**

1. You write your content, providing the structure and the prose
2. Another program adds style to your content and encodes it in a particular format, whether that be for the web, as a pdf, or a Word document.

Your working copy is your plain text markdown document. Your distribution copy is the the stylized, formatted version.

**The History of Markdown**

Markdown was first conceived as a tool to support web authoring. Writing html for web documents is a potentially onerous task. html, like markdown, is a plain text format. If you right click in your web browser and select \"View Page Source\" or the equivalent, you'll see the html markup that was written. Your web browser takes that marked up content and gives it style, formatting it so that it's (hopefully) enjoyable to interact with.

Markdown is consequently a very quick way to author documents. It's formatting options though are somewhat limited by its original intent to author web based prose. That being said, web based prose was originally designed to support the dissemination of academic research. So markdown is a perfect tool for authoring in academia.

* Overview of the basic elements of a markdown document

**Basic Structural Elements of Markdown**


  * headings
  * lists
  * links
  * tables
  * images

**Activity**


* Open our markdown document in a plain text editor - notepad or notepad++ on a PC, TextEdit on mac
  * open -e filename (mac)
  * ? (pc)
* Have some pre-populated content somewhere that we can format.

**Pandoc**

There are several different applications that are able to convert your marked up, plain text document, into a formatted document. We'll look at a couple of these, and in so doing, also become a little more familiar with the command line.

Pandoc is an amazing document conversion tool; there is virtually no document format that Pandoc cannot handle. Pandoc does not have an interface that we can interact with the point and click of a mouse. We access it exclusively through the command line. We're not going to explore it in depth here, we're just going to work through one example of what we can do with our markdown document.

Pandoc, at its simplest take two arguments, the name of an output file and the name of an input file. The input file is the file you've created and will include the file type designation, that is <code>.md</code> The output file name will be whatever you wish to call the new file and will include the file type designation that you want to convert to. To keep things simple, we'll keep the same file name. And since we're planning on publishing to the web, we'll convert this to html using the file ending <code>.html</code>

The formula is

```
pandoc -so outputFile inputFile
```

The <code>-so</code> ensures that we have a stand alone html web page that is sent to a file. The details of this are of little consequence at this stage, but we can discuss further if people are interested.

```
pandoc -so myfile.html myFile.md
```

Now that we've done the conversion, let's look at the product!

**Typora**

When it comes to applications in which we can author markdown documents, all you need is a plain text editor that comes packaged with your operating system.

There are, however, numerous applications that allow you to interact with your content in different ways. One that I like to use exclusively for writing prose is Typora, which does live rendering of your markdown content. In fact, this content was all written using Typora, but was rendered to html using RMarkdown which uses Pandoc, and then published to GitHub pages.

Let's take a quick look at what our content looks like in Typora

Mac

```
open -a Typora myFile.md # open file in Typora
```

PC

```
? myFile.md
```

There are numerous other markdown editors out there. You can access a comprehensive list from the [Markdown Guide](https://www.markdownguide.org/tools/).

Three others which I think are worth noting in terms of how they use markdown to implement some interesting authoring formats include

**Obsidian** which build a network mind map of all the documents that you author it allowing you to easily connect documents

**Joplin** which is designed for note taking and takes elements from EverNote or OneNote and implements them in markdown

**Atom** which is a popular text editor for all kinds of editing and coding and provides you with a side by side window to see your raw markdown content alongside a formatted rendition.

## GitHub Pages

### How GitHub Pages Works

In the same way that we converted our markdown document to html using Pandoc, GitHub pages uses another application called Jekyll to render your markdown files as html. And Jekyll requires much less work to get a nice, functional webpage.

A note on how web pages work. The landing page for any website is always called <code>index.html</code> This is a web authoring standard. GitHub Pages and Jekyll thus require that your landing page markdown document be called <code>index</code>, but we're working in markdown, so we'll call it <code>index.md</code>

Let's do that now in our terminal...

```
mv myFile.md index.md # rename to index.md
```

### Moving into GitHub

Let's log in to our [GitHub account](https://github.com/).

We'll now create a repository. We're going to strictly engage with GitHub as a web authoring tool at the moment. GitHub is, first and foremost, and web based implementation of the version control system Git, which is brilliant, but a workshop for another day.

So after setting up our repository, we'll select the link to \"upload an existing file\" and we'll upload out index.md file. Now it's just a matter of a couple of settings!

_config.yml

```
theme: jekyll-theme-cayman
title: Mathew's Page
github:
  is_project_page: false
```









readme file