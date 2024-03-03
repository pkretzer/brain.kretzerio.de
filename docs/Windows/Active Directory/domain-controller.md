---
tags:
    - microsoft
    - active directory
    - domain controller
    - dc
    - replication
---

# Domain Controller
## Check replication
**Check**
```powershell
Repadmin /replsummary
Repadmin /Queue
Repadmin /Showrepl
```

**Force replication**
```powershell
Repadmin /syncall
```
