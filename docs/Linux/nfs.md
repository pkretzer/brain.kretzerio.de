---
tags:
    - linux
    - nfs
    - nfs-server
---

# NFS
## Activate nfs Debuglog for client
**The log entries will be visible in the syslog (/var/log/messages or /var/log/syslog)**  
~~~bash
rpcdebug -m nfs -s auth proc
~~~

**Clear log flags**
~~~bash
rpcdebug -m nfs -c all
~~~

## Activate nfs Debuglog for server
**The log entries will be visible in the syslog (/var/log/messages or /var/log/syslog)**  
~~~bash
rpcdebug -m nfsd -s auth proc
~~~

**Clear log flags**
~~~bash
rpcdebug -m nfsd -c all
~~~