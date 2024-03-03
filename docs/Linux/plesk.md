---
tags:
    - linux
    - plesk
    - mysql
    - database
---

# Plesk
## Backup mysql database  from plesk
Plesk has encrypted all database with an encryption key. You can use the plesk binary to create a backup from the cli.
```bash
/usr/sbin/plesk db dump database-name > /path/to/file.sql
```
