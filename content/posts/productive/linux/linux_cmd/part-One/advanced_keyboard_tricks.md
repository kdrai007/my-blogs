---
title: "advanced_keyboard_tricks"
draft: false
---

Tag : #linux #keyboard #commands

# Advanced Keyboard Tricks

## Used commands

- clear - Clear the screen
- history - Display the contents of th history file

### Using history

`bash` maintains a history of commands that have been entered. A list of commands are kept in `.bash_history` in our home directory

- The history facility is a useful resource for reducing the amount of typing we have to do, for daily used commands

`$ history|less`
- We can see all the saved commands using this `command` with the help of `less`

- For example, we can use `grep` with `history`  command to grep a command which we used previously

```sh
$ history | grep "ls -l "`
 5  ls -la
 12  ls -la
 13  ls -la
 131  ls -la
```
- now we can use `5 ls -la` the number 5 to take the command as a input in `bash`

`$ !5`

- `bash` will expand `!5` into the content of the 5th line of history list

#### history expansion

The shell offers a specilized type of expansion for items in the history list by using `!` charcter 

- History expansion commands

| Sequence | Action                                            |
| -------- | ------------------------------------------------- |
| !!       | Repeat the last command                           |
| !number  | Repeat history list item number                   |
| !string  | Repeat last history item starting with the string |
| !?string | Repeat last hisotry list item containing string   |




