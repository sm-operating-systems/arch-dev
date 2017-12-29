# Base Install

### Updating and setting mirror sites from base install

```
 $ pacman -Syu  # To force an update
 $ pacman -Syy  # to refresh mirror lists
```

### Create disk partitions 
1. Run cfdisk and choose option dos
2. Create three partitions two primary types and one extended for home
```
 $ fdisk -l  # should show two partitions, one for the current disk size and another loopback
 ![](screenshot1.png)
