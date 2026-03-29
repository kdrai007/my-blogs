---
title: "storage_media"
draft: false
---

Tag: #linux #command #storage

# Storage Media

Linux has amezing capabilites of handling storage devices, whether physical storage like, hard drive, network storage or virtual devices like RAID(Redundent Array of Independent Disks) and LVM ( Logical Volume Manager). 

## Commands used

- mount – Mount a file system
- umount – Unmount a file system
- fsck – Check and repair a file system
- fdisk – Manipulate disk partition table
- mkfs – Create a file system
- dd – Convert and copy a file
- genisoimage (mkisofs) – Create an ISO 9660 image file
- wodim (cdrecord) – Write data to optical storage media
- md5sum – Calculate an MD5 checksum

### Mounting and Umounting storage devices

The first step is attaching a storage device to the file system tree. This process, called *mounting*, allows the device to interact with operating system. 

- A file name `/etc/fstab` (short for 'file system table' ) lists the device (typically hard disk partitions) that are to be mounted at boot time 
- Here, an example of `/etc/fstab` file

```sh
LABEL=/12    /          ext4 defaults 1 1
LABEL=/home  /home      ext4 defaults 1 2
LABEL=/boot  /boot      ext4 defaults 1 2
```
These are the hard disk partitions 

#### Viewing A list of File Systems

The `mount` command is used to mount file systems. Entering this command without any argument will list all mounted devices. 

- like, 

```sh
$ mount
/dev/sda2 on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda5 on /home type ext4 (rw)
/dev/sda1 on /boot type ext4 (rw)
```

- here en example, for mounting and umouting Disk Storage

```sh
# umount /dev/sdc
# mkdir -r /mnt/cdrom
# mount -t iso9660 /dev/sdc /mnt/cdrom
```

- After mouting our Disk to `/mtn/cdrom` we can check it's content
- And notice what will hapeen when we try to unmount it

```sh
# ls
# umount /mnt/sdc
umount: /mnt/cdrom: device is busy
```
- Why we can't `umount` storage, becaues we can't remove device when they are being used by user or some process
- Change directory back to home then try again the same step and you will be sucessfullbusy 


#### Manupulating Partitions using fdisk

`fdisk` is one of a host  of programs(both command line and graphical) that allows us to interact with disk-like devices such as hard disk at a very low level.

- With this tool we can edit,create and delete file partitions 
- To work with flash drive we first have to `umount` it and then invoke  the `fdisk` program :

```sh
$ sudo umount /dev/sdb
$ sudo  fdisk /dev/sdb
```
- after edit quit the program

#### Creating new file system with mkfs

With out partition done, it's time to create new file system on your drive. To do this we can use `mkfs`(short for 'make file system') 

- With `mkfs` we can create variety of file system like ext4,btrfs etc

`$ sudo mkfs -t ext4 /dev/sdb`

- This program will show lot of information related blocks and stuff 
- To reformat back to original FAT32 file system, specify vfat as the file sytem type

`$ sudo mkfs -t vfat /dev/sdb`


### Moving data from directly to and from devices

While we usually think data in organized form,it is also possible to think of data in "raw" form. If we see disk for example, we see large number of "blocks" of data that os sees as directories and files. However if we see drive as large blocks of data we can perform various useful tasks, such as cloning devices. 


- The `dd` command perform this task. It copies blocks of data to one place to another.

`$ dd if=input_file of=output_file [bs=block_size [count=blocks]]`

<details>
<summary>Warning!</summary>
<br>
<p>The <code>dd</code> command is very powerful. It is named "data definition" but it's also called "disk destroy" because user either mistype if or of command. <strong>Always double check your command! before pressing enter</strong></p>
</details>

#### Process

Suppose, we have two flash drive of the same size `/dev/sda` and `/dev/sdb` and we want 2nd drive to be exact same copy of 1st drive

- Attach both drive to the system.
- then run this command:-

```sh
$ dd if=/dev/sda of=/dev/sdb 
```

Alternately, if we have only one flash drive attached to our system we can copy it's image to our system and then tranfer it back to another device  like this:- 

```sh
$ dd if=/dev/sda of=drive.img
# attach another drive then perform this command 
$ dd if=drive.img of=/dev/sdb
```











