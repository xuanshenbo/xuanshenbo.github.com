---
layout: post
title: "Arch Linux Installation Guide"
description: ""
category: Unix
tags: [Unix]
---
{% include JB/setup %}

This is a simple guild that is much simpler than the official guild. It tells you how to install an Arch Linux & Windows dual system step by step. **Don't Panic!**

<!--more-->


1. [Prepare USB stick](#Prepare)
2. [Partition the disks & Formats the partitions](#Partition)
3. [Connect to the Internet](#Internet)
4. [Select the mirrors](#Mirrors)
5. [Install the base packages](#Packages)
6. [Configure the System](#Configuration)
7. [Install a bootloader](#Bootloader)
8. [Reboot](#Reboot)

---------

#Prepare USB stick <a id="Prepare"></a>



**Warning:** Remember to backup the USB, the **dd** command will erase the USB completely. 
Use **lsblk** command to find out the name of your USB drive.
DO **not** append a partition number, so do **not** use something like ```/dev/sdb1```

```
lsblk
```

```
dd bs=4M if=archlinux.iso of=/dev/sdx && sync
```

Then, you can use the USB stick boot the system.
Remember, if your system is 64 bit, then choose x86 64 archlinux. i686 is for 32 bit.

#Partition the disks & Formats the partitions<a id="Partition"></a>

Partition can be tricky.

####Identify the devices

```
lsblk
```

####Partitioning tools

 - parted
 - fdisk
 - others
 
####fdisk usage

I start fdisk from the shell prompt:

```
fdisk /dev/sdb
```

```
Command (m for help): p
```


    Command (m for help): n

    Command action

    	e extend

    	p primary partition (1-4)

    p

    Partition number (1-4): 1

Then , you need to follow the fdisk, calculate the size of each partition.
After you finish all the partitioning, use **w** to write to disk.

The partition plan can be different. Personally, I choose 20G for ```'/'```, then 40G for ```'/home'```.

####Create filesystems

```
mkfs.ext4 /dev/sdxY
```

####Mount the partitions

The ```/```  (root) partition must be mounted **first**.  If the root partition's name is sdxR. Do:

```
mount /dev/sdxR /mnt
```

The general procedure is to first create the mount point, and then mount the partition to it.

    mkdir -p /mnt/home
    mount /dev/sdxB /mnt/home


#Connect to the Internet<a id="Internet"></a>

use wifi-menu to connect to a wireless network:

```
wifi-menu
```

#Select the mirrors<a id="Mirrors"></a>


You may want to edit the mirrorlist file and place your preferred mirror first.

```
vi /etc/pacman.d/mirrorlist
```

If you want, you can delete all other lines but leave your favourite one. For example, I leave 3 US servers and a NZ server.

After change the file, use:

```
pacman -Syyu
```

To refresh all package lists.


#Install the base packages<a id="Packages"></a>


####Install the base system

The base system is installed using the pacstrap script.

```
pacstrap -i /mnt base base-devel
```

#Configure the System <a id="Configuration"></a> 

<br />

#### Configure fstab

    genfstab -U -p /mnt >> /mnt/etc/fstab
    cat /mnt/etc/fstab

**Warning:** The fstab file should always be checked after genering it. If you encounter errors running genfstab or later in the install process, do **not** run genfstab; just edit the fstab file.

#### Choot and configure the base system

chroot into your newly installed system:

```
arch-chroot /mnt /bin/bash
```

####Locale

```
vi /etc/locale.gen
```

Un comment en_US.UTF-8 UTF-8 or other locale.
Before locaes can be enabled, they must be generated:

```
locale-gen
```

Create ```/etc/locale.conf```, where LANG refers to the first column of an uncommented entry in ```/etc/locale.gen```

```
echo LANG=en_US.UTF-8 > /etc/locale.conf
```

Export the chosen locale:

```
export LANG=en_US.UTF-8
```


####Time zone
Available time zones and subzones can be found in the ```/usr/share/zoneinfo/Zone/subZone``` directories.

```
ln -s /usr/share/zoneinfo/Zone/SubZone /etc/locatime
```

####Hardware clock

Use UTC time

```
hwclock --systohc --utc
```

####Hostname

Define a name replace the 'myhostname' below:

```
echo myhostname > /etc/hostname
```

Add the same hostname to /etc/hosts:

    #<ip-address> <hostname.domain.org> <hostname>
    127.0.0.1 localhost.localdomain localhost myhostname
    ::1 localhost.localdomain localhost myhostname

####Configure the network

Install ```iw``` and ```wpa-supplicant``` which you will need to connect to a network:

```
pacman -S iw wpa_supplicant
```

#####Adding wireless networks

using ```wifi-menu```
install ```dialog```, which is required for ```wifi-menu```:

```
pacman -S dialog
```

Next time you start the system, use wifi-menu to connect to the Internet.

####Set the root password
Set the root password with

```
passwd
```

#Install a bootloader<a id="Bootloader"></a>

Install the grub package, to have search for other installed operating system, install os-prober in addition:

```
pacman -S grub os-prober
```

Install the bootloader to the drive Arch was installed to.

```
grub-install --target=i386-pc --recheck /dev/sda
```

Automatically generate grub.cfg:

```
grub-mkconfig -o /boot/grub/grub.cfg
```

#Reboot<a id="Reboot"></a>

```
exit
```

```
reboot
```
