---
tags:
    - vmware
    - esxi
    - advanced-settings
---

# ESXi Advanced Settings
## Dell SC Kernel Settings
For a Dell SC Storage there are a few settings which should be set so the storage works as intended.
The first setting terminates vms in case of permanent storage loss, the second removes LUNs that are on PDL (Permanent Device loss)
```
esxcli system settings kernel set -s terminateVMonPDL -v TRUE
esxcli system settings advanced set -o "/Disk/AutoremoveOnPDL" -i 1
```
