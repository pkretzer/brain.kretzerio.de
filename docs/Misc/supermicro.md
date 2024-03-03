---
tags:
    - supermicro
    - ipmi
    - password
---

# Supermicro
## Reset IPMI password via ipmicfg
If you forgot your IPMI password you can reset it via the supermicro [ipmicfg](https://www.supermicro.com/en/solutions/management-software/ipmi-utilities) tool.
You can use the tool from a booted linux live system for example.
```bash
ipmicfg -user setpwd 2 your_password_here
```
