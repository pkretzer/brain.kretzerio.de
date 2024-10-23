---
tags:
    - linux
    - mysql
    - mariadb
    - database
---

# MySQL
## Export database
```bash
mysqldump -u username -p database > database.sql
```

## Export database as archive
```bash
mysqldump -u username -p database | gzip -c > database.sql.gz
```

## Export specific tables from mysql database
```bash
mysqldump -u user -p database mytable > export.sql
```

## Create database with special character - (dash)
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

##  Restore database archive dump
**If database already exists**
```bash
zcat mydump.sql.gz | mysql -u user -p database
```

**If database does not exist**
```bash
mysql -u root -p
create mydb;
zcat mydump.sql.gz | mysql -u user -p database
```

## Create User
```bash
CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';
```

## Grant Privileges
**Dash in the database name**
```bash
GRANT ALL PRIVILEGES ON `database`.* TO 'username'@'localhost';
```

**Backup privileges**
```bash
GRANT LOCK TABLES, SELECT ON database.* TO 'backupuser'@'localhost';
```

## Show database size
```bash
SELECT table_schema, sum( data_length + index_length ) / 1024 / 1024 "Speicherbedarf (MB)" FROM information_schema.TABLES GROUP BY table_schema;
```

## Cleanup database
```bash
mysqlcheck -o --all-databases -u root -p  
```