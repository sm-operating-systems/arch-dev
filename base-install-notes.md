# Base Install

### Updating and setting mirror sites from base install

```
 $ pacman -Syu  # To force an update
 $ pacman -Syy  # to refresh mirror lists
```

### 1. Create disk partitions 
1. Run cfdisk and choose option dos
2. Create three partitions two primary types and one extended for home
   - Root partition of type primary and with "bootable" option
   - Swap partition of type primary - must be at  least twice the size of memory
   - Home partition of type extended for home directory
```
 $ fdisk -l  # should show two partitions, one for the current disk size and another loopback before creating partitions
``` 
```fdisk -l``` output should show the following after partitions have been created
 ![](screenshot1.png)

### 2. Format each partitions

The "root" and the "home" partitions should be formatted as ext4 while the swap partition as swp.

```
$ mkfs.ext4 /dev/sda1 #root partition
$ mkfs.ext4 /dev/sda5 #home partition
```
Now format and enable the swap partition
```
 $ mkswap /dev/sda2  # to format
 $ swapon /dev/sda2  #to turn it on
```
### 3. Mount the new created partitions
Mount root partition first
```
 $ mount /dev/sda1 /mnt # mounts the partition to the mount folder
```
Create a home folder under /mnt to mount the home folder to
```
 $ mkdir /mnt/home
 $ mount /dev/sda5 /mnt/home
```

### 4. Now install Arch Linux base system on /mnt
Use the pacstrap script to install the base system which is only 800M and for other development tools use base-devel
```
 $ pacstrap /mnt base base-devel
```
Use the [ArchLinux package search tool](https://www.archlinux.org/packages/) for all other available packages
