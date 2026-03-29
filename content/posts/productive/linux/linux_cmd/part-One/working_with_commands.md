---
title: "working_with_commands"
draft: false
---

Tag : #linux #commands
# Workings With Commands

## Used commands in this chapter

- type - Indicate how a command name is intepreted
- which - Display which executable program will be executed 
- help - Get help for shell builtins
- man  - Display a command's manual page
- apropos - Display a list of appropriate commands
- info - Display a command's info entry
- whatis - Display one line manual page descriptions
- alias - Create an alias for a command

### What Exactly are Commands ?

A command can one of the four different things:

1. An executable program
2. A command built into the shell itself
3. A shell function
4. An alias

### type - Display a Command's type

The `type` command is a shell builtin that display the kind of command the shell will execute, it work like this:

`$ type command`

here are some example,

```sh
$ type type
type is a shell builtin
$ type ls
ls is aliased to 'ls --color=tty'
```

### which - Display's an executables location

To determine the exact location of given excutables, the *which* command is used.

`$ which command`

here are some example,

```sh
$ which ls
ls: is shell builtin
$ which docker
/usr/bin/docker
```

### help - Get Help from Shell Builtins

Bash has the shell builtin help facility available for each of shell builtins, use *help*

`$ help command`

here are some example,

```sh
$ help cd
cd: cd [-L|[-P [-e]] [-@]] [dir]
Change the shell working directory.
Change the current directory to DIR.
value of the HOME shell variable.
The default DIR is the
The variable CDPATH defines the search path for the directory
containing DIR. Alternative directory names in CDPATH are
separated by a colon (:). A null directory name is the same as
the current directory. If DIR begins with a slash (/), then
CDPATH is not used.
If the directory is not found, and the shell option `cdable_vars'
is set, the word is assumed to be a variable name. If that
variable has a value, its value is used for DIR.
Options:
-L
force symbolic links to be followed: resolve symbolic
links in DIR after processing instances of `..'
-P
use the physical directory structure without following
symbolic links: resolve symbolic links in DIR before
processing instances of `..'
-e
if the -P option is supplied, and the current working
directory cannot be determined successfully, exit with
a non-zero status
```
> Note : If you are using some another shell like *zsh* *fish* you can't access help command

#### --help - Display Usage Information

Many executable program supports `--help` options that displays a description of the command's supported syntax and options

`$command --help`

here are some example,

```sh
$ mkdir --help
Usage: mkdir [OPTION]... DIRECTORY...
Create the DIRECTORY(ies), if they do not already exist.

Mandatory arguments to long options are mandatory for short options too.
  -m, --mode=MODE   set file mode (as in chmod), not a=rwx - umask
  -p, --parents     no error if existing, make parent directories as needed,
                    with their file modes unaffected by any -m option.
  -v, --verbose     print a message for each created directory
  -Z                   set SELinux security context of each created directory
                         to the default type
      --context[=CTX]  like -Z, or if CTX is specified then set the SELinux
                         or SMACK security context to CTX
      --help        display this help and exit
      --version     output version information and exit

GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
Full documentation <https://www.gnu.org/software/coreutils/mkdir>
or available locally via: info '(coreutils) mkdir invocation'
```

### man - Display's a program Manual page

Most executble program intended for command line use provide a formal piece of documentation called a manual or man page.

`$ man command`

- Manual page is very large in size so, I'will not show you guys 

- Sometimes we need to refer to a specific section of the man page to find what we are looking for.

`$ man section search_term`

example,

`$ man 5 passwd`

- This will display the man page describing the file format of the /etc/passwd file.


### apropos - Display appropriate commands

It is also possible to search the list of man pages for possible matches based on a search term 

`$ apropos command`

here a example,

```sh
$ apropos partiton
addpart (8) - simple wrapper around the "add partition"...
all-swaps (7) - event signalling that all swap partitions...
cfdisk (8) - display or manipulate disk partition table
cgdisk (8) - Curses-based GUID partition table (GPT)...
delpart (8) - simple wrapper around the "del partition"...
fdisk (8) - manipulate disk partition table
fixparts (8) - MBR partition table repair utility
```

### whatis - Display one-line manual page description

The *whatis* command display the one page description of the manual page matching specified word.

`$ whatis specified_word`

for example,

```sh
$ whatis ls
ls (1) - list directory contents
```

> Dare: read the whole man page of `bash`

### info - Display a program's info history

The *GNU* Project provides an alternatives for man page called `info`

- The info program reads info files, which are tree structured into individual nodes, each contains a single topic.

`$ info command`

example, 

`$ info coreutils`

- This command will show a page with hyperlinks to each program contained in coreutils package.


### alias - Creating our own commands using alias

We can create own command using alias

`$ alias name='commands'`

example,

```sh
$ alias ..='cd ..'
```
- now whenever we use `..` we will get back to one directory back.

#### Remove alias

For removing previously saved alias use

`$ unalias foo`

- This command will remove your alias from program list

> Note: To list our all prev saved alias use `$ alias` command to list every alias in your shell
> Problem: The only problem is while defining alias in  our shell, it will vanish when our shell restart.

