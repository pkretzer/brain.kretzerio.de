---
tags:
    - linux
    - mdadm
    - software-raid
---

# MDADM
## Start manual mdadm RAID-Check
With the below command you can start a manual raid-check, just change md0 to your raid name.
```bash
echo check > /sys/block/md0/md/sync_action
```

## Stop mdadm RAID-Check
With the below command you can stop a running raid-check, just change md0 to your raid name.
```bash
echo idle > /sys/block/md0/md/sync_action
```

## Add/Remove disk to mdadm RAID
**Add new disk**
```bash
mdadm --manage /dev/md0 --add /dev/sdx1
```

**Remove disk**
```bash
mdadm --manage /dev/md0 --set-faulty /dev/sdx1
mdadm --manage /dev/md0 --remove /dev/sdx1
```

## Reassemble broken raid
```bash
mdadm --assemble --run --force /dev/md3 /dev/sd[a-x]1
```
