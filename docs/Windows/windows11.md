---
tags:
    - microsoft
    - windows 11
---

# Windows 11
## Install Windows 11 on non supported hardware
The source for this information is [Oracle](https://blogs.oracle.com/virtualization/post/install-microsoft-windows-11-on-virtualbox)
You can set specific registry keys so that the installer wont check RAM, Secureboot and TMP 2.0

1. In the installer before clicking anything open a cmd window with **Shift + F10**
2. Open regedit
3. Go to **HKEY_LOCAL_MACHINE\SYSTEM\Setup**
4. Right-click **New** -> **Key** -> **LabConfig**
5. **New** -> **DWORD (32-bit)** -> **BypassTPMCheck** -> **1**
6. Do the same for **BypassRAMCheck** and **BypassSecureBootCheck**
