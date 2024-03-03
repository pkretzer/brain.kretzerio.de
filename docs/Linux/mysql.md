---
tags:
    - linux
    - mysql
    - mariadb
    - database
---

# MySQL
## Export specific tables from mysql database
```bash
mysqldump -u user -p database mytable > export.sql
```

## Create database with special character -
```sql
CREATE DATABASE `ccnet-db`;
```

## Restore database dump
**If database already exists**
```bash
mysql -u user -p mydb < mydump.sql
```

**If database does not exist**
```bash
mysql -u root -p
create mydb;
mysql -u user -p mydb < mydump.sql
```
