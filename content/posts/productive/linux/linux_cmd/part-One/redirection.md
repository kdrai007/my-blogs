---
title: "redirection"
draft: false
---

Tag : #linux #command_line #redirection #bash

# Redirection

"I/0" redirection the "I/O" stands for input/output and with this facility we can redirect the input and output command to and from files, as well as connect multiple commands togehter into powerful command *piplines*

## Used command in the chapter

1. cat - Concatenate files
2. sort - Sort lines of text
3. uniq - Report or omit repeated line
4. grep - Print lines matching a pattern
5. wc - print newline,words
6. head - output the first part of file
7. tail  - output the last part of file
8. tee - Read from standard input and write to standard output and files

## Standard Input, Outpue and Error

Many of the program that we used already produce some kind of output.This output may often consist of two types:

- The program's result,that is, the data program designed to proudce
- Status and eror message that tell us how the program is getting along

I/O redirection allows us to change where output goes and where input comes from. Normally,output goes to the screen and input comes from keyboard,but with I/O redirection we can change that

### Redirecting Standard Output

`$ ls -l /usr/bin > ls-output.txt`

- Here, we created a long listing of the `/usr/bin` directory and sent the result to the file `ls-output.txt`  now the .txt file contains the output of `ls /usr/bin` command,we can check the .txt file using  `less`
`$ less ls-output.tx`

- `>` this command will replace old data with new one, so to persist old data with new data we can use `>>` this double arrow will append the new output to `ls-output.txt file`

`$ ls -l /usr/bin >>ls-output.txt`

### Redirecting Standard Error

Redirecting standard error lacks the ease of dedicated redirection operator. To redirect a standard error we must refer ot its *file descriptor*

- A program can produce output on any of several numbered file streams 
- The first three of these file streams as *standard* input ,output and error 
  - the shell reference them internally as *file descriptors* 0,1 and 2

- Since standard error is the same as file descriptor number 2, we can redirect standard error with this notation,
`$ ls -l /usr/user 2> ls-error.txt`

- **Redirecting standard output and error to same file**
  - There are cases when we want to catch all types of output to a single file
  - to do tis we can run this command,

 `$ ls -l /usr/user >ls-output.txt 2>&1`

>Note:  This is old method which worked with old verisons of shells

Recent version of *bash* provide a second ,more streamlined method for performing this combined redirection 

`$ ls -l /usr/user &>ls-output.txt`

#### Disposing of Unwanted Output

Somtimes 'silence is golden' and we don't want output from the command,we just want to throw it away 

- This applies particularly to error and status messages
- To suppress error messages from a command, we do this:

`$ ls -l /usr/user 2>/dev/null`

- `/dev/null` file is a system device reffered to as bit bucket, which does accept input and does nothing with it

### Redirecting standard Input

#### cat - Concatenate files

The cat commands read one ore more lines and copies them to standard output like this:
`$ cat [files..]`

- for example this command will display the output of `out.txt` file

```sh
$ cat out.txt
there nothing to concatenate
```
- `cat` is often used to display short text files.
- Since `cat` can accept more than one argument, it can be used to join file together
  - say we have donwloaded a large file that has been split into multiple parts (multimedia files are often split this way on Usenet) and we want to join them togehter if the wile were named,
    `movie.mpeg.001 movie.mpeg.002 movie.mpeg.003 ...movie.mpeg`

   `$ cat movie.mpeg.0* >movie.mpeg`

   - Since wildcards always extend in sorted order, the argument will be sorted in correct order 

- `$ cat < ls-output.txt`
- By using `<` redirection operator, we change the source of standard input from keyboard to the file `ls-output.txt`


### Pipelines 

The capablity of commands to read data from standard input and send to standard output is utilized by shell feature called *pipeline*

- Using the `|` operator (vertical bar), the standard output of one command can be piped into the standard input of another
`command1 | command2`

example,

`$ ls -l /usr/bin | less`

### Filters

Pipelines are often used to perfrom complex operations. It's possible to put serverl commands togehter to perform some kind of operations, for this we can use various kind of filters like,

- Here we used `sort` program to sort the output of `ls` command and then pipe it to `less` command
`$ ls -l /bin /usr/bin |sort |less`

#### uniq - Report of Omit Repeated files

`uniq` command if often paired with `sort` command.`uniq` accepts sorted list of data from standard output or a single filename argument and, by default remove any duplicate item from list 

`$ ls -l /bin /usr/bin |sort |uniq |less` 

- This whole command wil first list files in `/bin` and `/usr/bin` folder and then with `sort` command it will be sorted then with `uniq` command all the duplicates file will be removed and then with `less` command user can see the output

- and if we only want to see duplicates files we can use `uniq -d` instead of just `uniq`

#### wc - Print line, words and byte counts

The wc(word count) command is used to display the number of lines,words and bytes contained in files

example,

```sh
$ ls -l /usr/bin | wc -l 
2024
```

- This example's output is containling total lines of the standard output of command `ls -l /usr/bin`

#### grep - print lines matching the pattern

`grep` is a powerfull program used fo find pattern within files it's used like this: 

`$ grep pattern [file...]`

- When `grep` encounter pattern in the file it's print out the line containing it.

example,

```sh
$ ls -l /usr/bin | sort | grep zip
zip
gzip
unzip
```
There are couple of handy options for grep:

  - `-i`, which caused `grep` to ignore case while searching through files  
  - `-v` , which tells grep to print those lines where pattern isn't a match

#### head/tail - Print first/last part of files
 
Sometimes we don't want all output of files,that's when we use these commands `head` and `tail`
  - The `head` commands prints first few lines of file
  - The `tail` commands prints last few lines of file
- By  default,both commands output can be adjusted by this `-n` option
- Generally they print first/last 10 lines of file

`$ head -n 5 file.txt`
`$ tail -n 5 file.txt`

or,by using pipelines

`$ ls -l /usr/bin | head -n 5`

>`tail` has an option which allows us to view files in real time. This is useful when watching progress of log files by using `-f` option


#### tee - Read the stdin and Output to stdout of files

It splits the output so that it can be viewed on the terminal while being saved to a file.

`$ command | tee [options] file_name`

example,

`$ echo "New line" | tee -a output.txt`

















