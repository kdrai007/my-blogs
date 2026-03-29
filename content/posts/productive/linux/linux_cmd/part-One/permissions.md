---
title: "permissions"
draft: false
---

Tag : #linux #permission #commands

# Permissions in linux

## Used Commands

1. id - Display user identity 
2. chmod - Change's file mode
3. umask - Set the defualt file permission
4. su - Run a shell as superuser
5. sudo - Execute a command as another user
6. chown - Change file's owner
7. chgrp - Change file's group ownership
8. passwd - Change user's password

### Owner,Groups,Members and everybody else

When we explore system pretty deep, we may encounter problem when trying to examine a file such as `/etc/passwd`

```sh
$ cat /etc/passwd
/etc/passwd: regular file, no read permission
$ less /etc/shadow
/etc/shadow: permission denied
```

- Reason for these error is, as a regular user we do not have permission to read these files
- In the *Unix* security model, a user may own files and directories, the user have control over its access 
- To check user's information about your identity, use the `id`  command

`$ id`
`output:uid=500(me) gid=500(me) groups=500(me)`

| Attribute | Files                                      | Directories                                                                                                |
| --------- | ------------------------------------------ | ---------------------------------------------------------------------------------------------------------- |
| r         | Allows a files to be opened and read       | Allow's directory's content to be listed                                                                   |
| w         | Allows a files to be written               | Allows files within the directory to be created ,deleted and renamed if the exectute attribute is also set |
| x         | Allows a files to be treated as a program. | Allows a directory to be entred, for e.g, cd directory                                                     |

#### chmod - Change File Mode

To change a  mode(permission) of file or directory, the `chmod` command is used.

- Be aware only file's owner and superuser can change the mode of file or directory
- `chmod` supports two distinct ways of specifying mode changes: octal number representation,or symbolic representation

- File modes in binary and octal

|Octal|Binary|File Mode|
|-----|------|---------|
|0|000|---|
|1|001|--x|
|3|010|-w-|
|4|100|r--|
|5|101|r-x|
|6|110|rw-|
|7|111|rwx|

- By using three octal digits,we can set the file mode for the owner,group owner and world

for example,

```sh
$ chmod 600 file.txt
$ ls -la file.txt
-rw------- 1 me me 0 2016-03-06 14:52 file.txt
```
- Ok so, after performing `chmod` command with argument `600`,we were able to set permissions of the owner to read and write while removing all permissions from the group owner and the world.

- `chmod` also supports symbolic notation.
- Symbolic notaton divided into three parts
  - Who the change will affect
  - Which operations will be performed
  - What permission will be set

- `chmod` symbolic notation

|Symbol | Meaning|
|-------|--------|
|u|Short for 'user' but means the file or directory owner|
|g|Group owner.|
|o|Short for 'others' but means world.|
|a|Short for 'all'. This is combination of 'u' 'g' and 'o'.|

- If no character is specified "all" will be assumed

- Some `chmod` symbolic Notation Examples,

  1. `u+x`    - Add execute permission for owner 
  2. `u-x`    - Remove execute permission for owner.
  3. `+x`     - Add execute permission to owner, owner group. This is equivalent to `a+x`
  4. `o-rw`   - Remove the read the write permission other and owner and group owner.
  5. `u+x,go=rx` - home work understand on your own, multiple specfications may be seperated by commas

----
##### What is octal number?

Octal(base 8) and,its cousin, hexadecimal(base 16) are number system often used to express numbers on computers.

- In octal, counting is done with the numberal zero through seven, like so;
0, 1, 2, 3, 4, 5, 6, 7, 10, 11, 12, 13, 14, 15, 16, 17, 20, 21...

- In hexadecimal counting uses the numerals zero through 9 plus the letters "A" to "F": 
0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F, 10, 11, 12, 13...

----

#### umask - Set default Permissions

The umask commands controls the defult permissions given the file when it is created.

- It uses octal notation to express a mask of bits to be removed from a file's mode attributes 

for example,

```sh
$ rm -f file.txt
$ umask
0002
$ touch file.txt
$ ls -l file.txt
-rw-rw-r-- 1 me me 0 2018-03-06 14:53 file.txt
```

- We removed any copy of `file.txt` to make sure we are on same page.
- We run the umask command without any argument to see the current value which was `0002`,which is octal representation of our mask 
- Then,we create new `file.txt` see their permissions,We can see that both owner and group get read and write permission,while everyone else get a read permission

We can change the value of mask like this,

```sh
$ rm file.txt
$ umask 0000
$ touch file.txt
$ ls -l file.txt
-rw-rw-rw- 1 me me 0 2018-03-06 14:58 file.txt
```
- Now,everyone have read and write permissions

### Changing Identities

At various time, we may need to perform some task as another user,Often we want to gain `superuser` privileges to carry out some adminstrative task, but it is also possible to "become" another regular  user  for such things as testing an accounting.

- There are three ways to take a alternative identity.
  - Log out and log back in as another user
  - use `su` command 
  - Use the `sudo` command

#### su - Run a shell with subsitute user and Group Ids

The `su` command is used to start the shell as another user.

- syntax look like this,

`$ su [[-l]] [user]`

- if the `-l` option is included, the result shell session is a login shell for the specified user.
- To start a shell for superuser,we would do this:

```sh
$ su -
Password:
# 
```

- After running `su -` command shell will ask for password for superuser, after entering correct password we can access root user account(# is sign for superuser)
- Once, we carry out commands as superuser, then enter `exit` to log back in your previous shell.

- It is also possible to execute a single command rahter than starting a interactive shell session 

`$ su -c 'command'`

for example,

```sh
$ su -c 'ls -l /root/*'
password:
-rw------- 1 root root 754 2007-08-11 03:19 /root/anaconda-ks.cfg
/root/Mail:
totoal 0
$ 
```

#### sudo - Execute the command as another user

The `sudo` command is like `su` in many ways but has some important additional capabilities. The adminstrator can configure `sudo` to allow a regular user to execute commands as different user(usually as superuser) in a controlled way.

- To perform a sudo command user doesn't need to know superuser's password but he should remember his own.

for example,

```sh
$ sudo apt update && sudo apt upgrade
Password:
programes to upgrades:
```
- In the above example, to perform updates on program a user need superuser privilege

#### chown - Change file owner and group

The chown command is used to change ownership of file and directories. superuser privileage are required to run this command.

- syntax of`chown` look like this:

`$ chown [owner][:[group]] file...`

- chown argument examples:
  - bob       - Changes the ownership of the file to user `bob`
  - bob:users - Changes the ownership of the file to user `bob` and changes the file group owners to group `users`
  - :admins   - Changes the group owner to the group `admins`. The file owner is unchanged
  - bob:      - Changes the file owner from the current owner to user `bob` and ,changes the group owner to the login group of user bob.

for example,

```sh
$ ls -l file.txt
-rw-r--r-- 1 me me 85 Sep  8 11:53 file.txt
$ sudo chown root: file.txt
password:
$ ls -l file.txt
-rw-r--r-- 1 root root 85 Sep  8 11:53 todo.txt
```

#### chgrp - Change Group Ownership

In older version of Unix, the chown command only change file ownership, not group ownership. For that purpose, a seperate command, `chgrp` was used.

- It work same as chown except for being more limited.

#### passwd - Change your password

To set or change password,the `passwd` command is used 

syntax,

`$ password [user]`

- To change just your password only `passwd` command is enough, you will be promted for your old password then new password.

```sh
$ passwd
Changing password for me.
Current password:
new password:
```











