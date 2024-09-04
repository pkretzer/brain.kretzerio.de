---
tags:
    - microsoft
    - windows
    - kms
    - key management server
---

# KMS
## Query KMS SRV Record from DNS
```powershell
nslookup -q=srv _vlmcs._tcp.domain.local
```

## Show KMS Host Keys
```powershell
cd C:\Windows\System32\
cscript slmgr.vbs /dli all > C:\tmp\keys.txt
```