---
tags:
    - linux
    - filesystem
    - disks
---

# Disks
## Extend a standard partition Online
**Rescan the disk after resizing**
```bash
echo "1" > /sys/class/block/sdb/device/rescan
```

**Extend partition with growpart**
```bash
growpart /dev/sdb 1
```

**Extend ext2/3/4 filesystem**
```bash
resize2fs /dev/sdb1
```

**Extend xfs filesystem**
```bash
xfs_growfs /dev/sdb1
```

## Extend a LVM Volume Online
**Rescan the disk after resizing**
```bash
echo "1" > /sys/class/block/sdb/device/rescan
```

**Extend partition with growpart if LVM is on a partition**
```bash
growpart /dev/sdb 1
```

**Resize Physical Volume**
```bash
pvresize /dev/sdb1
```

**Resize Logical Volume to full size**
```bash
lvextend -l +100%FREE /dev/my-vg/my-lv
```

**Extend ext2/3/4 filesystem**
```bash
resize2fs /dev/sdb1
```

**Extend xfs filesystem**
```bash
xfs_growfs /dev/sdb1
```

## Extend a Standard partition with parted
**Rescan the disk after resizing**
```bash
echo "1" > /sys/class/block/sdb/device/rescan
```

**Extend partition with parted**
```bash
parted -a optimal -s /dev/sdb resizepart 1 '100%'
```
If an error occurs that the blocks doesnt fit open parted an accept to fix the blocks.

**Extend ext2/3/4 filesystem**
```bash
resize2fs /dev/sdb1
```

**Extend xfs filesystem**
```bash
xfs_growfs /dev/sdb1
```

## Check all disks for faulty sectors
The below command checks all disks from /dev/sda to /dev/sdx for **Offline_Uncorrectable** and shows the results.
```bash
for i in /dev/sd[a-x]; do echo $i; smartctl -a $i | grep Offline_Uncorrectable;done
```

## Locate local disk and mark it with the Disk LED
For the below command the packet ledmon is needed.
**Activate Disk LED**
```bash
ledctl locate=/dev/sda
```

**Dectivate Disk LED**
```bash
ledctl locate_off=/dev/sda
```

## Create a partition with parted that uses the full size
**One Disk**
```bash
parted /dev/sdf mklabel gpt mkpart primary 0% 100%
```

**Bunch of disks**
```bash
parted /dev/sd[a...z] mklabel gpt mkpart primary 0% 100%
```
