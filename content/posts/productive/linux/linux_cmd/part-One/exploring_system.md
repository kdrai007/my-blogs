---
title: "exploring_system"
draft: false
---

tag : #linux #navigation 

# Exploring the system

## Commands

- ls - List direcotory content
- file - Determine file type
- less - View file content

### Having more fun with ls

The ls command is probably the most used command, and for a good reason

- We can ast ll types of contents in director using ls command 
- for example:
  ```sh
  $ ls Downloads/
  music.mp4 file1.png file2.jpeg

  $ ls Downloads/ Documents/
  Downloads:
  music.mp4 file1.png file2.jpeg 
  Documents:
  file1.pdf file2.pdf
  ```

- We can change format of the output to reveal more details
  - By adding "-l" to the command, we changed the output to the long format
```sh
$ ls -l

total 56
drwxrwxr-x 2 me me 4096 2017-10-26 17:20 Desktop
drwxrwxr-x 2 me me 4096 2017-10-26 17:20 Documents
drwxrwxr-x 2 me me 4096 2017-10-26 17:20 Music
drwxrwxr-x 2 me me 4096 2017-10-26 17:20 Pictures
drwxrwxr-x 2 me me 4096 2017-10-26 17:20 Public
drwxrwxr-x 2 me me 4096 2017-10-26 17:20 Templates
drwxrwxr-x 2 me me 4096 2017-10-26 17:20 Videos
```

#### Options are Arguments

This is very important point aobut how commands work, commands are often followed by one or more options that modeify  their behavior.

 command -options arguments 

- Most commands use option which consist of a single character preceded by dash like "-l" 
- Some common example:
  - `ls -lt --reverse` list the content of directory *-l* for long format and *-t* for sort file according to time and *--reverse* reverse the output of command

>Command options like filename in Linux, are case-sensitive

### Determining a File's type with file

As we explore the system it will be useful to know what file contains 

- Filenames in linux are not required to reflect a file's content.
- A Filename "photo.jpg" would normally be expect to contain jpeg compressed image , it is not required in linux 
- So, to determine type of file we use `file filename` command

```sh
$ file picture.jpg
picture.jpg: JPEG image data, JFIF standard 1.01
```
### Viewing file contents with less

The less command is a program to view text files.

- In Linux system there's are various human readable files, which we can read with *less* command 
- for example:
  - if the file is longer than one page,we can scroll up and down to exit *less*  press the "q" key

  ```sh
$ less /etc/passwd
  ```

### Symbolic Links

A symbolic link contains a text string that is automatically interpreted and followed by the operating system as a path to another file or directory.

`lrwxrwxrwx 1 root root 11 2007-08-11 07:34 libc.so.6 -> libc-2.6.so`

- Notice how first letter of listing "l" seems to have two filenames  this is special kind of files called Symbolic Link







