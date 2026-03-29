---
title: "customize_prompt"
draft: false
---

Tag: #linux #prompt 

# Customizing the Prompt

Like so many in linux, Prompt is highly configurable.

- We can configure pretty much, the way we want
- And it's give some sense of familarity because we can customize it the way we want

## Anatomy of a prompt

`[user@distro ~]$`

- Generally, without any config this is how our prompt look
- Notice, the prompt contain `username`, `hostname` and our `current directory`, You may ask why it look this way? 
    - The Prompt is defined by `env`  variable named `PS1` (prompt string 1) 
    - We can view the content of ps1 with `echo` command, 

    `$ echo $PS1`
    `output: [\u@\h \W]\$`

    - From the result we can understand something like, `@` sign `$` sign the square brackets `[]` else is mystery   

| Sequence | Value Displayed |
|----------|-----------------|
| \a       | ASCII bell. This makes the computer beep when it is encountered. |
| \d       | Current date in day, month, date format. For example, “Mon May 26.” |
| \h       | Hostname of the local machine minus the trailing domain name. |
| \H       | Full hostname. |
| \j       | Number of jobs running in the current shell session. |
| \l       | Name of the current terminal device. |
| \n       | A newline character. |
| \r       | A carriage return. |
| \s       | Name of the shell program. |
| \t       | Current time in 24-hour hours:minutes:seconds format. |
| \T       | Current time in 12-hour format. |
| \@       | Current time in 12-hour AM/PM format. |
| \A       | Current time in 24-hour hours:minutes format. |
| \u       | Username of the current user. |
| \v       | Version number of the shell. |
| \V       | Version and release numbers of the shell. |
| \w       | Name of the current working directory. |
| \W       | Last part of the current working directory name. |
| \!       | History number of the current command. |
| \#       | Number of commands entered during this shell session. |
| \$       | Displays a “$” character unless we have superuser privileges. Then it displays a “#” instead. |
| \[       | Signals the start of a series of one or more non-printing characters, used for embedding control characters like text colors. |
| \]       | Signals the end of a non-printing character sequence. |

for example,

```sh
17:37 linuxbox $ PS1="<\u@\h \W>\$ "
<me@linuxbox ~>$
```
- Now, we can play with prompt 

### Adding color

Withtout color, it looks dull so now we are gonna learn how to add color to prompt

here are some colors code to use, 

| Sequence     | Text        | Color Sequence Text | Color        |
|--------------|-------------|---------------------|--------------|
| \033[0;30m   | Black       | \033[1;30m          | Dark gray    |
| \033[0;31m   | Red         | \033[1;31m          | Light red    |
| \033[0;32m   | Green       | \033[1;32m          | Light green  |
| \033[0;33m   | Brown       | \033[1;33m          | Yellow       |
| \033[0;34m   | Blue        | \033[1;34m          | Light blue   |
| \033[0;35m   | Purple      | \033[1;35m          | Light purple |
| \033[0;36m   | Cyan        | \033[1;36m          | Light cyan   |
| \033[0;37m   | Light gray  | \033[1;37m          | White        |

- these are `ANSI` escape code

for example,

```sh
<me@linuxbox ~>$PS1="\[\033[0;31m\]<\u@\h \W>\$\[\033[0m\]"  
<me@linuxbox ~>$
```

- The new shell prompt will look red after using this command
- The escape sequence `\033[0;31m` is for red color so, the prompt will look red

### Moving the cursor

Escapes codes can be used to position the cursor.


| Escape Code         | Action                                                        |
|---------------------|---------------------------------------------------------------|
| \033[l;cH           | Move the cursor to line `l` and column `c`                    |
| \033[nA             | Move the cursor up `n` lines                                  |
| \033[nB             | Move the cursor down `n` lines                                |
| \033[nC             | Move the cursor forward `n` characters                        |
| \033[nD             | Move the cursor backward `n` characters                       |
| \033[2J             | Clear the screen and move the cursor to the upper-left corner |
| \033[K              | Clear from the cursor position to the end of the current line |
| \033[s              | Store the current cursor position                             |
| \033[u              | Recall the stored cursor position                             |

- With the use these escape sequence we can positions cursor anywhere we want.

example,

`PS1="\[\033[s\033[0;0H\033[0;41m\033[K\033[1;33m\t\033[0m\033[u\]<\u@\h \W>\$ "` 

