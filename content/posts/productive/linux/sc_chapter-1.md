---
title: "sc_chapter-1"
draft: false
---


## Chapter 1- Shell something out

#terminal the termianl is interactive tool while user use to interact with shell environment

printf  "%-5s %-10s %-4.2f\n" 1 Sarath 80.3456 
 prints:- 
1     Sarath     80.35

### How this works

%s, %c, %d, and %f are format substitution characters for which an argument can be placed 
after the quoted format string.

where:- 
s denotes string
c denotes character
d denotes number
f denotes float number

### Envionment Variables

Envionment variables are variables that are not defined by the current procuess but the parant processes

export PATH=$HOME/.local/bin:$PATH

### Playing with file descriptors and redirection

file descriptors are intergers that are associated with file input and output.
they keep track of open file best known descriptors are stdin, stdout and stderr

--File descriptors are integers associated with an opened file or data stream. File descriptors 0, 
1, and 2 are reserved as follows:

0: stdin (standard input)
1: stdout (standard output)
2: stderr (standard error)

### Arrays and associative array

Arrays are very important component for storing collection of data as seperate entities using indexes. 
generally array can store values on number based index but in associative array we can define our indexes
like this:-

declare -A fruits
fruits=([apple]="100Rs",[orange]="200Rs")
echo fruits[apple]


 










