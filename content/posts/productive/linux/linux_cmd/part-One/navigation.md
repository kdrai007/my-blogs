---
title: "navigation"
draft: false
---

Tag : #linux #terminal #navigation

# Navigation in CLI

- Most basic thing to learn in linux cli is how to navigate between files

- **Some navigation commands**
  - pwd - Print name of current working direcotry
  - cd - change directory
  - ls - list directory content

## Present Working Directory(PWD)

At any given time, we are in single directory and see contents in the diectory and the pathway to the directory above us(called the parent dir).

- To display the the working dir we can use use *pwd* 
```sh
$ pwd
/home/me
```

- When we first log in to our system our current working dir is to set to *home dir*, Each user is given their own home directory

## Listing the content of the folder(LS)

To list the files and contents of current dir, we use the *ls* command

```sh
$ ls
Documents Downloads Videos Images
```

- Actually, we can use the ls command to list content of any dir not just working dir

```sh
$ ls Downloads
a.jpeg go.pdf basic_docker.pdf
```

## Changing the Current Working Directory

To change our working dir we use the *cd* command 

```sh
$ cd Downloads
$ pwd
/home/me/Downloads
```

- **Aboslute Pathname** - An absolute pathname begins with the root directory and follows the tree branch by branch until the path to the desired directory or file is completed

```sh
$ cd /usr/bin
$ cd /usr
$ pwd
/usr
```

- **Relative Pathname** - Where an absolute pathname starts from the root directory and leads to its destination, a relative pathname starts from the working directory


```sh
$ cd /usr/bin
$ cd .. 
$ pwd
/usr
```


