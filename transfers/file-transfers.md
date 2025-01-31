---
title: File Transfers
layout: default
nav_order: 2
parent: Transfers
---

# File Transfers
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Introduction

Born digital collection material can be acquired through file transfer or forensic imaging. Most material will be transferred using a Bagit script through command line.

The file transfer workflows are detailed in this document. The workflows may vary based on media types and file types.  

**Before a media object can be transferred it first must be recorded in the collection’s media log in CMS. See [Verifying inventory in Media Log](/digarch/transfers/verify-inventory.html){:target="_blank"} for instructions.**

## Prepare destination folders for files

**These instructions show you how to prepare destination folders for a number of consecutive disks. Consider using a one-line command to create directories if the disks you are packaging do not have consecutive MediaID numbers or you are only transferring one media object.**  

* Run [makesips script](../software#makesips-script){:target="_blank"} to create a consecutive number of submission information packages for material from digital media.
  
On Windows:

* Start Cygwin from the desktop. A terminal like screen should appear.

![](media/image2.png)

On Mac:

* Open Terminal.
* Connect to ARCHV Mac.  
```$ ssh archv```  
* Change to fileTransfers directory.  
```$ filetransfers```
* Create a directory for your collection if it does not exist.  
```$ mkdir M1111```  
* Change into your collection directory.  
```$ cd M1111```  
* Run the program to build structured directories. The program will ask you for your collection name and the first and last number of items of the directories you’d like to build.  
```$ makesips```  

![](media/image8.png)

Or

* ``mkdir`` command can be used to create directories. This works when media aren't consecutively numbered. 0001 to 0009 require a different line from 0010 on.
* Change to fileTransfers directory.  
```$ filetransfers```
* Enter ```mkdir``` command.  
```mkdir -p CollID/Media-000{1..9}/{metadata/submissionDocumentation,objects}```  
```mkdir -p CollID/Media-00{10..99}/{metadata/submissionDocumentation,objects}```  
```mkdir -p CollID/Media-000{1,5,7,9}/{metadata/submissionDocumentation,objects}```  

### Directory structure

* /M2319-0021
  * /metadata
    * /submissionDocumentation
  * /objects

## Transfer files from media object

Files that have been updated by the donor within the past 30
 days should be quarantined for 30 days to ensure that
 all virus definitions are up to date.

* Use a write-blocker to connect the drive to the computer. See [Using Tableau Write Blockers](/digarch/transfers/using-tableaus.html){:target="_blank"} for instructions.  
* Run [ft.sh](../software#ftsh){:target="_blank"} to create a transfer package.

On Windows:

* Start Cygwin from the desktop. A terminal like screen should appear.

![](media/image2.png)

On Mac:

* Open Terminal.
* Enter the alias ```FT``` and hit return.

Or

* Enter ```/usr/local/bin/ft.sh``` and hit return if the alias is not set.
* Drag the destination directory from the media object to the window and hit return as prompted.
* Enter the MediaID for the file transfer and hit return.


Deprecated
{: .label .label-red }

* Copy the number of files in payload and the size of payload in kb when displayed in the window.
* Paste the number of files and the size in the File Transfers section of the media log in CMS.

### FT.sh
<script id="asciicast-mKpfPqUl74R3t30B0tvpfPBQV" src="https://asciinema.org/a/mKpfPqUl74R3t30B0tvpfPBQV.js" async></script>