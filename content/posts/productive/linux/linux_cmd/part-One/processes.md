---
title: "processes"
draft: false
---

Tag : #linux #commands #processes #crash

# Processes

The OS manages processes through scheduling, memory allocation, and communication. Processes have unique IDs (PIDs) and can be parent or child processes. They run in user space, and system calls interact with the kernel. Concurrency is handled via multitasking, with processes either running, waiting, or stopped. Processes can be controlled using commands like `ps`, `top`, and  `kill`.

## Command used

1. ps - Report a snapshot of current processes
2. top - Displays tasks
3. jobs  - List active jobs
4. bg - Place a job in background
5. fg - Place a job in foreground
6. kill - Send a signal to a process
9. killall - kill process by name
10. shutdown - shutdown or reboot the system

### How Proccess works

When a system starts up, the kernal initiates a few of its own activities as processes and launches a program called `init`.

- `init` runs a series of shell scripts(located in `/etc`) called init scripts, which starts all the system services.
- The fact the a program can launch another program is expressed in the process scheme as a *parent process* producing *child process*
- The kernal maintain information about each process to hlep keep things organized.
  - Each process is assigned with process ID(PID). 
  - Pid is assigned in acending order,with `init` always getting PID(1)

#### Viewing Processes (command used `ps`)

The most common command to view process is `ps`. 

- The `ps` command have serveral options but simplest form is used like this:

```sh
$ ps
PID TTY TIME CMD
5198 pts/1 00:00:00 bash
10129 pts/1 00:00:00 ps
```

- The result in this example, output of `ps` command is list of two processes `bash` and `ps` with their PID number
- By default ps command doesn't give much info on processes, To see more we have to give more arguments 
- To see every process you own, you can use this comand: 

```sh
$ ps x
 PID TTY      STAT   TIME COMMAND
818 tty1     Ssl+  21:15 sway
857 tty1     S+     0:00 swaybg -o eDP-1 -i /home/kdrai/Downloads/bg.jpg -m fit -o HDMI-A-1 -i /home/kdrai/Downloads/bg.jpg -m fit -o * -i /home/kdrai/Downloads/bg.jpg -m fit
874 tty1     Sl+    1:11 waybar -b bar-0
876 ?        S      0:00 mako
878 ?        S      0:00 wl-paste -t text --watch clipman store --no-persist
895 ?        Ssl    0:00 /usr/lib/at-spi-bus-launcher
901 ?        S      0:00 /usr/bin/dbus-broker-launch --config-file=/usr/share/defaults/at-spi2/accessibility.conf --scope user
902 ?        S      0:00 dbus-broker --log 4 --controller 9 --machine-id 23cd258233c646a893b5daa1e9d21502 --max-bytes 100000000000000 --max-fds 6400000 --max-matches 5000000000
903 ?        Ssl    0:00 /usr/lib/xdg-desktop-portal
and many more...
```

- Adding `x` argument tells `ps` to show all our proceses regardless of what terminal they are controlled by.
- The presence of `?` in the TTy column indicates there's no controlling terminal.

##### Viewing Processes dynamically with `top`

The `top` command displays a continously updating(by default every 5 seconds) display of the system process listed in order of process activity.

- The fact that `top` commands come from the top program is used to "top" process on the system.

### Controlling Processes

Let's observe what will happen when we run `kwrite` command in terminal

- first enter the `kwrite` command and verify that the program is running
- Next, return to the terminal window then press `ctrl+c`
- In a terminal, pressing `ctrl+c`, *interrupts* a program
- After the `ctrl+c` key is pressed `kwrite` program will closed and shell prompt returned.

#### Putting a Process in the Background

Let's say we want shell prompt without terminating or interrupting a program

- We can do this by putting `&` after the program.

for example,

```sh
$ kwrite &
[1] 28236
```
- the shell will return PID number means Program ID
- We can use this PID for various purpose like, `kill` this program with,

```sh
kill 28236
[1]  + 113380 done       kwrite
```
#### Rreturning a Process in the Foreground

A proccess in background is immune from terminal keyboard intput,including any try to interrupts with `ctrl+c`  

- To return a program in foreground use,

`$ fg %1`

- and we can put it back to background using

`$ bg %1`

#### Stopping (Pausing) a Process

Sometimes we'll want to stop a process without terminating it.

- To stop a foreground process use `ctrl+z`  to put the process in background.
- use `fg` to put it back in foreground

### Signals

The `kill` command is used to "kill" processes.

- This allows us to terminate program that need killing

for example,

```sh
$ xlogo &
[1] 28401
$ kill 28401
[1]+ Terminated xlogo
```

While this is all very straightforward, there is more to it than that. the `kill` command doesn't exactly kill processes: rather it sends them a *signals* 

- Signals are one of the serveral ways a os(operating system) communicates with programs
- We have already seen signals in action with the use of `ctrl+c`, `ctrl+z` 
  - When terminal receive one of these keystrokes, It sends a signal to the program in foreground 
  - In the case of `ctrl+c`,a signal called INT(interrupt) is sent.
  - with `ctlr+z`, a signal called TSTP (terminal stop) is sent.
- Programs, in turn, "listen" for signals and may act upon them as they are received.

- **Comman Signals** :-

|Number|Name|Meaning|
|------|----|-------|
|1|HUP|HangUP|
|3|QUIT|quite|
|2|INT|Interrupt|
|9|KILL|Kill, this signal is special directly goes to kernal, use it as a last resort|
|15|TERM|Terminate|
|18|CONT|Continue|
|19|STOP|stop|
|20|TSTP|Terminal Stop|

- This, command will show all available signals

`$ kill -l`

let's use the kill command with signals,

```sh
$ xlogo &
[1] 13546
$ kill -1 13546
[1]+ Hangup xlogo
```

#### Sending signals to multiple processes with `killall`

It's also possible to send signals to multiple processes with `killall` command. 

Here's the syntax,

```sh
$ kwrite &
[1] 18801
$ kwrite &
[1] 18802
$ killall kwrite
[1]- Terminated xlogo
[2]+ Terminated xlogo
```

### Shutting Down the System.

The process of shutting down the system require to first kill or close all running proccess, as well as performing some housekeeping chores(like syncing all of the mounted file systems) before system poweroff.

- There are four commands that can perform these operations like,
  -  `halt`,`reboot`,`poweroff` and `shutdown`
  -  here's an example,

  ```sh
  $ sudo poweroff
  $ sudo reboot
  $ sudo shutdown -h now
  ```

- More Process related commands

- `pstree` -> Outputs a process list arranged in a tree-like pattern showing the parent-child relationships between processes.
- `vmstat` -> Outputs a snapshot of system resource usage including, memory, swap, and disk I/O. To see a continuous display, follow the command with a time delay (in seconds) for updates.









