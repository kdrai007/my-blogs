---
title: "shell_world"
draft: false
---

Tag : #linux #commands #echo

# Seeing the world as Shell Sees it

## Used Commands

- echo - Display a line of text

### Expansion

Each time when we type command and press Enter key, `bash` performs a several subsitution on out text before it carries out our command, for instance when we use * character some commands work something else because * or wildcards sequence can have lot of meaning to the shell. The process to make this happen is called expansion

- `echo` is very simple command it prints it's text argument on standard output

`$ echo this is a test`
`output: this is a test`

let's try another example

```sh
echo *
Desktop Downloads Documents user notes codes
```

#### pathname expansion

The mechnism by which wildcards work is called **pathname expansion**

for example,

`$ echo d*`

- This command will through all the directory with  small case `d`  letter

and this,

`$ echo *s`

- This command will through all directory that's end with small case `s`

or even this:

`$ echo [[:upper:]]*`

- This command will through all direcotry with upper case

#### pathname expansion with hidden files

As we know files with period `.` is hidden in linux pathname expansion also respects that 

for example,

`$ echo .[!.]*`

- This command will through every directory with `.` as a first character


#### Arithmetic  expansion

The shell allows us to be performed by *expansion*

for example,

`$ echo $((2+2))`
`output: 4`

#### Brace Expansion

Perhpas the strangest expression is called brace expression.With it we can create multiple text strings from a pattern containing braces  

for example,

`$ echo Front-{A,B,C}-Back`
`output: Front-A-Back Front-B-Back Front-C-Back`

- Patterns to be braces extended may contain leader portion called *preamble*, and a trailing portion called *postscript*
- The braces expression may contain either a comma seperated list of strings or a range of integers or single characters 

example,

```sh
$ echo {1..15}
1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
```

- Here is a range of letters in reverse order:

```sh
$ echo {Z..A}
Z Y X W V U T S R Q P O N M L K J I H G F E D C B A
```

- Brace expansion can be nested

```sh
echo a{A{1,2},B{3,4}}b
aA1b aA2b aB3b aB4b
```

- In practical case we can use brace expansion in multiple ways 

for example,

```sh
$ mkdir {2009..2010}-{1..12}
```
- This command will create directory for year 2009 to 2010 december

#### Parameter expansion

Parameter expansion is featurs which manupulate string and variables using special character and operators

- It's a feature that is more useful in creating scripts than directly on command line
-  Some common examples of parameter expansion include:
      - `${var}` expands the value of the variable `var`.
      - `${var:-default}` expands the value of `var`, but if it is unset or empty, it expands to default.
      - `${var:=default}` expands the value of `var`, but if it is unset or empty, it expands to default and assigns default to var
      - `${var:+value}` expands to value if `var` is set and not empty, otherwise it expands to nothing
- These are just some examples

for example,

`$ echo $USER`
`output: userName`

- These `$USER` are variables which saved in system in chucks these are called *environment variables*
- We can list of vars using this:

`$ printenv|less`

#### Command subsitution

Command subsitution allows us to use output of a command as an expansion.

```sh
$ ls -l $(which docker)
-rwxr-xr-x 1 root root 27136560 Sep 14 02:48 /usr/bin/docker
```

- A little advance example can be:

```sh
$ file $(ls -l /usr/bin/* | grep zip)
/usr/bin/bunzip2: symbolic link to 'bzip2' 
/usr/bin/bzip2: ELF 32-bit LSB executable, Intel 80386,
version 1 (SYSV), dynamically linked (uses shared libs), for
GNU/Linux 2.6.9, stripped
/usr/bin/bzip2recover: ELF 32-bit LSB executable, Intel 80386,
version 1 (SYSV), dynamically linked (uses shared libs), for
GNU/Linux 2.6.9, stripped
/usr/bin/funzip:ELF 32-bit LSB executable, Intel 80
```
- output is just partial, it's originally very long
- In this example output of pipeline become argument list for `file` command


### Quotes

quotes are used in command expansion to control how the shell interprets special characters and spaces.

  - Single quotes `(')` preserve the literal value of each character within the quotes.
  - Double quotes `(")` allow for variable expansion and command substitution while preserving spaces.
  - Backticks `(`)` are used for command substitution, replacing the command with its output.
  - Double quotes with a leading `$` ("$") are used for parameter expansion, expanding variables or special parameters.
  - Double quotes with a leading `@` ("@...") are used for array expansion, expanding each element of an array.

for example,

```sh
$ echo text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER
text /home/me/ls-output.txt a b foo 4 me
$ echo "text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER"
text ~/*.txt {a,b} foo 4 me
$ echo 'text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER'
text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER
```


