---
tags:
    - vmware
    - powercli
    - snapshots
---

# PowerCLI
## Get open snapshots with creation date
```powershell
Get-VM | Get-Snapshot | select VM, Name, Created
```
