---
tags:
    - vmware
    - esxi
    - pxe
    - pxe-boot
---

# PXE-Boot

## Remove / (Slash) in boot.cfg so ISO can be booted via PXE
When you want to boot a standard VMware ESXi ISO Image via PXE you need to unpack it and remove the / (Slash) at the beginning
of the modules, otherwise the path for booting will not be correct. You can do this via the linux sed package.
```bash
sed -i 's/\///g' boot.cfg
```