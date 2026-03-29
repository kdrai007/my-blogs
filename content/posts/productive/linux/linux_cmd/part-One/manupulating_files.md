---
title: "manupulating_files"
draft: false
---

Tag : #linux #commands 

# Manupulating Files and Directories

## Used commands in this chapter

- cp - copy file and folder
- mv - move file and folder
- mkdir - create a directory
- rm - remove file and directory
- ln - create symbolic links


- These five and mostly used commands and used for manupulating files and directories
- To show how powerfull these commands are for ex:
  `$ cp -u *.html ~/location`
  - This command will copy all hmtl files to location folder
  - But there's a catch it will only copy those files that's not in location folder and update old version of those files with new one

### WildCards

| wildCards     | Meaning                                                   |
| ------------- | --------------------------------------------------------- |
| *             | matches any character                                     |
| ?             | matches any single character                              |
| [characters]  | matches any character that is member of the set character |
| [!characters] | opposite of previous one                                  |
| [[:class:]]   | matches any character that is memmeber of specified class |

- **WildCard Examples**

| Pattern                | Matches                                                                       |
| ---------------------- | ----------------------------------------------------------------------------- |
| *                      | All files                                                                     |
| g*                     | Any file beginning with “g”                                                   |
| b*.txt                 | Any file beginning with “b” followed by any characters and ending with “.txt” |
| Data??                 | Any file beginning with "Data" followed by exactly three characters           |
| [abc]*                 | Any file beginning with either an “a”, a “b”, or a “c”                        |
| BACKUP.[0-9][0-9][0-9] | Any file beginning with “BACKUP.” followed by exactly three numerals          |
| [[:upper:]]*           | Any file beginning with an uppercase letter                                   |
| [![:digit:]]*          | Any file not beginning with a numeral                                         |
| *[[:lower:]123]        | Any file ending with a lowercase letter or the numerals “1”, “2”, or “3”      |

- Wildcards can be used anything which accepts filename as arguments

### mkdir - Create Directories

The mkdir used for createing directories. for ex:

`$ mkdir dir1 dir2`

- this command will create two diretories named "dir1" and "dir2"

### cp - copy files and Directories

The cp command used for copying files to another location

`$ cp file1 ~/location`
`$ cp file1 file2 file3 ~/location`
`$ cp *.txt ~/location`

- cp commands can work for single or multiple files
- "*.txt" this wildcard will allow copy of all txt files to location folder

- use `$ man cp` for more info on cp
- or use `$ cp --help` this command will provide short and simple help descriptions

### mv - move or rename files and directories

This mv command is used for moving or renaming files and folder

`$ mv file1 ~/location`

- this command will move file1 to location folder

`$ mv file1 renamedfile`

- This command will rename this file named "file1" to "renamedFile"
- for further instruction either use `$ man mv` or `$ mv --help` in your command line

### rm - remove files and directories

`$ rm file1`

- This command will remove file1 for your system

>Be carefull, with rm you can't undone anything after using this command 

### ln - Create Links

The ln command is used for creating either hard link or symbolic link



#### Hard Links

Hard links are original way of unix for creating links,compare to symbolic links which are more modern

- By default, every file have a single hard link that gives the file its name.
- A hard link can't reference a file outside of its own filesystem
- A hard link may not reference a directory

`$ ln file link`
- This command will create hard link

##### way to recognize hard link:-

- With the help of `ls -li` command we can see some important info

```sh
$ ls -li
total 16
12353539 drwxrwxr-x 2 me me 4096 2018-01-14 16:17 dir1
12353540 drwxrwxr-x 2 me me 4096 2018-01-14 16:17 dir2
12353538 -rw-r--r-- 4 me me 1650 2018-01-10 16:33 fun
12353538 -rw-r--r-- 4 me me 1650 2018-01-10 16:33 fun-hard
```
- If you notice both file *fun* and *fun-hard* have same **inode** number `12353538` ,it's showing they are both hard links 

- After finding the *inode* number we can use this command to find all the files with same inode num.

`$ find / -inum 12353538`

#### Symbolic Links

Symbolic links were created to overcome the limitations of hard links like:

  - Hard links can't span physical devices 
  - Hard links can't reference directories, only files

- Symbolic links work by creating a special kind of file that contains a text pointer to the referenced file or directory
- If original file is deleted, then link will not work because it's pointing nothing.


`$ ln -s item link`
- This command will create symbolic link

##### Way to recognize Symbolic links:-

- it's way easier to recognize symbolic links compare to hard links

```sh
$ ln -s fun ./dir1/fun-sym
$ ls -l dir1
total 4
-rw-r--r-- 4 me me 1650 2018-01-10 16:33 fun-hard
lrwxrwxrwx 1 me me 6 2018-01-15 15:17 fun-sym -> ../fun
```

- In the given shell example, there is something out of the blue which is *->* this arrow which is refrencing to original file 
- So, it's pretty easy to find which file is original and which is symbolic link

- Just like we create symbolic link for file we can create for directories.

`$ ln -s dir link`





