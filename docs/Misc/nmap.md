---
tags:
    - nmap
---

# NMAP
Scan a network for open ports  
**Aggressive**
```bash
namp -v -A -T4 -oX nmap-scan.xml <subnet>
```

**Less aggressive**
```bash
namp -v -A -T3 -oX nmap-scan.xml <subnet>
```
